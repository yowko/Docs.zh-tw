---
title: "&lt;webScriptEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;webScriptEndpoint&gt;
這個組態項目定義標準端點，該端點具有固定的 [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) 繫結，會自動加入 [\<enableWebScript\>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) 行為。  撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。  
  
## 語法  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <webScriptEndpoint>   
          <standardEndpoint  
             webEndpointType=”String”/>        
       </webScriptEndpoint>   
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|webEndpointType|字串，指定端點的型別。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 \(位址、繫結、合約\)。|  
  
## 請參閱  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>   
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>