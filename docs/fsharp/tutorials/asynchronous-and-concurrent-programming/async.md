---
title: 非同步編程
description: 瞭解 F# 如何基於從核心函數程式設計概念派生的語言級程式設計模型為非同步提供乾淨的支援。
ms.date: 12/17/2018
ms.openlocfilehash: 0a7d400c9778e30d6b25798239f12b7b2b0e3d82
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021516"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="ee0df-103">F 中的非同步編程\#</span><span class="sxs-lookup"><span data-stu-id="ee0df-103">Async programming in F\#</span></span>

<span data-ttu-id="ee0df-104">非同步程式設計是一種機制,對於現代應用程式來說,由於各種原因至關重要。</span><span class="sxs-lookup"><span data-stu-id="ee0df-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="ee0df-105">大多數開發人員會遇到兩個主要用例:</span><span class="sxs-lookup"><span data-stu-id="ee0df-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="ee0df-106">顯示一個伺服器程序,該伺服器程序可以服務大量併發傳入請求,同時最小化請求處理時佔用的系統資源,等待來自該行程外部的系統或服務的輸入</span><span class="sxs-lookup"><span data-stu-id="ee0df-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="ee0df-107">維護回應靈敏的 UI 或主線程,同時推進後台工作</span><span class="sxs-lookup"><span data-stu-id="ee0df-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="ee0df-108">儘管後台工作通常涉及多個線程的利用,但單獨考慮非同步和多線程的概念非常重要。</span><span class="sxs-lookup"><span data-stu-id="ee0df-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="ee0df-109">事實上,它們是單獨的問題,一個並不意味著另一個。</span><span class="sxs-lookup"><span data-stu-id="ee0df-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="ee0df-110">本文更詳細地介紹不同的概念。</span><span class="sxs-lookup"><span data-stu-id="ee0df-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="ee0df-111">定義非同步</span><span class="sxs-lookup"><span data-stu-id="ee0df-111">Asynchrony defined</span></span>

<span data-ttu-id="ee0df-112">前一點 -非同步與多個線程的利用率無關 - 值得進一步解釋一下。</span><span class="sxs-lookup"><span data-stu-id="ee0df-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="ee0df-113">有三個概念有時相關,但嚴格地相互獨立:</span><span class="sxs-lookup"><span data-stu-id="ee0df-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="ee0df-114">併發性;在重疊的時間段中執行多個計算時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="ee0df-115">並行性;當多個計算或單個計算的幾個部分完全同時運行時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="ee0df-116">異步;當一個或多個計算可以獨立於主程式流執行時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="ee0df-117">這三個概念都是正交概念,但很容易組合,尤其是當它們一起使用時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="ee0df-118">例如,您可能需要並行執行多個非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="ee0df-119">這種關係並不意味著並行性或異步性相互暗示。</span><span class="sxs-lookup"><span data-stu-id="ee0df-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="ee0df-120">如果考慮「非同步」一詞的詞源,則涉及兩個部分:</span><span class="sxs-lookup"><span data-stu-id="ee0df-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="ee0df-121">"a",意思是"不"。</span><span class="sxs-lookup"><span data-stu-id="ee0df-121">"a", meaning "not".</span></span>
- <span data-ttu-id="ee0df-122">"同步",意思是"同時"。</span><span class="sxs-lookup"><span data-stu-id="ee0df-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="ee0df-123">將這兩個術語放在一起時,您將看到"非同步"表示"不是同時"</span><span class="sxs-lookup"><span data-stu-id="ee0df-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="ee0df-124">就這麼簡單！</span><span class="sxs-lookup"><span data-stu-id="ee0df-124">That's it!</span></span> <span data-ttu-id="ee0df-125">這個定義中沒有併發性或並行性的含義。</span><span class="sxs-lookup"><span data-stu-id="ee0df-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="ee0df-126">在實踐中也是如此。</span><span class="sxs-lookup"><span data-stu-id="ee0df-126">This is also true in practice.</span></span>

