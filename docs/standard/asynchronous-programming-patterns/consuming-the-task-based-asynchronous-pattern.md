---
title: 使用以工作為基礎的非同步模式
description: 瞭解如何使用以工作為基礎的非同步模式 (在使用非同步作業時，請按) 。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET and TAP
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: 4a2715ab6572c33a1564986c5cfda112d5fa11db
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888863"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="3492e-103">使用以工作為基礎的非同步模式</span><span class="sxs-lookup"><span data-stu-id="3492e-103">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="3492e-104">當您使用以工作為基礎的非同步模式 (TAP) 執行非同步作業時，您可以使用回撥來達到等待而不封鎖。</span><span class="sxs-lookup"><span data-stu-id="3492e-104">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span> <span data-ttu-id="3492e-105">就工作而言，這可透過 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 之類的方法來達成。</span><span class="sxs-lookup"><span data-stu-id="3492e-105">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3492e-106">以語言為基礎的非同步支援允許非同步作業在正常控制流程中等候，以隱藏回撥，而編譯器產生的程式碼提供這種相同的 API 層級支援。</span><span class="sxs-lookup"><span data-stu-id="3492e-106">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="3492e-107">使用 Await 暫停執行</span><span class="sxs-lookup"><span data-stu-id="3492e-107">Suspending Execution with Await</span></span>

