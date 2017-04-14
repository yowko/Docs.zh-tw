---
title: "WCF 探索 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "探索 [WCF]"
  - "WCF [WCF], 探索"
  - "Windows Communication Foundation [WCF], 探索"
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# WCF 探索
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用 WS\-Discovery 通訊協定提供支援，讓服務以互通方式在執行階段成為可搜尋的。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務可以使用多點傳送訊息向網路公告其可用性，或是直接對探索 Proxy 伺服器公告。用戶端應用程式可搜尋網路或探索 Proxy 伺服器，來尋找符合整組準則的服務。本節中的主題提供概要並詳細說明此功能的程式設計模型。  
  
## 在本節中  
 [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 提供 WS\-Discovery 支援的概要 \(由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供\)。  
  
 [WCF 探索物件模型](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 說明物件模型中的類別以及 WS\-Discovery 支援的擴充性。  
  
 [HOW TO：以程式設計方式將探索能力加入 WCF 服務與用戶端](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 示範如何讓 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務呈現可探索狀態。  
  
 [實作探索 Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 說明用來實作探索 Proxy 的必要步驟、使用探索 Proxy 註冊的可探索服務，以及使用探索 Proxy 來尋找服務的用戶端。  
  
 [探索版本控制](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 簡要概述部分新探索功能的原型實作。同時也概要說明如何選取要使用的探索版本。  
  
 [在組態檔中設定探索](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 示範如何設定組態中的探索。  
  
 [使用探索用戶端通道](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 示範如何在寫入 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式時，使用探索用戶端通道。