---
title: 虛擬成員
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 22eb71ccfc1b9a3d359b0453e4ff47f3f41827f5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828396"
---
# <a name="virtual-members"></a><span data-ttu-id="3b813-102">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="3b813-102">Virtual Members</span></span>
<span data-ttu-id="3b813-103">您可以覆寫虛擬成員，進而變更子類別的行為。</span><span class="sxs-lookup"><span data-stu-id="3b813-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="3b813-104">它們在提供的擴充性方面相當類似回呼，但它們在執行效能和記憶體耗用量方面更好。</span><span class="sxs-lookup"><span data-stu-id="3b813-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="3b813-105">此外，在需要建立特殊種類的現有類型 (特製化) 的案例中，虛擬成員會覺得更自然。</span><span class="sxs-lookup"><span data-stu-id="3b813-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="3b813-106">虛擬成員的執行效能優於回呼和事件，但效能不如非虛擬方法更好。</span><span class="sxs-lookup"><span data-stu-id="3b813-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="3b813-107">虛擬成員的主要缺點是，只有在編譯時才能修改虛擬成員的行為。</span><span class="sxs-lookup"><span data-stu-id="3b813-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="3b813-108">回呼的行為可在執行時間修改。</span><span class="sxs-lookup"><span data-stu-id="3b813-108">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="3b813-109">虛擬成員（像是回呼 (以及可能超過回呼) ）在設計、測試和維護方面很昂貴，因為對虛擬成員的任何呼叫都可以無法預期地覆寫，而且可以執行任意程式碼。</span><span class="sxs-lookup"><span data-stu-id="3b813-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="3b813-110">此外，通常需要更多投入時間才能清楚定義虛擬成員的合約，因此設計和記錄這些成員的成本較高。</span><span class="sxs-lookup"><span data-stu-id="3b813-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="3b813-111">❌ 除非您有充分的理由，才能讓成員成為虛擬的，而且您知道設計、測試和維護虛擬成員的所有相關成本。</span><span class="sxs-lookup"><span data-stu-id="3b813-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="3b813-112">虛擬成員在變更方面較不容許，因為它們可以在不中斷相容性的情況下進行變更。</span><span class="sxs-lookup"><span data-stu-id="3b813-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="3b813-113">此外，它們的速度會比非虛擬成員還要慢，因為虛擬成員的呼叫不是內嵌的。</span><span class="sxs-lookup"><span data-stu-id="3b813-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="3b813-114">✔️考慮將擴充性限制為僅限絕對必要。</span><span class="sxs-lookup"><span data-stu-id="3b813-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="3b813-115">✔️在虛擬成員的公用存取範圍上，偏好受保護的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="3b813-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="3b813-116">如果需要) 呼叫受保護的虛擬成員，則公用成員應提供擴充性 (。</span><span class="sxs-lookup"><span data-stu-id="3b813-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="3b813-117">類別的公用成員應為該類別的直接取用者提供正確的一組功能。</span><span class="sxs-lookup"><span data-stu-id="3b813-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="3b813-118">虛擬成員是設計用來在子類別中覆寫，而受保護的存取範圍是將所有虛擬擴充功能的範圍設為可使用的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="3b813-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="3b813-119">*部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="3b813-119">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3b813-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="3b813-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3b813-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b813-121">See also</span></span>

- [<span data-ttu-id="3b813-122">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="3b813-122">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="3b813-123">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="3b813-123">Designing for Extensibility</span></span>](designing-for-extensibility.md)
