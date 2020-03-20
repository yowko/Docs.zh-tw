---
title: <system.runtime.caching> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153850"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<系統.運行時.緩存>元素（緩存設置）

透過組態檔中的 <xref:System.Runtime.Caching.ObjectCache> 項目，提供預設記憶體內 `memoryCache` 實作的組態。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;**\<系統.運行時.緩存>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性

`None`  

### <a name="child-elements"></a>子元素

|元素|描述|  
|-------------|-----------------|  
|[\<記憶體緩存>](memorycache-element-cache-settings.md)|定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<配置>](../configuration-element.md)|指定通用語言運行時和 .NET Framework 應用程式使用的每個設定檔中的根項目。|  
  
## <a name="remarks"></a>備註

這個命名空間中的類別提供如同在 ASP.NET 中使用快取設備的方式，但是不需要在 `System.Web` 組件上的相依性。 如需詳細資訊，請參閱 [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md)。  
  
> [!NOTE]
> 命名空間中的<xref:System.Runtime.Caching>輸出緩存功能和類型在 .NET 框架 4 中是新的。  
  
## <a name="example"></a>範例

下列範例示範如何設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取， 並示範如何設定記憶體快取之 `namedCaches` 項目的執行個體。 通過將屬性設置為"預設"，`name`緩存的名稱將設置為預設緩存條目名稱。  
  
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

- [\<記憶體緩存>元素（緩存設置）](memorycache-element-cache-settings.md)
