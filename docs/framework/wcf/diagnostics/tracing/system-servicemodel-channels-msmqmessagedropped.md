---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d4b819b47d682a81bdcc031cc6b09604b072be7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="9fd6b-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="9fd6b-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="9fd6b-103">MSMQ 已捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="9fd6b-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9fd6b-104">描述</span><span class="sxs-lookup"><span data-stu-id="9fd6b-104">Description</span></span>  
 <span data-ttu-id="9fd6b-105">此追蹤表示已捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="9fd6b-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="9fd6b-106">當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (與 NetMsmqBinding 或 MsmqIntegrationBinding 配合使用) 無法處理 MSMQ 訊息時，就會捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="9fd6b-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="9fd6b-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="9fd6b-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="9fd6b-108">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。</span><span class="sxs-lookup"><span data-stu-id="9fd6b-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="9fd6b-109">捨棄的訊息會從佇列中移除，無法再復原。</span><span class="sxs-lookup"><span data-stu-id="9fd6b-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="9fd6b-110">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="9fd6b-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd6b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fd6b-111">See Also</span></span>  
 [<span data-ttu-id="9fd6b-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="9fd6b-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9fd6b-113">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="9fd6b-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9fd6b-114">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="9fd6b-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="9fd6b-115">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="9fd6b-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
