---
title: "interface (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- interface_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 126e674a2c56f04f54f35a011c24ebf0f713ee8d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="interface-c-reference"></a><span data-ttu-id="1dabc-102">interface (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1dabc-102">interface (C# Reference)</span></span>
<span data-ttu-id="1dabc-103">介面只會包含[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)、[事件](../../../csharp/programming-guide/events/index.md)或[索引子](../../../csharp/programming-guide/indexers/index.md)的簽章。</span><span class="sxs-lookup"><span data-stu-id="1dabc-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="1dabc-104">實作介面的類別或結構必須實作在介面定義中指定的介面成員。</span><span class="sxs-lookup"><span data-stu-id="1dabc-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="1dabc-105">在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="1dabc-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="1dabc-106">如需詳細資訊與範例，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1dabc-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dabc-107">範例</span><span class="sxs-lookup"><span data-stu-id="1dabc-107">Example</span></span>  
 <span data-ttu-id="1dabc-108">[!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1dabc-108">[!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]</span></span>  
  
 <span data-ttu-id="1dabc-109">介面可以是命名空間或類別的成員，而且可以包含下列成員的簽章：</span><span class="sxs-lookup"><span data-stu-id="1dabc-109">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="1dabc-110">方法</span><span class="sxs-lookup"><span data-stu-id="1dabc-110">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="1dabc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1dabc-111">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="1dabc-112">索引子</span><span class="sxs-lookup"><span data-stu-id="1dabc-112">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="1dabc-113">事件</span><span class="sxs-lookup"><span data-stu-id="1dabc-113">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="1dabc-114">介面可以繼承一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="1dabc-114">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="1dabc-115">當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。</span><span class="sxs-lookup"><span data-stu-id="1dabc-115">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="1dabc-116">實作介面的類別能夠明確實作該介面的成員。</span><span class="sxs-lookup"><span data-stu-id="1dabc-116">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="1dabc-117">明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。</span><span class="sxs-lookup"><span data-stu-id="1dabc-117">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="1dabc-118">如需明確介面實作的詳細資訊和程式碼範例，請參閱[明確介面實作](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="1dabc-118">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dabc-119">範例</span><span class="sxs-lookup"><span data-stu-id="1dabc-119">Example</span></span>  
 <span data-ttu-id="1dabc-120">下列範例示範介面實作。</span><span class="sxs-lookup"><span data-stu-id="1dabc-120">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="1dabc-121">在此範例中，介面包含屬性宣告，而類別包含實作。</span><span class="sxs-lookup"><span data-stu-id="1dabc-121">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="1dabc-122">實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。</span><span class="sxs-lookup"><span data-stu-id="1dabc-122">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 <span data-ttu-id="1dabc-123">[!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1dabc-123">[!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1dabc-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1dabc-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1dabc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dabc-125">See Also</span></span>  
 <span data-ttu-id="1dabc-126">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1dabc-127">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1dabc-128">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1dabc-129">[參考型別](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-129">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="1dabc-130">[介面](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-130">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 <span data-ttu-id="1dabc-131">[使用屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-131">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="1dabc-132">[使用索引子](../../../csharp/programming-guide/indexers/using-indexers.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-132">[Using Indexers](../../../csharp/programming-guide/indexers/using-indexers.md) </span></span>  
 <span data-ttu-id="1dabc-133">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-133">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="1dabc-134">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="1dabc-134">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="1dabc-135">介面</span><span class="sxs-lookup"><span data-stu-id="1dabc-135">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

