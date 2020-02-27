---
title: 非同步程式設計
description: 瞭解如何F#根據衍生自核心函式程式設計概念的語言層級程式設計模型，提供非同步全新支援。
ms.date: 12/17/2018
ms.openlocfilehash: 7021d7936d10f9ea6fceb4aa56db3285d21624ad
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628848"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="0c89b-103">F\# 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="0c89b-103">Async programming in F\#</span></span>

<span data-ttu-id="0c89b-104">非同步程式設計是基於各種原因而對現代化應用程式而言不可或缺的一種機制。</span><span class="sxs-lookup"><span data-stu-id="0c89b-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="0c89b-105">大部分的開發人員都會遇到兩個主要的使用案例：</span><span class="sxs-lookup"><span data-stu-id="0c89b-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="0c89b-106">呈現可提供大量並行連入要求的伺服器進程，同時將所佔用的系統資源降至最低，同時要求處理會等候該進程外部系統或服務的輸入</span><span class="sxs-lookup"><span data-stu-id="0c89b-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="0c89b-107">在同時進行的背景工作時，維護回應式 UI 或主執行緒</span><span class="sxs-lookup"><span data-stu-id="0c89b-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="0c89b-108">雖然背景工作通常會牽涉到多個執行緒的使用率，但請務必考慮非同步和多執行緒的概念。</span><span class="sxs-lookup"><span data-stu-id="0c89b-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="0c89b-109">事實上，它們是不同的考慮，而其中一個則不代表另一個。</span><span class="sxs-lookup"><span data-stu-id="0c89b-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="0c89b-110">本文所述的內容將會更詳細地說明。</span><span class="sxs-lookup"><span data-stu-id="0c89b-110">What follows in this article describes this in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="0c89b-111">非同步已定義</span><span class="sxs-lookup"><span data-stu-id="0c89b-111">Asynchrony defined</span></span>

<span data-ttu-id="0c89b-112">先前的重點是，非同步與多個執行緒的使用率無關，值得進一步說明。</span><span class="sxs-lookup"><span data-stu-id="0c89b-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="0c89b-113">有時候會有三個相關的概念，但完全獨立于另一個：</span><span class="sxs-lookup"><span data-stu-id="0c89b-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="0c89b-114">能力當多個計算在重迭的時間週期內執行時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="0c89b-115">平行處理原則當單一計算的多個計算或數個部分在完全相同的時間執行時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="0c89b-116">非同步當一或多個計算可與主要程式流程分開執行時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="0c89b-117">這三種概念都是相互關聯的概念，但很容易混為一談，特別是當它們一起使用時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="0c89b-118">例如，您可能需要以平行方式執行多個非同步計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="0c89b-119">這並不表示平行處理原則或非同步彼此隱含。</span><span class="sxs-lookup"><span data-stu-id="0c89b-119">This does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="0c89b-120">如果您考慮「非同步」一詞的 etymology，就會牽涉到兩個部分：</span><span class="sxs-lookup"><span data-stu-id="0c89b-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="0c89b-121">"a"，表示 "not"。</span><span class="sxs-lookup"><span data-stu-id="0c89b-121">"a", meaning "not".</span></span>
- <span data-ttu-id="0c89b-122">「同步」，表示「同時」。</span><span class="sxs-lookup"><span data-stu-id="0c89b-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="0c89b-123">當您將這兩個詞彙放在一起時，您會看到「非同步」表示「不是同一時間」。</span><span class="sxs-lookup"><span data-stu-id="0c89b-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="0c89b-124">就這麼簡單！</span><span class="sxs-lookup"><span data-stu-id="0c89b-124">That's it!</span></span> <span data-ttu-id="0c89b-125">在此定義中，不會隱含並行或平行處理。</span><span class="sxs-lookup"><span data-stu-id="0c89b-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="0c89b-126">這在實務上也是如此。</span><span class="sxs-lookup"><span data-stu-id="0c89b-126">This is also true in practice.</span></span>

<span data-ttu-id="0c89b-127">實際上，中F#的非同步計算會排定為獨立執行主要程式流程。</span><span class="sxs-lookup"><span data-stu-id="0c89b-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="0c89b-128">這並不代表並行或平行處理，也不表示一定會在背景中進行計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-128">This doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="0c89b-129">事實上，非同步計算甚至可以同步執行，視計算的本質和計算執行所在的環境而定。</span><span class="sxs-lookup"><span data-stu-id="0c89b-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="0c89b-130">主要的重點是，非同步計算與主要程式流程無關。</span><span class="sxs-lookup"><span data-stu-id="0c89b-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="0c89b-131">雖然非同步計算的執行時間或方式有一些保證，但還是有一些方法可以協調和排程它們。</span><span class="sxs-lookup"><span data-stu-id="0c89b-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="0c89b-132">本文的其餘部分將探討F#非同步核心概念，以及如何使用內建的類型、函式和運算式F#。</span><span class="sxs-lookup"><span data-stu-id="0c89b-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="0c89b-133">核心概念</span><span class="sxs-lookup"><span data-stu-id="0c89b-133">Core concepts</span></span>

<span data-ttu-id="0c89b-134">在F#中，非同步程式設計是以三個核心概念為中心：</span><span class="sxs-lookup"><span data-stu-id="0c89b-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="0c89b-135">`Async<'T>` 類型，代表可組合的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="0c89b-136">`Async` 模組函數，可讓您排程非同步工作、撰寫非同步計算，以及轉換非同步結果。</span><span class="sxs-lookup"><span data-stu-id="0c89b-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="0c89b-137">`async { }`[計算運算式](../../language-reference/computation-expressions.md)，提供建立和控制非同步計算的便利語法。</span><span class="sxs-lookup"><span data-stu-id="0c89b-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="0c89b-138">您可以在下列範例中看到這三個概念：</span><span class="sxs-lookup"><span data-stu-id="0c89b-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="0c89b-139">在此範例中，`printTotalFileBytes` 函數的類型 `string -> Async<unit>`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="0c89b-140">呼叫函數並不會實際執行非同步計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="0c89b-141">相反地，它會傳回 `Async<unit>`，作為要以非同步方式執行之工作的*規格*。</span><span class="sxs-lookup"><span data-stu-id="0c89b-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="0c89b-142">它會呼叫其主體中的 `Async.AwaitTask`，將 <xref:System.IO.File.ReadAllBytesAsync%2A> 的結果轉換成適當的類型。</span><span class="sxs-lookup"><span data-stu-id="0c89b-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="0c89b-143">另一個重要的程式程式碼是 `Async.RunSynchronously`的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0c89b-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="0c89b-144">這是非同步模組的其中一個啟動函式，如果您想要實際執行非同步計算，就必須F#呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="0c89b-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="0c89b-145">這是 `async` 程式設計的C#/Visual 基本樣式的基本差異。</span><span class="sxs-lookup"><span data-stu-id="0c89b-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="0c89b-146">在F#中，可以將非同步計算視為**冷**工作。</span><span class="sxs-lookup"><span data-stu-id="0c89b-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="0c89b-147">必須明確啟動才能實際執行。</span><span class="sxs-lookup"><span data-stu-id="0c89b-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="0c89b-148">這有一些優點，因為它可讓您比在或 Visual Basic 中C#更輕鬆地結合和排序非同步工作。</span><span class="sxs-lookup"><span data-stu-id="0c89b-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="0c89b-149">結合非同步計算</span><span class="sxs-lookup"><span data-stu-id="0c89b-149">Combine asynchronous computations</span></span>

