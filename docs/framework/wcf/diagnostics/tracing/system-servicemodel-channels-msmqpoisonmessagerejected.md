---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28924f04dc83387f49c2369c2598c028f9b8d4bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="1a650-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1a650-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="1a650-103">已拒絕有害訊息。</span><span class="sxs-lookup"><span data-stu-id="1a650-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a650-104">描述</span><span class="sxs-lookup"><span data-stu-id="1a650-104">Description</span></span>  
 <span data-ttu-id="1a650-105">此追蹤表示遇到有害訊息，隨後拒絕該訊息。</span><span class="sxs-lookup"><span data-stu-id="1a650-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="1a650-106">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="1a650-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="1a650-107">拒絕的訊息傳送至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkId=99544)。</span><span class="sxs-lookup"><span data-stu-id="1a650-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="1a650-108">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkId=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="1a650-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="1a650-109">請參閱[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)如需有關在 MSMQ 中表示的拒絕的訊息。</span><span class="sxs-lookup"><span data-stu-id="1a650-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a650-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a650-110">See Also</span></span>  
 [<span data-ttu-id="1a650-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="1a650-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1a650-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1a650-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1a650-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="1a650-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="1a650-114">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="1a650-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="1a650-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1a650-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
