---
title: '&lt;appDomainResourceMonitoring&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11e892d8ab9001d3670c801b43ba444aa24b2e41
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743572"
---
# <a name="ltappdomainresourcemonitoringgt-element"></a>&lt;appDomainResourceMonitoring&gt;項目
針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。  
  
 \<configuration>  
\<執行階段 >  
\<appDomainResourceMonitoring >  
  
## <a name="syntax"></a>語法  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否執行階段會收集應用程式定義域資源監視的統計資料。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`true`|會收集應用程式定義域資源監視的統計資料。|  
|`false`|不會收集應用程式定義域資源監視的統計資料。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 應用程式定義域資源監視是透過 managed 應用程式網域類別裝載[ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和事件追蹤 Windows (ETW)。 啟用監視，收集統計資料的程序的存留期的程序中的所有應用程式定義域。  
  
 若要啟用監視，從 managed 程式碼，請使用<xref:System.AppDomain.MonitoringIsEnabled%2A>屬性。  
  
 這個組態項目是僅適用於[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本。  
  
## <a name="example"></a>範例  
 下列範例會示範如何啟用應用程式定義域資源監視。  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
