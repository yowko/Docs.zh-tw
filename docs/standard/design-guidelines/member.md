---
title: 成員設計方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: c323e7edd752a1f003bd3f5d81689aca0eaefd20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288988"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="af283-102">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="af283-102">Member Design Guidelines</span></span>
<span data-ttu-id="af283-103">方法、屬性、事件、函數和欄位統稱為成員。</span><span class="sxs-lookup"><span data-stu-id="af283-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="af283-104">成員最終是對架構的使用者公開架構功能的方式。</span><span class="sxs-lookup"><span data-stu-id="af283-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="af283-105">成員可以是 virtual 或非虛擬、具體或抽象、靜態或實例，而且可以有數個不同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="af283-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="af283-106">這一切都能提供驚人的表達，但同時需要特別注意架構設計工具的一部分。</span><span class="sxs-lookup"><span data-stu-id="af283-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="af283-107">本章提供在設計任何類型的成員時應遵循的基本方針。</span><span class="sxs-lookup"><span data-stu-id="af283-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af283-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="af283-108">In This Section</span></span>  
 [<span data-ttu-id="af283-109">成員多載</span><span class="sxs-lookup"><span data-stu-id="af283-109">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="af283-110">屬性設計</span><span class="sxs-lookup"><span data-stu-id="af283-110">Property Design</span></span>](property.md)  
 [<span data-ttu-id="af283-111">函數設計</span><span class="sxs-lookup"><span data-stu-id="af283-111">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="af283-112">事件設計</span><span class="sxs-lookup"><span data-stu-id="af283-112">Event Design</span></span>](event.md)  
 [<span data-ttu-id="af283-113">欄位設計</span><span class="sxs-lookup"><span data-stu-id="af283-113">Field Design</span></span>](field.md)  
 [<span data-ttu-id="af283-114">擴充方法</span><span class="sxs-lookup"><span data-stu-id="af283-114">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="af283-115">運算子多載</span><span class="sxs-lookup"><span data-stu-id="af283-115">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="af283-116">參數設計</span><span class="sxs-lookup"><span data-stu-id="af283-116">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="af283-117">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="af283-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="af283-118">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="af283-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af283-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af283-119">See also</span></span>

- [<span data-ttu-id="af283-120">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="af283-120">Framework Design Guidelines</span></span>](index.md)
