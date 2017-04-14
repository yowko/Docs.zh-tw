---
title: "&lt;dispatcherSynchronization&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;dispatcherSynchronization&gt;
指定可讓服務以非同步方式傳送回覆的端點行為。  
  
## 語法  
  
```  
  
<dispatcherSynchronizationBehavior   
   asynchronousSendEnabled=”Boolean”  
   maxPendingReceives="Integer" />  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|asynchronousSendEnabled|布林值，指定是否啟用非同步傳送行為。|  
|`maxPendingReceives`|整數，指定可在通道發行之並行接收的數目。<br /><br /> 唯有在您正確設定服務節流閥行為後，才可設定這個值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.DispatcherSynchronizationBehaviorElement>   
 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>