---
title: 非同步程式設計
description: '瞭解 F # 如何根據衍生自核心功能程式設計概念的語言層級程式設計模型，提供非同步全新支援。'
ms.date: 08/15/2020
ms.openlocfilehash: 8bf8d6987187377cc1f44e77141b5d70d873f849
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366818"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="ab204-103">F 中的非同步程式設計\#</span><span class="sxs-lookup"><span data-stu-id="ab204-103">Async programming in F\#</span></span>

<span data-ttu-id="ab204-104">非同步程式設計是基於各種原因而對新式應用程式來說很重要的一種機制。</span><span class="sxs-lookup"><span data-stu-id="ab204-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="ab204-105">大部分的開發人員會遇到兩個主要的使用案例：</span><span class="sxs-lookup"><span data-stu-id="ab204-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="ab204-106">呈現可提供大量並行連入要求的伺服器程式，同時將要求處理期間所佔用的系統資源降至最低，同時等待來自該進程外部系統或服務的輸入</span><span class="sxs-lookup"><span data-stu-id="ab204-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="ab204-107">維護回應迅速的 UI 或主執行緒，同時進行背景工作</span><span class="sxs-lookup"><span data-stu-id="ab204-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="ab204-108">雖然背景工作通常牽涉到多個執行緒的使用率，但請務必考慮非同步和多執行緒的概念。</span><span class="sxs-lookup"><span data-stu-id="ab204-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="ab204-109">事實上，這些都是分開的考慮，而不是另一種。</span><span class="sxs-lookup"><span data-stu-id="ab204-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="ab204-110">本文將更詳細地說明不同的概念。</span><span class="sxs-lookup"><span data-stu-id="ab204-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="ab204-111">非同步已定義</span><span class="sxs-lookup"><span data-stu-id="ab204-111">Asynchrony defined</span></span>

<span data-ttu-id="ab204-112">上一個重點是，非同步與多個執行緒的使用無關，值得進一步說明。</span><span class="sxs-lookup"><span data-stu-id="ab204-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="ab204-113">有時候相關的概念有三個，但彼此之間完全無關：</span><span class="sxs-lookup"><span data-stu-id="ab204-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="ab204-114">Concurrency在重迭的時間週期內執行多個計算時。</span><span class="sxs-lookup"><span data-stu-id="ab204-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="ab204-115">並行當多個計算或單一計算的數個部分在相同時間執行時。</span><span class="sxs-lookup"><span data-stu-id="ab204-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="ab204-116">非同步當一或多個計算可以與主要程式流程分開執行時。</span><span class="sxs-lookup"><span data-stu-id="ab204-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="ab204-117">這三個都是互相關聯的概念，但很容易混為一談，尤其是在一起使用時。</span><span class="sxs-lookup"><span data-stu-id="ab204-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="ab204-118">例如，您可能需要以平行方式執行多個非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="ab204-119">此關聯性並不表示平行處理原則或非同步暗示另一個。</span><span class="sxs-lookup"><span data-stu-id="ab204-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="ab204-120">如果您考慮「非同步」這個字的 etymology，則牽涉到兩個部分：</span><span class="sxs-lookup"><span data-stu-id="ab204-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="ab204-121">"a"，表示「不」。</span><span class="sxs-lookup"><span data-stu-id="ab204-121">"a", meaning "not".</span></span>
- <span data-ttu-id="ab204-122">「同步」，表示「同時」。</span><span class="sxs-lookup"><span data-stu-id="ab204-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="ab204-123">當您將這兩個詞彙結合在一起時，您會看到「非同步」表示「不是同時」。</span><span class="sxs-lookup"><span data-stu-id="ab204-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="ab204-124">這樣就完成了！</span><span class="sxs-lookup"><span data-stu-id="ab204-124">That's it!</span></span> <span data-ttu-id="ab204-125">這項定義中沒有平行存取或平行處理原則的含意。</span><span class="sxs-lookup"><span data-stu-id="ab204-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="ab204-126">在實務上也是如此。</span><span class="sxs-lookup"><span data-stu-id="ab204-126">This is also true in practice.</span></span>

