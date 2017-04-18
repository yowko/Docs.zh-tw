---
title: "&lt;baseAddresses&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;baseAddresses&gt;
代表 `baseAddress` 項目的集合，這些項目是自我裝載環境中之服務主機的基底位址。  如果基底位址存在，即可以相對於基底位址的位址設定端點。  
  
## 語法  
  
```  
  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|指定由服務主機使用之基底位址的組態項目。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<Host \- 主應用程式\>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|指定服務主機設定的組態項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.HostElement>   
 <xref:System.ServiceModel.ServiceHost>   
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>   
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)