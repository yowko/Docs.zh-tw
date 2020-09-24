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
ms.openlocfilehash: 9316f026a807b6ad36014157061f67bdbd7d3d18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149435"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> 項目

指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指出 Windows 身分識別是否流經非同步點。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|除非透過 managed 方法（例如）執行模擬，否則 Windows 身分識別不會在非同步點之間流動 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 。 此為預設值。|  
|`true`|Windows 身分識別一律會流經非同步點，而不論模擬的執行方式為何。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 在 .NET Framework 1.0 和1.1 版中，Windows 身分識別不會在非同步點之間流動。 在 .NET Framework 2.0 版中，有一個 <xref:System.Threading.ExecutionContext> 物件包含目前執行中線程的相關資訊，並在應用程式域內的非同步點之間流動。 <xref:System.Security.Principal.WindowsIdentity>它也會在流經非同步點的資訊中流動，但前提是使用 managed 方法（例如 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> ，而不是透過其他方法（例如平台叫用）來達到模擬。 這個元素可用來指定 Windows 身分識別會在非同步點之間流動，而不論模擬的達成方式為何。  
  
 您可以透過兩種其他方式來改變這個預設行為：  
  
1. 在 managed 程式碼中，以每個執行緒為基礎。  
  
     您可以 <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> 使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> 、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> 或方法修改和設定，以每個執行緒為基礎來隱藏流程 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> 。  
  
2. 在非受控裝載介面的呼叫中，將 common language runtime 載入 (CLR) 。  
  
     如果使用非受控裝載介面 (而非簡單的 managed 可執行檔) 用來載入 CLR，您可以在 [CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的呼叫中指定特殊旗標。 若要啟用整個進程的相容性模式，請將 `flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的參數設定為 `STARTUP_ALWAYSFLOW_IMPERSONATION` 。  
  
## <a name="configuration-file"></a>組態檔  

 在 .NET Framework 應用程式中，這個元素只能用在應用程式佈建檔中。  
  
 針對 ASP.NET 應用程式，您可以在 \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet.config 檔案中設定模擬流程 \<Windows Folder> 。  
  
 ASP.NET 預設會使用下列設定來停用 aspnet.config 檔案中的模擬流程：  
  
```xml
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

 下列範例示範如何指定 Windows 身分識別流經非同步點，即使是透過 managed 方法以外的方式來達成模擬也是一樣。  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
- [\<legacyImpersonationPolicy> 元素](legacyimpersonationpolicy-element.md)
