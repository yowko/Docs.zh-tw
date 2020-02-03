---
title: 實作抽象的基底類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: b22923338f8488b6f7684e565f62d9afc16e6aa0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741775"
---
# <a name="base-classes-for-implementing-abstractions"></a><span data-ttu-id="49eaf-102">實作抽象的基底類別</span><span class="sxs-lookup"><span data-stu-id="49eaf-102">Base Classes for Implementing Abstractions</span></span>
<span data-ttu-id="49eaf-103">嚴格來說，當另一個類別衍生自它時，類別會變成基類。</span><span class="sxs-lookup"><span data-stu-id="49eaf-103">Strictly speaking, a class becomes a base class when another class is derived from it.</span></span> <span data-ttu-id="49eaf-104">不過，就本節的目的而言，基類是主要設計來提供通用抽象概念或其他類別的類別，以便在繼承時重複使用一些預設的執行。</span><span class="sxs-lookup"><span data-stu-id="49eaf-104">For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance.</span></span> <span data-ttu-id="49eaf-105">基類通常位於繼承階層的中間，在階層根目錄的抽象概念和底部的數個自訂實體系之間。</span><span class="sxs-lookup"><span data-stu-id="49eaf-105">Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.</span></span>

 <span data-ttu-id="49eaf-106">它們做為執行抽象概念的執行協助程式。</span><span class="sxs-lookup"><span data-stu-id="49eaf-106">They serve as implementation helpers for implementing abstractions.</span></span> <span data-ttu-id="49eaf-107">例如，已排序之專案集合的其中一個架構抽象層是 <xref:System.Collections.Generic.IList%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="49eaf-107">For example, one of the Framework’s abstractions for ordered collections of items is the <xref:System.Collections.Generic.IList%601> interface.</span></span> <span data-ttu-id="49eaf-108">執行 <xref:System.Collections.Generic.IList%601> 並不簡單，因此架構會提供數種基類，例如 <xref:System.Collections.ObjectModel.Collection%601> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602>，做為協助程式來執行自訂集合。</span><span class="sxs-lookup"><span data-stu-id="49eaf-108">Implementing <xref:System.Collections.Generic.IList%601> is not trivial, and therefore the Framework provides several base classes, such as <xref:System.Collections.ObjectModel.Collection%601> and <xref:System.Collections.ObjectModel.KeyedCollection%602>, which serve as helpers for implementing custom collections.</span></span>

 <span data-ttu-id="49eaf-109">基類通常不適合做為抽象概念，因為它們可能包含太多的執行。</span><span class="sxs-lookup"><span data-stu-id="49eaf-109">Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation.</span></span> <span data-ttu-id="49eaf-110">例如，`Collection<T>` 基類包含許多與執行非泛型 `IList` 介面的事實相關的實做（以更好的方式與非泛型集合整合），以及它是儲存在其中一個欄位之記憶體中的專案集合。</span><span class="sxs-lookup"><span data-stu-id="49eaf-110">For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.</span></span>

 <span data-ttu-id="49eaf-111">如先前所討論，基類可以為需要執行抽象概念的使用者提供寶貴的協助，但同時也可能會造成嚴重的責任。</span><span class="sxs-lookup"><span data-stu-id="49eaf-111">As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability.</span></span> <span data-ttu-id="49eaf-112">他們會加入介面區並增加繼承階層的深度，因此概念上會使架構複雜化。</span><span class="sxs-lookup"><span data-stu-id="49eaf-112">They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework.</span></span> <span data-ttu-id="49eaf-113">因此，只有當基類為架構的使用者提供顯著的價值時，才應該使用這些類別。</span><span class="sxs-lookup"><span data-stu-id="49eaf-113">Therefore, base classes should be used only if they provide significant value to the users of the framework.</span></span> <span data-ttu-id="49eaf-114">如果它們只提供值給架構的實作者，就應該避免這些情況，在此情況下，委派到內部執行，而不是從基類繼承。</span><span class="sxs-lookup"><span data-stu-id="49eaf-114">They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.</span></span>

 <span data-ttu-id="49eaf-115">✔️請考慮將基類設為抽象，即使它們未包含任何抽象成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="49eaf-115">✔️ CONSIDER making base classes abstract even if they don’t contain any abstract members.</span></span> <span data-ttu-id="49eaf-116">這會清楚地傳達類別設計為繼承自的使用者。</span><span class="sxs-lookup"><span data-stu-id="49eaf-116">This clearly communicates to the users that the class is designed solely to be inherited from.</span></span>

 <span data-ttu-id="49eaf-117">✔️考慮將基類放在主線案例類型的個別命名空間中。</span><span class="sxs-lookup"><span data-stu-id="49eaf-117">✔️ CONSIDER placing base classes in a separate namespace from the mainline scenario types.</span></span> <span data-ttu-id="49eaf-118">根據定義，基類適用于先進的擴充性案例，因此不會對大多數的使用者感興趣。</span><span class="sxs-lookup"><span data-stu-id="49eaf-118">By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.</span></span>

 <span data-ttu-id="49eaf-119">如果類別是要在公用 Api 中使用，❌ 避免以「基底」尾碼命名基類。</span><span class="sxs-lookup"><span data-stu-id="49eaf-119">❌ AVOID naming base classes with a "Base" suffix if the class is intended for use in public APIs.</span></span>

 <span data-ttu-id="49eaf-120">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="49eaf-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="49eaf-121">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="49eaf-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="49eaf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49eaf-122">See also</span></span>

- [<span data-ttu-id="49eaf-123">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="49eaf-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="49eaf-124">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="49eaf-124">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
