---
title: 抽象 (抽象類型和介面)
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: f5169cf730dc987526765c9538978901d424814b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701402"
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="87328-102">抽象 (抽象類型和介面)</span><span class="sxs-lookup"><span data-stu-id="87328-102">Abstractions (Abstract Types and Interfaces)</span></span>

<span data-ttu-id="87328-103">抽象概念是一種描述合約的類型，但不會提供完整的合約執行。</span><span class="sxs-lookup"><span data-stu-id="87328-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="87328-104">抽象概念通常會實作為抽象類別或介面，並隨附一組定義完善的參考檔，說明實作為合約的型別所需的語法。</span><span class="sxs-lookup"><span data-stu-id="87328-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="87328-105">.NET Framework 中最重要的抽象概念包括 <xref:System.IO.Stream> 、 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="87328-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>

 <span data-ttu-id="87328-106">您可以藉由執行可支援抽象概念的具象型別，以及使用此具象型別搭配使用 (在) 抽象概念上運作的架構 Api，來擴充架構。</span><span class="sxs-lookup"><span data-stu-id="87328-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>

 <span data-ttu-id="87328-107">有意義且有用的抽象概念，能夠承受時間的測試，是很難設計的。</span><span class="sxs-lookup"><span data-stu-id="87328-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="87328-108">主要的困難是取得一組正確的成員，而不是更多。</span><span class="sxs-lookup"><span data-stu-id="87328-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="87328-109">如果抽象概念的成員太多，就會變得很難或甚至根本無法執行。</span><span class="sxs-lookup"><span data-stu-id="87328-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="87328-110">如果該功能的成員太少，在許多有趣的情況下就會變得無用。</span><span class="sxs-lookup"><span data-stu-id="87328-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>

 <span data-ttu-id="87328-111">架構中有太多抽象概念也會對架構的可用性造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="87328-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="87328-112">您通常很難瞭解抽象概念，而不需要瞭解如何將它放入具體的實體，以及在抽象上操作之 Api 的較大圖片。</span><span class="sxs-lookup"><span data-stu-id="87328-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="87328-113">此外，抽象概念和其成員的名稱一定是抽象的，這通常會讓它們變得更清楚且 unapproachable，而不需要先瞭解其使用方式的廣泛內容。</span><span class="sxs-lookup"><span data-stu-id="87328-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>

 <span data-ttu-id="87328-114">不過，抽象層提供了功能強大的擴充性，而其他擴充性機制通常不能相符。</span><span class="sxs-lookup"><span data-stu-id="87328-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="87328-115">它們是許多架構模式的核心，例如外掛程式、控制反轉 (IoC) 、管線等等。</span><span class="sxs-lookup"><span data-stu-id="87328-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="87328-116">它們對於架構的可測試性也非常重要。</span><span class="sxs-lookup"><span data-stu-id="87328-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="87328-117">良好的抽象概念可讓您針對單元測試的目的，將繁重的相依性存根。</span><span class="sxs-lookup"><span data-stu-id="87328-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="87328-118">總而言之，抽象概念負責最豐富的新式物件導向架構。</span><span class="sxs-lookup"><span data-stu-id="87328-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>

 <span data-ttu-id="87328-119">❌ 除非透過開發數個具象的實作為測試，以及使用抽象概念的 Api，否則請勿提供抽象。</span><span class="sxs-lookup"><span data-stu-id="87328-119">❌ DO NOT provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>

 <span data-ttu-id="87328-120">設計抽象概念時，✔️務必仔細選擇抽象類別和介面。</span><span class="sxs-lookup"><span data-stu-id="87328-120">✔️ DO choose carefully between an abstract class and an interface when designing an abstraction.</span></span>

 <span data-ttu-id="87328-121">✔️考慮提供抽象概念的參考測試。</span><span class="sxs-lookup"><span data-stu-id="87328-121">✔️ CONSIDER providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="87328-122">這類測試應可讓使用者測試其執行是否正確地實行合約。</span><span class="sxs-lookup"><span data-stu-id="87328-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>

 <span data-ttu-id="87328-123">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="87328-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="87328-124">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="87328-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="87328-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87328-125">See also</span></span>

- [<span data-ttu-id="87328-126">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="87328-126">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="87328-127">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="87328-127">Designing for Extensibility</span></span>](designing-for-extensibility.md)
