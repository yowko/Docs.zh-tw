---
title: 明確介面實作 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 498c45ff1c5837f5dcb0d4a80d0e3bb249abd694
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589227"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="813ec-102">明確介面實作 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="813ec-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="813ec-103">如果[類別](../../language-reference/keywords/class.md)實作兩個具有相同簽章成員的介面，則在類別上實作該成員會造成這兩個介面都使用該成員進行實作。</span><span class="sxs-lookup"><span data-stu-id="813ec-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="813ec-104">在下列範例中，所有對 `Paint` 的呼叫都會叫用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="813ec-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 <span data-ttu-id="813ec-105">但如果兩個[介面](../../language-reference/keywords/interface.md)成員不執行相同的函式，這可能會導致其中一或兩個介面實作不正確。</span><span class="sxs-lookup"><span data-stu-id="813ec-105">If the two [interface](../../language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="813ec-106">可能可以明確實作介面成員：建立只能透過介面呼叫且專屬於該介面的類別成員。</span><span class="sxs-lookup"><span data-stu-id="813ec-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="813ec-107">只要使用介面的名稱和句號命名類別成員，即可達成。</span><span class="sxs-lookup"><span data-stu-id="813ec-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="813ec-108">例如：</span><span class="sxs-lookup"><span data-stu-id="813ec-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 <span data-ttu-id="813ec-109">類別成員 `IControl.Paint` 只能透過 `IControl` 介面取得，`ISurface.Paint` 只能透過 `ISurface` 取得。</span><span class="sxs-lookup"><span data-stu-id="813ec-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="813ec-110">這兩種方法實作是分開的，都無法直接在類別上使用。</span><span class="sxs-lookup"><span data-stu-id="813ec-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="813ec-111">例如：</span><span class="sxs-lookup"><span data-stu-id="813ec-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 <span data-ttu-id="813ec-112">兩個介面各自宣告同名之不同成員的情況下，例如屬性和方法，也可以使用明確實作來解決：</span><span class="sxs-lookup"><span data-stu-id="813ec-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 <span data-ttu-id="813ec-113">若要實作這兩個介面，類別必須針對屬性 P 或方法 P 或兩者使用明確的實作，來避免編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="813ec-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="813ec-114">例如：</span><span class="sxs-lookup"><span data-stu-id="813ec-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a><span data-ttu-id="813ec-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="813ec-115">See also</span></span>

- [<span data-ttu-id="813ec-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="813ec-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="813ec-117">類別和結構</span><span class="sxs-lookup"><span data-stu-id="813ec-117">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="813ec-118">介面</span><span class="sxs-lookup"><span data-stu-id="813ec-118">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="813ec-119">繼承</span><span class="sxs-lookup"><span data-stu-id="813ec-119">Inheritance</span></span>](../classes-and-structs/inheritance.md)
