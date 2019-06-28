---
title: <system.runtime.caching> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb977e05fa54b726b0cd584d287dc00c8ced995
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423259"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<system.runtime.caching > 項目 （快取設定）

透過組態檔中的 <xref:System.Runtime.Caching.ObjectCache> 項目，提供預設記憶體內 `memoryCache` 實作的組態。  
  
 \<configuration>  
\<system.runtime.caching>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性

`None`  

### <a name="child-elements"></a>子元素

|項目|描述|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|所有由 common language runtime 和.NET Framework 應用程式的組態檔中指定的根項目。|  
  
## <a name="remarks"></a>備註

這個命名空間中的類別提供如同在 ASP.NET 中使用快取設備的方式，但是不需要在 `System.Web` 組件上的相依性。 如需詳細資訊，請參閱 [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md)。  
  
> [!NOTE]
>  輸出快取功能與中的型別<xref:System.Runtime.Caching>命名空間是.NET Framework 4 的新功能。  
  
## <a name="example"></a>範例

下列範例示範如何設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取， 並示範如何設定記憶體快取之 `namedCaches` 項目的執行個體。 快取的名稱設定為預設快取項目名稱，藉由設定`name`屬性為"Default"。  
  
`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設定為零表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 自動調整啟發學習法。 快取實作應該會每隔兩分鐘即比較目前的記憶體負載與絕對和百分比型記憶體限制。  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [\<memoryCache > 項目 （快取設定）](memorycache-element-cache-settings.md)
