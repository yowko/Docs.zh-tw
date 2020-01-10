---
title: Framework 設計方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 623391de63891c1695a63482a424bb76a861deba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709305"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="e4721-102">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="e4721-102">Framework Design Guidelines</span></span>
<span data-ttu-id="e4721-103">本節提供設計程式庫的指導方針，這些程式庫會擴充 .NET Framework 並與之互動。</span><span class="sxs-lookup"><span data-stu-id="e4721-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="e4721-104">其目標是提供統一的程式設計模型，獨立于用於開發的程式設計語言，以協助程式庫設計人員確保 API 一致性和便於使用。</span><span class="sxs-lookup"><span data-stu-id="e4721-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="e4721-105">我們建議您在開發擴充 .NET Framework 的類別和元件時，遵循這些設計方針。</span><span class="sxs-lookup"><span data-stu-id="e4721-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="e4721-106">不一致的程式庫設計會對開發人員生產力和避免採用造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="e4721-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="e4721-107">這些指導方針會組織成前面加上 `Do`、`Consider`、`Avoid`和 `Do not`條款的簡單建議。</span><span class="sxs-lookup"><span data-stu-id="e4721-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="e4721-108">這些指導方針旨在協助類別庫設計人員瞭解不同解決方案之間的取捨。</span><span class="sxs-lookup"><span data-stu-id="e4721-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="e4721-109">在某些情況下，良好的程式庫設計會要求您違反這些設計方針。</span><span class="sxs-lookup"><span data-stu-id="e4721-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="e4721-110">這種情況應該很罕見，而且您一定要有清楚且引人注目的決策理由。</span><span class="sxs-lookup"><span data-stu-id="e4721-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="e4721-111">這些指導方針是從書籍*架構設計指導方針所摘錄自：可重複使用的 .net 程式庫第2版、Krzysztof Cwalina 和 Brad Abrams 的慣例、慣用語和模式*。</span><span class="sxs-lookup"><span data-stu-id="e4721-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4721-112">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e4721-112">In This Section</span></span>  
 [<span data-ttu-id="e4721-113">命名方針</span><span class="sxs-lookup"><span data-stu-id="e4721-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="e4721-114">提供在類別庫中命名元件、命名空間、類型和成員的指導方針。</span><span class="sxs-lookup"><span data-stu-id="e4721-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="e4721-115">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="e4721-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="e4721-116">提供使用靜態和抽象類別、介面、列舉、結構和其他類型的指導方針。</span><span class="sxs-lookup"><span data-stu-id="e4721-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="e4721-117">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="e4721-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="e4721-118">提供設計和使用屬性、方法、函式、欄位、事件、運算子和參數的指導方針。</span><span class="sxs-lookup"><span data-stu-id="e4721-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="e4721-119">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="e4721-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="e4721-120">討論擴充性機制，例如子類別化、使用事件、虛擬成員和回呼，並說明如何選擇最符合您架構需求的機制。</span><span class="sxs-lookup"><span data-stu-id="e4721-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="e4721-121">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="e4721-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="e4721-122">描述設計、擲回和攔截例外狀況的設計方針。</span><span class="sxs-lookup"><span data-stu-id="e4721-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="e4721-123">用法方針</span><span class="sxs-lookup"><span data-stu-id="e4721-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="e4721-124">描述使用一般類型的指導方針，例如陣列、屬性和集合、支援序列化和多載等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="e4721-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="e4721-125">一般設計模式</span><span class="sxs-lookup"><span data-stu-id="e4721-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="e4721-126">提供選擇和執行相依性屬性的指導方針。</span><span class="sxs-lookup"><span data-stu-id="e4721-126">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="e4721-127">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="e4721-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e4721-128">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="e4721-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4721-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4721-129">See also</span></span>

- [<span data-ttu-id="e4721-130">概觀</span><span class="sxs-lookup"><span data-stu-id="e4721-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="e4721-131">開發指南</span><span class="sxs-lookup"><span data-stu-id="e4721-131">Development Guide</span></span>](../../../docs/framework/development-guide.md)
