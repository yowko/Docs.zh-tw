---
title: "網路應用程式的快取管理 | Microsoft Docs"
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
  - "快取 [.NET Framework]，網路應用程式"
  - "網路資源，快取"
  - "網際網路，快取"
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# 網路應用程式的快取管理
這個主題及其相關的子主題描述快取使用 <xref:System.Net.WebClient>、 <xref:System.Net.WebRequest>、 <xref:System.Net.HttpWebRequest>和 <xref:System.Net.FtpWebRequest> 類別所佔用的資源。  
  
 快取區會為資源提供應用程式要求的暫時儲存區。  如果應用程式要求一次以上相同的資源，可以從快取傳回，以免再次從伺服器要求。  快取可以減少所需時間改善應用程式效能取得所要求的資源。  快取可以讓進出數縮減也會降低網路流量到伺服器。  當快取改善效能時，它會傳回資源的應用程式為過時的風險，表示它是由伺服器傳送的資源不同，如果快取不在使用中。  
  
 快取可以讓未經授權的使用者或處理序讀取敏感性資料。  快取的驗證的回應可能從快取中擷取資料，而不需要額外的授權。  如果啟用快取，請將變更為 <xref:System.Net.WebRequest.CachePolicy%2A> 至 <xref:System.Net.Cache.RequestCacheLevel> 或 <xref:System.Net.Cache.RequestCacheLevel> 加入這個要求中停用快取。  
  
 基於安全考量，快取是中介層案例建議的 **not** 。  
  
## 在本節中  
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)  
 說明何謂快取原則與如何定義。  
  
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 會根據位置的快取原則的每種可用的超文字傳輸協定 \(http、https\) 的資源。  
  
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 描述可以用來自訂以時間為主的快取原則的準則。  
  
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 描述如何以程式設計方式建立使用快取的快取原則和需求。  
  
## 參考  
 <xref:System.Net.Cache>  
 定義用於型別和列舉型別 \(Enumeration\) 定義使用 <xref:System.Net.WebRequest>、 <xref:System.Net.HttpWebRequest>和 <xref:System.Net.FtpWebRequest> 類別衍生之資源的快取原則。