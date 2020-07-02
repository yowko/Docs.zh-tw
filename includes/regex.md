---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802843"
---

> [!WARNING]
> 當使用 <xref:System.Text.RegularExpressions> 來處理不受信任的輸入時，請傳遞超時。 惡意使用者可以提供輸入， `RegularExpressions` 導致[拒絕服務攻擊](https://www.us-cert.gov/ncas/tips/ST04-015)。 使用的 ASP.NET Core framework Api 會 `RegularExpressions` 傳遞超時。
