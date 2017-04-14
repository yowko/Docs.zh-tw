---
title: "System.ServiceModel.Channels.FailedAcceptFromPool | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.FailedAcceptFromPool
嘗試重複使用共用連線失敗。  在指定的逾時期間內，進行另一次嘗試。  
  
## 描述  
 這個告知性追蹤表示嘗試重複使用共用連線時發生錯誤。  因為共用連線不相容、尚未就緒或不是使用中，可能就會發生這個問題。  若在指定的逾時值之內額外嘗試重複使用其他的共用連線，會建立新的連線，以防找不到可用的連線。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)