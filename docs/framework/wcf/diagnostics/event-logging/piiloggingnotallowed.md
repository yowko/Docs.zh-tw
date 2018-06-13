---
title: PiiLoggingNotAllowed
ms.date: 03/30/2017
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
ms.openlocfilehash: bbeaefc49df856e0fc3b989ad899f26052bed7b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33468279"
---
# <a name="piiloggingnotallowed"></a><span data-ttu-id="39bdb-102">PiiLoggingNotAllowed</span><span class="sxs-lookup"><span data-stu-id="39bdb-102">PiiLoggingNotAllowed</span></span>
<span data-ttu-id="39bdb-103">識別碼：108</span><span class="sxs-lookup"><span data-stu-id="39bdb-103">Id: 108</span></span>  
  
 <span data-ttu-id="39bdb-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="39bdb-104">Severity: Error</span></span>  
  
 <span data-ttu-id="39bdb-105">分類：追蹤</span><span class="sxs-lookup"><span data-stu-id="39bdb-105">Category: Tracing</span></span>  
  
## <a name="description"></a><span data-ttu-id="39bdb-106">描述</span><span class="sxs-lookup"><span data-stu-id="39bdb-106">Description</span></span>  
 <span data-ttu-id="39bdb-107">這個事件表示沒有在記錄任何已知的 PII。</span><span class="sxs-lookup"><span data-stu-id="39bdb-107">This event indicates that no known PII is being logged.</span></span> <span data-ttu-id="39bdb-108">記錄已知的 PII 是不允許的。</span><span class="sxs-lookup"><span data-stu-id="39bdb-108">Logging of known PII is not allowed.</span></span> <span data-ttu-id="39bdb-109">若要允許記錄已知的 PII，請將 Machine.config 中的 "enableLoggingKnownPii" 設定為 `true`。此事件會列出處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="39bdb-109">To allow logging of known PII, set "enableLoggingKnownPii" to `true` in Machine.config. The event lists the process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bdb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39bdb-110">See Also</span></span>  
 [<span data-ttu-id="39bdb-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="39bdb-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="39bdb-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="39bdb-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
