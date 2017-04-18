---
title: "竄改 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 竄改
*竄改*是一種修改訊息的動作，或是訊息的傳遞，以及將修改的訊息用於不是原本設計的目的。  
  
## 請勿停用 WS\-Addressing  
 WS\-Addressing 規格會提供每個訊息的位址標頭，允許訊息收件者驗證訊息的寄件者。您可以將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，藉此停用這個功能。  
  
 當安全性模式設為「訊息」，而 WS\-Addressing 停用時，攻擊者可能會從用戶端取得要求，然後傳送給另一項服務，使該服務無法偵測來自原始用戶端的訊息。如此一來，第一項服務就可在與第二項服務交談時假裝為用戶端。  
  
 為減少這種情況發生，絕不要將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，同時避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，例如靜態 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 屬性，這類屬性會將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。  
  
## 請參閱  
 [安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [資訊洩露](../../../../docs/framework/wcf/feature-details/information-disclosure.md)   
 [權限提高](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)   
 [阻斷服務](../../../../docs/framework/wcf/feature-details/denial-of-service.md)   
 [不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)   
 [重新執行攻擊](../../../../docs/framework/wcf/feature-details/replay-attacks.md)