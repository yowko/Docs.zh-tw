---
title: 非密封類別
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 672d36c6b888ee9a89a76d5d417a7a7e92dd8f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571657"
---
# <a name="unsealed-classes"></a><span data-ttu-id="cbbb2-102">非密封類別</span><span class="sxs-lookup"><span data-stu-id="cbbb2-102">Unsealed Classes</span></span>
<span data-ttu-id="cbbb2-103">密封的類別無法被繼承，以及它們會防止擴充性。</span><span class="sxs-lookup"><span data-stu-id="cbbb2-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="cbbb2-104">相反地，可以繼承自的類別稱為未密封的類別。</span><span class="sxs-lookup"><span data-stu-id="cbbb2-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="cbbb2-105">**✓ CONSIDER**沒有使用未密封的類別新增虛擬或受保護成員，為提供低成本的好方法卻高價值為架構的擴充性。</span><span class="sxs-lookup"><span data-stu-id="cbbb2-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="cbbb2-106">開發人員通常會想要繼承自非密封類別，以新增方便成員，例如自訂建構函式、 新的方法或方法多載。</span><span class="sxs-lookup"><span data-stu-id="cbbb2-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="cbbb2-107">例如，`System.Messaging.MessageQueue`未密封，因此可讓使用者建立自訂的佇列的特定佇列路徑的預設或加入自訂方法，可簡化針對特定案例的 API。</span><span class="sxs-lookup"><span data-stu-id="cbbb2-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="cbbb2-108">根據預設，在最具備程式設計語言中，未密封的類別是，這也是建議的預設值為架構中，大部分的類別。</span><span class="sxs-lookup"><span data-stu-id="cbbb2-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="cbbb2-109">非密封類型所提供的擴充性是由 framework 使用者很令人激賞和相當耗費大量資源因為相對較低的測試與未密封的型別相關聯的成本提供。</span><span class="sxs-lookup"><span data-stu-id="cbbb2-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="cbbb2-110">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="cbbb2-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cbbb2-111">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="cbbb2-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbb2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbbb2-112">See Also</span></span>  
 [<span data-ttu-id="cbbb2-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="cbbb2-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="cbbb2-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="cbbb2-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="cbbb2-115">密封</span><span class="sxs-lookup"><span data-stu-id="cbbb2-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
