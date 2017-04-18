---
title: "&lt;namedCaches&gt; 項目 (快取設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<namedCaches> 項目"
  - "快取 [.NET Framework], 組態"
  - "namedCaches 項目"
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;namedCaches&gt; 項目 (快取設定)
指定具名 <xref:System.Runtime.Caching.MemoryCache> 執行個體之組態設定的集合。  <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> 屬性會從組態檔的一或多個 `namedCaches` 項目參考組態設定的集合。  
  
## 語法  
  
```  
<namedCaches>  
  <add name="default"   
</namedCaches>  
```  
  
## 類型  
 `None`  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`CacheMemoryLimitMegabytes`|整數值，指定允許 <xref:System.Runtime.Caching.MemoryCache> 之執行個體成長至的最大大小，以 MB 為單位。  預設值為 0，表示會依預設使用 <xref:System.Runtime.Caching.MemoryCache> 類別的啟發式自動調整。|  
|`Name`|快取的名稱。|  
|`PhysicalMemoryLimitPercentage`|介於 0 與 100 之間的整數值，指定可由快取使用之實體安裝電腦記憶體的最大百分比。  預設值為 0，表示會依預設使用 <xref:System.Runtime.Caching.MemoryCache> 類別的啟發式自動調整。|  
|`PollingInterval`|表示時間間隔的值，快取實作經過這段時間間隔之後，就會將目前的記憶體負載與針對快取執行個體所設定的絕對記憶體限制和百分比記憶體限制進行比較。  這個值是以 "HH:MM:SS" 格式輸入。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|將具名快取加入至記憶體快取的 `namedCaches` 集合。|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|清除記憶體快取的 `namedCaches` 集合。|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|從記憶體快取的 `namedCaches` 集合中移除具名快取項目。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<memoryCache\>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
  
## 備註  
 Web.config 檔的記憶體快取組態區段，可以包含 `namedCaches` 集合的 `add`、`remove` 和 `clear` 屬性。  每個 `namedCaches` 項目都可由 `name` 屬性唯一識別。  
  
 您可以藉由參考應用程式組態檔中的資訊，來擷取記憶體快取項目的執行個體。  根據預設，只有預設快取執行個體在組態檔中有一個項目。  預設的快取執行個體，就是從 <xref:System.Runtime.Caching.MemoryCache.Default%2A> 屬性傳回的執行個體。  
  
 如果將名稱屬性設定為「預設」，該項目就會使用預設的記憶體快取執行個體。  
  
## 範例  
 下列範例會示範如何藉由將 `name` 屬性設定為 "default"，將快取的名稱設定為預設快取項目名稱。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。  將這些屬性設定為零，表示使用 <xref:System.Runtime.Caching.MemoryCache> 類別的啟發式自動調整。  每兩分鐘，快取實作都會比較目前的記憶體載入與絕對和百分比的記憶體限制。  
  
```  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## 請參閱  
 [\<memoryCache\> 項目 \(快取設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)