---
title: "HOW TO：判斷探查要求的探索版本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f51f48d6eefcc0f8ae5129526477d6e2a5b2385
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="92920-102">HOW TO：判斷探查要求的探索版本</span><span class="sxs-lookup"><span data-stu-id="92920-102">How to:Determine the Discovery Version of a Probe Request</span></span>
<span data-ttu-id="92920-103">探索 Proxy 可能會公開使用不同探索版本的多個探索端點。</span><span class="sxs-lookup"><span data-stu-id="92920-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="92920-104">當 UDP 多點傳送探查要求到達 Proxy 時，Proxy 應該使用多點傳送抑制訊息回應。</span><span class="sxs-lookup"><span data-stu-id="92920-104">When a UDP multicast Probe request arrives at the proxy the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="92920-105">若要這樣做，必須知道要求的探索版本。</span><span class="sxs-lookup"><span data-stu-id="92920-105">In order to do this it would have to know the discovery version of the request.</span></span>  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="92920-106">若要判斷探查要求的探索版本</span><span class="sxs-lookup"><span data-stu-id="92920-106">To Determine the Discovery Version of a Probe Request</span></span>  
  
1.  <span data-ttu-id="92920-107">在回應探查要求的方法 (例如 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) 中，使用靜態 <xref:System.ServiceModel.OperationContext.Current%2A> 屬性來搜尋  <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="92920-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) use the static <xref:System.ServiceModel.OperationContext.Current%2A> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> as shown in the following code.</span></span>  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="92920-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="92920-108">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [<span data-ttu-id="92920-109">實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="92920-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [<span data-ttu-id="92920-110">探索 Proxy 範例</span><span class="sxs-lookup"><span data-stu-id="92920-110">Discovery Proxy Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
