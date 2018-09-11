---
title: 介面 (F#)
description: '了解 F # 介面指定一組相關的其他類別所實作的成員的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 6d7f8ee9ea17d2294933f88577c30a96975ae5d4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267267"
---
# <a name="interfaces"></a>介面

*介面*指定一組相關的其他類別所實作的成員。

## <a name="syntax"></a>語法

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>備註

介面宣告類似於類別宣告，不同之處在於會實作任何成員。 相反地，所有成員都是抽象類別，以關鍵字`abstract`。 您未提供方法主體的抽象方法。 不過，您可以在這裡提供的預設實作也包含的成員為方法，以搭配不同的定義`default`關鍵字。 如此一來就相當於其他.NET 語言中的基底類別中建立的虛擬方法就行了。 這種虛擬的方法可以實作介面的類別中被覆寫。

介面的預設存取範圍是`public`。

您可以選擇性地每個方法的名稱命名參數使用一般的 F # 語法：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

在上述`ISprintable`範例中，`Print`方法具有單一參數型別的`string`同名`format`。

若要實作介面的兩種方式： 使用物件運算式，以及使用類別類型。 在任一情況下，類別型別或物件運算式會提供介面的抽象方法的方法主體。 實作專屬於每個實作介面的類型。 因此，在不同類型的介面方法可能彼此不同。

關鍵字`interface`和`end`，其中標記的開始和結束的定義，是選擇性，當您使用輕量型語法。 如果您不使用這些關鍵字，編譯器會嘗試推斷型別是否類別或介面藉由分析您所使用的建構。 如果您定義的成員，或使用其他類別的語法，則會將類型解譯為類別。

開始以大寫的所有介面的.NET 程式碼樣式是`I`。

## <a name="implementing-interfaces-by-using-class-types"></a>使用類別類型實作介面

您也可以使用類別類型中實作一或多個介面`interface`關鍵字，此介面的名稱和`with`關鍵字，後面介面成員的定義，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

介面實作，會繼承，因此不需要重新實作其任何衍生的類別。

## <a name="calling-interface-methods"></a>呼叫介面方法

可以呼叫介面方法，只能透過的介面，不是透過實作介面之型別的任何物件。 因此，您可能必須向上轉型為介面型別使用`:>`運算子或`upcast`為了呼叫這些方法的運算子。

當您有型別的物件時呼叫介面方法`SomeClass`，您必須向上轉型為介面型別物件，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

替代方法是在物件上的向上轉型成為宣告方法，並呼叫介面方法，如下列範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>使用物件運算式實作介面

物件運算式提供簡短的方式實作介面。 當您不需要建立具名的類型，且您只需要支援介面方法，不需要任何其他方法的物件很有幫助。 物件運算式是以下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>介面繼承

介面可以繼承一或多個基底介面。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [物件運算式](object-expressions.md)
- [類別](classes.md)
