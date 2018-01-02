---
title: "&lt;namedCaches&gt;項目 （快取設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f4c4bd9901b053c96a260435c34ffa3ddd2c7283
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt;項目 （快取設定）
指定的具名組態設定集合<xref:System.Runtime.Caching.MemoryCache>執行個體。 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性參考的組態設定集合從一或多個`namedCaches`的組態檔項目。  
  
 \<configuration>  
\<system.runtime.caching >  
\<memoryCache >  
\<namedCaches >  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>類型  
 `None`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|整數值，以 mb 為單位，指定最大容許大小的執行個體<xref:System.Runtime.Caching.MemoryCache>可以成長到。 預設值為 0，這表示的自動調整啟發學習法<xref:System.Runtime.Caching.MemoryCache>預設會使用類別。|  
|`name`|快取的名稱。|  
|`physicalMemoryLimitPercentage`|整數值 0 和 100 之間，指定可供快取的實際安裝的電腦記憶體的最大百分比。 預設值為 0，這表示的自動調整啟發學習法<xref:System.Runtime.Caching.MemoryCache>預設會使用類別。|  
|`pollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 這個值是以"Hh: mm:"格式輸入。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|將具名快取新增到記憶體快取的 `namedCaches` 集合。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|清除記憶體快取的 `namedCaches` 集合。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|從記憶體快取的 `namedCaches` 集合移除具名快取項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
  
## <a name="remarks"></a>備註  
 記憶體快取組態區段位於 Web.config 檔案可以包含`add`， `remove`，和`clear`屬性`namedCaches`集合。 每個`namedCaches`項目以唯一識別`name`屬性。  
  
 您可以藉由參考應用程式組態檔中的資訊擷取執行個體的記憶體快取項目。 根據預設，只有預設快取執行個體，請在組態檔中有項目。 預設快取執行個體是從傳回的執行個體<xref:System.Runtime.Caching.MemoryCache.Default%2A>屬性。  
  
 如果您設定 name 屬性為"default"，項目會使用預設的記憶體快取執行個體。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定預設快取項目名稱的快取的名稱，藉由設定`name`「 預設 」 的屬性。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設定為零表示自動調整啟發學習法的<xref:System.Runtime.Caching.MemoryCache>可用類別。 快取實作比較目前的記憶體負載，對絕對和以百分比為基礎的記憶體限制每兩分鐘。  
  
```xml  
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
  
## <a name="see-also"></a>請參閱  
 [\<memoryCache > 項目 （快取設定）](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
