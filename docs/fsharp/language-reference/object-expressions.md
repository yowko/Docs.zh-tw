---
title: 物件運算式
description: 了解如何使用F#物件運算式，當您想要避免額外的程式碼和額外負荷才能建立新的具名型別。
ms.date: 02/08/2019
ms.openlocfilehash: 63f2c1d7128721b7b8c744e4cf02d73c2a8b4a07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157843"
---
# <a name="object-expressions"></a>物件運算式

*物件運算式*是建立以動態方式建立、 匿名物件類型的新執行個體的運算式為基礎的現有基底型別、 介面或介面的集合。

## <a name="syntax"></a>語法

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>備註

在先前的語法*typename*代表現有的類別類型或介面型別。 *類型-params*描述的選擇性的泛型類型參數。 *引數*僅用於需要建構函式參數的類別類型。 *成員定義*覆寫基底類別方法，或從基底類別或介面的抽象方法的實作。

下列範例會說明許多不同類型的物件運算式。

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn "%A" obj1

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a>使用物件運算式

當您想要避免額外的程式碼，才能建立新的具名類型的額外負荷時，您可以使用物件運算式。 如果您使用物件運算式在程式中建立的類型數目降到最低時，您可以減少程式碼行的數目，並避免不必要的激增的型別。 不需要建立許多類型只可處理特定的情況下，您可以使用自訂現有的型別或手邊的特定案例提供適當的介面實作的物件運算式。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
