---
title: 建構函式設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d7ca279dc1626cd526910af93326280bcd8301d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575553"
---
# <a name="constructor-design"></a><span data-ttu-id="1d1d8-102">建構函式設計</span><span class="sxs-lookup"><span data-stu-id="1d1d8-102">Constructor Design</span></span>
<span data-ttu-id="1d1d8-103">有兩種類型的建構函式： 類型建構函式和執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="1d1d8-104">型別建構函式是靜態的而且使用該類型之前，由 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="1d1d8-105">建立類型的執行個體時，就會執行執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="1d1d8-106">型別建構函式不接受任何參數。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="1d1d8-107">可以執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-107">Instance constructors can.</span></span> <span data-ttu-id="1d1d8-108">不接受任何參數的執行個體建構函式通常會呼叫預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="1d1d8-109">建構函式會建立類型的執行個體的最自然的方式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="1d1d8-110">大部分的開發人員將會搜尋，然後再次嘗試使用建構函式，它們在考量替代方式來建立執行個體 （例如 factory 方法） 之前。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="1d1d8-111">**✓ CONSIDER**提供簡單、 在理想情況下預設、 建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="1d1d8-112">簡單的建構函式非常小的幾個參數，而且所有參數都都基本型別或列舉型別。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="1d1d8-113">這種簡單的建構函式會增加架構的可用性。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="1d1d8-114">**✓ CONSIDER**而不建構函式使用的靜態 factory 方法，如果所需的作業語意是否未直接對應至建構的新執行個體，或建構函式設計指導方針並不適合。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="1d1d8-115">**✓ DO**以捷徑中使用建構函式參數，設定主要屬性。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="1d1d8-116">不應該有任何差異，在語意使用空的建構函式後面接著某些屬性會設定並使用多個引數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="1d1d8-117">**✓ DO**如果建構函式參數用來只設定屬性，使用相同的名稱，建構函式參數和屬性。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="1d1d8-118">唯一的差異，這類參數和屬性之間應該大小寫。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="1d1d8-119">**✓ DO**建構函式中的最少工作。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="1d1d8-120">建構函式應該執行的工作量以外擷取建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="1d1d8-121">應延遲的任何其他處理成本，直到需要為止。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="1d1d8-122">**✓ DO**擲回例外狀況，從執行個體建構函式，如果適當的話。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="1d1d8-123">**✓ DO**明確宣告的公用預設建構函式在類別中，如果需要這類建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="1d1d8-124">如果您明確地不宣告任何建構函式的型別上，許多語言 （例如 C# 中) 會自動加入公用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="1d1d8-125">（抽象類別取得的受保護的建構函式）。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="1d1d8-126">將參數化建構函式加入類別，可防止編譯器加入預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="1d1d8-127">這通常會導致意外的重大變更。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="1d1d8-128">**X AVOID**明確定義結構的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="1d1d8-129">這可讓陣列建立速度更快，因為如果未定義預設建構函式，它並沒有在陣列中每個插槽上執行。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="1d1d8-130">請注意，許多編譯器，包括 C# 中，不允許結構，因此具有無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="1d1d8-131">**X AVOID**其建構函式內的物件上呼叫虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="1d1d8-132">呼叫虛擬成員會導致最常衍生的覆寫，會呼叫，即使最常衍生的型別建構函式已完全尚未執行。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="1d1d8-133">型別建構函式的指導方針</span><span class="sxs-lookup"><span data-stu-id="1d1d8-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="1d1d8-134">**✓ DO**私人靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="1d1d8-135">靜態建構函式，也稱為類別的建構函式，用來初始化型別。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="1d1d8-136">在建立類型的第一個執行個體，或呼叫該型別上的任何靜態成員之前，CLR 會呼叫靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="1d1d8-137">使用者已無法控制當呼叫靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="1d1d8-138">如果靜態建構函式不是私用的它可以由 CLR 以外的程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="1d1d8-139">根據建構函式中執行的作業，這可能會造成非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="1d1d8-140">C# 編譯器會強制為私用靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="1d1d8-141">**X DO NOT**擲回例外狀況，從靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="1d1d8-142">從型別建構函式擲回例外狀況，如果類型不是使用目前的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="1d1d8-143">**✓ CONSIDER**初始化的靜態欄位內嵌，而不是使用明確靜態建構函式，因為執行階段能夠使效能最佳化的不需要明確定義的靜態建構函式的類型。</span><span class="sxs-lookup"><span data-stu-id="1d1d8-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="1d1d8-144">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1d1d8-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1d1d8-145">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="1d1d8-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1d8-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d1d8-146">See Also</span></span>  
 [<span data-ttu-id="1d1d8-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="1d1d8-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="1d1d8-148">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="1d1d8-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
