---
title: <namedCaches> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 9cedd462aa539745ddab844dff158912914cb024
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663573"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches > 元素 (快取設定)
指定已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。 屬性會從設定檔的一個或多個`namedCaches`元素, 參考設定的集合。 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>  
  
 \<configuration>  
\<> 的緩存  
\<memoryCache>  
\<namedCaches>  
  
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
|`cacheMemoryLimitMegabytes`|整數值, 指定實例<xref:System.Runtime.Caching.MemoryCache>可以成長到的最大允許大小 (以 mb 為單位)。 預設值為 0, 表示預設會使用<xref:System.Runtime.Caching.MemoryCache>類別的自動調整大小啟發學習法。|  
|`name`|快取的名稱。|  
|`physicalMemoryLimitPercentage`|介於0和100之間的整數值, 指定可供快取使用之實際安裝電腦記憶體的最大百分比。 預設值為 0, 表示預設會使用<xref:System.Runtime.Caching.MemoryCache>類別的自動調整大小啟發學習法。|  
|`pollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 此值會以 "HH: MM: SS" 格式輸入。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|將具名快取新增到記憶體快取的 `namedCaches` 集合。|  
|[\<clear>](clear-element-for-namedcaches.md)|清除記憶體快取的 `namedCaches` 集合。|  
|[\<remove>](remove-element-for-namedcaches.md)|從記憶體快取的 `namedCaches` 集合移除具名快取項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
  
## <a name="remarks"></a>備註  
 Web.config 檔案的記憶體快取設定區段`add`可以包含`namedCaches`集合的、 `remove`和`clear`屬性。 每`namedCaches`個專案都是`name`由屬性唯一識別。  
  
 您可以藉由參考應用程式佈建檔中的資訊, 來取出記憶體快取專案的實例。 根據預設, 只有預設快取實例在設定檔中有一個專案。 預設的快取實例是從<xref:System.Runtime.Caching.MemoryCache.Default%2A>屬性傳回的實例。  
  
 如果您將 name 屬性設定為 "default", 元素會使用預設的記憶體快取實例。  
  
## <a name="example"></a>範例  
 下列範例示範如何透過將`name`屬性設定為 "default", 將快取的名稱設定為預設快取專案名稱。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設定為零表示會使用<xref:System.Runtime.Caching.MemoryCache>類別的自動調整大小啟發學習法。 快取執行會比較目前的記憶體負載與以百分比為基礎的記憶體限制, 每兩分鐘一次。  
  
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

- [\<memoryCache > 元素 (快取設定)](memorycache-element-cache-settings.md)
