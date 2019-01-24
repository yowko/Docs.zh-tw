---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 0dc74b784d8a9ed3ab27bb4b8d3de34143f6ce07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639480"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="be33d-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="be33d-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="be33d-103">識別碼:139</span><span class="sxs-lookup"><span data-stu-id="be33d-103">Id: 139</span></span>  
  
 <span data-ttu-id="be33d-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="be33d-104">Severity: Error</span></span>  
  
 <span data-ttu-id="be33d-105">類別：TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="be33d-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="be33d-106">描述</span><span class="sxs-lookup"><span data-stu-id="be33d-106">Description</span></span>  
 <span data-ttu-id="be33d-107">此事件表示協調器修復記錄項目損毀，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="be33d-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="be33d-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="be33d-108">Data loss may result from this error.</span></span> <span data-ttu-id="be33d-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="be33d-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be33d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be33d-110">See also</span></span>
- [<span data-ttu-id="be33d-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="be33d-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="be33d-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="be33d-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
