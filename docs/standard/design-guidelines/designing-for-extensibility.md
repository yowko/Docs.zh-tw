---
title: 擴充性設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697525"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="1c0c4-102">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="1c0c4-102">Designing for Extensibility</span></span>
<span data-ttu-id="1c0c4-103">設計一套架構的一個重要層面確保已仔細考慮擴充性的 framework。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="1c0c4-104">這需要您了解各種擴充性機制相關聯的優點與成本。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="1c0c4-105">此章節可協助您決定哪一種的擴充性機制，子類別化、 事件、 虛擬成員、 回呼和等等 — 可以最符合您的架構需求。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="1c0c4-106">有許多方法可允許擴充性架構中。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="1c0c4-107">它們範圍權力較小，但成本更低但昂貴的功能非常強大。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="1c0c4-108">任何指定的擴充性需求，您應該選擇符合需求的最低成本高擴充性機制。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="1c0c4-109">請記住，通常可以稍後新增更多的擴充性，但您絕對不能它立即且不會造成重大變更。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c0c4-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="1c0c4-110">In This Section</span></span>  
 [<span data-ttu-id="1c0c4-111">非密封類別</span><span class="sxs-lookup"><span data-stu-id="1c0c4-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="1c0c4-112">Protected 成員</span><span class="sxs-lookup"><span data-stu-id="1c0c4-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="1c0c4-113">事件和回呼</span><span class="sxs-lookup"><span data-stu-id="1c0c4-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="1c0c4-114">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="1c0c4-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="1c0c4-115">抽象 (抽象類型和介面)</span><span class="sxs-lookup"><span data-stu-id="1c0c4-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="1c0c4-116">實作抽象的基底類別</span><span class="sxs-lookup"><span data-stu-id="1c0c4-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="1c0c4-117">密封</span><span class="sxs-lookup"><span data-stu-id="1c0c4-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="1c0c4-118">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1c0c4-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1c0c4-119">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="1c0c4-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0c4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c0c4-120">See also</span></span>

- [<span data-ttu-id="1c0c4-121">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="1c0c4-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
