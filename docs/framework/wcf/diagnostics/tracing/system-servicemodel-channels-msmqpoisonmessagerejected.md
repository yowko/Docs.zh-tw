---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: f0e49fcfa13bb9932a88a4e79d617343c080bb3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598368"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="abc61-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="abc61-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="abc61-103">已拒絕有害訊息。</span><span class="sxs-lookup"><span data-stu-id="abc61-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="abc61-104">描述</span><span class="sxs-lookup"><span data-stu-id="abc61-104">Description</span></span>  

 <span data-ttu-id="abc61-105">此追蹤表示遇到有害訊息，隨後拒絕該訊息。</span><span class="sxs-lookup"><span data-stu-id="abc61-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="abc61-106">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="abc61-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="abc61-107">拒絕的訊息會傳回給寄件者的寄不出的[信件佇列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="abc61-108">如需訊息何時會變成有害的詳細資訊，以及如何設定您的服務來適當地處理它們，請參閱[有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="abc61-109">如需有關在 MSMQ 中拒絕的訊息意義的詳細資訊，請參閱[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))。</span><span class="sxs-lookup"><span data-stu-id="abc61-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc61-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="abc61-110">See also</span></span>

- [<span data-ttu-id="abc61-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="abc61-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="abc61-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="abc61-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="abc61-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="abc61-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="abc61-114">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="abc61-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="abc61-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="abc61-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
