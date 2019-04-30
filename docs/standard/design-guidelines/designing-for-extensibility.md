---
title: 擴充性設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: KrzysztofCwalina
ms.openlocfilehash: 94900dee72230a1b9d099d78168acc508af62af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026454"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="a6d1f-102">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="a6d1f-102">Designing for Extensibility</span></span>
<span data-ttu-id="a6d1f-103">設計一套架構的一個重要層面確保已仔細考慮擴充性的 framework。</span><span class="sxs-lookup"><span data-stu-id="a6d1f-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="a6d1f-104">這需要您了解各種擴充性機制相關聯的優點與成本。</span><span class="sxs-lookup"><span data-stu-id="a6d1f-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="a6d1f-105">此章節可協助您決定哪一種的擴充性機制，子類別化、 事件、 虛擬成員、 回呼和等等 — 可以最符合您的架構需求。</span><span class="sxs-lookup"><span data-stu-id="a6d1f-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="a6d1f-106">有許多方法可允許擴充性架構中。</span><span class="sxs-lookup"><span data-stu-id="a6d1f-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="a6d1f-107">它們範圍權力較小，但成本更低但昂貴的功能非常強大。</span><span class="sxs-lookup"><span data-stu-id="a6d1f-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="a6d1f-108">任何指定的擴充性需求，您應該選擇符合需求的最低成本高擴充性機制。</span><span class="sxs-lookup"><span data-stu-id="a6d1f-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="a6d1f-109">請記住，通常可以稍後新增更多的擴充性，但您絕對不能它立即且不會造成重大變更。</span><span class="sxs-lookup"><span data-stu-id="a6d1f-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6d1f-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="a6d1f-110">In This Section</span></span>  
 [<span data-ttu-id="a6d1f-111">非密封類別</span><span class="sxs-lookup"><span data-stu-id="a6d1f-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="a6d1f-112">Protected 成員</span><span class="sxs-lookup"><span data-stu-id="a6d1f-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="a6d1f-113">事件和回呼</span><span class="sxs-lookup"><span data-stu-id="a6d1f-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="a6d1f-114">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="a6d1f-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="a6d1f-115">抽象 (抽象類型和介面)</span><span class="sxs-lookup"><span data-stu-id="a6d1f-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="a6d1f-116">實作抽象的基底類別</span><span class="sxs-lookup"><span data-stu-id="a6d1f-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="a6d1f-117">密封</span><span class="sxs-lookup"><span data-stu-id="a6d1f-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="a6d1f-118">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="a6d1f-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a6d1f-119">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="a6d1f-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6d1f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d1f-120">See also</span></span>

- [<span data-ttu-id="a6d1f-121">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="a6d1f-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
