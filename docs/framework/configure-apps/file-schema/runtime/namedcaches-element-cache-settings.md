---
title: <namedCaches> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: ad76c01bba859934be399d73262bd974309efe98
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192395"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches> 項目 (快取設定)

指定已命名實例的設定集合 <xref:System.Runtime.Caching.MemoryCache> 。 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性會參考設定檔的一或多個專案中的設定設定集合 `namedCaches` 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`cacheMemoryLimitMegabytes`|整數值，指定的實例可成長的大小上限（以 mb 為單位） <xref:System.Runtime.Caching.MemoryCache> 。 預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。|  
|`name`|快取的名稱。|  
|`physicalMemoryLimitPercentage`|介於0與100之間的整數值，指定快取可以取用的實際安裝電腦記憶體百分比上限。 預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。|  
|`pollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 此值是以 "HH： MM： SS" 格式輸入。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|將具名快取新增到記憶體快取的 `namedCaches` 集合。|  
|[\<clear>](clear-element-for-namedcaches.md)|清除記憶體快取的 `namedCaches` 集合。|  
|[\<remove>](remove-element-for-namedcaches.md)|從記憶體快取的 `namedCaches` 集合移除具名快取項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|指定 common language runtime 和 .NET Framework 應用程式所使用之每個設定檔中的根項目。|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|包含類型，可讓您在 .NET Framework 內建的應用程式中，執行輸出快取。|  
  
## <a name="remarks"></a>備註  

 Web.config 檔案的 memory cache configuration 區段可以包含集合的 `add` 、 `remove` 和 `clear` 屬性 `namedCaches` 。 每個 `namedCaches` 專案都是由屬性唯一識別 `name` 。  
  
 您可以參考應用程式佈建檔中的資訊，以取出記憶體快取專案的實例。 依預設，只有預設快取實例在設定檔中有一個專案。 預設快取實例是從屬性傳回的實例 <xref:System.Runtime.Caching.MemoryCache.Default%2A> 。  
  
 如果您將 [名稱] 屬性設定為 "default"，元素就會使用預設的記憶體快取實例。  
  
## <a name="example"></a>範例  

 下列範例顯示如何藉由將 `name` 屬性設定為 "default"，將快取的名稱設定為預設快取專案名稱。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設定為零，表示會使用類別的自動調整大小啟發學習法 <xref:System.Runtime.Caching.MemoryCache> 。 快取執行會將目前的記憶體負載與每兩分鐘的絕對和百分比型記憶體限制進行比較。  
  
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

- [\<memoryCache> (快取設定的元素) ](memorycache-element-cache-settings.md)
