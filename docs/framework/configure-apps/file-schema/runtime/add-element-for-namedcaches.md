---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: cd920b58290050fcc30ea5d0a1ac113a333902fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195359"
---
# <a name="add-element-for-namedcaches"></a>\<namedCaches> 的 \<add> 項目

將 `namedCache` 專案加入至記憶體快取的集合中 `namedCaches` 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`CacheMemoryLimitMegabytes`|整數值，指定的實例可成長的大小上限 () （以 mb 為單位） <xref:System.Runtime.Caching.MemoryCache> 。 預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。|  
|`Name`|快取的名稱。|  
|`PhysicalMemoryLimitPercentage`|介於0與100之間的整數值，指定快取可以取用的實際安裝電腦記憶體百分比上限。 預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。|  
|`PollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 此值是以 "HH： MM： SS" 格式輸入。|  
  
### <a name="child-elements"></a>子元素  

 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|包含已命名實例的設定設定集合 <xref:System.Runtime.Caching.MemoryCache> 。|  
  
## <a name="remarks"></a>備註  

 `add`元素會將專案加入至記憶體快取的 `namedCaches` 集合中。 您可以在使用元素之前，先使用 [clear](clear-element-for-namedcaches.md) 元素， `add` 確定集合中沒有任何其他命名快取。 這個元素可用於 machine.config 檔案和 Web.config 檔案中。  
  
## <a name="example"></a>範例  

 下列範例示範如何為記憶體快取的集合定義預設專案的設定 `namedCache` `namedCaches` 。  
  
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

- [\<namedCaches> (快取設定的元素) ](namedcaches-element-cache-settings.md)
