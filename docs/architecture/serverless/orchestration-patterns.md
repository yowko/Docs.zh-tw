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
# <a name="orchestration-patterns"></a><span data-ttu-id="645a0-103">編排模式</span><span class="sxs-lookup"><span data-stu-id="645a0-103">Orchestration patterns</span></span>

<span data-ttu-id="645a0-104">耐用的函數使創建由無伺服器環境中離散、長時間運行的活動組成的有狀態工作流變得更加容易。</span><span class="sxs-lookup"><span data-stu-id="645a0-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="645a0-105">由於持久函數可以跟蹤工作流的進度並定期檢查執行歷史記錄，因此它有助於實現一些有趣的模式。</span><span class="sxs-lookup"><span data-stu-id="645a0-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="645a0-106">函式鏈結</span><span class="sxs-lookup"><span data-stu-id="645a0-106">Function chaining</span></span>

<span data-ttu-id="645a0-107">在典型的順序過程中，活動需要按特定順序逐一執行。</span><span class="sxs-lookup"><span data-stu-id="645a0-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="645a0-108">或者，即將進行的活動可能需要來自上一個函數的某些輸出。</span><span class="sxs-lookup"><span data-stu-id="645a0-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="645a0-109">這種對活動排序的依賴會創建一個執行的函數鏈。</span><span class="sxs-lookup"><span data-stu-id="645a0-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="645a0-110">使用持久函數來實現此工作流模式的好處來自于它執行檢查點的能力。</span><span class="sxs-lookup"><span data-stu-id="645a0-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="645a0-111">如果伺服器崩潰、網路超時或發生其他問題，則持久功能可以從上次已知狀態恢復並繼續運行工作流，即使它位於其他伺服器上也是如此。</span><span class="sxs-lookup"><span data-stu-id="645a0-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="645a0-112">在前面的代碼示例中，`CallActivityAsync`該函數負責在資料中心的虛擬機器上運行給定活動。</span><span class="sxs-lookup"><span data-stu-id="645a0-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="645a0-113">當等待返回和基礎任務完成時，執行將記錄到歷史記錄表中。</span><span class="sxs-lookup"><span data-stu-id="645a0-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="645a0-114">協調器函數中的代碼可以使用任務並行庫的任何熟悉的構造和非同步/等待關鍵字。</span><span class="sxs-lookup"><span data-stu-id="645a0-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="645a0-115">以下代碼是方法可能是什麼樣子的`ProcessPayment`簡化示例：</span><span class="sxs-lookup"><span data-stu-id="645a0-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="645a0-116">非同步 HTTP API</span><span class="sxs-lookup"><span data-stu-id="645a0-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="645a0-117">在某些情況下，工作流可能包含需要相對很長時間才能完成的活動。</span><span class="sxs-lookup"><span data-stu-id="645a0-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="645a0-118">想像一下，將媒體檔案備份到 Blob 存儲的過程。</span><span class="sxs-lookup"><span data-stu-id="645a0-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="645a0-119">根據媒體檔案的大小和數量，此備份過程可能需要數小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="645a0-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="645a0-120">在這種情況下，`DurableOrchestrationClient`檢查正在運行的工作流狀態的能力變得有用。</span><span class="sxs-lookup"><span data-stu-id="645a0-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="645a0-121">使用`HttpTrigger`啟動工作流時，`CreateCheckStatusResponse`該方法可用於返回 的`HttpResponseMessage`實例。</span><span class="sxs-lookup"><span data-stu-id="645a0-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="645a0-122">此回應在有效負載中為用戶端提供 URI，可用於檢查正在運行的進程的狀態。</span><span class="sxs-lookup"><span data-stu-id="645a0-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="645a0-123">下面的示例結果顯示回應負載的結構。</span><span class="sxs-lookup"><span data-stu-id="645a0-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="645a0-124">使用首選的 HTTP 用戶端，可以向狀態查詢GetUri 中的 URI 發出 GET 請求，以檢查正在運行的工作流的狀態。</span><span class="sxs-lookup"><span data-stu-id="645a0-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="645a0-125">返回的狀態回應應類似于以下代碼。</span><span class="sxs-lookup"><span data-stu-id="645a0-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="645a0-126">隨著進程的繼續，狀態回應將更改為 **"失敗"** 或 **"已完成**"。</span><span class="sxs-lookup"><span data-stu-id="645a0-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="645a0-127">成功完成後，有效負載中的**輸出**屬性將包含任何返回的資料。</span><span class="sxs-lookup"><span data-stu-id="645a0-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="645a0-128">監視</span><span class="sxs-lookup"><span data-stu-id="645a0-128">Monitoring</span></span>

<span data-ttu-id="645a0-129">對於簡單的重複任務，Azure 函數提供`TimerTrigger`可以基於 CRON 運算式進行計畫的。</span><span class="sxs-lookup"><span data-stu-id="645a0-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="645a0-130">計時器適用于簡單、短期的任務，但在某些情況下可能需要更靈活的調度。</span><span class="sxs-lookup"><span data-stu-id="645a0-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="645a0-131">此方案是監視模式和持久函數可以提供説明時。</span><span class="sxs-lookup"><span data-stu-id="645a0-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="645a0-132">持久函數允許靈活的調度間隔、存留期管理和從單個業務流程函數創建多個監視器進程。</span><span class="sxs-lookup"><span data-stu-id="645a0-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="645a0-133">此功能的一個用例可能是為滿足特定閾值後完成的股價變化創建觀察程式。</span><span class="sxs-lookup"><span data-stu-id="645a0-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="645a0-134">`DurableOrchestrationContext`該方法`CreateTimer`設置迴圈下一次調用的計畫，以檢查股票價格變化。</span><span class="sxs-lookup"><span data-stu-id="645a0-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="645a0-135">`DurableOrchestrationContext`還具有用於`CurrentUtcDateTime`獲取 UTC 中的當前 DateTime 值的屬性。</span><span class="sxs-lookup"><span data-stu-id="645a0-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="645a0-136">最好使用此屬性，`DateTime.UtcNow`而不是因為它很容易被嘲笑以進行測試。</span><span class="sxs-lookup"><span data-stu-id="645a0-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="645a0-137">建議的資源</span><span class="sxs-lookup"><span data-stu-id="645a0-137">Recommended resources</span></span>

- [<span data-ttu-id="645a0-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="645a0-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="645a0-139">.NET 核心和 .NET 標準中的單元測試</span><span class="sxs-lookup"><span data-stu-id="645a0-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="645a0-140">[上一個](durable-azure-functions.md)
>[下一個](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="645a0-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
