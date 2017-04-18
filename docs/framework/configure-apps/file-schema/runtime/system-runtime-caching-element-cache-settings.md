---
title: "&lt;system.runtime.caching&gt; 項目 (快取設定) | Microsoft Docs"
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
  - "<system.runtime.caching> 項目"
  - "快取 [.NET Framework], 組態"
  - "system.runtime.caching 項目"
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;system.runtime.caching&gt; 項目 (快取設定)
透過組態檔中的 `memoryCache` 項目，提供預設記憶體內 <xref:System.Runtime.Caching.ObjectCache> 實作的組態。  
  
 \<configuration\>  
\<system.runtime.caching\>  
  
## 語法  
  
```  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 `None`  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<memoryCache\>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|指定通用語言執行平台和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。|  
  
## 備註  
 這個命名空間中的類別提供如同在 ASP.NET 中使用快取設備的方式，但是不需要在 `System.Web` 組件上的相依性。 如需詳細資訊，請參閱[.NET Framework 應用程式中的快取](../../../../../docs/framework/performance/caching-in-net-framework-applications.md)。  
  
> [!NOTE]
>  輸出快取功能，以及 <xref:System.Runtime.Caching> 命名空間中的類型是 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 中的新功能。  
  
## 範例  
 下列範例示範如何設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取， 並示範如何設定記憶體快取之 `namedCaches` 項目的執行個體。 您可將 `name` 屬性設為 "default"，以將快取的名稱設定為預設快取項目。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設定為零表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 自動調整啟發學習法。 快取實作應該會每隔兩分鐘即比較目前的記憶體負載與絕對和百分比型記憶體限制。  
  
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