---
title: 非密封類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 8e332a6382cf644c82d5e26cf5234cea08dcc693
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289547"
---
# <a name="unsealed-classes"></a><span data-ttu-id="d4298-102">非密封類別</span><span class="sxs-lookup"><span data-stu-id="d4298-102">Unsealed Classes</span></span>
<span data-ttu-id="d4298-103">密封類別無法繼承自，而且它們會阻止擴充性。</span><span class="sxs-lookup"><span data-stu-id="d4298-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="d4298-104">相反地，可以繼承自的類別稱為未密封的類別。</span><span class="sxs-lookup"><span data-stu-id="d4298-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="d4298-105">✔️考慮使用未密封的類別，而不加入虛擬或受保護的成員，以提供價格實惠但對架構的擴充性的絕佳方法。</span><span class="sxs-lookup"><span data-stu-id="d4298-105">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="d4298-106">開發人員通常會想要從未密封的類別繼承，以便加入方便的成員，例如自訂的函數、新方法或方法多載。</span><span class="sxs-lookup"><span data-stu-id="d4298-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="d4298-107">例如， `System.Messaging.MessageQueue` 未密封，因此可讓使用者建立預設為特定佇列路徑的自訂佇列，或新增自訂方法來簡化特定案例的 API。</span><span class="sxs-lookup"><span data-stu-id="d4298-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="d4298-108">在大部分的程式設計語言中，類別預設為未密封，在架構中，大部分的類別也是建議使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="d4298-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="d4298-109">非密封類型所提供的擴充性非常感謝架構使用者，而且因為與非密封類型相關聯的測試成本相對較低，所以不太需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="d4298-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="d4298-110">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="d4298-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d4298-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="d4298-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d4298-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4298-112">See also</span></span>

- [<span data-ttu-id="d4298-113">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="d4298-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d4298-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="d4298-114">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="d4298-115">密封</span><span class="sxs-lookup"><span data-stu-id="d4298-115">Sealing</span></span>](sealing.md)
