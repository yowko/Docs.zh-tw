---
title: 抽象 (抽象類型和介面)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: KrzysztofCwalina
ms.openlocfilehash: 4ff79af968c8a0a360cade687b8c60cdd71de192
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149909"
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="8d574-102">抽象 (抽象類型和介面)</span><span class="sxs-lookup"><span data-stu-id="8d574-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="8d574-103">抽象概念是描述合約，但不提供完整的實作合約的型別。</span><span class="sxs-lookup"><span data-stu-id="8d574-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="8d574-104">抽象概念通常會實作為抽象類別或介面，和其隨附一組妥善定義的參考文件描述的實作合約的型別所需的語意。</span><span class="sxs-lookup"><span data-stu-id="8d574-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="8d574-105">最重要的抽象概念，.NET Framework 中的部分<xref:System.IO.Stream>， <xref:System.Collections.Generic.IEnumerable%601>，和<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="8d574-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="8d574-106">您可以藉由實作具象類型支援抽象類別的合約和 framework Api 取用 （操作） 時，使用此具象型別擴充架構的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="8d574-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>  
  
 <span data-ttu-id="8d574-107">有意義且實用的抽象層能夠承受，測試是時間的很難設計的。</span><span class="sxs-lookup"><span data-stu-id="8d574-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="8d574-108">主要的困難取得正確的不多也不較少的成員集。</span><span class="sxs-lookup"><span data-stu-id="8d574-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="8d574-109">如果抽象概念會有太多的成員，會變得很困難或甚至根本不可能實作。</span><span class="sxs-lookup"><span data-stu-id="8d574-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="8d574-110">如果有太少的成員，承諾的功能，它會變成在許多有趣的案例。</span><span class="sxs-lookup"><span data-stu-id="8d574-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>  
  
 <span data-ttu-id="8d574-111">太多的抽象概念的架構中也有負面影響使用性的 framework。</span><span class="sxs-lookup"><span data-stu-id="8d574-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="8d574-112">它通常是很難了解抽象概念，而不需要了解它如何融入相通的具象實作，運作於抽象概念的 Api。</span><span class="sxs-lookup"><span data-stu-id="8d574-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="8d574-113">此外，抽象概念和其成員的名稱是抽象的這樣會使得它們都使用加密和親近而不需要先了解其使用方式的更廣泛的內容。</span><span class="sxs-lookup"><span data-stu-id="8d574-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>  
  
 <span data-ttu-id="8d574-114">不過，抽象概念會提供功能極為強大的擴充性，通常無法比對的其他擴充性機制。</span><span class="sxs-lookup"><span data-stu-id="8d574-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="8d574-115">也就是核心的許多架構模式的詳細資訊，例如外掛程式，逆轉控制 (IoC)、 管線等等。</span><span class="sxs-lookup"><span data-stu-id="8d574-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="8d574-116">它們也是非常重要的可測試性的架構。</span><span class="sxs-lookup"><span data-stu-id="8d574-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="8d574-117">良好的抽象概念可使您能夠建立單元測試以大量相依性。</span><span class="sxs-lookup"><span data-stu-id="8d574-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="8d574-118">總而言之，抽象化是負責大快人心的豐富功能的現代的物件導向架構。</span><span class="sxs-lookup"><span data-stu-id="8d574-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>  
  
 <span data-ttu-id="8d574-119">**X DO NOT** 提供抽象，除非它們經過開發數種具象實作和應用程式開發介面使用的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="8d574-119">**X DO NOT** provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>  
  
 <span data-ttu-id="8d574-120">**✓ DO** 設計抽象時請小心選擇之間的抽象類別和介面。</span><span class="sxs-lookup"><span data-stu-id="8d574-120">**✓ DO** choose carefully between an abstract class and an interface when designing an abstraction.</span></span>  
  
 <span data-ttu-id="8d574-121">**✓ CONSIDER** 提供參考測試的具象實作的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="8d574-121">**✓ CONSIDER** providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="8d574-122">這類測試應該允許使用者來測試是否正確實作它們的實作的合約。</span><span class="sxs-lookup"><span data-stu-id="8d574-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>  
  
 <span data-ttu-id="8d574-123">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="8d574-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8d574-124">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="8d574-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d574-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d574-125">See also</span></span>

- [<span data-ttu-id="8d574-126">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="8d574-126">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="8d574-127">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="8d574-127">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
