---
title: <settings> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: ba08f630dc602c950da309bf29482d85b41af7ef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697687"
---
# <a name="settings-element-network-settings"></a>@no__t 0settings > 元素（網路設定）
為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<settings >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[httpListener](httplistener-element-network-settings.md)|自訂 <xref:System.Net.HttpListener> 類別所使用的參數。|  
|[httpWebRequest](httpwebrequest-element-network-settings.md)|自訂 Web 要求參數。|  
|[ipv6](ipv6-element-network-settings.md)|啟用網際網路通訊協定第6版（IPv6）支援。|  
|[@no__t 1performanceCounter > 元素（網路設定）](performancecounter-element-network-settings.md)|啟用網路效能計數器。|  
|[servicePointManager](servicepointmanager-element-network-settings.md)|設定網路資源的連接。|  
|[socket](socket-element-network-settings.md)|指定通訊端作業是否使用完成埠。|  
|[@no__t 1webProxyScript > 元素（網路設定）](webproxyscript-element-network-settings.md)|設定用來探索 Web proxy 之腳本的特性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
