---
title: "擴充性設計"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbee2fb24b9acf9bc2512b399e3a74e66720cc3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="ee7c2-102">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="ee7c2-102">Designing for Extensibility</span></span>
<span data-ttu-id="ee7c2-103">設計一個架構的一個重要層面確保已仔細考慮架構的擴充性。</span><span class="sxs-lookup"><span data-stu-id="ee7c2-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="ee7c2-104">這需要您已了解的成本與利益各種擴充性機制相關聯。</span><span class="sxs-lookup"><span data-stu-id="ee7c2-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="ee7c2-105">本章節可協助您決定哪一個擴充性機制 — 子類別化、 事件、 虛擬成員、 回呼 (callback) 等等，可以最符合您的架構的需求。</span><span class="sxs-lookup"><span data-stu-id="ee7c2-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="ee7c2-106">有許多方法可允許擴充性架構中。</span><span class="sxs-lookup"><span data-stu-id="ee7c2-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="ee7c2-107">這些範圍較不強大，卻經濟的成本非常強大，但高度耗費資源。</span><span class="sxs-lookup"><span data-stu-id="ee7c2-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="ee7c2-108">對於任何給定的擴充性項需求，您應該選擇符合需求的最高擴充性機制。</span><span class="sxs-lookup"><span data-stu-id="ee7c2-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="ee7c2-109">請記住，若要加入更大的擴充，通常可以但是您可以永遠不會佔用它而不會引進重大變更。</span><span class="sxs-lookup"><span data-stu-id="ee7c2-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee7c2-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="ee7c2-110">In This Section</span></span>  
 [<span data-ttu-id="ee7c2-111">非密封的類別</span><span class="sxs-lookup"><span data-stu-id="ee7c2-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="ee7c2-112">受保護的成員</span><span class="sxs-lookup"><span data-stu-id="ee7c2-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="ee7c2-113">事件和回撥</span><span class="sxs-lookup"><span data-stu-id="ee7c2-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="ee7c2-114">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="ee7c2-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="ee7c2-115">抽象層 （抽象型別和介面）</span><span class="sxs-lookup"><span data-stu-id="ee7c2-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="ee7c2-116">實作抽象的基底類別</span><span class="sxs-lookup"><span data-stu-id="ee7c2-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="ee7c2-117">密封</span><span class="sxs-lookup"><span data-stu-id="ee7c2-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="ee7c2-118">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="ee7c2-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ee7c2-119">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="ee7c2-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee7c2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee7c2-120">See Also</span></span>  
 [<span data-ttu-id="ee7c2-121">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="ee7c2-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
