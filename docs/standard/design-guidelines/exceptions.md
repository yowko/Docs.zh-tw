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
ms.openlocfilehash: d7580d4d3953b279824bba76b44c4134a7293b7a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289768"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="0449d-102">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="0449d-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="0449d-103">例外狀況處理與以傳回值為基礎的錯誤報表有許多優點。</span><span class="sxs-lookup"><span data-stu-id="0449d-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="0449d-104">良好的架構設計可協助應用程式開發人員實現例外狀況的優點。</span><span class="sxs-lookup"><span data-stu-id="0449d-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="0449d-105">本節討論例外狀況的優點，並提供有效使用它們的指導方針。</span><span class="sxs-lookup"><span data-stu-id="0449d-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0449d-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="0449d-106">In This Section</span></span>  
 [<span data-ttu-id="0449d-107">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="0449d-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="0449d-108">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="0449d-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="0449d-109">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="0449d-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="0449d-110">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="0449d-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0449d-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="0449d-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0449d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0449d-112">See also</span></span>

- [<span data-ttu-id="0449d-113">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="0449d-113">Framework Design Guidelines</span></span>](index.md)
