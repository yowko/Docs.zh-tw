---
title: "&lt;synchronousReceive&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;synchronousReceive&gt; 項目
這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。  它沒有任何屬性或子項目。  
  
## 語法  
  
```  
  
<synchronousReceive />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## 備註  
 您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 會發出新的執行緒，以提取每個接受的通道。  如果有許多個通道，執行緒可能會用完。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>   
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>