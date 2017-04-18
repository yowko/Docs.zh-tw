---
title: "System.ServiceModel.Channels.MsmqMessageDropped | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMessageDropped
MSMQ 已捨棄訊息。  
  
## 描述  
 此追蹤表示已捨棄 MSMQ 訊息。當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] \(與 NetMsmqBinding 或 MsmqIntegrationBinding 配合使用\) 無法處理 MSMQ 訊息時，就會捨棄 MSMQ 訊息。這類訊息稱為有害訊息。  
  
 當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。捨棄的訊息會從佇列中移除，無法再復原。  
  
 如需訊息何時變為有害，以及如何設定服務來適當處理這些訊息的詳細資訊，請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)