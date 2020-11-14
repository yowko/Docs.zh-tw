---
title: 介面
description: '瞭解 F # 介面如何指定其他類別所執行的相關成員集合。'
ms.date: 08/15/2020
ms.openlocfilehash: 0cef2932045dae401f5aa069107815543457ca4a
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557047"
---
# <a name="interfaces"></a>介面

*介面* 會指定其他類別所執行的相關成員集合。

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

介面宣告類似類別宣告，但不會執行任何成員。 相反地，所有成員都是抽象的，如關鍵字所指示 `abstract` 。 您未提供抽象方法的方法主體。 不過，您也可以提供預設的執行方式，也就是將個別的成員定義做為方法與 `default` 關鍵字一起使用。 這麼做相當於在其他 .NET 語言的基類中建立虛擬方法。 這類虛擬方法可以在執行介面的類別中覆寫。

介面的預設存取範圍是 `public` 。

您可以使用一般 F # 語法，選擇性地為每個方法參數指定名稱：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

在上述 `ISprintable` 範例中， `Print` 方法具有類型的單一參數，其名稱為 `string` `format` 。

有兩種方式可以執行介面：使用物件運算式，以及使用類別類型。 在任一種情況下，類別類型或物件運算式都會提供介面之抽象方法的方法主體。 實作為每個實作為介面的型別。 因此，不同類型的介面方法可能會彼此不同。

`interface` `end` 當您使用輕量語法時，關鍵字和（標示定義的開頭和結尾）是選擇性的。 如果您未使用這些關鍵字，編譯器會藉由分析您所使用的結構，嘗試推斷型別為類別或介面。 如果您定義成員或使用其他類別語法，則會將型別解釋為類別。

.NET 程式碼撰寫樣式是以大寫來開始所有的介面 `I` 。

您可以用兩種方式指定多個參數： F # 樣式和。NET 樣式。 這兩種方法都會針對 .NET 取用者進行編譯，但 F # 樣式會強制 F # 呼叫端使用 F # 樣式參數應用程式和。NET 樣式會強制 F # 呼叫端使用元組引數應用程式。

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a>使用類別類型來執行介面

您可以使用 `interface` 關鍵字、介面名稱和關鍵字，然後使用介面成員定義，在類別型別中執行一個或多個介面， `with` 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

介面會被繼承，因此任何衍生的類別都不需要重新執行它們。

## <a name="calling-interface-methods"></a>呼叫介面方法

介面方法只能透過介面呼叫，而不能透過任何實介面型別的物件來呼叫。 因此，您可能必須使用運算子或運算子來向上轉型為介面型別，才能 `:>` `upcast` 呼叫這些方法。

當您擁有類型的物件時，若要呼叫介面方法 `SomeClass` ，您必須將物件向上轉型為介面類別型，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

替代方法是在將和呼叫介面方法的物件上宣告方法，如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>使用物件運算式來執行介面

物件運算式提供簡單的方法來執行介面。 當您不需要建立已命名的型別，而且您只想要支援介面方法的物件，而不需要任何其他方法時，它們就很有用。 下列程式碼說明物件運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>介面繼承

介面可以繼承自一或多個基底介面。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a>使用預設實執行介面

C # 支援使用預設實作為定義介面，如下所示：

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

這些可直接從 F # 取用：

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

您可以使用覆寫的預設實值 `override` ，就像覆寫任何虛擬成員一樣。

沒有預設實值之介面中的任何成員仍必須明確地實作為。

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a>在不同的泛型具現化中執行相同的介面

F # 支援在不同的泛型具現化上執行相同的介面，如下所示：

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [物件運算式](object-expressions.md)
- [類別](classes.md)
