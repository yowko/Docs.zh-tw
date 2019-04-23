---
title: 非同步程式設計
description: 了解如何F#非同步程式設計透過語言層級的程式設計模型，而且容易使用自然語言來完成。
ms.date: 06/20/2016
ms.openlocfilehash: 6925a0132f9beed6be5f9dded3630b551072bea2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343450"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="5ddb0-103">在 F 中的非同步程式設計\#</span><span class="sxs-lookup"><span data-stu-id="5ddb0-103">Async Programming in F\#</span></span>

> [!NOTE]
> <span data-ttu-id="5ddb0-104">已在這篇文章探索一些不準確。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-104">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="5ddb0-105">它是正在重寫。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-105">It is being rewritten.</span></span>  <span data-ttu-id="5ddb0-106">請參閱[問題 #666](https://github.com/dotnet/docs/issues/666)若要了解所做的變更。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-106">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="5ddb0-107">非同步程式設計中F#即可完成設計為易於使用且自然語言的語言層級程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-107">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="5ddb0-108">非同步程式設計中的核心F#是`Async<'T>`，可觸發在背景中執行的工作的表示法所在`'T`會傳回透過特殊的型別`return`關鍵字或`unit`如果非同步工作流程具有可傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-108">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="5ddb0-109">若要了解的重要概念是非同步運算式的型別`Async<'T>`，也就是只_規格_要在非同步處理內容中完成的工作。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-109">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="5ddb0-110">它不會執行直到明確地與其中一個開始的函式開始 (例如`Async.RunSynchronously`)。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-110">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="5ddb0-111">雖然這是不同的方式來思考執行工作時，它最後是實際上相當簡單。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-111">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="5ddb0-112">例如，假設您想要從 dotnetfoundation.org 下載 HTML，而不會封鎖主執行緒。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-112">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="5ddb0-113">您可以完成此作業就像這樣：</span><span class="sxs-lookup"><span data-stu-id="5ddb0-113">You can accomplish it like this:</span></span>

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

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="5ddb0-114">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="5ddb0-114">And that’s it!</span></span> <span data-ttu-id="5ddb0-115">除了使用`async`， `let!`，並`return`，這是正常的只是F#程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-115">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="5ddb0-116">有幾個語法建構是值得一提：</span><span class="sxs-lookup"><span data-stu-id="5ddb0-116">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="5ddb0-117">`let!` 繫結非同步運算式 （它是在另一個內容） 的結果。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-117">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="5ddb0-118">`use!` 運作方式就像`let!`，但它超出範圍時，處置其繫結的資源。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-118">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="5ddb0-119">`do!` 將等候的非同步工作流程不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-119">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="5ddb0-120">`return` 從非同步運算式，只會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-120">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="5ddb0-121">`return!` 執行另一個非同步工作流程，並因此會傳回其傳回的值。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-121">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="5ddb0-122">此外，正常`let`， `use`，和`do`可以與非同步版本一起使用的關鍵字，就如同一般函式中。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-122">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="5ddb0-123">如何開始在 F 中的非同步程式碼\#</span><span class="sxs-lookup"><span data-stu-id="5ddb0-123">How to start Async Code in F\#</span></span>

<span data-ttu-id="5ddb0-124">如先前所述，非同步程式碼會是工作的要在需要明確地啟動另一個內容中完成規格。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-124">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="5ddb0-125">以下是為了達成此目的的兩種主要方式：</span><span class="sxs-lookup"><span data-stu-id="5ddb0-125">Here are two primary ways to accomplish this:</span></span>

1. <span data-ttu-id="5ddb0-126">`Async.RunSynchronously` 將另一個執行緒上啟動非同步工作流程，並等待其結果。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-126">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

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
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2. <span data-ttu-id="5ddb0-127">`Async.Start` 將會啟動非同步工作流程，另一個執行緒，並將**不**等待其結果。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-127">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="5ddb0-128">有其他方式來啟動非同步工作流程適用於較特定案例。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-128">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="5ddb0-129">這些方式詳述[非同步參考中](https://msdn.microsoft.com/library/ee370232.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-129">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="5ddb0-130">在執行緒上附註</span><span class="sxs-lookup"><span data-stu-id="5ddb0-130">A Note on Threads</span></span>

<span data-ttu-id="5ddb0-131">片語 「 在另一個執行緒 」 前面所述，但務必要知道**這不表示非同步工作流程是一個外觀進行多執行緒處理**。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-131">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="5ddb0-132">工作流程實際上 」 就會跳 「 之間採用它們的少量的時間才能執行有用工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-132">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="5ddb0-133">非同步工作流程會有效地 「 等待 」 （例如，等候網路呼叫傳回的項目），它採用在任何執行緒是會釋出到移執行其他有用的工作。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-133">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="5ddb0-134">這可讓非同步工作流程，利用它們盡可能的情況下，有效地執行的系統，並使其可針對大量 I/O 的情況下特別強大。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-134">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="5ddb0-135">如何將非同步程式碼中的平行處理原則</span><span class="sxs-lookup"><span data-stu-id="5ddb0-135">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="5ddb0-136">有時您可能需要執行多個非同步作業以平行方式，收集其結果，並以某種方式解譯這些。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-136">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="5ddb0-137">`Async.Parallel` 可讓您執行這項操作，而不需要使用工作平行程式庫，其中會包含您需要強制轉型`Task<'T>`和`Async<'T>`型別。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-137">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="5ddb0-138">下列範例會使用`Async.Parallel`到從四種熱門的網站，以平行方式下載 HTML，等候這些工作完成，並再列印已下載的 HTML。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-138">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

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

## <a name="important-info-and-advice"></a><span data-ttu-id="5ddb0-139">重要資訊和建議</span><span class="sxs-lookup"><span data-stu-id="5ddb0-139">Important Info and Advice</span></span>

*   <span data-ttu-id="5ddb0-140">將"Async"附加至您將使用的任何函式的結尾</span><span class="sxs-lookup"><span data-stu-id="5ddb0-140">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="5ddb0-141">雖然這只是命名慣例，它會簡化 API 搜尋功能等項目。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-141">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="5ddb0-142">特別是如果有相同的例行工作的同步和非同步版本，最好明確陳述這是非同步，透過名稱。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-142">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="5ddb0-143">聆聽編譯器 ！</span><span class="sxs-lookup"><span data-stu-id="5ddb0-143">Listen to the compiler!</span></span>

 <span data-ttu-id="5ddb0-144">F#編譯器是非常嚴格，因此幾乎不可能進行像是麻煩以同步方式執行"async"程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-144">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="5ddb0-145">如果您遇到警告時，這是登，程式碼不會認為它將如何執行。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-145">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="5ddb0-146">如果您可以讓編譯器滿意，您的程式碼將很有可能會執行，如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-146">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="5ddb0-147">針對C#/VB 程式設計人員想成 F\#</span><span class="sxs-lookup"><span data-stu-id="5ddb0-147">For the C#/VB Programmer Looking Into F\#</span></span>

<span data-ttu-id="5ddb0-148">本節假設您已熟悉使用中的非同步模型C#/VB.</span><span class="sxs-lookup"><span data-stu-id="5ddb0-148">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="5ddb0-149">如果您不是[中的非同步程式設計C#](../../../csharp/async.md)是起始點。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-149">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="5ddb0-150">沒有基本差別在於C#/VB 非同步模型和F#非同步模型。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-150">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="5ddb0-151">當您呼叫的函式會傳回`Task`或`Task<'T>`，該作業已開始執行。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-151">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="5ddb0-152">傳回的控制代碼表示已在執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-152">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="5ddb0-153">相反地，當您呼叫的非同步函式F#，則`Async<'a>`傳回代表工作將會**產生**在某個時間點。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-153">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="5ddb0-154">了解此模型是功能強大，因為它可讓您在非同步作業F#鏈結在一起更方便地有條件地執行，並開始時具有更細微的資料粒度的控制。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-154">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="5ddb0-155">有幾個其他的相似性與差異值得一提。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-155">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="5ddb0-156">相似之處</span><span class="sxs-lookup"><span data-stu-id="5ddb0-156">Similarities</span></span>

*   <span data-ttu-id="5ddb0-157">`let!``use!`，並`do!`類似`await`內呼叫的非同步作業時`async{ }`區塊。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-157">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="5ddb0-158">三個關鍵字只可用於`async { }`區塊中，類似`await`才會叫用內部`async`方法。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-158">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="5ddb0-159">簡單地說，`let!`是的當您想要擷取並使用結果，`use!`相同，但是為項目使用之後，應該取得清除其資源和`do!`是當您想要等候的非同步工作流程，且沒有傳回值，以完成再繼續。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-159">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="5ddb0-160">F#類似的方式支援資料平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-160">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="5ddb0-161">其運作方式非常不同的是，雖然`Async.Parallel`對應至`Task.WhenAll`想的一組非同步作業的結果，在全部完成時的案例。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-161">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="5ddb0-162">差異</span><span class="sxs-lookup"><span data-stu-id="5ddb0-162">Differences</span></span>

*   <span data-ttu-id="5ddb0-163">巢狀`let!`不允許，不同於巢狀結構 `await`</span><span class="sxs-lookup"><span data-stu-id="5ddb0-163">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="5ddb0-164">不同於`await`，這可以巢狀無限期`let!`無法和其結果，然後再將它在另一個繫結必須`let!`， `do!`，或`use!`。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-164">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="5ddb0-165">取消支援會在F#比C#/VB.</span><span class="sxs-lookup"><span data-stu-id="5ddb0-165">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="5ddb0-166">支援在執行工作中途取消C#/VB 需要檢查`IsCancellationRequested`屬性或呼叫`ThrowIfCancellationRequested()`上`CancellationToken`傳遞至非同步方法的物件。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-166">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="5ddb0-167">相反地，F#非同步工作流程是較自然地取消。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-167">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="5ddb0-168">取消是簡單的三步驟程序。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-168">Cancellation is a simple three-step process.</span></span>

1. <span data-ttu-id="5ddb0-169">建立新的 `CancellationTokenSource`。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-169">Create a new `CancellationTokenSource`.</span></span>
2. <span data-ttu-id="5ddb0-170">請將它傳遞到起始函式。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-170">Pass it into a starting function.</span></span>
3. <span data-ttu-id="5ddb0-171">呼叫`Cancel`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5ddb0-171">Call `Cancel` on the token.</span></span>

<span data-ttu-id="5ddb0-172">範例：</span><span class="sxs-lookup"><span data-stu-id="5ddb0-172">Example:</span></span>

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }
    
let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

<span data-ttu-id="5ddb0-173">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="5ddb0-173">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="5ddb0-174">其他資源︰</span><span class="sxs-lookup"><span data-stu-id="5ddb0-174">Further resources:</span></span>

*   [<span data-ttu-id="5ddb0-175">MSDN 上的非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="5ddb0-175">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="5ddb0-176">非同步順序F#</span><span class="sxs-lookup"><span data-stu-id="5ddb0-176">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="5ddb0-177">F#HTTP 資料公用程式</span><span class="sxs-lookup"><span data-stu-id="5ddb0-177">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)