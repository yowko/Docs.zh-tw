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
# <a name="slices"></a>配量

在 F # 中，配量是任何資料類型的子集， `GetSlice` 在其定義中或在範圍內的 [類型延伸](type-extensions.md)中都有方法。 它最常用於 F # 陣列和清單。 本文說明如何從現有的 F # 類型取得配量，以及如何定義您自己的配量。

配量類似于 [索引子](./members/indexed-properties.md)，但會產生多個值，而不是從基礎資料結構產生單一值。

F # 目前有配量字串、清單、陣列和2D 陣列的內部支援。

## <a name="basic-slicing-with-f-lists-and-arrays"></a>使用 F # 清單和陣列的基本配量

最常見的資料類型為 F # 清單和陣列。 下列範例示範如何使用清單來執行這項操作：

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

配量陣列就像切割清單一樣：

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

## <a name="slicing-multidimensional-arrays"></a>配量多維陣列

F # 支援 F # 核心程式庫中的多維度陣列。 如同一維陣列，多維陣列的配量也很有用。 不過，引入額外的維度會規定稍微不同的語法，讓您可以取得特定資料列和資料行的片段。

下列範例示範如何配量2D 陣列：

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

F # 核心程式庫目前不會 `GetSlice` 針對3d 陣列定義。 如果您想要配量3D 陣列或其他維度陣列，請自行定義 `GetSlice` 成員。

## <a name="defining-slices-for-other-data-structures"></a>定義其他資料結構的配量

F # 核心程式庫會定義一組有限類型的配量。 如果您想要定義更多資料類型的配量，可以在類型定義本身或類型延伸中進行。

例如，以下是您可能為類別定義配量 <xref:System.ArraySegment%601> 以允許方便資料操作的方式：

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

使用和類型的另一個範例 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> ：

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

## <a name="built-in-f-slices-are-end-inclusive"></a>內建 F # 配量為結尾（含）

F # 中的所有內建配量都是結尾（含）;亦即，上限會包含在配量中。 若為具有起始索引和結束索引的指定配量 `x` `y` ，則產生的配量會包含 *yth* 值。

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a>另請參閱

- [索引屬性](./members/indexed-properties.md)