<span data-ttu-id="ee0df-127">實際上,F# 中的非同步計算計畫獨立於主程式流執行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="ee0df-128">這種獨立執行並不意味著併發性或並行性,也不表示計算總是在後台發生。</span><span class="sxs-lookup"><span data-stu-id="ee0df-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="ee0df-129">事實上,非同步計算甚至可以同步執行,具體取決於計算的性質和計算執行的環境。</span><span class="sxs-lookup"><span data-stu-id="ee0df-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="ee0df-130">您應該有的主要要點是非同步計算獨立於主程式流。</span><span class="sxs-lookup"><span data-stu-id="ee0df-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="ee0df-131">儘管對異步計算執行的時間或方式幾乎沒有保證,但有一些方法來編排和調度它們。</span><span class="sxs-lookup"><span data-stu-id="ee0df-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="ee0df-132">本文的其餘部分將探討 F# 異步的核心概念以及如何使用 F# 中內置的類型、函數和運算式。</span><span class="sxs-lookup"><span data-stu-id="ee0df-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="ee0df-133">核心概念</span><span class="sxs-lookup"><span data-stu-id="ee0df-133">Core concepts</span></span>

<span data-ttu-id="ee0df-134">在 F# 中,非同步程式設計圍繞三個核心概念:</span><span class="sxs-lookup"><span data-stu-id="ee0df-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="ee0df-135">表示`Async<'T>`可組合非同步計算的類型。</span><span class="sxs-lookup"><span data-stu-id="ee0df-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="ee0df-136">模組`Async`函數允許您安排非同步工作、撰寫非同步計算並轉換同步結果。</span><span class="sxs-lookup"><span data-stu-id="ee0df-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="ee0df-137">`async { }`[計算運算式](../../language-reference/computation-expressions.md),為構建和控制非同步計算提供方便的語法。</span><span class="sxs-lookup"><span data-stu-id="ee0df-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="ee0df-138">您可以在以下範例中看到以下三個概念:</span><span class="sxs-lookup"><span data-stu-id="ee0df-138">You can see these three concepts in the following example:</span></span>

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

<span data-ttu-id="ee0df-139">這個選項,`printTotalFileBytes`函數的類型`string -> Async<unit>`為 。</span><span class="sxs-lookup"><span data-stu-id="ee0df-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="ee0df-140">調用函數實際上不會執行非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="ee0df-141">相反,它傳`Async<unit>`回 充當以非同步方式執行*的工作規範的*。</span><span class="sxs-lookup"><span data-stu-id="ee0df-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="ee0df-142">它在其`Async.AwaitTask`正文中調用,它將<xref:System.IO.File.ReadAllBytesAsync%2A>的結果 轉換為適當的類型。</span><span class="sxs-lookup"><span data-stu-id="ee0df-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="ee0df-143">另一個重要的行是呼叫`Async.RunSynchronously`。</span><span class="sxs-lookup"><span data-stu-id="ee0df-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="ee0df-144">這是 Async 模組啟動函數之一,如果要實際執行 F# 異步計算,則需要調用這些函數。</span><span class="sxs-lookup"><span data-stu-id="ee0df-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="ee0df-145">這與 C#/可視化`async`基本 程式設計風格有根本區別。</span><span class="sxs-lookup"><span data-stu-id="ee0df-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="ee0df-146">在 F# 中,非同步計算可以視為**冷工**。</span><span class="sxs-lookup"><span data-stu-id="ee0df-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="ee0df-147">它們必須顯式開始實際執行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="ee0df-148">這具有一些優點,因為它允許您比 C# 或 Visual Basic 更容易組合和序列非同步工作。</span><span class="sxs-lookup"><span data-stu-id="ee0df-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="ee0df-149">合併非同步計算</span><span class="sxs-lookup"><span data-stu-id="ee0df-149">Combine asynchronous computations</span></span>

<span data-ttu-id="ee0df-150">下面是一個通過組合計算構建在前一個範例的基礎上的範例:</span><span class="sxs-lookup"><span data-stu-id="ee0df-150">Here is an example that builds upon the previous one by combining computations:</span></span>

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