<span data-ttu-id="ab204-127">在實際的情況下，F # 中的非同步計算排程為獨立于主要程式流程的執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="ab204-128">此獨立執行不表示並行或平行處理，也不表示計算一律會在背景中發生。</span><span class="sxs-lookup"><span data-stu-id="ab204-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="ab204-129">事實上，根據計算的本質和計算執行所在的環境而定，非同步計算甚至可以同步執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="ab204-130">您應該具備的主要重點是，非同步計算與主要程式流程無關。</span><span class="sxs-lookup"><span data-stu-id="ab204-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="ab204-131">雖然非同步計算的執行時間或方式有一些保證，但是有一些方法可協調和排程。</span><span class="sxs-lookup"><span data-stu-id="ab204-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="ab204-132">本文的其餘部分會探索 F # 非同步核心概念，以及如何使用 F # 內建的類型、函式和運算式。</span><span class="sxs-lookup"><span data-stu-id="ab204-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="ab204-133">核心概念</span><span class="sxs-lookup"><span data-stu-id="ab204-133">Core concepts</span></span>

<span data-ttu-id="ab204-134">在 F # 中，非同步程式設計是以三個核心概念為中心：</span><span class="sxs-lookup"><span data-stu-id="ab204-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="ab204-135">`Async<'T>`型別，表示可組合的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="ab204-136">`Async`模組函數可讓您排程非同步工作、撰寫非同步計算，以及轉換非同步結果。</span><span class="sxs-lookup"><span data-stu-id="ab204-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="ab204-137">`async { }`[計算運算式](../../language-reference/computation-expressions.md)，提供建立和控制非同步計算的便利語法。</span><span class="sxs-lookup"><span data-stu-id="ab204-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="ab204-138">您可以在下列範例中看到這三個概念：</span><span class="sxs-lookup"><span data-stu-id="ab204-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="ab204-139">在此範例中， `printTotalFileBytes` 函數的型別為 `string -> Async<unit>` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="ab204-140">呼叫函數並不會實際執行非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="ab204-141">相反地，它會傳回 `Async<unit>` ，作為要以非同步方式執行的工作 *規格* 。</span><span class="sxs-lookup"><span data-stu-id="ab204-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="ab204-142">它會 `Async.AwaitTask` 在其主體中呼叫，以將的結果轉換 <xref:System.IO.File.ReadAllBytesAsync%2A> 為適當的類型。</span><span class="sxs-lookup"><span data-stu-id="ab204-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="ab204-143">另一個重要的程式列是的呼叫 `Async.RunSynchronously` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="ab204-144">如果您想要實際執行 F # 非同步計算，這是啟動函式的其中一個非同步模組，您必須呼叫這些函式。</span><span class="sxs-lookup"><span data-stu-id="ab204-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="ab204-145">這是 c #/Visual 基本程式設計風格的基本差異 `async` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="ab204-146">在 F # 中，可以將非同步計算視為 **冷** 工作。</span><span class="sxs-lookup"><span data-stu-id="ab204-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="ab204-147">它們必須明確地啟動，才能實際執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="ab204-148">這有一些優點，因為它可讓您比使用 c # 或 Visual Basic 更輕鬆地結合和排序非同步工作。</span><span class="sxs-lookup"><span data-stu-id="ab204-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="ab204-149">合併非同步計算</span><span class="sxs-lookup"><span data-stu-id="ab204-149">Combine asynchronous computations</span></span>

<span data-ttu-id="ab204-150">以下是透過合併計算來建立上一個範例的範例：</span><span class="sxs-lookup"><span data-stu-id="ab204-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="ab204-151">如您所見， `main` 函數有更多元素。</span><span class="sxs-lookup"><span data-stu-id="ab204-151">As you can see, the `main` function has quite a few more elements.</span></span> <span data-ttu-id="ab204-152">就概念而言，它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ab204-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="ab204-153">使用將命令列引數轉換成一系列 `Async<unit>` 計算 `Seq.map` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-153">Transform the command-line arguments into a sequence of `Async<unit>` computations with `Seq.map`.</span></span>
2. <span data-ttu-id="ab204-154">建立 `Async<'T[]>` ，以 `printTotalFileBytes` 在執行時平行排程和執行計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="ab204-155">建立 `Async<unit>` 會執行平行計算的，並忽略其結果 (也就是 `unit[]`) 。</span><span class="sxs-lookup"><span data-stu-id="ab204-155">Create an `Async<unit>` that will run the parallel computation and ignore its result (which is a `unit[]`).</span></span>
4. <span data-ttu-id="ab204-156">明確執行整體組成的計算 `Async.RunSynchronously` ，並封鎖直到完成為止。</span><span class="sxs-lookup"><span data-stu-id="ab204-156">Explicitly run the overall composed computation with `Async.RunSynchronously`, blocking until it completes.</span></span>

