---
title: "成員設計方針"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5df4ad5f6c947d8b3bf62c3bf7eb8426419e5f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="member-design-guidelines"></a><span data-ttu-id="46136-102">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="46136-102">Member Design Guidelines</span></span>
<span data-ttu-id="46136-103">方法、 屬性、 事件、 建構函式，以及欄位統稱為成員。</span><span class="sxs-lookup"><span data-stu-id="46136-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="46136-104">成員是最終 framework 功能向架構的使用者。</span><span class="sxs-lookup"><span data-stu-id="46136-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="46136-105">成員可以是虛擬或非虛擬、 實體或 abstract、 靜態或執行個體，且可以存取範圍的數個不同的範圍。</span><span class="sxs-lookup"><span data-stu-id="46136-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="46136-106">所有此各種提供驚人表達，但同時需要小心內容架構的設計工具上。</span><span class="sxs-lookup"><span data-stu-id="46136-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="46136-107">此章節提供基本設計的任何類型的成員時，應遵循的指導方針。</span><span class="sxs-lookup"><span data-stu-id="46136-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46136-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="46136-108">In This Section</span></span>  
 [<span data-ttu-id="46136-109">多載成員</span><span class="sxs-lookup"><span data-stu-id="46136-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="46136-110">屬性的設計</span><span class="sxs-lookup"><span data-stu-id="46136-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="46136-111">建構函式設計</span><span class="sxs-lookup"><span data-stu-id="46136-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="46136-112">事件設計</span><span class="sxs-lookup"><span data-stu-id="46136-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="46136-113">欄位設計</span><span class="sxs-lookup"><span data-stu-id="46136-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="46136-114">擴充方法</span><span class="sxs-lookup"><span data-stu-id="46136-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="46136-115">運算子多載</span><span class="sxs-lookup"><span data-stu-id="46136-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="46136-116">參數設計</span><span class="sxs-lookup"><span data-stu-id="46136-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="46136-117">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="46136-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="46136-118">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="46136-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46136-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46136-119">See Also</span></span>  
 [<span data-ttu-id="46136-120">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="46136-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
