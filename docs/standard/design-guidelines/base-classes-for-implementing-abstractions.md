---
title: 實作抽象的基底類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: KrzysztofCwalina
ms.openlocfilehash: 6811423258481fcbae24743c9b17f3f20c379c58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565809"
---
# <a name="base-classes-for-implementing-abstractions"></a><span data-ttu-id="04d48-102">實作抽象的基底類別</span><span class="sxs-lookup"><span data-stu-id="04d48-102">Base Classes for Implementing Abstractions</span></span>
<span data-ttu-id="04d48-103">嚴格來說，類別就變得基底類別衍生自此類別的另一個類別。</span><span class="sxs-lookup"><span data-stu-id="04d48-103">Strictly speaking, a class becomes a base class when another class is derived from it.</span></span> <span data-ttu-id="04d48-104">不過，為了本章節中，基底類別是設計主要是為了提供常見的抽象概念，或重複使用一些其他類別的預設實作透過繼承的類別。</span><span class="sxs-lookup"><span data-stu-id="04d48-104">For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance.</span></span> <span data-ttu-id="04d48-105">基底類別通常位於繼承階層架構，在階層的根的抽象概念與數個在底部的自訂實作之間的中間。</span><span class="sxs-lookup"><span data-stu-id="04d48-105">Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.</span></span>  
  
 <span data-ttu-id="04d48-106">它們可當做實作協助程式實作抽象的。</span><span class="sxs-lookup"><span data-stu-id="04d48-106">They serve as implementation helpers for implementing abstractions.</span></span> <span data-ttu-id="04d48-107">例如，其中一個項目的已排序集合的架構的抽象概念是<xref:System.Collections.Generic.IList%601>介面。</span><span class="sxs-lookup"><span data-stu-id="04d48-107">For example, one of the Framework’s abstractions for ordered collections of items is the <xref:System.Collections.Generic.IList%601> interface.</span></span> <span data-ttu-id="04d48-108">實作<xref:System.Collections.Generic.IList%601>並非易事，因此架構可提供數個基底類別，例如<xref:System.Collections.ObjectModel.Collection%601>和<xref:System.Collections.ObjectModel.KeyedCollection%602>，其中實作自訂的集合做為協助程式。</span><span class="sxs-lookup"><span data-stu-id="04d48-108">Implementing <xref:System.Collections.Generic.IList%601> is not trivial, and therefore the Framework provides several base classes, such as <xref:System.Collections.ObjectModel.Collection%601> and <xref:System.Collections.ObjectModel.KeyedCollection%602>, which serve as helpers for implementing custom collections.</span></span>  
  
 <span data-ttu-id="04d48-109">基底類別通常不適合作為抽象概念，本身，因為它們通常包含太多的實作。</span><span class="sxs-lookup"><span data-stu-id="04d48-109">Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation.</span></span> <span data-ttu-id="04d48-110">例如，`Collection<T>`基底類別包含許多相關的事實，它會實作非泛型實作`IList`介面 （若要整合更理想與非泛型集合），並實際上它是一組項目儲存在它的一個欄位中的記憶體。</span><span class="sxs-lookup"><span data-stu-id="04d48-110">For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.</span></span>  
  
 <span data-ttu-id="04d48-111">如先前所述，基底類別必須實作的抽象的使用者可以提供寶貴的說明，但同時也很重要的責任。</span><span class="sxs-lookup"><span data-stu-id="04d48-111">As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability.</span></span> <span data-ttu-id="04d48-112">它們加入介面區和增加的繼承階層架構的深度，以及因此在概念上會讓複雜的架構。</span><span class="sxs-lookup"><span data-stu-id="04d48-112">They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework.</span></span> <span data-ttu-id="04d48-113">因此，它們提供重大價值架構的使用者時，才應該使用基底類別。</span><span class="sxs-lookup"><span data-stu-id="04d48-113">Therefore, base classes should be used only if they provide significant value to the users of the framework.</span></span> <span data-ttu-id="04d48-114">它們應盡可能它們才能 framework 中，應該強烈考慮的內部實作，而不是繼承自基底類別的案例委派的實作，提供值。</span><span class="sxs-lookup"><span data-stu-id="04d48-114">They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.</span></span>  
  
 <span data-ttu-id="04d48-115">**✓ CONSIDER** 讓基底類別的抽象，即使它們不包含任何抽象成員。</span><span class="sxs-lookup"><span data-stu-id="04d48-115">**✓ CONSIDER** making base classes abstract even if they don’t contain any abstract members.</span></span> <span data-ttu-id="04d48-116">如此可清楚的使用者，該類別只可繼承自。</span><span class="sxs-lookup"><span data-stu-id="04d48-116">This clearly communicates to the users that the class is designed solely to be inherited from.</span></span>  
  
 <span data-ttu-id="04d48-117">**✓ CONSIDER** 置於不同的命名空間從主線情節類型的基底類別。</span><span class="sxs-lookup"><span data-stu-id="04d48-117">**✓ CONSIDER** placing base classes in a separate namespace from the mainline scenario types.</span></span> <span data-ttu-id="04d48-118">根據定義，基底類別適用的進階擴充性案例，因此不需要大部分的使用者。</span><span class="sxs-lookup"><span data-stu-id="04d48-118">By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.</span></span>  
  
 <span data-ttu-id="04d48-119">**X AVOID** 命名基底類別具有 「 基底"後置詞，如果類別是用於在公用 Api。</span><span class="sxs-lookup"><span data-stu-id="04d48-119">**X AVOID** naming base classes with a "Base" suffix if the class is intended for use in public APIs.</span></span>  
  
 <span data-ttu-id="04d48-120">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="04d48-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="04d48-121">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="04d48-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d48-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04d48-122">See also</span></span>

- [<span data-ttu-id="04d48-123">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="04d48-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="04d48-124">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="04d48-124">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
