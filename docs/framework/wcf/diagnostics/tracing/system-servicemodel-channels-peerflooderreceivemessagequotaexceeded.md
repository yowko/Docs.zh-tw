---
title: "System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
訊息的傳入接收速率太高。  
  
## 描述  
 這個追蹤會發生在嘗試處理傳入訊息時。  訊息無法轉送到特定的芳鄰，因為已超過該芳鄰的配額設定。  這發生在沒有回應的芳鄰無法清除該芳鄰之擱置訊息的待處理項目。  
  
## 疑難排解  
 降低訊息在 mesh 內傳送的速率。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)