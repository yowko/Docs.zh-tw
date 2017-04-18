---
title: "PiiLoggingNotAllowed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# PiiLoggingNotAllowed
識別碼：108  
  
 嚴重性：錯誤  
  
 分類：追蹤  
  
## 描述  
 這個事件表示沒有在記錄任何已知的 PII。  記錄已知的 PII 是不允許的。  若要允許記錄已知的 PII，請將 Machine.config 中的 "enableLoggingKnownPii" 設定為 `true`。  此事件會列出處理序名稱和處理序識別碼。  
  
## 請參閱  
 [事件記錄](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)   
 [事件一般參考](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)