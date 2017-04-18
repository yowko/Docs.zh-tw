---
title: "服務：每秒未授權的安全性呼叫數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# 服務：每秒未授權的安全性呼叫數
計數器名稱：每秒未授權的安全性呼叫數  
  
## 描述  
 來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。  
  
 當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649) \(本頁面可能為英文\)，它的值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)