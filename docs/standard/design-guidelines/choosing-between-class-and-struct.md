---
title: "在類別和結構之間選擇"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6659853e9c410ece3233cfa630c9066303a871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="6f529-102">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="6f529-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="6f529-103">其中每個架構設計師所面臨的基本設計決策在於要設計的類型 （參考型別） 的類別或結構 （實值類型）。</span><span class="sxs-lookup"><span data-stu-id="6f529-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="6f529-104">充分了解的參考類型和實值類型的行為差異是在選擇非常重要的。</span><span class="sxs-lookup"><span data-stu-id="6f529-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="6f529-105">第一個參考類型和實值類型是參考型別是在堆積上配置和記憶體回收，而實值類型會配置在堆疊上，或在包含內嵌類型，並取消配置時，我們會考慮之間的差異堆疊回溯或當其包含的型別取得已取消配置。</span><span class="sxs-lookup"><span data-stu-id="6f529-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="6f529-106">因此，實值類型的配置和解除是參考類型的配置和解除比廉價的一般。</span><span class="sxs-lookup"><span data-stu-id="6f529-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="6f529-107">接下來，陣列的參考型別會配置超出行，這表示的陣列項目是只是在堆積上的參考類型的執行個體參考。</span><span class="sxs-lookup"><span data-stu-id="6f529-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="6f529-108">值類型陣列的配置是內嵌，表示陣列元素為實值類型的實際執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f529-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="6f529-109">因此，值類型陣列的配置和解除會比參考型別陣列的配置和解除成本更低。</span><span class="sxs-lookup"><span data-stu-id="6f529-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="6f529-110">此外，在大部分情況下的值型別陣列會呈現多參考位置較佳。</span><span class="sxs-lookup"><span data-stu-id="6f529-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="6f529-111">下一項差異被與記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="6f529-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="6f529-112">取得 boxed 實值類型，當轉型為參考類型或其中一個所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="6f529-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="6f529-113">他們取得 unboxed 時轉型為實值型別。</span><span class="sxs-lookup"><span data-stu-id="6f529-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="6f529-114">因為方塊是在堆積上配置和記憶體回收、 過度 boxing 和 unboxing 是物件可以有堆積、 記憶體回收行程，以及最終的應用程式效能的負面影響。</span><span class="sxs-lookup"><span data-stu-id="6f529-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="6f529-115">相較之下，當參考類型會轉換，就會不發生任何這類 boxing。</span><span class="sxs-lookup"><span data-stu-id="6f529-115">In contrast, no such boxing occurs as reference types are cast.</span></span>  
  
 <span data-ttu-id="6f529-116">接下來，指派參考類型，將參考複製，而值的型別指派複製整個值。</span><span class="sxs-lookup"><span data-stu-id="6f529-116">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="6f529-117">因此，大型的參考類型的指派較低的大型值型別指派比。</span><span class="sxs-lookup"><span data-stu-id="6f529-117">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="6f529-118">最後，參考型別是傳址方式傳遞，而傳值方式傳遞的實值類型。</span><span class="sxs-lookup"><span data-stu-id="6f529-118">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="6f529-119">參考類型的執行個體的變更會影響所有指向執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="6f529-119">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="6f529-120">依值傳遞時，會複製值類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f529-120">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="6f529-121">當實值類型的執行個體變更時，當然不會影響任何其複本。</span><span class="sxs-lookup"><span data-stu-id="6f529-121">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="6f529-122">因為複本不由使用者明確建立，但會以隱含方式建立引數會傳遞或傳回值傳回時，可以變更的實值類型可以是許多使用者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="6f529-122">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="6f529-123">因此，實值型別應該是不變。</span><span class="sxs-lookup"><span data-stu-id="6f529-123">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="6f529-124">根據經驗法則，大部分的架構中的類型應該是類別。</span><span class="sxs-lookup"><span data-stu-id="6f529-124">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="6f529-125">有，不過，某些情況中的實值類型特性使得較適合使用結構。</span><span class="sxs-lookup"><span data-stu-id="6f529-125">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="6f529-126">**✓ 考慮**定義而不是類別結構，如果執行個體類型的小，通常存留較短或嵌入其他物件。</span><span class="sxs-lookup"><span data-stu-id="6f529-126">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="6f529-127">**請避免 x**定義結構，除非該類型具有所有下列特性：</span><span class="sxs-lookup"><span data-stu-id="6f529-127">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
-   <span data-ttu-id="6f529-128">它以邏輯方式表示的單一值，類似於基本類型 (`int`，`double`等。)。</span><span class="sxs-lookup"><span data-stu-id="6f529-128">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
-   <span data-ttu-id="6f529-129">它具有執行個體大小小於 16 個位元組。</span><span class="sxs-lookup"><span data-stu-id="6f529-129">It has an instance size under 16 bytes.</span></span>  
  
-   <span data-ttu-id="6f529-130">它永遠不變。</span><span class="sxs-lookup"><span data-stu-id="6f529-130">It is immutable.</span></span>  
  
-   <span data-ttu-id="6f529-131">它不會經常 boxed 處理。</span><span class="sxs-lookup"><span data-stu-id="6f529-131">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="6f529-132">在其他情況下，您應該做為類別定義您的型別。</span><span class="sxs-lookup"><span data-stu-id="6f529-132">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="6f529-133">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="6f529-133">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6f529-134">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="6f529-134">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f529-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f529-135">See Also</span></span>  
 [<span data-ttu-id="6f529-136">型別設計指導方針</span><span class="sxs-lookup"><span data-stu-id="6f529-136">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="6f529-137">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="6f529-137">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
