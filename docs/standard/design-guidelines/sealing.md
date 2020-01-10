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
ms.openlocfilehash: 0920ea26b94d86b41f8ba9338f3ec19f9bc099e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709084"
---
# <a name="sealing"></a><span data-ttu-id="f18f5-102">密封</span><span class="sxs-lookup"><span data-stu-id="f18f5-102">Sealing</span></span>
<span data-ttu-id="f18f5-103">物件導向架構的其中一項功能，就是開發人員可以利用 framework 設計工具無法預期的方式來擴充和自訂它們。</span><span class="sxs-lookup"><span data-stu-id="f18f5-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="f18f5-104">這同時也是可擴充設計的威力和危險。</span><span class="sxs-lookup"><span data-stu-id="f18f5-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="f18f5-105">當您設計架構時，請務必仔細設計所需的擴充性，並在危險時限制擴充性。</span><span class="sxs-lookup"><span data-stu-id="f18f5-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="f18f5-106">防止擴充性的強大機制是密封的。</span><span class="sxs-lookup"><span data-stu-id="f18f5-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="f18f5-107">您可以密封類別或個別成員。</span><span class="sxs-lookup"><span data-stu-id="f18f5-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="f18f5-108">密封類別可防止使用者繼承類別。</span><span class="sxs-lookup"><span data-stu-id="f18f5-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="f18f5-109">密封成員可防止使用者覆寫特定成員。</span><span class="sxs-lookup"><span data-stu-id="f18f5-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="f18f5-110">**X**不會密封類別，而不會有很好的理由這麼做。</span><span class="sxs-lookup"><span data-stu-id="f18f5-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="f18f5-111">密封類別是因為您不能認為擴充性案例並不是個好理由。</span><span class="sxs-lookup"><span data-stu-id="f18f5-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="f18f5-112">架構使用者想要從類別繼承，以因應各種 nonobvious 的原因，例如加入方便的成員。</span><span class="sxs-lookup"><span data-stu-id="f18f5-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="f18f5-113">如需使用者想要從類型繼承的 nonobvious 原因範例，請參閱未[密封的類別](../../../docs/standard/design-guidelines/unsealed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="f18f5-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="f18f5-114">密封類別的好理由包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="f18f5-114">Good reasons for sealing a class include the following:</span></span>  
  
- <span data-ttu-id="f18f5-115">類別是靜態類別。</span><span class="sxs-lookup"><span data-stu-id="f18f5-115">The class is a static class.</span></span> <span data-ttu-id="f18f5-116">請參閱[靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)。</span><span class="sxs-lookup"><span data-stu-id="f18f5-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
- <span data-ttu-id="f18f5-117">類別會將安全性機密的秘密儲存在繼承的受保護成員中。</span><span class="sxs-lookup"><span data-stu-id="f18f5-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
- <span data-ttu-id="f18f5-118">類別會繼承許多虛擬成員，而將其個別密封的成本，會超過讓類別不密封的優點。</span><span class="sxs-lookup"><span data-stu-id="f18f5-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
- <span data-ttu-id="f18f5-119">類別是需要非常快速的執行時間查閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="f18f5-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="f18f5-120">密封屬性的效能層級比未密封的屬性稍微高得多。</span><span class="sxs-lookup"><span data-stu-id="f18f5-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="f18f5-121">請參閱[屬性](../../../docs/standard/design-guidelines/attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="f18f5-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="f18f5-122">**X 不會**在密封類型上宣告 protected 或 virtual 成員。</span><span class="sxs-lookup"><span data-stu-id="f18f5-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="f18f5-123">根據定義，密封類型無法繼承自。</span><span class="sxs-lookup"><span data-stu-id="f18f5-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="f18f5-124">這表示不能呼叫密封類型上的 protected 成員，也無法覆寫密封類型上的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="f18f5-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="f18f5-125">**✓請考慮**密封您覆寫的成員。</span><span class="sxs-lookup"><span data-stu-id="f18f5-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="f18f5-126">導入虛擬成員（在[虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)中討論）的問題也適用于覆寫，雖然是稍微較低的程度。</span><span class="sxs-lookup"><span data-stu-id="f18f5-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="f18f5-127">密封覆寫會在繼承階層中從該點開始，讓您免于發生這些問題。</span><span class="sxs-lookup"><span data-stu-id="f18f5-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="f18f5-128">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="f18f5-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f18f5-129">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="f18f5-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18f5-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="f18f5-130">See also</span></span>

- [<span data-ttu-id="f18f5-131">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="f18f5-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f18f5-132">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="f18f5-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="f18f5-133">非密封類別</span><span class="sxs-lookup"><span data-stu-id="f18f5-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