<span data-ttu-id="ee0df-151">正如您所看到的,該`main`函數還有更多的調用。</span><span class="sxs-lookup"><span data-stu-id="ee0df-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="ee0df-152">從概念上講,它執行以下操作:</span><span class="sxs-lookup"><span data-stu-id="ee0df-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="ee0df-153">將命令列參數轉換為`Async<unit>``Array.map`具有的計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="ee0df-154">創建一`Async<'T[]>`個計劃並在運行時並行`printTotalFileBytes`運行計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="ee0df-155">建立將`Async<unit>`執行並行計算並忽略此結果的</span><span class="sxs-lookup"><span data-stu-id="ee0df-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="ee0df-156">顯式運行最後一個計算`Async.RunSynchronously`,直到完成。</span><span class="sxs-lookup"><span data-stu-id="ee0df-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it completes.</span></span>

<span data-ttu-id="ee0df-157">執行此程式時,`printTotalFileBytes`每個命令列參數並行執行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="ee0df-158">由於非同步計算獨立於程式流執行,因此它們無法按順序列印其資訊並完成執行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="ee0df-159">計算將並行計劃,但不能保證其執行順序。</span><span class="sxs-lookup"><span data-stu-id="ee0df-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="ee0df-160">序列非同步計算</span><span class="sxs-lookup"><span data-stu-id="ee0df-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="ee0df-161">因為`Async<'T>`是工作規範,而不是已經運行的任務,因此可以輕鬆地執行更複雜的轉換。</span><span class="sxs-lookup"><span data-stu-id="ee0df-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="ee0df-162">下面是一個示例,它對一組 Async 計算進行排序,以便它們逐一執行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

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

<span data-ttu-id="ee0df-163">這將按計劃`printTotalFileBytes`按的元素的順序執行,`argv`而不是並行調度它們。</span><span class="sxs-lookup"><span data-stu-id="ee0df-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="ee0df-164">由於下一項不會計劃,直到最後一次計算完成執行后,計算將進行排序,以便其執行中沒有重疊。</span><span class="sxs-lookup"><span data-stu-id="ee0df-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="ee0df-165">重要的非同步模組功能</span><span class="sxs-lookup"><span data-stu-id="ee0df-165">Important Async module functions</span></span>

<span data-ttu-id="ee0df-166">在 F# 中編寫非同步碼時,通常會與處理計算計畫的框架進行互動。</span><span class="sxs-lookup"><span data-stu-id="ee0df-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="ee0df-167">但是,情況並非總是如此,因此最好了解各種啟動函數來安排非同步工作。</span><span class="sxs-lookup"><span data-stu-id="ee0df-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="ee0df-168">由於 F# 非同步計算是工作_規範_,而不是已執行的工作的表示形式,因此必須顯式從啟動函數開始。</span><span class="sxs-lookup"><span data-stu-id="ee0df-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="ee0df-169">有許多[Async 啟動函數](https://msdn.microsoft.com/library/ee370232.aspx)在不同的上下文中非常有用。</span><span class="sxs-lookup"><span data-stu-id="ee0df-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="ee0df-170">以下部分介紹一些更常見的起始函數。</span><span class="sxs-lookup"><span data-stu-id="ee0df-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="ee0df-171">非同步.開始兒童</span><span class="sxs-lookup"><span data-stu-id="ee0df-171">Async.StartChild</span></span>

<span data-ttu-id="ee0df-172">在非同步計算中啟動子計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="ee0df-173">這允許同時執行多個非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="ee0df-174">子計算與父計算共用取消權杖。</span><span class="sxs-lookup"><span data-stu-id="ee0df-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="ee0df-175">如果取消父計算,則子計算也會取消。</span><span class="sxs-lookup"><span data-stu-id="ee0df-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="ee0df-176">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="ee0df-177">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-177">When to use:</span></span>

- <span data-ttu-id="ee0df-178">當您要同時執行多個非同步計算,而不是一次執行一個非同步計算時,卻不希望將它們同時計畫。</span><span class="sxs-lookup"><span data-stu-id="ee0df-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="ee0df-179">當您希望將子計算的存留期與父計算的存留期綁定時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="ee0df-180">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-180">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-181">使用`Async.StartChild`啟動多個計算與並行調度計算計算策略不同。</span><span class="sxs-lookup"><span data-stu-id="ee0df-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="ee0df-182">如果要並行計劃計算,請使用`Async.Parallel`。</span><span class="sxs-lookup"><span data-stu-id="ee0df-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="ee0df-183">取消父計算將觸發取消它啟動的所有子計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="ee0df-184">非同步.立即啟動</span><span class="sxs-lookup"><span data-stu-id="ee0df-184">Async.StartImmediate</span></span>

