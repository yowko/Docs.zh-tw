---
title: 配量F#()
description: 瞭解如何將配量用於現有F#的資料類型, 以及如何為其他資料類型定義您自己的配量。
ms.date: 01/22/2019
ms.openlocfilehash: 3067982c2b4249312c7e9365bbfb994be840911d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627142"
---
# <a name="slices"></a>配量

在F#中, 配量是資料類型的子集。 若要能夠從資料類型接受配量, 資料類型必須定義`GetSlice`方法, 或在範圍內的[類型延伸](type-extensions.md)中。 本文說明如何從現有F#的型別, 以及如何定義您自己的配量。

配量類似于[索引子](./members/indexed-properties.md), 但不會從基礎資料結構產生單一值, 而是會產生多個分割區。

F#目前具有配量字串、清單、陣列和2D 陣列的內建支援。

## <a name="basic-slicing-with-f-lists-and-arrays"></a>使用清單和F#陣列的基本配量

最常見的已切割資料類型是F#清單和陣列。 下列範例示範如何使用清單來執行這項操作:

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

切割陣列就像切割清單一樣:

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

## <a name="slicing-multidimensional-arrays"></a>切割多維陣列

F#支援核心程式庫中F#的多維度陣列。 就像一維陣列一樣, 多維陣列的配量也會很有用。 不過, 引入額外的維度會要求稍微不同的語法, 讓您可以接受特定資料列和資料行的配量。

下列範例示範如何配量2D 陣列:

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

F#核心程式庫不會針對`GetSlice`3d 陣列定義。 如果您想要配量其他維度或其他陣列, 您必須自行定義`GetSlice`成員。

## <a name="defining-slices-for-other-data-structures"></a>定義其他資料結構的配量

F#核心程式庫會定義一組有限類型的配量。 如果您想要定義更多資料類型的配量, 可以在類型定義本身或類型延伸中執行此動作。

例如, 以下說明如何定義<xref:System.ArraySegment%601>類別的配量, 以允許方便的資料操作:

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>如果需要, 請使用內嵌來避免進行裝箱

如果您要定義實際上是結構之類型的配量, 我們建議您`inline`使用該`GetSlice`成員。 F#編譯器會將選擇性引數優化, 避免因切割而產生任何堆積配置。 這對於無法在堆積上配置的切割<xref:System.Span%601>結構 (例如) 而言極為重要。

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

## <a name="see-also"></a>另請參閱

- [已編制索引的屬性](./members/indexed-properties.md)
