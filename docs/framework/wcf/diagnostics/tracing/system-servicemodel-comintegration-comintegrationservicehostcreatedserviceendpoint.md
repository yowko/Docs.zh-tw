---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 474895e7fbcf1b9ed7ad7da6d28313ae4894f720
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="107a9-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="107a9-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="107a9-103">無法移動或刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="107a9-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="107a9-104">描述</span><span class="sxs-lookup"><span data-stu-id="107a9-104">Description</span></span>  
 <span data-ttu-id="107a9-105">此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="107a9-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="107a9-106">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 與 NetMsmqBinding 或 MsmqIntegrationBinding 一起使用，會使用 MSMQ 訊息。此追蹤與 NetMsmqBinding 或 MsmqIntegrationBinding 上選定的 `ReceiveErrorHandling` 屬性值相關。</span><span class="sxs-lookup"><span data-stu-id="107a9-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="107a9-107">此追蹤不代表整體系統失敗。</span><span class="sxs-lookup"><span data-stu-id="107a9-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="107a9-108">但是，它代表某個訊息的選定有害訊息處置作業失敗。</span><span class="sxs-lookup"><span data-stu-id="107a9-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="107a9-109">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="107a9-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107a9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="107a9-110">See Also</span></span>  
 [<span data-ttu-id="107a9-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="107a9-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="107a9-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="107a9-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="107a9-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="107a9-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
