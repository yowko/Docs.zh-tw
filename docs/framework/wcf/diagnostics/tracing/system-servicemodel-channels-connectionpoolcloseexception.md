---
title: "System.ServiceModel.Channels.ConnectionPoolCloseException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# System.ServiceModel.Channels.ConnectionPoolCloseException
關閉此連線集區中的連線時發生例外狀況。  
  
## 描述  
 這個錯誤層級追蹤指出，在關閉由 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 的連接共用功能所使用的連線集區時發生錯誤。可能是因為 CloseTimeout 內的某個共用連線或某組共用連線未成功關閉。擲回此例外狀況時，同集區內其餘未關閉的連線都會中止，其他集區內未關閉的連線則會被放棄。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)