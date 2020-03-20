---
title: <appDomainResourceMonitoring> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154372"
---
# <a name="appdomainresourcemonitoring-element"></a>\<appDomain資源監視>元素
針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<應用程式域資源監視>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定運行時是否收集應用程式域資源監視的統計資訊。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`true`|收集應用程式域資源監視的統計資訊。|  
|`false`|不會收集應用程式域資源監視的統計資訊。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 應用程式域資源監視可通過託管應用程式域類、託管[ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和 Windows （ETW） 的事件跟蹤進行。 啟用監視後，將收集流程中所有應用程式域的統計資訊，以進行此過程的生命週期。  
  
 要啟用從託管代碼進行監視，請使用<xref:System.AppDomain.MonitoringIsEnabled%2A>屬性。  
  
 此配置元素僅在 .NET 框架 4 和更高版本中可用。  
  
## <a name="example"></a>範例  
 下面的示例演示如何啟用應用程式域資源監視。  
  
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
