---
title: "System.ServiceModel.Channels.MsmqPoisonMessageRejected | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqPoisonMessageRejected
已拒絕有害訊息。  
  
## 描述  
 此追蹤表示遇到有害訊息，隨後拒絕該訊息。當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。被拒絕的訊息會傳回至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkId=99544) \(本頁面可能為英文\)。  
  
 如需訊息何時變為有害，以及如何設定服務來適當處理這些訊息的詳細資訊，請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkId=99546) \(本頁面可能為英文\)。如需 MSMQ 中被拒絕的訊息具有何種意義的詳細資訊，請參閱 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) \(本頁面可能為英文\)。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [有害訊息處理](http://go.microsoft.com/fwlink/?LinkId=99546)   
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)