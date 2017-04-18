---
title: "&lt;mexEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;mexEndpoint&gt;
這個組態項目會定義具有固定 IMetadataExchange 合約的標準端點。  由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。  
  
## 語法  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <mexEndpoint>   
          <standardEndpoint  
                  name="String" />   
       </announcementEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|字串，這個字串會指定標準端點之組態的名稱。  這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 \(位址、繫結、合約\)。|