<span data-ttu-id="0c89b-150">以下是藉由結合計算，以先前的版本為基礎的範例：</span><span class="sxs-lookup"><span data-stu-id="0c89b-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="0c89b-151">如您所見，`main` 函式已進行更多呼叫。</span><span class="sxs-lookup"><span data-stu-id="0c89b-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="0c89b-152">在概念上，它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0c89b-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="0c89b-153">使用 `Array.map`，將命令列引數轉換成 `Async<unit>` 計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="0c89b-154">建立 `Async<'T[]>`，以在執行時以平行方式排程和執行 `printTotalFileBytes` 計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="0c89b-155">建立將會執行平行計算並忽略其結果的 `Async<unit>`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="0c89b-156">使用 `Async.RunSynchronously` 和 block 明確執行最後的計算，直到完成為止。</span><span class="sxs-lookup"><span data-stu-id="0c89b-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it is completes.</span></span>

<span data-ttu-id="0c89b-157">當此程式執行時，`printTotalFileBytes` 會針對每個命令列引數以平行方式執行。</span><span class="sxs-lookup"><span data-stu-id="0c89b-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="0c89b-158">因為非同步計算獨立執行程式流程，所以不會列印其資訊並完成執行。</span><span class="sxs-lookup"><span data-stu-id="0c89b-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="0c89b-159">計算會以平行方式排程，但不保證其執行順序。</span><span class="sxs-lookup"><span data-stu-id="0c89b-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="0c89b-160">順序非同步計算</span><span class="sxs-lookup"><span data-stu-id="0c89b-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="0c89b-161">由於 `Async<'T>` 是工作的規格，而不是已執行的工作，因此您可以輕鬆地執行更複雜的轉換。</span><span class="sxs-lookup"><span data-stu-id="0c89b-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="0c89b-162">以下範例會排序一組非同步計算，讓它們逐一執行。</span><span class="sxs-lookup"><span data-stu-id="0c89b-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="0c89b-163">這會依照 `argv` 元素的順序來排程 `printTotalFileBytes` 執行，而不是以平行方式進行排程。</span><span class="sxs-lookup"><span data-stu-id="0c89b-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="0c89b-164">因為下一個專案在最後一個計算完成執行後才會排程，所以計算會進行排序，使其執行不會有任何重迭。</span><span class="sxs-lookup"><span data-stu-id="0c89b-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="0c89b-165">重要的非同步模組函式</span><span class="sxs-lookup"><span data-stu-id="0c89b-165">Important Async module functions</span></span>

<span data-ttu-id="0c89b-166">當您在中F#撰寫非同步程式碼時，通常會與處理計算排程的架構互動。</span><span class="sxs-lookup"><span data-stu-id="0c89b-166">When you write async code in F# you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="0c89b-167">不過，這不一定會發生，因此最好學習各種啟動函數來排程非同步工作。</span><span class="sxs-lookup"><span data-stu-id="0c89b-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="0c89b-168">因為F#非同步計算是工作的_規格_，而不是已在執行中的工作表示法，所以必須以起始函式明確啟動。</span><span class="sxs-lookup"><span data-stu-id="0c89b-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="0c89b-169">有許多[非同步啟動函數](https://msdn.microsoft.com/library/ee370232.aspx)在不同的內容中很有説明。</span><span class="sxs-lookup"><span data-stu-id="0c89b-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="0c89b-170">下一節將說明一些較常見的啟動函數。</span><span class="sxs-lookup"><span data-stu-id="0c89b-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="0c89b-171">Async.startchild</span><span class="sxs-lookup"><span data-stu-id="0c89b-171">Async.StartChild</span></span>

<span data-ttu-id="0c89b-172">在非同步計算中啟動子計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="0c89b-173">這可讓多個非同步計算同時執行。</span><span class="sxs-lookup"><span data-stu-id="0c89b-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="0c89b-174">子計算會與父計算共用解除標記。</span><span class="sxs-lookup"><span data-stu-id="0c89b-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="0c89b-175">如果父計算已取消，子計算也會一併取消。</span><span class="sxs-lookup"><span data-stu-id="0c89b-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="0c89b-176">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-176">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="0c89b-177">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-177">When to use:</span></span>

