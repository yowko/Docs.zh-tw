---
title: "&lt;scopes&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;scopes&gt; 的 &lt;add&gt;
加入自訂的範圍 URI，這個 URI 可用於在查詢期間篩選服務端點。  
  
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
  
|屬性|描述|  
|--------|--------|  
|範圍|URI，其中包含端點的範圍資訊，可用於比對尋找服務的準則。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。|  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>