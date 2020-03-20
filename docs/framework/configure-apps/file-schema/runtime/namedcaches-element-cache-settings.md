---
title: <namedCaches> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153954"
---
# <a name="namedcaches-element-cache-settings"></a>\<具名快取>元素（緩存設置）
指定命名<xref:System.Runtime.Caching.MemoryCache>實例的配置設置集合。 該<xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性引用設定檔的一個或多個`namedCaches`元素的配置設置集合。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.運行時.緩存>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<記憶體緩存>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<具名快取>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a>類型  
 `None`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|指定 a<xref:System.Runtime.Caching.MemoryCache>實例可以增長到的最大允許大小（以百萬位元組為單位）的整數值。 預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動啟發式調整大小。|  
|`name`|快取的名稱。|  
|`physicalMemoryLimitPercentage`|介於 0 和 100 之間的整數值，指定緩存可以使用的物理安裝電腦記憶體的最大百分比。 預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動啟發式調整大小。|  
|`pollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 此值以"HH：MM：SS"格式輸入。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add-element-for-namedcaches.md)|將具名快取新增到記憶體快取的 `namedCaches` 集合。|  
|[\<明確>](clear-element-for-namedcaches.md)|清除記憶體快取的 `namedCaches` 集合。|  
|[\<刪除>](remove-element-for-namedcaches.md)|從記憶體快取的 `namedCaches` 集合移除具名快取項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<配置>](../configuration-element.md)|指定通用語言運行時和 .NET Framework 應用程式使用的每個設定檔中的根項目。|  
|[\<記憶體緩存>](memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
|[\<系統.運行時.緩存>](system-runtime-caching-element-cache-settings.md)|包含允許您在內置於 .NET 框架中的應用程式中實現輸出緩存的類型。|  
  
## <a name="remarks"></a>備註  
 Web.config`add`檔的記憶體緩存配置部分可以包含 集合`remove`的`namedCaches``clear`和 屬性。 每個`namedCaches`條目都由`name`屬性唯一標識。  
  
 您可以通過引用應用程式佈建檔中的資訊來檢索記憶體緩存條目的實例。 預設情況下，只有預設緩存實例在設定檔中具有條目。 預設緩存實例是從屬性返回的<xref:System.Runtime.Caching.MemoryCache.Default%2A>實例。  
  
 如果將名稱屬性設置為"預設"，則元素將使用預設記憶體緩存實例。  
  
## <a name="example"></a>範例  
 下面的示例演示如何通過將`name`屬性設置為"預設"來將緩存的名稱設置為預設緩存條目名稱。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設置為零意味著使用<xref:System.Runtime.Caching.MemoryCache>類的自動啟發式調整大小。 緩存實現將當前記憶體負載與絕對記憶體限制和基於百分比的記憶體限制每兩分鐘進行比較。  
  
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

- [\<記憶體緩存>元素（緩存設置）](memorycache-element-cache-settings.md)
