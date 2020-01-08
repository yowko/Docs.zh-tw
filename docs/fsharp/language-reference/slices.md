---
title: 配量
description: 瞭解如何將配量用於現有F#的資料類型，以及如何為其他資料類型定義您自己的配量。
ms.date: 12/23/2019
ms.openlocfilehash: 3911139c7ce656043817eb23d30f3686555b6efe
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545109"
---
# <a name="slices"></a><span data-ttu-id="9768f-103">配量</span><span class="sxs-lookup"><span data-stu-id="9768f-103">Slices</span></span>

<span data-ttu-id="9768f-104">在F#中，配量是任何資料類型的子集，在其定義或範圍內的[類型延伸](type-extensions.md)中具有 `GetSlice` 方法。</span><span class="sxs-lookup"><span data-stu-id="9768f-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="9768f-105">它最常用於F#陣列和清單。</span><span class="sxs-lookup"><span data-stu-id="9768f-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="9768f-106">本文說明如何從現有F#的型別拍照，以及如何定義您自己的配量。</span><span class="sxs-lookup"><span data-stu-id="9768f-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="9768f-107">配量類似于[索引子](./members/indexed-properties.md)，但不會從基礎資料結構產生單一值，而是會產生多個分割區。</span><span class="sxs-lookup"><span data-stu-id="9768f-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="9768f-108">F#目前具有配量字串、清單、陣列和2D 陣列的內建支援。</span><span class="sxs-lookup"><span data-stu-id="9768f-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="9768f-109">使用清單和F#陣列的基本配量</span><span class="sxs-lookup"><span data-stu-id="9768f-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="9768f-110">最常見的已切割資料類型是F#清單和陣列。</span><span class="sxs-lookup"><span data-stu-id="9768f-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="9768f-111">下列範例示範如何使用清單來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="9768f-111">The following example demonstrates how to do this with lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="9768f-112">切割陣列就像切割清單一樣：</span><span class="sxs-lookup"><span data-stu-id="9768f-112">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="9768f-113">切割多維陣列</span><span class="sxs-lookup"><span data-stu-id="9768f-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="9768f-114">F#支援核心程式庫中F#的多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="9768f-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="9768f-115">就像一維陣列一樣，多維陣列的配量也會很有用。</span><span class="sxs-lookup"><span data-stu-id="9768f-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="9768f-116">不過，引入額外的維度會要求稍微不同的語法，讓您可以接受特定資料列和資料行的配量。</span><span class="sxs-lookup"><span data-stu-id="9768f-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="9768f-117">下列範例示範如何配量2D 陣列：</span><span class="sxs-lookup"><span data-stu-id="9768f-117">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

<span data-ttu-id="9768f-118">F#核心程式庫目前不會定義3d 陣列的 `GetSlice`。</span><span class="sxs-lookup"><span data-stu-id="9768f-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="9768f-119">如果您想要配量3D 陣列或其他更多維度的陣列，請自行定義 `GetSlice` 成員。</span><span class="sxs-lookup"><span data-stu-id="9768f-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="9768f-120">定義其他資料結構的配量</span><span class="sxs-lookup"><span data-stu-id="9768f-120">Defining slices for other data structures</span></span>

<span data-ttu-id="9768f-121">F#核心程式庫會定義一組有限類型的配量。</span><span class="sxs-lookup"><span data-stu-id="9768f-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="9768f-122">如果您想要定義更多資料類型的配量，可以在類型定義本身或類型延伸中執行此動作。</span><span class="sxs-lookup"><span data-stu-id="9768f-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="9768f-123">例如，以下是您可以為 <xref:System.ArraySegment%601> 類別定義配量的方式，以允許方便的資料操作：</span><span class="sxs-lookup"><span data-stu-id="9768f-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="9768f-124">如果需要，請使用內嵌來避免進行裝箱</span><span class="sxs-lookup"><span data-stu-id="9768f-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="9768f-125">如果您要定義實際上是結構之類型的配量，我們建議您 `inline` `GetSlice` 成員。</span><span class="sxs-lookup"><span data-stu-id="9768f-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="9768f-126">F#編譯器會將選擇性引數優化，避免因切割而產生任何堆積配置。</span><span class="sxs-lookup"><span data-stu-id="9768f-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="9768f-127">這對切割結構（例如無法在堆積上配置的 <xref:System.Span%601>）而言極為重要。</span><span class="sxs-lookup"><span data-stu-id="9768f-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    // Note the 'inline' in the member definition
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="9768f-128">內F#建配量是結尾包含的</span><span class="sxs-lookup"><span data-stu-id="9768f-128">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="9768f-129">中的所有內F#建配量都是結尾包含的;也就是說，上限會包含在配量中。</span><span class="sxs-lookup"><span data-stu-id="9768f-129">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="9768f-130">對於啟動索引 `x` 和結束索引 `y`的給定配量，產生的配量會包含*yth*值。</span><span class="sxs-lookup"><span data-stu-id="9768f-130">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a><span data-ttu-id="9768f-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="9768f-131">See also</span></span>

- [<span data-ttu-id="9768f-132">已編制索引的屬性</span><span class="sxs-lookup"><span data-stu-id="9768f-132">Indexed properties</span></span>](./members/indexed-properties.md)
