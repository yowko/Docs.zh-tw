---
title: "&lt;timeOuts&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;timeOuts&gt;
表示組態項目，指定允許服務主機開啟或關閉的時間間隔。  
  
## 語法  
  
```  
  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`closeTimeout`|<xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。|  
|`openTimeout`|<xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<Host \- 主應用程式\>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|指定服務主機設定的組態項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.HostElement>   
 <xref:System.ServiceModel.ServiceHost>   
 <xref:System.ServiceModel.ServiceHost.CloseTimeout%2A>   
 <xref:System.ServiceModel.ServiceHost.OpenTimeout%2A>   
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)