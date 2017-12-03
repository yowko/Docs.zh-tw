---
title: CoordinatorRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d57f0e7528c8df6ebf98aa712fe3efd728b421d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="48537-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="48537-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="48537-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="48537-103">Id: 139</span></span>  
  
 <span data-ttu-id="48537-104">嚴重性：錯誤</span><span class="sxs-lookup"><span data-stu-id="48537-104">Severity: Error</span></span>  
  
 <span data-ttu-id="48537-105">分類：TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="48537-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="48537-106">描述</span><span class="sxs-lookup"><span data-stu-id="48537-106">Description</span></span>  
 <span data-ttu-id="48537-107">此事件表示協調器修復記錄項目損毀，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="48537-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="48537-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="48537-108">Data loss may result from this error.</span></span> <span data-ttu-id="48537-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="48537-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48537-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48537-110">See Also</span></span>  
 [<span data-ttu-id="48537-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="48537-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="48537-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="48537-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
