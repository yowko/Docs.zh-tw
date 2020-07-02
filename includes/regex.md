---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802843"
---

> [!WARNING]
> <span data-ttu-id="501d8-101">當使用 <xref:System.Text.RegularExpressions> 來處理不受信任的輸入時，請傳遞超時。</span><span class="sxs-lookup"><span data-stu-id="501d8-101">When using <xref:System.Text.RegularExpressions> to process untrusted input, pass a timeout.</span></span> <span data-ttu-id="501d8-102">惡意使用者可以提供輸入， `RegularExpressions` 導致[拒絕服務攻擊](https://www.us-cert.gov/ncas/tips/ST04-015)。</span><span class="sxs-lookup"><span data-stu-id="501d8-102">A malicious user can provide input to `RegularExpressions` causing a [Denial-of-Service attack](https://www.us-cert.gov/ncas/tips/ST04-015).</span></span> <span data-ttu-id="501d8-103">使用的 ASP.NET Core framework Api 會 `RegularExpressions` 傳遞超時。</span><span class="sxs-lookup"><span data-stu-id="501d8-103">ASP.NET Core framework APIs that use `RegularExpressions` pass a timeout.</span></span>
