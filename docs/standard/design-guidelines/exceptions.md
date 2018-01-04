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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 471746242e7abe491148201103741fd00f4338cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="c70b4-102">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="c70b4-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="c70b4-103">例外狀況處理有許多優於傳回值為基礎的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="c70b4-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="c70b4-104">良好的架構設計，可協助應用程式開發人員了解例外狀況的優點。</span><span class="sxs-lookup"><span data-stu-id="c70b4-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="c70b4-105">本節討論例外狀況的優點，並提供有效地使用這些指導方針。</span><span class="sxs-lookup"><span data-stu-id="c70b4-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c70b4-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c70b4-106">In This Section</span></span>  
 [<span data-ttu-id="c70b4-107">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="c70b4-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="c70b4-108">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="c70b4-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="c70b4-109">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="c70b4-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="c70b4-110">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="c70b4-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c70b4-111">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="c70b4-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70b4-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="c70b4-112">See Also</span></span>  
 [<span data-ttu-id="c70b4-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="c70b4-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
