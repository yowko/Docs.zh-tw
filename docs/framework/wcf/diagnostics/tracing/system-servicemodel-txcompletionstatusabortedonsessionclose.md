---
title: "System.ServiceModel.TxCompletionStatusAbortedOnSessionClose | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
指定的交易已中止，因為當工作階段關閉時，交易未完成，並且 TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute 設定為 false。  
  
## 描述  
 如果目前使用中的工作階段已關閉，且交易尚未完成，加上 TransactionAutoCompleteOnSessionClose 設定為 `false`，則會進行追蹤。  
  
## 疑難排解  
 這個追蹤表示存在應該進行調查的潛在應用程式 Bug。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)