<span data-ttu-id="ee0df-185">運行非同步計算,立即開始在當前作業系統線程上。</span><span class="sxs-lookup"><span data-stu-id="ee0df-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="ee0df-186">如果您在計算期間需要更新調用線程上的內容,這非常有用。</span><span class="sxs-lookup"><span data-stu-id="ee0df-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="ee0df-187">例如,如果非同步計算必須更新 UI(如更新進度列),則`Async.StartImmediate`應使用。</span><span class="sxs-lookup"><span data-stu-id="ee0df-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="ee0df-188">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="ee0df-189">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-189">When to use:</span></span>

- <span data-ttu-id="ee0df-190">當您需要在非同步計算中更新呼叫線程上的內容時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="ee0df-191">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-191">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-192">非同步計算中的代碼將在預定的任何線程上運行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="ee0df-193">如果該線程在某種程度上是敏感的(如UI線程),則可能會有問題。</span><span class="sxs-lookup"><span data-stu-id="ee0df-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="ee0df-194">在這種情況下,`Async.StartImmediate`很可能不適合使用。</span><span class="sxs-lookup"><span data-stu-id="ee0df-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="ee0df-195">非同步.StartAsTask</span><span class="sxs-lookup"><span data-stu-id="ee0df-195">Async.StartAsTask</span></span>

<span data-ttu-id="ee0df-196">在線程池中執行計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="ee0df-197">返回將在<xref:System.Threading.Tasks.Task%601>計算終止后在相應狀態上完成的的(生成結果、引發異常或被取消)。</span><span class="sxs-lookup"><span data-stu-id="ee0df-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="ee0df-198">如果未提供取消權杖,則使用預設取消權杖。</span><span class="sxs-lookup"><span data-stu-id="ee0df-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="ee0df-199">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="ee0df-200">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-200">When to use:</span></span>

- <span data-ttu-id="ee0df-201">當您需要調用 .NET API<xref:System.Threading.Tasks.Task%601>時,該 API 希望 表示非同步計算的結果。</span><span class="sxs-lookup"><span data-stu-id="ee0df-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="ee0df-202">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-202">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-203">此調用將分配一個`Task`附加物件,如果經常使用,可能會增加開銷。</span><span class="sxs-lookup"><span data-stu-id="ee0df-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="ee0df-204">非同步.並行</span><span class="sxs-lookup"><span data-stu-id="ee0df-204">Async.Parallel</span></span>

<span data-ttu-id="ee0df-205">計劃要並行執行的非同步計算序列。</span><span class="sxs-lookup"><span data-stu-id="ee0df-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="ee0df-206">通過指定`maxDegreesOfParallelism`參數,可以選擇調整/限制並行性的程度。</span><span class="sxs-lookup"><span data-stu-id="ee0df-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="ee0df-207">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="ee0df-208">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-208">When to use it:</span></span>

- <span data-ttu-id="ee0df-209">如果需要同時運行一組計算,並且不依賴於它們的執行順序。</span><span class="sxs-lookup"><span data-stu-id="ee0df-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="ee0df-210">如果不需要並行計劃計算的結果,直到它們全部完成。</span><span class="sxs-lookup"><span data-stu-id="ee0df-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="ee0df-211">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-211">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-212">只有在所有計算完成後,才能訪問生成的值陣列。</span><span class="sxs-lookup"><span data-stu-id="ee0df-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="ee0df-213">計算將在計劃結束時運行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="ee0df-214">此行為意味著您不能依賴他們的執行順序。</span><span class="sxs-lookup"><span data-stu-id="ee0df-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="ee0df-215">非同步。順序</span><span class="sxs-lookup"><span data-stu-id="ee0df-215">Async.Sequential</span></span>

