---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 562399c1d45dc73c7c88bd165e9f95ee1bcfa19d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125077"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="979b3-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="979b3-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="979b3-103">已拒絕有害訊息。</span><span class="sxs-lookup"><span data-stu-id="979b3-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="979b3-104">描述</span><span class="sxs-lookup"><span data-stu-id="979b3-104">Description</span></span>  
 <span data-ttu-id="979b3-105">此追蹤表示遇到有害訊息，隨後拒絕該訊息。</span><span class="sxs-lookup"><span data-stu-id="979b3-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="979b3-106">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="979b3-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="979b3-107">被拒絕的訊息會傳遞回寄件者[寄不出信件佇列](https://go.microsoft.com/fwlink/?LinkId=99544)。</span><span class="sxs-lookup"><span data-stu-id="979b3-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="979b3-108">請參閱[有害訊息處理](https://go.microsoft.com/fwlink/?LinkId=99546)如需詳細資訊訊息何時變為有害，以及如何將服務設定為適當地處理它們。</span><span class="sxs-lookup"><span data-stu-id="979b3-108">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="979b3-109">請參閱[MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548)如需詳細資訊被拒絕的訊息表示 MSMQ 中。</span><span class="sxs-lookup"><span data-stu-id="979b3-109">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979b3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="979b3-110">See also</span></span>

- [<span data-ttu-id="979b3-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="979b3-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="979b3-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="979b3-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="979b3-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="979b3-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="979b3-114">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="979b3-114">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkId=99546)
- [<span data-ttu-id="979b3-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="979b3-115">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkId=99548)
