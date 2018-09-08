---
title: 陣列 (F#)
description: '了解如何建立及使用 F # 程式設計語言中的陣列。'
ms.date: 05/16/2016
ms.openlocfilehash: 27b73efc900ac2efc813fe66f81baa2e9ae1e843
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135727"
---
# <a name="arrays"></a>陣列

> [!NOTE]
API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

陣列是固定大小、 以零為起始、 可變的連續資料的項目都是相同類型的集合。

## <a name="creating-arrays"></a>建立陣列

您可以透過數種方式來建立陣列。 您可以藉由列出之間的連續值來建立小型陣列`[|`和`|]`並以分號分隔，如下列範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

您也可以將每個項目放在個別行中，情況下，分號分隔符號可有可無。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

陣列元素的型別從的常值來推斷，而且必須一致。 下列程式碼會導致錯誤，因為 1.0 為浮點，而 2 和 3 為整數。

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

您也可以使用循序項運算式來建立陣列。 以下是範例建立 1 到 10 之整數平方陣列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

若要建立的陣列，其中的所有項目會初始化為零，請使用`Array.zeroCreate`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a>存取項目

您可以使用點運算子來存取陣列項目 (`.`) 和括號 (`[`和`]`)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

陣列索引從 0 開始。

您也可以使用切割標記法，可讓您指定陣列的子範圍，以存取陣列項目。 切割標記法的範例如下。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

使用切割標記法時，會建立新陣列的複本。

## <a name="array-types-and-modules"></a>陣列類型和模組

所有的 F # 陣列的型別是.NET Framework 型別<xref:System.Array?displayProperty=nameWithType>。 因此，F # 陣列支援中可用的所有功能<xref:System.Array?displayProperty=nameWithType>。

程式庫模組[ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)支援一維陣列的作業。 模組`Array2D`， `Array3D`，和`Array4D`包含分別支援陣列的兩個三維和四維，作業的函式。 您可以建立陣列的陣序大於四個使用<xref:System.Array?displayProperty=nameWithType>。

### <a name="simple-functions"></a>簡單的函式

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) 取得項目。 [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) 提供陣列的長度。 [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) 指定的值設定的項目。 下列程式碼範例說明如何使用這些函式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

輸出如下。

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>建立陣列的函式

數個函式會建立陣列，而不需要現有的陣列。 [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) 建立新的陣列，其中不包含任何項目。 [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) 建立指定大小的陣列，並將所有項目設定為提供的值。 [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) 建立陣列，指定的維度和函式來產生項目。 [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) 建立的陣列，其中所有項目初始化陣列的型別為零的值。 下列程式碼示範這些函式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

輸出如下。

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) 建立新的陣列，其中包含從現有的陣列複製的元素。 請注意，複本是淺層複本，這表示，如果項目型別是參考型別，只將參考複製，而不是基礎的物件。 下列程式碼範例會說明這點。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

上述程式碼的輸出如下所示：

```
[|Test1; Test2; |]
[|; Test2; |]
```

字串`Test1`只會出現在第一個陣列的作業建立新的項目會覆寫中的參考，因為`firstArray`但不會影響仍存在於為空字串的原始參考`secondArray`。 字串`Test2`出現在兩個陣列，因為`Insert`上的作業<xref:System.Text.StringBuilder?displayProperty=nameWithType>型別會影響基礎<xref:System.Text.StringBuilder?displayProperty=nameWithType>物件，參考在兩個陣列。

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) 從陣列中的子範圍中產生新的陣列。 您可以提供的起始索引和長度，以指定子範圍。 下列程式碼示範 `Array.sub` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

輸出會顯示子陣列項目 5 開始，而且包含 10 個項目。

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) 藉由結合兩個現有的陣列建立新的陣列。

下列程式碼示範**Array.append**。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

上述程式碼的輸出如下所示。

