---
title: 協調流程模式-無伺服器應用程式
description: Azure Durable functions pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8be499a24e2c5a94132ce07241e17f675e8a1274
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843754"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="a5a74-103">協調流程模式</span><span class="sxs-lookup"><span data-stu-id="a5a74-103">Orchestration patterns</span></span>

<span data-ttu-id="a5a74-104">Durable Functions 可讓您更輕鬆地建立無伺服器環境中的離散、 長時間執行的活動所組成的可設定狀態工作流程。</span><span class="sxs-lookup"><span data-stu-id="a5a74-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="a5a74-105">執行歷程記錄時，Durable Functions 可以追蹤工作流程和定期檢查點的進度，因為它本身實作一些有趣的模式。</span><span class="sxs-lookup"><span data-stu-id="a5a74-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="a5a74-106">函式鏈結</span><span class="sxs-lookup"><span data-stu-id="a5a74-106">Function chaining</span></span>

<span data-ttu-id="a5a74-107">在典型的循序程序，您需要以特定順序執行一個接著一個活動。</span><span class="sxs-lookup"><span data-stu-id="a5a74-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="a5a74-108">（選擇性） 即將推出的活動可能需要一些從先前的函式的輸出。</span><span class="sxs-lookup"><span data-stu-id="a5a74-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="a5a74-109">這種相依性的活動順序會建立執行的函式鏈結。</span><span class="sxs-lookup"><span data-stu-id="a5a74-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="a5a74-110">實作此工作流程模式使用 Durable Functions 的優點在於它可以執行檢查點。</span><span class="sxs-lookup"><span data-stu-id="a5a74-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="a5a74-111">如果伺服器當機，網路逾時或一些其他問題發生，Durable functions 可以從上次已知狀態恢復，並繼續執行您的工作流程，即使它是在另一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a5a74-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="a5a74-112">在上述程式碼範例中，`CallActivityAsync`函式會負責資料中心內的虛擬機器上執行指定的活動。</span><span class="sxs-lookup"><span data-stu-id="a5a74-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="a5a74-113">Await 傳回和基礎的工作完成時，執行會記錄到記錄資料表中。</span><span class="sxs-lookup"><span data-stu-id="a5a74-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="a5a74-114">協調器函式中的程式碼可利用其中任何一熟悉的建構，工作平行程式庫和 async/await 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a5a74-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="a5a74-115">下列程式碼是什麼的簡化的範例`ProcessPayment`方法可能看起來像：</span><span class="sxs-lookup"><span data-stu-id="a5a74-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="a5a74-116">非同步 HTTP Api</span><span class="sxs-lookup"><span data-stu-id="a5a74-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="a5a74-117">在某些情況下，工作流程可能需要相當長的時間才能完成的活動。</span><span class="sxs-lookup"><span data-stu-id="a5a74-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="a5a74-118">假設一開始會媒體的備份檔案到 blob 儲存體的程序。</span><span class="sxs-lookup"><span data-stu-id="a5a74-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="a5a74-119">根據大小和數量的媒體檔案，此備份程序可能需要小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="a5a74-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="a5a74-120">在此案例中，`DurableOrchestrationClient`的能夠檢查執行中工作流程的狀態很實用。</span><span class="sxs-lookup"><span data-stu-id="a5a74-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="a5a74-121">使用時`HttpTrigger`啟動的工作流程中，`CreateCheckStatusResponse`方法可用來傳回的執行個體`HttpResponseMessage`。</span><span class="sxs-lookup"><span data-stu-id="a5a74-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="a5a74-122">此回應會提供用戶端可用來檢查執行中處理序狀態的承載中的 URI。</span><span class="sxs-lookup"><span data-stu-id="a5a74-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="a5a74-123">下列範例結果顯示的回應裝載的結構。</span><span class="sxs-lookup"><span data-stu-id="a5a74-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="a5a74-124">使用您慣用的 HTTP 用戶端，GET 要求可以對 statusQueryGetUri 中的 URI 來檢查執行中工作流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="a5a74-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="a5a74-125">傳回的狀態回應看起來應該像下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="a5a74-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="a5a74-126">此程序會繼續，因為狀態回應會將變更為**失敗**或是**已完成**。</span><span class="sxs-lookup"><span data-stu-id="a5a74-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="a5a74-127">成功完成時，**輸出**承載中的屬性會包含任何傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="a5a74-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="a5a74-128">監視</span><span class="sxs-lookup"><span data-stu-id="a5a74-128">Monitoring</span></span>

<span data-ttu-id="a5a74-129">如需簡單的週期性工作，提供 Azure Functions `TimerTrigger` ，可排程的 CRON 運算式為基礎。</span><span class="sxs-lookup"><span data-stu-id="a5a74-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="a5a74-130">計時器很適合簡單、 存留較短的工作，但可能會有更彈性的排程，需要的位置的案例。</span><span class="sxs-lookup"><span data-stu-id="a5a74-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="a5a74-131">此案例時，Durable Functions 與監視的模式可以幫助。</span><span class="sxs-lookup"><span data-stu-id="a5a74-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="a5a74-132">Durable Functions 可讓彈性的排程間隔、 存留期管理，和從單一的協調流程函式的多個監視器處理序的建立。</span><span class="sxs-lookup"><span data-stu-id="a5a74-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="a5a74-133">這項功能的其中一個使用案例就是建立監看員在符合特定的臨界值之後完成的股票價格變更。</span><span class="sxs-lookup"><span data-stu-id="a5a74-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="a5a74-134">`DurableOrchestrationContext``CreateTimer`方法檢查股票價格變更會設定迴圈的下一個引動過程的排程。</span><span class="sxs-lookup"><span data-stu-id="a5a74-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="a5a74-135">`DurableOrchestrationContext` 也有`CurrentUtcDateTime`屬性來取得目前的日期時間值以 utc 格式。</span><span class="sxs-lookup"><span data-stu-id="a5a74-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="a5a74-136">最好是使用這個屬性，而不是`DateTime.UtcNow`因為它輕鬆地模擬 （mock） 進行測試。</span><span class="sxs-lookup"><span data-stu-id="a5a74-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="a5a74-137">建議的資源</span><span class="sxs-lookup"><span data-stu-id="a5a74-137">Recommended resources</span></span>

* [<span data-ttu-id="a5a74-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="a5a74-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="a5a74-139">.NET Core 與 .NET Standard 中的單元測試</span><span class="sxs-lookup"><span data-stu-id="a5a74-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="a5a74-140">[上一頁](durable-azure-functions.md)
>[下一頁](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="a5a74-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>