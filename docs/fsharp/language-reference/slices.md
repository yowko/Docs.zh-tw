---
title: 配量 (F#)
description: 深入了解如何使用現有的配量F#資料類型以及如何定義您自己的配量的其他資料型別。
ms.date: 01/22/2019
ms.openlocfilehash: c204c6cbb195b33998b92dd940313a132ecc321d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746703"
---
# <a name="slices"></a>配量

在F#，配量為資料類型的子集。 若要能夠從資料類型進行配量，資料類型必須是定義`GetSlice`方法或在[輸入副檔名](type-extensions.md)也就是在範圍內。 這篇文章說明如何從現有的配量F#類型，以及如何定義您自己。

配量都類似於[索引子](members/indexed-properties.md)，但是而不是產生單一值從基礎資料結構，會產生多個項目。

F#目前沒有內建支援字串、 清單、 陣列和 2D 陣列配量。

## <a name="basic-slicing-with-f-lists-and-arrays"></a>使用基本配量F#清單和陣列

最常見配量的資料類型為F#清單和陣列。 下列範例示範如何執行此動作的清單：

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

配量陣列，就如同配量清單：

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

## <a name="slicing-multidimensional-arrays"></a>配量的多維陣列

F#支援中的多維陣列F#核心程式庫。 如同一維陣列、 多維陣列的配量也相當有用。 不過，其他維度的簡介會強制稍有不同的語法，讓您可以採取特定的資料列和資料行的配量。

下列範例示範如何配量的 2D 陣列：

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
printfn "%A" twobyTwo
```

F#核心程式庫不會定義`GetSlice`的 3D 的陣列。 如果您想要配量或其他陣列或多個維度，您必須定義`GetSlice`成員自己。

## <a name="defining-slices-for-other-data-structures"></a>定義其他資料結構的配量

F#核心程式庫定義配量的一組有限的類型。 如果您想要定義配量更多的資料類型，則可以本身型別定義中或在類型擴充功能。

例如，以下是如何定義配量<xref:System.ArraySegment`1>以供方便存取的資料操作的類別：

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>使用內嵌，以避免 boxing，如有必要

如果您正在定義的類型，實際上是結構的配量，我們建議您`inline``GetSlice`成員。 F#編譯器會最佳化選擇性引數，避免任何堆積配置，因為配量。 這點非常重要的配量建構這類<xref:System.Span`1>，不能配置在堆積上。

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

- [索引的屬性](members/indexed-properties.md)