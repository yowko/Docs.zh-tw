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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ff5d45997456c12d0292176771ad3c332f6c043
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>HOW TO：判斷探查要求的探索版本
探索 Proxy 可能會公開使用不同探索版本的多個探索端點。 當 UDP 多點傳送探查要求到達 Proxy 時，Proxy 應該使用多點傳送抑制訊息回應。 若要這樣做，必須知道要求的探索版本。  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>若要判斷探查要求的探索版本  
  
1.  在回應探查要求的方法 (例如 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) 中，使用靜態 <xref:System.ServiceModel.OperationContext.Current%2A> 屬性來搜尋  <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>，如下列程式碼所示。  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [實作探索 Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [探索 Proxy 範例](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
