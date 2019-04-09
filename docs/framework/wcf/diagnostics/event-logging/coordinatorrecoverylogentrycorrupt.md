---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: faf4a07badb71588c601cd9390e4d8e3f187e629
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121624"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="53083-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="53083-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="53083-103">識別碼:139</span><span class="sxs-lookup"><span data-stu-id="53083-103">Id: 139</span></span>  
  
 <span data-ttu-id="53083-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="53083-104">Severity: Error</span></span>  
  
 <span data-ttu-id="53083-105">類別：TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="53083-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="53083-106">描述</span><span class="sxs-lookup"><span data-stu-id="53083-106">Description</span></span>  
 <span data-ttu-id="53083-107">此事件表示協調器修復記錄項目損毀，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="53083-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="53083-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="53083-108">Data loss may result from this error.</span></span> <span data-ttu-id="53083-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="53083-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53083-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53083-110">See also</span></span>

- [<span data-ttu-id="53083-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="53083-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="53083-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="53083-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
