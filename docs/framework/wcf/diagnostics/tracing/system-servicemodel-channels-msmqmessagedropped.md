---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674804"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="d3937-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="d3937-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="d3937-103">MSMQ 已捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="d3937-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d3937-104">描述</span><span class="sxs-lookup"><span data-stu-id="d3937-104">Description</span></span>  
 <span data-ttu-id="d3937-105">此追蹤表示已捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="d3937-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="d3937-106">當 Windows 通信基礎 （WCF） （與 NetMmqBinding 或 Msmq 集成綁定一起使用） 無法處理它們時，MSMQ 消息可以被刪除。</span><span class="sxs-lookup"><span data-stu-id="d3937-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="d3937-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="d3937-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="d3937-108">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。</span><span class="sxs-lookup"><span data-stu-id="d3937-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="d3937-109">捨棄的訊息會從佇列中移除，無法再復原。</span><span class="sxs-lookup"><span data-stu-id="d3937-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="d3937-110">有關消息何時成為病毒以及如何佈建服務以正確處理它們的詳細資訊，請參閱[毒消息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="d3937-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3937-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3937-111">See also</span></span>

- [<span data-ttu-id="d3937-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="d3937-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="d3937-113">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="d3937-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d3937-114">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="d3937-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="d3937-115">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="d3937-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
