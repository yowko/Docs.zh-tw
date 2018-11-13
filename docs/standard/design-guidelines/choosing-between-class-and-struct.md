---
title: 在類別和結構之間選擇
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7590d5628f4951a8c7c2199f0e954007ed9fa962
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "50757422"
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="e2ccc-102">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="e2ccc-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="e2ccc-103">每個 framework 設計工具所面臨的基本設計決策之一是設計為型別，做為類別 （參考型別） 或結構 （實值型別）。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="e2ccc-104">深入了解的參考型別和實值類型的行為差異是非常重要的做此選擇。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="e2ccc-105">第一個參考型別和實值型別是參考型別在堆積上配置和回收，則實值型別會配置在堆疊上，或包含內嵌類型，並解除配置時，我們會考慮之間的差異堆疊回溯時或當其包含的型別取得已取消配置。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="e2ccc-106">因此，實值類型的配置和解除會比參考類型的配置和解除便宜的一般。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="e2ccc-107">接下來，參考類型的陣列配置外行，這表示的陣列項目是只在堆積上的參考類型的執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="e2ccc-108">值型別陣列的配置是內嵌，這表示陣列項目實值型別的實際的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="e2ccc-109">因此，值型別陣列的配置和解除會比參考型別陣列的配置和解除成本更低。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="e2ccc-110">此外，在大多數情況下值型別陣列顯現出更好的參考位置。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="e2ccc-111">下一項差異被與記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="e2ccc-112">取得 boxed 實值型別，當轉換成參考型別或其中一個所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="e2ccc-113">他們會收到 unboxed 時轉換回實值型別。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="e2ccc-114">因為方塊是在堆積上配置，而且會回收，太多 boxing 和 unboxing 的物件可以有堆積、 記憶體回收行程，以及最終的應用程式效能的負面影響。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="e2ccc-115">相反地，當參考型別會轉換，就會不發生任何這類 boxing。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-115">In contrast, no such boxing occurs as reference types are cast.</span></span> <span data-ttu-id="e2ccc-116">(如需詳細資訊，請參閱 < [Boxing 和 Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md))。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-116">(For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)).</span></span>
  
 <span data-ttu-id="e2ccc-117">接下來，參考型別指派會複製參考，而值的型別指派會複製整個值。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-117">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="e2ccc-118">因此，大型的參考類型的指派成本較低的大型值型別指派比。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-118">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="e2ccc-119">最後，參考型別是傳址方式傳遞，而由值傳遞實值型別。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-119">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="e2ccc-120">參考類型的執行個體的變更會影響所有指向執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-120">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="e2ccc-121">依值傳遞時，會複製值型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-121">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="e2ccc-122">變更的實值型別執行個體時，它當然不會影響任何其複本。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-122">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="e2ccc-123">因為複本不由使用者明確建立，但隱含建立引數會傳遞或傳回值傳回時，可以變更的實值型別可以是許多使用者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-123">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="e2ccc-124">因此，實值型別應該是不可變的。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-124">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="e2ccc-125">根據經驗法則，大部分的架構中的類型應該是類別。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-125">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="e2ccc-126">有，不過，某些情況中實值類型的特性讓它更適合使用結構。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-126">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="e2ccc-127">**✓ CONSIDER** 定義而不是類別結構，如果執行個體類型的小，通常存留較短或嵌入其他物件。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-127">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="e2ccc-128">**X AVOID** 定義結構，除非該類型具有所有下列特性：</span><span class="sxs-lookup"><span data-stu-id="e2ccc-128">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
-   <span data-ttu-id="e2ccc-129">它以邏輯方式表示的單一值，類似於基本型別 (`int`， `double`，依此類推。)。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-129">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
-   <span data-ttu-id="e2ccc-130">它具有執行個體大小小於 16 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-130">It has an instance size under 16 bytes.</span></span>  
  
-   <span data-ttu-id="e2ccc-131">它永遠不變。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-131">It is immutable.</span></span>  
  
-   <span data-ttu-id="e2ccc-132">它不會經常 boxed。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-132">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="e2ccc-133">在其他情況下，您應該做為類別定義您的型別。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-133">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="e2ccc-134">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="e2ccc-134">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e2ccc-135">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="e2ccc-135">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ccc-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2ccc-136">See also</span></span>

- [<span data-ttu-id="e2ccc-137">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="e2ccc-137">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="e2ccc-138">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="e2ccc-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
