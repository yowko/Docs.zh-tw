---
title: "密封"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39bb29d36b6d81464b1213ebc0bf7aee6ceb5713
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="sealing"></a><span data-ttu-id="173c1-102">密封</span><span class="sxs-lookup"><span data-stu-id="173c1-102">Sealing</span></span>
<span data-ttu-id="173c1-103">物件導向架構的功能之一是開發人員可以擴充並自訂架構設計人員所預期的方式。</span><span class="sxs-lookup"><span data-stu-id="173c1-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="173c1-104">這是設計的電源和可延伸的危險。</span><span class="sxs-lookup"><span data-stu-id="173c1-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="173c1-105">當您設計您的架構時，它是，因此，它需要時，小心設計擴充性，並限制危險時的擴充性非常重要。</span><span class="sxs-lookup"><span data-stu-id="173c1-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="173c1-106">強大的機制，可防止擴充性密封。</span><span class="sxs-lookup"><span data-stu-id="173c1-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="173c1-107">您可以密封類別或個別成員。</span><span class="sxs-lookup"><span data-stu-id="173c1-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="173c1-108">密封類別，可防止使用者從類別繼承。</span><span class="sxs-lookup"><span data-stu-id="173c1-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="173c1-109">密封成員可防止使用者覆寫特定成員。</span><span class="sxs-lookup"><span data-stu-id="173c1-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="173c1-110">**X 不**密封類別有充分的理由，若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="173c1-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="173c1-111">密封類別，因為您無法將擴充性案例不是很好的理由。</span><span class="sxs-lookup"><span data-stu-id="173c1-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="173c1-112">架構的使用者想要基於各種 nonobvious 原因的詳細資訊，例如新增方便成員繼承自類別。</span><span class="sxs-lookup"><span data-stu-id="173c1-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="173c1-113">請參閱[非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)nonobvious 原因的範例使用者想要繼承自型別。</span><span class="sxs-lookup"><span data-stu-id="173c1-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="173c1-114">密封類別的原因包括：</span><span class="sxs-lookup"><span data-stu-id="173c1-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="173c1-115">此類別是靜態的類別。</span><span class="sxs-lookup"><span data-stu-id="173c1-115">The class is a static class.</span></span> <span data-ttu-id="173c1-116">請參閱[靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)。</span><span class="sxs-lookup"><span data-stu-id="173c1-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="173c1-117">類別會繼承的 protected 成員中儲存機密的機密資料。</span><span class="sxs-lookup"><span data-stu-id="173c1-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="173c1-118">類別繼承許多虛擬成員，而且個別密封它們的成本會超過優點可能會留下未密封的類別。</span><span class="sxs-lookup"><span data-stu-id="173c1-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="173c1-119">此類別是需要非常快速的執行階段查閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="173c1-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="173c1-120">密封的屬性具有稍微較高的效能層級比未密封。</span><span class="sxs-lookup"><span data-stu-id="173c1-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="173c1-121">請參閱[屬性](../../../docs/standard/design-guidelines/attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="173c1-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="173c1-122">**X 不**在密封類型上宣告受保護或虛擬的成員。</span><span class="sxs-lookup"><span data-stu-id="173c1-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="173c1-123">根據定義，密封的類型無法繼承自中。</span><span class="sxs-lookup"><span data-stu-id="173c1-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="173c1-124">這表示無法呼叫密封類型上的受保護的成員，而且不能覆寫虛擬方法，密封類型上。</span><span class="sxs-lookup"><span data-stu-id="173c1-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="173c1-125">**✓ 考慮**密封您覆寫的成員。</span><span class="sxs-lookup"><span data-stu-id="173c1-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="173c1-126">可能是因為簡介虛擬成員的問題 (討論[虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)) 套用於覆寫，雖然稍微較低刻度。</span><span class="sxs-lookup"><span data-stu-id="173c1-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="173c1-127">密封覆寫保護不受影響您從該階層架構中的點開始這些問題。</span><span class="sxs-lookup"><span data-stu-id="173c1-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="173c1-128">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="173c1-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="173c1-129">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="173c1-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173c1-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="173c1-130">See Also</span></span>  
 [<span data-ttu-id="173c1-131">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="173c1-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="173c1-132">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="173c1-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="173c1-133">非密封類別</span><span class="sxs-lookup"><span data-stu-id="173c1-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