<span data-ttu-id="ee0df-216">計劃一系列非同步計算,以便按傳遞順序執行。</span><span class="sxs-lookup"><span data-stu-id="ee0df-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="ee0df-217">將執行第一個計算,然後執行下一個計算,等等。</span><span class="sxs-lookup"><span data-stu-id="ee0df-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="ee0df-218">不會並行執行任何計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="ee0df-219">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="ee0df-220">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-220">When to use it:</span></span>

- <span data-ttu-id="ee0df-221">如果需要按順序執行多個計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="ee0df-222">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-222">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-223">只有在所有計算完成後,才能訪問生成的值陣列。</span><span class="sxs-lookup"><span data-stu-id="ee0df-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="ee0df-224">計算將以傳遞給此函數的順序運行,這可能意味著在返回結果之前將經過更多的時間。</span><span class="sxs-lookup"><span data-stu-id="ee0df-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="ee0df-225">非同步.Await任務</span><span class="sxs-lookup"><span data-stu-id="ee0df-225">Async.AwaitTask</span></span>

<span data-ttu-id="ee0df-226">返回一個非同步計算,該計算等待給定<xref:System.Threading.Tasks.Task%601>的計算完成,並將其結果作為`Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="ee0df-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="ee0df-227">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="ee0df-228">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-228">When to use:</span></span>

- <span data-ttu-id="ee0df-229">使用 .NET API<xref:System.Threading.Tasks.Task%601>時,API 在 F# 非同步計算中傳回 。</span><span class="sxs-lookup"><span data-stu-id="ee0df-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="ee0df-230">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-230">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-231">異常按照任務並行庫<xref:System.AggregateException>的約定進行包裝,並且此行為與 F# 異步通常顯示異常的方式不同。</span><span class="sxs-lookup"><span data-stu-id="ee0df-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="ee0df-232">非同步.捕獲</span><span class="sxs-lookup"><span data-stu-id="ee0df-232">Async.Catch</span></span>

<span data-ttu-id="ee0df-233">建立一個非同步計算,該計算執行`Async<'T>`給定的`Async<Choice<'T, exn>>`,傳回 。</span><span class="sxs-lookup"><span data-stu-id="ee0df-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="ee0df-234">如果給定`Async<'T>`完成成功,則傳回`Choice1Of2`有結果值的傳回 。</span><span class="sxs-lookup"><span data-stu-id="ee0df-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="ee0df-235">如果在異常完成之前引發異常,`Choice2of2`則返回,並引發異常。</span><span class="sxs-lookup"><span data-stu-id="ee0df-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="ee0df-236">如果它用於由許多計算組成的非同步計算,並且其中一個計算引發異常,則包羅萬象的計算將完全停止。</span><span class="sxs-lookup"><span data-stu-id="ee0df-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="ee0df-237">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="ee0df-238">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-238">When to use:</span></span>

- <span data-ttu-id="ee0df-239">執行非同步工作時,可能會因異常而失敗,並且希望在調用方中處理該異常。</span><span class="sxs-lookup"><span data-stu-id="ee0df-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="ee0df-240">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-240">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-241">使用組合或序列非同步計算時,如果包包含計算的內部"計算之一引發異常,則包包含計算將完全停止。</span><span class="sxs-lookup"><span data-stu-id="ee0df-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="ee0df-242">非同步.忽略</span><span class="sxs-lookup"><span data-stu-id="ee0df-242">Async.Ignore</span></span>

<span data-ttu-id="ee0df-243">建立運行給定計算並忽略其結果的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="ee0df-244">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="ee0df-245">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-245">When to use:</span></span>

- <span data-ttu-id="ee0df-246">當您有不需要結果的非同步計算時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="ee0df-247">這類似於非異步`ignore`代碼的代碼。</span><span class="sxs-lookup"><span data-stu-id="ee0df-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="ee0df-248">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-248">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-249">如果由於希望使用`Async.Ignore``Async.Start`或其他需要`Async<unit>`的功能而必須使用,請考慮丟棄結果是否正常。</span><span class="sxs-lookup"><span data-stu-id="ee0df-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="ee0df-250">為了避免僅丟棄結果以適合類型簽名。</span><span class="sxs-lookup"><span data-stu-id="ee0df-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="ee0df-251">非同步同步執行</span><span class="sxs-lookup"><span data-stu-id="ee0df-251">Async.RunSynchronously</span></span>

