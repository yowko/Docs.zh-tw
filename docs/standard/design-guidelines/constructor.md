---
title: 建構函式設計
ms.date: 10/22/2008
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
ms.openlocfilehash: 27fb73aa01adf31117d1b82724873db3a03fd269
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821394"
---
# <a name="constructor-design"></a><span data-ttu-id="38bd0-102">建構函式設計</span><span class="sxs-lookup"><span data-stu-id="38bd0-102">Constructor Design</span></span>

<span data-ttu-id="38bd0-103">有兩種類型的函數：類型的函式和實例的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="38bd0-104">型別函式是靜態的，而且是在使用型別之前由 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="38bd0-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="38bd0-105">建立型別的實例時，會執行實例的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="38bd0-106">型別函式不能採用任何參數。</span><span class="sxs-lookup"><span data-stu-id="38bd0-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="38bd0-107">實例的函式可以。</span><span class="sxs-lookup"><span data-stu-id="38bd0-107">Instance constructors can.</span></span> <span data-ttu-id="38bd0-108">未採用任何參數的實例函式通常稱為無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="38bd0-109">使用函式是建立型別實例的最自然方式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="38bd0-110">大部分的開發人員會先搜尋並嘗試使用函式，再考慮建立實例的替代方式 (例如) 的 factory 方法。</span><span class="sxs-lookup"><span data-stu-id="38bd0-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="38bd0-111">✔️考慮提供簡單且理想的預設值。</span><span class="sxs-lookup"><span data-stu-id="38bd0-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="38bd0-112">簡單的函式具有極少的參數數目，而所有參數都是基本或列舉。</span><span class="sxs-lookup"><span data-stu-id="38bd0-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="38bd0-113">這類簡單的函式會增加架構的可用性。</span><span class="sxs-lookup"><span data-stu-id="38bd0-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="38bd0-114">如果所需作業的語法不會直接對應至新實例的結構，或遵循函式設計指導方針的非自然，則✔️考慮使用靜態 factory 方法，而不是函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="38bd0-115">✔️請使用函式參數做為設定主要屬性的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="38bd0-116">在使用空白的函式後接某些屬性集，以及使用具有多個引數的函式時，兩者之間的語法應該沒有任何差異。</span><span class="sxs-lookup"><span data-stu-id="38bd0-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="38bd0-117">如果使用函式參數來直接設定屬性，則✔️會針對函式參數使用相同的名稱，並使用屬性。</span><span class="sxs-lookup"><span data-stu-id="38bd0-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="38bd0-118">這類參數和屬性之間的唯一差異應該是大小寫。</span><span class="sxs-lookup"><span data-stu-id="38bd0-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="38bd0-119">✔️在函式中執行最少量的工作。</span><span class="sxs-lookup"><span data-stu-id="38bd0-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="38bd0-120">除了捕捉函式參數之外，這些函式不應該執行太多工作。</span><span class="sxs-lookup"><span data-stu-id="38bd0-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="38bd0-121">任何其他處理的成本都應該延遲到需要的時間。</span><span class="sxs-lookup"><span data-stu-id="38bd0-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="38bd0-122">✔️確實會從實例的函式擲回例外狀況（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="38bd0-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="38bd0-123">如果需要這類的函式，✔️確實在類別中宣告公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="38bd0-124">如果您未在類型上明確宣告任何的函式，則許多語言 (例如 c # ) 會自動加入公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="38bd0-125"> (抽象類別會取得受保護的函式。 ) </span><span class="sxs-lookup"><span data-stu-id="38bd0-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="38bd0-126">將參數化的函式加入至類別，可防止編譯器新增無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="38bd0-127">這通常會導致意外的中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="38bd0-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="38bd0-128">❌ 避免在結構上明確定義無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="38bd0-129">這使得陣列的建立速度更快，因為如果未定義無參數的函式，則不需要在陣列中的每個位置執行。</span><span class="sxs-lookup"><span data-stu-id="38bd0-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="38bd0-130">請注意，許多編譯器（包括 c #）都不允許結構因為這個原因而有無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="38bd0-131">❌ 避免在其函式內的物件上呼叫虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="38bd0-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="38bd0-132">呼叫虛擬成員會導致呼叫最常衍生的覆寫，即使大部分衍生類型的函式尚未完全執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="38bd0-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="38bd0-133">型別函式指導方針</span><span class="sxs-lookup"><span data-stu-id="38bd0-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="38bd0-134">✔️將靜態的函式設為私用。</span><span class="sxs-lookup"><span data-stu-id="38bd0-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="38bd0-135">靜態的函式（也稱為類別的函式）是用來初始化型別。</span><span class="sxs-lookup"><span data-stu-id="38bd0-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="38bd0-136">CLR 會在建立類型的第一個實例或呼叫該類型上的任何靜態成員之前，呼叫靜態的函式。</span><span class="sxs-lookup"><span data-stu-id="38bd0-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="38bd0-137">使用者無法控制呼叫靜態函式的時機。</span><span class="sxs-lookup"><span data-stu-id="38bd0-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="38bd0-138">如果靜態的函式不是私用的，則可由 CLR 以外的程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="38bd0-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="38bd0-139">根據在函式中執行的作業而定，這可能會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="38bd0-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="38bd0-140">C # 編譯器會強制將靜態的函式設為私用。</span><span class="sxs-lookup"><span data-stu-id="38bd0-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="38bd0-141">❌ 請勿從靜態的函式擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="38bd0-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="38bd0-142">如果從類型的函式擲回例外狀況，則類型在目前的應用程式域中無法使用。</span><span class="sxs-lookup"><span data-stu-id="38bd0-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="38bd0-143">✔️考慮將靜態欄位初始化，而不是明確地使用靜態的函式，因為執行時間可以將沒有明確定義之靜態函式的類型效能優化。</span><span class="sxs-lookup"><span data-stu-id="38bd0-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="38bd0-144">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="38bd0-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="38bd0-145">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="38bd0-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="38bd0-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="38bd0-146">See also</span></span>

- [<span data-ttu-id="38bd0-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="38bd0-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="38bd0-148">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="38bd0-148">Framework Design Guidelines</span></span>](index.md)
