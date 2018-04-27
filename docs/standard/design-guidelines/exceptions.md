---
title: 例外狀況的設計方針
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6dcd29f96ce32f1b2602af5d844339fe33c0ed7b
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="94830-102">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="94830-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="94830-103">例外狀況處理有許多優於傳回值為基礎的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="94830-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="94830-104">良好的架構設計，可協助應用程式開發人員了解例外狀況的優點。</span><span class="sxs-lookup"><span data-stu-id="94830-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="94830-105">本節討論例外狀況的優點，並提供有效地使用這些指導方針。</span><span class="sxs-lookup"><span data-stu-id="94830-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94830-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="94830-106">In This Section</span></span>  
 [<span data-ttu-id="94830-107">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="94830-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="94830-108">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="94830-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="94830-109">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="94830-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="94830-110">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="94830-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="94830-111">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="94830-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94830-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94830-112">See Also</span></span>  
 [<span data-ttu-id="94830-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="94830-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