- <span data-ttu-id="0c89b-178">當您想要同時執行多個非同步計算，而不是一次，但未以平行方式排程它們時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="0c89b-179">當您想要將子計算的存留期系結至父計算的存留期間。</span><span class="sxs-lookup"><span data-stu-id="0c89b-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="0c89b-180">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-180">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-181">使用 `Async.StartChild` 啟動多個計算，與以平行方式進行排程並不相同。</span><span class="sxs-lookup"><span data-stu-id="0c89b-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="0c89b-182">如果您想要平行排程計算，請使用 `Async.Parallel`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="0c89b-183">取消父計算會觸發其啟動之所有子計算的取消作業。</span><span class="sxs-lookup"><span data-stu-id="0c89b-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="0c89b-184">StartImmediate</span><span class="sxs-lookup"><span data-stu-id="0c89b-184">Async.StartImmediate</span></span>

<span data-ttu-id="0c89b-185">執行非同步計算，並在目前的作業系統執行緒上立即啟動。</span><span class="sxs-lookup"><span data-stu-id="0c89b-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="0c89b-186">如果您需要在計算期間更新呼叫執行緒上的某個專案，這會很有説明。</span><span class="sxs-lookup"><span data-stu-id="0c89b-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="0c89b-187">例如，如果非同步計算必須更新 UI （例如更新進度列），則應該使用 `Async.StartImmediate`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="0c89b-188">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-188">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="0c89b-189">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-189">When to use:</span></span>

- <span data-ttu-id="0c89b-190">當您需要在非同步計算過程中更新呼叫執行緒上的某些專案時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="0c89b-191">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-191">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-192">非同步計算中的程式碼會在任何一個要排程的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="0c89b-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="0c89b-193">如果該執行緒以某種方式區分，例如 UI 執行緒，這可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="0c89b-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="0c89b-194">在這種情況下，`Async.StartImmediate` 可能不適合使用。</span><span class="sxs-lookup"><span data-stu-id="0c89b-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="0c89b-195">Async.startastask</span><span class="sxs-lookup"><span data-stu-id="0c89b-195">Async.StartAsTask</span></span>

<span data-ttu-id="0c89b-196">執行執行緒集區中的計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="0c89b-197">傳回在計算終止（產生結果、擲回例外狀況或取消）時，將在對應狀態下完成的 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="0c89b-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="0c89b-198">如果未提供解除標記，則會使用預設的解除標記。</span><span class="sxs-lookup"><span data-stu-id="0c89b-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="0c89b-199">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-199">Signature:</span></span>

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="0c89b-200">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-200">When to use:</span></span>

- <span data-ttu-id="0c89b-201">當您需要呼叫 .NET API，而該應用程式預期會有 <xref:System.Threading.Tasks.Task%601> 來表示非同步計算的結果時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="0c89b-202">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-202">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-203">此呼叫會配置額外的 `Task` 物件，如果經常使用，則會增加額外負荷。</span><span class="sxs-lookup"><span data-stu-id="0c89b-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="0c89b-204">Async。 Parallel</span><span class="sxs-lookup"><span data-stu-id="0c89b-204">Async.Parallel</span></span>

<span data-ttu-id="0c89b-205">排定要平行執行的一系列非同步計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="0c89b-206">藉由指定 `maxDegreesOfParallelism` 參數，可以選擇性地調整/節流處理平行處理原則的程度。</span><span class="sxs-lookup"><span data-stu-id="0c89b-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="0c89b-207">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="0c89b-208">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-208">When to use it:</span></span>

- <span data-ttu-id="0c89b-209">如果您需要同時執行一組計算，而且不依賴其執行順序。</span><span class="sxs-lookup"><span data-stu-id="0c89b-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="0c89b-210">如果您不需要以平行方式排程的結果，直到全部完成為止。</span><span class="sxs-lookup"><span data-stu-id="0c89b-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="0c89b-211">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-211">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-212">一旦所有計算完成之後，您就只能存取產生的值陣列。</span><span class="sxs-lookup"><span data-stu-id="0c89b-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="0c89b-213">計算將會執行，但最終會進行排程。</span><span class="sxs-lookup"><span data-stu-id="0c89b-213">Computations will be run however they end up getting scheduled.</span></span> <span data-ttu-id="0c89b-214">這表示您無法依賴其執行順序。</span><span class="sxs-lookup"><span data-stu-id="0c89b-214">This means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="0c89b-215">非同步。連續</span><span class="sxs-lookup"><span data-stu-id="0c89b-215">Async.Sequential</span></span>

