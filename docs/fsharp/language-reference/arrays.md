---
title: 陣列
description: '瞭解如何以 F # 程式設計語言建立和使用陣列。'
ms.date: 08/13/2020
ms.openlocfilehash: 37f781ccd2c7bc2ca2c7b93bda53bbb3ea93b504
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608508"
---
# <a name="arrays"></a>陣列

陣列是固定大小、以零為基礎且可變動的連續資料元素集合，這些專案全都屬於相同類型。

## <a name="create-arrays"></a>建立陣列

您可以用數種方式建立陣列。 您可以藉由列出介於和之間的連續值 `[|` `|]` ，並以分號分隔來建立小型陣列，如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

您也可以將每個專案放在個別的行上，在這種情況下，分號分隔符號是選擇性的。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

陣列元素的型別是從使用的常值推斷而來，而且必須是一致的。 下列程式碼會造成錯誤，因為1.0 是 float，而2和3是整數。

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

您也可以使用順序運算式來建立陣列。 以下範例會建立從1到10的整數平方陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

若要建立陣列，其中所有元素都會初始化為零，請使用 `Array.zeroCreate` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a>存取元素

您可以使用點運算子來存取陣列元素 (`.`) 和方括弧 (`[` 和 `]`) 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

陣列索引從0開始。

您也可以使用配量標記法來存取陣列元素，這可讓您指定陣列的子範圍。 配量標記法的範例如下。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

使用配量標記法時，會建立陣列的新複本。

## <a name="array-types-and-modules"></a>陣列類型和模組

所有 F # 陣列的型別都是 .NET Framework 型別 <xref:System.Array?displayProperty=nameWithType> 。 因此，F # 陣列支援中所有可用的功能 <xref:System.Array?displayProperty=nameWithType> 。

此[ `Array` 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)支援一維陣列上的作業。 模組 `Array2D` 、 `Array3D` 和包含的函式 `Array4D` 分別支援兩個、三個和四個維度的陣列作業。 您可以使用來建立順位大於四的陣列 <xref:System.Array?displayProperty=nameWithType> 。

### <a name="simple-functions"></a>簡單函數

[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) 取得專案。 [`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) 提供陣列的長度。 [`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 將元素設定為指定的值。 下列程式碼範例說明這些函數的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

輸出如下。

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>建立陣列的函式

有幾個函式會建立陣列，而不需要現有的陣列。 [`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) 建立不包含任何專案的新陣列。 [`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) 建立指定大小的陣列，並將所有元素設定為提供的值。 [`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) 建立陣列，並指定維度和函式來產生元素。 [`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) 建立陣列，其中所有元素都會初始化為數組類型的零值。 下列程式碼示範這些函數。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

輸出如下。

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) 建立新的陣列，其中包含從現有陣列複製的元素。 請注意，複製是淺層複製，這表示如果元素類型是參考型別，則只會複製參考，而不會複製基礎物件。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

上述程式碼的輸出如下所示：

```console
[|Test1; Test2; |]
[|; Test2; |]
```

字串 `Test1` 只會出現在第一個陣列中，因為建立新專案的作業會覆寫中的參考， `firstArray` 但不會影響仍然存在於中之空字串的原始參考 `secondArray` 。 字串 `Test2` 會出現在這兩個數組中 `Insert` ，因為類型上的作業 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 會影響在 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 這兩個數組中所參考的基礎物件。

[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) 從陣列的子範圍產生新的陣列。 您可以藉由提供開始索引和長度來指定子範圍。 下列程式碼示範 `Array.sub` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

輸出顯示子陣列在元素5開始，且包含10個元素。

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) 藉由結合兩個現有的陣列，建立新的陣列。

下列程式碼示範 **陣列. append**。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

上述程式碼的輸出如下所示。

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) 選取要包含在新陣列中的陣列元素。 下列程式碼示範 `Array.choose` 。 請注意，陣列的元素類型不需要符合選項類型中所傳回值的類型。 在此範例中，元素類型為， `int` 而選項是多項式函式的結果， `elem*elem - 1` 做為浮點數。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

