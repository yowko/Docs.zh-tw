---
title: "例外狀況的設計方針"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ee456632070f778d51d7fb40475a795a0f620b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="ab24b-102">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="ab24b-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="ab24b-103">例外狀況處理有許多優於傳回值為基礎的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="ab24b-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="ab24b-104">良好的架構設計，可協助應用程式開發人員了解例外狀況的優點。</span><span class="sxs-lookup"><span data-stu-id="ab24b-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="ab24b-105">本節討論例外狀況的優點，並提供有效地使用這些指導方針。</span><span class="sxs-lookup"><span data-stu-id="ab24b-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab24b-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="ab24b-106">In This Section</span></span>  
 [<span data-ttu-id="ab24b-107">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="ab24b-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="ab24b-108">使用標準的例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="ab24b-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="ab24b-109">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="ab24b-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="ab24b-110">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="ab24b-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ab24b-111">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="ab24b-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab24b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab24b-112">See Also</span></span>  
 [<span data-ttu-id="ab24b-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="ab24b-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
