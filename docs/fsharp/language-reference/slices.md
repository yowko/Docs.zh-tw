---
title: 配量
description: '瞭解如何使用現有 F # 資料類型的配量，以及如何為其他資料類型定義您自己的配量。'
ms.date: 12/23/2019
ms.openlocfilehash: d3ddb2c247c36a85842f565f051372c5f2c9a9e9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559007"
---
# <a name="slices"></a><span data-ttu-id="5bde4-103">配量</span><span class="sxs-lookup"><span data-stu-id="5bde4-103">Slices</span></span>

<span data-ttu-id="5bde4-104">在 F # 中，配量是任何資料類型的子集， `GetSlice` 在其定義中或在範圍內的 [類型延伸](type-extensions.md)中都有方法。</span><span class="sxs-lookup"><span data-stu-id="5bde4-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="5bde4-105">它最常用於 F # 陣列和清單。</span><span class="sxs-lookup"><span data-stu-id="5bde4-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="5bde4-106">本文說明如何從現有的 F # 類型取得配量，以及如何定義您自己的配量。</span><span class="sxs-lookup"><span data-stu-id="5bde4-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="5bde4-107">配量類似于 [索引子](./members/indexed-properties.md)，但會產生多個值，而不是從基礎資料結構產生單一值。</span><span class="sxs-lookup"><span data-stu-id="5bde4-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="5bde4-108">F # 目前有配量字串、清單、陣列和2D 陣列的內部支援。</span><span class="sxs-lookup"><span data-stu-id="5bde4-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="5bde4-109">使用 F # 清單和陣列的基本配量</span><span class="sxs-lookup"><span data-stu-id="5bde4-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="5bde4-110">最常見的資料類型為 F # 清單和陣列。</span><span class="sxs-lookup"><span data-stu-id="5bde4-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="5bde4-111">下列範例示範如何使用清單來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="5bde4-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="5bde4-112">配量陣列就像切割清單一樣：</span><span class="sxs-lookup"><span data-stu-id="5bde4-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="5bde4-113">配量多維陣列</span><span class="sxs-lookup"><span data-stu-id="5bde4-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="5bde4-114">F # 支援 F # 核心程式庫中的多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="5bde4-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="5bde4-115">如同一維陣列，多維陣列的配量也很有用。</span><span class="sxs-lookup"><span data-stu-id="5bde4-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="5bde4-116">不過，引入額外的維度會規定稍微不同的語法，讓您可以取得特定資料列和資料行的片段。</span><span class="sxs-lookup"><span data-stu-id="5bde4-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="5bde4-117">下列範例示範如何配量2D 陣列：</span><span class="sxs-lookup"><span data-stu-id="5bde4-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="5bde4-118">F # 核心程式庫目前不會 `GetSlice` 針對3d 陣列定義。</span><span class="sxs-lookup"><span data-stu-id="5bde4-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="5bde4-119">如果您想要配量3D 陣列或其他維度陣列，請自行定義 `GetSlice` 成員。</span><span class="sxs-lookup"><span data-stu-id="5bde4-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="5bde4-120">定義其他資料結構的配量</span><span class="sxs-lookup"><span data-stu-id="5bde4-120">Defining slices for other data structures</span></span>

<span data-ttu-id="5bde4-121">F # 核心程式庫會定義一組有限類型的配量。</span><span class="sxs-lookup"><span data-stu-id="5bde4-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="5bde4-122">如果您想要定義更多資料類型的配量，可以在類型定義本身或類型延伸中進行。</span><span class="sxs-lookup"><span data-stu-id="5bde4-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="5bde4-123">例如，以下是您可能為類別定義配量 <xref:System.ArraySegment%601> 以允許方便資料操作的方式：</span><span class="sxs-lookup"><span data-stu-id="5bde4-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

<span data-ttu-id="5bde4-124">使用和類型的另一個範例 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> ：</span><span class="sxs-lookup"><span data-stu-id="5bde4-124">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
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
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="5bde4-125">內建 F # 配量為結尾（含）</span><span class="sxs-lookup"><span data-stu-id="5bde4-125">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="5bde4-126">F # 中的所有內建配量都是結尾（含）;亦即，上限會包含在配量中。</span><span class="sxs-lookup"><span data-stu-id="5bde4-126">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="5bde4-127">若為具有起始索引和結束索引的指定配量 `x` `y` ，則產生的配量會包含 *yth* 值。</span><span class="sxs-lookup"><span data-stu-id="5bde4-127">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a><span data-ttu-id="5bde4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bde4-128">See also</span></span>

- [<span data-ttu-id="5bde4-129">索引屬性</span><span class="sxs-lookup"><span data-stu-id="5bde4-129">Indexed properties</span></span>](./members/indexed-properties.md)
