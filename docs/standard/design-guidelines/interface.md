---
title: 介面設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 544035180a5004bfe2f4c75c680116e52bf25f98
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744160"
---
# <a name="interface-design"></a><span data-ttu-id="95dc1-102">介面設計</span><span class="sxs-lookup"><span data-stu-id="95dc1-102">Interface Design</span></span>
<span data-ttu-id="95dc1-103">雖然大部分的 Api 都是使用類別和結構來進行模型化，但有時候介面較合適或是唯一的選項。</span><span class="sxs-lookup"><span data-stu-id="95dc1-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="95dc1-104">CLR 不支援多重繼承（也就是 CLR 類別無法繼承自一個以上的基類），但是除了繼承自基類之外，它還允許型別執行一或多個介面。</span><span class="sxs-lookup"><span data-stu-id="95dc1-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="95dc1-105">因此，通常會使用介面來達到多重繼承的效果。</span><span class="sxs-lookup"><span data-stu-id="95dc1-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="95dc1-106">例如，<xref:System.IDisposable> 是一個介面，可讓類型支援 disposability，而不受其想要參與的任何其他繼承階層。</span><span class="sxs-lookup"><span data-stu-id="95dc1-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="95dc1-107">定義介面的另一種情況是建立可由數種類型支援的通用介面，包括一些實數值型別。</span><span class="sxs-lookup"><span data-stu-id="95dc1-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="95dc1-108">實值型別無法繼承自 <xref:System.ValueType>以外的型別，但它們可以實作為介面，因此使用介面是唯一的選項，以便提供一般基底型別。</span><span class="sxs-lookup"><span data-stu-id="95dc1-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="95dc1-109">如果您需要一組包含實數值型別的類型來支援一些通用 API，✔️請定義介面。</span><span class="sxs-lookup"><span data-stu-id="95dc1-109">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="95dc1-110">如果您需要在已經繼承自其他類型的類型上支援其功能，✔️請考慮定義介面。</span><span class="sxs-lookup"><span data-stu-id="95dc1-110">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="95dc1-111">❌ 避免使用標記介面（沒有成員的介面）。</span><span class="sxs-lookup"><span data-stu-id="95dc1-111">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="95dc1-112">如果您需要將類別標示為具有特定特性（標記），則一般會使用自訂屬性，而不是介面。</span><span class="sxs-lookup"><span data-stu-id="95dc1-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="95dc1-113">✔️提供至少一個型別，也就是介面的執行。</span><span class="sxs-lookup"><span data-stu-id="95dc1-113">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="95dc1-114">這麼做有助於驗證介面的設計。</span><span class="sxs-lookup"><span data-stu-id="95dc1-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="95dc1-115">例如，<xref:System.Collections.Generic.List%601> 是 <xref:System.Collections.Generic.IList%601> 介面的執行。</span><span class="sxs-lookup"><span data-stu-id="95dc1-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="95dc1-116">✔️提供至少一個使用您所定義之介面的 API （將介面當做參數或屬性輸入為介面的方法）。</span><span class="sxs-lookup"><span data-stu-id="95dc1-116">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="95dc1-117">這麼做有助於驗證介面設計。</span><span class="sxs-lookup"><span data-stu-id="95dc1-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="95dc1-118">例如，<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 會使用 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="95dc1-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="95dc1-119">❌ 不要將成員新增至先前隨附的介面。</span><span class="sxs-lookup"><span data-stu-id="95dc1-119">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="95dc1-120">這麼做會中斷介面的實現。</span><span class="sxs-lookup"><span data-stu-id="95dc1-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="95dc1-121">您應該建立新的介面，以避免版本控制問題。</span><span class="sxs-lookup"><span data-stu-id="95dc1-121">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="95dc1-122">除了這些指導方針中所述的情況之外，您通常應該選擇 [類別]，而不是 [設計 managed 程式碼可重複使用的程式庫] 中的介面。</span><span class="sxs-lookup"><span data-stu-id="95dc1-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="95dc1-123">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="95dc1-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="95dc1-124">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="95dc1-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="95dc1-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="95dc1-125">See also</span></span>

- [<span data-ttu-id="95dc1-126">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="95dc1-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="95dc1-127">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="95dc1-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
