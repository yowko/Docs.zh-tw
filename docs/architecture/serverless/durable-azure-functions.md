---
title: 持久的 Azure 函式-無伺服器應用程式
description: 持久的 Azure 函式會擴充 Azure Functions 執行時間，以在程式碼中啟用具狀態工作流程。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522858"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="f9ae4-103">永久的 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="f9ae4-103">Durable Azure functions</span></span>

<span data-ttu-id="f9ae4-104">使用 Azure Functions 建立無伺服器應用程式時，您的作業通常會設計成以無狀態的方式執行。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="f9ae4-105">這種設計選擇的原因是因為平臺會調整，所以難以得知程式碼執行所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="f9ae4-106">此外，也很難以知道有多少實例在任何指定的時間點處於作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="f9ae4-107">不過，有些類別的應用程式需要已知進程的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="f9ae4-108">請考慮將訂單提交到線上商店的程式。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="f9ae4-109">簽出作業可能是由多個需要知道進程狀態的作業所組成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="f9ae4-110">這類資訊可能包括產品清查、客戶的帳戶上是否有任何信用額度，還有處理信用卡的結果。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="f9ae4-111">這些作業很容易就是自己的內部工作流程，甚至是協力廠商系統的服務。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="f9ae4-112">目前有各種模式可協助協調內部和外部系統之間的應用程式狀態。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="f9ae4-113">在依賴集中式佇列系統、分散式索引鍵/值存放區或共用資料庫來管理該狀態的解決方案中，通常會有這種情況。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="f9ae4-114">不過，這些都是現在需要布建和管理的其他資源。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="f9ae4-115">在無伺服器環境中，您的程式碼可能會變得麻煩地嘗試與這些資源手動協調。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="f9ae4-116">Azure Functions 提供建立名為 Durable Functions 的具狀態函式的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="f9ae4-117">Durable Functions 是 Azure Functions 執行時間的延伸模組，可讓您在程式碼中定義具狀態工作流程。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="f9ae4-118">藉由將工作流程分解成活動，Durable Functions 擴充功能可以管理狀態、建立進度檢查點，以及處理跨伺服器的函式呼叫分佈。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="f9ae4-119">在背景中，它會使用 Azure 儲存體帳戶來保存執行歷程記錄、排程活動函式，以及取得回應。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="f9ae4-120">您的無伺服器程式碼應該永遠不會與該儲存體帳戶中的保存資訊互動，而且通常不是開發人員需要互動的東西。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="f9ae4-121">觸發具狀態工作流程</span><span class="sxs-lookup"><span data-stu-id="f9ae4-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="f9ae4-122">Durable Functions 中可設定狀態的工作流程可以分成兩個內部元件;協調流程和活動觸發程式。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="f9ae4-123">觸發程式和系結是 Azure Functions 所使用的核心元件，可讓您的無伺服器函式在啟動、接收輸入和傳回結果時收到通知。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="f9ae4-124">使用協調流程用戶端</span><span class="sxs-lookup"><span data-stu-id="f9ae4-124">Working with the Orchestration client</span></span>

<span data-ttu-id="f9ae4-125">相較于 Azure Functions 中的其他已觸發作業樣式，協調流程是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="f9ae4-126">Durable Functions 可執行可能需要數小時或甚至數天才能完成的函式。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="f9ae4-127">該類型的行為需要能夠檢查執行中協調流程的狀態、事先終止，或傳送外來事件的通知。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="f9ae4-128">在這種情況下，Durable Functions 擴充功能會提供 `DurableOrchestrationClient` 類別，讓您能夠與協調的函式互動。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="f9ae4-129">您可以使用 `OrchestrationClientAttribute` 系結取得協調流程用戶端的存取權。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="f9ae4-130">一般來說，您會將此屬性包含在另一個觸發程式類型，例如 `HttpTrigger` 或 `ServiceBusTrigger`。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="f9ae4-131">一旦觸發了來源函式，就可以使用協調流程用戶端來啟動協調器函數。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="f9ae4-132">協調器函式</span><span class="sxs-lookup"><span data-stu-id="f9ae4-132">The orchestrator function</span></span>

<span data-ttu-id="f9ae4-133">使用 Azure Functions 標記中的 OrchestrationTriggerAttribute 來標注函式，以作為協調器函數。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="f9ae4-134">負責管理組成具狀態工作流程的各種活動。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="f9ae4-135">協調器函式無法利用 OrchestrationTriggerAttribute 以外的系結。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="f9ae4-136">這個屬性只能搭配 DurableOrchestrationCoNtext 的參數類型使用。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="f9ae4-137">因為不支援在函式簽章中的輸入還原序列化，所以不能使用其他輸入。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="f9ae4-138">若要取得協調流程用戶端所提供的輸入，必須使用 Getinput t>\<T\> 方法。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="f9ae4-139">此外，協調流程函式的傳回類型必須是 void、Task 或 JSON 可序列化的值。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="f9ae4-140">*為了簡潔起見，已省略錯誤處理常式代碼*</span><span class="sxs-lookup"><span data-stu-id="f9ae4-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="f9ae4-141">協調流程的多個實例可以同時啟動和執行。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="f9ae4-142">在 `DurableOrchestrationClient` 上呼叫 `StartNewAsync` 方法會啟動協調流程的新實例。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="f9ae4-143">方法會傳回在協調流程啟動時完成的 `Task<string>`。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="f9ae4-144">如果協調流程未在30秒內啟動，則會擲回 `TimeoutException` 類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="f9ae4-145">從 `StartNewAsync` 完成的 `Task<string>` 應該包含協調流程實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="f9ae4-146">此實例識別碼可用來叫用該特定協調流程上的作業。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="f9ae4-147">可以查詢協調流程中的狀態或已傳送的事件通知。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="f9ae4-148">活動函式</span><span class="sxs-lookup"><span data-stu-id="f9ae4-148">The activity functions</span></span>

<span data-ttu-id="f9ae4-149">活動函式是離散作業，會在協調流程函數內一起撰寫以建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="f9ae4-150">以下是大部分實際工作發生的地方。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="f9ae4-151">它們代表商務邏輯、長時間執行的程式，以及更大的解決方案的拼圖片段。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="f9ae4-152">`ActivityTriggerAttribute` 可用來標注 `DurableActivityContext`類型的函數參數。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="f9ae4-153">使用批註會通知執行時間函式要當做活動函數使用。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="f9ae4-154">使用 `DurableActivityContext` 參數的 `GetInput<T>` 方法來抓取活動函式的輸入值。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="f9ae4-155">與協調流程函式類似，活動函式的傳回類型必須是 void、Task 或 JSON 可序列化的值。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="f9ae4-156">任何在活動函式中擲回的未處理例外狀況，都會傳送至呼叫協調器函式，並以 `TaskFailedException`形式呈現。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="f9ae4-157">此時，可能會攔截到錯誤並記錄在協調器中，而且可以重試活動。</span><span class="sxs-lookup"><span data-stu-id="f9ae4-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="f9ae4-158">建議的資源</span><span class="sxs-lookup"><span data-stu-id="f9ae4-158">Recommended resources</span></span>

- [<span data-ttu-id="f9ae4-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="f9ae4-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="f9ae4-160">Durable Functions 的系結</span><span class="sxs-lookup"><span data-stu-id="f9ae4-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="f9ae4-161">管理 Durable Functions 中的實例</span><span class="sxs-lookup"><span data-stu-id="f9ae4-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="f9ae4-162">[上一頁](event-grid.md)
>[下一頁](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f9ae4-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
