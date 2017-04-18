---
title: "端點：每秒未授權的安全性呼叫數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# 端點：每秒未授權的安全性呼叫數
計數器名稱：每秒未授權的安全性呼叫數。  
  
## 描述  
 來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。  
  
 當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)