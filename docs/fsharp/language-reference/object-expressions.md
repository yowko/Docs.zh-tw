---
title: "物件運算式 (F#)"
description: "了解如何使用 F # 物件運算式，當您想要避免額外的程式碼並建立新的所需的額外負荷具名型別。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c6dcf4c9-e7fd-4eee-9e4e-1176f4c27f57
ms.openlocfilehash: 28660d430473de02a8a55e37a26609827b364012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="object-expressions"></a><span data-ttu-id="b6515-104">物件運算式</span><span class="sxs-lookup"><span data-stu-id="b6515-104">Object Expressions</span></span>

<span data-ttu-id="b6515-105">*物件運算式*是建立動態建立的匿名物件類型的新執行個體的運算式為基礎的現有基底類型、 介面或介面的集合。</span><span class="sxs-lookup"><span data-stu-id="b6515-105">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="b6515-106">語法</span><span class="sxs-lookup"><span data-stu-id="b6515-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b6515-107">備註</span><span class="sxs-lookup"><span data-stu-id="b6515-107">Remarks</span></span>
<span data-ttu-id="b6515-108">在先前的語法， *typename*代表現有的類別類型或介面類型。</span><span class="sxs-lookup"><span data-stu-id="b6515-108">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="b6515-109">*型別參數*描述選擇性的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="b6515-109">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="b6515-110">*引數*只能用於類別類型，需要建構函式的參數。</span><span class="sxs-lookup"><span data-stu-id="b6515-110">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="b6515-111">*成員定義*基底類別方法的覆寫或實作抽象基底類別或介面的方法。</span><span class="sxs-lookup"><span data-stu-id="b6515-111">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="b6515-112">下列範例會說明許多不同類型的物件運算式。</span><span class="sxs-lookup"><span data-stu-id="b6515-112">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="b6515-113">使用物件運算式</span><span class="sxs-lookup"><span data-stu-id="b6515-113">Using Object Expressions</span></span>
<span data-ttu-id="b6515-114">當您想要避免額外的程式碼，才能建立新的具名類型的額外負荷時，您可以使用物件運算式。</span><span class="sxs-lookup"><span data-stu-id="b6515-114">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="b6515-115">如果您使用物件運算式在程式中建立型別的數目降至最低，您可以減少程式碼行的數目，並避免不必要的型別激增。</span><span class="sxs-lookup"><span data-stu-id="b6515-115">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="b6515-116">而不是建立許多類型，只是為了處理特定的情況下，您可以使用物件運算式，可自訂現有的類型，或提供特定的大小寫的適當實作的介面。</span><span class="sxs-lookup"><span data-stu-id="b6515-116">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="b6515-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6515-117">See Also</span></span>
[<span data-ttu-id="b6515-118">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="b6515-118">F# Language Reference</span></span>](index.md)
