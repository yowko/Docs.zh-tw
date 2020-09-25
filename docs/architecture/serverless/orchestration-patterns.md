---
title: 協調流程模式-無伺服器應用程式
description: Azure 持久函式 pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 6c5f6aaedbc13c47289e102bb59f7b066525b107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171659"
---
# <a name="orchestration-patterns"></a>協調流程模式

Durable Functions 可讓您更輕鬆地建立可設定狀態的工作流程，這些工作流程是由無伺服器環境中的離散、長時間執行的活動 由於 Durable Functions 可以追蹤工作流程的進度，並定期檢查執行歷程記錄的檢查點，因此它本身就能實現一些有趣的模式。

## <a name="function-chaining"></a>函式鏈結

在一般的順序程式中，活動需要以特定循序執行另一個。 （選擇性）即將推出的活動可能需要某些來自先前函式的輸出。 這項活動順序的相依性會建立執行的函式鏈。

使用 Durable Functions 來執行此工作流程模式的好處，在於其執行檢查點的能力。 如果伺服器當機、網路超時或發生一些其他問題，則永久性函式可以從上次已知狀態恢復，並繼續執行您的工作流程，即使它是在另一部伺服器上也一樣。

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

在上述程式碼範例中，函式 `CallActivityAsync` 負責在資料中心內的虛擬機器上執行指定的活動。 當 await 傳回且基礎工作完成時，會將執行記錄至歷程記錄資料表。 協調器函式中的程式碼可以利用工作平行程式庫和 async/await 關鍵字的任何熟悉的結構。

下列程式碼是方法可能外觀的簡化範例 `ProcessPayment` ：

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a>非同步 HTTP Api

在某些情況下，工作流程可能包含需要相當長時間才能完成的活動。 想像出將媒體檔案備份到 blob 儲存體的程式。 視媒體檔案的大小和數量而定，此備份程式可能需要數小時才能完成。

在此案例中， `DurableOrchestrationClient` 檢查執行中工作流程狀態的功能將會變得很有用。 使用 `HttpTrigger` 啟動工作流程時， `CreateCheckStatusResponse` 可以使用方法來傳回的實例 `HttpResponseMessage` 。 此回應會提供承載中的 URI 給用戶端，可用來檢查執行中進程的狀態。

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

下列範例結果顯示回應裝載的結構。

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

使用您慣用的 HTTP 用戶端時，您可以在 statusQueryGetUri 中對 URI 提出 GET 要求，以檢查執行中工作流程的狀態。 傳回的狀態回應應該類似于下列程式碼。

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

當程式繼續時，狀態回應會變更為 [ **失敗** ] 或 [ **已完成**]。 成功完成時，承載中的 **輸出** 屬性將會包含任何傳回的資料。

## <a name="monitoring"></a>監視

針對簡單的週期性工作，Azure Functions 提供 `TimerTrigger` 可根據 CRON 運算式排程的。 計時器適用于簡單、短期的工作，但在某些情況下，可能需要更多彈性的排程。 此案例是監視模式和 Durable Functions 可以提供協助。

Durable Functions 可提供彈性的排程間隔、存留期管理，以及從單一協調流程函式建立多個監視器進程的功能。 這項功能的其中一個使用案例，就是在符合特定臨界值時，為完成的股票價格變更建立監看員。

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

`DurableOrchestrationContext`的 `CreateTimer` 方法會設定下一個叫用迴圈的排程，以檢查股票價格變更。 `DurableOrchestrationContext` 也有 `CurrentUtcDateTime` 屬性可取得目前的日期時間值（UTC）。 最好使用此屬性而不是， `DateTime.UtcNow` 因為它很容易模擬進行測試。

## <a name="recommended-resources"></a>建議的資源

- [Azure Durable Functions](/azure/azure-functions/durable-functions-overview)
- [.NET Core 和 .NET Standard 中的單元測試](../../core/testing/index.md)

>[!div class="step-by-step"]
>[上一個](durable-azure-functions.md) 
>[下一步](serverless-business-scenarios.md)
