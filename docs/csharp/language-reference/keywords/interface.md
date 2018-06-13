---
title: interface (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 0320b1e287f8c7a3eb7751b68b40120f74e8f61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266538"
---
# <a name="interface-c-reference"></a><span data-ttu-id="35d6f-102">interface (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="35d6f-102">interface (C# Reference)</span></span>
<span data-ttu-id="35d6f-103">介面只會包含[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)、[事件](../../../csharp/programming-guide/events/index.md)或[索引子](../../../csharp/programming-guide/indexers/index.md)的簽章。</span><span class="sxs-lookup"><span data-stu-id="35d6f-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="35d6f-104">實作介面的類別或結構必須實作在介面定義中指定的介面成員。</span><span class="sxs-lookup"><span data-stu-id="35d6f-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="35d6f-105">在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="35d6f-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="35d6f-106">如需詳細資訊與範例，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="35d6f-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35d6f-107">範例</span><span class="sxs-lookup"><span data-stu-id="35d6f-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="35d6f-108">介面可以是命名空間或類別的成員，而且可以包含下列成員的簽章：</span><span class="sxs-lookup"><span data-stu-id="35d6f-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="35d6f-109">方法</span><span class="sxs-lookup"><span data-stu-id="35d6f-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="35d6f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="35d6f-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="35d6f-111">索引子</span><span class="sxs-lookup"><span data-stu-id="35d6f-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="35d6f-112">事件</span><span class="sxs-lookup"><span data-stu-id="35d6f-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="35d6f-113">介面可以繼承一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="35d6f-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="35d6f-114">當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。</span><span class="sxs-lookup"><span data-stu-id="35d6f-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="35d6f-115">實作介面的類別能夠明確實作該介面的成員。</span><span class="sxs-lookup"><span data-stu-id="35d6f-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="35d6f-116">明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。</span><span class="sxs-lookup"><span data-stu-id="35d6f-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="35d6f-117">如需明確介面實作的詳細資訊和程式碼範例，請參閱[明確介面實作](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="35d6f-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35d6f-118">範例</span><span class="sxs-lookup"><span data-stu-id="35d6f-118">Example</span></span>  
 <span data-ttu-id="35d6f-119">下列範例示範介面實作。</span><span class="sxs-lookup"><span data-stu-id="35d6f-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="35d6f-120">在此範例中，介面包含屬性宣告，而類別包含實作。</span><span class="sxs-lookup"><span data-stu-id="35d6f-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="35d6f-121">實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。</span><span class="sxs-lookup"><span data-stu-id="35d6f-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="35d6f-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="35d6f-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35d6f-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="35d6f-123">See Also</span></span>  
 [<span data-ttu-id="35d6f-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="35d6f-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="35d6f-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="35d6f-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="35d6f-126">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="35d6f-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="35d6f-127">參考型別</span><span class="sxs-lookup"><span data-stu-id="35d6f-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="35d6f-128">介面</span><span class="sxs-lookup"><span data-stu-id="35d6f-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="35d6f-129">使用屬性</span><span class="sxs-lookup"><span data-stu-id="35d6f-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="35d6f-130">使用索引子</span><span class="sxs-lookup"><span data-stu-id="35d6f-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="35d6f-131">class</span><span class="sxs-lookup"><span data-stu-id="35d6f-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="35d6f-132">struct</span><span class="sxs-lookup"><span data-stu-id="35d6f-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="35d6f-133">介面</span><span class="sxs-lookup"><span data-stu-id="35d6f-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
