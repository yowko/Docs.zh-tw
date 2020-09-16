---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: e602dd7da2a5652ec10e74fa05c73b75afec2ed4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551987"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="7e7a0-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="7e7a0-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="7e7a0-103">MSMQ 已拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7e7a0-104">描述</span><span class="sxs-lookup"><span data-stu-id="7e7a0-104">Description</span></span>  
 <span data-ttu-id="7e7a0-105">這個追蹤表示已拒絕 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="7e7a0-106">當 Windows Communication Foundation (WCF)  (搭配 NetMsmqBinding 或 MsmqIntegrationBinding) 無法處理時，MSMQ 訊息可能會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="7e7a0-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="7e7a0-108">有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="7e7a0-109">拒絕的訊息會傳回給寄件者的寄不出的 [信件佇列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="7e7a0-110">如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="7e7a0-111">如需 MSMQ 中的已拒絕訊息的詳細資訊，請參閱 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="7e7a0-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7a0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e7a0-112">See also</span></span>

- [<span data-ttu-id="7e7a0-113">追蹤</span><span class="sxs-lookup"><span data-stu-id="7e7a0-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="7e7a0-114">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="7e7a0-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7e7a0-115">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="7e7a0-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="7e7a0-116">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="7e7a0-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="7e7a0-117">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7e7a0-117">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
