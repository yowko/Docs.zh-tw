---
title: 繼承
description: 瞭解如何使用 ' F# inherit ' 關鍵字來指定繼承關聯性。
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627660"
---
# <a name="inheritance"></a>繼承

繼承是用來建立物件導向程式設計中的「is-a」關聯性或 subtyping 模型。

## <a name="specifying-inheritance-relationships"></a>指定繼承關聯性

您可以使用類別宣告中的`inherit`關鍵字來指定繼承關聯性。 基本的語法形式如下列範例所示。

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

一個類別最多隻能有一個直接基類。 如果您未使用`inherit`關鍵字指定基類, 類別會隱含繼承自。 `System.Object`

## <a name="inherited-members"></a>繼承的成員

如果類別繼承自另一個類別, 則衍生類別的使用者可以使用基類的方法和成員, 就如同它們是衍生類別的直接成員一樣。

任何 let 系結和函式參數都是類別的私用, 因此無法從衍生類別存取。

關鍵字`base`可在衍生類別中使用, 並參考基類實例。 其使用方式與自我識別碼類似。

## <a name="virtual-methods-and-overrides"></a>虛擬方法和覆寫

相較于其他 .NET 語言, 虛擬方法 ( F#和屬性) 在中的工作方式稍有不同。 若要宣告新的虛擬成員, 請使用`abstract`關鍵字。 無論您是否為該方法提供預設的實作為, 都可以執行此動作。 因此, 基底類別中虛擬方法的完整定義會遵循此模式:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

而在衍生類別中, 此虛擬方法的覆寫會遵循此模式:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

如果您省略基類中的預設實作為, 基底類別會變成抽象類別。

下列程式碼範例說明如何在基類中宣告新的`function1`虛擬方法, 以及如何在衍生類別中覆寫它。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>建構函式和繼承

基類的函式必須在衍生類別中呼叫。 基類的引數會出現在`inherit`子句的引數清單中。 所使用的值必須從提供給衍生類別的引數來判斷。

下列程式碼顯示基類和衍生類別, 其中衍生的類別會在繼承子句中呼叫基類的函式:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

在多個函式的情況下, 可以使用下列程式碼。 衍生類別的第一行程式碼是`inherit`子句, 而欄位則是以`val`關鍵字宣告的明確欄位來顯示。 如需詳細資訊, [請參閱明確欄位:`val`關鍵字。](./members/explicit-fields-the-val-keyword.md)

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>繼承的替代專案

在需要稍微修改類型的情況下, 請考慮使用物件運算式做為繼承的替代方法。 下列範例說明如何使用物件運算式, 做為建立新衍生型別的替代方法:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

如需物件運算式的詳細資訊, 請參閱[物件運算式](object-expressions.md)。

當您建立物件階層時, 請考慮使用區分聯集, 而不是繼承。 相異聯集也可以針對共用一般類型的不同物件, 建立各種不同的行為模型。 單一差異聯集通常不需要多個不同的衍生類別, 而是彼此的次要變化。 如需區分等位的詳細資訊, 請參閱[區分](discriminated-unions.md)等位。

## <a name="see-also"></a>另請參閱

- [物件運算式](object-expressions.md)
- [F# 語言參考](index.md)
