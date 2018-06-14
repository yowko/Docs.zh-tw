---
title: '&lt;legacyImpersonationPolicy&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f90853a93b40eeb72f07ad9b1849aa99c8e8bf3d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745184"
---
# <a name="ltlegacyimpersonationpolicygt-element"></a>&lt;legacyImpersonationPolicy&gt;項目
指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。  
  
 \<configuration>  
\<執行階段 >  
\<legacyImpersonationPolicy>  
  
## <a name="syntax"></a>語法  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定<xref:System.Security.Principal.WindowsIdentity>不會流動到非同步的點，不論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> 非同步而定的點之間的流量<xref:System.Threading.ExecutionContext>流程設定目前的執行緒。 這是預設值。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> 不會流動到非同步的點，不論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET framework 1.0 和 1.1 版，<xref:System.Security.Principal.WindowsIdentity>不會流動到任何使用者定義的非同步點。 從.NET Framework 2.0 版開始，沒有<xref:System.Threading.ExecutionContext>非同步應用程式定義域中的點上的物件，其中包含目前執行中執行緒，和它的資訊傳輸。 <xref:System.Security.Principal.WindowsIdentity>隨附於此執行內容，因此也會流動到非同步的點，這表示，如果模擬內容存在，它將資料流程以及。  
  
 從.NET Framework 2.0 開始，您可以使用`<legacyImpersonationPolicy>`以指定的項目<xref:System.Security.Principal.WindowsIdentity>不會流動到非同步的點。  
  
> [!NOTE]
>  Common language runtime (CLR) 並知道模擬使用 managed 程式碼，不是模擬以外 managed 程式碼，例如執行可透過平台執行的作業叫用 unmanaged 程式碼或透過直接呼叫 Win32 函式。 只能管理<xref:System.Security.Principal.WindowsIdentity>物件流向可跨非同步的點，除非`alwaysFlowImpersonationPolicy`項目已設定為 true (`<alwaysFlowImpersonationPolicy enabled="true"/>`)。 設定`alwaysFlowImpersonationPolicy`為 true 的項目會指定 Windows 身分識別一律流動到非同步的點，無論模擬執行的方式。 如需詳細資訊傳送到非同步點 unmanaged 模擬，請參閱[ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。  
  
 您可以變更此預設行為，另外兩種方式：  
  
1.  在每個執行緒為基礎的 managed 程式碼。  
  
     您可以藉由修改隱藏每個執行緒為基礎的流程<xref:System.Threading.ExecutionContext>和<xref:System.Security.SecurityContext>設定使用<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>，<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。  
  
2.  在載入 common language runtime (CLR) 的 unmanaged 裝載介面的呼叫。  
  
     如果載入 CLR 用於 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔），您可以呼叫中指定的特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。 若要啟用的整個程序的相容性模式，`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)STARTUP_LEGACY_IMPERSONATION 至。  
  
 如需詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。  
  
## <a name="configuration-file"></a>組態檔  
 在.NET Framework 應用程式中，此項目只可以用於與應用程式組態檔。  
  
 可以位於 aspnet.config 檔案中設定 ASP.NET 應用程式，模擬流程\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。  
  
 預設的 ASP.NET 中，會停用模擬流程 aspnet.config 檔案中的使用下列組態設定：  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 在 ASP.NET 中，如果您想要允許的模擬流程相反地，您必須明確地使用下列組態設定：  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何指定舊版的行為，不會跨非同步點流動的 Windows 身分識別。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
