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
ms.openlocfilehash: ca10c809ddf319817aaa074ba5fc3415abf6387d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192512"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy> 項目

指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定 <xref:System.Security.Principal.WindowsIdentity> 不論 <xref:System.Threading.ExecutionContext> 目前線程上的流程設定為何，都不會在非同步點之間流動。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> 依據目前線程的流程設定，在非同步點之間流動 <xref:System.Threading.ExecutionContext> 。 此為預設值。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> 無論 <xref:System.Threading.ExecutionContext> 目前線程上的流程設定為何，都不會在非同步點之間流動。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 在 .NET Framework 1.0 和1.1 版中，不 <xref:System.Security.Principal.WindowsIdentity> 會在任何使用者定義的非同步點之間流動。 從 .NET Framework 版本2.0 開始，有一個 <xref:System.Threading.ExecutionContext> 物件包含目前執行中線程的相關資訊，並且會在應用程式域內的非同步點之間流動。 <xref:System.Security.Principal.WindowsIdentity>包含在此執行內容中，因此也會在非同步點之間流動，這表示如果有模擬內容，則也會進行流動。  
  
 從 .NET Framework 2.0 開始，您可以使用 `<legacyImpersonationPolicy>` 元素來指定不  <xref:System.Security.Principal.WindowsIdentity> 會在非同步點之間流動。  
  
> [!NOTE]
> Common language runtime (CLR) 知道使用 managed 程式碼執行的模擬作業，而不是在 managed 程式碼之外執行的模擬，例如透過平台叫用至非受控程式碼，或直接呼叫 Win32 函數。 <xref:System.Security.Principal.WindowsIdentity>除非已將專案設定為 true，否則只有 managed 物件可以在非同步點之間流動 `alwaysFlowImpersonationPolicy` (`<alwaysFlowImpersonationPolicy enabled="true"/>`) 。 將專案設定 `alwaysFlowImpersonationPolicy` 為 true，會指定無論模擬的執行方式為何，Windows 身分識別一律會流經非同步點。 如需跨非同步點流動非受控模擬的詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy> 元素](alwaysflowimpersonationpolicy-element.md)。  
  
 您可以透過兩種其他方式來改變這個預設行為：  
  
1. 在 managed 程式碼中，以每個執行緒為基礎。  
  
     您可以 <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> 使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> 、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> 或方法修改和設定，以每個執行緒為基礎來隱藏流程 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> 。  
  
2. 在非受控裝載介面的呼叫中，將 common language runtime 載入 (CLR) 。  
  
     如果使用非受控裝載介面 (而非簡單的 managed 可執行檔) 用來載入 CLR，您可以在 [CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的呼叫中指定特殊旗標。 若要啟用整個進程的相容性模式，請將 `flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的參數設定為 STARTUP_LEGACY_IMPERSONATION。  
  
 如需詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy> 元素](alwaysflowimpersonationpolicy-element.md)。  
  
## <a name="configuration-file"></a>組態檔  

 在 .NET Framework 應用程式中，這個元素只能用在應用程式佈建檔中。  
  
 針對 ASP.NET 應用程式，您可以在 \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet.config 檔案中設定模擬流程 \<Windows Folder> 。  
  
 ASP.NET 預設會使用下列設定來停用 aspnet.config 檔案中的模擬流程：  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 在 ASP.NET 中，如果您想要改為允許模擬的流程，您必須明確地使用下列設定：  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>範例  

 下列範例示範如何指定不會跨非同步點傳送 Windows 身分識別的舊版行為。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
- [\<alwaysFlowImpersonationPolicy> 元素](alwaysflowimpersonationpolicy-element.md)
