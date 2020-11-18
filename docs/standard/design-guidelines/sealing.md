---
title: 密封
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 29023ad431f9d05caf44e59f66eccee24bfa0433
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828682"
---
# <a name="sealing"></a><span data-ttu-id="46edf-102">密封</span><span class="sxs-lookup"><span data-stu-id="46edf-102">Sealing</span></span>
<span data-ttu-id="46edf-103">物件導向架構的其中一項功能，就是開發人員可以使用架構設計工具無法預期的方式來擴充和自訂它們。</span><span class="sxs-lookup"><span data-stu-id="46edf-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="46edf-104">這是可延伸設計的強大功能和風險。</span><span class="sxs-lookup"><span data-stu-id="46edf-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="46edf-105">當您設計您的架構時，請務必在需要時仔細設計擴充性，並且在具風險時限制擴充性。</span><span class="sxs-lookup"><span data-stu-id="46edf-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="46edf-106">防止擴充性的強大機制是密封的。</span><span class="sxs-lookup"><span data-stu-id="46edf-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="46edf-107">您可以密封類別或個別成員。</span><span class="sxs-lookup"><span data-stu-id="46edf-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="46edf-108">密封類別可防止使用者繼承自類別。</span><span class="sxs-lookup"><span data-stu-id="46edf-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="46edf-109">密封成員可以防止使用者覆寫特定的成員。</span><span class="sxs-lookup"><span data-stu-id="46edf-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="46edf-110">❌ 請勿密封類別，而不會有很好的理由。</span><span class="sxs-lookup"><span data-stu-id="46edf-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="46edf-111">密封類別是因為您不能認為擴充性案例不是好的原因。</span><span class="sxs-lookup"><span data-stu-id="46edf-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="46edf-112">基於各種 nonobvious 的原因（例如新增便利性成員），需要繼承類別的架構使用者。</span><span class="sxs-lookup"><span data-stu-id="46edf-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="46edf-113">請參閱未 [密封的類別](unsealed-classes.md) ，以取得使用者想要從類型繼承的 nonobvious 原因範例。</span><span class="sxs-lookup"><span data-stu-id="46edf-113">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="46edf-114">密封類別的好理由包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="46edf-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="46edf-115">類別是靜態類別。</span><span class="sxs-lookup"><span data-stu-id="46edf-115">The class is a static class.</span></span> <span data-ttu-id="46edf-116">請參閱 [靜態類別設計](static-class.md)。</span><span class="sxs-lookup"><span data-stu-id="46edf-116">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="46edf-117">類別會在繼承的受保護成員中儲存安全性機密秘密。</span><span class="sxs-lookup"><span data-stu-id="46edf-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="46edf-118">類別會繼承許多虛擬成員，而個別密封這些成員的成本，會超過將類別保持未密封的優點。</span><span class="sxs-lookup"><span data-stu-id="46edf-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="46edf-119">類別是需要非常快速的執行時間查閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="46edf-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="46edf-120">密封的屬性比未密封的屬性具有些許較高的效能層級。</span><span class="sxs-lookup"><span data-stu-id="46edf-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="46edf-121">請參閱 [屬性](attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="46edf-121">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="46edf-122">❌ 請勿在密封類型上宣告受保護的或虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="46edf-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="46edf-123">根據定義，密封類型無法繼承自。</span><span class="sxs-lookup"><span data-stu-id="46edf-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="46edf-124">這表示無法呼叫密封型別上的 protected 成員，也無法覆寫密封類型上的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="46edf-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="46edf-125">✔️考慮密封您覆寫的成員。</span><span class="sxs-lookup"><span data-stu-id="46edf-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="46edf-126"> (在 [虛擬成員](virtual-members.md) 中討論的虛擬成員引進的問題，也) 也適用于覆寫，不過稍微較低的程度。</span><span class="sxs-lookup"><span data-stu-id="46edf-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="46edf-127">密封覆寫會防止這些問題從繼承階層中的那個點開始。</span><span class="sxs-lookup"><span data-stu-id="46edf-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="46edf-128">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="46edf-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="46edf-129">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="46edf-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="46edf-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="46edf-130">See also</span></span>

- [<span data-ttu-id="46edf-131">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="46edf-131">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="46edf-132">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="46edf-132">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="46edf-133">未密封的類別</span><span class="sxs-lookup"><span data-stu-id="46edf-133">Unsealed Classes</span></span>](unsealed-classes.md)