<span data-ttu-id="3492e-108">您可以在 c # 中使用 [await](../../csharp/language-reference/operators/await.md) 關鍵字，並在 Visual Basic 中使用 [await 運算子](../../visual-basic/language-reference/operators/await-operator.md) ，以非同步方式 await <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="3492e-108">You can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="3492e-109">當您等候的是 <xref:System.Threading.Tasks.Task> 時，`await` 運算式的類型會是 `void`。</span><span class="sxs-lookup"><span data-stu-id="3492e-109">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="3492e-110">當您等候的是 <xref:System.Threading.Tasks.Task%601> 時，`await` 運算式的類型會是 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="3492e-110">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="3492e-111">`await` 運算式必須發生在非同步方法的主體內。</span><span class="sxs-lookup"><span data-stu-id="3492e-111">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="3492e-112">這些語言功能 (在 .NET Framework 4.5 中引進。 ) </span><span class="sxs-lookup"><span data-stu-id="3492e-112">(These language features were introduced in .NET Framework 4.5.)</span></span>

 <span data-ttu-id="3492e-113">實際上，等候功能會使用接續在工作上安裝回撥。</span><span class="sxs-lookup"><span data-stu-id="3492e-113">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="3492e-114">此回撥會從暫止點繼續非同步方法。</span><span class="sxs-lookup"><span data-stu-id="3492e-114">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="3492e-115">當非同步方法繼續時，如果等候的作業順利完成，而且是 <xref:System.Threading.Tasks.Task%601>，就會傳回其 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="3492e-115">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="3492e-116">如果所等候的 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 以 <xref:System.Threading.Tasks.TaskStatus.Canceled> 狀態結束，則會擲回 <xref:System.OperationCanceledException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3492e-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="3492e-117">如果所等候的 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 以 <xref:System.Threading.Tasks.TaskStatus.Faulted> 狀態結束，則會擲回造成它發生錯誤的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3492e-117">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="3492e-118">`Task` 會因為多個例外狀況而錯誤，但只會傳播其中一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3492e-118">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="3492e-119">不過，<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 屬性會傳回包含所有錯誤的 <xref:System.AggregateException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3492e-119">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="3492e-120">如果同步處理內容 (<xref:System.Threading.SynchronizationContext> 物件) 與暫止時正在執行非同步方法的執行緒相關聯 (例如，如果 <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> 不 `null`) 屬性，則非同步方法會使用內容的方法繼續執行相同的同步處理內容 <xref:System.Threading.SynchronizationContext.Post%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3492e-120">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context's <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="3492e-121">否則，它會依賴暫止時當前的工作排程器 (<xref:System.Threading.Tasks.TaskScheduler> 物件)。</span><span class="sxs-lookup"><span data-stu-id="3492e-121">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="3492e-122">通常，這會是以執行緒集區為目標的預設工作排程器 (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="3492e-122">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="3492e-123">這個工作排程器決定等候的非同步作業是否應該在完成處繼續，還是應該排定繼續。</span><span class="sxs-lookup"><span data-stu-id="3492e-123">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="3492e-124">預設排程器通常允許在完成等候作業的執行緒上接續執行。</span><span class="sxs-lookup"><span data-stu-id="3492e-124">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="3492e-125">呼叫非同步方法時會同步執行函式主體，直到尚未完成的可等候執行個體上的第一個 await 運算式為止，此時引動過程會返回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3492e-125">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="3492e-126">如果非同步方法並未傳回 `void`，則會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件來代表進行中的計算。</span><span class="sxs-lookup"><span data-stu-id="3492e-126">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="3492e-127">在非 void 非同步方法中，如果遇到 return 陳述式或到達方法主體的結尾，工作會以 <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> 最終狀態完成。</span><span class="sxs-lookup"><span data-stu-id="3492e-127">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="3492e-128">如果未處理的例外狀況導致控制權離開非同步方法的主體，工作則會以 <xref:System.Threading.Tasks.TaskStatus.Faulted> 狀態結束。</span><span class="sxs-lookup"><span data-stu-id="3492e-128">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="3492e-129">如果例外狀況是 <xref:System.OperationCanceledException>，工作就會變成在 <xref:System.Threading.Tasks.TaskStatus.Canceled> 狀態下結束。</span><span class="sxs-lookup"><span data-stu-id="3492e-129">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="3492e-130">就這樣，最後會發佈結果或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3492e-130">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="3492e-131">此行為有數個重要的變化。</span><span class="sxs-lookup"><span data-stu-id="3492e-131">There are several important variations of this behavior.</span></span>  <span data-ttu-id="3492e-132">基於效能考量，如果工作在開始等候之前已完成，則不會讓出控制權，函式會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="3492e-132">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="3492e-133">此外，返回原始內容不一見得是想要的行為，可以變更；下一節會詳細說明。</span><span class="sxs-lookup"><span data-stu-id="3492e-133">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="3492e-134">使用 Yield 和 ConfigureAwait 設定暫止和繼續</span><span class="sxs-lookup"><span data-stu-id="3492e-134">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="3492e-135">有數種方法可讓您更充分掌控非同步方法的執行。</span><span class="sxs-lookup"><span data-stu-id="3492e-135">Several methods provide more control over an asynchronous method's execution.</span></span> <span data-ttu-id="3492e-136">例如，您可以使用 <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> 方法在非同步方法的中導入 Yield 點：</span><span class="sxs-lookup"><span data-stu-id="3492e-136">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="3492e-137">這相當於以非同步方式往回張貼或排定到目前的內容。</span><span class="sxs-lookup"><span data-stu-id="3492e-137">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="3492e-138">您也可以使用 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 方法，更充分掌控非同步方法中的暫止和繼續。</span><span class="sxs-lookup"><span data-stu-id="3492e-138">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="3492e-139">如先前所述，根據預設，當非同步方法暫停時，會捕捉到目前的內容，並在繼續時使用捕捉的內容叫用非同步方法的接續。</span><span class="sxs-lookup"><span data-stu-id="3492e-139">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method's continuation upon resumption.</span></span>  <span data-ttu-id="3492e-140">在許多情況下，這就是您想要的行為。</span><span class="sxs-lookup"><span data-stu-id="3492e-140">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="3492e-141">在其他情況下，您可能不在意接續內容，您可以避免這樣往回張貼到原始內容，以達到更高效能。</span><span class="sxs-lookup"><span data-stu-id="3492e-141">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="3492e-142">若要這樣做，請使用 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 方法來告知等候作業不要在內容上擷取和繼續，而是只要所等候的非同步作業完成，就繼續執行︰</span><span class="sxs-lookup"><span data-stu-id="3492e-142">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="3492e-143">取消非同步作業</span><span class="sxs-lookup"><span data-stu-id="3492e-143">Canceling an Asynchronous Operation</span></span>

