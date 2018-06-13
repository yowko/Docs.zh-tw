---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33476316"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="31cf5-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="31cf5-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="31cf5-103">WS-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。</span><span class="sxs-lookup"><span data-stu-id="31cf5-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="31cf5-104">因此，交易已中止。</span><span class="sxs-lookup"><span data-stu-id="31cf5-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="31cf5-105">描述</span><span class="sxs-lookup"><span data-stu-id="31cf5-105">Description</span></span>  
 <span data-ttu-id="31cf5-106">如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="31cf5-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="31cf5-107">這是此狀態的不合法訊息，因此交易即將中止。</span><span class="sxs-lookup"><span data-stu-id="31cf5-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="31cf5-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="31cf5-108">Troubleshooting</span></span>  
 <span data-ttu-id="31cf5-109">接收這項錯誤可能表示參與者 (包括下層異動管理員) 已經從失敗復原，不過不確定異動結果並要求其狀態。</span><span class="sxs-lookup"><span data-stu-id="31cf5-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31cf5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31cf5-110">See Also</span></span>  
 [<span data-ttu-id="31cf5-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="31cf5-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="31cf5-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="31cf5-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="31cf5-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="31cf5-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
