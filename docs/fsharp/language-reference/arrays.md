---
title: 陣列
description: 瞭解如何以程式F#設計語言建立和使用陣列。
ms.date: 05/16/2016
ms.openlocfilehash: 142d2c8d9aa7247e1490867a7bb905e2e7fec41e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630048"
---
# <a name="arrays"></a>陣列

> [!NOTE]
> API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

陣列是固定大小、以零為基底、可變動的連續資料元素集合, 這些專案全都屬於相同的類型。

## <a name="creating-arrays"></a>建立陣列

您可以透過數種方式來建立陣列。 您可以藉由列出介於和`[|` `|]`之間的連續值, 並以分號分隔, 來建立小型陣列, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

您也可以將每個元素放在不同的行上, 在此情況下, 分號分隔符號是選擇性的。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

陣列元素的類型是從使用的常值推斷而來, 且必須一致。 下列程式碼會造成錯誤, 因為1.0 是 float, 而2和3是整數。

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

您也可以使用順序運算式來建立陣列。 以下範例會建立從1到10的整數的平方陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

若要建立陣列, 其中所有元素都初始化為零, 請使用`Array.zeroCreate`。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a>存取元素

您可以使用點運算子 (`.`) 和括弧 (`[`和`]`) 來存取陣列元素。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

陣列索引從0開始。

您也可以使用配量標記法來存取陣列元素, 這可讓您指定陣列的子範圍。 配量標記法的範例如下。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

當使用配量標記法時, 會建立陣列的新複本。

## <a name="array-types-and-modules"></a>陣列類型和模組

所有F#陣列的類型都是 .NET Framework 類型<xref:System.Array?displayProperty=nameWithType>。 因此, F#陣列支援中<xref:System.Array?displayProperty=nameWithType>提供的所有功能。

Library 模組[`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)支援一維陣列上的作業。 模組`Array2D`、 `Array3D`和包含的函式,分別支援兩個、三個和四個維度之陣列的作業。`Array4D` 您可以使用<xref:System.Array?displayProperty=nameWithType>, 建立大於四的次序陣列。

### <a name="simple-functions"></a>簡單函式

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)取得元素。 [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)提供陣列的長度。 [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)將元素設定為指定的值。 下列程式碼範例說明如何使用這些函數。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

輸出如下。

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>建立陣列的函式

有數個函式會建立陣列, 而不需要現有的陣列。 [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)建立不包含任何元素的新陣列。 [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)建立指定大小的陣列, 並將所有元素設定為提供的值。 [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)建立陣列, 並指定要產生元素的維度和函式。 [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)建立陣列, 其中所有的元素都會初始化為數組類型的零值。 下列程式碼會示範這些函數。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

輸出如下。

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)建立新的陣列, 其中包含從現有陣列複製的元素。 請注意, 複製是淺層複製, 這表示如果元素類型是參考型別, 則只會複製參考, 而不會複製基礎物件。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

上述程式碼的輸出如下所示:

```
[|Test1; Test2; |]
[|; Test2; |]
```

此字串`Test1`只會出現在第一個陣列中, 因為建立新專案的作業會覆寫`firstArray`中的參考, 但不會影響仍然存在於中`secondArray`之空字串的原始參考。 此字串`Test2`會出現在這兩個`Insert`陣列中, <xref:System.Text.StringBuilder?displayProperty=nameWithType>因為類型的作業<xref:System.Text.StringBuilder?displayProperty=nameWithType>會影響在這兩個數組中所參考的基礎物件。

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)從陣列的子範圍產生新的陣列。 您可以藉由提供起始索引和長度來指定子範圍。 下列程式碼示範 `Array.sub` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

輸出顯示子陣列從專案5開始, 且包含10個元素。

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)結合兩個現有的陣列, 以建立新的陣列。

下列程式碼示範**陣列. append**。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

上述程式碼的輸出如下所示。

```
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)選取要包含在新陣列中之陣列的元素。 下列程式碼示範`Array.choose`。 請注意, 陣列的元素類型不一定要符合選項類型中所傳回值的類型。 在此範例中, 專案類型為`int` , 而選項是多項式`elem*elem - 1`函式的結果 (做為浮點數)。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