<span data-ttu-id="3492e-144">從 .NET Framework 4 開始，請按一下支援取消的方法，至少提供一個可接受解除標記的多載 (<xref:System.Threading.CancellationToken> 物件) 。</span><span class="sxs-lookup"><span data-stu-id="3492e-144">Starting with .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="3492e-145">建立取消權杖時，會透過某個取消權杖來源 (<xref:System.Threading.CancellationTokenSource> 物件) 來建立。</span><span class="sxs-lookup"><span data-stu-id="3492e-145">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="3492e-146">來源的 <xref:System.Threading.CancellationTokenSource.Token%2A> 屬性會傳回呼叫來源的方法時，將會收到通知的解除標記 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3492e-146">The source's <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="3492e-147">例如，如果您想要下載單一網頁，而且想要能夠取消此作業，請建立一個 <xref:System.Threading.CancellationTokenSource> 物件，將它的權杖傳遞給點一下方法，然後在 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 您準備好要取消作業時呼叫來源的方法：</span><span class="sxs-lookup"><span data-stu-id="3492e-147">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="3492e-148">若要取消多個非同步引動過程，您可以將相同的語彙基元傳遞至所有引動過程︰</span><span class="sxs-lookup"><span data-stu-id="3492e-148">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="3492e-149">或者，您可以將相同的語彙基元傳遞至一組經過挑選的作業︰</span><span class="sxs-lookup"><span data-stu-id="3492e-149">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="3492e-150">任何執行緒都可能起始取消要求。</span><span class="sxs-lookup"><span data-stu-id="3492e-150">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="3492e-151">您可以將 <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> 值傳遞給任何接受取消權杖的方法，以表示永遠不要求取消作業。</span><span class="sxs-lookup"><span data-stu-id="3492e-151">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="3492e-152">這會導致 <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> 屬性傳回 `false`，而可相應地將所呼叫的方法最佳化。</span><span class="sxs-lookup"><span data-stu-id="3492e-152">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="3492e-153">在測試時，您也可以傳入以建構函式具現化之預先取消的取消語彙基元，此建構函式接受布林值，以指出語彙基元最初應該處於已取消或不可取消狀態。</span><span class="sxs-lookup"><span data-stu-id="3492e-153">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="3492e-154">這種取消方法有幾項優點︰</span><span class="sxs-lookup"><span data-stu-id="3492e-154">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="3492e-155">您可以將相同的取消語彙基元傳遞至任何數目的非同步和同步作業。</span><span class="sxs-lookup"><span data-stu-id="3492e-155">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="3492e-156">相同的取消要求可以擴散至任何數目的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3492e-156">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="3492e-157">非同步 API 的開發人員可以完全控制是否可要求取消及何時生效。</span><span class="sxs-lookup"><span data-stu-id="3492e-157">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="3492e-158">使用 API 的程式碼可能選擇性地決定要將取消要求傳播至其中的非同步引動過程。</span><span class="sxs-lookup"><span data-stu-id="3492e-158">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="3492e-159">監視進度</span><span class="sxs-lookup"><span data-stu-id="3492e-159">Monitoring Progress</span></span>
 <span data-ttu-id="3492e-160">某些非同步方法會透過傳遞至非同步方法的進度介面來公開進度。</span><span class="sxs-lookup"><span data-stu-id="3492e-160">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="3492e-161">例如，請考慮以非同步方式下載文字字串的函式，以及引發進度更新，包括截至目前為止已完成的下載百分比。</span><span class="sxs-lookup"><span data-stu-id="3492e-161">For example, consider a function that asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="3492e-162">Windows Presentation Foundation (WPF) 應用程式中可以使用這種方法，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="3492e-162">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="3492e-163">使用內建以工作為基礎的組合器</span><span class="sxs-lookup"><span data-stu-id="3492e-163">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="3492e-164"><xref:System.Threading.Tasks> 命名空間包含數個用於撰寫和處理工作的方式。</span><span class="sxs-lookup"><span data-stu-id="3492e-164">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="3492e-165">Task.Run</span><span class="sxs-lookup"><span data-stu-id="3492e-165">Task.Run</span></span>
 <span data-ttu-id="3492e-166"><xref:System.Threading.Tasks.Task>類別包含數個 <xref:System.Threading.Tasks.Task.Run%2A> 方法，可讓您輕鬆地將工作以 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的形式卸載至執行緒集區，例如：</span><span class="sxs-lookup"><span data-stu-id="3492e-166">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="3492e-167">這些 <xref:System.Threading.Tasks.Task.Run%2A> 方法中有些 (例如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> 多載) 會作為 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法的速記。</span><span class="sxs-lookup"><span data-stu-id="3492e-167">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="3492e-168">其他多載 (例如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>) 則可讓您在所卸載的工作中使用 await，例如：</span><span class="sxs-lookup"><span data-stu-id="3492e-168">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="3492e-169">這類多載在邏輯上等同於使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法搭配「工作平行程式庫」中的 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="3492e-169">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="3492e-170">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="3492e-170">Task.FromResult</span></span>
 <span data-ttu-id="3492e-171">在可能已有資料可用，而只需從放在 <xref:System.Threading.Tasks.Task%601> 中的工作傳回方法傳回的情況下，請使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="3492e-171">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="3492e-172">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="3492e-172">Task.WhenAll</span></span>
 <span data-ttu-id="3492e-173">請使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法，以非同步方式等候多個以工作表示的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="3492e-173">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="3492e-174">此方法有多個多載可支援一組非泛型工作或一組非統一泛型工作 (例如，非同步等候多個 void 傳回作業，或非同步等候多個值傳回方法，而每個值可能有不同型別)，也支援一組統一泛型工作 (例如，非同步等候多個 `TResult` 傳回方法)。</span><span class="sxs-lookup"><span data-stu-id="3492e-174">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="3492e-175">假設您想要將電子郵件訊息傳送給數個客戶。</span><span class="sxs-lookup"><span data-stu-id="3492e-175">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="3492e-176">您可以重疊傳送訊息，不必等待一個訊息完成才傳送下一個訊息。</span><span class="sxs-lookup"><span data-stu-id="3492e-176">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="3492e-177">您也可以查明傳送作業何時完成及是否發生任何錯誤︰</span><span class="sxs-lookup"><span data-stu-id="3492e-177">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="3492e-178">以下程式碼不會明確處理可能發生的例外狀況，而是會在 <xref:System.Threading.Tasks.Task.WhenAll%2A> 產生的工作上，讓例外狀況從 `await` 傳播出來。</span><span class="sxs-lookup"><span data-stu-id="3492e-178">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="3492e-179">若要處理例外狀況，您可以使用下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="3492e-179">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="3492e-180">在此案例中，如果任何非同步作業失敗，所有例外狀況會合併成一個 <xref:System.AggregateException> 例外狀況，並儲存在 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法所傳回的 <xref:System.Threading.Tasks.Task> 中。</span><span class="sxs-lookup"><span data-stu-id="3492e-180">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="3492e-181">不過，`await` 關鍵字只會傳播其中一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3492e-181">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="3492e-182">如果您想要檢查所有例外狀況，您可以改寫先前的程式碼，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="3492e-182">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="3492e-183">舉例說明，假設從 web 非同步下載多個檔案。</span><span class="sxs-lookup"><span data-stu-id="3492e-183">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="3492e-184">在此例子中，所有非同步作業有相同的結果型別，很容易存取結果︰</span><span class="sxs-lookup"><span data-stu-id="3492e-184">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="3492e-185">您可以使用我們在先前 void 傳回案例中討論過的相同例外狀況處理技術︰</span><span class="sxs-lookup"><span data-stu-id="3492e-185">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task<string> [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="3492e-186">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="3492e-186">Task.WhenAny</span></span>
 <span data-ttu-id="3492e-187">您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法，在多個以工作表示的非同步作業中，只以非同步方式等候其中一個完成。</span><span class="sxs-lookup"><span data-stu-id="3492e-187">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="3492e-188">這個方法適用於四種主要的使用案例：</span><span class="sxs-lookup"><span data-stu-id="3492e-188">This method serves four primary use cases:</span></span>

