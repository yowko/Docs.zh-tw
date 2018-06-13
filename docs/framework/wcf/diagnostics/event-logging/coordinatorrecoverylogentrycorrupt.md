---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3f51d1269f5ca89f4f02257c8accef3423aa7eb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472679"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="c012e-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="c012e-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="c012e-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="c012e-103">Id: 139</span></span>  
  
 <span data-ttu-id="c012e-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="c012e-104">Severity: Error</span></span>  
  
 <span data-ttu-id="c012e-105">分類：TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="c012e-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="c012e-106">描述</span><span class="sxs-lookup"><span data-stu-id="c012e-106">Description</span></span>  
 <span data-ttu-id="c012e-107">此事件表示協調器修復記錄項目損毀，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="c012e-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="c012e-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="c012e-108">Data loss may result from this error.</span></span> <span data-ttu-id="c012e-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="c012e-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c012e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c012e-110">See Also</span></span>  
 [<span data-ttu-id="c012e-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="c012e-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="c012e-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="c012e-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
