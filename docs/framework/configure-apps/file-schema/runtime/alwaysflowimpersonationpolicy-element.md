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
ms.openlocfilehash: 164492eb1abc7329481f158963118b47d2c4aebc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252867"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy > 元素
指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<alwaysFlowImpersonationPolicy>** \  
  
## <a name="syntax"></a>語法  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指出 Windows 身分識別是否流經非同步點。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|說明|  
|-----------|-----------------|  
|`false`|Windows 識別不會流經非同步點, 除非模擬是透過 managed 方法 (例如) <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>來執行。 這是預設值。|  
|`true`|無論模擬的執行方式為何, Windows 身分識別一律會流經非同步點。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET Framework 版本1.0 和1.1 中, Windows 識別不會流經非同步點。 在 .NET Framework 版本2.0 中, 有一個<xref:System.Threading.ExecutionContext>物件包含目前執行中線程的相關資訊, 並會在應用程式域內的非同步點之間流動。 也會在流經非同步點的資訊中流動, 但前提是使用 managed 方法 (例如) <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>來達成模擬, 而不是透過其他方式 (例如平台叫用) 來達成。 <xref:System.Security.Principal.WindowsIdentity> 此元素可用來指定 Windows 識別會在非同步點之間流動, 不論模擬的達成方式為何。  
  
 您可以透過兩種其他方式來改變此預設行為:  
  
1. 在 managed 程式碼中, 以每個執行緒為基礎。  
  
     <xref:System.Threading.ExecutionContext>您可以使用、或<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>方法來修改和<xref:System.Security.SecurityContext>設定, 以隱藏每個執行緒的流程。 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>  
  
2. 在非受控裝載介面的呼叫中, 載入 common language runtime (CLR)。  
  
     如果使用非受控裝載介面 (而不是簡單的 managed 可執行檔) 來載入 CLR, 您可以在呼叫[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式中指定特殊旗標。 若要啟用整個進程的相容性模式, 請將`flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式的參數`STARTUP_ALWAYSFLOW_IMPERSONATION`設定為。  
  
## <a name="configuration-file"></a>組態檔  
 在 .NET Framework 應用程式中, 這個元素只能用在應用程式佈建檔中。  
  
 針對 ASP.NET 應用程式, 可以在\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet .config 檔案中設定模擬流程。  
  
 ASP.NET 預設會使用下列設定來停用 aspnet .config 檔案中的模擬流程:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 在 ASP.NET 中, 如果您想要改為允許模擬的流程, 則必須明確地使用下列設定:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何指定 Windows 身分識別流經非同步點, 即使透過 managed 方法以外的方式來達成模擬也是一樣。  
  
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
- [\<legacyImpersonationPolicy > 元素](legacyimpersonationpolicy-element.md)
