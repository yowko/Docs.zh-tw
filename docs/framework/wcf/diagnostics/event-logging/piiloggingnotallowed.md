---
title: PiiLoggingNotAllowed
ms.date: 03/30/2017
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
ms.openlocfilehash: 24b31c33b31bb0ef763de30ce24fbc28f03aa039
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797652"
---
# <a name="piiloggingnotallowed"></a><span data-ttu-id="cd111-102">PiiLoggingNotAllowed</span><span class="sxs-lookup"><span data-stu-id="cd111-102">PiiLoggingNotAllowed</span></span>
<span data-ttu-id="cd111-103">識別碼:108</span><span class="sxs-lookup"><span data-stu-id="cd111-103">Id: 108</span></span>  
  
 <span data-ttu-id="cd111-104">嚴重性：Error</span><span class="sxs-lookup"><span data-stu-id="cd111-104">Severity: Error</span></span>  
  
 <span data-ttu-id="cd111-105">Category追蹤</span><span class="sxs-lookup"><span data-stu-id="cd111-105">Category: Tracing</span></span>  
  
## <a name="description"></a><span data-ttu-id="cd111-106">說明</span><span class="sxs-lookup"><span data-stu-id="cd111-106">Description</span></span>  
 <span data-ttu-id="cd111-107">這個事件表示沒有在記錄任何已知的 PII。</span><span class="sxs-lookup"><span data-stu-id="cd111-107">This event indicates that no known PII is being logged.</span></span> <span data-ttu-id="cd111-108">記錄已知的 PII 是不允許的。</span><span class="sxs-lookup"><span data-stu-id="cd111-108">Logging of known PII is not allowed.</span></span> <span data-ttu-id="cd111-109">若要允許記錄已知的 PII，請將 Machine.config 中的 "enableLoggingKnownPii" 設定為 `true`。此事件會列出處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="cd111-109">To allow logging of known PII, set "enableLoggingKnownPii" to `true` in Machine.config. The event lists the process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd111-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd111-110">See also</span></span>

- [<span data-ttu-id="cd111-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="cd111-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="cd111-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="cd111-112">Events General Reference</span></span>](events-general-reference.md)
