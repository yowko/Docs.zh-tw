---
title: 成員設計方針
description: 瞭解 .NET 中的成員設計方針。 成員包含方法、屬性、事件、函數和欄位。
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: 512fc3b7fde93279995a67be2fc0b285ba235f16
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820939"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="884dd-104">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="884dd-104">Member Design Guidelines</span></span>
<span data-ttu-id="884dd-105">方法、屬性、事件、函數和欄位統稱為成員。</span><span class="sxs-lookup"><span data-stu-id="884dd-105">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="884dd-106">成員最終是對架構的使用者公開架構功能的方法。</span><span class="sxs-lookup"><span data-stu-id="884dd-106">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="884dd-107">成員可以是虛擬或非虛擬、具體或抽象、靜態或實例，而且可以有數個不同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="884dd-107">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="884dd-108">這所有的各項都提供絕佳的表達，但同時需要注意架構設計工具的一部分。</span><span class="sxs-lookup"><span data-stu-id="884dd-108">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="884dd-109">本章提供在設計任何類型的成員時應遵循的基本指導方針。</span><span class="sxs-lookup"><span data-stu-id="884dd-109">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="884dd-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="884dd-110">In This Section</span></span>  
 [<span data-ttu-id="884dd-111">成員多載</span><span class="sxs-lookup"><span data-stu-id="884dd-111">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="884dd-112">屬性設計</span><span class="sxs-lookup"><span data-stu-id="884dd-112">Property Design</span></span>](property.md)  
 [<span data-ttu-id="884dd-113">設計函數設計</span><span class="sxs-lookup"><span data-stu-id="884dd-113">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="884dd-114">事件設計</span><span class="sxs-lookup"><span data-stu-id="884dd-114">Event Design</span></span>](event.md)  
 [<span data-ttu-id="884dd-115">欄位設計</span><span class="sxs-lookup"><span data-stu-id="884dd-115">Field Design</span></span>](field.md)  
 [<span data-ttu-id="884dd-116">擴充方法</span><span class="sxs-lookup"><span data-stu-id="884dd-116">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="884dd-117">運算子多載</span><span class="sxs-lookup"><span data-stu-id="884dd-117">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="884dd-118">參數設計</span><span class="sxs-lookup"><span data-stu-id="884dd-118">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="884dd-119">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="884dd-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="884dd-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="884dd-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="884dd-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="884dd-121">See also</span></span>

- [<span data-ttu-id="884dd-122">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="884dd-122">Framework Design Guidelines</span></span>](index.md)