<span data-ttu-id="ab204-157">當此程式執行時，會 `printTotalFileBytes` 針對每個命令列引數平行執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="ab204-158">由於非同步計算獨立執行程式流程，因此沒有任何定義的順序可列印其資訊並完成執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-158">Because asynchronous computations execute independently of program flow, there is no defined order in which they print their information and finish executing.</span></span> <span data-ttu-id="ab204-159">計算會以平行方式排程，但不保證其執行順序。</span><span class="sxs-lookup"><span data-stu-id="ab204-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="ab204-160">順序非同步計算</span><span class="sxs-lookup"><span data-stu-id="ab204-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="ab204-161">由於 `Async<'T>` 是工作的規格，而不是已執行的工作，因此您可以輕鬆地執行更複雜的轉換。</span><span class="sxs-lookup"><span data-stu-id="ab204-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="ab204-162">以下範例會針對一組非同步計算進行順序，讓它們在另一個之後執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="ab204-163">這會排程依 `printTotalFileBytes` 元素循序執行， `argv` 而非以平行方式進行排程。</span><span class="sxs-lookup"><span data-stu-id="ab204-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="ab204-164">因為後續的計算完成執行之後，每個後續的作業都不會排程，所以計算會排序，使其執行不會有任何重迭。</span><span class="sxs-lookup"><span data-stu-id="ab204-164">Because each successive operation will not be scheduled until after the preceding computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="ab204-165">重要的非同步模組函數</span><span class="sxs-lookup"><span data-stu-id="ab204-165">Important Async module functions</span></span>

<span data-ttu-id="ab204-166">當您在 F # 中撰寫非同步程式碼時，通常會與處理計算排程的架構互動。</span><span class="sxs-lookup"><span data-stu-id="ab204-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="ab204-167">不過，這不一定都是如此，因此最好瞭解可用來排程非同步工作的各種功能。</span><span class="sxs-lookup"><span data-stu-id="ab204-167">However, this is not always the case, so it is good to understand the various functions that can be used to schedule asynchronous work.</span></span>

<span data-ttu-id="ab204-168">因為 F # 非同步計算是工作的 _規格_ ，而不是表示已在執行中的工作，所以必須使用啟動函式來明確地啟動它們。</span><span class="sxs-lookup"><span data-stu-id="ab204-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="ab204-169">有許多 [非同步啟動方法](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) 在不同的內容中很有用。</span><span class="sxs-lookup"><span data-stu-id="ab204-169">There are many [Async starting methods](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) that are helpful in different contexts.</span></span> <span data-ttu-id="ab204-170">下一節將說明一些較常見的啟動函式。</span><span class="sxs-lookup"><span data-stu-id="ab204-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="ab204-171">Async. Async.startchild</span><span class="sxs-lookup"><span data-stu-id="ab204-171">Async.StartChild</span></span>

<span data-ttu-id="ab204-172">在非同步計算中啟動子計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="ab204-173">這可讓您同時執行多個非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="ab204-174">子系計算會與父計算共用解除標記。</span><span class="sxs-lookup"><span data-stu-id="ab204-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="ab204-175">如果取消父代計算，子計算也會取消。</span><span class="sxs-lookup"><span data-stu-id="ab204-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="ab204-176">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="ab204-177">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-177">When to use:</span></span>

- <span data-ttu-id="ab204-178">當您想要同時執行多個非同步計算（而不是一次一個），但未以平行方式排程它們時。</span><span class="sxs-lookup"><span data-stu-id="ab204-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="ab204-179">當您想要將子計算的存留期與父計算的存留期系結時。</span><span class="sxs-lookup"><span data-stu-id="ab204-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="ab204-180">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-180">What to watch out for:</span></span>

