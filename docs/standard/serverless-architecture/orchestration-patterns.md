---
title: 協調流程模式-無伺服器應用程式
description: Azure Durable functions pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 18e13c5355490ef4a019ceda459114bdb6bfd539
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638791"
---
# <a name="orchestration-patterns"></a>協調流程模式

Durable Functions 可讓您更輕鬆地建立無伺服器環境中的離散、 長時間執行的活動所組成的可設定狀態工作流程。 執行歷程記錄時，Durable Functions 可以追蹤工作流程和定期檢查點的進度，因為它本身實作一些有趣的模式。

## <a name="function-chaining"></a>函式鏈結

在典型的循序程序，您需要以特定順序執行一個接著一個活動。 （選擇性） 即將推出的活動可能需要一些從先前的函式的輸出。 這種相依性的活動順序會建立執行的函式鏈結。

實作此工作流程模式使用 Durable Functions 的優點在於它可以執行檢查點。 如果伺服器當機，網路逾時或一些其他問題發生，Durable functions 可以從上次已知狀態恢復，並繼續執行您的工作流程，即使它是在另一部伺服器上。

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

在上述程式碼範例中，`CallActivityAsync`函式會負責資料中心內的虛擬機器上執行指定的活動。 Await 傳回和基礎的工作完成時，執行會記錄到記錄資料表中。 協調器函式中的程式碼可利用其中任何一熟悉的建構，工作平行程式庫和 async/await 關鍵字。

下列程式碼是什麼的簡化的範例`ProcessPayment`方法可能看起來像：

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

在某些情況下，工作流程可能需要相當長的時間才能完成的活動。 假設一開始會媒體的備份檔案到 blob 儲存體的程序。 根據大小和數量的媒體檔案，此備份程序可能需要小時才能完成。

在此案例中，`DurableOrchestrationClient`的能夠檢查執行中工作流程的狀態很實用。 使用時`HttpTrigger`啟動的工作流程中，`CreateCheckStatusResponse`方法可用來傳回的執行個體`HttpResponseMessage`。 此回應會提供用戶端可用來檢查執行中處理序狀態的承載中的 URI。

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

下列範例結果顯示的回應裝載的結構。

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

使用您慣用的 HTTP 用戶端，GET 要求可以對 statusQueryGetUri 中的 URI 來檢查執行中工作流程的狀態。 傳回的狀態回應看起來應該像下列程式碼。

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

此程序會繼續，因為狀態回應會將變更為**失敗**或是**已完成**。 成功完成時，**輸出**承載中的屬性會包含任何傳回的資料。

## <a name="monitoring"></a>監視

如需簡單的週期性工作，提供 Azure Functions `TimerTrigger` ，可排程的 CRON 運算式為基礎。 計時器很適合簡單、 存留較短的工作，但可能會有更彈性的排程，需要的位置的案例。 此案例時，Durable Functions 與監視的模式可以幫助。

Durable Functions 可讓彈性的排程間隔、 存留期管理，和從單一的協調流程函式的多個監視器處理序的建立。 這項功能的其中一個使用案例就是建立監看員在符合特定的臨界值之後完成的股票價格變更。

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

`DurableOrchestrationContext``CreateTimer`方法檢查股票價格變更會設定迴圈的下一個引動過程的排程。 `DurableOrchestrationContext` 也有`CurrentUtcDateTime`屬性來取得目前的日期時間值以 utc 格式。 最好是使用這個屬性，而不是`DateTime.UtcNow`因為它輕鬆地模擬 （mock） 進行測試。

## <a name="recommended-resources"></a>建議的資源

* [Azure Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [.NET Core 與 .NET Standard 中的單元測試](../../core/testing/index.md)

>[!div class="step-by-step"]
>[上一頁](durable-azure-functions.md)
>[下一頁](serverless-business-scenarios.md)
