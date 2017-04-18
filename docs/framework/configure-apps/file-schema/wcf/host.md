---
title: "&lt;Host - 主應用程式&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;Host - 主應用程式&gt;
指定服務主機的設定。  
  
## 語法  
  
```  
  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
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
|[\<baseAddresses\>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|`baseAddress` 項目的集合，指定服務主機使用的基底位址。|  
|[\<timeOuts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|組態項目，指定允許服務主機開啟或關閉的時間間隔。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<服務\>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務的設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.HostElement>   
 <xref:System.ServiceModel.ServiceHost>   
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)