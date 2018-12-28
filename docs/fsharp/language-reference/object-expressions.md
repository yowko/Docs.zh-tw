---
title: 物件運算式
description: 了解如何使用F#物件運算式，當您想要避免額外的程式碼和額外負荷才能建立新的具名型別。
ms.date: 05/16/2016
ms.openlocfilehash: cb15983543fde2459c589b3de2554575d73db686
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613917"
---
# <a name="object-expressions"></a><span data-ttu-id="21ac2-103">物件運算式</span><span class="sxs-lookup"><span data-stu-id="21ac2-103">Object Expressions</span></span>

<span data-ttu-id="21ac2-104">*物件運算式*是建立以動態方式建立、 匿名物件類型的新執行個體的運算式為基礎的現有基底型別、 介面或介面的集合。</span><span class="sxs-lookup"><span data-stu-id="21ac2-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="21ac2-105">語法</span><span class="sxs-lookup"><span data-stu-id="21ac2-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="21ac2-106">備註</span><span class="sxs-lookup"><span data-stu-id="21ac2-106">Remarks</span></span>

<span data-ttu-id="21ac2-107">在先前的語法*typename*代表現有的類別類型或介面型別。</span><span class="sxs-lookup"><span data-stu-id="21ac2-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="21ac2-108">*類型-params*描述的選擇性的泛型類型參數。</span><span class="sxs-lookup"><span data-stu-id="21ac2-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="21ac2-109">*引數*僅用於需要建構函式參數的類別類型。</span><span class="sxs-lookup"><span data-stu-id="21ac2-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="21ac2-110">*成員定義*覆寫基底類別方法，或從基底類別或介面的抽象方法的實作。</span><span class="sxs-lookup"><span data-stu-id="21ac2-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="21ac2-111">下列範例會說明許多不同類型的物件運算式。</span><span class="sxs-lookup"><span data-stu-id="21ac2-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="21ac2-112">使用物件運算式</span><span class="sxs-lookup"><span data-stu-id="21ac2-112">Using Object Expressions</span></span>

<span data-ttu-id="21ac2-113">當您想要避免額外的程式碼，才能建立新的具名類型的額外負荷時，您可以使用物件運算式。</span><span class="sxs-lookup"><span data-stu-id="21ac2-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="21ac2-114">如果您使用物件運算式在程式中建立的類型數目降到最低時，您可以減少程式碼行的數目，並避免不必要的激增的型別。</span><span class="sxs-lookup"><span data-stu-id="21ac2-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="21ac2-115">不需要建立許多類型只可處理特定的情況下，您可以使用自訂現有的型別或手邊的特定案例提供適當的介面實作的物件運算式。</span><span class="sxs-lookup"><span data-stu-id="21ac2-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="21ac2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21ac2-116">See also</span></span>

- [<span data-ttu-id="21ac2-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="21ac2-117">F# Language Reference</span></span>](index.md)