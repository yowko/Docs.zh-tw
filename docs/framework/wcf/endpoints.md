---
title: "Windows Communication Foundation 端點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "端點 [WCF]"
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Windows Communication Foundation 端點
所有與 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務的通訊都是透過服務的「*端點*」\(Endpoint\) 發生的。  端點針對 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務所提供的功能提供了用戶端存取。  
  
 如需有關如何建立端點的概觀，請參閱[端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)。  每個端點包含：  
  
-   指出可在何處找到端點的位址。  
  
-   指定用戶端可以如何與端點通訊的繫結。  
  
-   識別可用方法的合約。  
  
 如需有關如何指定端點之這些個別部分的說明，請參閱：  
  
-   [指定端點位址](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [使用繫結來設定服務和用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [設計與實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## 在本節中  
 [端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 說明端點的結構，並且摘要說明如何透過組態與程式碼來定義端點，以及如何使用執行階段所提供的預設端點、繫結和行為。  
  
 [指定端點位址](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 說明與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的通訊如何透過端點來進行。  
  
 [HOW TO：在組態中建立服務端點](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 示範如何在組態中建立服務端點。  
  
 [HOW TO：在程式碼中建立服務端點](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 示範如何在程式碼中建立服務端點。  
  
 [發行中繼資料端點](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 示範如何在組態和程式碼中發行中繼資料端點，以發行中繼資料。  
  
## 參考  
 <xref:System.ServiceModel.EndpointAddress>  
  
## 相關章節  
 [基本程式設計週期](../../../docs/framework/wcf/basic-programming-lifecycle.md)