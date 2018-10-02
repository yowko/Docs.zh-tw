---
title: '&lt;namedCaches&gt;元素 （快取設定）'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a74dfaf883ea23514c6bc4641d9d576f5baf10b4
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028291"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt;元素 （快取設定）
指定的具名組態設定集合<xref:System.Runtime.Caching.MemoryCache>執行個體。 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性從一或多個參考的組態設定集合`namedCaches`組態檔的項目。  
  
 \<configuration>  
\< system.runtime.caching >  
\<memoryCache>  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|整數值，指定允許的大小上限，以 mb 為單位，可執行個體<xref:System.Runtime.Caching.MemoryCache>可以成長到。 預設值為 0，這表示的自動調整啟發學習法<xref:System.Runtime.Caching.MemoryCache>預設會使用類別。|  
|`name`|快取的名稱。|  
|`physicalMemoryLimitPercentage`|整數值介於 0 到 100 之間，指定可供快取的實際安裝的電腦記憶體的最大百分比。 預設值為 0，這表示的自動調整啟發學習法<xref:System.Runtime.Caching.MemoryCache>預設會使用類別。|  
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
 可以包含 Web.config 檔的記憶體快取組態區段`add`， `remove`，並`clear`屬性`namedCaches`集合。 每個`namedCaches`項目會識別`name`屬性。  
  
 您可以藉由參考應用程式組態檔中的資訊擷取執行個體的記憶體快取項目。 根據預設，只有預設快取執行個體具有組態檔中的項目。 預設快取執行個體是從傳回的執行個體<xref:System.Runtime.Caching.MemoryCache.Default%2A>屬性。  
  
 如果您設定為"default"的 name 屬性時，項目會使用預設的記憶體快取執行個體。  
  
## <a name="example"></a>範例  
 下列範例示範如何將預設快取項目名稱中的快取的名稱，藉由設定`name`為"default"的屬性。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設定為零表示自動調整啟發學習法<xref:System.Runtime.Caching.MemoryCache>類別使用。 快取實作會比較目前的記憶體負載與絕對和百分比型記憶體限制每隔兩分鐘。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<memoryCache > 項目 （快取設定）](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
