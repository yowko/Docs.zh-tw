---
title: "&lt;scopes&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;scopes&gt;
包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。  
  
## 語法  
  
```  
  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="String">  
      <endpointDiscovery enable="Boolean">  
        <scopes>  
          <add scope="URI"/>  
        </scopes>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|屬性|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|加入端點的範圍資訊，可用於比對尋找服務的準則。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<endpointDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。|  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>