```
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) 選取要包含在新的陣列中陣列的元素。 下列程式碼示範`Array.choose`。 請注意，不需要符合選項類型中傳回的值的型別陣列的項目類型。 在此範例中，項目類型是`int`選項是多項式函式的結果`elem*elem - 1`，做為浮點數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

上述程式碼的輸出如下所示。

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) 在現有陣列的每個陣列項目上執行指定的函式然後收集函式所產生的項目，並將它們合併成新的陣列。 下列程式碼示範`Array.collect`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

上述程式碼的輸出如下所示。

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) 序列的陣列，並將它們合併成單一陣列。 下列程式碼示範`Array.concat`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

上述程式碼的輸出如下所示。

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) 採用布林條件函式，並產生新的陣列，包含這些條件為 true 之輸入陣列項目。 下列程式碼示範`Array.filter`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

上述程式碼的輸出如下所示。

```
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) 藉由反轉現有陣列的順序來產生新的陣列。 下列程式碼示範`Array.rev`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

上述程式碼的輸出如下所示。

```
"Hello world!"
```

您可以輕鬆合併陣列模組中使用管線運算子來轉換陣列的函式 (`|>`)，如下列範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

輸出為

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>多維陣列

您可以建立多維陣列，但是沒有撰寫多維陣列常值的語法。 使用運算子[ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236)來從一連串的陣列項目序列建立陣列。 序列可以是陣列或清單常值。 例如，下列程式碼會建立二維陣列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

您也可以使用此函式[ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b)初始化陣列的兩個維度，與類似函式可供使用的三維和四維陣列。 這些函式會接受用來建立元素的函式。 若要建立包含項目設為初始的值，而不是指定函式的二維陣列，請使用[ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804)函式，這也適用於陣列最多四個維度。 下列程式碼範例首先顯示如何建立陣列的陣列，包含所需的項目，並接著會使用`Array2D.init`來產生所需的二維陣列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

陣列陣序 4 之前都支援陣列索引和分割語法。 當您指定多個維度的索引時，您使用逗號來分隔的索引，如下列程式碼範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]

二維陣列的型別會寫出做`<type>[,]`(例如`int[,]`， `double[,]`)，並三維陣列的型別撰寫為`<type>[,,]`，依此類推的更高維度的陣列。

也可用於多維陣列的一維陣列可用的函式的子集。 如需詳細資訊，請參閱 < [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d)， [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d)， [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d)，以及[ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d)。

### <a name="array-slicing-and-multidimensional-arrays"></a>陣列切割和多維陣列

在二維陣列 （矩陣） 中，您可以藉由指定範圍和使用萬用字元擷取子矩陣 (`*`) 字元來指定整個資料列或資料行。

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

自 F # 3.1 之後，您可以將多維陣列分解的相同或較低維度的子陣列。 例如，您也可以指定單一資料列或資料行，以取得向量從矩陣。

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

您可以使用此切割語法以型別會實作項目存取運算子，以及多載`GetSlice`方法。 例如，下列程式碼會建立包裝 F # 2D 陣列，實作提供支援，陣列編製索引，項目屬性，並實作三個版本的 Matrix 類型`GetSlice`。 如果您可以使用此程式碼做為範本，為矩陣類型，您可以使用本章節描述的所有切割作業。

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish = 
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>在陣列上的布林函式

函式[ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9)並[ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e)分別測試一個或兩個陣列中的項目。 這些函式採用測試函式，並傳回`true`如果沒有項目 (或項目配對`Array.exists2`) 滿足條件。

下列程式碼示範如何使用`Array.exists`和`Array.exists2`。 在這些範例中，新的函式會建立只套用其中一個引數，在這些情況下，函式引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

上述程式碼的輸出如下所示。

```
true
false
false
true
```

同樣地，此函式[ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4)測試陣列，以判斷每個項目是否都滿足布林條件。 變化[ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9)使用布林值的函式，牽涉到兩個陣列的長度相等的項目執行相同的動作。 下列程式碼說明如何使用這些函式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

如需這些範例輸出如下所示。

```
false
true
true
false
```

### <a name="searching-arrays"></a>搜尋陣列

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) 採用布林函式，並傳回第一個元素，則函數會傳回`true`，或引發<xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType>如果找到符合條件的項目。 [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) 就像`Array.find`，只不過它會傳回而不是項目本身之項目的索引。

