---
title: 已區分的聯集
description: 瞭解如何使用 F# 歧視結合。
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400215"
---
# <a name="discriminated-unions"></a>已區分的聯集

歧視聯合為值提供支援，這些值可以是許多命名案例之一，可能每個值和類型不同。 受歧視結合對異構資料很有用;可能有特殊情況的資料，包括有效和錯誤案例;因類型而異的資料;並作為小物件層次結構的替代方案。 此外，遞迴區分結合用於表示樹資料結構。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>備註

歧視聯合與其他語言中的聯合類型類似，但存在差異。 與 C++ 中的聯合類型或 Visual Basic 中的變體類型一樣，存儲在值中的資料不是固定的;它可以是幾個不同的選項之一。 但是，與這些其他語言中的聯合不同，每個可能的選項都給定一個*案例識別碼*。 案例識別碼是此類型物件可能具有的各種可能類型的值的名稱;值是可選的。 如果不存在值，則大小寫等效于枚舉大小寫。 如果存在值，則每個值可以是指定類型的單個值，也可以是聚合相同或不同類型的多個欄位的元組。 您可以為單個欄位指定名稱，但該名稱是可選的，即使在同一情況下命名了其他欄位也是如此。

受歧視聯合的可訪問性`public`預設為 。

例如，請考慮以下形狀類型的聲明。

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

前面的代碼聲明一個受歧視的聯合形狀，它可以具有三種情況中的任何一個的值：矩形、圓體和棱鏡。 每個案例都有一組不同的欄位。 矩形大小寫有兩個命名欄位，兩個`float`命名欄位的類型，具有名稱寬度和長度。 圓大小寫只有一個命名欄位，半徑。 棱鏡大小寫有三個欄位，其中兩個欄位（寬度和高度）被命名為欄位。 未命名的欄位稱為匿名欄位。

通過根據以下示例為命名欄位和匿名欄位提供值來構造物件。

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

此代碼顯示，您可以在初始化中使用命名欄位，也可以依賴聲明中欄位的順序，並依次為每個欄位提供值。 上一個代碼`rect`中的建構函式調用使用命名欄位，但建構函式調用`circ`使用排序。 可以混合有序欄位和命名欄位，如 在 構造 中`prism`。

該`option`類型是 F# 核心庫中的簡單區分聯合。 類型`option`聲明如下。

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

前面的代碼指定類型`Option`是具有兩個案例的受歧視聯合，`Some`和`None`。 案例`Some`具有一個關聯值，該值由一個匿名欄位組成，其類型由類型`'a`參數表示。 案例`None`沒有關聯的值。 因此，`option`類型指定具有特定類型值或無值的泛型型別。 類型`Option`還有一個小寫類型別名`option`，這是更常用的。

案例識別碼可用作區分聯合類型的建構函式。 例如，以下代碼用於創建`option`類型的值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

大小寫識別碼也用於模式匹配運算式。 在模式匹配運算式中，為與單個情況關聯的值提供識別碼。 例如，在以下代碼中，`x`是給定與`Some``option`類型大小寫關聯的值的識別碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

在模式匹配運算式中，可以使用命名欄位指定受區別的聯合匹配。 對於以前聲明的 Shape 類型，可以使用命名欄位，如以下代碼所示，以提取欄位的值。

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

通常，可以使用案例識別碼，而無需使用聯合名稱對其進行限定。 如果希望名稱始終與聯合的名稱限定，則可以將["需要限定Access"](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp])屬性應用於聯合類型定義。

### <a name="unwrapping-discriminated-unions"></a>未包裝的受歧視聯合

在 F# 中，區分聯合通常用於域建模，用於包裝單個類型。 通過模式匹配也很容易提取基礎值。 不需要對單個情況使用匹配運算式：

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

模式匹配也直接允許在函數參數中進行，因此您可以在那裡打開單個大小寫：

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>結構歧視聯盟

您還可以將"受歧視聯合"表示為結構。  這使用屬性`[<Struct>]`完成。

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

由於這些數值型別而不是參考型別，因此與引用區分結合相比，存在額外的注意事項：

1. 它們作為數值型別複製，並且具有數值型別語義。
2. 不能使用具有多大小寫結構的區分聯合的遞迴類型定義。
3. 您必須為多大小寫結構區分聯合提供唯一的案例名稱。

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>使用可區分聯合而不是物件層次結構

通常可以使用受歧視的聯合作為小物件層次結構的更簡單的替代方法。 例如，可以使用以下受歧視聯合來代替具有圓、平方等`Shape`派生類型的基類。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

可以使用模式匹配到分支到適當的公式來計算這些數量，而不是像在物件導向的實現中使用那樣計算區域或週邊的虛擬方法。 在下面的示例中，使用不同的公式來計算區域，具體取決於形狀。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

輸出如下所示：

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>對樹資料結構使用區分聯合

可進行遞迴，這意味著工會本身可以包含在一個或多個案例的類型中。 遞迴區分結合可用於創建樹結構，這些結構用於對程式設計語言中的運算式建模。 在以下代碼中，遞迴區分聯合用於創建二進位樹資料結構。 聯合由兩個案例組成，`Node`即具有整數值的節點和左右子樹，以及`Tip`終止樹。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

在前面的代碼中，`resultSumTree`具有值 10。 下圖顯示了 的`myTree`樹結構。

![顯示 MyTree 的樹形結構的圖表。](../media/discriminated-unions/tree-structure-mytree.png)

如果樹中的節點是異構的，則區分結合可以很好地工作。 在以下代碼中，類型`Expression`表示運算式的抽象語法樹，該語言支援數位和變數的添加和乘法。 某些聯合案例不是遞迴的，表示數位 （`Number`） 或變數 （`Variable`） 。 其他情況是遞迴的，並表示操作 （`Add`和`Multiply`），其中運算元也是運算式。 函數`Evaluate`使用匹配運算式遞迴處理語法樹。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

執行此代碼時，值`result`為 5。

## <a name="members"></a>成員

可以定義受歧視工會的成員。 下面的示例演示如何定義屬性和實現介面：

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

## <a name="common-attributes"></a>常見屬性

以下屬性常見於受歧視聯合：

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
