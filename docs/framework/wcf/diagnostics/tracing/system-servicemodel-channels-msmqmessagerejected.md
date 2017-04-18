---
title: "System.ServiceModel.Channels.MsmqMessageRejected | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMessageRejected
MSMQ 已拒絕訊息。  
  
## 描述  
 這個追蹤表示已拒絕 MSMQ 訊息。  
  
 MSMQ 訊息會在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] \(搭配使用 NetMsmqBinding 或 MsmqIntegrationBinding \) 無法加以處理時遭到拒絕。這類訊息稱為有害訊息。有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。被拒絕的訊息會傳回至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkID=99544) \(本頁面可能為英文\)。  
  
 如需訊息何時變為有害，以及如何設定服務來適當處理這些訊息的詳細資訊，請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546) \(本頁面可能為英文\)。  
  
 如需 MSMQ 中被拒絕的訊息具有何種意義的詳細資訊，請參閱 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) \(本頁面可能為英文\)。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)   
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)