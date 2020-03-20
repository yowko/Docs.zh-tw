---
title: <alwaysFlowImpersonationPolicy> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154479"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<源流類比策略>元素
指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<始終流類比策略>**\  
  
## <a name="syntax"></a>語法  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指示 Windows 標識是否跨非同步點流動。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|Windows 標識不會跨非同步點流動，除非通過託管方法（如<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>） 執行類比。 這是預設值。|  
|`true`|無論類比執行方式如何，Windows 標識始終跨非同步點流動。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET 框架版本 1.0 和 1.1 中，Windows 標識不會跨非同步點流動。 在 .NET Framework 版本 2.0<xref:System.Threading.ExecutionContext>中，有一個物件包含有關當前正在執行的執行緒的資訊，並跨應用程式域中的非同步點進行流。 如果<xref:System.Security.Principal.WindowsIdentity>類比是使用託管方法（如，<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>而不是通過其他方法（如平台叫用本機方法）實現的，則該函數也會作為流經非同步點的資訊的一部分進行流動。 此元素用於指定 Windows 標識確實跨非同步點流動，而不考慮類比是如何實現的。  
  
 您可以通過兩種其他方式更改此預設行為：  
  
1. 在基於每個執行緒的託管代碼中。  
  
     <xref:System.Threading.ExecutionContext>通過使用 、 或<xref:System.Security.SecurityContext><xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法修改 和 設置，可以按執行緒禁止流。  
  
2. 在調用非託管主機介面以載入通用語言運行時 （CLR）。  
  
     如果使用非託管託管介面（而不是簡單的託管可執行檔）來載入 CLR，則可以在[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的調用中指定一個特殊的標誌。 要為整個過程啟用相容性模式，將`flags`[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的參數設置為`STARTUP_ALWAYSFLOW_IMPERSONATION`。  
  
## <a name="configuration-file"></a>組態檔  
 在 .NET 框架應用程式中，此元素只能在應用程式佈建檔中使用。  
  
 對於ASP.NET應用程式，可以在\<Windows 資料夾>_Microsoft.NET_Framework_vx.x.xxx 目錄中的 aspnet.config 檔中配置類比流。  
  
 預設情況下ASP.NET使用以下配置設置禁用 aspnet.config 檔中的類比流：  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 在ASP.NET中，如果要改為允許類比流，則必須顯式使用以下配置設置：  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>範例  
 下面的示例演示如何指定 Windows 標識跨非同步點流動，即使類比是通過託管方法以外的方法實現的。  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [\<傳統類比策略>元素](legacyimpersonationpolicy-element.md)
