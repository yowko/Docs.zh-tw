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
ms.openlocfilehash: fd5b8fe10d0dcca5da3a2093f7be37f6d88b382a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280610"
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="35e4d-102">抽象 (抽象類型和介面)</span><span class="sxs-lookup"><span data-stu-id="35e4d-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="35e4d-103">抽象概念是描述合約，但不提供合約完整執行的類型。</span><span class="sxs-lookup"><span data-stu-id="35e4d-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="35e4d-104">抽象概念通常會實作為抽象類別或介面，而且會隨附一組定義完善的參考檔，說明實作為合約的型別所需的語法。</span><span class="sxs-lookup"><span data-stu-id="35e4d-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="35e4d-105">.NET Framework 中一些最重要的抽象概念包括 <xref:System.IO.Stream> 、 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="35e4d-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>

 <span data-ttu-id="35e4d-106">您可以藉由實作為支援抽象概念的具象型別，並使用此具體型別搭配耗用（操作）抽象概念的架構 Api，來擴充架構。</span><span class="sxs-lookup"><span data-stu-id="35e4d-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>

 <span data-ttu-id="35e4d-107">有意義且有用的抽象概念，能夠承受時間測試，並不容易設計。</span><span class="sxs-lookup"><span data-stu-id="35e4d-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="35e4d-108">主要的難題是取得正確的成員集合，而不是更少。</span><span class="sxs-lookup"><span data-stu-id="35e4d-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="35e4d-109">如果抽象概念有太多成員，就會變得很難或甚至無法執行。</span><span class="sxs-lookup"><span data-stu-id="35e4d-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="35e4d-110">如果其承諾的功能有太少的成員，則在許多有趣的案例中會變得毫無用處。</span><span class="sxs-lookup"><span data-stu-id="35e4d-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>

 <span data-ttu-id="35e4d-111">架構中有太多抽象概念也會對架構的可用性造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="35e4d-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="35e4d-112">您通常很難瞭解抽象概念，而不需要瞭解它如何融入具體的執行，以及在抽象概念上操作的 Api。</span><span class="sxs-lookup"><span data-stu-id="35e4d-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="35e4d-113">此外，抽象和其成員的名稱一定是抽象的，這通常會使它們變得更不容易 unapproachable，而不需要先瞭解其使用方式的更廣泛內容。</span><span class="sxs-lookup"><span data-stu-id="35e4d-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>

 <span data-ttu-id="35e4d-114">不過，抽象層提供非常強大的擴充性，其他擴充性機制通常不會符合。</span><span class="sxs-lookup"><span data-stu-id="35e4d-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="35e4d-115">它們是許多架構模式的核心，例如外掛程式、控制反轉（IoC）、管線等等。</span><span class="sxs-lookup"><span data-stu-id="35e4d-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="35e4d-116">它們對於架構的可測試性也非常重要。</span><span class="sxs-lookup"><span data-stu-id="35e4d-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="35e4d-117">良好的抽象概念可讓您針對單元測試的目的，將繁重的相依性 stub。</span><span class="sxs-lookup"><span data-stu-id="35e4d-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="35e4d-118">總而言之，抽象概念會負責各種現代化物件導向架構的豐富功能。</span><span class="sxs-lookup"><span data-stu-id="35e4d-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>

 <span data-ttu-id="35e4d-119">❌除非藉由開發數個具體的執行和使用抽象概念的 Api 進行測試，否則請不要提供抽象概念。</span><span class="sxs-lookup"><span data-stu-id="35e4d-119">❌ DO NOT provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>

 <span data-ttu-id="35e4d-120">在設計抽象概念時，✔️請在抽象類別和介面之間謹慎選擇。</span><span class="sxs-lookup"><span data-stu-id="35e4d-120">✔️ DO choose carefully between an abstract class and an interface when designing an abstraction.</span></span>

 <span data-ttu-id="35e4d-121">✔️考慮為抽象的具體執行提供參考測試。</span><span class="sxs-lookup"><span data-stu-id="35e4d-121">✔️ CONSIDER providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="35e4d-122">這類測試應允許使用者測試其執行是否正確地實作為合約。</span><span class="sxs-lookup"><span data-stu-id="35e4d-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>

 <span data-ttu-id="35e4d-123">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="35e4d-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="35e4d-124">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="35e4d-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="35e4d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35e4d-125">See also</span></span>

- [<span data-ttu-id="35e4d-126">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="35e4d-126">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="35e4d-127">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="35e4d-127">Designing for Extensibility</span></span>](designing-for-extensibility.md)
