---
title: "&lt;設定&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 07f356c0425b071ac320e702a9ba7cd6b9537341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsettingsgt-element-network-settings"></a>&lt;設定&gt;項目 （網路設定）
為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。  
  
 \<configuration>  
\<system.net >  
\<設定 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[httpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|自訂所用參數<xref:System.Net.HttpListener>類別。|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|可自訂 Web 要求參數。|  
|[ipv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|可讓網際網路通訊協定第 6 版 (IPv6) 支援。|  
|[\<performanceCounter > 項目 （網路設定）](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|啟用網路效能計數器。|  
|[servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|設定連線到網路資源。|  
|[通訊端](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|指定通訊端作業是否使用完成通訊埠。|  
|[\<webProxyScript > 項目 （網路設定）](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|設定用來探索 Web proxy 的指令碼的特性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net?displayProperty=nameWithType>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
