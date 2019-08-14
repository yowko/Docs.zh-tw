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
author: KrzysztofCwalina
ms.openlocfilehash: a43ec815275e58f4bc6462fb4f5cb4733267de31
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972109"
---
# <a name="constructor-design"></a><span data-ttu-id="ac0d7-102">建構函式設計</span><span class="sxs-lookup"><span data-stu-id="ac0d7-102">Constructor Design</span></span>

<span data-ttu-id="ac0d7-103">有兩種類型的「型別」 (type) 和「實例」 (instance) 函數。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="ac0d7-104">類型的函式是靜態的, 而且會在使用類型之前由 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="ac0d7-105">建立類型的實例時, 會執行實例的函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="ac0d7-106">類型的函式不能接受任何參數。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="ac0d7-107">實例構造函式可以。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-107">Instance constructors can.</span></span> <span data-ttu-id="ac0d7-108">不接受任何參數的實例構造函式通常稱為無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="ac0d7-109">建立型別的實例時, 這些是最自然的方式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="ac0d7-110">大部分的開發人員會先搜尋並嘗試使用「函式」, 然後再考慮建立實例的替代方式 (例如 factory 方法)。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="ac0d7-111">**✓ CONSIDER** 提供簡單、 在理想情況下預設、 建構函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="ac0d7-112">簡單的函式有非常少的參數數目, 而所有參數都是基本或列舉。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="ac0d7-113">這類簡單的函式會提高架構的可用性。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="ac0d7-114">**✓ CONSIDER** 而不建構函式使用的靜態 factory 方法，如果所需的作業語意是否未直接對應至建構的新執行個體，或建構函式設計指導方針並不適合。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="ac0d7-115">**✓ DO** 以捷徑中使用建構函式參數，設定主要屬性。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="ac0d7-116">使用空白的函式, 後面接著一些屬性集, 並使用具有多個引數的函式, 兩者之間的語義應該沒有任何差異。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="ac0d7-117">**✓ DO** 如果建構函式參數用來只設定屬性，使用相同的名稱，建構函式參數和屬性。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="ac0d7-118">這類參數和屬性之間的唯一差異應該是大小寫。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="ac0d7-119">**✓ DO** 建構函式中的最少工作。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-119">**✓ DO** minimal work in the constructor.</span></span>

<span data-ttu-id="ac0d7-120">除了 capture 函式參數之外, 這些函式不應執行太多工。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="ac0d7-121">任何其他處理的成本應延遲到需要的時間。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="ac0d7-122">**✓ DO** 擲回例外狀況，從執行個體建構函式，如果適當的話。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="ac0d7-123">如果需要這類的函式, **✓**會在類別中明確宣告公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-123">**✓ DO** explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="ac0d7-124">如果您未在類型上明確宣告任何函式, 許多語言 (例如C#) 會自動加入公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="ac0d7-125">(抽象類別會取得受保護的構造函式)。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="ac0d7-126">將參數化的函式加入至類別, 可防止編譯器加入無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="ac0d7-127">這通常會導致意外的中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="ac0d7-128">**X 避免**在結構上明確定義無參數的構造函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-128">**X AVOID** explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="ac0d7-129">這樣可以更快速地建立陣列, 因為如果未定義無參數的函式, 則不需要在陣列中的每個位置上執行。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="ac0d7-130">請注意, 許多編譯器 ( C#包括) 都不允許結構因為此原因而擁有無參數的構造函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="ac0d7-131">**X AVOID** 其建構函式內的物件上呼叫虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="ac0d7-132">呼叫虛擬成員會導致呼叫最常衍生的覆寫, 即使最常衍生類型的函式尚未完全執行。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="ac0d7-133">型別函數方針</span><span class="sxs-lookup"><span data-stu-id="ac0d7-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="ac0d7-134">**✓ DO** 私人靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-134">**✓ DO** make static constructors private.</span></span>

<span data-ttu-id="ac0d7-135">靜態的函式 (也稱為類別的函式) 是用來初始化型別。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="ac0d7-136">CLR 會在建立類型的第一個實例或呼叫該類型的任何靜態成員之前, 呼叫靜態的函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="ac0d7-137">使用者無法控制呼叫靜態函式的時間。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="ac0d7-138">如果靜態的函式不是私用, 則可由 CLR 以外的程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="ac0d7-139">視在此函式中執行的作業而定, 這可能會造成非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="ac0d7-140">C#編譯器會強制將靜態的構造函式設為私用。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="ac0d7-141">**X DO NOT** 擲回例外狀況，從靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-141">**X DO NOT** throw exceptions from static constructors.</span></span>

<span data-ttu-id="ac0d7-142">如果從類型的函式擲回例外狀況, 類型在目前的應用程式域中無法使用。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="ac0d7-143">**✓ CONSIDER** 初始化的靜態欄位內嵌，而不是使用明確靜態建構函式，因為執行階段能夠使效能最佳化的不需要明確定義的靜態建構函式的類型。</span><span class="sxs-lookup"><span data-stu-id="ac0d7-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="ac0d7-144">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="ac0d7-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="ac0d7-145">*從[架構設計方針轉載已獲得皮耳森教育, inc. 的許可權:Krzysztof Cwalina 和 Brad Abrams 可重複使用的 .net 程式庫第](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 2 版的慣例、慣用語和模式, 已于2008年10月22日發行, 屬於 Microsoft Windows 開發系列的 Addison-Wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="ac0d7-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ac0d7-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac0d7-146">See also</span></span>

- [<span data-ttu-id="ac0d7-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="ac0d7-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="ac0d7-148">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="ac0d7-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