<span data-ttu-id="ee0df-252">運行非同步計算,並在調用線程上等待其結果。</span><span class="sxs-lookup"><span data-stu-id="ee0df-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="ee0df-253">此呼叫已阻塞。</span><span class="sxs-lookup"><span data-stu-id="ee0df-253">This call is blocking.</span></span>

<span data-ttu-id="ee0df-254">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-254">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="ee0df-255">使用時機：</span><span class="sxs-lookup"><span data-stu-id="ee0df-255">When to use it:</span></span>

- <span data-ttu-id="ee0df-256">如果需要,請僅在應用程式中使用它一次 - 在可執行檔的入口點。</span><span class="sxs-lookup"><span data-stu-id="ee0df-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="ee0df-257">當您不關心性能並希望同時執行一組其他非同步操作時。</span><span class="sxs-lookup"><span data-stu-id="ee0df-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="ee0df-258">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-258">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-259">調用`Async.RunSynchronously`阻止調用線程,直到執行完成。</span><span class="sxs-lookup"><span data-stu-id="ee0df-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="ee0df-260">非同步.開始</span><span class="sxs-lookup"><span data-stu-id="ee0df-260">Async.Start</span></span>

<span data-ttu-id="ee0df-261">線上程池中啟動可非同步計算,計算`unit`傳回 。</span><span class="sxs-lookup"><span data-stu-id="ee0df-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="ee0df-262">不等待結果。</span><span class="sxs-lookup"><span data-stu-id="ee0df-262">Doesn't wait for its result.</span></span> <span data-ttu-id="ee0df-263">開始的`Async.Start`嵌套計算獨立於調用它們的父計算開始。</span><span class="sxs-lookup"><span data-stu-id="ee0df-263">Nested computations started with `Async.Start` are started independently of the parent computation that called them.</span></span> <span data-ttu-id="ee0df-264">其存留期不與任何父計算相關聯。</span><span class="sxs-lookup"><span data-stu-id="ee0df-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="ee0df-265">如果取消父計算,則不會取消子計算。</span><span class="sxs-lookup"><span data-stu-id="ee0df-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="ee0df-266">簽章：</span><span class="sxs-lookup"><span data-stu-id="ee0df-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="ee0df-267">只在:</span><span class="sxs-lookup"><span data-stu-id="ee0df-267">Use only when:</span></span>

- <span data-ttu-id="ee0df-268">非同步計算不會產生結果和/或需要處理一個結果。</span><span class="sxs-lookup"><span data-stu-id="ee0df-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="ee0df-269">您無需知道非同步計算何時完成。</span><span class="sxs-lookup"><span data-stu-id="ee0df-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="ee0df-270">您不關心非同步計算執行哪個線程。</span><span class="sxs-lookup"><span data-stu-id="ee0df-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="ee0df-271">您無需瞭解或報告任務產生的異常。</span><span class="sxs-lookup"><span data-stu-id="ee0df-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="ee0df-272">需要注意的:</span><span class="sxs-lookup"><span data-stu-id="ee0df-272">What to watch out for:</span></span>

- <span data-ttu-id="ee0df-273">由開始`Async.Start`計算引發的異常不會傳播到調用方。</span><span class="sxs-lookup"><span data-stu-id="ee0df-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="ee0df-274">調用堆疊將完全解功能。</span><span class="sxs-lookup"><span data-stu-id="ee0df-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="ee0df-275">任何開始的工作(如調用`printfn``Async.Start`) 不會導致程式執行的主線程上發生效果。</span><span class="sxs-lookup"><span data-stu-id="ee0df-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="ee0df-276">與 .NET 互通</span><span class="sxs-lookup"><span data-stu-id="ee0df-276">Interoperate with .NET</span></span>

