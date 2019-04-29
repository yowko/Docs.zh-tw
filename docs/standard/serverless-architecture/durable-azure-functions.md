---
title: 持久的 Azure functions-無伺服器應用程式
description: 持久的 Azure functions 會擴充的 Azure Functions 執行階段，以啟用程式碼中的具狀態工作流程。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8ad354e1708eb88f016130f8235f534b967eb122
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776008"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="5b435-103">永久的 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="5b435-103">Durable Azure functions</span></span>

<span data-ttu-id="5b435-104">當使用 Azure Functions 建立無伺服器應用程式，您的作業將通常設計成無狀態的方式執行。</span><span class="sxs-lookup"><span data-stu-id="5b435-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="5b435-105">這種設計選擇的原因是因為平台的規模而調整，但是很難知道哪些伺服器執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5b435-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="5b435-106">也就很難知道多少個執行個體是在任何指定的時間點作用中。</span><span class="sxs-lookup"><span data-stu-id="5b435-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="5b435-107">不過，有一些需要知道處理程序的目前狀態的應用程式的類別。</span><span class="sxs-lookup"><span data-stu-id="5b435-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="5b435-108">請考慮提交訂單的線上商店的程序。</span><span class="sxs-lookup"><span data-stu-id="5b435-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="5b435-109">簽出作業可能需要知道處理序狀態的多個作業所組成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="5b435-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="5b435-110">這類資訊可能包含產品存貨，如果客戶有任何信用額度他們的帳戶，以及處理信用卡的結果。</span><span class="sxs-lookup"><span data-stu-id="5b435-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="5b435-111">這些作業很可能他們自己的內部工作流程或甚至是協力廠商系統服務。</span><span class="sxs-lookup"><span data-stu-id="5b435-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="5b435-112">各種模式現存內部和外部系統之間的應用程式狀態的協調輔助。</span><span class="sxs-lookup"><span data-stu-id="5b435-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="5b435-113">您常會遇到需要集中式的佇列系統、 分散式的索引鍵-值存放區或共用的資料庫，以管理該狀態的解決方案。</span><span class="sxs-lookup"><span data-stu-id="5b435-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="5b435-114">不過，這些是現在需要佈建和管理的所有其他資源。</span><span class="sxs-lookup"><span data-stu-id="5b435-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="5b435-115">在無伺服器環境中，您的程式碼可能會很麻煩嘗試以手動方式協調與這些資源。</span><span class="sxs-lookup"><span data-stu-id="5b435-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="5b435-116">Azure Functions 提供建立稱為 「 長期函式的具狀態函式的替代方式。</span><span class="sxs-lookup"><span data-stu-id="5b435-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="5b435-117">Durable Functions 是 Azure Functions 執行階段，讓您的程式碼中的具狀態工作流程定義的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="5b435-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="5b435-118">細分成活動的工作流程，Durable Functions 擴充功能可以管理狀態、 建立進度的檢查點，以及在伺服器之間處理函式呼叫的分佈。</span><span class="sxs-lookup"><span data-stu-id="5b435-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="5b435-119">在背景中，它會使用 Azure 儲存體帳戶來保存執行歷程記錄、 排程活動函式，並擷取回應。</span><span class="sxs-lookup"><span data-stu-id="5b435-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="5b435-120">您的無伺服器程式碼與保存的資訊，儲存體帳戶，應該永遠不會互動，並通常並不是開發人員需要互動。</span><span class="sxs-lookup"><span data-stu-id="5b435-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="5b435-121">觸發具狀態的工作流程</span><span class="sxs-lookup"><span data-stu-id="5b435-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="5b435-122">Durable Functions 中的具狀態工作流程可以細分成兩個內建元件;協調流程和活動觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5b435-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="5b435-123">觸發程序和繫結是 Azure Functions 可讓您啟動、 收到輸入，並傳回結果時收到通知的無伺服器函式的核心元件。</span><span class="sxs-lookup"><span data-stu-id="5b435-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="5b435-124">使用 協調流程用戶端</span><span class="sxs-lookup"><span data-stu-id="5b435-124">Working with the Orchestration client</span></span>

<span data-ttu-id="5b435-125">協調流程是唯一，相較於在 Azure Functions 中觸發作業的其他樣式。</span><span class="sxs-lookup"><span data-stu-id="5b435-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="5b435-126">Durable Functions 可讓函式，可能需要幾小時甚至幾天才能完成執行。</span><span class="sxs-lookup"><span data-stu-id="5b435-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="5b435-127">該類型是行為的必須能夠檢查執行中協調流程的狀態，提前結束，或傳送的外部事件通知。</span><span class="sxs-lookup"><span data-stu-id="5b435-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="5b435-128">Durable Functions 擴充功能會提供這種情況下，`DurableOrchestrationClient`類別，可讓您與互動協調函式。</span><span class="sxs-lookup"><span data-stu-id="5b435-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="5b435-129">使用協調流程用戶端取得存取`OrchestrationClientAttribute`繫結。</span><span class="sxs-lookup"><span data-stu-id="5b435-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="5b435-130">一般而言，您會加入此屬性與另一個觸發程序類型，例如`HttpTrigger`或`ServiceBusTrigger`。</span><span class="sxs-lookup"><span data-stu-id="5b435-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="5b435-131">一旦已觸發來源函式，協調流程用戶端可用來啟動協調器函式。</span><span class="sxs-lookup"><span data-stu-id="5b435-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="5b435-132">協調器函式</span><span class="sxs-lookup"><span data-stu-id="5b435-132">The orchestrator function</span></span>

