---
title: 已區分的聯集
description: 瞭解如何使用F#區分等位。
ms.date: 05/16/2016
ms.openlocfilehash: 940bc51f49e283c31846dd2047b749769b919838
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630356"
---
# <a name="discriminated-unions"></a>已區分的聯集

相異聯集提供的值, 可能是其中一個已命名的案例, 可能會有不同的值和類型。 區分等位適用于異質資料;可以有特殊案例的資料, 包括有效和錯誤的案例;從一個實例到另一個實例的類型不同的資料;和作為小型物件階層的替代方案。 此外, 遞迴的區分等位是用來表示樹狀結構的資料結構。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>備註

區分聯集與其他語言的等位類型類似, 但有差異。 如同中C++的聯集類型或 Visual Basic 中的 variant 類型, 儲存在值中的資料不會固定;它可以是幾個不同選項的其中一個。 不同于這些其他語言的等位, 每個可能的選項都會被賦予一個*案例識別碼*。 案例識別碼是此類型之物件的各種可能數值型別的名稱。這些值是選擇性的。 如果值不存在, 則案例相當於列舉案例。 如果有值, 每個值都可以是指定類型的單一值, 或是匯總相同或不同類型之多個欄位的元組。 您可以為個別的欄位指定名稱, 但名稱是選擇性的, 即使相同案例中的其他欄位命名也一樣。

區分等位的協助工具`public`預設為。

例如, 請考慮下列圖形類型的宣告。

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

上述程式碼會宣告一個區分聯集圖形, 其值可以是下列三種情況的其中一種:矩形、圓形和 Prism。 每個案例都有一組不同的欄位。 矩形案例有兩個名為的欄位, 兩`float`個都是類型, 其名稱為 width 和 length。 圓形案例只有一個命名欄位 [半徑]。 Prism 案例有三個欄位, 其中兩個 (寬度和高度) 為欄位。 未命名的欄位稱為「匿名欄位」。

您可以根據下列範例, 提供已命名和匿名欄位的值來建立物件。

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

這段程式碼顯示您可以在初始化中使用已命名的欄位, 或者您可以依賴宣告中的欄位順序, 然後只提供每個欄位的值。 先前程式`rect`代碼中的函式呼叫會使用已命名的欄位, 但的函數`circ`調用會使用排序。 您可以混合使用已排序的欄位和命名欄位, 如同的結構`prism`。

類型是F#核心程式庫中的簡單區分聯集。 `option` 類型`option`的宣告方式如下。

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

先前的程式碼指定類型`Option`為具有兩個案例的區分聯集, `Some`和。 `None` 案例有一個相關聯的值, 其中包含一個匿名欄位, 其型別是由型`'a`別參數表示。 `Some` 案例`None`沒有相關聯的值。 因此, `option`此型別會指定具有某個型別值或沒有值的泛型型別。 此類型`Option`也有一個較常用的小寫`option`類型別名。

案例識別碼可用來做為區分聯集類型的構造函式。 例如, 下列程式碼是用來建立`option`型別的值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

案例識別碼也會用於模式比對運算式。 在模式比對運算式中, 會提供與個別案例相關聯之值的識別碼。 例如, 在下列程式碼中, `x`是指定`Some`與`option`類型案例相關聯之值的識別碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

在模式比對運算式中, 您可以使用命名欄位來指定區分聯集的相符專案。 針對先前宣告的圖形類型, 您可以使用已命名的欄位, 如下列程式碼所示, 以解壓縮欄位的值。

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

一般來說, 您可以使用案例識別碼, 而不需要使用聯集的名稱來加以限定。 如果您想要讓名稱一律以聯集的名稱限定, 可以將[RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp])屬性套用至 union 類型定義。

### <a name="unwrapping-discriminated-unions"></a>解除包裝區分等位

在F#區分等位中, 通常會在用來包裝單一類型的網域模型中使用。 您也可以透過模式比對, 輕鬆地將基礎值解壓縮。 您不需要在單一案例中使用 match 運算式:

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

下列範例為其示範：

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

函式參數中也可直接使用模式比對, 因此您可以將單一案例解除包裝在該處:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>結構區分等位

您也可以將區分等位當做結構來表示。  這是使用`[<Struct>]`屬性來完成的。

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

因為這些是實值型別, 而不是參考型別, 所以相較于參考區分等位, 會有額外的考慮:

1. 它們會複製為實值型別, 並具有實數值型別的語義。
2. 您不能將遞迴型別定義與 multicase 結構區分聯集搭配使用。
3. 您必須為 multicase 結構區分聯集提供唯一的案例名稱。

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>使用區分聯集, 而不是物件階層

您通常可以使用區分聯集作為小型物件階層的較簡單替代方式。 例如, 您可以使用下列的區分聯集, 而不`Shape`是具有 circle、方形等衍生類型的基類。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

除了用來計算區域或周邊的虛擬方法之外, 您也可以在物件導向的執行中使用模式比對, 以適當的公式分支來計算這些數量。 在下列範例中, 會使用不同的公式來計算區域, 視圖形而定。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

其輸出如下：

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>使用樹狀資料結構的區分等位

區分聯集可以是遞迴的, 這表示等位本身可以包含在一或多個案例的類型中。 遞迴的區分等位可以用來建立樹狀結構, 用來以程式設計語言將運算式模型。 在下列程式碼中, 會使用遞迴的區分聯集來建立二進位樹狀結構資料結構。 聯集包含兩個案例, `Node`也就是具有整數值和左和右子樹的節點, 以及`Tip`終止樹狀結構的。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

在先前的程式碼`resultSumTree`中, 的值為10。 下圖顯示的樹狀結構`myTree`。

![顯示 myTree 樹狀結構的圖表。](../media/discriminated-unions/tree-structure-mytree.png)

如果樹狀結構中的節點是異類的, 則區分聯集的運作良好。 在下列程式碼中, 類型`Expression`會以簡單的程式設計語言, 表示運算式的抽象語法樹狀結構, 以支援數位和變數的加法和乘法。 某些聯集案例不是遞迴的, 而是代表數位`Number`() 或變數`Variable`()。 其他情況則是遞迴的, 表示作業`Add` ( `Multiply`和), 其中的運算元也是運算式。 `Evaluate`函式會使用 match 運算式來以遞迴方式處理語法樹狀結構。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

執行此程式碼時, 的值`result`會是5。

## <a name="members"></a>成員

您可以在區分等位上定義成員。 下列範例顯示如何定義屬性和實作為介面:

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a>通用屬性

下列屬性通常會出現在區分等位中:

* `[<RequireQualifiedAccess>]`
* `[<NoEquality>]`
* `[<NoComparison>]`
* `[<Struct>]`

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
