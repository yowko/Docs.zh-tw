---
title: "HOW TO：判斷探查要求的探索版本 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：判斷探查要求的探索版本
探索 Proxy 可能會公開使用不同探索版本的多個探索端點。  當 UDP 多點傳送探查要求到達 Proxy 時，Proxy 應該使用多點傳送抑制訊息回應。  若要這樣做，必須知道要求的探索版本。  
  
### 若要判斷探查要求的探索版本  
  
1.  在回應探查要求的方法 \(例如 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>\) 中，使用靜態 <xref:System.ServiceModel.OperationContext.Current%2A> 屬性來搜尋  <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>，如下列程式碼所示。  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
  
    ```  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>   
 [實作探索 Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)   
 [探索 Proxy 範例](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)