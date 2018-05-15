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
---
# <a name="ltlegacyimpersonationpolicygt-element"></a><span data-ttu-id="0aa73-102">&lt;legacyImpersonationPolicy&gt;項目</span><span class="sxs-lookup"><span data-stu-id="0aa73-102">&lt;legacyImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="0aa73-103">指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="0aa73-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="0aa73-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0aa73-104">\<configuration></span></span>  
<span data-ttu-id="0aa73-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="0aa73-105">\<runtime></span></span>  
<span data-ttu-id="0aa73-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="0aa73-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa73-107">語法</span><span class="sxs-lookup"><span data-stu-id="0aa73-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0aa73-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0aa73-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0aa73-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0aa73-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0aa73-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0aa73-110">Attributes</span></span>  
  
|<span data-ttu-id="0aa73-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0aa73-111">Attribute</span></span>|<span data-ttu-id="0aa73-112">描述</span><span class="sxs-lookup"><span data-stu-id="0aa73-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0aa73-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0aa73-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0aa73-114">指定<xref:System.Security.Principal.WindowsIdentity>不會流動到非同步的點，不論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="0aa73-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0aa73-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="0aa73-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0aa73-116">值</span><span class="sxs-lookup"><span data-stu-id="0aa73-116">Value</span></span>|<span data-ttu-id="0aa73-117">描述</span><span class="sxs-lookup"><span data-stu-id="0aa73-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0aa73-118"><xref:System.Security.Principal.WindowsIdentity> 非同步而定的點之間的流量<xref:System.Threading.ExecutionContext>流程設定目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0aa73-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="0aa73-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0aa73-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0aa73-120"><xref:System.Security.Principal.WindowsIdentity> 不會流動到非同步的點，不論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="0aa73-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0aa73-121">子項目</span><span class="sxs-lookup"><span data-stu-id="0aa73-121">Child Elements</span></span>  
 <span data-ttu-id="0aa73-122">無。</span><span class="sxs-lookup"><span data-stu-id="0aa73-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0aa73-123">父項目</span><span class="sxs-lookup"><span data-stu-id="0aa73-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0aa73-124">項目</span><span class="sxs-lookup"><span data-stu-id="0aa73-124">Element</span></span>|<span data-ttu-id="0aa73-125">描述</span><span class="sxs-lookup"><span data-stu-id="0aa73-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0aa73-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0aa73-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0aa73-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="0aa73-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aa73-128">備註</span><span class="sxs-lookup"><span data-stu-id="0aa73-128">Remarks</span></span>  
 <span data-ttu-id="0aa73-129">在.NET framework 1.0 和 1.1 版，<xref:System.Security.Principal.WindowsIdentity>不會流動到任何使用者定義的非同步點。</span><span class="sxs-lookup"><span data-stu-id="0aa73-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="0aa73-130">從.NET Framework 2.0 版開始，沒有<xref:System.Threading.ExecutionContext>非同步應用程式定義域中的點上的物件，其中包含目前執行中執行緒，和它的資訊傳輸。</span><span class="sxs-lookup"><span data-stu-id="0aa73-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="0aa73-131"><xref:System.Security.Principal.WindowsIdentity>隨附於此執行內容，因此也會流動到非同步的點，這表示，如果模擬內容存在，它將資料流程以及。</span><span class="sxs-lookup"><span data-stu-id="0aa73-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="0aa73-132">從.NET Framework 2.0 開始，您可以使用`<legacyImpersonationPolicy>`以指定的項目<xref:System.Security.Principal.WindowsIdentity>不會流動到非同步的點。</span><span class="sxs-lookup"><span data-stu-id="0aa73-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aa73-133">Common language runtime (CLR) 並知道模擬使用 managed 程式碼，不是模擬以外 managed 程式碼，例如執行可透過平台執行的作業叫用 unmanaged 程式碼或透過直接呼叫 Win32 函式。</span><span class="sxs-lookup"><span data-stu-id="0aa73-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="0aa73-134">只能管理<xref:System.Security.Principal.WindowsIdentity>物件流向可跨非同步的點，除非`alwaysFlowImpersonationPolicy`項目已設定為 true (`<alwaysFlowImpersonationPolicy enabled="true"/>`)。</span><span class="sxs-lookup"><span data-stu-id="0aa73-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="0aa73-135">設定`alwaysFlowImpersonationPolicy`為 true 的項目會指定 Windows 身分識別一律流動到非同步的點，無論模擬執行的方式。</span><span class="sxs-lookup"><span data-stu-id="0aa73-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="0aa73-136">如需詳細資訊傳送到非同步點 unmanaged 模擬，請參閱[ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="0aa73-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="0aa73-137">您可以變更此預設行為，另外兩種方式：</span><span class="sxs-lookup"><span data-stu-id="0aa73-137">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="0aa73-138">在每個執行緒為基礎的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0aa73-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="0aa73-139">您可以藉由修改隱藏每個執行緒為基礎的流程<xref:System.Threading.ExecutionContext>和<xref:System.Security.SecurityContext>設定使用<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>，<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="0aa73-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="0aa73-140">在載入 common language runtime (CLR) 的 unmanaged 裝載介面的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0aa73-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="0aa73-141">如果載入 CLR 用於 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔），您可以呼叫中指定的特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="0aa73-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="0aa73-142">若要啟用的整個程序的相容性模式，`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)STARTUP_LEGACY_IMPERSONATION 至。</span><span class="sxs-lookup"><span data-stu-id="0aa73-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="0aa73-143">如需詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="0aa73-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0aa73-144">組態檔</span><span class="sxs-lookup"><span data-stu-id="0aa73-144">Configuration File</span></span>  
 <span data-ttu-id="0aa73-145">在.NET Framework 應用程式中，此項目只可以用於與應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="0aa73-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="0aa73-146">可以位於 aspnet.config 檔案中設定 ASP.NET 應用程式，模擬流程\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。</span><span class="sxs-lookup"><span data-stu-id="0aa73-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="0aa73-147">預設的 ASP.NET 中，會停用模擬流程 aspnet.config 檔案中的使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="0aa73-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="0aa73-148">在 ASP.NET 中，如果您想要允許的模擬流程相反地，您必須明確地使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="0aa73-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="0aa73-149">範例</span><span class="sxs-lookup"><span data-stu-id="0aa73-149">Example</span></span>  
 <span data-ttu-id="0aa73-150">下列範例會示範如何指定舊版的行為，不會跨非同步點流動的 Windows 身分識別。</span><span class="sxs-lookup"><span data-stu-id="0aa73-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0aa73-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0aa73-151">See Also</span></span>  
 [<span data-ttu-id="0aa73-152">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0aa73-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0aa73-153">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0aa73-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0aa73-154">\<alwaysFlowImpersonationPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="0aa73-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
