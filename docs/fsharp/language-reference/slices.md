---
title: 配量
description: '瞭解如何使用現有 F # 資料類型的配量，以及如何為其他資料類型定義您自己的配量。'
ms.date: 11/20/2020
ms.openlocfilehash: b776058df5a174dfe48dbf513bf17281036dd83e
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740376"
---
# <a name="slices"></a><span data-ttu-id="6290e-103">配量</span><span class="sxs-lookup"><span data-stu-id="6290e-103">Slices</span></span>

<span data-ttu-id="6290e-104">本文說明如何從現有的 F # 類型取得配量，以及如何定義您自己的配量。</span><span class="sxs-lookup"><span data-stu-id="6290e-104">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="6290e-105">在 F # 中，配量是任何資料類型的子集。</span><span class="sxs-lookup"><span data-stu-id="6290e-105">In F#, a slice is a subset of any data type.</span></span>  <span data-ttu-id="6290e-106">配量類似于 [索引子](./members/indexed-properties.md)，但會產生多個值，而不是從基礎資料結構產生單一值。</span><span class="sxs-lookup"><span data-stu-id="6290e-106">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span> <span data-ttu-id="6290e-107">配量使用 `..` 運算子語法來選取資料類型中指定之索引的範圍。</span><span class="sxs-lookup"><span data-stu-id="6290e-107">Slices use the `..` operator syntax to select the range of specified indices in a data type.</span></span> <span data-ttu-id="6290e-108">如需詳細資訊，請參閱 [迴圈運算式參考文章](./loops-for-in-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="6290e-108">For more information, see the [looping expression reference article](./loops-for-in-expression.md).</span></span>

<span data-ttu-id="6290e-109">F # 目前有配量字串、清單、陣列和多維度 (2D、3D、4D) 陣列的內建支援。</span><span class="sxs-lookup"><span data-stu-id="6290e-109">F# currently has intrinsic support for slicing strings, lists, arrays, and multidimensional (2D, 3D, 4D) arrays.</span></span> <span data-ttu-id="6290e-110">切割最常用於 F # 陣列和清單。</span><span class="sxs-lookup"><span data-stu-id="6290e-110">Slicing is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="6290e-111">您可以使用類型定義中的方法，或在範圍內的 `GetSlice` [類型延伸](type-extensions.md)中，將配量新增至自訂資料類型。</span><span class="sxs-lookup"><span data-stu-id="6290e-111">You can add slicing to your custom data types by using the `GetSlice` method in your type definition or in an in-scope [type extension](type-extensions.md).</span></span>

## <a name="slicing-f-lists-and-arrays"></a><span data-ttu-id="6290e-112">切割 F # 清單和陣列</span><span class="sxs-lookup"><span data-stu-id="6290e-112">Slicing F# lists and arrays</span></span>

<span data-ttu-id="6290e-113">最常見的資料類型為 F # 清單和陣列。</span><span class="sxs-lookup"><span data-stu-id="6290e-113">The most common data types that are sliced are F# lists and arrays.</span></span>  <span data-ttu-id="6290e-114">下列範例示範如何配量清單：</span><span class="sxs-lookup"><span data-stu-id="6290e-114">The following example demonstrates how to slice lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn $"Small slice: {smallSlice}"

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn $"Unbounded beginning slice: {unboundedBeginning}"

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn $"Unbounded end slice: {unboundedEnd}"
```

<span data-ttu-id="6290e-115">配量陣列就像切割清單一樣：</span><span class="sxs-lookup"><span data-stu-id="6290e-115">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn $"Small slice: {smallSlice}"

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn $"Unbounded beginning slice: {unboundedBeginning}"

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn $"Unbounded end slice: {unboundedEnd}"
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="6290e-116">配量多維陣列</span><span class="sxs-lookup"><span data-stu-id="6290e-116">Slicing multidimensional arrays</span></span>

<span data-ttu-id="6290e-117">F # 支援 F # 核心程式庫中的多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="6290e-117">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="6290e-118">如同一維陣列，多維陣列的配量也很有用。</span><span class="sxs-lookup"><span data-stu-id="6290e-118">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="6290e-119">不過，引入額外的維度會規定稍微不同的語法，讓您可以取得特定資料列和資料行的片段。</span><span class="sxs-lookup"><span data-stu-id="6290e-119">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="6290e-120">下列範例示範如何配量2D 陣列：</span><span class="sxs-lookup"><span data-stu-id="6290e-120">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn $"Full matrix:\n {A}"

// Take the first row
let row0 = A.[0,*]
printfn $"{row0}"

// Take the first column
let col0 = A.[*,0]
printfn $"{col0}"

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn $"{subA}"

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn $"{subA}"

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn $"{twoByTwo}"
```

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="6290e-121">定義其他資料結構的配量</span><span class="sxs-lookup"><span data-stu-id="6290e-121">Defining slices for other data structures</span></span>