上述程式碼的輸出如下所示。

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) 在現有陣列的每個陣列元素上執行指定的函式，然後收集函式所產生的元素，並將它們合併成新的陣列。 下列程式碼示範 `Array.collect` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

上述程式碼的輸出如下所示。

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) 接受一連串的陣列，並將它們結合成單一陣列。 下列程式碼示範 `Array.concat` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

上述程式碼的輸出如下所示。

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) 採用布林條件函式，並產生新的陣列，其中只包含輸入陣列中條件為 true 的元素。 下列程式碼示範 `Array.filter` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

上述程式碼的輸出如下所示。

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) 藉由反轉現有陣列的順序來產生新的陣列。 下列程式碼示範 `Array.rev` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

上述程式碼的輸出如下所示。

```console
"Hello world!"
```

您可以輕鬆地結合陣列模組中的函式，使用管線運算子 () 來轉換陣列 `|>` ，如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

輸出為

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>多維陣列

您可以建立多維度陣列，但是沒有寫入多維陣列常值的語法。 使用運算子 [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) ，從陣列元素序列的序列中建立陣列。 序列可以是陣列或清單常值。 例如，下列程式碼會建立二維陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

您也可以使用函式 [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) 來初始化兩個維度的陣列，而類似的函式可用於三和四個維度的陣列。 這些函式會取得用來建立元素的函式。 若要建立包含設定為初始值之專案的二維陣列，而不是指定函式，請使用函式 [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) ，此函式也適用于最多四個維度的陣列。 下列程式碼範例會先示範如何建立包含所需元素的陣列陣列，然後使用 `Array2D.init` 來產生所需的二維陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

陣列索引和切割語法支援最高排名4的陣列。 當您指定多個維度中的索引時，您可以使用逗號來分隔索引，如下列程式碼範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

二維陣列的型別會寫出做為 (例如， `<type>[,]` `int[,]` `double[,]`) ，而三維陣列的型別則是撰寫為 `<type>[,,]` ，依此類推，針對較高維度的陣列。

只有一維陣列的可用函式子集也適用于多維度陣列。

### <a name="array-slicing-and-multidimensional-arrays"></a>陣列切割和多維陣列

在二維陣列 (矩陣) 中，您可以指定範圍，並使用萬用字元 (`*`) 字元來指定整個資料列或資料行，藉以解壓縮子矩陣。

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

您可以將多維陣列分解成相同或較低維度的 subarrays。 例如，您可以藉由指定單一資料列或資料行，從矩陣取得向量。

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

您可以針對實際引數素存取運算子和多載方法的型別使用此切割語法 `GetSlice` 。 例如，下列程式碼會建立包裝 F # 2D 陣列的矩陣類型、執行專案屬性以提供陣列索引編制的支援，以及執行三個版本的 `GetSlice` 。 如果您可以使用此程式碼作為矩陣類型的範本，您可以使用本節描述的所有配量作業。

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

[`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) 一或兩個數組中的函式和測試專案，分別為。 `true`如果符合條件的) 有元素 (或元素組，則這些函式會採用測試函式，並傳回 `Array.exists2` 。

下列程式碼示範如何使用 `Array.exists` 和 `Array.exists2` 。 在這些範例中，會藉由只套用其中一個引數（在這些情況下為函式引數）來建立新的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

上述程式碼的輸出如下所示。

```console
true
false
false
true
```

同樣地，函 [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) 式會測試陣列，以判斷每個專案是否符合布林值條件。 變異 [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) 會使用布耳函數來執行相同的動作，此函式牽涉到兩個相等長度陣列的元素。 下列程式碼說明如何使用這些函數。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

這些範例的輸出如下所示。

```console
false
true
true
false
```

### <a name="search-arrays"></a>搜尋陣列

[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) 採用布林函式，並傳回函式傳回的第一個專案 `true` ， <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> 如果找不到符合條件的專案，則會引發。 [`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) 類似，不同的是它會傳回專案的 `Array.find` 索引，而不是元素本身。

