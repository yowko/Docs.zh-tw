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
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="c766c-102">\<源流類比策略>元素</span><span class="sxs-lookup"><span data-stu-id="c766c-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="c766c-103">指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="c766c-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="c766c-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c766c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c766c-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c766c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c766c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<始終流類比策略>**</span><span class="sxs-lookup"><span data-stu-id="c766c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="c766c-107">語法</span><span class="sxs-lookup"><span data-stu-id="c766c-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c766c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c766c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c766c-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c766c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c766c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c766c-110">Attributes</span></span>  
  
|<span data-ttu-id="c766c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c766c-111">Attribute</span></span>|<span data-ttu-id="c766c-112">描述</span><span class="sxs-lookup"><span data-stu-id="c766c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c766c-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c766c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c766c-114">指示 Windows 標識是否跨非同步點流動。</span><span class="sxs-lookup"><span data-stu-id="c766c-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c766c-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="c766c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c766c-116">值</span><span class="sxs-lookup"><span data-stu-id="c766c-116">Value</span></span>|<span data-ttu-id="c766c-117">描述</span><span class="sxs-lookup"><span data-stu-id="c766c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c766c-118">Windows 標識不會跨非同步點流動，除非通過託管方法（如<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>） 執行類比。</span><span class="sxs-lookup"><span data-stu-id="c766c-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="c766c-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c766c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c766c-120">無論類比執行方式如何，Windows 標識始終跨非同步點流動。</span><span class="sxs-lookup"><span data-stu-id="c766c-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c766c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c766c-121">Child Elements</span></span>  
 <span data-ttu-id="c766c-122">無。</span><span class="sxs-lookup"><span data-stu-id="c766c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c766c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c766c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c766c-124">元素</span><span class="sxs-lookup"><span data-stu-id="c766c-124">Element</span></span>|<span data-ttu-id="c766c-125">描述</span><span class="sxs-lookup"><span data-stu-id="c766c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c766c-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c766c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c766c-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="c766c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c766c-128">備註</span><span class="sxs-lookup"><span data-stu-id="c766c-128">Remarks</span></span>  
 <span data-ttu-id="c766c-129">在 .NET 框架版本 1.0 和 1.1 中，Windows 標識不會跨非同步點流動。</span><span class="sxs-lookup"><span data-stu-id="c766c-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="c766c-130">在 .NET Framework 版本 2.0<xref:System.Threading.ExecutionContext>中，有一個物件包含有關當前正在執行的執行緒的資訊，並跨應用程式域中的非同步點進行流。</span><span class="sxs-lookup"><span data-stu-id="c766c-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="c766c-131">如果<xref:System.Security.Principal.WindowsIdentity>類比是使用託管方法（如，<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>而不是通過其他方法（如平台叫用本機方法）實現的，則該函數也會作為流經非同步點的資訊的一部分進行流動。</span><span class="sxs-lookup"><span data-stu-id="c766c-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="c766c-132">此元素用於指定 Windows 標識確實跨非同步點流動，而不考慮類比是如何實現的。</span><span class="sxs-lookup"><span data-stu-id="c766c-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="c766c-133">您可以通過兩種其他方式更改此預設行為：</span><span class="sxs-lookup"><span data-stu-id="c766c-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="c766c-134">在基於每個執行緒的託管代碼中。</span><span class="sxs-lookup"><span data-stu-id="c766c-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="c766c-135"><xref:System.Threading.ExecutionContext>通過使用 、 或<xref:System.Security.SecurityContext><xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法修改 和 設置，可以按執行緒禁止流。</span><span class="sxs-lookup"><span data-stu-id="c766c-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="c766c-136">在調用非託管主機介面以載入通用語言運行時 （CLR）。</span><span class="sxs-lookup"><span data-stu-id="c766c-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="c766c-137">如果使用非託管託管介面（而不是簡單的託管可執行檔）來載入 CLR，則可以在[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的調用中指定一個特殊的標誌。</span><span class="sxs-lookup"><span data-stu-id="c766c-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="c766c-138">要為整個過程啟用相容性模式，將`flags`[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的參數設置為`STARTUP_ALWAYSFLOW_IMPERSONATION`。</span><span class="sxs-lookup"><span data-stu-id="c766c-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="c766c-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="c766c-139">Configuration File</span></span>  
 <span data-ttu-id="c766c-140">在 .NET 框架應用程式中，此元素只能在應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="c766c-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="c766c-141">對於ASP.NET應用程式，可以在\<Windows 資料夾>_Microsoft.NET_Framework_vx.x.xxx 目錄中的 aspnet.config 檔中配置類比流。</span><span class="sxs-lookup"><span data-stu-id="c766c-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="c766c-142">預設情況下ASP.NET使用以下配置設置禁用 aspnet.config 檔中的類比流：</span><span class="sxs-lookup"><span data-stu-id="c766c-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="c766c-143">在ASP.NET中，如果要改為允許類比流，則必須顯式使用以下配置設置：</span><span class="sxs-lookup"><span data-stu-id="c766c-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="c766c-144">範例</span><span class="sxs-lookup"><span data-stu-id="c766c-144">Example</span></span>  
 <span data-ttu-id="c766c-145">下面的示例演示如何指定 Windows 標識跨非同步點流動，即使類比是通過託管方法以外的方法實現的。</span><span class="sxs-lookup"><span data-stu-id="c766c-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c766c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c766c-146">See also</span></span>

- [<span data-ttu-id="c766c-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c766c-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c766c-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c766c-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c766c-149">\<傳統類比策略>元素</span><span class="sxs-lookup"><span data-stu-id="c766c-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