<span data-ttu-id="6290e-122">F # 核心程式庫會定義一組有限類型的配量。</span><span class="sxs-lookup"><span data-stu-id="6290e-122">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="6290e-123">如果您想要定義更多資料類型的配量，可以在類型定義本身或類型延伸中進行。</span><span class="sxs-lookup"><span data-stu-id="6290e-123">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="6290e-124">例如，以下是您可能為類別定義配量 <xref:System.ArraySegment%601> 以允許方便資料操作的方式：</span><span class="sxs-lookup"><span data-stu-id="6290e-124">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

<span data-ttu-id="6290e-125">使用和類型的另一個範例 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> ：</span><span class="sxs-lookup"><span data-stu-id="6290e-125">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

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
    printfn $"{arr}"

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="6290e-126">內建 F # 配量為結尾（含）</span><span class="sxs-lookup"><span data-stu-id="6290e-126">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="6290e-127">F # 中的所有內建配量都是結尾（含）;亦即，上限會包含在配量中。</span><span class="sxs-lookup"><span data-stu-id="6290e-127">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="6290e-128">若為具有起始索引和結束索引的指定配量 `x` `y` ，則產生的配量會包含 *yth* 值。</span><span class="sxs-lookup"><span data-stu-id="6290e-128">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn $"{xs.[2..5]}" // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="6290e-129">內建 F # 空白配量</span><span class="sxs-lookup"><span data-stu-id="6290e-129">Built-in F# empty slices</span></span>

<span data-ttu-id="6290e-130">如果語法可能會產生不存在的配量，則 F # 清單、陣列、序列、字串、多維度 (2D、3D、4D) 陣列都將會產生空的磁區。</span><span class="sxs-lookup"><span data-stu-id="6290e-130">F# lists, arrays, sequences, strings, multidimensional (2D, 3D, 4D) arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="6290e-131">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="6290e-131">Consider the following example:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

> [!IMPORTANT]
> <span data-ttu-id="6290e-132">C # 開發人員可能會預期這些會擲回例外狀況，而不是產生空白的配量。</span><span class="sxs-lookup"><span data-stu-id="6290e-132">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="6290e-133">這是以 F # 撰寫空白集合的事實設計決策。</span><span class="sxs-lookup"><span data-stu-id="6290e-133">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="6290e-134">空白的 F # 清單可以使用另一個 F # 清單來撰寫，空字串可以加入至現有的字串等等。</span><span class="sxs-lookup"><span data-stu-id="6290e-134">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="6290e-135">使用以參數形式傳遞的值來取得配量是很常見的，並藉由產生空的集合來滿足 F # 程式碼的複合本質，進而容忍超出範圍 > 的能力。</span><span class="sxs-lookup"><span data-stu-id="6290e-135">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds > by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="6290e-136">固定-3D 和4D 陣列的索引配量</span><span class="sxs-lookup"><span data-stu-id="6290e-136">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="6290e-137">針對 F # 3D 和4D 陣列，您可以「修正」特定的索引，並將已修正該索引的其他維度進行配量。</span><span class="sxs-lookup"><span data-stu-id="6290e-137">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="6290e-138">為了說明這一點，請考慮下列3D 陣列：</span><span class="sxs-lookup"><span data-stu-id="6290e-138">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="6290e-139">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="6290e-139">*z = 0*</span></span>