<span data-ttu-id="5b435-133">註解的函式搭配 Azure Functions 標示 OrchestrationTriggerAttribute 該函式為協調器函式。</span><span class="sxs-lookup"><span data-stu-id="5b435-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="5b435-134">它會負責管理您可設定狀態的工作流程所構成的各種活動。</span><span class="sxs-lookup"><span data-stu-id="5b435-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="5b435-135">協調器函式都無法使用的繫結 OrchestrationTriggerAttribute 以外。</span><span class="sxs-lookup"><span data-stu-id="5b435-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="5b435-136">這個屬性只可以搭配 DurableOrchestrationContext 參數類型。</span><span class="sxs-lookup"><span data-stu-id="5b435-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="5b435-137">可以不使用任何其他輸入，因為不支援的輸入函式簽章中還原序列化。</span><span class="sxs-lookup"><span data-stu-id="5b435-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="5b435-138">若要取得協調流程用戶端，GetInput 所提供的輸入\<T\>必須使用的方法。</span><span class="sxs-lookup"><span data-stu-id="5b435-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="5b435-139">此外，協調流程函式的傳回型別必須是 void、 工作或 JSON 可序列化的值。</span><span class="sxs-lookup"><span data-stu-id="5b435-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="5b435-140">*為求簡單明瞭的錯誤處理程式碼省略了*</span><span class="sxs-lookup"><span data-stu-id="5b435-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="5b435-141">在同一時間可以啟動並執行多個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="5b435-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="5b435-142">呼叫`StartNewAsync`方法`DurableOrchestrationClient`啟動協調流程的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="5b435-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="5b435-143">此方法會傳回`Task<string>`完成協調流程已啟動。</span><span class="sxs-lookup"><span data-stu-id="5b435-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="5b435-144">類型的例外狀況`TimeoutException`取得擲回，如果協調流程沒有在 30 秒內啟動。</span><span class="sxs-lookup"><span data-stu-id="5b435-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="5b435-145">已完成`Task<string>`從`StartNewAsync`應該包含協調流程執行個體的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="5b435-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="5b435-146">這個執行個體識別碼可用來叫用該特定協調流程上的作業。</span><span class="sxs-lookup"><span data-stu-id="5b435-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="5b435-147">協調流程可以查詢的狀態，或傳送事件通知。</span><span class="sxs-lookup"><span data-stu-id="5b435-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="5b435-148">活動函式</span><span class="sxs-lookup"><span data-stu-id="5b435-148">The activity functions</span></span>

<span data-ttu-id="5b435-149">活動函式會取得一起包含協調流程函式來建立工作流程內的個別作業。</span><span class="sxs-lookup"><span data-stu-id="5b435-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="5b435-150">以下是其中大部分的實際工作也不會發生。</span><span class="sxs-lookup"><span data-stu-id="5b435-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="5b435-151">它們代表商務邏輯，長時間執行的處理程序和較大的解決方案拼圖。</span><span class="sxs-lookup"><span data-stu-id="5b435-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="5b435-152">`ActivityTriggerAttribute`用來標註函式參數的型別`DurableActivityContext`。</span><span class="sxs-lookup"><span data-stu-id="5b435-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="5b435-153">使用註解，會通知執行階段函式要用作活動函式。</span><span class="sxs-lookup"><span data-stu-id="5b435-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="5b435-154">使用擷取活動函式的輸入的值`GetInput<T>`方法的`DurableActivityContext`參數。</span><span class="sxs-lookup"><span data-stu-id="5b435-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="5b435-155">類似於協調流程函式，活動函式的傳回型別必須是 void、 工作或 JSON 可序列化的值。</span><span class="sxs-lookup"><span data-stu-id="5b435-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="5b435-156">取得在活動函式內擲回任何未處理例外狀況將會傳送至呼叫的協調器函式，並顯示`TaskFailedException`。</span><span class="sxs-lookup"><span data-stu-id="5b435-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="5b435-157">此時，錯誤可以捕捉及記錄在 orchestrator 中，並可重試活動的功能。</span><span class="sxs-lookup"><span data-stu-id="5b435-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="5b435-158">建議的資源</span><span class="sxs-lookup"><span data-stu-id="5b435-158">Recommended resources</span></span>

* [<span data-ttu-id="5b435-159">長期函式</span><span class="sxs-lookup"><span data-stu-id="5b435-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="5b435-160">Durable Functions 的繫結</span><span class="sxs-lookup"><span data-stu-id="5b435-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [<span data-ttu-id="5b435-161">Durable Functions 中管理執行個體</span><span class="sxs-lookup"><span data-stu-id="5b435-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="5b435-162">[上一頁](event-grid.md)
>[下一頁](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="5b435-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>