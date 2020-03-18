---
title: 業務流程模式 - 無伺服器應用
description: Azure 持久功能 pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522644"
---
# <a name="orchestration-patterns"></a>編排模式

耐用的函數使創建由無伺服器環境中離散、長時間運行的活動組成的有狀態工作流變得更加容易。 由於持久函數可以跟蹤工作流的進度並定期檢查執行歷史記錄，因此它有助於實現一些有趣的模式。

## <a name="function-chaining"></a>函式鏈結

在典型的順序過程中，活動需要按特定順序逐一執行。 或者，即將進行的活動可能需要來自上一個函數的某些輸出。 這種對活動排序的依賴會創建一個執行的函數鏈。

使用持久函數來實現此工作流模式的好處來自于它執行檢查點的能力。 如果伺服器崩潰、網路超時或發生其他問題，則持久功能可以從上次已知狀態恢復並繼續運行工作流，即使它位於其他伺服器上也是如此。

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

在前面的代碼示例中，`CallActivityAsync`該函數負責在資料中心的虛擬機器上運行給定活動。 當等待返回和基礎任務完成時，執行將記錄到歷史記錄表中。 協調器函數中的代碼可以使用任務並行庫的任何熟悉的構造和非同步/等待關鍵字。

以下代碼是方法可能是什麼樣子的`ProcessPayment`簡化示例：

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

## <a name="asynchronous-http-apis"></a>非同步 HTTP API

在某些情況下，工作流可能包含需要相對很長時間才能完成的活動。 想像一下，將媒體檔案備份到 Blob 存儲的過程。 根據媒體檔案的大小和數量，此備份過程可能需要數小時才能完成。

在這種情況下，`DurableOrchestrationClient`檢查正在運行的工作流狀態的能力變得有用。 使用`HttpTrigger`啟動工作流時，`CreateCheckStatusResponse`該方法可用於返回 的`HttpResponseMessage`實例。 此回應在有效負載中為用戶端提供 URI，可用於檢查正在運行的進程的狀態。

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

下面的示例結果顯示回應負載的結構。

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

使用首選的 HTTP 用戶端，可以向狀態查詢GetUri 中的 URI 發出 GET 請求，以檢查正在運行的工作流的狀態。 返回的狀態回應應類似于以下代碼。

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

隨著進程的繼續，狀態回應將更改為 **"失敗"** 或 **"已完成**"。 成功完成後，有效負載中的**輸出**屬性將包含任何返回的資料。

## <a name="monitoring"></a>監視

對於簡單的重複任務，Azure 函數提供`TimerTrigger`可以基於 CRON 運算式進行計畫的。 計時器適用于簡單、短期的任務，但在某些情況下可能需要更靈活的調度。 此方案是監視模式和持久函數可以提供説明時。

持久函數允許靈活的調度間隔、存留期管理和從單個業務流程函數創建多個監視器進程。 此功能的一個用例可能是為滿足特定閾值後完成的股價變化創建觀察程式。

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

`DurableOrchestrationContext`該方法`CreateTimer`設置迴圈下一次調用的計畫，以檢查股票價格變化。 `DurableOrchestrationContext`還具有用於`CurrentUtcDateTime`獲取 UTC 中的當前 DateTime 值的屬性。 最好使用此屬性，`DateTime.UtcNow`而不是因為它很容易被嘲笑以進行測試。

## <a name="recommended-resources"></a>建議的資源

- [Azure Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [.NET 核心和 .NET 標準中的單元測試](../../core/testing/index.md)

>[!div class="step-by-step"]
>[上一個](durable-azure-functions.md)
>[下一個](serverless-business-scenarios.md)
