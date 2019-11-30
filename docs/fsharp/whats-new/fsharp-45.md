---
title: F# 4.5 的新功能- F#指南
description: 取得4.5 中F#可用的新功能總覽。
ms.date: 11/27/2019
ms.openlocfilehash: 780b33a564432aae5ec99c70ff8620988b553fd1
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644107"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="31486-103">4\.5 中F#的新功能</span><span class="sxs-lookup"><span data-stu-id="31486-103">What's new in F# 4.5</span></span>

<span data-ttu-id="31486-104">F#4.5 新增多項語言的F#增強功能。</span><span class="sxs-lookup"><span data-stu-id="31486-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="31486-105">其中許多功能都已新增在一起，可讓您在中F#撰寫有效率的程式碼，同時確保此程式碼是安全的。</span><span class="sxs-lookup"><span data-stu-id="31486-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="31486-106">這麼做表示在使用這些結構時，將幾個概念新增至語言，以及大量編譯器分析。</span><span class="sxs-lookup"><span data-stu-id="31486-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="31486-107">開始使用</span><span class="sxs-lookup"><span data-stu-id="31486-107">Get started</span></span>

<span data-ttu-id="31486-108">F#4.5 適用于所有 .NET Core 發行版本和 Visual Studio 工具。</span><span class="sxs-lookup"><span data-stu-id="31486-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="31486-109">[開始使用F# ](../get-started/index.md)以深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="31486-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="31486-110">Span 和類似 byref 的結構</span><span class="sxs-lookup"><span data-stu-id="31486-110">Span and byref-like structs</span></span>

<span data-ttu-id="31486-111">.NET Core 中引進的 <xref:System.Span%601> 類型，可讓您以強型別方式來表示記憶體中的緩衝區，這在F#從F# 4.5 開始是允許的。</span><span class="sxs-lookup"><span data-stu-id="31486-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="31486-112">下列範例會示範如何在具有不同緩衝區標記法的 <xref:System.Span%601> 上重複使用函式：</span><span class="sxs-lookup"><span data-stu-id="31486-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="31486-113">其中一個重要的層面是，Span 和其他[byref 類似的結構](../language-reference/structures.md#byreflike-structs)都有非常嚴格的靜態分析，由編譯器執行，以限制其使用方式，因為您可能會發現非預期的情況。</span><span class="sxs-lookup"><span data-stu-id="31486-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="31486-114">這是4.5 中F#引進的效能、表達和安全性之間的基本取捨。</span><span class="sxs-lookup"><span data-stu-id="31486-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="31486-115">改頭換面 byref</span><span class="sxs-lookup"><span data-stu-id="31486-115">Revamped byrefs</span></span>

<span data-ttu-id="31486-116">在F# 4.5 之前， [byref](../language-reference/byrefs.md)在F#許多應用程式中都是 unsafe 和無效:。</span><span class="sxs-lookup"><span data-stu-id="31486-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="31486-117">4\.5 中F#已解決 byref 的 Soundness 問題，而且也套用了對 span 和類似 byref 的結構所進行的相同靜態分析。</span><span class="sxs-lookup"><span data-stu-id="31486-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="31486-118">inref < 不 > 和 outref < 不 ></span><span class="sxs-lookup"><span data-stu-id="31486-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="31486-119">為了表示唯讀、唯讀和讀取/寫入受控指標的概念， F# 4.5 引進了 `inref<'T>`，`outref<'T>` 類型，分別代表唯讀和僅限寫入的指標。</span><span class="sxs-lookup"><span data-stu-id="31486-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="31486-120">每個都有不同的語義。</span><span class="sxs-lookup"><span data-stu-id="31486-120">Each have different semantics.</span></span> <span data-ttu-id="31486-121">例如，您無法寫入 `inref<'T>`：</span><span class="sxs-lookup"><span data-stu-id="31486-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="31486-122">根據預設，除非已經宣告為可變動的F# ，否則型別推斷會將 managed 指標推斷為與程式碼不可變性質的 `inref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="31486-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="31486-123">若要使其成為可寫入的專案，您必須先將類型宣告為 `mutable`，再將其位址傳遞給操作它的函式或成員。</span><span class="sxs-lookup"><span data-stu-id="31486-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="31486-124">若要深入瞭解，請參閱[byref](../language-reference/byrefs.md)。</span><span class="sxs-lookup"><span data-stu-id="31486-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="31486-125">Readonly 結構</span><span class="sxs-lookup"><span data-stu-id="31486-125">Readonly structs</span></span>

<span data-ttu-id="31486-126">從F# 4.5 開始，您可以使用 <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> 來標注結構，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31486-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="31486-127">這不允許您在結構中宣告可變動的成員，並且會發出F#允許C#和的中繼資料，以便在從元件取用時將其視為唯讀。</span><span class="sxs-lookup"><span data-stu-id="31486-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="31486-128">若要深入瞭解，請參閱[ReadOnly 結構](../language-reference/structures.md#readonly-structs)</span><span class="sxs-lookup"><span data-stu-id="31486-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs)</span></span>

## <a name="void-pointers"></a><span data-ttu-id="31486-129">Void 指標</span><span class="sxs-lookup"><span data-stu-id="31486-129">Void pointers</span></span>

<span data-ttu-id="31486-130">`voidptr` 類型會新增至F# 4.5，如同下列函數：</span><span class="sxs-lookup"><span data-stu-id="31486-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="31486-131">`NativePtr.ofVoidPtr` 將 void 指標轉換成原生 int 指標</span><span class="sxs-lookup"><span data-stu-id="31486-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="31486-132">`NativePtr.toVoidPtr` 將原生 int 指標轉換成 void 指標</span><span class="sxs-lookup"><span data-stu-id="31486-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="31486-133">當與使用 void 指標的原生元件互通時，這會很有説明。</span><span class="sxs-lookup"><span data-stu-id="31486-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="31486-134">`match!` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="31486-134">The `match!` keyword</span></span>

<span data-ttu-id="31486-135">`match!` 關鍵字會在計算運算式內時增強模式比對：</span><span class="sxs-lookup"><span data-stu-id="31486-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="31486-136">這可讓您縮短程式碼，這通常牽涉到混合選項（或其他類型）與計算運算式（例如 async）。</span><span class="sxs-lookup"><span data-stu-id="31486-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="31486-137">若要深入瞭解，請參閱[match！](../language-reference/computation-expressions.md#match)。</span><span class="sxs-lookup"><span data-stu-id="31486-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="31486-138">陣列、清單和順序運算式中的寬鬆 upcasting 需求</span><span class="sxs-lookup"><span data-stu-id="31486-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="31486-139">混合型別，其中一個可能繼承自陣列、清單和序列運算式內的另一個類型，傳統上會要求您使用 `:>` 或 `upcast`，將任何衍生的型別向上轉換成其父系型別。</span><span class="sxs-lookup"><span data-stu-id="31486-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="31486-140">這現在是寬鬆的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31486-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="31486-141">陣列和清單運算式的縮排放寬</span><span class="sxs-lookup"><span data-stu-id="31486-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="31486-142">在F# 4.5 之前，您需要在將陣列和清單運算式當做引數傳遞給方法呼叫時，過度將其縮排。</span><span class="sxs-lookup"><span data-stu-id="31486-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="31486-143">已不再需要此動作：</span><span class="sxs-lookup"><span data-stu-id="31486-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting = 
    System.Console.WriteLine(format="{0}", arg = [| 
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
