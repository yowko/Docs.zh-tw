---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589128"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="e64f3-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="e64f3-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="e64f3-103">WS-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。</span><span class="sxs-lookup"><span data-stu-id="e64f3-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="e64f3-104">因此，交易已中止。</span><span class="sxs-lookup"><span data-stu-id="e64f3-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e64f3-105">描述</span><span class="sxs-lookup"><span data-stu-id="e64f3-105">Description</span></span>  
 <span data-ttu-id="e64f3-106">如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="e64f3-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="e64f3-107">這是此狀態的不合法訊息，因此異動即將中止。</span><span class="sxs-lookup"><span data-stu-id="e64f3-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e64f3-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e64f3-108">Troubleshooting</span></span>

<span data-ttu-id="e64f3-109">收到此錯誤可能表示持久的參與者（包括次級 TransactionManagers）已從失敗中復原;不過，它不確定交易結果並要求其狀態。</span><span class="sxs-lookup"><span data-stu-id="e64f3-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e64f3-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="e64f3-110">See also</span></span>

- [<span data-ttu-id="e64f3-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="e64f3-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="e64f3-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="e64f3-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e64f3-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="e64f3-113">Administration and Diagnostics</span></span>](../index.md)
