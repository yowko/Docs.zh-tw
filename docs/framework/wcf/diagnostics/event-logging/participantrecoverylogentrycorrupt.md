---
title: ParticipantRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
ms.openlocfilehash: 5a2f23a3335f938b26a378010e083525803ffb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33470487"
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="d8172-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="d8172-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="d8172-103">Id: 138</span><span class="sxs-lookup"><span data-stu-id="d8172-103">Id: 138</span></span>  
  
 <span data-ttu-id="d8172-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="d8172-104">Severity: Error</span></span>  
  
 <span data-ttu-id="d8172-105">分類：TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="d8172-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8172-106">描述</span><span class="sxs-lookup"><span data-stu-id="d8172-106">Description</span></span>  
 <span data-ttu-id="d8172-107">這個事件指出，參與者修復記錄項目已毀損，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d8172-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="d8172-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="d8172-108">Data loss may result from this error.</span></span> <span data-ttu-id="d8172-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="d8172-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8172-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8172-110">See Also</span></span>  
 [<span data-ttu-id="d8172-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="d8172-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="d8172-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="d8172-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
