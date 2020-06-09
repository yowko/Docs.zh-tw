---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578047"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="dd5ba-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="dd5ba-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="dd5ba-103">MSMQ 已拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dd5ba-104">描述</span><span class="sxs-lookup"><span data-stu-id="dd5ba-104">Description</span></span>  
 <span data-ttu-id="dd5ba-105">這個追蹤表示已拒絕 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="dd5ba-106">當 Windows Communication Foundation （WCF）（搭配 NetMsmqBinding 或 MsmqIntegrationBinding 使用）無法處理時，MSMQ 訊息可能會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="dd5ba-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="dd5ba-108">有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="dd5ba-109">拒絕的訊息會傳回給寄件者的寄不出的[信件佇列](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="dd5ba-110">如需訊息何時會變成有害的詳細資訊，以及如何設定您的服務來適當地處理它們，請參閱[有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="dd5ba-111">如需有關在 MSMQ 中拒絕的訊息意義的詳細資訊，請參閱[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))。</span><span class="sxs-lookup"><span data-stu-id="dd5ba-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5ba-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5ba-112">See also</span></span>

- [<span data-ttu-id="dd5ba-113">追蹤</span><span class="sxs-lookup"><span data-stu-id="dd5ba-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="dd5ba-114">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="dd5ba-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dd5ba-115">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="dd5ba-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="dd5ba-116">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="dd5ba-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="dd5ba-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="dd5ba-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
