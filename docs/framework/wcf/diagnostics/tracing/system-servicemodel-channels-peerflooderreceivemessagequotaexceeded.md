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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136baabc0760826aa9ba76dc19862c9c4b60e16e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="7fe82-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="7fe82-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="7fe82-103">訊息的傳入接收速率太高。</span><span class="sxs-lookup"><span data-stu-id="7fe82-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7fe82-104">描述</span><span class="sxs-lookup"><span data-stu-id="7fe82-104">Description</span></span>  
 <span data-ttu-id="7fe82-105">這個追蹤會發生在嘗試處理傳入訊息時。</span><span class="sxs-lookup"><span data-stu-id="7fe82-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="7fe82-106">訊息無法轉送到特定的芳鄰，因為已超過該芳鄰的配額設定。</span><span class="sxs-lookup"><span data-stu-id="7fe82-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="7fe82-107">這發生在沒有回應的芳鄰無法清除該芳鄰之擱置訊息的待處理項目。</span><span class="sxs-lookup"><span data-stu-id="7fe82-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7fe82-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="7fe82-108">Troubleshooting</span></span>  
 <span data-ttu-id="7fe82-109">降低訊息在 mesh 內傳送的速率。</span><span class="sxs-lookup"><span data-stu-id="7fe82-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe82-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="7fe82-110">See Also</span></span>  
 [<span data-ttu-id="7fe82-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="7fe82-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7fe82-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7fe82-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7fe82-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="7fe82-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
