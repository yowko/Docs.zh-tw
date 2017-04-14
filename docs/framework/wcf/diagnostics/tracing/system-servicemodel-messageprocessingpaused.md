---
title: "System.ServiceModel.MessageProcessingPaused | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.MessageProcessingPaused
System.ServiceModel.MessageProcessingPaused  
  
## 描述  
 已在處理訊息時切換執行緒。  
  
 訊息處理可能會因為下列原因而暫停：  
  
-   ConcurrencyMode 是單一或可重新進入，且服務正在處理另一個訊息。  
  
-   交易已啟用且服務正在處理另一個交易。  
  
-   同步處理內容不是最新的。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)