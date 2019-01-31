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
ms.openlocfilehash: a731a54771f3ac589031e856539ba0c21ca22778
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270484"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="37ace-102">\<legacyImpersonationPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="37ace-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="37ace-103">指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="37ace-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="37ace-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="37ace-104">\<configuration></span></span>  
<span data-ttu-id="37ace-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="37ace-105">\<runtime></span></span>  
<span data-ttu-id="37ace-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="37ace-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ace-107">語法</span><span class="sxs-lookup"><span data-stu-id="37ace-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37ace-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="37ace-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37ace-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="37ace-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37ace-110">屬性</span><span class="sxs-lookup"><span data-stu-id="37ace-110">Attributes</span></span>  
  
|<span data-ttu-id="37ace-111">屬性</span><span class="sxs-lookup"><span data-stu-id="37ace-111">Attribute</span></span>|<span data-ttu-id="37ace-112">描述</span><span class="sxs-lookup"><span data-stu-id="37ace-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="37ace-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="37ace-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="37ace-114">指定<xref:System.Security.Principal.WindowsIdentity>不會流經非同步點，無論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="37ace-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="37ace-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="37ace-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="37ace-116">值</span><span class="sxs-lookup"><span data-stu-id="37ace-116">Value</span></span>|<span data-ttu-id="37ace-117">描述</span><span class="sxs-lookup"><span data-stu-id="37ace-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="37ace-118"><xref:System.Security.Principal.WindowsIdentity> 根據非同步點間流量<xref:System.Threading.ExecutionContext>流程目前執行緒的設定。</span><span class="sxs-lookup"><span data-stu-id="37ace-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="37ace-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="37ace-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="37ace-120"><xref:System.Security.Principal.WindowsIdentity> 不會流經非同步點，無論<xref:System.Threading.ExecutionContext>流程目前的執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="37ace-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37ace-121">子元素</span><span class="sxs-lookup"><span data-stu-id="37ace-121">Child Elements</span></span>  
 <span data-ttu-id="37ace-122">無。</span><span class="sxs-lookup"><span data-stu-id="37ace-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37ace-123">父項目</span><span class="sxs-lookup"><span data-stu-id="37ace-123">Parent Elements</span></span>  
  
|<span data-ttu-id="37ace-124">項目</span><span class="sxs-lookup"><span data-stu-id="37ace-124">Element</span></span>|<span data-ttu-id="37ace-125">描述</span><span class="sxs-lookup"><span data-stu-id="37ace-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="37ace-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="37ace-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="37ace-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="37ace-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ace-128">備註</span><span class="sxs-lookup"><span data-stu-id="37ace-128">Remarks</span></span>  
 <span data-ttu-id="37ace-129">在.NET framework 1.0 和 1.1 版，<xref:System.Security.Principal.WindowsIdentity>不會傳送到任何使用者定義的非同步點。</span><span class="sxs-lookup"><span data-stu-id="37ace-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="37ace-130">從.NET Framework 2.0 版開始，沒有<xref:System.Threading.ExecutionContext>物件，包含目前執行中執行緒，和它的資訊流過應用程式定義域中的非同步點。</span><span class="sxs-lookup"><span data-stu-id="37ace-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="37ace-131"><xref:System.Security.Principal.WindowsIdentity>納入此執行內容，且因此也流經非同步點，這表示，如果模擬內容存在，將會傳送它以及。</span><span class="sxs-lookup"><span data-stu-id="37ace-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="37ace-132">從.NET Framework 2.0 開始，您可以使用`<legacyImpersonationPolicy>`項目來指定，<xref:System.Security.Principal.WindowsIdentity>不會流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="37ace-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37ace-133">Common language runtime (CLR) 並知道使用 managed 程式碼，不是模擬外部 managed 程式碼，例如執行透過平台執行的作業叫用 unmanaged 程式碼，或透過直接呼叫 Win32 函式的模擬。</span><span class="sxs-lookup"><span data-stu-id="37ace-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="37ace-134">只有受控<xref:System.Security.Principal.WindowsIdentity>物件可以流經非同步點，除非`alwaysFlowImpersonationPolicy`項目已設定為 true (`<alwaysFlowImpersonationPolicy enabled="true"/>`)。</span><span class="sxs-lookup"><span data-stu-id="37ace-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="37ace-135">設定`alwaysFlowImpersonationPolicy`設為 true 的項目會指定 Windows 識別一律流經非同步點，不論模擬的執行方式。</span><span class="sxs-lookup"><span data-stu-id="37ace-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="37ace-136">如需詳細資訊流動 unmanaged 模擬跨非同步點，請參閱 < [ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="37ace-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="37ace-137">您可以變更此預設行為，另外兩種方式：</span><span class="sxs-lookup"><span data-stu-id="37ace-137">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="37ace-138">在每個執行緒為基礎的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="37ace-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="37ace-139">您可以隱藏個別的執行緒上的流程，藉由修改<xref:System.Threading.ExecutionContext>並<xref:System.Security.SecurityContext>藉由設定<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>，<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="37ace-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="37ace-140">在呼叫 unmanaged 裝載介面載入 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="37ace-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="37ace-141">如果 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔） 用來載入 CLR，您可以呼叫中指定特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="37ace-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="37ace-142">若要啟用相容性模式，整個程序，將`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)STARTUP_LEGACY_IMPERSONATION 到。</span><span class="sxs-lookup"><span data-stu-id="37ace-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="37ace-143">如需詳細資訊，請參閱 < [ \<alwaysFlowImpersonationPolicy > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="37ace-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="37ace-144">組態檔</span><span class="sxs-lookup"><span data-stu-id="37ace-144">Configuration File</span></span>  
 <span data-ttu-id="37ace-145">在.NET Framework 應用程式中，這個項目只可以用於與應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="37ace-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="37ace-146">針對 ASP.NET 應用程式，可以設定模擬流程 aspnet.config 檔案中找到\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。</span><span class="sxs-lookup"><span data-stu-id="37ace-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="37ace-147">ASP.NET 預設會使用下列組態設定，停用模擬流程 aspnet.config 檔案：</span><span class="sxs-lookup"><span data-stu-id="37ace-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="37ace-148">在 ASP.NET 中，如果您想要允許的模擬流程相反地，您必須明確地使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="37ace-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="37ace-149">範例</span><span class="sxs-lookup"><span data-stu-id="37ace-149">Example</span></span>  
 <span data-ttu-id="37ace-150">下列範例示範如何指定不會流經非同步點的 Windows 身分識別的舊行為。</span><span class="sxs-lookup"><span data-stu-id="37ace-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37ace-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37ace-151">See also</span></span>
- [<span data-ttu-id="37ace-152">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="37ace-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="37ace-153">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="37ace-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="37ace-154">\<alwaysFlowImpersonationPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="37ace-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
