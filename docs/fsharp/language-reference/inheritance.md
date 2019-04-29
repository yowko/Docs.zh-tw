---
title: 繼承
description: 了解如何指定F#使用 'inherit' 關鍵字的繼承關聯性。
ms.date: 05/16/2016
ms.openlocfilehash: 775ee52039caf4c4ab65f82fa21d4e536135a12a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937458"
---
# <a name="inheritance"></a>繼承

使用繼承來建立模型的 「 是 」 關聯性，或子型別，在物件導向程式設計中。

## <a name="specifying-inheritance-relationships"></a>指定的繼承關聯性

使用指定繼承關聯性`inherit`類別宣告中的關鍵字。 基本的語法形式是由下列範例所示。

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

一個類別可以有最多一個基底類別。 如果您未指定基底類別使用`inherit`關鍵字，類別會隱含地繼承自`System.Object`。

## <a name="inherited-members"></a>繼承的成員

如果類別繼承自另一個類別，方法和基底類別成員可用於衍生類別的使用者，就像是在衍生類別的直接成員一樣。

任何的 let 繫結和建構函式參數都是私用的類別，因此，無法從衍生類別存取。

關鍵字`base`隨附在衍生類別中，參考的基底類別的執行個體。 它當成自我識別項。

## <a name="virtual-methods-and-overrides"></a>虛擬方法和覆寫

虛擬方法 （和屬性） 運作方式稍有不同的F#相較於其他.NET 語言。 若要宣告新的虛擬成員，您使用`abstract`關鍵字。 要這麼做，不論您是否提供該方法的預設實作。 因此基底類別中的虛擬方法的完整定義會遵循下列模式：

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

然後，在衍生類別中，此虛擬方法的覆寫會遵循此模式：

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

如果您省略基底類別中的預設實作，基底類別變成抽象類別。

下列程式碼範例說明新的虛擬方法的宣告`function1`基底類別，以及如何在衍生類別中覆寫它。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>建構函式和繼承

在衍生類別中，就必須呼叫基底類別的建構函式。 基底類別建構函式的引數出現在引數清單中`inherit`子句。 從衍生的類別建構函式所提供的引數，必須決定所使用的值。

下列程式碼顯示基底類別和衍生的類別，衍生的類別繼承子句中呼叫基底類別建構函式的位置：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

在多個建構函式的情況下可以使用下列程式碼。 在衍生的類別建構函式的第一行會`inherit`子句和欄位會顯示為使用宣告的明確欄位`val`關鍵字。 如需詳細資訊，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。

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

在需要稍微修改的型別所在的情況下，請考慮使用替代繼承的物件運算式。 下列範例說明如何使用的物件運算式，以建立新的衍生的類型的替代方案：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

如需有關物件運算式的詳細資訊，請參閱[物件運算式](object-expressions.md)。

當您建立的物件階層架構時，請考慮使用已區分的聯集而非繼承。 差別等位也各不相同的模型行為的不同共用常見的整體類型的物件。 單一的已區分聯集可以通常不需要是彼此的微小差異的衍生類別的數字。 差別聯集的相關資訊，請參閱[差別聯集](discriminated-unions.md)。

## <a name="see-also"></a>另請參閱

- [物件運算式](object-expressions.md)
- [F# 語言參考](index.md)