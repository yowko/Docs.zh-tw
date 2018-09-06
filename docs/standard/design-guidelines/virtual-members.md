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
ms.openlocfilehash: b92b648e7886fb0214238e32eacae2870b470340
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892794"
---
# <a name="virtual-members"></a><span data-ttu-id="f757f-102">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="f757f-102">Virtual Members</span></span>
<span data-ttu-id="f757f-103">虛擬成員可以被覆寫，因此變更子類別的行為。</span><span class="sxs-lookup"><span data-stu-id="f757f-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="f757f-104">它們是回呼提供，擴充性方面相當類似，但它們會有較高的執行效能和記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="f757f-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="f757f-105">此外，虛擬成員覺得在需要建立一種特殊種類的現有類型 （特製化） 的情況下更自然的。</span><span class="sxs-lookup"><span data-stu-id="f757f-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="f757f-106">虛擬成員會優於回呼和事件，但不是會被執行優於非虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="f757f-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="f757f-107">虛擬成員的主要缺點是只可以在編譯時修改虛擬成員的行為。</span><span class="sxs-lookup"><span data-stu-id="f757f-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="f757f-108">回呼的行為可以在執行階段修改。</span><span class="sxs-lookup"><span data-stu-id="f757f-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="f757f-109">虛擬成員，例如回呼 （和可能有多個回呼），是設計、 測試及維護，因為虛擬成員的任何呼叫可以覆寫非預期的方式，而且可以執行任意程式碼的成本。</span><span class="sxs-lookup"><span data-stu-id="f757f-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="f757f-110">此外，更多精力通常需要清楚定義的虛擬成員的合約，讓設計與記錄它們的成本較高。</span><span class="sxs-lookup"><span data-stu-id="f757f-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="f757f-111">**X DO NOT** 讓成員虛擬，除非您有很好的理由，若要這樣做，而且您了解所有設計、 測試及維護虛擬成員與相關的成本。</span><span class="sxs-lookup"><span data-stu-id="f757f-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="f757f-112">虛擬成員會較少能夠容許方面可以對它們而不會中斷相容性的變更。</span><span class="sxs-lookup"><span data-stu-id="f757f-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="f757f-113">此外，也就是低於非虛擬成員，這多半是因為呼叫虛擬成員不會內嵌。</span><span class="sxs-lookup"><span data-stu-id="f757f-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="f757f-114">**✓ CONSIDER** 限制只是絕對必要的擴充性。</span><span class="sxs-lookup"><span data-stu-id="f757f-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="f757f-115">**✓ DO** 不用公用存取範圍中的受保護的存取範圍，在虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="f757f-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="f757f-116">Public 成員應該提供擴充性 （如有必要） 藉由呼叫受保護的虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="f757f-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="f757f-117">類別的 public 成員應該為該類別的直接取用者提供正確的功能集。</span><span class="sxs-lookup"><span data-stu-id="f757f-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="f757f-118">虛擬成員設計用來覆寫子類別，在和受保護的存取範圍是範圍可以要使用的所有虛擬擴充性點的好方法。</span><span class="sxs-lookup"><span data-stu-id="f757f-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="f757f-119">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="f757f-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f757f-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="f757f-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f757f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f757f-121">See also</span></span>

- [<span data-ttu-id="f757f-122">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="f757f-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="f757f-123">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="f757f-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
