---
title: <legacyImpersonationPolicy> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154100"
---
# <a name="legacyimpersonationpolicy-element"></a>\<傳統類比策略>元素
指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<傳統類比策略>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定<xref:System.Security.Principal.WindowsIdentity>不跨非同步點流動，而不考慮當前執行緒上的<xref:System.Threading.ExecutionContext>流設置。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>流經非同步點，<xref:System.Threading.ExecutionContext>具體取決於當前執行緒的流設置。 這是預設值。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>無論當前執行緒上的<xref:System.Threading.ExecutionContext>流設置如何，都不會在非同步點之間流動。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET 框架版本 1.0 和 1.1 中，<xref:System.Security.Principal.WindowsIdentity>不會流過任何使用者定義的非同步點。 從 .NET Framework 版本 2.0 開始<xref:System.Threading.ExecutionContext>，有一個物件包含有關當前正在執行的執行緒的資訊，並且它跨應用程式域中的非同步點流動。 <xref:System.Security.Principal.WindowsIdentity>包含在此執行上下文中，因此也會跨非同步點流動，這意味著如果存在類比上下文，它也會流動。  
  
 從 .NET 框架 2.0 開始，可以使用`<legacyImpersonationPolicy>`元素指定<xref:System.Security.Principal.WindowsIdentity>不跨非同步點流動的元素。  
  
> [!NOTE]
> 通用語言運行時 （CLR） 知道僅使用託管代碼執行的類比操作，而不是在託管代碼之外執行的類比操作，例如通過平台叫用非託管代碼或直接調用 Win32 函數。 只有託管<xref:System.Security.Principal.WindowsIdentity>物件才能跨非同步點流動，除非`alwaysFlowImpersonationPolicy`元素已設置為 true （`<alwaysFlowImpersonationPolicy enabled="true"/>`。 將`alwaysFlowImpersonationPolicy`元素設置為 true 指定 Windows 標識始終跨非同步點流動，而不考慮類比的執行方式。 有關跨非同步點的流式非託管類比的詳細資訊，請參閱[\<始終 FlowImpersonation 策略>元素](alwaysflowimpersonationpolicy-element.md)。  
  
 您可以通過兩種其他方式更改此預設行為：  
  
1. 在基於每個執行緒的託管代碼中。  
  
     通過使用<xref:System.Threading.ExecutionContext>修改 和<xref:System.Security.SecurityContext>設置<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>，可以使用 或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法，從而在每個執行緒的基礎上禁止流。  
  
2. 在調用非託管主機介面以載入通用語言運行時 （CLR）。  
  
     如果使用非託管託管介面（而不是簡單的託管可執行檔）來載入 CLR，則可以在[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的調用中指定一個特殊的標誌。 要為整個過程啟用相容性模式，將`flags` [CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的參數設置為STARTUP_LEGACY_IMPERSONATION。  
  
 有關詳細資訊，請參閱[\<始終 FlowImpersonaton 策略>元素](alwaysflowimpersonationpolicy-element.md)。  
  
## <a name="configuration-file"></a>組態檔  
 在 .NET 框架應用程式中，此元素只能在應用程式佈建檔中使用。  
  
 對於ASP.NET應用程式，可以在\<Windows 資料夾>_Microsoft.NET_Framework_vx.x.xxx 目錄中的 aspnet.config 檔中配置類比流。  
  
 預設情況下ASP.NET使用以下配置設置禁用 aspnet.config 檔中的類比流：  
  
``` xml
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
 下面的示例演示如何指定不跨非同步點流式到 Windows 標識的舊行為。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [\<源流類比策略>元素](alwaysflowimpersonationpolicy-element.md)
