---
title: 已區分的聯集 (F#)
description: 了解如何使用 F# 差別聯集。
ms.date: 05/16/2016
ms.openlocfilehash: 06d6c154790f659c0c7ff73290357ab50a134362
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43788119"
---
# <a name="discriminated-unions"></a>已區分的聯集

差別等位可以是其中一個具名案例數，而每個不同的值和類型的值提供支援。 差別等位是適用於異質資料，可以有特殊的情況下，包括有效和錯誤案例的資料為另一個，從一個執行個體的型別中改變資料並為小型物件階層架構的替代方式。 此外，遞迴的已區分聯集用來代表樹狀資料結構。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>備註

差別聯的集是以其他語言的聯集類型類似，但有一些差異。 做為與 c + + 中的等位型別或在 Visual Basic 中的變數類型的值中儲存的資料不被固定;它可以是多個相異選項的其中一個。 不同於其他語言的聯集，不過，每個可能的選項基於*寫的識別項*。 案例識別項是各種可能的可能是此類型的物件; 的值類型的名稱值是選擇性的。 如果值不存在，它就相當於列舉案例。 如果值存在，每個值可以是單一值的指定的類型或彙總相同或不同類型的多個欄位的 tuple。 您可以為個別欄位的名稱，但名稱是選擇性的即使在相同的情況下的其他欄位的名稱。

差別聯集的存取範圍預設為`public`。

例如，請考慮下列 Shape 類型的宣告。

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

上述的程式碼宣告差別等位圖形，它可以有三種情況下的任何值： 矩形、 圓形和角柱。 每個案例中有一組不同的欄位。 矩形案例有兩個具名欄位，都屬於型別`float`，具有名稱寬度和長度。 圓形案例有只有一個具名的欄位，radius。 角柱案例有三個欄位，其中的 （寬度和高度） 兩個名為欄位。 未命名的欄位稱為匿名欄位。

您所提供的具名和匿名的欄位，根據下列範例值建構物件。

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

此程式碼示範您可以使用具名的欄位初始化，或您可以依賴宣告中的欄位順序，並只接著每個欄位提供值。 建構函式呼叫`rect`在先前的程式碼會使用具名的欄位，但建構函式呼叫的`circ`使用順序。 您可以混合排序的欄位，並命名為欄位，如建構`prism`。

`option`類型是 F# 核心程式庫中的簡單已區分聯集。 `option`類型宣告，如下所示。

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

先前的程式碼指定型別`Option`是具有兩個案例的已區分聯集`Some`和`None`。 `Some`案例有相關聯的值，其中包含型別由型別參數的一個匿名欄位`'a`。 `None`案例沒有任何相關聯的值。 因此`option`型別指定值為 some 類型或沒有值的泛型類型。 型別`Option`也有小寫類型別名`option`，也就是較常使用。

案例識別項可以作為已區分的聯集類型的建構函式。 比方說，下列程式碼用來建立值`option`型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

案例識別項也用於模式比對運算式。 在模式比對運算式中，會提供識別項的個別案例相關聯的值。 例如，在下列程式碼中，`x`識別項的值會指定相關聯`Some`案例`option`型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

在模式比對運算式中，您可以使用具名的欄位來指定差別聯集的相符項目。 對於先前宣告的圖形類型，您可以使用具名的欄位，如下列程式碼所示擷取欄位的值。

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

通常，案例識別項可不搭配聯集的名稱來限定它們。 如果您想要一律以聯集的名稱限定的名稱，您可以套用[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)等位型別定義的屬性。

### <a name="unwrapping-discriminated-unions"></a>解除包裝的差別聯的集

在 F# 差別聯集通常用於在領域模型中包裝單一類型。 它可輕易擷取透過模式比對以及基礎值。 您不需要使用比對運算式，針對單一案例：

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

下列範例為其示範：

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a>結構差別聯集

從 F# 4.1 開始，您也可以表示差別等位為結構。  做法是使用`[<Struct>]`屬性。

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

因為這些是實值型別，而且未參考的型別，所以會有額外考量相較於參考差別聯集：

1. 它們會複製為實值型別，並且具有實值型別語意。
2. 您無法使用 multicase 結構 Discriminated Union 的遞迴類型定義。
3. 您必須提供 Discriminated Union multicase 結構案例的唯一名稱。

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>使用已區分的聯集而非物件階層

您通常可以使用已區分的聯集為小型物件階層的簡單替代方式。 例如，可以使用下列已區分的聯集而不是`Shape`基底類別具有衍生型別的 circle、，方形，依此類推。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

若要計算區域或周邊的虛擬方法，為您是使用物件導向實作中，您可以使用模式比對分支至適當的公式來計算這些數量。 在下列範例中，不同的公式來計算區域中的，根據形狀。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

其輸出如下：

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>差別聯的集用於樹狀資料結構

差別等位可以是遞迴的這表示聯集本身可以納入一或多個案例的型別。 遞迴差別聯的集可以用來建立樹狀結構，用來在程式設計語言中的模型運算式。 下列程式碼中，遞迴的已區分聯集用來建立二進位樹狀資料結構。 聯集是由兩個案例所組成`Node`，這是整數值與和左右子節點和`Tip`，可結束樹狀結構。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

在先前的程式碼`resultSumTree`具有值為 10。 下圖顯示的樹狀結構`myTree`。

![Mytree 的樹狀結構](../media/TreeStructureDiagram.png)

在樹狀目錄中的節點是異質也運作差別聯的集。 下列程式碼類型`Expression`代表抽象語法樹狀目錄中的運算式中簡單的程式設計語言支援新增和相乘的數字和變數。 部分聯集案例不是遞迴和代表數字 (`Number`) 或變數 (`Variable`)。 其他情況下是遞迴的而且代表運算 (`Add`和`Multiply`)，其中運算元也是運算式。 `Evaluate`函式會使用比對運算式來遞迴處理語法樹狀結構。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

此程式碼執行時，值`result`為 5。

## <a name="common-attributes"></a>常見屬性

差別聯集中，常見的下列屬性：

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
