---
title: "網路應用程式的快取管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b960942d17e402b333354bbd932cf63d11b1209f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cache-management-for-network-applications"></a>網路應用程式的快取管理
本主題和其相關子主題描述如何使用 <xref:System.Net.WebClient>、<xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest> 和 <xref:System.Net.FtpWebRequest> 類別所取得資源的快取。  
  
 快取提供應用程式已要求的資源暫時儲存位置。 如果應用程式多次要求相同的資源，則可以從快取傳回資源，避免從伺服器重新要求它的額外負荷。 快取可以透過減少取得所要求資源所需的時間，來改善應用程式效能。 快取也可以減少往返伺服器的次數，來降低網路流量。 雖然快取可改善效能，但是會增加傳回給應用程式的資源過時的風險，這表示它與未使用快取時由伺服器所傳送的資源不同。  
  
 快取可讓未經授權的使用者或處理序讀取敏感性資料。 可以從快取擷取所快取的已驗證回應，而不需要額外授權。 如果啟用快取，請將 <xref:System.Net.WebRequest.CachePolicy%2A> 變更為 <xref:System.Net.Cache.RequestCacheLevel.BypassCache> 或 <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore>，以停用此要求的快取。  
  
 基於安全性考量，**不**建議針對中介層案例進行快取。  
  
## <a name="in-this-section"></a>本章節內容  
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)  
 說明快取原則是什麼，以及如何定義快取原則。  
  
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 定義可用於超文字傳輸通訊協定 (http 和 https) 資源的每種以位置為基礎的快取原則。  
  
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 描述可用來自訂以時間為基礎的快取原則的條件。  
  
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 描述如何以程式設計方式建立快取原則以及使用快取的要求。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Net.Cache>  
 可定義類型和列舉，這些類型和列舉是用來定義使用 <xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest> 和 <xref:System.Net.FtpWebRequest> 類別所取得之資源的快取原則。