<span data-ttu-id="0c89b-216">排程要依行程順序執行的一系列非同步計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="0c89b-217">第一次計算將會執行，接下來是下一個，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0c89b-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="0c89b-218">不會平行執行計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="0c89b-219">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="0c89b-220">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-220">When to use it:</span></span>

- <span data-ttu-id="0c89b-221">如果您需要依序執行多個計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="0c89b-222">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-222">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-223">一旦所有計算完成之後，您就只能存取產生的值陣列。</span><span class="sxs-lookup"><span data-stu-id="0c89b-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="0c89b-224">計算會依照傳遞至此函式的循序執行，這可能表示傳回結果之前會經過較多的時間。</span><span class="sxs-lookup"><span data-stu-id="0c89b-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="0c89b-225">Async.awaittask</span><span class="sxs-lookup"><span data-stu-id="0c89b-225">Async.AwaitTask</span></span>

<span data-ttu-id="0c89b-226">傳回非同步計算，等候指定的 <xref:System.Threading.Tasks.Task%601> 完成，並將其結果傳回為 `Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="0c89b-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="0c89b-227">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-227">Signature:</span></span>

```fsharp
task: Task<'T>  -> Async<'T>
```

<span data-ttu-id="0c89b-228">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-228">When to use:</span></span>

- <span data-ttu-id="0c89b-229">當您使用的 .NET API 會在F#非同步計算中傳回 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="0c89b-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="0c89b-230">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-230">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-231">例外狀況會依照工作平行程式庫的慣例包裝在 <xref:System.AggregateException> 中，這與非同步一般呈現F#例外狀況的方式不同。</span><span class="sxs-lookup"><span data-stu-id="0c89b-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="0c89b-232">Async Catch</span><span class="sxs-lookup"><span data-stu-id="0c89b-232">Async.Catch</span></span>

<span data-ttu-id="0c89b-233">建立異步計算，以執行指定的 `Async<'T>`，並傳回 `Async<Choice<'T, exn>>`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="0c89b-234">如果指定的 `Async<'T>` 成功完成，則會傳回包含結果值的 `Choice1Of2`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="0c89b-235">如果在完成之前擲回例外狀況，則會傳回具有引發例外狀況的 `Choice2of2`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="0c89b-236">如果它用於本身由許多計算組成的非同步計算，而其中一個計算擲回例外狀況，則會完全停止內含的計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="0c89b-237">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="0c89b-238">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-238">When to use:</span></span>

- <span data-ttu-id="0c89b-239">當您執行可能因例外狀況而失敗的非同步工作，而且您想要在呼叫端處理該例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0c89b-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="0c89b-240">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-240">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-241">當使用結合或排序的非同步計算時，如果其中一個「內部」計算擲回例外狀況，則包含的計算將會完全停止。</span><span class="sxs-lookup"><span data-stu-id="0c89b-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="0c89b-242">Async。忽略</span><span class="sxs-lookup"><span data-stu-id="0c89b-242">Async.Ignore</span></span>

<span data-ttu-id="0c89b-243">建立異步計算來執行指定的計算，並忽略其結果。</span><span class="sxs-lookup"><span data-stu-id="0c89b-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="0c89b-244">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="0c89b-245">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-245">When to use:</span></span>

