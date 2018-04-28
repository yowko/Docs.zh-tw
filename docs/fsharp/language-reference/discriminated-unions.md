---
title: 已區分的聯集 (F#)
description: '了解如何使用 F # 差別等位。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 64c91410e284ee16036c4f51bd2247475a202a45
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="discriminated-unions"></a>已區分的聯集

差別等位可以是其中一個具名的情況下，可能各有不同的值和類型的數字的值提供支援。 差別等位是適用於異質資料，特殊案例，包括有效和錯誤的情況下，可以有的資料變化為另一個，從一個執行個體的型別中的資料並為小型物件階層架構的替代選項。 此外，遞迴差別等位用來表示樹狀目錄中的資料結構。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a>備註
差別等位類似於聯集類型在其他語言中，但有一些差異。 做為與 c + + 中的等位型別或在 Visual Basic 中的之變數類型的值中所儲存的資料不被固定;它可以是其中幾個不同的選項。 不同於這些其他語言中的等位，不過，每個可能的選項擁有*案例識別碼*。 大小寫的識別項是各種可能的值，這個類型的物件; 類型名稱值是選擇性的。 如果值不存在，就有一個情況相當於列舉案例。 如果值存在，每個值可以是單一值的指定的類型或彙總多個欄位的相同或不同類型的 tuple。 為準，F # 3.1，您可以指定個別欄位的名稱，但名稱是選擇性的即使名為相同的大小寫的其他欄位。

例如，請考慮下列的圖形類型宣告。

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

上述程式碼會宣告差別聯集圖形，可以有三種情況的任何值： 矩形、 圓形和角柱。 每個案例具有一組不同的欄位。 欄位案例有兩個具名的矩形，這兩個型別`float`，具有名稱寬度和長度。 圓形案例有一個具名的欄位，radius。 角柱案例有三個欄位，其中的 （寬度和高度） 兩個名為欄位。 未命名的欄位稱為匿名的欄位。

您可以根據下列範例為具名和匿名欄位提供值，以建構物件。

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

此程式碼示範您可以使用具名的欄位初始化，或您可以依賴的宣告中的欄位順序，並只接著每個欄位提供值。 建構函式呼叫，如`rect`先前的程式碼會使用具名的欄位，但建構函式呼叫，如`circ`使用順序。 您可以混合的已排序的欄位和欄位，如所示建構`prism`。

`option`類型是簡單的差別等位在 F # 核心程式庫。 `option`型別宣告，如下所示。

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

先前的程式碼指定的型別`Option`是有兩種情況下，差別聯集`Some`和`None`。 `Some`案例有關聯的值是由一個型別由型別參數的匿名欄位組成`'a`。 `None`案例有沒有相關聯的值。 因此`option`類型指定的泛型類型，都有某些型別或任何值的值。 型別`Option`也有一個小寫類型別名`option`，也就是多常用。

大小寫的識別項可以作為差別聯集類型的建構函式。 例如，下列程式碼用來建立的值`option`型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

模式比對運算式中，也會使用大小寫的識別項。 在模式比對運算式中，識別項可供個別案例與相關聯的值。 例如，在下列程式碼，`x`識別項的值會指定相關聯`Some`案例`option`型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

在模式比對運算式中，您可以使用具名的欄位來指定差別聯集的相符項目。 針對先前已宣告的圖形類型，您可以使用具名的欄位，如下列程式碼所示來擷取欄位的值。

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

一般來說，大小寫的識別項可以利用不含限定聯集的名稱。 如果您想要一律以聯集的名稱限定的名稱，您可以套用[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)等位型別定義此屬性。

### <a name="unwrapping-discriminated-unions"></a>解除包裝的差別等位

F # 差別等位中通常用於在網域模型包裝單一類型。 所以可以輕鬆地擷取透過以及模式比對的基礎值。 您不需要使用比對運算式針對單一案例：
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

## <a name="struct-discriminated-unions"></a>結構的差別等位

從 F # 4.1 開始，您也可以代表差別等位為結構。  做法是使用`[<Struct>]`屬性。

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

由於這些是實值類型和參考型別時，會有額外考量相較於參考差別等位：

1. 可複製為實值類型，並且具有實值類型語意。
2. 您無法使用 multicase 結構 Discriminated Union 的遞迴類型定義。
3. 您必須提供 Discriminated Union multicase 結構案例的唯一名稱。

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>使用差別聯的集而不物件階層架構
您通常可以使用差別聯集為小型物件階層簡單的替代方案。 例如，下列差別聯集無法使用而不是`Shape`基底類別具有衍生類型的圓形，方形，依此類推。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

虛擬方法，以計算區域或周邊，您會改用物件導向的實作中，您可以使用模式比對分支到適當的公式來計算這些數量。 在下列範例中，不同的公式用來計算區域中的，根據圖形。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

其輸出如下：

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>使用資料的樹狀結構的差別等位
差別等位可以是遞迴的這表示等位本身可以納入一或多個案例的型別。 遞迴差別等位可以用來建立樹狀結構，可用來程式設計語言中的模型運算式。 下列程式碼中，遞迴差別聯集用來建立二元樹狀資料結構。 聯集包含兩種情況下， `Node`，這是整數值與左邊和右邊子樹節點和`Tip`，這會終止在樹狀結構。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

先前的程式碼，`resultSumTree`具有值為 10。 下圖顯示的樹狀結構`myTree`。

![MyTree 的樹狀結構](../media/TreeStructureDiagram.png)

差別等位工作樹狀結構中的節點都是異質性的情況。 下列程式碼類型`Expression`代表抽象語法樹狀目錄的運算式中簡單的程式設計語言支援加法和乘法的數字和變數。 部分聯集的情況下無法遞迴且代表其中一個數字 (`Number`) 或變數 (`Variable`)。 其他情況下都是遞迴，而且代表作業 (`Add`和`Multiply`)，其中運算元也是運算式。 `Evaluate`函式會使用遞迴程序的語法樹狀目錄的比對運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

此程式碼執行時，值`result`為 5。

## <a name="common-attributes"></a>常見屬性

差別等位中，常見的下列屬性：

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]` （F # 4.1 和更新版本）

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
