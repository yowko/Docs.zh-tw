---
title: "&lt;alwaysFlowImpersonationPolicy&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be1df955f7586848968cb32cd66a4c6889cfffa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;alwaysFlowImpersonationPolicy&gt;項目
指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。  
  
 \<configuration>  
\<執行階段 >  
\<alwaysFlowImpersonationPolicy >  
  
## <a name="syntax"></a>語法  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指出是否 Windows 身分識別流動到非同步的點。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|身分識別不會流動到非同步的點，除非透過執行模擬的 Windows managed 方法例如<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>。 這是預設值。|  
|`true`|Windows 識別一律流動到非同步的點，無論模擬執行的方式。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET framework 1.0 和 1.1 版中，Windows 身分識別不會流動到非同步的點。 在.NET Framework 2.0 版中，沒有<xref:System.Threading.ExecutionContext>物件，包含目前執行的執行緒的相關資訊，並傳送到非同步應用程式定義域中的點。 <xref:System.Security.Principal.WindowsIdentity>也流程一部分的資訊提供使用達成模擬流動到非同步的點，管理方法例如<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>並不能透過其他方式如平台叫用原生方法。 這個項目用來指定 Windows 身分識別沒有流經非同步的點，無論模擬所達成的效果。  
  
 您可以變更此預設行為，另外兩種方式：  
  
1.  在每個執行緒為基礎的 managed 程式碼。  
  
     您可以藉由修改隱藏每個執行緒為基礎的流程<xref:System.Threading.ExecutionContext>和<xref:System.Security.SecurityContext>設定使用<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>， <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>，或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。  
  
2.  在載入 common language runtime (CLR) 的 unmanaged 裝載介面的呼叫。  
  
     如果載入 CLR 用於 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔），您可以呼叫中指定的特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。 若要啟用的整個程序的相容性模式，`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)至`STARTUP_ALWAYSFLOW_IMPERSONATION`。  
  
## <a name="configuration-file"></a>組態檔  
 在.NET Framework 應用程式中，此項目只可以用於與應用程式組態檔。  
  
 可以位於 aspnet.config 檔案中設定 ASP.NET 應用程式，模擬流程\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。  
  
 預設的 ASP.NET 中，會停用模擬流程 aspnet.config 檔案中的使用下列組態設定：  
  
```  
configuration>  
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
 下列範例會示範如何指定 Windows 身分識別流動到非同步的點，即使模擬透過 managed 方法以外的方式來達成。  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<legacyImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
