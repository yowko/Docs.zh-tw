---
title: 建構函式設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400600"
---
# <a name="constructor-design"></a><span data-ttu-id="db7c7-102">建構函式設計</span><span class="sxs-lookup"><span data-stu-id="db7c7-102">Constructor Design</span></span>

<span data-ttu-id="db7c7-103">有兩種建構函式：類型建構函式和實例建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="db7c7-104">類型建構函式是靜態的，在使用類型之前由 CLR 運行。</span><span class="sxs-lookup"><span data-stu-id="db7c7-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="db7c7-105">實例建構函式在創建類型的實例時運行。</span><span class="sxs-lookup"><span data-stu-id="db7c7-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="db7c7-106">類型建構函式不能採用任何參數。</span><span class="sxs-lookup"><span data-stu-id="db7c7-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="db7c7-107">實例建構函式可以。</span><span class="sxs-lookup"><span data-stu-id="db7c7-107">Instance constructors can.</span></span> <span data-ttu-id="db7c7-108">不採用任何參數的實例建構函式通常稱為無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="db7c7-109">建構函式是創建類型實例的最自然方法。</span><span class="sxs-lookup"><span data-stu-id="db7c7-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="db7c7-110">大多數開發人員在考慮創建實例（如工廠方法）的替代方法之前，將搜索並嘗試使用建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="db7c7-111">✔️ 考慮提供簡單、理想的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="db7c7-112">簡單的建構函式具有非常少量的參數，並且所有參數都是基元或枚舉。</span><span class="sxs-lookup"><span data-stu-id="db7c7-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="db7c7-113">這種簡單的建構函式提高了框架的可用性。</span><span class="sxs-lookup"><span data-stu-id="db7c7-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="db7c7-114">✔️如果所需操作的語義不直接映射到新實例的構造，或者遵循建構函式設計準則感覺不自然，則考慮使用靜態工廠方法而不是建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="db7c7-115">✔️ DO 使用建構函式參數作為設置主屬性的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="db7c7-116">在語義上，使用空建構函式後跟某些屬性集和使用具有多個參數的建構函式之間應該沒有區別。</span><span class="sxs-lookup"><span data-stu-id="db7c7-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="db7c7-117">如果建構函式參數用於簡單地設置屬性，則✔️ DO 對建構函式參數使用相同的名稱和屬性。</span><span class="sxs-lookup"><span data-stu-id="db7c7-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="db7c7-118">此類參數和屬性之間的唯一區別應該是套管。</span><span class="sxs-lookup"><span data-stu-id="db7c7-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="db7c7-119">✔️在建構函式中執行最小工作。</span><span class="sxs-lookup"><span data-stu-id="db7c7-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="db7c7-120">除了捕獲建構函式參數之外，建構函式不應執行太多工作。</span><span class="sxs-lookup"><span data-stu-id="db7c7-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="db7c7-121">任何其他處理的成本應延遲到需要。</span><span class="sxs-lookup"><span data-stu-id="db7c7-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="db7c7-122">✔️如果適用，從實例建構函式引發異常。</span><span class="sxs-lookup"><span data-stu-id="db7c7-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="db7c7-123">✔️如果需要這樣的建構函式，則在類中顯式聲明公共無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="db7c7-124">如果不顯式聲明類型上的任何建構函式，則許多語言（如 C#）將自動添加公共無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="db7c7-125">（抽象類別獲取受保護的建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="db7c7-126">向類添加參數化建構函式可防止編譯器添加無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="db7c7-127">這通常會導致意外的中斷更改。</span><span class="sxs-lookup"><span data-stu-id="db7c7-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="db7c7-128">❌AVOID 在結構上顯式定義無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="db7c7-129">這使得陣列創建速度更快，因為如果未定義無參數建構函式，則不必在陣列中的每個插槽上運行。</span><span class="sxs-lookup"><span data-stu-id="db7c7-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="db7c7-130">請注意，許多編譯器（包括 C#）不允許結構具有無參數建構函式。因此。</span><span class="sxs-lookup"><span data-stu-id="db7c7-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="db7c7-131">❌AVOID 在其建構函式內的物件上調用虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="db7c7-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="db7c7-132">調用虛擬成員將導致調用最派生的重寫，即使最派生類型的建構函式尚未完全運行。</span><span class="sxs-lookup"><span data-stu-id="db7c7-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="db7c7-133">類型建構函式指南</span><span class="sxs-lookup"><span data-stu-id="db7c7-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="db7c7-134">✔️將靜態建構函式作為私有。</span><span class="sxs-lookup"><span data-stu-id="db7c7-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="db7c7-135">靜態建構函式（也稱為類建構函式）用於初始化類型。</span><span class="sxs-lookup"><span data-stu-id="db7c7-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="db7c7-136">CLR 在創建類型的第一個實例或調用該類型上的任何靜態成員之前調用靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="db7c7-137">使用者無法控制何時調用靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="db7c7-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="db7c7-138">如果靜態建構函式不是私有的，則可以由 CLR 以外的代碼調用它。</span><span class="sxs-lookup"><span data-stu-id="db7c7-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="db7c7-139">根據建構函式中執行的操作，這可能導致意外行為。</span><span class="sxs-lookup"><span data-stu-id="db7c7-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="db7c7-140">C# 編譯器強制靜態建構函式為私有。</span><span class="sxs-lookup"><span data-stu-id="db7c7-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="db7c7-141">❌不要從靜態建構函式引發異常。</span><span class="sxs-lookup"><span data-stu-id="db7c7-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="db7c7-142">如果從類型建構函式引發異常，則該類型在當前應用程式域中不可用。</span><span class="sxs-lookup"><span data-stu-id="db7c7-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="db7c7-143">✔️考慮內聯初始化靜態欄位，而不是顯式使用靜態建構函式，因為運行時能夠優化沒有顯式定義的靜態建構函式的類型的性能。</span><span class="sxs-lookup"><span data-stu-id="db7c7-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="db7c7-144">*部分© 2005， 2009 微軟公司.保留擁有權利。*</span><span class="sxs-lookup"><span data-stu-id="db7c7-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="db7c7-145">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="db7c7-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="db7c7-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db7c7-146">See also</span></span>

- [<span data-ttu-id="db7c7-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="db7c7-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="db7c7-148">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="db7c7-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
