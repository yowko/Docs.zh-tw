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
ms.openlocfilehash: 406c15b6ce42b637ed1bbb61761d05e040995579
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280240"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="b4af5-102">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="b4af5-102">Designing for Extensibility</span></span>
<span data-ttu-id="b4af5-103">設計架構的其中一個重要層面，就是確定已仔細考慮架構的擴充性。</span><span class="sxs-lookup"><span data-stu-id="b4af5-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="b4af5-104">這需要您瞭解與各種擴充性機制相關聯的成本和優點。</span><span class="sxs-lookup"><span data-stu-id="b4af5-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="b4af5-105">這一章可協助您決定哪些擴充性機制（子類別、事件、虛擬成員、回呼等等）最符合您的架構需求。</span><span class="sxs-lookup"><span data-stu-id="b4af5-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="b4af5-106">有許多方法可讓您在架構中提供擴充性。</span><span class="sxs-lookup"><span data-stu-id="b4af5-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="b4af5-107">其範圍從較不強大，但成本較低，但成本低廉。</span><span class="sxs-lookup"><span data-stu-id="b4af5-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="b4af5-108">針對任何指定的擴充性需求，您應該選擇符合需求的成本最低的擴充性機制。</span><span class="sxs-lookup"><span data-stu-id="b4af5-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="b4af5-109">請記住，稍後可能會加入更多擴充性，但您永遠不會在不引入重大變更的情況下將它移開。</span><span class="sxs-lookup"><span data-stu-id="b4af5-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4af5-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="b4af5-110">In This Section</span></span>  
 [<span data-ttu-id="b4af5-111">未密封的類別</span><span class="sxs-lookup"><span data-stu-id="b4af5-111">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="b4af5-112">受保護的成員</span><span class="sxs-lookup"><span data-stu-id="b4af5-112">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="b4af5-113">事件和回呼</span><span class="sxs-lookup"><span data-stu-id="b4af5-113">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="b4af5-114">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="b4af5-114">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="b4af5-115">抽象（抽象類別型和介面）</span><span class="sxs-lookup"><span data-stu-id="b4af5-115">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="b4af5-116">用來執行抽象概念的基類</span><span class="sxs-lookup"><span data-stu-id="b4af5-116">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="b4af5-117">密封</span><span class="sxs-lookup"><span data-stu-id="b4af5-117">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="b4af5-118">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="b4af5-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b4af5-119">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="b4af5-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4af5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4af5-120">See also</span></span>

- [<span data-ttu-id="b4af5-121">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="b4af5-121">Framework Design Guidelines</span></span>](index.md)
