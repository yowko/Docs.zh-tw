---
title: 耐用的 Azure 功能 - 無伺服器應用
description: 持久 Azure 函數擴展 Azure 函數運行時，以便在代碼中啟用有狀態的工作流。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522858"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="624ad-103">永久的 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="624ad-103">Durable Azure functions</span></span>

<span data-ttu-id="624ad-104">使用 Azure 函數創建無伺服器應用程式時，操作通常設計為以無狀態方式運行。</span><span class="sxs-lookup"><span data-stu-id="624ad-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="624ad-105">之所以選擇此設計，是因為隨著平臺的擴展，很難知道代碼在運行哪些伺服器。</span><span class="sxs-lookup"><span data-stu-id="624ad-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="624ad-106">也很難知道在任意給定點啟動了多少個實例。</span><span class="sxs-lookup"><span data-stu-id="624ad-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="624ad-107">但是，有些應用程式類需要已知的進程目前狀態。</span><span class="sxs-lookup"><span data-stu-id="624ad-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="624ad-108">考慮向線上商店提交訂單的過程。</span><span class="sxs-lookup"><span data-stu-id="624ad-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="624ad-109">簽出操作可能是一個工作流，由需要瞭解流程狀態的多個操作組成。</span><span class="sxs-lookup"><span data-stu-id="624ad-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="624ad-110">如果客戶帳戶上有任何積分，以及處理信用卡的結果，此類資訊可能包括產品庫存。</span><span class="sxs-lookup"><span data-stu-id="624ad-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="624ad-111">這些操作很容易成為它們自己的內部工作流，甚至是來自協力廠商系統的服務。</span><span class="sxs-lookup"><span data-stu-id="624ad-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="624ad-112">當今存在各種模式，有助於協調內部和外部系統之間的應用程式狀態。</span><span class="sxs-lookup"><span data-stu-id="624ad-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="624ad-113">通常遇到依賴集中式佇列系統、分散式金鑰值存儲或共用資料庫來管理該狀態的解決方案。</span><span class="sxs-lookup"><span data-stu-id="624ad-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="624ad-114">但是，這些都是現在需要預配和管理的其他資源。</span><span class="sxs-lookup"><span data-stu-id="624ad-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="624ad-115">在無伺服器環境中，嘗試手動與這些資源進行協調時，代碼可能會變得麻煩。</span><span class="sxs-lookup"><span data-stu-id="624ad-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="624ad-116">Azure 函數提供了創建稱為持久函數的有狀態函數的替代方法。</span><span class="sxs-lookup"><span data-stu-id="624ad-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="624ad-117">持久函數是 Azure 函數運行時的擴展，用於在代碼中定義有狀態工作流。</span><span class="sxs-lookup"><span data-stu-id="624ad-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="624ad-118">通過將工作流分解為活動，持久函數擴展可以管理狀態、創建進度檢查點和處理跨伺服器分發函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="624ad-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="624ad-119">在後臺，它利用 Azure 存儲帳戶來保留執行歷史記錄、計畫活動函數和檢索回應。</span><span class="sxs-lookup"><span data-stu-id="624ad-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="624ad-120">無伺服器代碼絕不應與該存儲帳戶中的持久資訊進行交互，並且通常不是開發人員需要與之交互的內容。</span><span class="sxs-lookup"><span data-stu-id="624ad-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="624ad-121">觸發有狀態的工作流</span><span class="sxs-lookup"><span data-stu-id="624ad-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="624ad-122">持久函數中的有狀態工作流可以分為兩個內在元件;業務流程和活動觸發器。</span><span class="sxs-lookup"><span data-stu-id="624ad-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="624ad-123">觸發器和綁定是 Azure 函數使用的核心元件，用於使無伺服器函數在啟動、接收輸入和返回結果時收到通知。</span><span class="sxs-lookup"><span data-stu-id="624ad-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="624ad-124">使用業務流程用戶端</span><span class="sxs-lookup"><span data-stu-id="624ad-124">Working with the Orchestration client</span></span>

<span data-ttu-id="624ad-125">與 Azure 函數中其他樣式的觸發操作相比，業務流程是唯一的。</span><span class="sxs-lookup"><span data-stu-id="624ad-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="624ad-126">持久功能允許執行可能需要數小時甚至數天才能完成的功能。</span><span class="sxs-lookup"><span data-stu-id="624ad-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="624ad-127">這種類型的行為需要能夠檢查正在運行的業務流程的狀態、先發制人地終止或發送外來事件的通知。</span><span class="sxs-lookup"><span data-stu-id="624ad-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="624ad-128">在這種情況下，持久函數擴展提供允許您與業務流程交互`DurableOrchestrationClient`的類。</span><span class="sxs-lookup"><span data-stu-id="624ad-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="624ad-129">您可以使用`OrchestrationClientAttribute`綁定訪問業務流程用戶端。</span><span class="sxs-lookup"><span data-stu-id="624ad-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="624ad-130">通常，您將此屬性包含為另一個觸發器類型，如 或`HttpTrigger``ServiceBusTrigger`。</span><span class="sxs-lookup"><span data-stu-id="624ad-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="624ad-131">觸發源函數後，業務流程用戶端可用於啟動協調器函數。</span><span class="sxs-lookup"><span data-stu-id="624ad-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a><span data-ttu-id="624ad-132">協調器功能</span><span class="sxs-lookup"><span data-stu-id="624ad-132">The orchestrator function</span></span>