- <span data-ttu-id="0c89b-246">當您有不需要其結果的非同步計算時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="0c89b-247">這類似于非非同步程式碼的 `ignore` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c89b-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="0c89b-248">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-248">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-249">如果您因為想要使用 `Async.Start` 或其他需要 `Async<unit>`的函式而必須使用此功能，請考慮捨棄結果是否可以執行。</span><span class="sxs-lookup"><span data-stu-id="0c89b-249">If you must use this because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay to do.</span></span> <span data-ttu-id="0c89b-250">通常不應該只是為了符合類型簽章而捨棄結果。</span><span class="sxs-lookup"><span data-stu-id="0c89b-250">Discarding results just to fit a type signature should not generally be done.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="0c89b-251">Async.runsynchronously</span><span class="sxs-lookup"><span data-stu-id="0c89b-251">Async.RunSynchronously</span></span>

<span data-ttu-id="0c89b-252">執行非同步計算，並在呼叫執行緒上等候其結果。</span><span class="sxs-lookup"><span data-stu-id="0c89b-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="0c89b-253">此呼叫正在封鎖。</span><span class="sxs-lookup"><span data-stu-id="0c89b-253">This call is blocking.</span></span>

<span data-ttu-id="0c89b-254">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-254">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="0c89b-255">使用時機：</span><span class="sxs-lookup"><span data-stu-id="0c89b-255">When to use it:</span></span>

- <span data-ttu-id="0c89b-256">如果您需要，請在應用程式中使用它（在可執行檔的進入點上）。</span><span class="sxs-lookup"><span data-stu-id="0c89b-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="0c89b-257">當您不在意效能，而且想要一次執行一組其他非同步作業時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="0c89b-258">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-258">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-259">呼叫 `Async.RunSynchronously` 會封鎖呼叫執行緒，直到執行完成為止。</span><span class="sxs-lookup"><span data-stu-id="0c89b-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="0c89b-260">Async. Start</span><span class="sxs-lookup"><span data-stu-id="0c89b-260">Async.Start</span></span>

<span data-ttu-id="0c89b-261">線上程集區中啟動會傳回 `unit`的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="0c89b-262">不等候其結果。</span><span class="sxs-lookup"><span data-stu-id="0c89b-262">Doesn't wait for its result.</span></span> <span data-ttu-id="0c89b-263">以 `Async.Start` 開始的嵌套計算會與呼叫它們的父系計算完全獨立地啟動。</span><span class="sxs-lookup"><span data-stu-id="0c89b-263">Nested computations started with `Async.Start` are started completely independently of the parent computation that called them.</span></span> <span data-ttu-id="0c89b-264">其存留期不會系結至任何父系計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="0c89b-265">如果父代計算已取消，則不會取消任何子計算。</span><span class="sxs-lookup"><span data-stu-id="0c89b-265">If the parent computation is canceled, no child computations are cancelled.</span></span>

<span data-ttu-id="0c89b-266">簽章</span><span class="sxs-lookup"><span data-stu-id="0c89b-266">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="0c89b-267">只在下列情況使用：</span><span class="sxs-lookup"><span data-stu-id="0c89b-267">Use only when:</span></span>

- <span data-ttu-id="0c89b-268">您的非同步計算不會產生結果，也不需要處理一次。</span><span class="sxs-lookup"><span data-stu-id="0c89b-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="0c89b-269">您不需要知道非同步計算何時完成。</span><span class="sxs-lookup"><span data-stu-id="0c89b-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="0c89b-270">您不在意非同步計算執行所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0c89b-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="0c89b-271">您不需要留意或報告工作所產生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0c89b-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="0c89b-272">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="0c89b-272">What to watch out for:</span></span>

- <span data-ttu-id="0c89b-273">以 `Async.Start` 開頭的計算所引發的例外狀況不會傳播至呼叫者。</span><span class="sxs-lookup"><span data-stu-id="0c89b-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="0c89b-274">將完全展開呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="0c89b-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="0c89b-275">`Async.Start` 啟動的任何 effectful 工作（例如呼叫 `printfn`）都不會造成此效果在程式執行的主要執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="0c89b-275">Any effectful work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="0c89b-276">與 .NET 交互操作</span><span class="sxs-lookup"><span data-stu-id="0c89b-276">Interoperate with .NET</span></span>

