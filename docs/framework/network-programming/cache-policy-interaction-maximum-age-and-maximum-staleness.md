---
title: "快取原則互動 — 最長使用期限和最長過時 | Microsoft Docs"
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
  - "最長過時"
  - "快取資源的有效期限"
  - "時間，快取資源"
  - "最長使用期限原則"
  - "快取資源的過時"
  - "快取資源的存留期"
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 快取原則互動 — 最長使用期限和最長過時
若要協助確保最新內容傳回至用戶端應用程式，用戶端快取原則的互動和伺服器重新確認要求一定會產生最保守的快取原則。  本主題中的範例說明西元 1 年 1 月 4 日 . 快取和 Expires 之資源的快取原則。  
  
 在下列範例中，最大過時值 \(`maxStale`\) 與最長保留期限 \(`maxAge`\) 搭配使用:  
  
-   如果快取原則設定 `maxAge` \= 5 天，而不指定 `maxStale` 值，視 `maxAge` 值，內容可直到 1 月 6。  不過，根據伺服器的重新驗證要求，內容在 1 月 4. 過期。  由於內容到期日較為保守的 \(快取\)，其優先順序會比 `maxAge` 原則。  因此，內容在 1 月 4 日過期且必須重新確認，即使它的最長保留期限無法到達。  
  
-   如果快取原則設定 `maxAge` \= 5 日和 `maxStale` \= 3 天，根據 `maxAge` 值，內容可直到 1 月 6。  根據 `maxStale` 值，內容可直到 1 月 7。  因此，內容在 1 月 6. 取得重新驗證。  
  
-   如果快取原則設定 `maxAge` \= 5 日和 `maxStale` \= 1 天，根據 `maxAge` 值，內容可直到 1 月 6。  根據 `maxStale` 值，內容可直到 1 月 5。  因此，內容在 1 月 5. 取得重新驗證。  
  
 當最長保留期限小於內容到期日時為，較為保守的快取行為永遠克服了，而最大過時值就沒有作用。  下列範例說明如何設定最大為組態 \(`maxStale`\) 值的效果，而最長保留期限 \(`maxAge`\) 為止，內容到期之前:  
  
-   如果快取原則設定 `maxAge` \= 1 天，而不會 `maxStale` 值指定值，內容在 1 月 2 日重新確認，即使尚未過期。  
  
-   如果快取原則設定`maxAge` \= 1 日和 `maxStale` \= 3 天，內容在 1 月 2 日重新確認強制執行較為保守的原則設定。  
  
-   如果快取原則設定 `maxAge` \= 1 日和 `maxStale` \= 1 天，內容在 1 月 2. 重新驗證。  
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)   
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [快取原則互動 — 最長使用期限和最小有效期限](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)