<span data-ttu-id="ee0df-277">您可能正在使用使用[非同步/await-](../../../standard/async.md)樣式非同步程式設計的 .NET 庫或 C# 程式庫。</span><span class="sxs-lookup"><span data-stu-id="ee0df-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="ee0df-278">由於 C# 和大多數 .NET 庫使用<xref:System.Threading.Tasks.Task%601><xref:System.Threading.Tasks.Task>和 類型作為`Async<'T>`其核心抽象,而不是 ,您必須跨越這兩種非同步方法之間的邊界。</span><span class="sxs-lookup"><span data-stu-id="ee0df-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="ee0df-279">如何使用 .NET 同步與`Task<T>`</span><span class="sxs-lookup"><span data-stu-id="ee0df-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="ee0df-280">使用 .NET 非同步庫和代碼<xref:System.Threading.Tasks.Task%601>庫( 即具有返回值的非同步計算)非常簡單,並且具有 F# 的內置支援。</span><span class="sxs-lookup"><span data-stu-id="ee0df-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="ee0df-281">可以使用函數`Async.AwaitTask`等待 .NET 同步計算:</span><span class="sxs-lookup"><span data-stu-id="ee0df-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="ee0df-282">可以使用函數`Async.StartAsTask`將非同步計算到 .NET 呼叫者:</span><span class="sxs-lookup"><span data-stu-id="ee0df-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="ee0df-283">如何使用 .NET 同步與`Task`</span><span class="sxs-lookup"><span data-stu-id="ee0df-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="ee0df-284">要使用使用的<xref:System.Threading.Tasks.Task>API (即 .NET 非同步計算不傳回值),您可能需要新增`Async<'T>`一個轉換為的<xref:System.Threading.Tasks.Task>其他函數:</span><span class="sxs-lookup"><span data-stu-id="ee0df-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="ee0df-285">已經有一個`Async.AwaitTask`接受<xref:System.Threading.Tasks.Task>作為 輸入的。</span><span class="sxs-lookup"><span data-stu-id="ee0df-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="ee0df-286">使用此函數和以前定義的`startTaskFromAsyncUnit`函數,可以從 F# 異<xref:System.Threading.Tasks.Task>步計算開始和等待類型。</span><span class="sxs-lookup"><span data-stu-id="ee0df-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="ee0df-287">與多線程的關係</span><span class="sxs-lookup"><span data-stu-id="ee0df-287">Relationship to multi-threading</span></span>

<span data-ttu-id="ee0df-288">儘管本文中提到了線程,但有兩件重要的事情需要記住:</span><span class="sxs-lookup"><span data-stu-id="ee0df-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="ee0df-289">除非在當前線程上顯式啟動,否則非同步計算和線程之間沒有關聯。</span><span class="sxs-lookup"><span data-stu-id="ee0df-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="ee0df-290">F# 中的非同步程式設計不是多線程的抽象。</span><span class="sxs-lookup"><span data-stu-id="ee0df-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="ee0df-291">例如,計算實際上可能在其調用方的線程上運行,具體取決於工作的性質。</span><span class="sxs-lookup"><span data-stu-id="ee0df-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="ee0df-292">計算還可以「跳轉」線程之間,借用它們少量時間在「等待」期間(例如網路呼叫傳輸時)之間執行有用的工作。</span><span class="sxs-lookup"><span data-stu-id="ee0df-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="ee0df-293">儘管 F# 提供了在當前線程(或顯式不在當前線程上)啟動非同步計算的一些功能,但異步通常不與特定的線程策略相關聯。</span><span class="sxs-lookup"><span data-stu-id="ee0df-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee0df-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee0df-294">See also</span></span>

- [<span data-ttu-id="ee0df-295">F# 非同步程式設計模型</span><span class="sxs-lookup"><span data-stu-id="ee0df-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="ee0df-296">Jet.com 的 F# 非同步指南</span><span class="sxs-lookup"><span data-stu-id="ee0df-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="ee0df-297">F# 用於娛樂和盈利的非同步程式指導</span><span class="sxs-lookup"><span data-stu-id="ee0df-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="ee0df-298">C# 和 F# 中的非同步:C 中的非同步#</span><span class="sxs-lookup"><span data-stu-id="ee0df-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
