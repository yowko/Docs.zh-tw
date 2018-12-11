---
title: 例外狀況的設計方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
author: KrzysztofCwalina
ms.openlocfilehash: 60c3d25138c224f5eabf44d06b6c9a8373eb5f96
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153187"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="8bdf1-102">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="8bdf1-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="8bdf1-103">例外狀況處理有傳回值為基礎的錯誤報告的許多優點。</span><span class="sxs-lookup"><span data-stu-id="8bdf1-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="8bdf1-104">良好的架構設計可協助應用程式開發人員實現優勢的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8bdf1-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="8bdf1-105">本節討論這些優點的例外狀況，並提供有效地使用這些指導方針。</span><span class="sxs-lookup"><span data-stu-id="8bdf1-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8bdf1-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="8bdf1-106">In This Section</span></span>  
 [<span data-ttu-id="8bdf1-107">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="8bdf1-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="8bdf1-108">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="8bdf1-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="8bdf1-109">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="8bdf1-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="8bdf1-110">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="8bdf1-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8bdf1-111">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="8bdf1-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bdf1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bdf1-112">See also</span></span>

- [<span data-ttu-id="8bdf1-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="8bdf1-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
