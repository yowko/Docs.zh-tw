---
title: 成員設計方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1598ac63af38f1ca3e11104bc8e1cd6323d35ed
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871014"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="ad7bb-102">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="ad7bb-102">Member Design Guidelines</span></span>
<span data-ttu-id="ad7bb-103">方法、 屬性、 事件、 建構函式和欄位會統稱為成員。</span><span class="sxs-lookup"><span data-stu-id="ad7bb-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="ad7bb-104">成員是最後 framework 功能向終端使用者的一種架構的方法。</span><span class="sxs-lookup"><span data-stu-id="ad7bb-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="ad7bb-105">成員可以是虛擬或非虛擬、 實體或抽象的靜態或執行個體，而且可以有數個不同的範圍的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="ad7bb-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="ad7bb-106">所有的不同種類提供驚人的表達，但同時需要小心執行 framework 設計工具。</span><span class="sxs-lookup"><span data-stu-id="ad7bb-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="ad7bb-107">本章提供基本設計的任何型別成員時，應遵循的指導方針。</span><span class="sxs-lookup"><span data-stu-id="ad7bb-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad7bb-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="ad7bb-108">In This Section</span></span>  
 [<span data-ttu-id="ad7bb-109">成員多載</span><span class="sxs-lookup"><span data-stu-id="ad7bb-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="ad7bb-110">屬性設計</span><span class="sxs-lookup"><span data-stu-id="ad7bb-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="ad7bb-111">建構函式設計</span><span class="sxs-lookup"><span data-stu-id="ad7bb-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="ad7bb-112">事件設計</span><span class="sxs-lookup"><span data-stu-id="ad7bb-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="ad7bb-113">欄位設計</span><span class="sxs-lookup"><span data-stu-id="ad7bb-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="ad7bb-114">擴充方法</span><span class="sxs-lookup"><span data-stu-id="ad7bb-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="ad7bb-115">運算子多載</span><span class="sxs-lookup"><span data-stu-id="ad7bb-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="ad7bb-116">參數設計</span><span class="sxs-lookup"><span data-stu-id="ad7bb-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="ad7bb-117">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="ad7bb-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ad7bb-118">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="ad7bb-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7bb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad7bb-119">See also</span></span>

- [<span data-ttu-id="ad7bb-120">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="ad7bb-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
