---
title: 介面設計
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 6f8cbb757ffb42f63903b212fee33cdcbba7ecb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727675"
---
# <a name="interface-design"></a><span data-ttu-id="6a756-102">介面設計</span><span class="sxs-lookup"><span data-stu-id="6a756-102">Interface Design</span></span>

<span data-ttu-id="6a756-103">雖然大部分的 Api 最適合使用類別和結構來建立模型，但在某些情況下，介面較適合或為唯一的選項。</span><span class="sxs-lookup"><span data-stu-id="6a756-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="6a756-104">CLR 不支援多重繼承 (亦即，CLR 類別無法繼承自一個以上的基類) ，但是除了繼承自基類之外，它也允許型別執行一或多個介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="6a756-105">因此，介面通常用來達成多重繼承的效果。</span><span class="sxs-lookup"><span data-stu-id="6a756-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="6a756-106">例如， <xref:System.IDisposable> 是允許類型支援 disposability 的介面，而不受其想要參與的任何其他繼承階層。</span><span class="sxs-lookup"><span data-stu-id="6a756-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="6a756-107">定義介面的另一種情況是建立可由數種類型支援的通用介面，包括一些實數值型別。</span><span class="sxs-lookup"><span data-stu-id="6a756-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="6a756-108">實值型別無法繼承自以外的型別 <xref:System.ValueType> ，但是它們可以實作為介面，因此使用介面是唯一的選項，以便提供通用基底型別。</span><span class="sxs-lookup"><span data-stu-id="6a756-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="6a756-109">如果您需要一組包含實值型別的型別，✔️會定義介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-109">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="6a756-110">如果您需要在已繼承自其他類型的類型上支援其功能，✔️考慮定義介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-110">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="6a756-111">❌ 避免使用標記介面 (沒有成員) 的介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-111">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="6a756-112">如果您需要將類別標示為具有特定特性 (標記) ，一般而言，請使用自訂屬性，而不是介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="6a756-113">✔️請至少提供一個實作為介面的型別。</span><span class="sxs-lookup"><span data-stu-id="6a756-113">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="6a756-114">這樣做有助於驗證介面的設計。</span><span class="sxs-lookup"><span data-stu-id="6a756-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="6a756-115">例如， <xref:System.Collections.Generic.List%601> 是介面的實 <xref:System.Collections.Generic.IList%601> 。</span><span class="sxs-lookup"><span data-stu-id="6a756-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="6a756-116">✔️請提供至少一個 API 來取用您所定義的每個介面， (使用介面做為參數的方法，或輸入為介面) 的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a756-116">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="6a756-117">這樣做有助於驗證介面設計。</span><span class="sxs-lookup"><span data-stu-id="6a756-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="6a756-118">例如， <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 使用 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="6a756-119">❌ 請勿將成員新增至先前已發行的介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-119">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="6a756-120">這麼做會中斷介面的實作為。</span><span class="sxs-lookup"><span data-stu-id="6a756-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="6a756-121">您應該建立新的介面，以避免版本控制問題。</span><span class="sxs-lookup"><span data-stu-id="6a756-121">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="6a756-122">除了這些指導方針中所述的情況之外，一般而言，您應該在設計 managed 程式碼可重複使用的程式庫中選擇類別，而不是介面。</span><span class="sxs-lookup"><span data-stu-id="6a756-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="6a756-123">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="6a756-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6a756-124">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="6a756-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6a756-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a756-125">See also</span></span>

- [<span data-ttu-id="6a756-126">型別設計方針</span><span class="sxs-lookup"><span data-stu-id="6a756-126">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="6a756-127">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="6a756-127">Framework Design Guidelines</span></span>](index.md)
