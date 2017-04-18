---
title: "Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
WS\-AT 通訊協定服務無法登錄控制通訊協定的參與者。  
  
## 描述  
 如果 MSDTC 偵測到無效的登錄要求則會進行追蹤。這種情形可能是因為多個完成登錄要求和內部錯誤所造成。  
  
## 疑難排解  
 請勿嘗試多次登錄完成。同時，檢查追蹤訊息內的狀態字串，以判斷是否有任何可執行動作的項目存在。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)