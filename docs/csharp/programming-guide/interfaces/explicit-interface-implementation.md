---
title: 明確介面實作 - C# 程式設計指南
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167669"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="2b740-102">明確介面實作 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2b740-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="2b740-103">如果[類別](../../language-reference/keywords/class.md)實作兩個具有相同簽章成員的介面，則在類別上實作該成員會造成這兩個介面都使用該成員進行實作。</span><span class="sxs-lookup"><span data-stu-id="2b740-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="2b740-104">在下列範例中，所有對 `Paint` 的呼叫都會叫用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="2b740-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="2b740-105">第一個示例定義類型：</span><span class="sxs-lookup"><span data-stu-id="2b740-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="2b740-106">以下示例調用這些方法：</span><span class="sxs-lookup"><span data-stu-id="2b740-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="2b740-107">當兩個介面成員不執行相同的函數時，它會導致一個或兩個介面的實現不正確。</span><span class="sxs-lookup"><span data-stu-id="2b740-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="2b740-108">可以顯式實現介面成員 — 創建僅通過介面調用且特定于該介面的類成員。</span><span class="sxs-lookup"><span data-stu-id="2b740-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="2b740-109">使用介面和句點的名稱命名類成員。</span><span class="sxs-lookup"><span data-stu-id="2b740-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="2b740-110">例如：</span><span class="sxs-lookup"><span data-stu-id="2b740-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="2b740-111">類別成員 `IControl.Paint` 只能透過 `IControl` 介面取得，`ISurface.Paint` 只能透過 `ISurface` 取得。</span><span class="sxs-lookup"><span data-stu-id="2b740-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="2b740-112">兩個方法實現都是獨立的，並且兩者都沒有直接在類上可用。</span><span class="sxs-lookup"><span data-stu-id="2b740-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="2b740-113">例如：</span><span class="sxs-lookup"><span data-stu-id="2b740-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="2b740-114">顯式實現還用於解決兩個介面都聲明相同名稱的不同成員（如屬性和方法）的情況。</span><span class="sxs-lookup"><span data-stu-id="2b740-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="2b740-115">要實現這兩個介面，類必須對屬性`P`、方法`P`或兩者使用顯式實現，以避免編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b740-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="2b740-116">例如：</span><span class="sxs-lookup"><span data-stu-id="2b740-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="2b740-117">從[C# 8.0](../../whats-new/csharp-8.md#default-interface-methods)開始，可以為在介面中聲明的成員定義實現。</span><span class="sxs-lookup"><span data-stu-id="2b740-117">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="2b740-118">如果類從介面繼承方法實現，則只能通過介面類別型的引用訪問該方法。</span><span class="sxs-lookup"><span data-stu-id="2b740-118">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="2b740-119">繼承的成員不顯示為公共介面的一部分。</span><span class="sxs-lookup"><span data-stu-id="2b740-119">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="2b740-120">以下示例定義介面方法的預設實現：</span><span class="sxs-lookup"><span data-stu-id="2b740-120">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="2b740-121">以下示例調用預設實現：</span><span class="sxs-lookup"><span data-stu-id="2b740-121">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="2b740-122">實現`IControl`介面的任何類都可以重寫預設`Paint`方法，也可以作為公共方法重寫，也可以作為明確介面實作重寫。</span><span class="sxs-lookup"><span data-stu-id="2b740-122">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b740-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b740-123">See also</span></span>

- [<span data-ttu-id="2b740-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2b740-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2b740-125">類別和結構</span><span class="sxs-lookup"><span data-stu-id="2b740-125">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="2b740-126">介面</span><span class="sxs-lookup"><span data-stu-id="2b740-126">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="2b740-127">繼承</span><span class="sxs-lookup"><span data-stu-id="2b740-127">Inheritance</span></span>](../classes-and-structs/inheritance.md)
