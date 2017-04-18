---
title: "快取原則 | Microsoft Docs"
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
  - "以位置為基礎的快取原則"
  - "快取 [.NET Framework]，原則"
  - "要求快取原則"
  - "快取資源的最新狀態"
  - "內容快取原則"
  - "已到期的內容"
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 快取原則
快取原則會定義規則 \(Rule\)，用於判斷所要求資源的快取複本是否可以滿足要求。  應用程式指定用戶端有效期限快取要求，不過，用戶端快取要求、伺服器的內容到期日和要求的伺服器重新確認需求取決於有效的快取原則。  用戶端快取原則和伺服器要求的互動一定會產生最保守的快取原則，協助確保最新內容傳回至用戶端應用程式。  
  
 快取原則或位置以時間為基礎的。  以位置為主的快取原則以定義的快取項目的有效期限要求的資源可能是從中的位置。  使用資源擷取的時間，標頭中傳回的資源和目前時間，以時間為主的快取原則定義快取項目的有效期限。  大部分的應用程式可以使用預設時間為主的快取原則，實作這些物件所指定的快取原則 2616， [http:\/\/www.ietf.org](http://www.ietf.org/)網址為。  
  
 下表所描述的類別是用來指定快取原則。  
  
|類別名稱|描述|  
|----------|--------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|表示位置並以時間為基礎的使用 <xref:System.Net.HttpWebRequest> 物件所要求之資源的快取原則。|  
|<xref:System.Net.Cache.RequestCachePolicy>|表示以位置為主的快取原則或 <xref:System.Net.Cache.RequestCacheLevel> 時間為基礎的使用 <xref:System.Net.WebRequest> 物件所要求之資源的快取原則。|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|指定用於的值建立時間架構 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|指定使用值建立的位置和以時間為主的 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。|  
|<xref:System.Net.Cache.RequestCacheLevel>|指定使用值建立的位置或 <xref:System.Net.Cache.RequestCacheLevel> 以時間為主的 <xref:System.Net.Cache.RequestCachePolicy> 物件。|  
  
 您可以定義一個項目的快取原則應用程式所執行的所有需求或個別要求的。  當您指定一個應用程式層級的快取原則和一項要求層級的快取原則時，使用這項要求層級原則。  您可以指定一個應用程式層級的快取原則以程式設計方式或使用應用程式或電腦組態檔。  如需詳細資訊，請參閱[\<requestCaching\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)。  
  
 若要建立快取原則，您必須建立 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 類別的執行個體建立原則物件。  若要指定原則需求，請將要求的 <xref:System.Net.WebRequest.CachePolicy%2A> 屬性對原則物件。  當設定一項應用程式層級的原則，以程式設計方式設定 <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> 屬性對原則物件。  
  
 如需示範如何建立及使用快取原則的程式碼範例，請參閱 [在 Web 應用程式中設定快取](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)。  
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)