---
title: ParticipantRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
ms.openlocfilehash: 61ab172a3924e3c0ca00ffc25ef96446e33c5142
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796227"
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="e092d-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="e092d-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="e092d-103">識別碼:138</span><span class="sxs-lookup"><span data-stu-id="e092d-103">Id: 138</span></span>  
  
 <span data-ttu-id="e092d-104">嚴重性：Error</span><span class="sxs-lookup"><span data-stu-id="e092d-104">Severity: Error</span></span>  
  
 <span data-ttu-id="e092d-105">CategoryTransactionBridge</span><span class="sxs-lookup"><span data-stu-id="e092d-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="e092d-106">說明</span><span class="sxs-lookup"><span data-stu-id="e092d-106">Description</span></span>  
 <span data-ttu-id="e092d-107">這個事件指出，參與者修復記錄項目已毀損，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="e092d-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="e092d-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="e092d-108">Data loss may result from this error.</span></span> <span data-ttu-id="e092d-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="e092d-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e092d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e092d-110">See also</span></span>

- [<span data-ttu-id="e092d-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="e092d-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="e092d-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="e092d-112">Events General Reference</span></span>](events-general-reference.md)