下列 `Array.find` 程式碼會使用和 `Array.findIndex` 來找出同時為完美方形和完美 cube 的數位。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

輸出如下。

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) 類似 `Array.find` ，不同之處在于它的結果是選項類型， `None` 如果找不到任何元素，則會傳回。 `Array.tryFind``Array.find`如果您不知道相符的專案是否在陣列中，則應該使用而不是。 同樣地，它 [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) 也是一樣， `Array.findIndex` 但選項類型是傳回值。 如果找不到任何元素，則選項為 `None` 。

下列程式碼示範 `Array.tryFind` 的用法。 此程式碼相依于先前的程式碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

輸出如下。

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

[`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick)當您需要轉換元素，並加以尋找時，請使用。 結果為函式傳回已轉換元素做為選項值的第一個專案， `None` 如果找不到這類元素，則為。

下列程式碼示範 `Array.tryPick` 的用法。 在此情況下，不會使用 lambda 運算式，而是定義數個本機 helper 函數來簡化程式碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

輸出如下。

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a>在陣列上執行計算

函數會傳回 [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) 陣列中每個元素的平均值。 它受限於支援整數除以整數的專案類型，其中包含浮點數類型，但不包括整數類資料類型。 函數會傳回在 [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) 每個專案上呼叫函式的結果平均值。 若為整數類資料類型的陣列，您可以使用 `Array.averageBy` ，並讓函式將每個元素轉換成浮點數類型以進行計算。

[`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max)如果專案 [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) 類型支援，請使用或來取得最大或最小元素。 同樣地，也可讓函式 [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) 先執行，也許可以轉換成支援比較的型別。

[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) 加入陣列的元素，並 [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) 在每個專案上呼叫函式，並將結果加在一起。

若要在陣列中的每個元素上執行函式，而不儲存傳回值，請使用 [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) 。 若為涉及兩個相等長度陣列的函式，請使用 [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) 。 如果您也需要保留函式結果的陣列，請使用 [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) 或 [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) ，它會一次在兩個數組上運作。

變數 [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) 和可 [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) 讓元素的索引參與計算; 和相同的情況也是如此 [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) 。

[`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold)包含陣列所有元素的函式、、、、 [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) 和 [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) 執行演算法。 同樣地，變化 [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) 和 [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) 在兩個數組上執行計算。

這些執行計算的函式會對應到 [清單模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)中相同名稱的函式。 如需使用範例，請參閱 [清單](lists.md)。

### <a name="modify-arrays"></a>修改陣列

[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 將元素設定為指定的值。 [`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) 將陣列中的元素範圍設定為指定的值。 下列程式碼提供的範例 `Array.fill` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

輸出如下。

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

您可以使用將 [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) 某個陣列的子區段複製到另一個陣列。

### <a name="convert-to-and-from-other-types"></a>從其他類型轉換

[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) 從清單建立陣列。 [`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) 從序列建立陣列。 [`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) 並 [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) 從陣列型別轉換為這些其他集合類型。

### <a name="sort-arrays"></a>排序陣列

使用 [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) 來排序陣列，方法是使用泛型比較函數。 使用指定一個函式，此函式 [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) 會產生值（稱為索引 *鍵*），以在索引鍵上使用泛型比較函數進行排序。 [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith)如果您想要提供自訂比較函數，請使用。 `Array.sort`、 `Array.sortBy` 和 `Array.sortWith` 全都會以新陣列的形式傳回已排序的陣列。 變化 [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) 、 [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) 和會 [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) 修改現有的陣列，而不是傳回新的陣列。

### <a name="arrays-and-tuples"></a>陣列和元組

函數 [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) 和會 [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) 將元組的陣列轉換成陣列的元組，反之亦然。 [`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) 和 [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) 很類似，不同之處在于它們會使用三個元素的元組或三個數組的元組。

## <a name="parallel-computations-on-arrays"></a>針對陣列進行平行計算

模組 [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) 包含在陣列上執行平行計算的函數。 在版本4之前，以 .NET Framework 版本為目標的應用程式無法使用此模組。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [F# 類型](fsharp-types.md)
