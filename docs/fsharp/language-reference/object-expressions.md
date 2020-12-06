---
title: 物件運算式
description: '當您想要避免建立新的、命名的型別所需的額外程式碼和額外負荷時，請瞭解如何使用 F # 物件運算式。'
ms.date: 02/08/2019
ms.openlocfilehash: 8a3e40b7833b551eefb95ec62b935acd1ba7b1f9
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740298"
---
# <a name="object-expressions"></a><span data-ttu-id="2e29e-103">物件運算式</span><span class="sxs-lookup"><span data-stu-id="2e29e-103">Object Expressions</span></span>

<span data-ttu-id="2e29e-104">*物件運算式* 是一個運算式，它會根據現有的基底類型、介面或介面集，建立動態建立之匿名物件類型的新實例。</span><span class="sxs-lookup"><span data-stu-id="2e29e-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e29e-105">語法</span><span class="sxs-lookup"><span data-stu-id="2e29e-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="2e29e-106">備註</span><span class="sxs-lookup"><span data-stu-id="2e29e-106">Remarks</span></span>

<span data-ttu-id="2e29e-107">在先前的語法中， *typename* 代表現有的類別型別或介面型別。</span><span class="sxs-lookup"><span data-stu-id="2e29e-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="2e29e-108">*類型* 參數描述選擇性的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="2e29e-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="2e29e-109">*引數* 只適用于需要使用函式參數的類別類型。</span><span class="sxs-lookup"><span data-stu-id="2e29e-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="2e29e-110">*成員定義* 是基類方法的覆寫，或是基類或介面的抽象方法的執行。</span><span class="sxs-lookup"><span data-stu-id="2e29e-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="2e29e-111">下列範例說明數種不同類型的物件運算式。</span><span class="sxs-lookup"><span data-stu-id="2e29e-111">The following example illustrates several different types of object expressions.</span></span>

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn $"{obj1}"

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

## <a name="using-object-expressions"></a><span data-ttu-id="2e29e-112">使用物件運算式</span><span class="sxs-lookup"><span data-stu-id="2e29e-112">Using Object Expressions</span></span>

<span data-ttu-id="2e29e-113">當您想要避免建立新的、命名的型別所需的額外程式碼和額外負荷時，請使用物件運算式。</span><span class="sxs-lookup"><span data-stu-id="2e29e-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="2e29e-114">如果您使用物件運算式將程式中所建立的類型數目降至最低，您可以減少程式碼的行數，並避免不必要的類型激增。</span><span class="sxs-lookup"><span data-stu-id="2e29e-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="2e29e-115">您可以使用物件運算式來自訂現有的型別，或為手邊的特定案例提供適當的介面執行，而不需建立許多型別來處理特定情況。</span><span class="sxs-lookup"><span data-stu-id="2e29e-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e29e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e29e-116">See also</span></span>

- [<span data-ttu-id="2e29e-117">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="2e29e-117">F# Language Reference</span></span>](index.md)
