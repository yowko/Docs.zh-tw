---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674778"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="8a9cc-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="8a9cc-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="8a9cc-103">MSMQ 已拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8a9cc-104">描述</span><span class="sxs-lookup"><span data-stu-id="8a9cc-104">Description</span></span>  
 <span data-ttu-id="8a9cc-105">這個追蹤表示已拒絕 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="8a9cc-106">當 Windows 通信基礎 （WCF） （與 NetMmqBinding 或 Msmq 集成綁定一起使用） 無法處理 MSMQ 消息時，MSMQ 消息可能會被拒絕。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="8a9cc-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="8a9cc-108">有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="8a9cc-109">被拒絕的郵件將傳遞回寄件者[的無效信件佇列](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="8a9cc-110">有關消息何時成為病毒以及如何佈建服務以正確處理它們的詳細資訊，請參閱[毒消息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="8a9cc-111">有關被拒絕的郵件在 MSMQ 中的含義的詳細資訊，請參閱[MQMarkMessage 拒絕](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))。</span><span class="sxs-lookup"><span data-stu-id="8a9cc-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9cc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a9cc-112">See also</span></span>

- [<span data-ttu-id="8a9cc-113">追蹤</span><span class="sxs-lookup"><span data-stu-id="8a9cc-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8a9cc-114">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="8a9cc-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8a9cc-115">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="8a9cc-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="8a9cc-116">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="8a9cc-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="8a9cc-117">[MQMark消息被拒絕](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="8a9cc-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
