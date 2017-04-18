---
title: "&lt;clientVia&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;clientVia&gt;
指定應建立傳輸通道的 URI。  如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ClientViaBehavior>。  
  
## 語法  
  
```  
  
<clientVia viaUri="String"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`viaUri`|字串，指定表示訊息應採用之路徑的 URI。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ClientViaElement>   
 <xref:System.ServiceModel.Description.ClientViaBehavior>