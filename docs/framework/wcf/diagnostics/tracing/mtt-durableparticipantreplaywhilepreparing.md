---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 3b51a100677221866186b2e24f34396c012d11c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603127"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="c903c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="c903c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="c903c-103">WS-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。</span><span class="sxs-lookup"><span data-stu-id="c903c-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="c903c-104">因此，交易已中止。</span><span class="sxs-lookup"><span data-stu-id="c903c-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c903c-105">描述</span><span class="sxs-lookup"><span data-stu-id="c903c-105">Description</span></span>  
 <span data-ttu-id="c903c-106">如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="c903c-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="c903c-107">這是此狀態的不合法訊息，因此交易即將中止。</span><span class="sxs-lookup"><span data-stu-id="c903c-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c903c-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="c903c-108">Troubleshooting</span></span>  
 <span data-ttu-id="c903c-109">接收這項錯誤可能表示參與者 (包括下層異動管理員) 已經從失敗復原，不過不確定異動結果並要求其狀態。</span><span class="sxs-lookup"><span data-stu-id="c903c-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c903c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c903c-110">See also</span></span>
- [<span data-ttu-id="c903c-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="c903c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c903c-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c903c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c903c-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="c903c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
