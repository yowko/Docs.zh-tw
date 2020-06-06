---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154501"
---
# <a name="add-element-for-namedcaches"></a>\<namedCaches> 的 \<add> 項目
將 `namedCache` 專案加入至記憶體快取的 `namedCaches` 集合。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
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
|`CacheMemoryLimitMegabytes`|整數值，指定實例可以成長到的最大允許大小（以 mb 為單位） <xref:System.Runtime.Caching.MemoryCache> 。 預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。|  
|`Name`|快取的名稱。|  
|`PhysicalMemoryLimitPercentage`|介於0和100之間的整數值，指定可供快取使用之實際安裝電腦記憶體的最大百分比。 預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。|  
|`PollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 此值會以 "HH： MM： SS" 格式輸入。|  
  
### <a name="child-elements"></a>子元素  
 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|包含已命名實例的設定集合 <xref:System.Runtime.Caching.MemoryCache> 。|  
  
## <a name="remarks"></a>備註  
 `add`元素會將專案加入至記憶體快取的 `namedCaches` 集合。 在您使用專案之前，您可以使用[clear](clear-element-for-namedcaches.md)元素， `add` 以確定集合中沒有任何其他已命名的快取。 這個元素可以在 machine.config 檔案和 web.config 檔案中使用。  
  
## <a name="example"></a>範例  
 下列範例示範如何將預設專案的設定定義為 `namedCache` 記憶體快取的 `namedCaches` 集合。  
  
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

- [\<namedCaches>元素（快取設定）](namedcaches-element-cache-settings.md)
