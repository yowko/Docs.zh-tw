---
title: "快取原則互動 — 最長使用期限和最小有效期限 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "以時間為基礎的快取原則"
  - "重新驗證原則"
  - "快取 [.NET Framework]，以時間為基礎的原則"
  - "快取資源的最新狀態"
  - "最長使用期限原則"
  - "最小有效期限原則"
  - "快取資源的存留期"
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 快取原則互動 — 最長使用期限和最小有效期限
若要協助確保最新內容傳回至用戶端應用程式，用戶端快取原則的互動和伺服器重新確認要求一定會產生最保守的快取原則。  本主題中的範例說明西元 1 年 1 月 4 日 . 快取和 Expires 之資源的快取原則。  
  
 下列範例會明 \+ 起化最長保留期限的快取原則 \(`maxAge`\) 和最短有效期限 \(`minFresh`\) 值的互動。  
  
-   如果快取原則設定 `maxAge` \= 2 天，而 `minFresh` 未指定，則內容在 1 月 3. 重新驗證。  
  
-   如果快取原則設定 `maxAge` \= 2 日和 `minFresh` \= 1 天，根據 `maxAge`，內容是最新的直到 1 月 3。  根據 `minFresh`，內容是最新的直到 1 月 3。  因此，內容在 1 月 3. 必須重新確認。  
  
-   如果快取原則設定 `maxAge`\= 2 日和 `minFresh` \= 2 天，根據 `maxAge`，內容是最新的直到 1 月 3。  根據 `minFresh` 內容是最新的直到 1 月 2。  因此，內容在 1 月 2. 必須重新確認。  
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)   
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [快取原則互動 — 最長使用期限和最長過時](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)