- <span data-ttu-id="ab204-181">啟動多個計算和 `Async.StartChild` 平行排程不同。</span><span class="sxs-lookup"><span data-stu-id="ab204-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="ab204-182">如果您想要以平行方式排程計算，請使用 `Async.Parallel` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="ab204-183">取消父計算將會觸發其啟動的所有子計算的取消。</span><span class="sxs-lookup"><span data-stu-id="ab204-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="ab204-184">Async. StartImmediate</span><span class="sxs-lookup"><span data-stu-id="ab204-184">Async.StartImmediate</span></span>

<span data-ttu-id="ab204-185">執行非同步計算，並在目前的作業系統執行緒上立即開始。</span><span class="sxs-lookup"><span data-stu-id="ab204-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="ab204-186">如果您需要在計算期間更新呼叫執行緒上的某個內容，這會很有説明。</span><span class="sxs-lookup"><span data-stu-id="ab204-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="ab204-187">例如，如果非同步計算必須更新 UI (例如更新進度列) ，則 `Async.StartImmediate` 應該使用。</span><span class="sxs-lookup"><span data-stu-id="ab204-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="ab204-188">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="ab204-189">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-189">When to use:</span></span>

- <span data-ttu-id="ab204-190">當您需要在非同步計算的過程中，更新呼叫執行緒上的某些內容。</span><span class="sxs-lookup"><span data-stu-id="ab204-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="ab204-191">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-191">What to watch out for:</span></span>

- <span data-ttu-id="ab204-192">非同步計算中的程式碼將會在發生排程的任何執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="ab204-193">如果執行緒是以某種方式區分，例如 UI 執行緒，這可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="ab204-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="ab204-194">在這種情況下， `Async.StartImmediate` 可能不適合使用。</span><span class="sxs-lookup"><span data-stu-id="ab204-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="ab204-195">Async. Async.startastask</span><span class="sxs-lookup"><span data-stu-id="ab204-195">Async.StartAsTask</span></span>

<span data-ttu-id="ab204-196">線上程集區中執行計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="ab204-197">傳回 <xref:System.Threading.Tasks.Task%601> ，當計算終止 (產生結果、擲回例外狀況或取消) 時，會在對應的狀態下完成。</span><span class="sxs-lookup"><span data-stu-id="ab204-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="ab204-198">如果未提供取消權杖，則會使用預設解除標記。</span><span class="sxs-lookup"><span data-stu-id="ab204-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="ab204-199">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="ab204-200">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-200">When to use:</span></span>

- <span data-ttu-id="ab204-201">當您需要呼叫 .NET API 時，它會產生 <xref:System.Threading.Tasks.Task%601> 以代表非同步計算的結果。</span><span class="sxs-lookup"><span data-stu-id="ab204-201">When you need to call into a .NET API that yields a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="ab204-202">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-202">What to watch out for:</span></span>

- <span data-ttu-id="ab204-203">此呼叫會配置額外的 `Task` 物件，如果經常使用，則會增加額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ab204-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="ab204-204">Async. Parallel</span><span class="sxs-lookup"><span data-stu-id="ab204-204">Async.Parallel</span></span>

