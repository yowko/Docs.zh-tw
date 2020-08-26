---
title: 已區分的聯集
description: '瞭解如何使用 F # 區分等位。'
ms.date: 08/15/2020
ms.openlocfilehash: 3f8ac656bd00b1022b2b13ee1be7ca5c98f68db5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812129"
---
# <a name="discriminated-unions"></a>已區分的聯集

差異聯集可支援可能是數個命名案例之一的值，可能是每個都有不同的值和類型。 相異聯集適用于異質資料;可能具有特殊案例的資料，包括有效和錯誤案例;從某個實例到另一個實例的類型不同的資料;以及做為小型物件階層的替代方案。 此外，遞迴差異聯集用來表示樹狀結構資料結構。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>備註

相異聯集與其他語言的等位類型類似，但有一些差異。 如同 c + + 中的等位類型或 Visual Basic 中的 variant 類型，儲存在值中的資料不是固定的;它可以是數個不同選項的其中一個。 不過，不同于這些其他語言的等位，每個可能的選項都會獲得一個 *案例識別碼*。 案例識別碼是適用于各種可能類型之值的名稱，這些類型的物件可能是：這些值是選擇性的。 如果值不存在，則案例相當於列舉案例。 如果有值，每個值都可以是指定類型的單一值，或是匯總多個相同或不同類型之欄位的元組。 您可以提供個別欄位的名稱，但名稱是選擇性的，即使相同案例中的其他欄位已命名也一樣。

區分等位的協助工具預設為 `public` 。

例如，請考慮下列圖形類型的宣告。

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

上述程式碼會宣告差異聯集圖形，其值可以是下列三種情況之一：矩形、圓形和 Prism。 每個案例都有一組不同的欄位。 矩形大小寫有兩個名稱為的欄位，兩者都 `float` 有名稱寬度和長度的型別。 圓形案例只有一個命名欄位，半徑。 Prism 案例有三個欄位，其中兩個 (寬度和高度) 命名為 [欄位]。 未命名的欄位稱為匿名欄位。

您可以根據下列範例提供已命名和匿名欄位的值來建立物件。

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

這段程式碼顯示您可以在初始化中使用已命名的欄位，也可以依賴宣告中的欄位順序，然後再依序提供每個欄位的值。 先前程式碼中的函式呼叫會 `rect` 使用命名欄位，但的函式呼叫會 `circ` 使用排序。 您可以混用已排序的欄位和命名欄位，就像在的結構中一樣 `prism` 。

此 `option` 類型是 F # 核心程式庫中的簡單差異聯集。 型別宣告 `option` 如下。

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

先前的程式碼指定類型 `Option` 是具有兩個案例的差異聯集， `Some` 以及 `None` 。 `Some`案例具有相關聯的值，其中包含一個匿名欄位，而該欄位的型別是由型別參數表示 `'a` 。 `None`案例沒有相關聯的值。 因此， `option` 型別會指定具有某個類型值或沒有任何值的泛型型別。 此類型 `Option` 也有較常用的小寫類型別名 `option` 。

案例識別碼可用來當做差異聯集類型的函式。 例如，下列程式碼會用來建立類型的值 `option` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

案例識別碼也會在模式比對運算式中使用。 在模式比對運算式中，會提供與個別案例相關聯之值的識別碼。 例如，在下列程式碼中， `x` 是提供與型別案例相關聯之值的識別碼 `Some` `option` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

在模式比對運算式中，您可以使用指定的欄位來指定差異聯集相符專案。 針對先前宣告的圖形類型，您可以使用命名欄位，如下列程式碼所示，用來將欄位的值解壓縮。

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

一般情況下，您可以使用案例識別碼，而不使用聯集的名稱來限定。 如果您想要使用聯集的名稱來限定名稱，您可以將 [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) 屬性套用至聯集類型定義。

### <a name="unwrapping-discriminated-unions"></a>解除包裝區分等位

在 F # 差異等位中，通常用於包裝單一型別的網域模型。 您也可以透過模式比對，輕鬆地將基礎值解壓縮。 單一案例不需要使用 match 運算式：

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

下列範例為其示範：

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

也可以直接在函式參數中使用模式比對，因此您可以在該處解除包裝單一案例：

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>結構區分等位

您也可以將區分等位表示為結構。  這是透過屬性來完成 `[<Struct>]` 。

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

因為這些是實值型別，而不是參考型別，所以相較于參考差異聯集，還有其他考慮：

1. 它們會複製為實數值型別，並具有實數值型別的語義。
2. 您無法使用具有 multicase 結構差異聯集的遞迴型別定義。
3. 您必須為 multicase 結構差異聯集提供唯一的案例名稱。

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>使用區分聯集而非物件階層

您通常可以使用差異聯集做為小型物件階層的較簡單替代項。 例如，您可以使用下列差異聯集，而不是 `Shape` 具有圓形、正方形等衍生類型的基類。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

您可以使用模式比對來分支至適當的公式來計算這些數量，而不是使用虛擬方法來計算區域或周邊。 在下列範例中，根據圖形，使用不同的公式來計算區域。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

輸出如下所示：

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>針對樹狀結構資料結構使用區分聯集

差異聯集可以是遞迴的，也就是說，等位本身可以包含在一或多個案例的型別中。 遞迴差異聯集可以用來建立樹狀結構，用來建立程式設計語言中的運算式模型。 在下列程式碼中，會使用遞迴差異聯集來建立二進位樹狀結構資料結構。 Union 包含兩個案例，也 `Node` 就是具有整數值、左和右樹系的節點，以及用 `Tip` 來終止樹狀結構的節點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

在先前的程式碼中， `resultSumTree` 的值為10。 下圖顯示的樹狀結構 `myTree` 。

![顯示 myTree 樹狀結構的圖表。](../media/discriminated-unions/tree-structure-mytree.png)

如果樹狀結構中的節點是異類的，則區分聯集的運作效果很好。 在下列程式碼中，類型 `Expression` 以簡單的程式設計語言表示運算式的抽象語法樹狀結構，支援數位和變數的加法和乘法。 某些聯集案例不是遞迴的，且代表 `Number` () 的 () 或變數 `Variable` 。 其他案例是遞迴的，表示作業 (`Add` 和 `Multiply`) ，其中運算元也是運算式。 `Evaluate`函數會使用 match 運算式以遞迴方式處理語法樹狀結構。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

執行此程式碼時，的值 `result` 為5。

## <a name="members"></a>成員

您可以定義區分等位的成員。 下列範例顯示如何定義屬性並執行介面：

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

下列屬性通常會出現在區分等位中：

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
