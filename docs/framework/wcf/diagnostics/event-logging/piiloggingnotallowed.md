---
title: PiiLoggingNotAllowed
ms.date: 03/30/2017
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
ms.openlocfilehash: 621d8ebe945186011e730c6d06b4c102486ac467
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278501"
---
# <a name="piiloggingnotallowed"></a><span data-ttu-id="bdd2b-102">PiiLoggingNotAllowed</span><span class="sxs-lookup"><span data-stu-id="bdd2b-102">PiiLoggingNotAllowed</span></span>

<span data-ttu-id="bdd2b-103">識別碼：108</span><span class="sxs-lookup"><span data-stu-id="bdd2b-103">Id: 108</span></span>  
  
 <span data-ttu-id="bdd2b-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="bdd2b-104">Severity: Error</span></span>  
  
 <span data-ttu-id="bdd2b-105">分類：追蹤</span><span class="sxs-lookup"><span data-stu-id="bdd2b-105">Category: Tracing</span></span>  
  
## <a name="description"></a><span data-ttu-id="bdd2b-106">描述</span><span class="sxs-lookup"><span data-stu-id="bdd2b-106">Description</span></span>  

 <span data-ttu-id="bdd2b-107">這個事件表示沒有在記錄任何已知的 PII。</span><span class="sxs-lookup"><span data-stu-id="bdd2b-107">This event indicates that no known PII is being logged.</span></span> <span data-ttu-id="bdd2b-108">記錄已知的 PII 是不允許的。</span><span class="sxs-lookup"><span data-stu-id="bdd2b-108">Logging of known PII is not allowed.</span></span> <span data-ttu-id="bdd2b-109">若要允許記錄已知的 PII，請在 Machine.config 中將 "enableLoggingKnownPii" 設定為 `true` 。此事件會列出進程名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="bdd2b-109">To allow logging of known PII, set "enableLoggingKnownPii" to `true` in Machine.config. The event lists the process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd2b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdd2b-110">See also</span></span>

- [<span data-ttu-id="bdd2b-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="bdd2b-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="bdd2b-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="bdd2b-112">Events General Reference</span></span>](events-general-reference.md)
