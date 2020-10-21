---
title: 繼承
description: "瞭解如何使用 ' inherit ' 關鍵字指定 F # 繼承關聯性。"
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223845"
---
# <a name="inheritance"></a>繼承

在物件導向程式設計中，會使用繼承來建立「是」關聯性或 subtyping 的模型。

## <a name="specifying-inheritance-relationships"></a>指定繼承關聯性

您可以在類別宣告中使用關鍵字來指定繼承關聯性 `inherit` 。 下列範例會顯示基本的語法形式。

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

一個類別最多隻能有一個直接基類。 如果您沒有使用關鍵字來指定基類 `inherit` ，則類別會隱含地繼承自 `System.Object` 。

## <a name="inherited-members"></a>繼承的成員

如果類別繼承自另一個類別，則衍生類別的使用者可以使用基類的方法和成員，如同它們是衍生類別的直接成員。

任何 let 系結和函式參數都是類別私用的，因此無法從衍生類別存取。

關鍵字 `base` 會在衍生類別中提供，並參考基類實例。 它會像自我識別碼一樣使用。

## <a name="virtual-methods-and-overrides"></a>虛擬方法和覆寫

相較于其他 .NET 語言， (和屬性的虛擬方法) 在 F # 中的運作方式稍有不同。 若要宣告新的虛擬成員，請使用 `abstract` 關鍵字。 無論您是否提供該方法的預設執行，您都可以這麼做。 因此，基底類別中虛擬方法的完整定義會遵循此模式：

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

在衍生類別中，此虛擬方法的覆寫會遵循此模式：

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

如果您省略基類中的預設實值，基類就會變成抽象類別。

下列程式碼範例說明如何在基類中宣告新的虛擬方法 `function1` ，以及如何在衍生類別中覆寫它。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>建構函式和繼承

基類的函式必須在衍生類別中呼叫。 基類（base class）的引數會出現在子句的引數清單中 `inherit` 。 使用的值必須取決於提供給衍生類別的引數。

下列程式碼顯示基類和衍生類別，其中衍生類別會在繼承子句中呼叫基類的函式：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

在多個函式的情況下，可以使用下列程式碼。 衍生類別的第一行是 `inherit` 子句，而這些欄位會顯示為使用關鍵字宣告的明確欄位 `val` 。 如需詳細資訊，請參閱 [明確欄位： `val` 關鍵字](./members/explicit-fields-the-val-keyword.md)。

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

## <a name="alternatives-to-inheritance"></a>繼承的替代方案

在需要稍微修改類型的情況下，請考慮使用物件運算式作為繼承的替代方法。 下列範例說明如何使用物件運算式做為建立新衍生型別的替代方法：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

如需物件運算式的詳細資訊，請參閱 [物件運算式](object-expressions.md)。

當您建立物件階層時，請考慮使用差異聯集，而不是繼承。 差異聯集也可以針對共用通用整體類型的不同物件，建立各種不同的行為模型。 單一差異聯集通常可以免除一些不同的衍生類別需求。 如需差異聯集的詳細資訊，請參閱 [區分](discriminated-unions.md)聯集。

## <a name="see-also"></a>另請參閱

- [物件運算式](object-expressions.md)
- [F # 語言參考](index.md)
