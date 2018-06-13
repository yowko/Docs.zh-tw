---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 7dc1e4120caae7c4a592067f5e77ed4f56e82e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478162"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="2863f-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="2863f-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="2863f-103">已拒絕有害訊息。</span><span class="sxs-lookup"><span data-stu-id="2863f-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2863f-104">描述</span><span class="sxs-lookup"><span data-stu-id="2863f-104">Description</span></span>  
 <span data-ttu-id="2863f-105">此追蹤表示遇到有害訊息，隨後拒絕該訊息。</span><span class="sxs-lookup"><span data-stu-id="2863f-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="2863f-106">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="2863f-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="2863f-107">拒絕的訊息傳送至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkId=99544)。</span><span class="sxs-lookup"><span data-stu-id="2863f-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="2863f-108">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkId=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="2863f-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="2863f-109">請參閱[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)如需有關在 MSMQ 中表示的拒絕的訊息。</span><span class="sxs-lookup"><span data-stu-id="2863f-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2863f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2863f-110">See Also</span></span>  
 [<span data-ttu-id="2863f-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="2863f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2863f-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="2863f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2863f-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="2863f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="2863f-114">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="2863f-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="2863f-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="2863f-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
