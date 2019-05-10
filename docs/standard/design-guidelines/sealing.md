---
title: 密封
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: f25573c0fef29ef54dc04c5287757903429d89d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615206"
---
# <a name="sealing"></a><span data-ttu-id="7a6b0-102">密封</span><span class="sxs-lookup"><span data-stu-id="7a6b0-102">Sealing</span></span>
<span data-ttu-id="7a6b0-103">物件導向的架構功能之一是開發人員可以擴充並自訂它們以非預期的架構設計人員的方式。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="7a6b0-104">這是設計的電源和可延伸的危險。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="7a6b0-105">當您設計您的架構時，它，因此它是時需要它，則應該仔細設計擴充性，以及限制擴充性，會有問題時非常重要。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="7a6b0-106">功能強大的機制，以防止擴充性密封。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="7a6b0-107">您可以密封類別或個別成員。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="7a6b0-108">密封類別，可防止使用者從類別繼承。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="7a6b0-109">密封的成員，可防止使用者覆寫特定成員。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="7a6b0-110">**X DO NOT** 密封類別有充分的理由，若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="7a6b0-111">密封類別，因為您無法將擴充性案例，不是好的理由。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="7a6b0-112">Framework 使用者想要基於各種 nonobvious 原因的詳細資訊，例如新增方便成員繼承自類別。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="7a6b0-113">請參閱[非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)nonobvious 原因，例如使用者想要繼承自型別。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="7a6b0-114">很好的理由，用於密封類別包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="7a6b0-114">Good reasons for sealing a class include the following:</span></span>  
  
- <span data-ttu-id="7a6b0-115">類別是靜態類別。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-115">The class is a static class.</span></span> <span data-ttu-id="7a6b0-116">請參閱[靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
- <span data-ttu-id="7a6b0-117">此類別會繼承的 protected 成員中儲存安全性敏感密碼。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
- <span data-ttu-id="7a6b0-118">類別繼承許多虛擬成員，而且個別密封它們的成本會超過保留的未密封的類別的優點。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
- <span data-ttu-id="7a6b0-119">此類別是需要非常快速的執行階段查閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="7a6b0-120">密封的屬性會有較高的效能層級，於未密封的。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="7a6b0-121">請參閱[屬性](../../../docs/standard/design-guidelines/attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="7a6b0-122">**X DO NOT** 在密封類型上宣告受保護或虛擬的成員。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="7a6b0-123">根據定義，密封的類型無法繼承自。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="7a6b0-124">這表示無法呼叫密封類型上的受保護的成員，而且不能覆寫虛擬方法，密封類型上。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="7a6b0-125">**✓ CONSIDER** 密封您覆寫的成員。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="7a6b0-126">可能是因為引進虛擬成員的問題 (所述[虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)) 套用至覆寫，雖然到稍微較低的程度。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="7a6b0-127">密封覆寫保護您抵禦繼承階層架構中的該點開始這些問題。</span><span class="sxs-lookup"><span data-stu-id="7a6b0-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="7a6b0-128">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="7a6b0-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7a6b0-129">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="7a6b0-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6b0-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a6b0-130">See also</span></span>

- [<span data-ttu-id="7a6b0-131">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="7a6b0-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="7a6b0-132">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="7a6b0-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="7a6b0-133">非密封類別</span><span class="sxs-lookup"><span data-stu-id="7a6b0-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
