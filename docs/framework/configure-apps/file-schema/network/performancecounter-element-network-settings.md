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
ms.openlocfilehash: 05aac6c1ed3c04bce263a45cafdb9bec906bd75b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664053"
---
# <a name="performancecounter-element-network-settings"></a>\<performanceCounter > 元素 (網路設定)
啟用或停用網路效能計數器。  
  
 \<configuration>  
\<system.net>  
\<設定 >  
\<performanceCounters>  
  
## <a name="syntax"></a>語法  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|指定是否啟用網路效能計數器。 預設值為 `false`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[設置](settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
 需要在組態檔中啟用，才能使用網路效能計數器。 藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。 不能啟用或停用個別的網路效能計數器。 如需特定網路效能計數器的詳細資訊, 請參閱[網路效能計數器](../../../debug-trace-profile/performance-counters.md#networking)。  
  
 預設值是網路效能計數器已停用。  
  
 屬性可以用來從適用的設定檔取得**已啟用**屬性的目前值。 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>範例  
 下列範例顯示如何設定和相關的<xref:System.Net>命名空間, 以啟用網路效能計數器。  
  
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
- [網路效能計數器](../../../debug-trace-profile/performance-counters.md#networking)
