---
title: <performanceCounter> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 4859f3a9e6de4f1bf8a56212bfe01f94d66f5650
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190237"
---
# <a name="performancecounter-element-network-settings"></a>\<performanceCounter> 項目 (網路設定)

啟用或停用網路效能計數器。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a>Syntax  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|指定是否啟用網路效能計數器。 預設值是 `false`。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[設定](settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
 需要在組態檔中啟用，才能使用網路效能計數器。 藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。 不能啟用或停用個別的網路效能計數器。 如需特定網路效能計數器的詳細資訊，請參閱 [網路效能計數器](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)。  
  
 預設值是網路效能計數器已停用。  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得**已啟用**屬性的目前值。  
  
## <a name="example"></a>範例  

 下列範例顯示如何設定 <xref:System.Net> 和相關的命名空間，以啟用網路效能計數器。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
- [網路效能計數器](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
