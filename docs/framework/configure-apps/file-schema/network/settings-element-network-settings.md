---
title: <settings> 項目 （網路設定）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: a1733803d1f5a5bf64aeb69d0360cef3de3b3a69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096923"
---
# <a name="settings-element-network-settings"></a>\<設定 > 項目 （網路設定）
為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。  
  
 \<configuration>  
\<system.net>  
\<settings>  
  
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
  
|項目|描述|  
|-------------|-----------------|  
|[httpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|自訂所使用的參數<xref:System.Net.HttpListener>類別。|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|自訂 Web 要求參數。|  
|[ipv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|可讓網際網路通訊協定第 6 版 (IPv6) 支援。|  
|[\<performanceCounter > 項目 （網路設定）](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|啟用網路效能計數器。|  
|[servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|設定網路資源的連線。|  
|[通訊端](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|指定通訊端作業是否使用完成通訊埠。|  
|[\<webProxyScript > 項目 （網路設定）](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|設定用來探索 Web proxy 指令碼的特性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net?displayProperty=nameWithType>
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
