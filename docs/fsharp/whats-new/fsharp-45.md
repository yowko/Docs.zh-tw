---
title: F# 4.5 - F# 指南中的新增功能
description: 獲取 F# 4.5 中提供的新功能的概述。
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186128"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="43a57-103">F# 4.5 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="43a57-103">What's new in F# 4.5</span></span>

<span data-ttu-id="43a57-104">F# 4.5 為 F# 語言添加了多項改進。</span><span class="sxs-lookup"><span data-stu-id="43a57-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="43a57-105">這些功能中有許多被添加到一起，使您能夠在 F# 中編寫高效的代碼，同時確保此代碼是安全的。</span><span class="sxs-lookup"><span data-stu-id="43a57-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="43a57-106">這樣做意味著在使用這些構造時向語言添加一些概念和大量編譯器分析。</span><span class="sxs-lookup"><span data-stu-id="43a57-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="43a57-107">開始使用</span><span class="sxs-lookup"><span data-stu-id="43a57-107">Get started</span></span>

<span data-ttu-id="43a57-108">F# 4.5 在所有 .NET 核心發行版本和視覺化工作室工具中均可用。</span><span class="sxs-lookup"><span data-stu-id="43a57-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="43a57-109">[開始使用 F#](../get-started/index.md)瞭解更多資訊。</span><span class="sxs-lookup"><span data-stu-id="43a57-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="43a57-110">跨度和位元組式結構</span><span class="sxs-lookup"><span data-stu-id="43a57-110">Span and byref-like structs</span></span>

<span data-ttu-id="43a57-111">.NET Core 中引入<xref:System.Span%601>的類型允許您以強型別的方式表示記憶體中的緩衝區，現在 F# 中允許使用 F# 4.5。</span><span class="sxs-lookup"><span data-stu-id="43a57-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="43a57-112">下面的示例演示如何使用具有不同緩衝區表示表示的 對 的<xref:System.Span%601>函數操作：</span><span class="sxs-lookup"><span data-stu-id="43a57-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

<span data-ttu-id="43a57-113">這方面的一個重要方面是，Span 和其他類似[byref 的構造](../language-reference/structures.md#byreflike-structs)具有由編譯器執行的非常嚴格的靜態分析，這些分析以您可能會發現意外的方式限制它們的使用。</span><span class="sxs-lookup"><span data-stu-id="43a57-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="43a57-114">這是 F# 4.5 中引入的性能、表現力和安全性之間的基本權衡。</span><span class="sxs-lookup"><span data-stu-id="43a57-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="43a57-115">已改造的參考</span><span class="sxs-lookup"><span data-stu-id="43a57-115">Revamped byrefs</span></span>

<span data-ttu-id="43a57-116">在 F# 4.5 之前，F# 中的[Byrefs](../language-reference/byrefs.md)對許多應用程式不安全且不健全。</span><span class="sxs-lookup"><span data-stu-id="43a57-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="43a57-117">在 F# 4.5 中解決了 byrefs 周圍的聲音問題，並且還應用了對跨度和 byref 類似結構的相同靜態分析。</span><span class="sxs-lookup"><span data-stu-id="43a57-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="43a57-118">inref<'t't>和出<'t'></span><span class="sxs-lookup"><span data-stu-id="43a57-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="43a57-119">為了表示唯讀、只寫和讀/寫託管指標的概念，F# 4.5 分別引入了`inref<'T>`表示唯讀`outref<'T>`指標和只寫指標的類型。</span><span class="sxs-lookup"><span data-stu-id="43a57-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="43a57-120">每個都有不同的語義。</span><span class="sxs-lookup"><span data-stu-id="43a57-120">Each have different semantics.</span></span> <span data-ttu-id="43a57-121">例如，您不能寫入 ： `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="43a57-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="43a57-122">預設情況下，型別推斷將推斷託管指標`inref<'T>`與 F# 代碼的不可變性質一致，除非某些內容已聲明為可變指標。</span><span class="sxs-lookup"><span data-stu-id="43a57-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="43a57-123">要使某些內容具有可寫性，您需要在將類型位址傳遞給操作`mutable`它的函數或成員之前聲明類型。</span><span class="sxs-lookup"><span data-stu-id="43a57-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="43a57-124">要瞭解更多資訊，請參閱[Byrefs](../language-reference/byrefs.md)。</span><span class="sxs-lookup"><span data-stu-id="43a57-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="43a57-125">唯讀結構</span><span class="sxs-lookup"><span data-stu-id="43a57-125">Readonly structs</span></span>

<span data-ttu-id="43a57-126">從 F# 4.5 開始，您可以用<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute>這樣的來對結構進行加號：</span><span class="sxs-lookup"><span data-stu-id="43a57-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="43a57-127">這不允許您在結構中聲明可變成員，併發出中繼資料，允許 F# 和 C# 在從程式集使用時將其視為唯讀。</span><span class="sxs-lookup"><span data-stu-id="43a57-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="43a57-128">要瞭解更多資訊，請參閱[唯讀結構](../language-reference/structures.md#readonly-structs)。</span><span class="sxs-lookup"><span data-stu-id="43a57-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="43a57-129">虛空指標</span><span class="sxs-lookup"><span data-stu-id="43a57-129">Void pointers</span></span>

<span data-ttu-id="43a57-130">類型`voidptr`將添加到 F# 4.5，以下函數也包括：</span><span class="sxs-lookup"><span data-stu-id="43a57-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="43a57-131">`NativePtr.ofVoidPtr`將 void 指標轉換為本機 int 指標</span><span class="sxs-lookup"><span data-stu-id="43a57-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="43a57-132">`NativePtr.toVoidPtr`將本機 int 指標轉換為空指標</span><span class="sxs-lookup"><span data-stu-id="43a57-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="43a57-133">當與使用 void 指標的本機組件進行交互操作時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="43a57-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="43a57-134">`match!` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="43a57-134">The `match!` keyword</span></span>

<span data-ttu-id="43a57-135">關鍵字`match!`在計算運算式內增強模式匹配：</span><span class="sxs-lookup"><span data-stu-id="43a57-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

<span data-ttu-id="43a57-136">這允許您縮短通常涉及混合選項（或其他類型）的代碼與計算運算式（如非同步）。</span><span class="sxs-lookup"><span data-stu-id="43a57-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="43a57-137">要瞭解更多資訊，請參閱[匹配！](../language-reference/computation-expressions.md#match)</span><span class="sxs-lookup"><span data-stu-id="43a57-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="43a57-138">在陣列、清單和序列運算式中放寬了向上轉換要求</span><span class="sxs-lookup"><span data-stu-id="43a57-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="43a57-139">混合類型，其中一個類型可以從陣列、清單和序列運算式的另一個內部繼承，傳統上需要您將任何派生類型用`:>`或`upcast`將其父類型向上轉換。</span><span class="sxs-lookup"><span data-stu-id="43a57-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="43a57-140">這是現在放鬆，如下所示：</span><span class="sxs-lookup"><span data-stu-id="43a57-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="43a57-141">陣列和清單運算式的縮進放鬆</span><span class="sxs-lookup"><span data-stu-id="43a57-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="43a57-142">在 F# 4.5 之前，當作為參數傳遞給方法調用時，需要過度縮進陣列和清單運算式。</span><span class="sxs-lookup"><span data-stu-id="43a57-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="43a57-143">不再需要這一點：</span><span class="sxs-lookup"><span data-stu-id="43a57-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