<span data-ttu-id="624ad-133">在 Azure 函數中使用業務流程觸發器屬性對函數進行標記標記，該函數充當協調器函數。</span><span class="sxs-lookup"><span data-stu-id="624ad-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="624ad-134">它負責管理構成有狀態工作流的各種活動。</span><span class="sxs-lookup"><span data-stu-id="624ad-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="624ad-135">協調器函數無法使用業務流程觸發器屬性以外的綁定。</span><span class="sxs-lookup"><span data-stu-id="624ad-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="624ad-136">此屬性只能與持久管弦上下文的參數類型一起使用。</span><span class="sxs-lookup"><span data-stu-id="624ad-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="624ad-137">由於不支援函數簽名中輸入的序列化，因此無法使用任何其他輸入。</span><span class="sxs-lookup"><span data-stu-id="624ad-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="624ad-138">要獲取業務流程用戶端提供的輸入，必須使用 GetInput\<T\>方法。</span><span class="sxs-lookup"><span data-stu-id="624ad-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="624ad-139">此外，業務流程函數的返回類型必須是 void、任務或 JSON 可序列化值。</span><span class="sxs-lookup"><span data-stu-id="624ad-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="624ad-140">*為了簡潔起見，錯誤處理代碼被遺漏了*</span><span class="sxs-lookup"><span data-stu-id="624ad-140">*Error handling code has been left out for brevity*</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="624ad-141">可以同時啟動和運行業務流程的多個實例。</span><span class="sxs-lookup"><span data-stu-id="624ad-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="624ad-142">在`StartNewAsync`調用 上`DurableOrchestrationClient`的方法將啟動業務流程的新實例。</span><span class="sxs-lookup"><span data-stu-id="624ad-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="624ad-143">該方法返回在業務流程`Task<string>`啟動時完成的 。</span><span class="sxs-lookup"><span data-stu-id="624ad-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="624ad-144">如果業務流程在`TimeoutException`30 秒內未啟動，則引發類型的異常。</span><span class="sxs-lookup"><span data-stu-id="624ad-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="624ad-145">已完成`Task<string>`的`StartNewAsync`應包含業務流程實例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="624ad-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="624ad-146">此實例 ID 可用於調用該特定業務流程的操作。</span><span class="sxs-lookup"><span data-stu-id="624ad-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="624ad-147">可以查詢業務流程的狀態或發送的事件通知。</span><span class="sxs-lookup"><span data-stu-id="624ad-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="624ad-148">活動功能</span><span class="sxs-lookup"><span data-stu-id="624ad-148">The activity functions</span></span>

<span data-ttu-id="624ad-149">活動函數是在業務流程函數中組合以創建工作流的離散操作。</span><span class="sxs-lookup"><span data-stu-id="624ad-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="624ad-150">這裡大多數實際工作將發生的地方。</span><span class="sxs-lookup"><span data-stu-id="624ad-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="624ad-151">它們表示業務邏輯、長時間運行的流程以及較大解決方案的拼圖。</span><span class="sxs-lookup"><span data-stu-id="624ad-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="624ad-152">`ActivityTriggerAttribute`用於批批類型`DurableActivityContext`中的函數參數。</span><span class="sxs-lookup"><span data-stu-id="624ad-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="624ad-153">使用注釋通知運行時該函數旨在用作活動函數。</span><span class="sxs-lookup"><span data-stu-id="624ad-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="624ad-154">使用`GetInput<T>``DurableActivityContext`參數的方法檢索活動函數的輸入值。</span><span class="sxs-lookup"><span data-stu-id="624ad-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="624ad-155">與業務流程函數類似，活動函數的返回類型必須是 void、任務或 JSON 可序列化值。</span><span class="sxs-lookup"><span data-stu-id="624ad-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="624ad-156">在活動函數中引發的任何未處理異常都將發送到調用協調器函數，並呈現為`TaskFailedException`。</span><span class="sxs-lookup"><span data-stu-id="624ad-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="624ad-157">此時，錯誤可以捕獲並記錄在協調器中，並且可以重試活動。</span><span class="sxs-lookup"><span data-stu-id="624ad-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="624ad-158">建議的資源</span><span class="sxs-lookup"><span data-stu-id="624ad-158">Recommended resources</span></span>

- [<span data-ttu-id="624ad-159">長期函式</span><span class="sxs-lookup"><span data-stu-id="624ad-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="624ad-160">持久函數綁定</span><span class="sxs-lookup"><span data-stu-id="624ad-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="624ad-161">在持久函數中管理實例</span><span class="sxs-lookup"><span data-stu-id="624ad-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="624ad-162">[上一個](event-grid.md)
>[下一個](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="624ad-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
