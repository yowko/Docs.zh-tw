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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fa6b9aa2b2c427c86da5204a446cc60eadd1bb7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201009"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy > 項目
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
|`enabled`|必要屬性。<br /><br /> 指定<xref:System.Security.Principal.WindowsIdentity>不會流經非同步點，無論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> 根據非同步點間流量<xref:System.Threading.ExecutionContext>流程目前執行緒的設定。 這是預設值。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> 不會流經非同步點，無論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET framework 1.0 和 1.1 版，<xref:System.Security.Principal.WindowsIdentity>不會傳送到任何使用者定義的非同步點。 從.NET Framework 2.0 版開始，沒有<xref:System.Threading.ExecutionContext>物件，包含目前執行中執行緒，和它的資訊流過應用程式定義域中的非同步點。 <xref:System.Security.Principal.WindowsIdentity>納入此執行內容，且因此也流經非同步點，這表示，如果模擬內容存在，將會傳送它以及。  
  
 從.NET Framework 2.0 開始，您可以使用`<legacyImpersonationPolicy>`項目來指定，<xref:System.Security.Principal.WindowsIdentity>不會流經非同步點。  
  
> [!NOTE]
>  Common language runtime (CLR) 並知道使用 managed 程式碼，不是模擬外部 managed 程式碼，例如執行透過平台執行的作業叫用 unmanaged 程式碼，或透過直接呼叫 Win32 函式的模擬。 只有受控<xref:System.Security.Principal.WindowsIdentity>物件可以流經非同步點，除非`alwaysFlowImpersonationPolicy`項目已設定為 true (`<alwaysFlowImpersonationPolicy enabled="true"/>`)。 設定`alwaysFlowImpersonationPolicy`設為 true 的項目會指定 Windows 識別一律流經非同步點，不論模擬的執行方式。 如需詳細資訊流動 unmanaged 模擬跨非同步點，請參閱 < [ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。  
  
 您可以變更此預設行為，另外兩種方式：  
  
1.  在每個執行緒為基礎的 managed 程式碼。  
  
     您可以隱藏個別的執行緒上的流程，藉由修改<xref:System.Threading.ExecutionContext>並<xref:System.Security.SecurityContext>藉由設定<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>，<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。  
  
2.  在呼叫 unmanaged 裝載介面載入 common language runtime (CLR)。  
  
     如果 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔） 用來載入 CLR，您可以呼叫中指定特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。 若要啟用相容性模式，整個程序，將`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)STARTUP_LEGACY_IMPERSONATION 到。  
  
 如需詳細資訊，請參閱 < [ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。  
  
## <a name="configuration-file"></a>組態檔  
 在.NET Framework 應用程式中，這個項目只可以用於與應用程式組態檔。  
  
 針對 ASP.NET 應用程式，可以設定模擬流程 aspnet.config 檔案中找到\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。  
  
 ASP.NET 預設會使用下列組態設定，停用模擬流程 aspnet.config 檔案：  
  
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
 下列範例示範如何指定不會流經非同步點的 Windows 身分識別的舊行為。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
