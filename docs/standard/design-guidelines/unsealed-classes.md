---
title: 非密封類別
ms.date: 10/22/2008
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 9e380f533cfc290e952281c6a04f19978fa92aa3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677501"
---
# <a name="unsealed-classes"></a><span data-ttu-id="6e72a-102">非密封類別</span><span class="sxs-lookup"><span data-stu-id="6e72a-102">Unsealed Classes</span></span>

<span data-ttu-id="6e72a-103">密封類別不能繼承自，而且它們會防止擴充性。</span><span class="sxs-lookup"><span data-stu-id="6e72a-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="6e72a-104">相反地，可繼承的類別稱為未密封類別。</span><span class="sxs-lookup"><span data-stu-id="6e72a-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="6e72a-105">✔️考慮使用未密封的類別，而不是加入虛擬或受保護的成員，這是為架構提供便宜的擴充性的絕佳方法。</span><span class="sxs-lookup"><span data-stu-id="6e72a-105">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="6e72a-106">開發人員通常會想要繼承自未密封的類別，以便加入方便的成員，例如自訂的函式、新方法或方法多載。</span><span class="sxs-lookup"><span data-stu-id="6e72a-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="6e72a-107">例如，  `System.Messaging.MessageQueue` 未密封，因此可讓使用者建立預設為特定佇列路徑的自訂佇列，或新增自訂方法，以簡化特定案例的 API。</span><span class="sxs-lookup"><span data-stu-id="6e72a-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="6e72a-108">在大部分的程式設計語言中，類別預設是未密封的，而且在架構中，大部分的類別也是建議的預設值。</span><span class="sxs-lookup"><span data-stu-id="6e72a-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="6e72a-109">非密封型別所提供的擴充性，是由架構使用者所提供，且相當便宜，因為與非密封類型相關聯的測試成本相對較低。</span><span class="sxs-lookup"><span data-stu-id="6e72a-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="6e72a-110">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="6e72a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6e72a-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="6e72a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6e72a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e72a-112">See also</span></span>

- [<span data-ttu-id="6e72a-113">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="6e72a-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="6e72a-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="6e72a-114">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="6e72a-115">密封</span><span class="sxs-lookup"><span data-stu-id="6e72a-115">Sealing</span></span>](sealing.md)
