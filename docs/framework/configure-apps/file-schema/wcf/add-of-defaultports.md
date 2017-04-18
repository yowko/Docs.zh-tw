---
title: "&lt;defaultPorts&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;defaultPorts&gt; 的 &lt;add&gt;
預設通訊端點，用戶端應用程式會接聽這個端點。  
  
## 語法  
  
```  
  
<useRequestHeadersForMetadataAddress>  
   <defaultPorts>  
      <add port="Integer" scheme="String" />  
   </defaultPorts>  
</useRequestHeadersForMetadataAddress>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|連接埠|指定預設通訊埠編號的整數。|  
|scheme|指定與通訊連接埠相關之通訊協定設定群組的字串。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<defaultPorts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>