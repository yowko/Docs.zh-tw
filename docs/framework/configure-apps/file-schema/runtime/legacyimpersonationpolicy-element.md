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
ms.openlocfilehash: 4cf997c8ff13e0a6a4664ea3b538ac0def1baacf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663632"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy > 元素
指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。  
  
 \<configuration>  
\<執行時間 >  
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
|`enabled`|必要屬性。<br /><br /> 指定不流經非同步點, 而不論目前線程上的<xref:System.Threading.ExecutionContext>流程設定為何。<xref:System.Security.Principal.WindowsIdentity>|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>根據目前線程的流程設定, <xref:System.Threading.ExecutionContext>在非同步點之間流動。 這是預設值。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>不會流經非同步點, 而不論<xref:System.Threading.ExecutionContext>目前線程上的流程設定為何。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET Framework 版本1.0 和1.1 中, 不<xref:System.Security.Principal.WindowsIdentity>會流經任何使用者定義的非同步點。 從 .NET Framework 版本2.0 開始, 有一個<xref:System.Threading.ExecutionContext>物件包含目前執行中線程的相關資訊, 而且它會在應用程式域內的非同步點之間流動。 <xref:System.Security.Principal.WindowsIdentity>會包含在這個執行內容中, 因此也會流經非同步點, 這表示如果模擬內容存在, 它也會流動。  
  
 從 .NET Framework 2.0 開始, 您可以使用`<legacyImpersonationPolicy>`元素來<xref:System.Security.Principal.WindowsIdentity>指定不流經非同步點。  
  
> [!NOTE]
>  通用語言執行平臺 (CLR) 會感知僅使用 managed 程式碼執行的模擬作業, 而不是在 managed 程式碼外部執行的模擬, 例如透過平台叫用來進行非受控程式碼, 或透過直接呼叫 Win32 函數。 除非專案<xref:System.Security.Principal.WindowsIdentity>已設定為 true (`<alwaysFlowImpersonationPolicy enabled="true"/>`), 否則只有managed物件可以流經非同步點。`alwaysFlowImpersonationPolicy` `alwaysFlowImpersonationPolicy`將專案設定為 true, 會指定 Windows 識別一律流經非同步點, 而不論模擬的執行方式為何。 如需有關跨非同步點流動非受控模擬的詳細資訊, 請參閱[ \<alwaysFlowImpersonationPolicy > 元素](alwaysflowimpersonationpolicy-element.md)。  
  
 您可以透過兩種其他方式來改變此預設行為:  
  
1. 在 managed 程式碼中, 以每個執行緒為基礎。  
  
     <xref:System.Threading.ExecutionContext>您可以使用、或<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>方法來修改和<xref:System.Security.SecurityContext>設定, 以隱藏每個執行緒的流程。 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>  
  
2. 在非受控裝載介面的呼叫中, 載入 common language runtime (CLR)。  
  
     如果使用非受控裝載介面 (而不是簡單的 managed 可執行檔) 來載入 CLR, 您可以在呼叫[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式中指定特殊旗標。 若要啟用整個進程的相容性模式, 請將`flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式的參數設定為 STARTUP_LEGACY_IMPERSONATION。  
  
 如需詳細資訊, 請參閱[ \<alwaysFlowImpersonationPolicy > 元素](alwaysflowimpersonationpolicy-element.md)。  
  
## <a name="configuration-file"></a>組態檔  
 在 .NET Framework 應用程式中, 這個元素只能用在應用程式佈建檔中。  
  
 針對 ASP.NET 應用程式, 可以在\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet .config 檔案中設定模擬流程。  
  
 ASP.NET 預設會使用下列設定來停用 aspnet .config 檔案中的模擬流程:  
  
``` xml
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
 下列範例示範如何指定不會跨非同步點傳送 Windows 識別的舊版行為。  
  
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
- [\<alwaysFlowImpersonationPolicy > 元素](alwaysflowimpersonationpolicy-element.md)
