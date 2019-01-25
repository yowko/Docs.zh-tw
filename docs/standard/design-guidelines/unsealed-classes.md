---
title: 非密封類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616925"
---
# <a name="unsealed-classes"></a><span data-ttu-id="2ced6-102">非密封類別</span><span class="sxs-lookup"><span data-stu-id="2ced6-102">Unsealed Classes</span></span>
<span data-ttu-id="2ced6-103">密封的類別無法被繼承，並循環讓擴充性。</span><span class="sxs-lookup"><span data-stu-id="2ced6-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="2ced6-104">相反地，可以繼承自的類別稱為未密封的類別。</span><span class="sxs-lookup"><span data-stu-id="2ced6-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="2ced6-105">**✓ CONSIDER** 沒有使用未密封的類別新增虛擬或受保護成員，為提供低成本的好方法卻高價值為架構的擴充性。</span><span class="sxs-lookup"><span data-stu-id="2ced6-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="2ced6-106">開發人員通常會想要繼承自未密封的類別，以便加入方便的成員，例如自訂建構函式、 新的方法或方法多載。</span><span class="sxs-lookup"><span data-stu-id="2ced6-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="2ced6-107">比方說，`System.Messaging.MessageQueue`未密封，因此可讓使用者建立自訂的佇列預設為特定的佇列路徑，或加入自訂的方法，可簡化針對特定案例的 API。</span><span class="sxs-lookup"><span data-stu-id="2ced6-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="2ced6-108">根據預設，在多數程式設計語言中，未密封的類別是，這也是在架構中的大部分類別的建議預設值。</span><span class="sxs-lookup"><span data-stu-id="2ced6-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="2ced6-109">非密封類型所提供的擴充性是更令人激賞的 framework 使用者，因為非密封類型相關聯的相對較低的測試成本提供成本很低。</span><span class="sxs-lookup"><span data-stu-id="2ced6-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="2ced6-110">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="2ced6-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2ced6-111">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="2ced6-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ced6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ced6-112">See also</span></span>

- [<span data-ttu-id="2ced6-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="2ced6-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="2ced6-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="2ced6-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="2ced6-115">密封</span><span class="sxs-lookup"><span data-stu-id="2ced6-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
