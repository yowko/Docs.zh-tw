---
title: "實作抽象的基底類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c8cd779dba0e7ce559e29af7b16bf04b3d0dc2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="base-classes-for-implementing-abstractions"></a><span data-ttu-id="1be21-102">實作抽象的基底類別</span><span class="sxs-lookup"><span data-stu-id="1be21-102">Base Classes for Implementing Abstractions</span></span>
<span data-ttu-id="1be21-103">嚴格來說，當另一個類別會從其衍生類別成為基底類別。</span><span class="sxs-lookup"><span data-stu-id="1be21-103">Strictly speaking, a class becomes a base class when another class is derived from it.</span></span> <span data-ttu-id="1be21-104">不過，為了本節中，基底類別是主要設計成提供的通用抽象概念，或重複使用一些其他類別的預設實作透過繼承的類別。</span><span class="sxs-lookup"><span data-stu-id="1be21-104">For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance.</span></span> <span data-ttu-id="1be21-105">繼承階層架構的抽象概念，在階層的根和數個在底部的自訂實作之間的中間通常坐基底類別。</span><span class="sxs-lookup"><span data-stu-id="1be21-105">Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.</span></span>  
  
 <span data-ttu-id="1be21-106">它們會充當實作 helper 實作抽象的。</span><span class="sxs-lookup"><span data-stu-id="1be21-106">They serve as implementation helpers for implementing abstractions.</span></span> <span data-ttu-id="1be21-107">例如，其中一個項目的已排序集合的架構的抽象概念是<xref:System.Collections.Generic.IList%601>介面。</span><span class="sxs-lookup"><span data-stu-id="1be21-107">For example, one of the Framework’s abstractions for ordered collections of items is the <xref:System.Collections.Generic.IList%601> interface.</span></span> <span data-ttu-id="1be21-108">實作<xref:System.Collections.Generic.IList%601>並非易事，並因此架構提供數個基底類別，例如<xref:System.Collections.ObjectModel.Collection%601>和<xref:System.Collections.ObjectModel.KeyedCollection%602>，其做為 helper 實作自訂的集合。</span><span class="sxs-lookup"><span data-stu-id="1be21-108">Implementing <xref:System.Collections.Generic.IList%601> is not trivial, and therefore the Framework provides several base classes, such as <xref:System.Collections.ObjectModel.Collection%601> and <xref:System.Collections.ObjectModel.KeyedCollection%602>, which serve as helpers for implementing custom collections.</span></span>  
  
 <span data-ttu-id="1be21-109">基底類別通常不適合作為抽象本身，因為它們通常包含太多的實作。</span><span class="sxs-lookup"><span data-stu-id="1be21-109">Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation.</span></span> <span data-ttu-id="1be21-110">例如，`Collection<T>`基底類別包含許多相關的事實，它會實作非泛型實作`IList`介面 （若要進一步整合非泛型集合），並在於它是集合的項目儲存在其中一個欄位中的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1be21-110">For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.</span></span>  
  
 <span data-ttu-id="1be21-111">如先前所討論，基底類別必須實作的抽象概念的使用者可以提供有用的說明，但它們可以同時是重大的負擔。</span><span class="sxs-lookup"><span data-stu-id="1be21-111">As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability.</span></span> <span data-ttu-id="1be21-112">它們加入介面區和增加的繼承階層架構的深度，以及因此在概念上使得架構。</span><span class="sxs-lookup"><span data-stu-id="1be21-112">They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework.</span></span> <span data-ttu-id="1be21-113">因此，它們提供重大價值架構的使用者，才應該使用基底類別。</span><span class="sxs-lookup"><span data-stu-id="1be21-113">Therefore, base classes should be used only if they provide significant value to the users of the framework.</span></span> <span data-ttu-id="1be21-114">它們應該避免如果它們的 framework，應強視為案例委派的內部實作，而非繼承自基底類別實作器，才能提供的值。</span><span class="sxs-lookup"><span data-stu-id="1be21-114">They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.</span></span>  
  
 <span data-ttu-id="1be21-115">**✓ 考慮**讓基底類別的抽象，即使它們不包含任何抽象成員。</span><span class="sxs-lookup"><span data-stu-id="1be21-115">**✓ CONSIDER** making base classes abstract even if they don’t contain any abstract members.</span></span> <span data-ttu-id="1be21-116">如此可清楚的使用者，此類別的設計只是要繼承自。</span><span class="sxs-lookup"><span data-stu-id="1be21-116">This clearly communicates to the users that the class is designed solely to be inherited from.</span></span>  
  
 <span data-ttu-id="1be21-117">**✓ 考慮**置於不同的命名空間從主線情節類型的基底類別。</span><span class="sxs-lookup"><span data-stu-id="1be21-117">**✓ CONSIDER** placing base classes in a separate namespace from the mainline scenario types.</span></span> <span data-ttu-id="1be21-118">根據定義，基底類別是針對進階的擴充性情節，因此無法興趣大部分的使用者。</span><span class="sxs-lookup"><span data-stu-id="1be21-118">By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.</span></span>  
  
 <span data-ttu-id="1be21-119">**請避免 x**命名基底類別具有 「 基底"後置詞，如果類別是用於在公用 Api。</span><span class="sxs-lookup"><span data-stu-id="1be21-119">**X AVOID** naming base classes with a "Base" suffix if the class is intended for use in public APIs.</span></span>  
  
 <span data-ttu-id="1be21-120">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1be21-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1be21-121">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="1be21-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be21-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1be21-122">See Also</span></span>  
 [<span data-ttu-id="1be21-123">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="1be21-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="1be21-124">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="1be21-124">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
