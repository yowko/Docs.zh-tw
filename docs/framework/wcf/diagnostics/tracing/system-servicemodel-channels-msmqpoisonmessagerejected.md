---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: c5401bae1d8e7f61939d8de321353f59f412f966
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535329"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="1c1f2-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1c1f2-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="1c1f2-103">已拒絕有害訊息。</span><span class="sxs-lookup"><span data-stu-id="1c1f2-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1c1f2-104">描述</span><span class="sxs-lookup"><span data-stu-id="1c1f2-104">Description</span></span>  

 <span data-ttu-id="1c1f2-105">此追蹤表示遇到有害訊息，隨後拒絕該訊息。</span><span class="sxs-lookup"><span data-stu-id="1c1f2-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="1c1f2-106">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="1c1f2-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="1c1f2-107">拒絕的訊息會傳回給寄件者的寄不出的 [信件佇列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。</span><span class="sxs-lookup"><span data-stu-id="1c1f2-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="1c1f2-108">如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="1c1f2-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="1c1f2-109">如需 MSMQ 中的已拒絕訊息的詳細資訊，請參閱 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="1c1f2-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c1f2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c1f2-110">See also</span></span>

- [<span data-ttu-id="1c1f2-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="1c1f2-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="1c1f2-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="1c1f2-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1c1f2-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="1c1f2-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="1c1f2-114">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="1c1f2-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="1c1f2-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1c1f2-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
