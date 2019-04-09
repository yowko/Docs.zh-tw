---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 4feeb1b57d79c7445d51f5d688b0a9f55e761542
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143386"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="25a4a-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="25a4a-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="25a4a-103">MSMQ 已拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="25a4a-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="25a4a-104">描述</span><span class="sxs-lookup"><span data-stu-id="25a4a-104">Description</span></span>  
 <span data-ttu-id="25a4a-105">這個追蹤表示已拒絕 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="25a4a-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="25a4a-106">Windows Communication Foundation (WCF) （使用與 NetMsmqBinding 或 MsmqIntegrationBinding） 無法處理它們時，可能會拒絕 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="25a4a-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="25a4a-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="25a4a-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="25a4a-108">有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="25a4a-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="25a4a-109">被拒絕的訊息會傳遞回寄件者[寄不出信件佇列](https://go.microsoft.com/fwlink/?LinkID=99544)。</span><span class="sxs-lookup"><span data-stu-id="25a4a-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="25a4a-110">請參閱[有害訊息處理](https://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及如何將服務設定為適當地處理它們。</span><span class="sxs-lookup"><span data-stu-id="25a4a-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="25a4a-111">請參閱[MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548)如需詳細資訊被拒絕的訊息表示 MSMQ 中。</span><span class="sxs-lookup"><span data-stu-id="25a4a-111">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a4a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25a4a-112">See also</span></span>

- [<span data-ttu-id="25a4a-113">追蹤</span><span class="sxs-lookup"><span data-stu-id="25a4a-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="25a4a-114">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="25a4a-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="25a4a-115">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="25a4a-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="25a4a-116">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="25a4a-116">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
- [<span data-ttu-id="25a4a-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="25a4a-117">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkID=99548)
