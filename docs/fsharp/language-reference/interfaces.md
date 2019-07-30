---
title: 介面
description: 瞭解介面F#如何指定其他類別所要執行的相關成員集合。
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627644"
---
# <a name="interfaces"></a>介面

*介面*會指定其他類別所要執行的相關成員集合。

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

介面宣告類似于類別宣告, 不同之處在于不會執行任何成員。 相反地, 所有成員都是抽象的, 如關鍵字`abstract`所指示。 您未提供抽象方法的方法主體。 不過, 您也可以提供預設的執行方式, 方法是同時包含成員的個別定義做為方法, `default`並搭配關鍵字。 這麼做相當於在其他 .NET 語言的基類中建立虛擬方法。 這類虛擬方法可以在實介面的類別中覆寫。

介面的預設存取範圍是`public`。

您可以使用一般F#語法, 選擇性地提供每個方法參數的名稱:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

在上述`ISprintable`範例中`Print` , 方法具有名稱`format`為之類型`string`的單一參數。

有兩種方式可以執行介面: 藉由使用物件運算式, 以及使用類別類型。 在任一情況下, 類別類型或物件運算式都會針對介面的抽象方法提供方法主體。 針對每個實作為介面的型別, 都是專用的。 因此, 不同類型上的介面方法可能會彼此不同。

當您`interface`使用`end`輕量語法時, 關鍵字和 (用來標示定義的開始和結束) 是選擇性的。 如果您未使用這些關鍵字, 編譯器會藉由分析您所使用的結構, 嘗試推斷該類型是類別或介面。 如果您定義成員或使用其他類別語法, 則會將類型視為類別。

.NET 程式碼樣式是用來開始所有具有資本`I`的介面。

## <a name="implementing-interfaces-by-using-class-types"></a>使用類別類型來執行介面

您可以使用`interface`關鍵字、介面的名稱`with`和關鍵字 (後面接著介面成員定義) 來執行類別類型中的一或多個介面, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

系統會繼承介面實作為, 因此任何衍生的類別都不需要加以重新執行。

## <a name="calling-interface-methods"></a>呼叫介面方法

介面方法只能透過介面呼叫, 而不能透過實作為介面之型別的任何物件。 因此, 您可能必須使用`:>`運算子`upcast`或運算子來向上轉換成介面類別型, 才能呼叫這些方法。

若要在具有類型`SomeClass`的物件時呼叫介面方法, 您必須將物件向上轉型為介面類別型, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

另一個替代方式是在 upcasts 和呼叫介面方法的物件上宣告方法, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>使用物件運算式來執行介面

物件運算式提供了簡單的方法來執行介面。 當您不需要建立命名類型, 而且只想要支援介面方法的物件, 而不需要任何其他方法時, 它們會很有用。 下列程式碼說明物件運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>介面繼承

介面可以繼承自一或多個基底介面。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [物件運算式](object-expressions.md)
- [類別](classes.md)