<span data-ttu-id="ab204-205">排定要平行執行的非同步計算順序，以提供的順序產生結果陣列。</span><span class="sxs-lookup"><span data-stu-id="ab204-205">Schedules a sequence of asynchronous computations to be executed in parallel, yielding an array of results in the order they were supplied.</span></span> <span data-ttu-id="ab204-206">藉由指定參數，可以選擇性地調整/節流處理平行處理原則的程度 `maxDegreeOfParallelism` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreeOfParallelism` parameter.</span></span>

<span data-ttu-id="ab204-207">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreeOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="ab204-208">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-208">When to use it:</span></span>

- <span data-ttu-id="ab204-209">如果您需要同時執行一組計算，而不依賴它們的執行順序。</span><span class="sxs-lookup"><span data-stu-id="ab204-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="ab204-210">如果您不需要以平行方式排程的結果，直到它們全部完成為止。</span><span class="sxs-lookup"><span data-stu-id="ab204-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="ab204-211">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-211">What to watch out for:</span></span>

- <span data-ttu-id="ab204-212">一旦所有計算完成之後，您就只能存取產生的值陣列。</span><span class="sxs-lookup"><span data-stu-id="ab204-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="ab204-213">計算會在最後一次排程時執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="ab204-214">此行為表示您無法依賴它們的執行順序。</span><span class="sxs-lookup"><span data-stu-id="ab204-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="ab204-215">Async. 連續</span><span class="sxs-lookup"><span data-stu-id="ab204-215">Async.Sequential</span></span>

<span data-ttu-id="ab204-216">排定以傳遞的循序執行非同步計算的順序。</span><span class="sxs-lookup"><span data-stu-id="ab204-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="ab204-217">第一個計算將會執行，然後再執行一次，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ab204-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="ab204-218">不會以平行方式執行計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="ab204-219">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="ab204-220">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-220">When to use it:</span></span>

- <span data-ttu-id="ab204-221">如果您需要依序執行多個計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="ab204-222">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-222">What to watch out for:</span></span>

- <span data-ttu-id="ab204-223">一旦所有計算完成之後，您就只能存取產生的值陣列。</span><span class="sxs-lookup"><span data-stu-id="ab204-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="ab204-224">計算將依傳遞給此函式的循序執行，這可能表示在傳回結果之前，會經歷更多時間。</span><span class="sxs-lookup"><span data-stu-id="ab204-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="ab204-225">Async. Async.awaittask</span><span class="sxs-lookup"><span data-stu-id="ab204-225">Async.AwaitTask</span></span>

<span data-ttu-id="ab204-226">傳回非同步計算，等候指定的 <xref:System.Threading.Tasks.Task%601> 完成，並將其結果傳回為 `Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="ab204-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="ab204-227">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="ab204-228">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-228">When to use:</span></span>

- <span data-ttu-id="ab204-229">當您使用的 .NET API 會 <xref:System.Threading.Tasks.Task%601> 在 F # 非同步計算中傳回。</span><span class="sxs-lookup"><span data-stu-id="ab204-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="ab204-230">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-230">What to watch out for:</span></span>

- <span data-ttu-id="ab204-231">例外狀況會依照 <xref:System.AggregateException> 工作平行程式庫的慣例包裝，而這種行為與 F # async 通常會如何呈現例外狀況不同。</span><span class="sxs-lookup"><span data-stu-id="ab204-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library; this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="ab204-232">Async. Catch</span><span class="sxs-lookup"><span data-stu-id="ab204-232">Async.Catch</span></span>

<span data-ttu-id="ab204-233">建立異步計算，以執行指定的 `Async<'T>` ，傳回 `Async<Choice<'T, exn>>` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="ab204-234">如果指定的 `Async<'T>` 成功完成，則 `Choice1Of2` 會傳回具有結果值的。</span><span class="sxs-lookup"><span data-stu-id="ab204-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="ab204-235">如果例外狀況在完成之前擲回，則 `Choice2of2` 會傳回，並產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ab204-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="ab204-236">如果它是在由許多計算所組成的非同步計算上使用，且其中一個計算擲回例外狀況，則會完全停止包含的計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="ab204-237">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="ab204-238">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-238">When to use:</span></span>

- <span data-ttu-id="ab204-239">當您執行的非同步工作可能因例外狀況而失敗，而您想要在呼叫端中處理該例外狀況時。</span><span class="sxs-lookup"><span data-stu-id="ab204-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="ab204-240">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-240">What to watch out for:</span></span>

- <span data-ttu-id="ab204-241">當使用結合或排序的非同步計算時，如果其中一個「內部」計算擲回例外狀況，則會完全停止包含的計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="ab204-242">Async. Ignore</span><span class="sxs-lookup"><span data-stu-id="ab204-242">Async.Ignore</span></span>

<span data-ttu-id="ab204-243">建立會執行指定計算但捨棄其結果的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-243">Creates an asynchronous computation that runs the given computation but drops its result.</span></span>

<span data-ttu-id="ab204-244">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="ab204-245">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-245">When to use:</span></span>

- <span data-ttu-id="ab204-246">當您有不需要結果的非同步計算時。</span><span class="sxs-lookup"><span data-stu-id="ab204-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="ab204-247">這類似于 `ignore` 非非同步程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="ab204-247">This is analogous to the `ignore` function for non-asynchronous code.</span></span>

<span data-ttu-id="ab204-248">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-248">What to watch out for:</span></span>

