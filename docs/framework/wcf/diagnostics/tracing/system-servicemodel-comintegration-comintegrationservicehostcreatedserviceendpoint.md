---
title: "System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
無法移動或刪除訊息。  
  
## 描述  
 此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。  
  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 與 NetMsmqBinding 或 MsmqIntegrationBinding 一起使用，會使用 MSMQ 訊息。此追蹤與 NetMsmqBinding 或 MsmqIntegrationBinding 上選定的 `ReceiveErrorHandling` 屬性值相關。  
  
 此追蹤不代表整體系統失敗。  但是，它代表某個訊息的選定有害訊息處置作業失敗。  如需訊息何時變為有害，以及如何設定服務來適當處理這些訊息的詳細資訊，請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)