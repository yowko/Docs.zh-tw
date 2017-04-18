---
title: "&lt;namedCaches&gt; 的 &lt;add&gt; 項目 | Microsoft Docs"
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
  - "<namedCaches> 的 <add> 項目"
  - "<namedCaches> 的 add 項目"
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;namedCaches&gt; 的 &lt;add&gt; 項目
記憶體快取之 `namedCaches` 集合的 `namedCache` 項目。  
  
## 語法  
  
```  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## 類型  
 `None`  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|||  
|-|-|  
|屬性|描述|  
|`CacheMemoryLimitMegabytes`|整數值，指定 <xref:System.Runtime.Caching.MemoryCache> 之執行個體可成長至的最大允許大小，以 MB 為單位。  預設值為 0，表示會依預設使用 <xref:System.Runtime.Caching.MemoryCache> 類別的啟發式自動調整。|  
|`Name`|快取的名稱。|  
|`PhysicalMemoryLimitPercentage`|介於 0 與 100 之間的整數值，指定可由快取使用之實體安裝電腦記憶體的最大百分比。  預設值為 0，表示會依預設使用 <xref:System.Runtime.Caching.MemoryCache> 類別的啟發式自動調整。|  
|`PollingInterval`|表示時間間隔的值，快取實作經過這段時間間隔之後，就會將目前的記憶體負載與針對快取執行個體所設定的絕對記憶體限制和百分比記憶體限制進行比較。  這個值是以 "HH:MM:SS" 格式輸入。|  
  
### 子項目  
 `None`  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|包含具名 <xref:System.Runtime.Caching.MemoryCache> 執行個體之組態設定的集合。|  
  
## 備註  
 `add` 項目 \(Element\) 會將項目 \(Entry\) 加入記憶體快取的 `namedCaches` 集合。  使用 `add` 項目確定在集合中沒有其他具名快取之前，您可以先使用 [](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md "<clear> Element for <namedCaches>") 項目。  這個項目可以在 machine.config 檔和 Web.config 檔中使用。  
  
## 範例  
 下列範例會示範如何定義記憶體快取在 `namedCaches`  集合的預設 `namedCache` 項目的設定值。  
  
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
 [\<namedCaches\> 項目 \(快取設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)