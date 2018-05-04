---
title: '&lt;新增&gt;元素&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a>&lt;新增&gt;元素&lt;namedCaches&gt;
新增`namedCache`進入`namedCaches`記憶體快取的集合。  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches >  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>類型  
 `None`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|-|-|  
|`CacheMemoryLimitMegabytes`|整數值，指定允許的最大大小 （mb) 的執行個體<xref:System.Runtime.Caching.MemoryCache>可以成長到。 預設值為 0，這表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整啟發學習法。|  
|`Name`|快取的名稱。|  
|`PhysicalMemoryLimitPercentage`|整數值 0 和 100 之間，指定可供快取的實際安裝的電腦記憶體的最大百分比。 預設值為 0，這表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整啟發學習法。|  
|`PollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 這個值是以"Hh: mm:"格式輸入。|  
  
### <a name="child-elements"></a>子項目  
 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。|  
  
## <a name="remarks"></a>備註  
 `add`項目加入至項目的`namedCaches`記憶體快取的集合。 您可以使用[清除](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)使用之前的項目`add`項目，以確定有沒有其他具名快取，在集合中的。 這個項目可以用於 machine.config 檔案中，並在 Web.config 檔案中。  
  
## <a name="example"></a>範例  
 下列範例示範如何定義預設的設定`namedCache`進入`namedCaches`記憶體快取的集合。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [\<namedCaches > 項目 （快取設定）](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
