---
title: "&lt;serviceTimeouts&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# &lt;serviceTimeouts&gt;
指定服務的逾時。  
  
## 語法  
  
```  
  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`transactionTimeout`|<xref:System.TimeSpan> 值，指定交易必須從用戶端流動至伺服器的時間間隔。  預設為 "00:00:00"。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>