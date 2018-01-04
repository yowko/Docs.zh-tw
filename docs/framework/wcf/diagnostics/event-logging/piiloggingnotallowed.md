---
title: PiiLoggingNotAllowed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44c4c1bbd42b2bf66c83899623012d6b07c1a2f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="piiloggingnotallowed"></a><span data-ttu-id="9b277-102">PiiLoggingNotAllowed</span><span class="sxs-lookup"><span data-stu-id="9b277-102">PiiLoggingNotAllowed</span></span>
<span data-ttu-id="9b277-103">識別碼：108</span><span class="sxs-lookup"><span data-stu-id="9b277-103">Id: 108</span></span>  
  
 <span data-ttu-id="9b277-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="9b277-104">Severity: Error</span></span>  
  
 <span data-ttu-id="9b277-105">分類：追蹤</span><span class="sxs-lookup"><span data-stu-id="9b277-105">Category: Tracing</span></span>  
  
## <a name="description"></a><span data-ttu-id="9b277-106">描述</span><span class="sxs-lookup"><span data-stu-id="9b277-106">Description</span></span>  
 <span data-ttu-id="9b277-107">這個事件表示沒有在記錄任何已知的 PII。</span><span class="sxs-lookup"><span data-stu-id="9b277-107">This event indicates that no known PII is being logged.</span></span> <span data-ttu-id="9b277-108">記錄已知的 PII 是不允許的。</span><span class="sxs-lookup"><span data-stu-id="9b277-108">Logging of known PII is not allowed.</span></span> <span data-ttu-id="9b277-109">若要允許記錄已知的 PII，請將 Machine.config 中的 "enableLoggingKnownPii" 設定為 `true`。此事件會列出處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="9b277-109">To allow logging of known PII, set "enableLoggingKnownPii" to `true` in Machine.config. The event lists the process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b277-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b277-110">See Also</span></span>  
 [<span data-ttu-id="9b277-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="9b277-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="9b277-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="9b277-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