- <span data-ttu-id="ab204-249">如果您必須使用 `Async.Ignore` ，因為您想要使用 `Async.Start` 或其他需要的函式 `Async<unit>` ，請考慮是否要捨棄結果。</span><span class="sxs-lookup"><span data-stu-id="ab204-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="ab204-250">避免只為了符合型別簽章而捨棄結果。</span><span class="sxs-lookup"><span data-stu-id="ab204-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="ab204-251">Async. Async.runsynchronously</span><span class="sxs-lookup"><span data-stu-id="ab204-251">Async.RunSynchronously</span></span>

<span data-ttu-id="ab204-252">執行非同步計算，並等候其在呼叫執行緒上的結果。</span><span class="sxs-lookup"><span data-stu-id="ab204-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="ab204-253">如果計算產生一個例外狀況，則會傳播例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ab204-253">Propagates an exception should the computation yield one.</span></span> <span data-ttu-id="ab204-254">此呼叫正在封鎖中。</span><span class="sxs-lookup"><span data-stu-id="ab204-254">This call is blocking.</span></span>

<span data-ttu-id="ab204-255">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-255">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="ab204-256">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ab204-256">When to use it:</span></span>

- <span data-ttu-id="ab204-257">如果需要，請在應用程式中只使用一次（在可執行檔的進入點）。</span><span class="sxs-lookup"><span data-stu-id="ab204-257">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="ab204-258">當您不在意效能，並且想要一次執行一組其他非同步作業時。</span><span class="sxs-lookup"><span data-stu-id="ab204-258">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="ab204-259">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-259">What to watch out for:</span></span>

- <span data-ttu-id="ab204-260">呼叫會 `Async.RunSynchronously` 封鎖呼叫的執行緒，直到執行完成為止。</span><span class="sxs-lookup"><span data-stu-id="ab204-260">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="ab204-261">Async. 開始</span><span class="sxs-lookup"><span data-stu-id="ab204-261">Async.Start</span></span>

<span data-ttu-id="ab204-262">啟動會線上程集區中傳回的非同步計算 `unit` 。</span><span class="sxs-lookup"><span data-stu-id="ab204-262">Starts an asynchronous computation that returns `unit` in the thread pool.</span></span> <span data-ttu-id="ab204-263">不會等待其完成，並（或）觀察到例外狀況結果。</span><span class="sxs-lookup"><span data-stu-id="ab204-263">Doesn't wait for its completion and/or observe an exception outcome.</span></span> <span data-ttu-id="ab204-264">開頭的嵌套計算 `Async.Start` 會與呼叫它們的父代計算分開啟動; 其存留期不會系結至任何父代計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-264">Nested computations started with `Async.Start` are started independently of the parent computation that called them; their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="ab204-265">如果取消父代計算，則不會取消任何子計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="ab204-266">簽章：</span><span class="sxs-lookup"><span data-stu-id="ab204-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="ab204-267">僅用於：</span><span class="sxs-lookup"><span data-stu-id="ab204-267">Use only when:</span></span>

- <span data-ttu-id="ab204-268">您有不產生結果及/或需要處理一項的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ab204-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="ab204-269">非同步計算完成時，您不需要知道。</span><span class="sxs-lookup"><span data-stu-id="ab204-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="ab204-270">您不在意非同步計算執行所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ab204-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="ab204-271">您不需要留意或報告執行所產生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ab204-271">You don't have any need to be aware of or report exceptions resulting from the execution.</span></span>

<span data-ttu-id="ab204-272">要注意的事項：</span><span class="sxs-lookup"><span data-stu-id="ab204-272">What to watch out for:</span></span>

- <span data-ttu-id="ab204-273">從開始計算所引發的例外狀況 `Async.Start` 不會傳播至呼叫端。</span><span class="sxs-lookup"><span data-stu-id="ab204-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="ab204-274">呼叫堆疊將會完全展開。</span><span class="sxs-lookup"><span data-stu-id="ab204-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="ab204-275">任何工作 (例如 `printfn`) 啟動的呼叫都 `Async.Start` 不會導致程式執行的主要執行緒發生效果。</span><span class="sxs-lookup"><span data-stu-id="ab204-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="ab204-276">與 .NET 交互操作</span><span class="sxs-lookup"><span data-stu-id="ab204-276">Interoperate with .NET</span></span>

