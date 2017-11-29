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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecbbd8bc0e798388f994432ea2d3f25396f7de97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="0e644-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="0e644-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="0e644-103">MSMQ 已拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="0e644-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0e644-104">描述</span><span class="sxs-lookup"><span data-stu-id="0e644-104">Description</span></span>  
 <span data-ttu-id="0e644-105">這個追蹤表示已拒絕 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="0e644-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="0e644-106">MSMQ 訊息會在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (搭配使用 NetMsmqBinding 或 MsmqIntegrationBinding ) 無法加以處理時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="0e644-106">MSMQ messages can be rejected when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="0e644-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="0e644-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="0e644-108">有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="0e644-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="0e644-109">拒絕的訊息傳送至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkID=99544)。</span><span class="sxs-lookup"><span data-stu-id="0e644-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="0e644-110">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="0e644-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="0e644-111">請參閱[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)如需有關在 MSMQ 中表示的拒絕的訊息。</span><span class="sxs-lookup"><span data-stu-id="0e644-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e644-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e644-112">See Also</span></span>  
 [<span data-ttu-id="0e644-113">追蹤</span><span class="sxs-lookup"><span data-stu-id="0e644-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0e644-114">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="0e644-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0e644-115">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="0e644-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="0e644-116">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="0e644-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="0e644-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="0e644-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
