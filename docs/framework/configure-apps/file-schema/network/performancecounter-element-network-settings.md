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
ms.openlocfilehash: 4603a942788d31a049196fb699d07a13551fa443
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279756"
---
# <a name="performancecounter-element-network-settings"></a>\<performanceCounter > 項目 （網路設定）
啟用或停用網路的效能計數器。  
  
 \<configuration>  
\<system.net>  
\<settings>  
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
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
 需要在組態檔中啟用，才能使用網路效能計數器。 藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。 不能啟用或停用個別的網路效能計數器。 如需有關特定的網路效能計數器的詳細資訊，請參閱[網路效能計數器](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)。  
  
 預設值是該網路的效能計數器已停用。  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>屬性可用來取得目前的值**啟用**適用的組態檔中的屬性。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定<xref:System.Net>和相關命名空間，以啟用網路效能計數器。  
  
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
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [網路效能計數器](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
