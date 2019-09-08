---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: de9d27e74088b1bac9c8a401c5af2b119fc8e90e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797980"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="07115-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="07115-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="07115-103">識別碼:139</span><span class="sxs-lookup"><span data-stu-id="07115-103">Id: 139</span></span>  
  
 <span data-ttu-id="07115-104">嚴重性：Error</span><span class="sxs-lookup"><span data-stu-id="07115-104">Severity: Error</span></span>  
  
 <span data-ttu-id="07115-105">CategoryTransactionBridge</span><span class="sxs-lookup"><span data-stu-id="07115-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="07115-106">描述</span><span class="sxs-lookup"><span data-stu-id="07115-106">Description</span></span>  
 <span data-ttu-id="07115-107">此事件表示協調器修復記錄項目損毀，且無法還原序列化。</span><span class="sxs-lookup"><span data-stu-id="07115-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="07115-108">這個錯誤可能會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="07115-108">Data loss may result from this error.</span></span> <span data-ttu-id="07115-109">事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="07115-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07115-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07115-110">See also</span></span>

- [<span data-ttu-id="07115-111">事件記錄</span><span class="sxs-lookup"><span data-stu-id="07115-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="07115-112">事件一般參考</span><span class="sxs-lookup"><span data-stu-id="07115-112">Events General Reference</span></span>](events-general-reference.md)
