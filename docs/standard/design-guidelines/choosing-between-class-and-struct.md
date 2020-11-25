---
title: 在類別和結構之間選擇
description: 瞭解如何決定是否要將類型設計為類別，或將型別設計為結構。 瞭解 .NET 中的參考型別和實數值型別有何不同。
ms.date: 10/22/2008
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
ms.openlocfilehash: 05ba9abbc9495d927b7f58ebb06f152c0c15772f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701246"
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="79db7-104">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="79db7-104">Choosing Between Class and Struct</span></span>

<span data-ttu-id="79db7-105">每個 framework 設計工具都有臉部的其中一個基本設計決策，就是要將類型設計為類別 (參考型別) 或作為結構 () 數值型別。</span><span class="sxs-lookup"><span data-stu-id="79db7-105">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="79db7-106">若要對參考型別和實值型別行為的差異有很大的瞭解，對進行這項選擇是很重要的。</span><span class="sxs-lookup"><span data-stu-id="79db7-106">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>

 <span data-ttu-id="79db7-107">參考型別和實值型別之間的第一個差異是，參考型別是在堆積上配置和垃圾收集，而實值型別則是在堆疊上配置，或是在堆疊回溯或其包含型別解除配置時解除配置。</span><span class="sxs-lookup"><span data-stu-id="79db7-107">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="79db7-108">因此，實值型別的配置和取消配置，通常比參考型別的配置和取消配置還便宜。</span><span class="sxs-lookup"><span data-stu-id="79db7-108">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>

 <span data-ttu-id="79db7-109">接下來，參考型別的陣列是在外配置的，這表示陣列元素只是參考型別（位於堆積上）的實例參考。</span><span class="sxs-lookup"><span data-stu-id="79db7-109">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="79db7-110">實值型別陣列是以內嵌方式配置，表示陣列元素是實值型別的實際實例。</span><span class="sxs-lookup"><span data-stu-id="79db7-110">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="79db7-111">因此，實值型別陣列的配置和取消配置比參考型別陣列的配置和取消配置更便宜。</span><span class="sxs-lookup"><span data-stu-id="79db7-111">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="79db7-112">此外，在大部分的情況下，實值型別陣列也展現了更好的參考位置。</span><span class="sxs-lookup"><span data-stu-id="79db7-112">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>

 <span data-ttu-id="79db7-113">下一項差異與記憶體使用量有關。</span><span class="sxs-lookup"><span data-stu-id="79db7-113">The next difference is related to memory usage.</span></span> <span data-ttu-id="79db7-114">當轉換成參考型別或它們所執行的其中一個介面時，實值型別會被裝箱。</span><span class="sxs-lookup"><span data-stu-id="79db7-114">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="79db7-115">當轉換回實值型別時，它們會被取消裝箱。</span><span class="sxs-lookup"><span data-stu-id="79db7-115">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="79db7-116">因為 box 是在堆積上配置的物件，而且會進行垃圾收集，所乙太多的裝箱和取消取消項對堆積、垃圾收集行程，以及最終的應用程式效能可能會有負面影響。</span><span class="sxs-lookup"><span data-stu-id="79db7-116">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="79db7-117">相反地，在轉換參考型別時，不會發生這類的裝箱。</span><span class="sxs-lookup"><span data-stu-id="79db7-117">In contrast, no such boxing occurs as reference types are cast.</span></span> <span data-ttu-id="79db7-118"> (需詳細資訊，請參閱) 的 [裝箱和取消](../../csharp/programming-guide/types/boxing-and-unboxing.md) 。</span><span class="sxs-lookup"><span data-stu-id="79db7-118">(For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)).</span></span>

 <span data-ttu-id="79db7-119">接下來，參考型別指派會複製參考，而實值型別指派則會複製整個值。</span><span class="sxs-lookup"><span data-stu-id="79db7-119">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="79db7-120">因此，大型參考型別的指派比大型實值型別的指派更便宜。</span><span class="sxs-lookup"><span data-stu-id="79db7-120">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>

 <span data-ttu-id="79db7-121">最後，參考型別會以傳址方式傳遞，而實值型別會以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="79db7-121">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="79db7-122">對參考型別的實例所做的變更會影響所有指向該實例的參考。</span><span class="sxs-lookup"><span data-stu-id="79db7-122">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="79db7-123">數值型別實例會在以傳值方式傳遞時複製。</span><span class="sxs-lookup"><span data-stu-id="79db7-123">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="79db7-124">當實值型別的實例變更時，當然不會影響它的任何複本。</span><span class="sxs-lookup"><span data-stu-id="79db7-124">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="79db7-125">由於系統不會明確地建立複本，而是在傳遞引數或傳回值時，隱含地建立複本，因此可以變更的實數值型別可能會讓許多使用者混淆。</span><span class="sxs-lookup"><span data-stu-id="79db7-125">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="79db7-126">因此，實數值型別應該是不可變的。</span><span class="sxs-lookup"><span data-stu-id="79db7-126">Therefore, value types should be immutable.</span></span>

 <span data-ttu-id="79db7-127">根據經驗法則，架構中的大部分類型都應該是類別。</span><span class="sxs-lookup"><span data-stu-id="79db7-127">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="79db7-128">不過，在某些情況下，實值型別的特性讓它更適合使用結構。</span><span class="sxs-lookup"><span data-stu-id="79db7-128">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>

 <span data-ttu-id="79db7-129">如果類型的實例很小且通常是存留期，或通常內嵌于其他物件中，✔️可考慮定義結構，而不是類別。</span><span class="sxs-lookup"><span data-stu-id="79db7-129">✔️ CONSIDER defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>

 <span data-ttu-id="79db7-130">❌ 除非類型具有下列所有特性，否則請避免定義結構：</span><span class="sxs-lookup"><span data-stu-id="79db7-130">❌ AVOID defining a struct unless the type has all of the following characteristics:</span></span>

- <span data-ttu-id="79db7-131">它會以邏輯方式表示單一值，類似于基本類型 (`int` 、等 `double` ) 。</span><span class="sxs-lookup"><span data-stu-id="79db7-131">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>

- <span data-ttu-id="79db7-132">它的實例大小低於16位元組。</span><span class="sxs-lookup"><span data-stu-id="79db7-132">It has an instance size under 16 bytes.</span></span>

- <span data-ttu-id="79db7-133">它是不可變的。</span><span class="sxs-lookup"><span data-stu-id="79db7-133">It is immutable.</span></span>

- <span data-ttu-id="79db7-134">不需要經常進行封裝。</span><span class="sxs-lookup"><span data-stu-id="79db7-134">It will not have to be boxed frequently.</span></span>

 <span data-ttu-id="79db7-135">在所有其他情況下，您應該將類型定義為類別。</span><span class="sxs-lookup"><span data-stu-id="79db7-135">In all other cases, you should define your types as classes.</span></span>

 <span data-ttu-id="79db7-136">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="79db7-136">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="79db7-137">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="79db7-137">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="79db7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79db7-138">See also</span></span>

- [<span data-ttu-id="79db7-139">型別設計方針</span><span class="sxs-lookup"><span data-stu-id="79db7-139">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="79db7-140">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="79db7-140">Framework Design Guidelines</span></span>](index.md)
