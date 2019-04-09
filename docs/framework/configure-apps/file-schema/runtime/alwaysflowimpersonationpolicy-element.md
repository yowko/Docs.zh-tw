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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce1928254699f4de41e92087c76be9bc3c249523
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108039"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy > 項目
指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。  
  
 \<configuration>  
\<執行階段 >  
\<alwaysFlowImpersonationPolicy>  
  
## <a name="syntax"></a>語法  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 表示 Windows 身分識別是否流經非同步點。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|身分識別不會流經非同步點，除非透過執行模擬 Windows 之類的管理方法<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>。 這是預設值。|  
|`true`|Windows 識別一律流經非同步點，不論模擬的執行方式。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET framework 1.0 和 1.1 版中，Windows 身分識別不會流經非同步點。 在.NET Framework 2.0 版中，沒有<xref:System.Threading.ExecutionContext>物件，包含目前執行中執行緒，資訊流過應用程式定義域中的非同步點。 <xref:System.Security.Principal.WindowsIdentity>也做為一部分流經非同步點中，，模擬已達到使用提供的資訊流程之類的管理方法<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>並不是透過其他方式如平台叫用原生方法。 這個項目用來指定 Windows 身分識別會流經非同步點，無論達成的模擬。  
  
 您可以變更此預設行為，另外兩種方式：  
  
1.  在每個執行緒為基礎的 managed 程式碼。  
  
     您可以隱藏個別的執行緒上的流程，藉由修改<xref:System.Threading.ExecutionContext>並<xref:System.Security.SecurityContext>藉由設定<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>， <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>，或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。  
  
2.  在呼叫 unmanaged 裝載介面載入 common language runtime (CLR)。  
  
     如果 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔） 用來載入 CLR，您可以呼叫中指定特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。 若要啟用相容性模式，整個程序，將`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)至`STARTUP_ALWAYSFLOW_IMPERSONATION`。  
  
## <a name="configuration-file"></a>組態檔  
 在.NET Framework 應用程式中，這個項目只可以用於與應用程式組態檔。  
  
 針對 ASP.NET 應用程式，可以設定模擬流程 aspnet.config 檔案中找到\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。  
  
 ASP.NET 預設會使用下列組態設定，停用模擬流程 aspnet.config 檔案：  
  
```xml
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
 下列範例示範如何指定模擬可透過受管理的方法以外的方式，即使 Windows 身分識別存流經非同步點。  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<legacyImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
