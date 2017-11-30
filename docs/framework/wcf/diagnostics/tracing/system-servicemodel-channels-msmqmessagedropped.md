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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55b489bcad85eff5adba16f6f40493c88e476505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="0f894-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="0f894-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="0f894-103">MSMQ 已捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="0f894-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f894-104">描述</span><span class="sxs-lookup"><span data-stu-id="0f894-104">Description</span></span>  
 <span data-ttu-id="0f894-105">此追蹤表示已捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="0f894-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="0f894-106">當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (與 NetMsmqBinding 或 MsmqIntegrationBinding 配合使用) 無法處理 MSMQ 訊息時，就會捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="0f894-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="0f894-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="0f894-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="0f894-108">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。</span><span class="sxs-lookup"><span data-stu-id="0f894-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="0f894-109">捨棄的訊息會從佇列中移除，無法再復原。</span><span class="sxs-lookup"><span data-stu-id="0f894-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="0f894-110">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="0f894-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f894-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f894-111">See Also</span></span>  
 [<span data-ttu-id="0f894-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="0f894-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0f894-113">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="0f894-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0f894-114">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="0f894-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="0f894-115">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="0f894-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