- <span data-ttu-id="3492e-189">備援：多次執行某項作業並選擇最先完成的作業 (例如，連絡多個會產生單一結果的提供股價報價服務的網站，並且選擇最快完成的那一個)。</span><span class="sxs-lookup"><span data-stu-id="3492e-189">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="3492e-190">交錯：啟動多項作業並等候所有作業完成，不過，會在作業完成時才進行處理。</span><span class="sxs-lookup"><span data-stu-id="3492e-190">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="3492e-191">節流：當作業完成時，允許其他作業開始。</span><span class="sxs-lookup"><span data-stu-id="3492e-191">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="3492e-192">這是交錯情節的擴充。</span><span class="sxs-lookup"><span data-stu-id="3492e-192">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="3492e-193">提早釋出：例如，工作 t1 代表的作業可以在 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作中與另一個工作 t2 合併成群組，然後您可以等候 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作。</span><span class="sxs-lookup"><span data-stu-id="3492e-193">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="3492e-194">工作 t2 可代表造成 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作比 t1 更早完成的逾時、取消或一些其他訊號。</span><span class="sxs-lookup"><span data-stu-id="3492e-194">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="3492e-195">備援性</span><span class="sxs-lookup"><span data-stu-id="3492e-195">Redundancy</span></span>
 <span data-ttu-id="3492e-196">假設您想決定是否購買股票。</span><span class="sxs-lookup"><span data-stu-id="3492e-196">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="3492e-197">您有好幾個信任的股票建議 Web 服務，不過依據每日負載，每個服務可能會在不同時間點變得很慢。</span><span class="sxs-lookup"><span data-stu-id="3492e-197">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="3492e-198">您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法來接收任何作業完成的通知：</span><span class="sxs-lookup"><span data-stu-id="3492e-198">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="3492e-199">不同於 <xref:System.Threading.Tasks.Task.WhenAll%2A> 會傳回所有成功完成之工作的未包裝結果，<xref:System.Threading.Tasks.Task.WhenAny%2A> 會傳回已完成的工作。</span><span class="sxs-lookup"><span data-stu-id="3492e-199">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="3492e-200">如果工作失敗，請務必知道它失敗，而且如果工作成功，就必須知道傳回值與之相關聯的工作。</span><span class="sxs-lookup"><span data-stu-id="3492e-200">If a task fails, it's important to know that it failed, and if a task succeeds, it's important to know which task the return value is associated with.</span></span>  <span data-ttu-id="3492e-201">因此，您需要存取所傳回工作的結果，或進一步等待，如這個範例所示。</span><span class="sxs-lookup"><span data-stu-id="3492e-201">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="3492e-202">與使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 時相同，您必須能夠通融例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3492e-202">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="3492e-203">因為您要收回已完成的工作，您可以等候傳回的工作傳播錯誤，並適當地 `try/catch`，例如︰</span><span class="sxs-lookup"><span data-stu-id="3492e-203">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="3492e-204">此外，即使第一個工作成功完成，後續工作可能失敗。</span><span class="sxs-lookup"><span data-stu-id="3492e-204">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="3492e-205">此時，您有幾個處理例外狀況的選項：您可以等待所有啟動的工作完成，在這種情況下，您可以使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法，或者您可以決定所有例外狀況都很重要，必須全部記錄。</span><span class="sxs-lookup"><span data-stu-id="3492e-205">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="3492e-206">對此，您可以使用接續，在工作完成時以非同步方式接收通知︰</span><span class="sxs-lookup"><span data-stu-id="3492e-206">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="3492e-207">或者：</span><span class="sxs-lookup"><span data-stu-id="3492e-207">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="3492e-208">或甚至︰</span><span class="sxs-lookup"><span data-stu-id="3492e-208">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="3492e-209">最後，您可能想要取消其餘所有作業︰</span><span class="sxs-lookup"><span data-stu-id="3492e-209">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="3492e-210">交錯</span><span class="sxs-lookup"><span data-stu-id="3492e-210">Interleaving</span></span>
 <span data-ttu-id="3492e-211">假設您從 web 下載影像並處理每個影像 (例如，將影像新增至 UI 控制項)。</span><span class="sxs-lookup"><span data-stu-id="3492e-211">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span> <span data-ttu-id="3492e-212">您會在 UI 執行緒上依序處理影像，但想要盡可能同時下載影像。</span><span class="sxs-lookup"><span data-stu-id="3492e-212">You process the images sequentially on the UI thread, but want to download the images as concurrently as possible.</span></span> <span data-ttu-id="3492e-213">此外，您也不想要將影像新增至 UI，直到全部下載完畢。</span><span class="sxs-lookup"><span data-stu-id="3492e-213">Also, you don't want to hold up adding the images to the UI until they're all downloaded.</span></span> <span data-ttu-id="3492e-214">相反地，您會想要在它們完成時新增它們。</span><span class="sxs-lookup"><span data-stu-id="3492e-214">Instead, you want to add them as they complete.</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="3492e-215">如果所下載影像的 <xref:System.Threading.ThreadPool> 上涉及密集運算處理，您也可以套用交錯，例如：</span><span class="sxs-lookup"><span data-stu-id="3492e-215">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="3492e-216">節流</span><span class="sxs-lookup"><span data-stu-id="3492e-216">Throttling</span></span>
 <span data-ttu-id="3492e-217">在交錯範例中，除非使用者下載太多影像，以至於必須節流下載。例如，您只想要同時進行一定數量的下載。</span><span class="sxs-lookup"><span data-stu-id="3492e-217">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="3492e-218">為了達到此目的，您可以先啟動一部分的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="3492e-218">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="3492e-219">當這些作業完成時，您可以再啟動另一批作業︰</span><span class="sxs-lookup"><span data-stu-id="3492e-219">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="3492e-220">提早脫離</span><span class="sxs-lookup"><span data-stu-id="3492e-220">Early Bailout</span></span>
 <span data-ttu-id="3492e-221">請考慮您正在以非同步方式等候作業完成，同時也能同時回應使用者的取消要求 (例如，使用者按一下 [取消] 按鈕) 。</span><span class="sxs-lookup"><span data-stu-id="3492e-221">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user's cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="3492e-222">下列程式碼說明這種情節：</span><span class="sxs-lookup"><span data-stu-id="3492e-222">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="3492e-223">當您決定脫離時，此實作會立即重新啟用使用者介面，但不取消幕後的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="3492e-223">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span> <span data-ttu-id="3492e-224">另一個替代方法是在您決定要退出時取消暫止的作業，但不會在作業完成之前重新建立使用者介面，可能是因為取消要求提早結束：</span><span class="sxs-lookup"><span data-stu-id="3492e-224">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="3492e-225">另一個提早釋出的例子涉及使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法搭配 <xref:System.Threading.Tasks.Task.Delay%2A> 方法，如下一節所述。</span><span class="sxs-lookup"><span data-stu-id="3492e-225">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="3492e-226">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="3492e-226">Task.Delay</span></span>
 <span data-ttu-id="3492e-227">您可以使用 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 方法，將暫停引入非同步方法的執行。</span><span class="sxs-lookup"><span data-stu-id="3492e-227">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method's execution.</span></span>  <span data-ttu-id="3492e-228">這適用於許多種功能，包括建置輪詢迴圈和將使用者輸入延遲一段預先定義的時間再處理。</span><span class="sxs-lookup"><span data-stu-id="3492e-228">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="3492e-229"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 與 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 搭配使用時也相當實用，可用來在等候上實作逾時。</span><span class="sxs-lookup"><span data-stu-id="3492e-229">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="3492e-230">如果屬於較大型非同步作業的工作 (例如，ASP.NET web 服務) 花費太多時間才能完成，則整體作業可能會受到影響，尤其是當它無法完成時。</span><span class="sxs-lookup"><span data-stu-id="3492e-230">If a task that's part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="3492e-231">基於這個理由，在等候非同步作業時，一定要能夠有時間。</span><span class="sxs-lookup"><span data-stu-id="3492e-231">For this reason, it's important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="3492e-232">同步的 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>及 <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> 方法可接受逾時值，但對應的 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 和先前提到的 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法則無法接受逾時值。</span><span class="sxs-lookup"><span data-stu-id="3492e-232">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="3492e-233">您可以改用 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 搭配 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 來實作逾時。</span><span class="sxs-lookup"><span data-stu-id="3492e-233">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="3492e-234">例如，在您的應用程式 UI 中，假設您想要下載影像，並於下載影像時停用 UI。</span><span class="sxs-lookup"><span data-stu-id="3492e-234">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="3492e-235">不過，如果下載的時間太長，您想要重新啟用 UI 並放棄下載︰</span><span class="sxs-lookup"><span data-stu-id="3492e-235">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="3492e-236">這同樣適用於多個下載，因為 <xref:System.Threading.Tasks.Task.WhenAll%2A> 會傳回工作：</span><span class="sxs-lookup"><span data-stu-id="3492e-236">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads.Result) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="3492e-237">建置以工作為基礎的組合器</span><span class="sxs-lookup"><span data-stu-id="3492e-237">Building Task-based Combinators</span></span>
 <span data-ttu-id="3492e-238">因為工作能夠完全代表非同步作業，並提供同步和非同步功能來聯結作業、擷取其結果等等，所以您可以建置實用的組合器程式庫，將工作組合以建置更大的模式。</span><span class="sxs-lookup"><span data-stu-id="3492e-238">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span> <span data-ttu-id="3492e-239">如上一節所述，.NET 包含數個內建的組合器，但您也可以建立自己的。</span><span class="sxs-lookup"><span data-stu-id="3492e-239">As discussed in the previous section, .NET includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="3492e-240">下列章節提供幾個範例說明可能的結合器方法和型別。</span><span class="sxs-lookup"><span data-stu-id="3492e-240">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="3492e-241">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="3492e-241">RetryOnFault</span></span>
 <span data-ttu-id="3492e-242">在許多情況下，您可能想要在作業前次嘗試失敗時重試。</span><span class="sxs-lookup"><span data-stu-id="3492e-242">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="3492e-243">在同步程式碼中，您可能建置協助程式方法來達到這個目的，例如下列範例中的 `RetryOnFault`︰</span><span class="sxs-lookup"><span data-stu-id="3492e-243">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="3492e-244">對於以 TAP 實作而傳回工作的非同步作業，您可以建置幾乎完全相同的協助程式方法：</span><span class="sxs-lookup"><span data-stu-id="3492e-244">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="3492e-245">然後，您可以使用此組合器，將重試編碼為應用程式的邏輯;例如：</span><span class="sxs-lookup"><span data-stu-id="3492e-245">You can then use this combinator to encode retries into the application's logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="3492e-246">您可以進一步擴充 `RetryOnFault` 函式。</span><span class="sxs-lookup"><span data-stu-id="3492e-246">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="3492e-247">例如，此函式可以接受另一個 `Func<Task>` 在重試之間叫用，以判斷何時再次嘗試，例如︰</span><span class="sxs-lookup"><span data-stu-id="3492e-247">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="3492e-248">然後，您可以如下所示使用此函式，先等待一秒再重試作業︰</span><span class="sxs-lookup"><span data-stu-id="3492e-248">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="3492e-249">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="3492e-249">NeedOnlyOne</span></span>
 <span data-ttu-id="3492e-250">有時候，您可以利用冗余來改善作業的延遲和成功的機會。</span><span class="sxs-lookup"><span data-stu-id="3492e-250">Sometimes, you can take advantage of redundancy to improve an operation's latency and chances for success.</span></span>  <span data-ttu-id="3492e-251">假設有多個 Web 服務在一天中的不同時間提供股票報價，每個服務可能提供不同的品質等級和回應時間。</span><span class="sxs-lookup"><span data-stu-id="3492e-251">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="3492e-252">為了因應這些變動，您可以發出要求給所有 Web 服務，只要從其中一個服務收到回應，就立刻取消其餘要求。</span><span class="sxs-lookup"><span data-stu-id="3492e-252">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="3492e-253">您可以實作協助程式函式，更輕鬆地實作這種常見模式，亦即啟動多項作業、等候任何回應，然後取消其餘作業。</span><span class="sxs-lookup"><span data-stu-id="3492e-253">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="3492e-254">下列範例中的 `NeedOnlyOne` 函式說明此情節：</span><span class="sxs-lookup"><span data-stu-id="3492e-254">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="3492e-255">然後，您可以如下所示使用此函式︰</span><span class="sxs-lookup"><span data-stu-id="3492e-255">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="3492e-256">交錯作業</span><span class="sxs-lookup"><span data-stu-id="3492e-256">Interleaved Operations</span></span>
 <span data-ttu-id="3492e-257"><xref:System.Threading.Tasks.Task.WhenAny%2A>當您使用大型工作集時，使用方法來支援交錯的案例，可能會有潛在的效能問題。</span><span class="sxs-lookup"><span data-stu-id="3492e-257">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with large sets of tasks.</span></span> <span data-ttu-id="3492e-258">對 <xref:System.Threading.Tasks.Task.WhenAny%2A> 發出的每個呼叫會導致向每個工作登錄接續。</span><span class="sxs-lookup"><span data-stu-id="3492e-258">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="3492e-259">針對 N 個工作，這會導致 (N<sup>2</sup>) 在交錯作業的存留期內建立的接續。</span><span class="sxs-lookup"><span data-stu-id="3492e-259">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="3492e-260">如果您正在處理大量的工作，您可以使用下列範例中的組合器 (`Interleaved`) 來解決效能問題：</span><span class="sxs-lookup"><span data-stu-id="3492e-260">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="3492e-261">然後，您可以利用組合器處理工作完成時的結果，例如︰</span><span class="sxs-lookup"><span data-stu-id="3492e-261">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="3492e-262">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="3492e-262">WhenAllOrFirstException</span></span>
 <span data-ttu-id="3492e-263">在某些分散/集中的情節中，您可能想要等候一個集合的所有工作，但如果其中一個發生錯誤，您想要在發生例外狀況時立刻停止等候。</span><span class="sxs-lookup"><span data-stu-id="3492e-263">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="3492e-264">您可以使用結合器方法來達到此目的，如下列範例中的 `WhenAllOrFirstException`︰</span><span class="sxs-lookup"><span data-stu-id="3492e-264">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="3492e-265">建置以工作為基礎的資料結構</span><span class="sxs-lookup"><span data-stu-id="3492e-265">Building Task-based Data Structures</span></span>
 <span data-ttu-id="3492e-266">除了能夠建立自訂的工作型組合器之外，在和中使用資料結構來 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 代表非同步作業的結果，以及與其聯結所需的同步處理，讓它成為強大的型別，可在其中建立自訂資料結構以用於非同步案例中。</span><span class="sxs-lookup"><span data-stu-id="3492e-266">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="3492e-267">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="3492e-267">AsyncCache</span></span>
 <span data-ttu-id="3492e-268">工作的其中一個重要層面就是它可以交給多個取用者，這些取用者全都可以等待它、向它登錄接續、取得其結果或例外狀況 (如果是 <xref:System.Threading.Tasks.Task%601>)等。</span><span class="sxs-lookup"><span data-stu-id="3492e-268">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="3492e-269">這使得 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 非常適合用於非同步快取基礎結構中。</span><span class="sxs-lookup"><span data-stu-id="3492e-269">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="3492e-270">以下是一個小型但功能強大的非同步快取，其建立在下列位置的範例 <xref:System.Threading.Tasks.Task%601> ：</span><span class="sxs-lookup"><span data-stu-id="3492e-270">Here's an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="3492e-271">[AsyncCache \<TKey,TValue> ](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/)類別會接受採用的函式作為其函式的委派， `TKey` 並傳回 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="3492e-271">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="3492e-272">先前從快取中存取的任何值會儲存在內部字典中，`AsyncCache` 會確保每個索引鍵只產生一個工作，即使並行存取快取也一樣。</span><span class="sxs-lookup"><span data-stu-id="3492e-272">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="3492e-273">例如，您可以為下載的網頁建置快取︰</span><span class="sxs-lookup"><span data-stu-id="3492e-273">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="3492e-274">然後，每當您需要網頁的內容時，您可以在非同步方法中使用此快取。</span><span class="sxs-lookup"><span data-stu-id="3492e-274">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="3492e-275">`AsyncCache`類別可確保您下載的頁面越少，並快取結果。</span><span class="sxs-lookup"><span data-stu-id="3492e-275">The `AsyncCache` class ensures that you're downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="3492e-276">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="3492e-276">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="3492e-277">您也可以使用工作來建置資料結構，以協調非同步活動。</span><span class="sxs-lookup"><span data-stu-id="3492e-277">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="3492e-278">請考量其中一種傳統的平行設計模式︰產生者/取用者。</span><span class="sxs-lookup"><span data-stu-id="3492e-278">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="3492e-279">在此模式中，產生者產生由取用者取用的資料，產生者和消費者可以平行執行。</span><span class="sxs-lookup"><span data-stu-id="3492e-279">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="3492e-280">比方說，取用者處理先前由產生者產生的項目 1，而產生者現在產生項目 2。</span><span class="sxs-lookup"><span data-stu-id="3492e-280">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="3492e-281">在產生者/取用者模式中，您無可避免地一定要使用某種資料結構來儲存產生者建立的工作，才能讓取用者在新資料出現時收到通知並且找到新資料。</span><span class="sxs-lookup"><span data-stu-id="3492e-281">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="3492e-282">以下是以工作為基礎的簡單資料結構，可讓您使用非同步方法作為生產者和取用者：</span><span class="sxs-lookup"><span data-stu-id="3492e-282">Here's a simple data structure, built on top of tasks, that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="3492e-283">利用該資料結構，您可以撰寫如下所示的程式碼︰</span><span class="sxs-lookup"><span data-stu-id="3492e-283">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="3492e-284"><xref:System.Threading.Tasks.Dataflow> 命名空間包含 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類型，使用方式很類似，但不需要建置自訂集合類型︰</span><span class="sxs-lookup"><span data-stu-id="3492e-284">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="3492e-285"><xref:System.Threading.Tasks.Dataflow>命名空間會以 NuGet 套件的形式提供。</span><span class="sxs-lookup"><span data-stu-id="3492e-285">The <xref:System.Threading.Tasks.Dataflow> namespace is available as a NuGet package.</span></span> <span data-ttu-id="3492e-286">若要安裝包含 <xref:System.Threading.Tasks.Dataflow> 命名空間的元件，請在 Visual Studio 中開啟您的專案，從 [專案] 功能表中選擇 [ **管理 NuGet 套件** ]，然後在線上搜尋 `System.Threading.Tasks.Dataflow` 封裝。</span><span class="sxs-lookup"><span data-stu-id="3492e-286">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the `System.Threading.Tasks.Dataflow` package.</span></span>

## <a name="see-also"></a><span data-ttu-id="3492e-287">請參閱</span><span class="sxs-lookup"><span data-stu-id="3492e-287">See also</span></span>

- [<span data-ttu-id="3492e-288">以工作為基礎的非同步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="3492e-288">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="3492e-289">實作以工作為基礎的非同步模式</span><span class="sxs-lookup"><span data-stu-id="3492e-289">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="3492e-290">Interop 與其他非同步模式和類型</span><span class="sxs-lookup"><span data-stu-id="3492e-290">Interop with Other Asynchronous Patterns and Types</span></span>](interop-with-other-asynchronous-patterns-and-types.md)
