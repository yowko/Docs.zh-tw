---
title: Protected 成員
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4574dffc3f9dd1b60d655bfde33a4ddc1a81d350
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140940"
---
# <a name="protected-members"></a><span data-ttu-id="62258-102">Protected 成員</span><span class="sxs-lookup"><span data-stu-id="62258-102">Protected Members</span></span>
<span data-ttu-id="62258-103">受保護的成員，本身不提供任何擴充性，但它們可以讓透過子類別化的擴充性功能更強大。</span><span class="sxs-lookup"><span data-stu-id="62258-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="62258-104">它們可以用來公開 （expose） 而不需要不必要地複雜的主要公用介面的進階的自訂選項。</span><span class="sxs-lookup"><span data-stu-id="62258-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="62258-105">架構設計人員必須謹慎使用受保護的成員，是因為 「 受保護 」 的名稱可以讓安全性的錯覺。</span><span class="sxs-lookup"><span data-stu-id="62258-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="62258-106">任何人都能夠子類別的未密封的類別，然後存取受保護成員，因此相同的所有用於公用成員的防禦性程式碼撰寫慣例套用至受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="62258-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="62258-107">**✓ CONSIDER** 使用受保護的進階自訂的成員。</span><span class="sxs-lookup"><span data-stu-id="62258-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="62258-108">**✓ DO** 為用於安全性、 文件，以及相容性的分析公用非密封類別以處理受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="62258-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="62258-109">任何人都可以繼承自的類別，並存取受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="62258-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="62258-110">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="62258-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="62258-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="62258-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62258-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62258-112">See also</span></span>

- [<span data-ttu-id="62258-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="62258-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="62258-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="62258-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