上述程式碼的輸出如下所示。

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)在現有陣列的每個陣列元素上執行指定的函式, 然後收集函數所產生的專案, 並將它們結合到新的陣列中。 下列程式碼示範`Array.collect`。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

上述程式碼的輸出如下所示。

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)採用一連串的陣列, 並將它們結合成單一陣列。 下列程式碼示範`Array.concat`。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

上述程式碼的輸出如下所示。

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)採用布林條件函式, 並產生新的陣列, 其中只包含來自輸入陣列的條件為 true 的元素。 下列程式碼示範`Array.filter`。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

上述程式碼的輸出如下所示。

```
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)藉由反轉現有陣列的順序, 產生新的陣列。 下列程式碼示範`Array.rev`。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

上述程式碼的輸出如下所示。

```
"Hello world!"
```

您可以使用管線運算子 (`|>`) 輕鬆地結合陣列模組中的函式, 以轉換陣列, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

輸出為

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>多維陣列

多維陣列可以建立, 但是沒有寫入多維陣列常值的語法。 使用運算子[`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) , 從陣列元素的序列順序建立陣列。 序列可以是陣列或清單常值。 例如, 下列程式碼會建立二維陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

您也可以使用[`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b)函式來初始化兩個維度的陣列, 而類似的函數適用于三和四個維度的陣列。 這些函式會採用用來建立元素的函式。 若要建立二維陣列, 其中包含設定為初始值的專案, 而不是指定函式, 請使用[`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804)函式, 此函數也適用于最多四個維度的陣列。 下列程式碼範例會先示範如何建立陣列陣列, 其中包含所需的元素, 然後使用`Array2D.init`來產生所需的二維陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

陣列的索引和配量語法支援最高至等級4的陣列。 當您指定多個維度中的索引時, 您可以使用逗號來分隔索引, 如下列程式碼範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

二維陣列的類型會寫出`<type>[,]`為 ( `int[,]`例如,, `double[,]`), 而三維陣列的類型則會寫入為`<type>[,,]`, 而對於較高維度的陣列則為。

只有一維陣列可用的函數子集也適用于多維陣列。 如需詳細資訊, [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d)請[`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d)參閱[`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d)、、 [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d)和。

### <a name="array-slicing-and-multidimensional-arrays"></a>陣列切割和多維陣列

在二維陣列 (矩陣) 中, 您可以藉由指定範圍並使用萬用字元 (`*`) 字元來指定完整的資料列或資料行, 來將子矩陣解壓縮。

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

從F# 3.1, 您可以將多維陣列分解成相同或較低維度的 subarrays。 例如, 您可以藉由指定單一資料列或資料行, 從矩陣取得向量。

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

您可以針對實作為元素存取運算子和`GetSlice`多載方法的類型使用此切割語法。 例如, 下列程式碼會建立包裝F# 2d 陣列的矩陣類型、執行專案屬性以提供陣列索引編制的支援, 以及執行的`GetSlice`三個版本。 如果您可以使用此程式碼當做矩陣類型的範本, 則可以使用本節所述的所有切割作業。

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

### <a name="boolean-functions-on-arrays"></a>陣列上的布耳函數

一或兩[`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e)個數組中的函式[和測試專案分別為。`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) 這些函式會採用測試函式`true` , 並在有符合條件的元素 (或`Array.exists2`專案組) 時傳回。

下列程式碼示範`Array.exists`和`Array.exists2`的用法。 在這些範例中, 會藉由只套用其中一個引數 (在這些情況下為函數引數) 來建立新的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

上述程式碼的輸出如下所示。

```
true
false
false
true
```