下列程式碼會使用`Array.find`和`Array.findIndex`尋找是完全平方和完全立方的數字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

輸出如下。

```
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) 就像是`Array.find`，只不過它的結果是選項類型，且會傳回`None`如果不找到任何項目。 `Array.tryFind` 應該使用而不是`Array.find`時您不知道是否相符的項目是陣列中。 同樣地， [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a)類似[ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)不同之處在於選項類型是傳回的值。 如果不找到任何項目，則選項`None`。

下列程式碼示範 `Array.tryFind` 的用法。 此程式碼視先前的程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

輸出如下。

```
Found an element: 1
Found an element: 729
```

使用[ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e)當您需要轉換它尋找項目。 結果是此函數會傳回已轉換的項目，做為選項值，為第一個項目或`None`如果找到這類項目。

下列程式碼示範 `Array.tryPick` 的用法。 在此情況下，而不是 lambda 運算式，數種本機 helper 函式定義來簡化程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

輸出如下。

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>對陣列執行計算

[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e)函式會傳回陣列中的每個項目的平均值。 它僅限於支援完全整除的整數，其中包含浮點類型，而不是整數類型的項目型別。 [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54)函式傳回之結果的每個項目上呼叫函式的平均。 對於整數型別的陣列，您可以使用`Array.averageBy`讓函式將每個項目轉換成浮點計算的類型。

使用[ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b)或是[ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd)取得的最大或最小項目，如果項目型別支援。 同樣地， [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045)並[ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f)允許先執行，這可能會轉換成支援比較類型的函式。

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) 加入陣列的元素和[ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b)上每個項目呼叫函式，並將結果相加。

若要在陣列中每個項目上執行函式，而不儲存傳回的值，使用[ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516)。 針對涉及兩個陣列的長度相等的函式，使用[ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc)。 如果您也需要保留一個陣列的函式的結果，使用[ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45)或是[ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c)，作兩個陣列一次。

變化[ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486)並[ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405)允許以包含在計算項目的索引; 這也適用於[ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4)並[ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0)。

函式[ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09)， [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c)， [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d)， [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9)， [`Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)，並[ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad)執行涉及陣列的所有元素的演算法。 同樣地，變化[ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79)並[ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862)上兩個陣列執行計算。

執行計算的這些函式對應中的相同名稱的函式[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。 如需使用方式範例，請參閱[列出](lists.md)。

### <a name="modifying-arrays"></a>修改陣列

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) 指定的值設定的項目。 [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) 設定項目範圍中指定的值陣列。 下列程式碼提供的範例`Array.fill`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

輸出如下。

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

您可以使用[ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) ，將其中一個陣列的子區段複製到另一個陣列。

### <a name="converting-to-and-from-other-types"></a>其他型別來回轉換

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) 從清單建立陣列。 [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) 從序列建立陣列。 [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) 並[ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4)從陣列類型轉換為這些其他集合型別。

### <a name="sorting-arrays"></a>排序陣列

使用[ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312)來使用泛型比較函式中排序陣列。 使用[ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b)為指定的函式會產生值，稱為*金鑰*，若要排序的索引鍵上使用泛型比較函式。 使用[ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95)如果您想要提供自訂比較函式。 `Array.sort``Array.sortBy`，和`Array.sortWith`所有傳回的已排序的陣列，做為新陣列。 變化[ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0)， [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)，以及[ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b)修改現有的陣列，而不是傳回新的。

### <a name="arrays-and-tuples"></a>陣列和 Tuple

函式[ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187)並[ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48)將元組配對的陣列轉換成元組的陣列，反之亦然。 [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) 並[ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677)很類似，不同之處在於它們使用的三個元素的 tuple 或三個陣列的 tuple。

## <a name="parallel-computations-on-arrays"></a>陣列的平行計算

模組[ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09)包含在陣列上執行平行計算的函式。 無法在以.NET framework 版本 4 之前的版本為目標的應用程式中使用此模組。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F # 中;型別](fsharp-types.md)
