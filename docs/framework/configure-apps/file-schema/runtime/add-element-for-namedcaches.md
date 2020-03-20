---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154501"
---
# <a name="add-element-for-namedcaches"></a>\<為\<具名快取添加>元素>
向`namedCache`記憶體緩存`namedCaches`的集合添加條目。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.運行時.緩存>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<記憶體緩存>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<具名快取>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>類型  
 `None`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|-|-|  
|`CacheMemoryLimitMegabytes`|指定 a<xref:System.Runtime.Caching.MemoryCache>實例可以增長到的最大允許大小（以百萬位元組為單位）的整數值。 預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動調整啟發式。|  
|`Name`|快取的名稱。|  
|`PhysicalMemoryLimitPercentage`|介於 0 和 100 之間的整數值，指定緩存可以使用的物理安裝電腦記憶體的最大百分比。 預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動調整啟發式。|  
|`PollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 此值以"HH：MM：SS"格式輸入。|  
  
### <a name="child-elements"></a>子元素  
 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<具名快取>](namedcaches-element-cache-settings.md)|包含命名<xref:System.Runtime.Caching.MemoryCache>實例的配置設置集合。|  
  
## <a name="remarks"></a>備註  
 該`add`元素向記憶體緩存`namedCaches`的集合添加一個條目。 在使用 元素[clear](clear-element-for-namedcaches.md)之前，`add`可以使用 clear 元素來確保集合中沒有其他具名快取。 此元素可用於電腦.config 檔和 Web.config 檔中。  
  
## <a name="example"></a>範例  
 下面的示例演示如何為記憶體緩存集合的`namedCache``namedCaches`預設條目定義設置。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [\<具名快取>元素（緩存設置）](namedcaches-element-cache-settings.md)
