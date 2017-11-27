---
title: "F # 中的非同步程式設計"
description: "了解如何完成 F # 非同步程式設計的語言層級的程式設計模型是易於使用和自然語言，透過。"
keywords: .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: 23528d84d0f28283868a1ea316953543d0fd566a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="async-programming-in-f"></a><span data-ttu-id="88549-104">F # 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="88549-104">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="88549-105">本文章中發現某些不準確。</span><span class="sxs-lookup"><span data-stu-id="88549-105">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="88549-106">它正在重寫。</span><span class="sxs-lookup"><span data-stu-id="88549-106">It is being rewritten.</span></span>  <span data-ttu-id="88549-107">請參閱[問題 #666](https://github.com/dotnet/docs/issues/666)若要了解所做的變更。</span><span class="sxs-lookup"><span data-stu-id="88549-107">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="88549-108">非同步程式設計 F # 中，即可完成設計為易於使用和自然語言的語言層級程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="88549-108">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="88549-109">F # 中的非同步程式設計的核心是`Async<'T>`，可以觸發要在背景中執行的工作的表示法其中`'T`透過特殊傳回的型別`return`關鍵字或`unit`如果非同步工作流程沒有。傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="88549-109">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="88549-110">若要了解的重要概念是非同步運算式的類型是`Async<'T>`，也就是只_規格_的工作來完成非同步的內容中。</span><span class="sxs-lookup"><span data-stu-id="88549-110">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="88549-111">不會執行直到明確地以其中一個開始的函式的開頭 (例如`Async.RunSynchronously`)。</span><span class="sxs-lookup"><span data-stu-id="88549-111">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="88549-112">雖然這是不同的方式來思考執行工作時，它最終會被實際上相當簡單。</span><span class="sxs-lookup"><span data-stu-id="88549-112">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="88549-113">例如，假設您想要從 dotnetfoundation.org 下載 HTML，而不會封鎖主執行緒。</span><span class="sxs-lookup"><span data-stu-id="88549-113">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="88549-114">您可以完成它，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="88549-114">You can accomplish it like this:</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="88549-115">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="88549-115">And that’s it!</span></span> <span data-ttu-id="88549-116">除了使用`async`， `let!`，和`return`，這是一般只要 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="88549-116">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="88549-117">有幾個語法建構是值得注意：</span><span class="sxs-lookup"><span data-stu-id="88549-117">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="88549-118">`let!`將繫結運算式結果的非同步 （它是在其他內容）。</span><span class="sxs-lookup"><span data-stu-id="88549-118">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="88549-119">`use!`運作方式就像`let!`，但超出範圍時便會處置它繫結的資源。</span><span class="sxs-lookup"><span data-stu-id="88549-119">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="88549-120">`do!`將會等候非同步工作流程，後者則不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="88549-120">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="88549-121">`return`只從非同步運算式會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="88549-121">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="88549-122">`return!`執行另一個非同步工作流程並傳回它的傳回值的結果。</span><span class="sxs-lookup"><span data-stu-id="88549-122">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="88549-123">此外，一般`let`， `use`，和`do`關鍵字可以用旁邊的非同步版本，就如同一般函式中。</span><span class="sxs-lookup"><span data-stu-id="88549-123">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="88549-124">如何啟動 F # 中的非同步程式碼</span><span class="sxs-lookup"><span data-stu-id="88549-124">How to start Async Code in F#</span></span> #

