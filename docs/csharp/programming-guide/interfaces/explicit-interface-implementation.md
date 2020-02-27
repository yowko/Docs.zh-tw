---
title: 明確介面實作 - C# 程式設計指南
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628146"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="04b4d-102">明確介面實作 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="04b4d-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="04b4d-103">如果[類別](../../language-reference/keywords/class.md)實作兩個具有相同簽章成員的介面，則在類別上實作該成員會造成這兩個介面都使用該成員進行實作。</span><span class="sxs-lookup"><span data-stu-id="04b4d-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="04b4d-104">在下列範例中，所有對 `Paint` 的呼叫都會叫用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="04b4d-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="04b4d-105">第一個範例會定義類型：</span><span class="sxs-lookup"><span data-stu-id="04b4d-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="04b4d-106">下列範例會呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="04b4d-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="04b4d-107">當兩個介面成員未執行相同的函式時，會導致其中一個或兩個介面的實作為不正確。</span><span class="sxs-lookup"><span data-stu-id="04b4d-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="04b4d-108">您可以明確地實作為介面成員，建立只透過介面呼叫且專屬於該介面的類別成員。</span><span class="sxs-lookup"><span data-stu-id="04b4d-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="04b4d-109">將類別成員命名為介面的名稱和句點。</span><span class="sxs-lookup"><span data-stu-id="04b4d-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="04b4d-110">例如：</span><span class="sxs-lookup"><span data-stu-id="04b4d-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="04b4d-111">類別成員 `IControl.Paint` 只能透過 `IControl` 介面取得，`ISurface.Paint` 只能透過 `ISurface` 取得。</span><span class="sxs-lookup"><span data-stu-id="04b4d-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="04b4d-112">這兩種方法都是分開的，而且都無法直接在類別上使用。</span><span class="sxs-lookup"><span data-stu-id="04b4d-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="04b4d-113">例如：</span><span class="sxs-lookup"><span data-stu-id="04b4d-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="04b4d-114">明確的執行也可用來解決兩個介面各自宣告相同名稱的不同成員（例如屬性和方法）的情況。</span><span class="sxs-lookup"><span data-stu-id="04b4d-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="04b4d-115">若要同時執行這兩個介面，類別必須針對屬性 `P`或方法 `P`（或兩者）使用明確的執行，以避免編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="04b4d-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="04b4d-116">例如：</span><span class="sxs-lookup"><span data-stu-id="04b4d-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="04b4d-117">如果類別繼承介面的方法執行，則只能透過介面類別型的參考來存取該方法。</span><span class="sxs-lookup"><span data-stu-id="04b4d-117">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="04b4d-118">繼承的成員不會顯示為公用介面的一部分。</span><span class="sxs-lookup"><span data-stu-id="04b4d-118">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="04b4d-119">下列範例會定義介面方法的預設實值：</span><span class="sxs-lookup"><span data-stu-id="04b4d-119">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="04b4d-120">下列範例會叫用預設的實值：</span><span class="sxs-lookup"><span data-stu-id="04b4d-120">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="04b4d-121">任何實 `IControl` 介面的類別，都可以覆寫預設的 `Paint` 方法（做為公用方法），或做為明確介面的執行。</span><span class="sxs-lookup"><span data-stu-id="04b4d-121">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="04b4d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04b4d-122">See also</span></span>

- [<span data-ttu-id="04b4d-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="04b4d-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04b4d-124">類別和結構</span><span class="sxs-lookup"><span data-stu-id="04b4d-124">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="04b4d-125">介面</span><span class="sxs-lookup"><span data-stu-id="04b4d-125">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="04b4d-126">繼承</span><span class="sxs-lookup"><span data-stu-id="04b4d-126">Inheritance</span></span>](../classes-and-structs/inheritance.md)
