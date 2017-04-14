---
title: "&lt;persistenceProvider&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;persistenceProvider&gt;
指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。  
  
## 語法  
  
```  
  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|persistenceOperationTimeout|<xref:System.TimeSpan> 值，此值會指定用於持續性作業的逾時。  預設為 "00:00:30"。|  
|類型|字串，指定要使用的持續性提供者處理站之型別。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## 備註  
 這個項目會指定持續性提供者，該提供者會用來序列化 WCF 服務的狀態。  它應該搭配在 HTTP 標頭中傳遞狀態資訊的 `wsHttpContextBinding` 使用。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>   
 <xref:System.ServiceModel.Persistence.PersistenceProvider>