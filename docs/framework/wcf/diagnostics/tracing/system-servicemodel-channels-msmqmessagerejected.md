---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b433e5e3c0a961098f82ad601d127290b1d6bd73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="f3154-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f3154-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="f3154-103">MSMQ 已拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="f3154-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f3154-104">描述</span><span class="sxs-lookup"><span data-stu-id="f3154-104">Description</span></span>  
 <span data-ttu-id="f3154-105">這個追蹤表示已拒絕 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="f3154-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="f3154-106">MSMQ 訊息會在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (搭配使用 NetMsmqBinding 或 MsmqIntegrationBinding ) 無法加以處理時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="f3154-106">MSMQ messages can be rejected when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="f3154-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="f3154-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="f3154-108">有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="f3154-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="f3154-109">拒絕的訊息傳送至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkID=99544)。</span><span class="sxs-lookup"><span data-stu-id="f3154-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="f3154-110">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="f3154-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="f3154-111">請參閱[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)如需有關在 MSMQ 中表示的拒絕的訊息。</span><span class="sxs-lookup"><span data-stu-id="f3154-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3154-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3154-112">See Also</span></span>  
 [<span data-ttu-id="f3154-113">追蹤</span><span class="sxs-lookup"><span data-stu-id="f3154-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f3154-114">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="f3154-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f3154-115">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="f3154-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="f3154-116">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="f3154-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="f3154-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f3154-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
