---
title: ParticipantRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
ms.openlocfilehash: 6856ac8b70ec30b795585b4ab2d2e76d1b61796c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684498"
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="434e3-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="434e3-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="434e3-103">識別碼:138</span><span class="sxs-lookup"><span data-stu-id="434e3-103">Id: 138</span></span>  
  
 <span data-ttu-id="434e3-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="434e3-104">Severity: Error</span></span>  
  
 <span data-ttu-id="434e3-105">類別：TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="434e3-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="434e3-106">描述</span><span class="sxs-lookup"><span data-stu-id="434e3-106">Description</span></span>  
 <span data-ttu-id="434e3-107">這個事件指出，參與者修復記錄項目已毀損，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="434e3-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="434e3-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="434e3-108">Data loss may result from this error.</span></span> <span data-ttu-id="434e3-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="434e3-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434e3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="434e3-110">See also</span></span>
- [<span data-ttu-id="434e3-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="434e3-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="434e3-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="434e3-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
