---
title: "以位置為基礎的快取原則 | Microsoft Docs"
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
  - "可用時快取原則"
  - "重新載入原則"
  - "以位置為基礎的快取原則"
  - "僅限快取原則"
  - "本機快取"
  - "中繼快取"
  - "無快取且無存放區原則"
  - "快取 [.NET Framework]，以位置為基礎的原則"
  - "重新驗證原則"
  - "快取資源的重新整理"
  - "僅限快取或下一個快取原則"
  - "重新整理原則"
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 以位置為基礎的快取原則
以位置為主的快取原則會定義以有效的快取項目的有效期限要求的資源可能是從中的位置。  如果使用它不違反指定伺服器的重新驗證要求，則快取的資源是有效的。  您可以使用 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 類別建構函式，以位置為主的快取原則以程式設計方式建立的。  使用 <xref:System.Net.Cache.RequestCacheLevel> 或 <xref:System.Net.Cache.HttpRequestCacheLevel> 列舉值，以位置之原則的型別傳遞至建構函式。  如需建立以位置的快取原則的程式碼範例，請參閱 [HOW TO:設定應用程式的以位置為主的快取原則](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md)。  下列章節說明以位置的快取原則的每種類型的超文字傳輸協定 \(http、https\) 資源的。  
  
## 若有快取原則  
 如果需要有效的資源在本機快取，則會使用快取資源;否則，會將資源要求傳送至伺服器。  如果要求的資源可以在用戶端與伺服器之間的任何快取，要求可以透過中繼快取內容。  
  
## 只快取原則  
 如果有效要求資源的本機快取中，就會使用快取的資源。  當這個快取原則層級指定時， <xref:System.Net.WebException> 擲回例外狀況，如果項目不在本機快取。  
  
## 快取或下一項只快取原則  
 如果需要有效的資源在本機快取或中繼快取區域網路上，使用快取的資源。  否則會擲回 <xref:System.Net.WebException> 例外狀況。  如果只使用快取的快取控制項指示詞，在快取通訊協定中 HTTP，達到此效果。  
  
## 沒有快取沒有原則存放區  
 所要求資源的所有快取從未使用及在任何快取從未放置。  如果所要求的資源出現在本機快取，則會將它移除。  這個原則層級表示中繼快取它們也應該移除資源。  使用無存放區快取控制項指示詞，在快取通訊協定中 HTTP，達到此效果。  
  
## 重新整理原則  
 所要求資源的本機快取之外，，，如果是從伺服器取得或在快取中找到才能使用。  透過中繼快取滿足要求之前，該快取必須使用伺服器重新確認其快取的項目。  在快取通訊協定中，這個 HTTP 達成使用 max\-age \= 0 快取控制項指示詞和無快取 Pragma 標頭。  
  
## 重新載入原則  
 必須從伺服器取得要求的資源。  回應可以在本機快取中。  使用 no\-cache 快取控制項指示詞和無快取 Pragma 標頭，在快取通訊協定中 HTTP，達到此效果。  
  
## Revalidate 原則  
 將快取中資源的複本與伺服器上的複本相比較。  如果伺服器上的複本較新，則會使用它滿足要求並取代快取中的複本。  如果快取中的複本與伺服器複本相同，則會使用快取的複本。  在 HTTP 快取通訊協定中，可以使用條件要求達到此效果。  
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)   
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [\<requestCaching\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)