同樣地, [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4)函式會測試陣列, 以判斷每個元素是否符合布林條件。 此變化[`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9)會使用包含兩個相等長度陣列之元素的布林函式, 來執行相同的工作。 下列程式碼說明這些函式的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

這些範例的輸出如下所示。

```
false
true
true
false
```

### <a name="searching-arrays"></a>搜尋陣列

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)採用布耳函數, 並傳回函式傳回的第一個`true`專案, <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType>如果找不到符合條件的專案, 則會引發。 [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)類似`Array.find`, 但它會傳回專案的索引, 而不是元素本身。

下列程式碼會`Array.find`使用`Array.findIndex`和來尋找同時為完美方形和完美 cube 的數位。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

輸出如下。

```
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)類似于`Array.find`, 但它的結果是選項類型, `None`如果找不到任何元素, 則會傳回。 `Array.tryFind``Array.find`當您不知道相符的元素是否在陣列中時, 應該使用而不是。 同樣地[`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) , 類似[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)于選項類型為傳回值的例外。 如果找不到任何元素, 則選項`None`為。

下列程式碼示範 `Array.tryFind` 的用法。 此程式碼視先前的程式碼而定。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

輸出如下。

```
Found an element: 1
Found an element: 729
```

當[`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e)您需要轉換專案, 以及找出元素時, 請使用。 結果是第一個專案, 函式會將轉換的元素當做選項值傳回, `None`如果找不到這類元素, 則為。

下列程式碼示範 `Array.tryPick` 的用法。 在此情況下, 會定義數個本機 helper 函式來簡化程式碼, 而不是 lambda 運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

輸出如下。

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>在陣列上執行計算

[`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e)函式會傳回陣列中每個元素的平均值。 它受限於支援精確除以整數的元素類型, 其中包括浮點類型, 而不是整數類型。 [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54)函式會傳回每個元素上呼叫函式的結果平均值。 針對整數類型的陣列, 您可以使用`Array.averageBy` , 並讓函式將每個專案轉換成浮點類型以進行計算。

如果[`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b)元素[`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd)類型支援, 請使用或來取得最大或最小專案。 同樣地[`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) , [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f)和允許先執行函式, 可能會轉換成支援比較的類型。

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)加入陣列的元素, 並[`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b)在每個專案上呼叫函式, 並將結果加在一起。

若要在陣列中的每個元素上執行函式, 而不儲存[`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516)傳回值, 請使用。 對於涉及兩個相等長度陣列的函數, 請[`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc)使用。 如果您也需要保留函數結果的陣列, 請使用[`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45)或[`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), 這會在兩個數組上一次操作。

變數的[`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486)變化[`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405)和允許專案的索引會包含在計算中, [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4)而和[`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0)則相同。

[`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c)[函式`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d)、 [、、`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) 、和包含陣列所有元素的執行演算法。 [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9) [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09) [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0) 同樣地, 變數[`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79)和[`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862)會在兩個數組上執行計算。

這些用來執行計算的函式會對應至[清單模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)中相同名稱的函式。 如需使用範例, 請參閱[清單](lists.md)。

### <a name="modifying-arrays"></a>修改陣列

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)將元素設定為指定的值。 [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)將陣列中的元素範圍設定為指定的值。 下列程式碼提供的範例`Array.fill`。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

輸出如下。

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

您可以使用[`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) , 將一個陣列的子區段複製到另一個陣列。

### <a name="converting-to-and-from-other-types"></a>來回轉換其他類型

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)從清單建立陣列。 [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)從序列建立陣列。 [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)和[`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4)會從陣列類型轉換成這些其他集合類型。

### <a name="sorting-arrays"></a>排序陣列

使用[`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312)來排序陣列, 方法是使用泛型比較函數。 使用[`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b)來指定產生值 (稱為索引*鍵*) 的函式, 以使用索引鍵上的泛型比較函數進行排序。 如果[`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95)您想要提供自訂比較函數, 請使用。 `Array.sort`、 `Array.sortBy`和`Array.sortWith`全都會以新陣列的形式傳回已排序的陣列。 變體[`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0)、 [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)和[`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b)會修改現有的陣列, 而不是傳回新的陣列。

### <a name="arrays-and-tuples"></a>陣列和元組

函式會將元組配對的陣列[轉換成陣列的元組,反之亦然。`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)和[`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677)很相似, 不同之處在于它們會與三個數組的三個元素或元組的元組搭配使用。

## <a name="parallel-computations-on-arrays"></a>陣列上的平行計算

模組[`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09)包含在陣列上執行平行計算的函數。 在版本4之前以 .NET Framework 版本為目標的應用程式中, 無法使用此模組。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