<span data-ttu-id="88549-125">如先前所述，非同步程式碼會為要進行明確的啟動所需的其他內容中的工作規格。</span><span class="sxs-lookup"><span data-stu-id="88549-125">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="88549-126">以下是兩個主要的方式可完成這項作業：</span><span class="sxs-lookup"><span data-stu-id="88549-126">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="88549-127">`Async.RunSynchronously`將啟動另一個執行緒上非同步工作流程，並等候其結果。</span><span class="sxs-lookup"><span data-stu-id="88549-127">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="88549-128">`Async.Start`開始非同步工作流程，另一個執行緒上，將**不**等候其結果。</span><span class="sxs-lookup"><span data-stu-id="88549-128">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="88549-129">還有其他方式啟動非同步工作流程提供給其他特定的情況。</span><span class="sxs-lookup"><span data-stu-id="88549-129">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="88549-130">它們詳述[非同步參考中](https://msdn.microsoft.com/library/ee370232.aspx)。</span><span class="sxs-lookup"><span data-stu-id="88549-130">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="88549-131">在執行緒上附註</span><span class="sxs-lookup"><span data-stu-id="88549-131">A Note on Threads</span></span>

<span data-ttu-id="88549-132">上述 「 在另一個執行緒"片語，但請務必了解**這不表示非同步工作流程的外觀的多執行緒**。</span><span class="sxs-lookup"><span data-stu-id="88549-132">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="88549-133">工作流程實際"跳 」 之間需它們靠借貸小的一段時間才能執行有用的工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="88549-133">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="88549-134">當非同步工作流程會有效地 「 正在等候 」 （例如，等待網路呼叫，以傳回內容） 時，它所需靠借貸時的任何執行緒被釋出最有用的工作移執行上其他項目。</span><span class="sxs-lookup"><span data-stu-id="88549-134">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="88549-135">這可讓非同步工作流程，以利用的系統盡可能有效率地執行，並使其更大量的 I/O 案例特別強大。</span><span class="sxs-lookup"><span data-stu-id="88549-135">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="88549-136">如何將平行處理原則新增至非同步程式碼</span><span class="sxs-lookup"><span data-stu-id="88549-136">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="88549-137">有時候您可能需要執行多個非同步作業以平行方式，收集其結果，並以某種方式解譯。</span><span class="sxs-lookup"><span data-stu-id="88549-137">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="88549-138">`Async.Parallel`可讓您執行這項操作，而不需要使用工作平行程式庫，這會牽涉到要強制轉型需要`Task<'T>`和`Async<'T>`型別。</span><span class="sxs-lookup"><span data-stu-id="88549-138">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="88549-139">下列範例會使用`Async.Parallel`若要下載 HTML 從四個熱門的網站，以平行方式，等候這些工作完成，然後再列印已下載的 HTML。</span><span class="sxs-lookup"><span data-stu-id="88549-139">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "http://www.microsoft.com"
      "http://www.google.com"
      "http://www.amazon.com"
      "http://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a><span data-ttu-id="88549-140">重要資訊和建議</span><span class="sxs-lookup"><span data-stu-id="88549-140">Important Info and Advice</span></span>

*   <span data-ttu-id="88549-141">將"Async"附加至您要使用的任何函式的結尾</span><span class="sxs-lookup"><span data-stu-id="88549-141">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="88549-142">雖然這是只使用命名慣例，但它並簡化之類的應用程式開發介面可搜尋性。</span><span class="sxs-lookup"><span data-stu-id="88549-142">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="88549-143">特別是如果有同步和非同步版本的相同的常式，最好明確陳述這是非同步的名稱。</span><span class="sxs-lookup"><span data-stu-id="88549-143">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="88549-144">聆聽編譯器 ！</span><span class="sxs-lookup"><span data-stu-id="88549-144">Listen to the compiler!</span></span>

 <span data-ttu-id="88549-145">F # 編譯器非常嚴格，讓您幾乎不可能做到麻煩類似"async"的程式碼同步執行。</span><span class="sxs-lookup"><span data-stu-id="88549-145">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="88549-146">如果您遇到警告時，這是程式碼將不會執行自己設想將會使用正負號。</span><span class="sxs-lookup"><span data-stu-id="88549-146">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="88549-147">如果您可以讓編譯器滿意，如預期般，將最有可能會執行您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="88549-147">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="88549-148">針對 C# /VB 程式設計人員想要 F #</span><span class="sxs-lookup"><span data-stu-id="88549-148">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="88549-149">本節假設您熟悉 C# 中的非同步模型 / VB</span><span class="sxs-lookup"><span data-stu-id="88549-149">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="88549-150">如果不是，[以 C# 撰寫的非同步](../../../csharp/async.md)是起始點。</span><span class="sxs-lookup"><span data-stu-id="88549-150">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="88549-151">沒有 C# /VB 非同步模型與 F # 非同步模型之間的基本差異。</span><span class="sxs-lookup"><span data-stu-id="88549-151">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="88549-152">當您呼叫的函式會傳回`Task`或`Task<'T>`，該作業已開始執行。</span><span class="sxs-lookup"><span data-stu-id="88549-152">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="88549-153">傳回的控制代碼表示已經在執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="88549-153">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="88549-154">相反地，當您呼叫 async 函式在 F #`Async<'a>`傳回代表工作都將**產生**在某個時間點。</span><span class="sxs-lookup"><span data-stu-id="88549-154">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="88549-155">了解此模型是功能強大，因為它允許 F # 中的非同步作業的鏈結在一起更方便地有條件地執行，而且會使用更精細的資料粒度的控制項來啟動。</span><span class="sxs-lookup"><span data-stu-id="88549-155">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="88549-156">有幾個其他相似性與值得注意的差異。</span><span class="sxs-lookup"><span data-stu-id="88549-156">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="88549-157">相似之處</span><span class="sxs-lookup"><span data-stu-id="88549-157">Similarities</span></span>

*   <span data-ttu-id="88549-158">`let!``use!`，和`do!`類似於`await`內呼叫非同步作業時`async{ }`區塊。</span><span class="sxs-lookup"><span data-stu-id="88549-158">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="88549-159">三個關鍵字只可用於`async { }`區塊，類似`await`只內叫用`async`方法。</span><span class="sxs-lookup"><span data-stu-id="88549-159">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="88549-160">簡單地說，`let!`適用於當您想要擷取並使用結果，`use!`相同，但是為之後使用時，應該清除其資源的項目和`do!`適用於當您想要等候的非同步工作流程完成不傳回值再進行。</span><span class="sxs-lookup"><span data-stu-id="88549-160">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="88549-161">F # 類似的方式支援資料平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="88549-161">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="88549-162">其運作方式非常不同，雖然`Async.Parallel`對應至`Task.WhenAll`它們全部完成時，由一組非同步工作的結果的案例。</span><span class="sxs-lookup"><span data-stu-id="88549-162">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="88549-163">差異</span><span class="sxs-lookup"><span data-stu-id="88549-163">Differences</span></span>

*   <span data-ttu-id="88549-164">巢狀`let!`不允許，不同於巢狀結構`await`</span><span class="sxs-lookup"><span data-stu-id="88549-164">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="88549-165">不同於`await`，這可以巢狀無限期地`let!`無法和其結果，然後再將它在另一個繫結必須`let!`， `do!`，或`use!`。</span><span class="sxs-lookup"><span data-stu-id="88549-165">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="88549-166">取消支援是在 F # 與 C# 中更簡單 / VB</span><span class="sxs-lookup"><span data-stu-id="88549-166">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="88549-167">在 C# /VB 支援取消的工作中途島，透過其執行需要檢查`IsCancellationRequested`屬性或呼叫`ThrowIfCancellationRequested()`上`CancellationToken`傳遞至非同步方法的物件。</span><span class="sxs-lookup"><span data-stu-id="88549-167">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="88549-168">相反地，F # 非同步工作流程會較自然可取消。</span><span class="sxs-lookup"><span data-stu-id="88549-168">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="88549-169">取消是簡單的三個步驟程序。</span><span class="sxs-lookup"><span data-stu-id="88549-169">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="88549-170">建立新的 `CancellationTokenSource`。</span><span class="sxs-lookup"><span data-stu-id="88549-170">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="88549-171">請將它傳遞到起始的函式。</span><span class="sxs-lookup"><span data-stu-id="88549-171">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="88549-172">呼叫`Cancel`對這個語彙基元。</span><span class="sxs-lookup"><span data-stu-id="88549-172">Call `Cancel` on the token.</span></span>

<span data-ttu-id="88549-173">範例：</span><span class="sxs-lookup"><span data-stu-id="88549-173">Example:</span></span>

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="88549-174">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="88549-174">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="88549-175">進一步的資源：</span><span class="sxs-lookup"><span data-stu-id="88549-175">Further resources:</span></span>

*   [<span data-ttu-id="88549-176">MSDN 上的非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="88549-176">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="88549-177">F # 的非同步順序</span><span class="sxs-lookup"><span data-stu-id="88549-177">Asynchronous Sequences for F#</span></span>](http://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="88549-178">F # 資料 HTTP 公用程式</span><span class="sxs-lookup"><span data-stu-id="88549-178">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
