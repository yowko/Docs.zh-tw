---
title: 抽象 (抽象類型和介面)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5863b4ae9cad940e4dd47ef93e07763916427f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="dfddc-102">抽象 (抽象類型和介面)</span><span class="sxs-lookup"><span data-stu-id="dfddc-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="dfddc-103">抽象概念是描述合約，但不提供完整的實作的合約的型別。</span><span class="sxs-lookup"><span data-stu-id="dfddc-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="dfddc-104">抽象概念通常會實作為抽象類別或介面，和它們隨附一組妥善定義的參考文件描述的實作合約的型別所需的語意。</span><span class="sxs-lookup"><span data-stu-id="dfddc-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="dfddc-105">某些.NET Framework 中最重要的抽象概念包括<xref:System.IO.Stream>， <xref:System.Collections.Generic.IEnumerable%601>，和<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="dfddc-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="dfddc-106">您可以透過實作支援抽象的合約的具象型別，並使用 framework 應用程式開發介面使用 （操作） 此具象型別擴充架構的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="dfddc-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>  
  
 <span data-ttu-id="dfddc-107">有意義且實用的抽象概念，能夠承受，測試是時間的很難設計。</span><span class="sxs-lookup"><span data-stu-id="dfddc-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="dfddc-108">主要的難度即將不再和不較少的成員權限集。</span><span class="sxs-lookup"><span data-stu-id="dfddc-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="dfddc-109">如果抽象概念，具有太多的成員，它會變成難以或甚至無法實作。</span><span class="sxs-lookup"><span data-stu-id="dfddc-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="dfddc-110">如果有太少的成員，承諾的功能，它會變成無效，在許多有趣的情況下。</span><span class="sxs-lookup"><span data-stu-id="dfddc-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>  
  
 <span data-ttu-id="dfddc-111">太多的抽象概念，在架構中也有負面影響架構的可用性。</span><span class="sxs-lookup"><span data-stu-id="dfddc-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="dfddc-112">通常是很難了解如果不了解它如何融入的具象實作和操作資料的抽象 Api 較大的圖片的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="dfddc-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="dfddc-113">此外，抽象概念和其成員的名稱是抽象的這樣會使得它們隱晦且親近不含第一個的了解其使用方式的更廣泛的內容。</span><span class="sxs-lookup"><span data-stu-id="dfddc-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>  
  
 <span data-ttu-id="dfddc-114">不過，抽象層提供極為強大的其他擴充性機制無法通常會比對的擴充性。</span><span class="sxs-lookup"><span data-stu-id="dfddc-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="dfddc-115">它們是許多架構模式的詳細資訊，例如外掛程式，核心逆轉控制 (IoC)、 管線等等。</span><span class="sxs-lookup"><span data-stu-id="dfddc-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="dfddc-116">它們也是極為重要的測試能力的架構。</span><span class="sxs-lookup"><span data-stu-id="dfddc-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="dfddc-117">良好的抽象概念實現出大量的相依性，以便進行單元測試虛設常式。</span><span class="sxs-lookup"><span data-stu-id="dfddc-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="dfddc-118">總而言之，抽象化是負責 sought-after 現代化的物件導向架構的豐富。</span><span class="sxs-lookup"><span data-stu-id="dfddc-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>  
  
 <span data-ttu-id="dfddc-119">**X 不**提供抽象，除非它們經過開發數種具象實作和應用程式開發介面使用的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="dfddc-119">**X DO NOT** provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>  
  
 <span data-ttu-id="dfddc-120">**✓ 不要**設計抽象時請小心選擇之間的抽象類別和介面。</span><span class="sxs-lookup"><span data-stu-id="dfddc-120">**✓ DO** choose carefully between an abstract class and an interface when designing an abstraction.</span></span>  
  
 <span data-ttu-id="dfddc-121">**✓ 考慮**提供參考測試的具象實作的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="dfddc-121">**✓ CONSIDER** providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="dfddc-122">這類測試應該允許使用者以測試是否有其正確實作的合約。</span><span class="sxs-lookup"><span data-stu-id="dfddc-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>  
  
 <span data-ttu-id="dfddc-123">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="dfddc-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="dfddc-124">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="dfddc-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfddc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfddc-125">See Also</span></span>  
 [<span data-ttu-id="dfddc-126">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="dfddc-126">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="dfddc-127">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="dfddc-127">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
