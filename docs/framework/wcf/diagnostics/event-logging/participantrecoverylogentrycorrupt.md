---
title: ParticipantRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 134cc6c1c3f0a04b55cc20aa7d9c7cadbe9c09af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="3dd9f-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="3dd9f-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="3dd9f-103">Id: 138</span><span class="sxs-lookup"><span data-stu-id="3dd9f-103">Id: 138</span></span>  
  
 <span data-ttu-id="3dd9f-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="3dd9f-104">Severity: Error</span></span>  
  
 <span data-ttu-id="3dd9f-105">分類：TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="3dd9f-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="3dd9f-106">描述</span><span class="sxs-lookup"><span data-stu-id="3dd9f-106">Description</span></span>  
 <span data-ttu-id="3dd9f-107">這個事件指出，參與者修復記錄項目已毀損，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="3dd9f-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="3dd9f-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="3dd9f-108">Data loss may result from this error.</span></span> <span data-ttu-id="3dd9f-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="3dd9f-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd9f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dd9f-110">See Also</span></span>  
 [<span data-ttu-id="3dd9f-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="3dd9f-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="3dd9f-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="3dd9f-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