| <span data-ttu-id="6290e-140">x\y</span><span class="sxs-lookup"><span data-stu-id="6290e-140">x\y</span></span>   | <span data-ttu-id="6290e-141">0</span><span class="sxs-lookup"><span data-stu-id="6290e-141">0</span></span> | <span data-ttu-id="6290e-142">1</span><span class="sxs-lookup"><span data-stu-id="6290e-142">1</span></span> |
|-------|---|---|
| <span data-ttu-id="6290e-143">**0**</span><span class="sxs-lookup"><span data-stu-id="6290e-143">**0**</span></span> | <span data-ttu-id="6290e-144">0</span><span class="sxs-lookup"><span data-stu-id="6290e-144">0</span></span> | <span data-ttu-id="6290e-145">1</span><span class="sxs-lookup"><span data-stu-id="6290e-145">1</span></span> |
| <span data-ttu-id="6290e-146">**1**</span><span class="sxs-lookup"><span data-stu-id="6290e-146">**1**</span></span> | <span data-ttu-id="6290e-147">2</span><span class="sxs-lookup"><span data-stu-id="6290e-147">2</span></span> | <span data-ttu-id="6290e-148">3</span><span class="sxs-lookup"><span data-stu-id="6290e-148">3</span></span> |

<span data-ttu-id="6290e-149">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="6290e-149">*z = 1*</span></span>

| <span data-ttu-id="6290e-150">x\y</span><span class="sxs-lookup"><span data-stu-id="6290e-150">x\y</span></span>   | <span data-ttu-id="6290e-151">0</span><span class="sxs-lookup"><span data-stu-id="6290e-151">0</span></span> | <span data-ttu-id="6290e-152">1</span><span class="sxs-lookup"><span data-stu-id="6290e-152">1</span></span> |
|-------|---|---|
| <span data-ttu-id="6290e-153">**0**</span><span class="sxs-lookup"><span data-stu-id="6290e-153">**0**</span></span> | <span data-ttu-id="6290e-154">4</span><span class="sxs-lookup"><span data-stu-id="6290e-154">4</span></span> | <span data-ttu-id="6290e-155">5</span><span class="sxs-lookup"><span data-stu-id="6290e-155">5</span></span> |
| <span data-ttu-id="6290e-156">**1**</span><span class="sxs-lookup"><span data-stu-id="6290e-156">**1**</span></span> | <span data-ttu-id="6290e-157">6</span><span class="sxs-lookup"><span data-stu-id="6290e-157">6</span></span> | <span data-ttu-id="6290e-158">7</span><span class="sxs-lookup"><span data-stu-id="6290e-158">7</span></span> |

<span data-ttu-id="6290e-159">如果您想要從陣列中將配量解壓縮 `[| 4; 5 |]` ，請使用固定索引配量。</span><span class="sxs-lookup"><span data-stu-id="6290e-159">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

```fsharp
let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

<span data-ttu-id="6290e-160">最後一行 `y` `z` 會修正3d 陣列的和索引，並採用 `x` 對應至矩陣的其餘值。</span><span class="sxs-lookup"><span data-stu-id="6290e-160">The last line fixes the `y` and `z` indices of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="6290e-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6290e-161">See also</span></span>

- [<span data-ttu-id="6290e-162">索引屬性</span><span class="sxs-lookup"><span data-stu-id="6290e-162">Indexed properties</span></span>](./members/indexed-properties.md)
