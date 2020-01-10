---
title: 在類別和結構之間選擇
ms.date: 10/22/2008
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
ms.openlocfilehash: 34ab2589364e244fed1c64c1703205fb4b0832e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709513"
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="7f309-102">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="7f309-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="7f309-103">每個架構設計工具所面臨的基本設計決策之一，是要將型別設計為類別（參考型別）還是結構（實值型別）。</span><span class="sxs-lookup"><span data-stu-id="7f309-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="7f309-104">瞭解參考型別和實值型別的行為差異，對於進行這項選擇十分重要。</span><span class="sxs-lookup"><span data-stu-id="7f309-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="7f309-105">參考型別和實值型別之間的第一個差異在於，參考型別會在堆積上配置並進行垃圾收集，而實值型別則會在堆疊上配置，或在包含型別中內嵌，而在堆疊中則會解除配置。回溯或其包含類型解除配置時。</span><span class="sxs-lookup"><span data-stu-id="7f309-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="7f309-106">因此，實數值型別的配置和取消配置，通常比參考類型的配置和取消配置來得便宜。</span><span class="sxs-lookup"><span data-stu-id="7f309-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="7f309-107">接下來，參考型別的陣列是配置的，這表示陣列元素只是在堆積上之參考型別實例的參考。</span><span class="sxs-lookup"><span data-stu-id="7f309-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="7f309-108">實值型別陣列是以內嵌方式配置，這表示陣列元素是實值型別的實際實例。</span><span class="sxs-lookup"><span data-stu-id="7f309-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="7f309-109">因此，實數值型別陣列的配置和取消配置，比參考類型陣列的配置和取消配置更便宜。</span><span class="sxs-lookup"><span data-stu-id="7f309-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="7f309-110">此外，在大部分的情況下，實數值型別陣列表現出更好的參考位置。</span><span class="sxs-lookup"><span data-stu-id="7f309-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="7f309-111">下一個差異與記憶體使用量有關。</span><span class="sxs-lookup"><span data-stu-id="7f309-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="7f309-112">轉換成參考型別或其所實的其中一個介面時，實數值型別會得到裝箱。</span><span class="sxs-lookup"><span data-stu-id="7f309-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="7f309-113">當轉換回實值型別時，它們會被取消裝箱。</span><span class="sxs-lookup"><span data-stu-id="7f309-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="7f309-114">因為 box 是在堆積上配置的物件，而且會進行垃圾收集，所乙太多的裝箱和取消裝箱可能會對堆積、垃圾收集行程和最終應用程式效能產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="7f309-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="7f309-115">相反地，在參考型別轉換時，不會發生這類的裝箱。</span><span class="sxs-lookup"><span data-stu-id="7f309-115">In contrast, no such boxing occurs as reference types are cast.</span></span> <span data-ttu-id="7f309-116">（如需詳細資訊，請參閱[裝箱和取消裝箱](../../csharp/programming-guide/types/boxing-and-unboxing.md)）。</span><span class="sxs-lookup"><span data-stu-id="7f309-116">(For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)).</span></span>
  
 <span data-ttu-id="7f309-117">接下來，參考型別指派會複製參考，而實值型別指派則會複製整個值。</span><span class="sxs-lookup"><span data-stu-id="7f309-117">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="7f309-118">因此，大型參考型別的指派比大型實值型別的指派便宜。</span><span class="sxs-lookup"><span data-stu-id="7f309-118">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="7f309-119">最後，參考型別會以傳址方式傳遞，而實值型別則會以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="7f309-119">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="7f309-120">對參考型別的實例所做的變更會影響指向該實例的所有參考。</span><span class="sxs-lookup"><span data-stu-id="7f309-120">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="7f309-121">數值型別實例會在以傳值方式傳遞時複製。</span><span class="sxs-lookup"><span data-stu-id="7f309-121">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="7f309-122">當實值型別的實例變更時，當然不會影響它的任何複本。</span><span class="sxs-lookup"><span data-stu-id="7f309-122">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="7f309-123">由於複本不是由使用者明確建立，而是在傳遞引數或傳回值時以隱含方式建立，因此可以變更的實數值型別可能會讓許多使用者感到困惑。</span><span class="sxs-lookup"><span data-stu-id="7f309-123">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="7f309-124">因此，實數值型別應該是不可變的。</span><span class="sxs-lookup"><span data-stu-id="7f309-124">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="7f309-125">根據經驗法則，架構中的大部分類型都應該是類別。</span><span class="sxs-lookup"><span data-stu-id="7f309-125">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="7f309-126">不過，在某些情況下，實數值型別的特性會使其更適合使用結構。</span><span class="sxs-lookup"><span data-stu-id="7f309-126">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="7f309-127">如果類型的實例很小，而且通常很短，或通常內嵌于其他物件中，則**✓會考慮**定義結構，而不是類別。</span><span class="sxs-lookup"><span data-stu-id="7f309-127">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="7f309-128">**X**除非類型具有下列所有特性，否則請避免定義結構：</span><span class="sxs-lookup"><span data-stu-id="7f309-128">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
- <span data-ttu-id="7f309-129">它會以邏輯方式表示單一值，類似于基本類型（`int`、`double`等）。</span><span class="sxs-lookup"><span data-stu-id="7f309-129">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
- <span data-ttu-id="7f309-130">其實例大小低於16個位元組。</span><span class="sxs-lookup"><span data-stu-id="7f309-130">It has an instance size under 16 bytes.</span></span>  
  
- <span data-ttu-id="7f309-131">它是不可變的。</span><span class="sxs-lookup"><span data-stu-id="7f309-131">It is immutable.</span></span>  
  
- <span data-ttu-id="7f309-132">不需要經常進行裝箱。</span><span class="sxs-lookup"><span data-stu-id="7f309-132">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="7f309-133">在所有其他情況下，您應該將類型定義為類別。</span><span class="sxs-lookup"><span data-stu-id="7f309-133">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="7f309-134">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="7f309-134">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7f309-135">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="7f309-135">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f309-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f309-136">See also</span></span>

- [<span data-ttu-id="7f309-137">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="7f309-137">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="7f309-138">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="7f309-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
