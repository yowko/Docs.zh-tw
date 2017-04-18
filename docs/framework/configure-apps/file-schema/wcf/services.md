---
title: "&lt;服務&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;服務&gt;
服務定義於組態檔的 `services` 區段中。  各服務都有自己的 `service` 組態區段。  
  
 \<system.ServiceModel\>  
  
## 語法  
  
```  
  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<服務\>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|定義特定服務的服務合約、行為和端點。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|所有 Windows Communication Foundation \(WCF\) 組態項目的根項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServicesSection>