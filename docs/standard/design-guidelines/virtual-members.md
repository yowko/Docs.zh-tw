---
title: 虛擬成員
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa4227fc4476b86f07216650b22fccc25af7dd98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573083"
---
# <a name="virtual-members"></a><span data-ttu-id="2c0e6-102">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="2c0e6-102">Virtual Members</span></span>
<span data-ttu-id="2c0e6-103">虛擬成員會覆寫，因此變更子類別的行為。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="2c0e6-104">它們是回呼提供，擴充性方面相當類似，但是可以執行效能和記憶體耗用量方面更好。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="2c0e6-105">此外，虛擬成員感覺更自然的案例中，需要建立一個特殊種類的現有類型 （特製化）。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="2c0e6-106">虛擬成員的執行效能優於回撥和事件，但不是執行效能優於非虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="2c0e6-107">虛擬成員的主要缺點是虛擬成員的行為只發生在編譯階段中變更。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="2c0e6-108">回呼的行為可以在執行階段修改。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="2c0e6-109">虛擬成員，例如回呼，可能有多個回呼成本很高設計、 測試和維護，因為任何呼叫虛擬成員會覆寫非預期的方式，而且可以執行任意程式碼。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="2c0e6-110">此外，還要更多的投入時間通常才能清楚地定義合約的虛擬成員，讓設計和撰寫它們的成本較高者為。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="2c0e6-111">**X 不**讓成員虛擬，除非您有很好的理由，若要這樣做，而且您了解所有設計、 測試及維護虛擬成員與相關的成本。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="2c0e6-112">虛擬成員都是較少能夠容許方面可能會對它們而不會中斷相容性的變更。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="2c0e6-113">此外，它們不低於非虛擬的成員，主要是因為不是內嵌的虛擬成員的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="2c0e6-114">**✓ 考慮**限制只是絕對必要的擴充性。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="2c0e6-115">**✓ 不要**不用公用存取範圍中的受保護的存取範圍，在虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="2c0e6-116">Public 成員應該提供擴充性 （如有必要） 藉由呼叫受保護的虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="2c0e6-117">類別的 public 成員應該提供正確的功能集，該類別的直接取用者。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="2c0e6-118">虛擬成員設計用來覆寫中的子類別，以及受保護的存取範圍是領域可以要使用的所有虛擬擴充性點的好方法。</span><span class="sxs-lookup"><span data-stu-id="2c0e6-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="2c0e6-119">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="2c0e6-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2c0e6-120">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="2c0e6-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0e6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c0e6-121">See Also</span></span>  
 [<span data-ttu-id="2c0e6-122">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="2c0e6-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="2c0e6-123">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="2c0e6-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
