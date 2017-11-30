---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2931eec5646b44eea19d70b11eb43c056b0ee0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="df216-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="df216-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="df216-103">訊息的傳入接收速率太高。</span><span class="sxs-lookup"><span data-stu-id="df216-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="df216-104">描述</span><span class="sxs-lookup"><span data-stu-id="df216-104">Description</span></span>  
 <span data-ttu-id="df216-105">這個追蹤會發生在嘗試處理傳入訊息時。</span><span class="sxs-lookup"><span data-stu-id="df216-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="df216-106">訊息無法轉送到特定的芳鄰，因為已超過該芳鄰的配額設定。</span><span class="sxs-lookup"><span data-stu-id="df216-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="df216-107">這發生在沒有回應的芳鄰無法清除該芳鄰之擱置訊息的待處理項目。</span><span class="sxs-lookup"><span data-stu-id="df216-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="df216-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="df216-108">Troubleshooting</span></span>  
 <span data-ttu-id="df216-109">降低訊息在 mesh 內傳送的速率。</span><span class="sxs-lookup"><span data-stu-id="df216-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df216-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df216-110">See Also</span></span>  
 [<span data-ttu-id="df216-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="df216-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="df216-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="df216-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="df216-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="df216-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
