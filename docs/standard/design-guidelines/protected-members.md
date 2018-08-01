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
ms.openlocfilehash: 5d4d334d9809f374442e19807d3b249a17a1d9df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571079"
---
# <a name="protected-members"></a><span data-ttu-id="76f63-102">Protected 成員</span><span class="sxs-lookup"><span data-stu-id="76f63-102">Protected Members</span></span>
<span data-ttu-id="76f63-103">受保護的成員，本身不提供任何擴充性，但會讓透過子類別化的擴充性功能更強大。</span><span class="sxs-lookup"><span data-stu-id="76f63-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="76f63-104">它們可以用於不含不必要地複雜的主要公用介面公開進階的自訂選項。</span><span class="sxs-lookup"><span data-stu-id="76f63-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="76f63-105">架構設計人員必須謹慎使用受保護成員因為 「 受保護 」 的名稱可以提供感應的安全性。</span><span class="sxs-lookup"><span data-stu-id="76f63-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="76f63-106">任何人都可以子類別的未密封類別，然後存取受保護成員，用於公用成員的防衛性程式碼撰寫方式完全相同，套用至受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="76f63-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="76f63-107">**✓ CONSIDER**使用受保護的進階自訂的成員。</span><span class="sxs-lookup"><span data-stu-id="76f63-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="76f63-108">**✓ DO**為用於安全性、 文件，以及相容性的分析公用非密封類別以處理受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="76f63-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="76f63-109">任何人都可以繼承自類別，並存取受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="76f63-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="76f63-110">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="76f63-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="76f63-111">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="76f63-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f63-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76f63-112">See Also</span></span>  
 [<span data-ttu-id="76f63-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="76f63-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="76f63-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="76f63-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