<span data-ttu-id="ab204-277">您可以使用 .NET 程式庫或使用 [async/await](../../../standard/async.md)樣式非同步程式設計的 c # 程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="ab204-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="ab204-278">因為 c # 和大部分的 .NET 程式庫都使用 <xref:System.Threading.Tasks.Task%601> 和 <xref:System.Threading.Tasks.Task> 類型作為其核心抽象概念，而不是 `Async<'T>` ，所以您必須在這兩種方法之間的界限之間進行非同步。</span><span class="sxs-lookup"><span data-stu-id="ab204-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="ab204-279">如何使用 .NET async 和 `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="ab204-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="ab204-280">使用使用 (的 .NET 非同步程式庫和程式碼基底 <xref:System.Threading.Tasks.Task%601> ，) 具有傳回值的非同步計算相當簡單，而且具備 F # 的內建支援。</span><span class="sxs-lookup"><span data-stu-id="ab204-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="ab204-281">您可以使用 `Async.AwaitTask` 函數來等候 .net 非同步計算：</span><span class="sxs-lookup"><span data-stu-id="ab204-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="ab204-282">您可以使用 `Async.StartAsTask` 函數，將非同步計算行程給 .net 呼叫端：</span><span class="sxs-lookup"><span data-stu-id="ab204-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="ab204-283">如何使用 .NET async 和 `Task`</span><span class="sxs-lookup"><span data-stu-id="ab204-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="ab204-284">若要使用的 Api 使用 <xref:System.Threading.Tasks.Task> (也就是不會傳回值) 的 .net 非同步計算，您可能需要加入其他函式，以將轉換成 `Async<'T>` <xref:System.Threading.Tasks.Task> ：</span><span class="sxs-lookup"><span data-stu-id="ab204-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="ab204-285">已經有 `Async.AwaitTask` 接受 <xref:System.Threading.Tasks.Task> as 輸入的。</span><span class="sxs-lookup"><span data-stu-id="ab204-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="ab204-286">使用這個與先前定義的函 `startTaskFromAsyncUnit` 式，您可以 <xref:System.Threading.Tasks.Task> 從 F # 非同步計算啟動和等候類型。</span><span class="sxs-lookup"><span data-stu-id="ab204-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="ab204-287">多執行緒的關聯性</span><span class="sxs-lookup"><span data-stu-id="ab204-287">Relationship to multi-threading</span></span>

<span data-ttu-id="ab204-288">雖然這篇文章中提到執行緒，但是有兩個重要事項要記住：</span><span class="sxs-lookup"><span data-stu-id="ab204-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="ab204-289">非同步計算和執行緒之間沒有任何關聯性，除非在目前的執行緒上明確啟動。</span><span class="sxs-lookup"><span data-stu-id="ab204-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="ab204-290">F # 中的非同步程式設計不是多重執行緒的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="ab204-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="ab204-291">例如，根據工作的本質而定，計算實際上可能會在其呼叫端的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="ab204-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="ab204-292">計算也可以線上程之間「跳躍」，以在一小段時間內進行處理，以在「等候」 (期間（例如，當網路通話處於傳輸) 時執行有用的工作）。</span><span class="sxs-lookup"><span data-stu-id="ab204-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="ab204-293">雖然 F # 提供了一些功能，可讓您在目前的執行緒上啟動非同步計算 (或明確地不) 目前的執行緒上，非同步通常不會與特定的執行緒策略相關聯。</span><span class="sxs-lookup"><span data-stu-id="ab204-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab204-294">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab204-294">See also</span></span>

- [<span data-ttu-id="ab204-295">F # 非同步程式設計模型</span><span class="sxs-lookup"><span data-stu-id="ab204-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="ab204-296">Jet .com 的 F # 非同步指南</span><span class="sxs-lookup"><span data-stu-id="ab204-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="ab204-297">適用于有趣和收益之非同步程式設計指南的 F #</span><span class="sxs-lookup"><span data-stu-id="ab204-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="ab204-298">C # 中的非同步和 F #： C 中的非同步陷阱#</span><span class="sxs-lookup"><span data-stu-id="ab204-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
