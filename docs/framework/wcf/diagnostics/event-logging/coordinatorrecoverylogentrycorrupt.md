---
title: "CoordinatorRecoveryLogEntryCorrupt | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# CoordinatorRecoveryLogEntryCorrupt
ID：139  
  
 嚴重性：錯誤  
  
 分類：TransactionBridge  
  
## 描述  
 此事件表示協調器修復記錄項目損毀，且無法還原序列化。這個錯誤可能會造成資料遺失。事件會列出交易識別碼、修復資料 \(以 Base64 編碼\)、例外狀況、處理序名稱和處理序識別碼。  
  
## 請參閱  
 [事件記錄](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)   
 [事件一般參考](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)