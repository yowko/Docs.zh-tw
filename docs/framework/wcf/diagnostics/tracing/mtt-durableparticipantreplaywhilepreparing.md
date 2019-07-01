---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486761"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="57ef7-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="57ef7-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="57ef7-103">WS-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。</span><span class="sxs-lookup"><span data-stu-id="57ef7-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="57ef7-104">因此，交易已中止。</span><span class="sxs-lookup"><span data-stu-id="57ef7-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="57ef7-105">描述</span><span class="sxs-lookup"><span data-stu-id="57ef7-105">Description</span></span>  
 <span data-ttu-id="57ef7-106">如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="57ef7-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="57ef7-107">這是此狀態的不合法訊息，因此異動即將中止。</span><span class="sxs-lookup"><span data-stu-id="57ef7-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="57ef7-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="57ef7-108">Troubleshooting</span></span>

<span data-ttu-id="57ef7-109">收到這個錯誤可能表示已從災難中復原 （包括下層異動管理員） 的長期參與者不過，它會不確定交易結果，並要求其狀態。</span><span class="sxs-lookup"><span data-stu-id="57ef7-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ef7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57ef7-110">See also</span></span>

- [<span data-ttu-id="57ef7-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="57ef7-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="57ef7-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="57ef7-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="57ef7-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="57ef7-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
