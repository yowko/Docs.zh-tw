---
title: 例外狀況的設計方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51cc5296a7b3f6d75b5e56d6bbc74330fa147848
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140953"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="e57b6-102">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="e57b6-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="e57b6-103">例外狀況處理有傳回值為基礎的錯誤報告的許多優點。</span><span class="sxs-lookup"><span data-stu-id="e57b6-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="e57b6-104">良好的架構設計可協助應用程式開發人員實現優勢的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e57b6-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="e57b6-105">本節討論這些優點的例外狀況，並提供有效地使用這些指導方針。</span><span class="sxs-lookup"><span data-stu-id="e57b6-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e57b6-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="e57b6-106">In This Section</span></span>  
 [<span data-ttu-id="e57b6-107">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="e57b6-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="e57b6-108">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="e57b6-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="e57b6-109">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="e57b6-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="e57b6-110">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="e57b6-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e57b6-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="e57b6-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57b6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e57b6-112">See also</span></span>

- [<span data-ttu-id="e57b6-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="e57b6-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
