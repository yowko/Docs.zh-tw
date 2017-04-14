---
title: "以時間為基礎的快取原則 | Microsoft Docs"
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
  - "快取同步處理日期原則"
  - "快取 [.NET Framework]，以時間為基礎的原則"
  - "快取資源的有效期限"
  - "時間，快取資源"
  - "最長使用期限原則"
  - "同步處理，快取"
  - "快取資源的過時"
  - "以時間為基礎的預設快取原則"
  - "最長過時原則"
  - "內容快取原則"
  - "已到期的內容"
  - "最小有效期限原則"
  - "快取資源的存留期"
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 以時間為基礎的快取原則
以時間為主的快取原則定義快取項目的有效期限使用資源擷取的時間，標頭中傳回的資源和目前的時間。  當設定為以時間為主的快取原則時，您可以使用這項 <xref:System.Net.Cache.HttpRequestCacheLevel> 時間架構原則或建立一個自訂的時間架構原則。  在使用預設時間為基礎的使用超文字傳輸通訊協定 \(HTTPS\) 和類別所取得的原則 \(HTTP\)，在指定的行為取決於實際的快取行為是由這個快取回應包含標題和 Section 13 和第 14 節 RFC 2616， [http:\/\/www.ietf.org](http://www.ietf.org/)網址為。  示範如何設定的程式碼範例的預設時間為基礎的 HTTP 資源的原則，請參閱 [HOW TO:將應用程式的預設時間為主的快取原則](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)。  如需示範如何建立及使用快取原則的程式碼範例，請參閱 [在 Web 應用程式中設定快取](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)。  
  
## 判斷快取項目的有效期限的標準  
 若要自訂以時間為主的快取原則，您可以指定下列其中一個或多個標準用來判斷快取項目的有效期限:  
  
-   最長保留期限  
  
-   最大為組態  
  
-   最短有效期限  
  
-   快取同步處理日期  
  
> [!NOTE]
>  使用預設時間為主的快取原則不應與設定應用程式的預設快取原則混淆。  這項預設時間架構原則是可以在要求中使用或應用程式層級的特定原則。  您的應用程式的預設快取原則是原則 \(以位置或以時間\)，該函式會在需要時未設定。  如需設定預設快取原則的詳細資料應用程式的詳細資訊，請參閱 <xref:System.Net.WebRequest.DefaultCachePolicy%2A>。  
  
### 最長保留期限  
 最長保留期限原則標準指定可以使用資源的快取複本的時間。  如果資源的快取複本比指定的時間還要舊，則必須先簽出它重新確認對伺服器的內容。  如果要讓資源使用最長保留期限，在項目過期之後，這個標準不被接受，除非最大過時值同時指定。  
  
### 最大為組態  
 最大為組態原則標準內容到期後指定時間可以使用資源的快取複本。  這是允許使用資源的快取原則準則，在過期之後。  
  
### 最短有效期限  
 最短有效期限原則標準指定內容到期之前的時間可以使用資源的快取複本。  此原則會讓快取項目的角色會在它的到期日之前到期，因此，最短有效期限和最大為組態設定互斥 \(Mutually Exclusive\)。  
  
## 快取同步處理日期  
 快取同步處理日期原則準則來判斷資源的快取複本時必須先簽出它重新確認對伺服器的內容。  如果內容已變更，就會快取的項目，則會從伺服器擷取，儲存在快取中，並傳回應用程式。  如果內容沒有變更，它的更新時間戳記，而應用程式取得快取的內容。  
  
 快取同步處理日期可讓您指定必須重新確認快取內容的絕對日期。  如果新快取項目在快取同步處理日期之前最後重新確認，與伺服器的重新確認仍會發生。  如果快取重新確認項目，在快取同步處理日期但失效快取項目將不會有額外的有效期限或伺服器重新確認需求之後，您可以從快取中的項目。  如果將快取同步處理日期設為未來的日期，則每次要求時都會重新確認項目，直到過了快取同步處理日期為止。  
  
 下列主題提供有關合併時間為主的快取原則準則之功能的相關資訊:  
  
-   [快取原則互動 — 最長使用期限和最長過時](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [快取原則互動 — 最長使用期限和最小有效期限](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)   
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [\<requestCaching\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)