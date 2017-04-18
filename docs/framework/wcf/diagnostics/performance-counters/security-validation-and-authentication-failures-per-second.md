---
title: "每秒的安全性驗證和驗證失敗數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# 每秒的安全性驗證和驗證失敗數
計數器名稱：每秒的安全性驗證和驗證失敗。  
  
## 描述  
 每當有訊息因為「未授權的安全性呼叫數」計數器未涵蓋的安全性問題而遭到拒絕時，這個計數器就會遞增。這類問題包括：  
  
-   無法從訊息中讀取用戶端權杖。  
  
-   用戶端權杖已經驗證失敗 \(例如密碼錯誤\)。  
  
-   簽章驗證已經失敗 \(例如訊息遭到竄改\)。  
  
-   此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。  
  
-   發生解密失敗。  
  
-   訊息中遺失某些必要的項目 \(例如遺失時間戳記或加密的資料區塊\)。  
  
-   在 TLSNEGO\/SPNEGO 交換期間發生錯誤。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) \(本頁面可能為英文\)，它的值是使用以下公式計算而來：  
  
 \(N1\-N0\)\/\(\(D1\-D0\)\/F\)