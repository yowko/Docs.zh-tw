---
title: <defaultHttpCachePolicy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: 1dd31884a072d16ed004c0b49be61e8cee399787
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664146"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a>\<defaultHttpCachePolicy > 元素 (網路設定)
描述 HTTP 快取是否作用中, 並描述預設的快取原則。  
  
 \<configuration>  
\<system.net>  
\<requestCaching>  
\<defaultHttpCachePolicy>  
  
## <a name="syntax"></a>語法  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`maximumAge`|指定快取的物件標記為過期之前的時間間隔上限。|  
|`maximumStale`|指定在快取的物件標示為過期之前, 經過計算的最晚時間的時間上限。|  
|`minimumFresh`|指定快取物件被視為最新的時間下限。|  
|`policyLevel`|指定快取原則是自動的, 還是略過快取。 預設值為 `BypassCache`。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
  
## <a name="remarks"></a>備註  
 `policyLevel`屬性的值`BypassCache`為或`Default`。  
  
 、和專案的值`maximumStale`為明確的時間間隔, 格式為*d。* `maximumAge` `minimumFresh` *hh*:*mm*:*ss* (天、小時、分鐘和秒), 或適當的常數`minValue`或`maxValue`。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定最短的新時間 (六個小時)、兩天的最長存留期, 以及最大過時時間 (四小時)。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [網路設定結構描述](index.md)
