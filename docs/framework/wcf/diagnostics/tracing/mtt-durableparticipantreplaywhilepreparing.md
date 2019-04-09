---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: f5d74d73cc43b500d3920ca03905f4eb7543619a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075531"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="36bac-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="36bac-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="36bac-103">WS-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。</span><span class="sxs-lookup"><span data-stu-id="36bac-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="36bac-104">因此，交易已中止。</span><span class="sxs-lookup"><span data-stu-id="36bac-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="36bac-105">描述</span><span class="sxs-lookup"><span data-stu-id="36bac-105">Description</span></span>  
 <span data-ttu-id="36bac-106">如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="36bac-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="36bac-107">這是此狀態的不合法訊息，因此異動即將中止。</span><span class="sxs-lookup"><span data-stu-id="36bac-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="36bac-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="36bac-108">Troubleshooting</span></span>  
 <span data-ttu-id="36bac-109">接收這項錯誤可能表示參與者 (包括下層交易管理員) 已經從失敗復原，不過不確定交易結果並要求其狀態。</span><span class="sxs-lookup"><span data-stu-id="36bac-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bac-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36bac-110">See also</span></span>

- [<span data-ttu-id="36bac-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="36bac-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="36bac-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="36bac-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="36bac-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="36bac-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
