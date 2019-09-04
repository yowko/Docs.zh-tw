---
title: <appDomainResourceMonitoring> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1395ee64d94e33693344b678c7a949665f994079
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252828"
---
# <a name="appdomainresourcemonitoring-element"></a>\<appDomainResourceMonitoring > 元素
針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainResourceMonitoring>**  
  
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
|`enabled`|必要屬性。<br /><br /> 指定執行時間是否收集應用程式域資源監視的統計資料。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`true`|系統會收集應用程式域資源監視的統計資料。|  
|`false`|不會收集應用程式域資源監視的統計資料。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 應用程式域資源監視可透過受控應用程式域類別、裝載[ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和 Windows 事件追蹤 (ETW) 來取得。 啟用監視時, 會針對進程中的所有應用程式域收集統計資料。  
  
 若要從 managed 程式碼啟用監視, <xref:System.AppDomain.MonitoringIsEnabled%2A>請使用屬性。  
  
 此 configuration 元素僅適用于 .NET Framework 4 和更新版本。  
  
## <a name="example"></a>範例  
 下列範例顯示如何啟用應用程式域資源監視。  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
