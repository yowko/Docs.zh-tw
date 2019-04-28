---
title: 配量 (F#)
description: 深入了解如何使用現有的配量F#資料類型以及如何定義您自己的配量的其他資料型別。
ms.date: 01/22/2019
ms.openlocfilehash: 1d8bb029ad18c8853ab58888959967ed279fb368
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925982"
---
# <a name="slices"></a><span data-ttu-id="e7c49-103">配量</span><span class="sxs-lookup"><span data-stu-id="e7c49-103">Slices</span></span>

<span data-ttu-id="e7c49-104">在F#，配量為資料類型的子集。</span><span class="sxs-lookup"><span data-stu-id="e7c49-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="e7c49-105">若要能夠從資料類型進行配量，資料類型必須是定義`GetSlice`方法或在[輸入副檔名](type-extensions.md)也就是在範圍內。</span><span class="sxs-lookup"><span data-stu-id="e7c49-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="e7c49-106">這篇文章說明如何從現有的配量F#類型，以及如何定義您自己。</span><span class="sxs-lookup"><span data-stu-id="e7c49-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="e7c49-107">配量都類似於[索引子](members/indexed-properties.md)，但是而不是產生單一值從基礎資料結構，會產生多個項目。</span><span class="sxs-lookup"><span data-stu-id="e7c49-107">Slices are similar to [indexers](members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="e7c49-108">F#目前沒有內建支援字串、 清單、 陣列和 2D 陣列配量。</span><span class="sxs-lookup"><span data-stu-id="e7c49-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="e7c49-109">使用基本配量F#清單和陣列</span><span class="sxs-lookup"><span data-stu-id="e7c49-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="e7c49-110">最常見配量的資料類型為F#清單和陣列。</span><span class="sxs-lookup"><span data-stu-id="e7c49-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="e7c49-111">下列範例示範如何執行此動作的清單：</span><span class="sxs-lookup"><span data-stu-id="e7c49-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="e7c49-112">配量陣列，就如同配量清單：</span><span class="sxs-lookup"><span data-stu-id="e7c49-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="e7c49-113">配量的多維陣列</span><span class="sxs-lookup"><span data-stu-id="e7c49-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="e7c49-114">F#支援中的多維陣列F#核心程式庫。</span><span class="sxs-lookup"><span data-stu-id="e7c49-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="e7c49-115">如同一維陣列、 多維陣列的配量也相當有用。</span><span class="sxs-lookup"><span data-stu-id="e7c49-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="e7c49-116">不過，其他維度的簡介會強制稍有不同的語法，讓您可以採取特定的資料列和資料行的配量。</span><span class="sxs-lookup"><span data-stu-id="e7c49-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="e7c49-117">下列範例示範如何配量的 2D 陣列：</span><span class="sxs-lookup"><span data-stu-id="e7c49-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="e7c49-118">F#核心程式庫不會定義`GetSlice`的 3D 的陣列。</span><span class="sxs-lookup"><span data-stu-id="e7c49-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="e7c49-119">如果您想要配量或其他陣列或多個維度，您必須定義`GetSlice`成員自己。</span><span class="sxs-lookup"><span data-stu-id="e7c49-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="e7c49-120">定義其他資料結構的配量</span><span class="sxs-lookup"><span data-stu-id="e7c49-120">Defining slices for other data structures</span></span>

<span data-ttu-id="e7c49-121">F#核心程式庫定義配量的一組有限的類型。</span><span class="sxs-lookup"><span data-stu-id="e7c49-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="e7c49-122">如果您想要定義配量更多的資料類型，則可以本身型別定義中或在類型擴充功能。</span><span class="sxs-lookup"><span data-stu-id="e7c49-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="e7c49-123">例如，以下是如何定義配量<xref:System.ArraySegment%601>以供方便存取的資料操作的類別：</span><span class="sxs-lookup"><span data-stu-id="e7c49-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(?start, ?finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="e7c49-124">使用內嵌，以避免 boxing，如有必要</span><span class="sxs-lookup"><span data-stu-id="e7c49-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="e7c49-125">如果您正在定義的類型，實際上是結構的配量，我們建議您`inline``GetSlice`成員。</span><span class="sxs-lookup"><span data-stu-id="e7c49-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="e7c49-126">F#編譯器會最佳化選擇性引數，避免任何堆積配置，因為配量。</span><span class="sxs-lookup"><span data-stu-id="e7c49-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="e7c49-127">這點非常重要的配量建構這類<xref:System.Span%601>，無法配置在堆積上。</span><span class="sxs-lookup"><span data-stu-id="e7c49-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a><span data-ttu-id="e7c49-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7c49-128">See also</span></span>

- [<span data-ttu-id="e7c49-129">索引的屬性</span><span class="sxs-lookup"><span data-stu-id="e7c49-129">Indexed properties</span></span>](members/indexed-properties.md)