<span data-ttu-id="0c89b-277">您可能使用的 .NET 程式庫或C#程式碼基底，會使用非同步[/await](../../../standard/async.md)樣式的非同步程式設計。</span><span class="sxs-lookup"><span data-stu-id="0c89b-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="0c89b-278">因為C#大部分的 .net 程式庫會使用 <xref:System.Threading.Tasks.Task%601> 和 <xref:System.Threading.Tasks.Task> 類型做為其核心抽象概念，而不是 `Async<'T>`，所以您必須在這兩種方法之間，將界限交叉到非同步。</span><span class="sxs-lookup"><span data-stu-id="0c89b-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="0c89b-279">如何使用 .NET async 和 `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="0c89b-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="0c89b-280">使用 <xref:System.Threading.Tasks.Task%601> 的 .NET async 程式庫和程式碼基底（也就是具有傳回值的非同步計算）很簡單，而且具有內建F#的支援。</span><span class="sxs-lookup"><span data-stu-id="0c89b-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="0c89b-281">您可以使用 `Async.AwaitTask` 函數來等待 .NET 非同步計算：</span><span class="sxs-lookup"><span data-stu-id="0c89b-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="0c89b-282">您可以使用 `Async.StartAsTask` 函式，將非同步計算行程給 .NET 呼叫者：</span><span class="sxs-lookup"><span data-stu-id="0c89b-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="0c89b-283">如何使用 .NET async 和 `Task`</span><span class="sxs-lookup"><span data-stu-id="0c89b-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="0c89b-284">若要使用 <xref:System.Threading.Tasks.Task> 的 Api （也就是不會傳回值的 .NET 非同步計算），您可能需要新增額外的函式，以將 `Async<'T>` 轉換為 <xref:System.Threading.Tasks.Task>：</span><span class="sxs-lookup"><span data-stu-id="0c89b-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="0c89b-285">已經有可接受 <xref:System.Threading.Tasks.Task> 做為輸入的 `Async.AwaitTask`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="0c89b-286">使用此和先前定義的 `startTaskFromAsyncUnit` 函式F# ，您可以從非同步計算啟動和等待 <xref:System.Threading.Tasks.Task> 類型。</span><span class="sxs-lookup"><span data-stu-id="0c89b-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="0c89b-287">多執行緒的關聯性</span><span class="sxs-lookup"><span data-stu-id="0c89b-287">Relationship to multi-threading</span></span>

<span data-ttu-id="0c89b-288">雖然這篇文章中提到了執行緒，但有兩個重要的事項要記住：</span><span class="sxs-lookup"><span data-stu-id="0c89b-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="0c89b-289">除非在目前線程上明確啟動，否則非同步計算和執行緒之間沒有相似性。</span><span class="sxs-lookup"><span data-stu-id="0c89b-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="0c89b-290">中F#的非同步程式設計不是多執行緒的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="0c89b-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="0c89b-291">例如，計算實際上可能會在其呼叫端的執行緒上執行，視工作的本質而定。</span><span class="sxs-lookup"><span data-stu-id="0c89b-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="0c89b-292">計算也可以線上程之間「跳躍」，以一小段時間來進行，以在「等候」期間執行有用的工作（例如當網路呼叫正在傳輸時）。</span><span class="sxs-lookup"><span data-stu-id="0c89b-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="0c89b-293">雖然F#提供在目前線程上啟動非同步計算的一些功能（或明確地不在目前線程上），但非同步通常不會與特定的執行緒策略相關聯。</span><span class="sxs-lookup"><span data-stu-id="0c89b-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c89b-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c89b-294">See also</span></span>

- [<span data-ttu-id="0c89b-295">F#非同步程式設計模型</span><span class="sxs-lookup"><span data-stu-id="0c89b-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="0c89b-296">Jet .com 的F#非同步指南</span><span class="sxs-lookup"><span data-stu-id="0c89b-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="0c89b-297">F#針對有趣和利潤的非同步程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0c89b-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="0c89b-298">和F#中C#的非同步：中的非同步陷阱C#</span><span class="sxs-lookup"><span data-stu-id="0c89b-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
