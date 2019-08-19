---
title: 協調流程模式-無伺服器應用程式
description: Azure 長期函數 pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 18e13c5355490ef4a019ceda459114bdb6bfd539
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577401"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="ef9fc-103">協調流程模式</span><span class="sxs-lookup"><span data-stu-id="ef9fc-103">Orchestration patterns</span></span>

<span data-ttu-id="ef9fc-104">Durable Functions 可讓您更輕鬆地建立可設定狀態的工作流程, 其中包含無伺服器環境中的離散、長時間執行活動。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="ef9fc-105">由於 Durable Functions 可以追蹤您工作流程的進度, 並定期檢查執行歷程記錄, 因此它本身就能執行一些有趣的模式。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="ef9fc-106">函數鏈</span><span class="sxs-lookup"><span data-stu-id="ef9fc-106">Function chaining</span></span>

<span data-ttu-id="ef9fc-107">在一般的順序程式中, 活動必須以特定順序逐一執行。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="ef9fc-108">(選擇性) 近期的活動可能需要先前函式的一些輸出。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="ef9fc-109">這項對活動順序的相依性會建立執行的函式鏈。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="ef9fc-110">使用 Durable Functions 來執行此工作流程模式的優點, 在於它的執行檢查點功能。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="ef9fc-111">如果伺服器當機、網路超時或發生其他問題, 長期函式會從上次已知狀態繼續, 並繼續執行您的工作流程, 即使它位於另一部伺服器上也一樣。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="ef9fc-112">在上述程式碼範例中, `CallActivityAsync`函式會負責在資料中心的虛擬機器上執行指定的活動。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="ef9fc-113">當 await 傳回且基礎工作完成時, 會將執行記錄到歷程記錄資料表。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="ef9fc-114">協調器函式中的程式碼可利用工作平行程式庫的任何熟悉結構和 async/await 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="ef9fc-115">下列程式碼是`ProcessPayment`方法可能外觀的簡化範例:</span><span class="sxs-lookup"><span data-stu-id="ef9fc-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="ef9fc-116">非同步 HTTP Api</span><span class="sxs-lookup"><span data-stu-id="ef9fc-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="ef9fc-117">在某些情況下, 工作流程可能會包含需要相當長一段時間才能完成的活動。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="ef9fc-118">假設有一個處理常式, 會將媒體檔案備份到 blob 儲存體中。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="ef9fc-119">視媒體檔案的大小和數量而定, 此備份程式可能需要數小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="ef9fc-120">在此案例中, `DurableOrchestrationClient`檢查執行中工作流程狀態的功能會變得很有用。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="ef9fc-121">當使用`HttpTrigger`來啟動工作流程時`CreateCheckStatusResponse` , 可以使用方法`HttpResponseMessage`來傳回的實例。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="ef9fc-122">此回應會在承載中提供具有 URI 的用戶端, 可用來檢查執行中進程的狀態。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="ef9fc-123">下面的範例結果顯示回應承載的結構。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="ef9fc-124">使用您慣用的 HTTP 用戶端時, 可以對 statusQueryGetUri 中的 URI 提出 GET 要求, 以檢查執行中工作流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="ef9fc-125">傳回的狀態回應應如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="ef9fc-126">當程式繼續進行時, 狀態回應會變更為 [**失敗**] 或 [**已完成**]。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="ef9fc-127">成功完成時, 裝載中的**輸出**屬性會包含任何傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="ef9fc-128">監視</span><span class="sxs-lookup"><span data-stu-id="ef9fc-128">Monitoring</span></span>

<span data-ttu-id="ef9fc-129">對於簡單的週期性工作, Azure Functions 會`TimerTrigger`提供可根據 CRON 運算式排程的。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="ef9fc-130">計時器適用于簡單、短期的工作, 但在某些情況下, 也可能需要更具彈性的排程。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="ef9fc-131">此案例是監視模式和 Durable Functions 可提供協助的時機。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="ef9fc-132">Durable Functions 可提供彈性的排程間隔、存留期管理, 以及從單一協調流程功能建立多個監視器進程。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="ef9fc-133">這項功能的其中一個使用案例, 可能是建立在符合特定閾值後才會完成的股票價格變更監看員。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="ef9fc-134">`DurableOrchestrationContext`的`CreateTimer`方法會設定下一個叫用迴圈的排程, 以檢查股票價格變更。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="ef9fc-135">`DurableOrchestrationContext`也有`CurrentUtcDateTime`屬性可取得目前的日期時間值 (以 UTC 表示)。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="ef9fc-136">最好是使用這個屬性, 而不是`DateTime.UtcNow` , 因為它很容易模擬以進行測試。</span><span class="sxs-lookup"><span data-stu-id="ef9fc-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="ef9fc-137">建議的資源</span><span class="sxs-lookup"><span data-stu-id="ef9fc-137">Recommended resources</span></span>

* [<span data-ttu-id="ef9fc-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="ef9fc-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="ef9fc-139">.NET Core 與 .NET Standard 中的單元測試</span><span class="sxs-lookup"><span data-stu-id="ef9fc-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="ef9fc-140">[上一頁](durable-azure-functions.md)
>[下一頁](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="ef9fc-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
