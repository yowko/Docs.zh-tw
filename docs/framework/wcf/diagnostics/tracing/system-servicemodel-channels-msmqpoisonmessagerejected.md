---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 69da35f65e04a3cba15885c4fe6e57d63762cb1c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260340"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="50a48-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="50a48-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>

<span data-ttu-id="50a48-103">已拒絕有害訊息。</span><span class="sxs-lookup"><span data-stu-id="50a48-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="50a48-104">描述</span><span class="sxs-lookup"><span data-stu-id="50a48-104">Description</span></span>  

 <span data-ttu-id="50a48-105">此追蹤表示遇到有害訊息，隨後拒絕該訊息。</span><span class="sxs-lookup"><span data-stu-id="50a48-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="50a48-106">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="50a48-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="50a48-107">拒絕的訊息會傳回給寄件者的寄不出的 [信件佇列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。</span><span class="sxs-lookup"><span data-stu-id="50a48-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="50a48-108">如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="50a48-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="50a48-109">如需 MSMQ 中的已拒絕訊息的詳細資訊，請參閱 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="50a48-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a48-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50a48-110">See also</span></span>

- [<span data-ttu-id="50a48-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="50a48-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="50a48-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="50a48-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="50a48-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="50a48-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="50a48-114">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="50a48-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="50a48-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="50a48-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
