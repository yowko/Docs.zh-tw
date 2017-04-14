---
title: "發行中繼資料端點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 發行中繼資料端點
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務會藉由發行一或多個中繼資料端點以發行中繼資料。發行服務中繼資料會使用標準化的通訊協定 \(例如 WS\-MetadataExchange \(MEX\) 和 HTTP\/GET 要求\) 來提供中繼資料。中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約，並且能夠透過組態或程式碼新增至服務主機。若要啟用發行中繼資料端點，您必須將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為新增至服務。  
  
## 本章節內容  
 [HOW TO：使用組態檔發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 示範如何設定 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務來發行中繼資料，以便讓用戶端能夠使用 `?wsdl` 查詢字串透過 WS\-MetadataExchange 或 HTTP\/GET 要求擷取中繼資料。  
  
 [HOW TO：使用程式碼發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 示範如何在程式碼中啟用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的中繼資料發行，以便讓用戶端能夠使用 `?wsdl` 查詢字串透過 WS\-MetadataExchange 或 HTTP\/GET 要求擷取中繼資料。  
  
## 請參閱  
 [發行中繼資料](../../../docs/framework/wcf/feature-details/publishing-metadata.md)