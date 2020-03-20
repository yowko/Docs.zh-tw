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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154100"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="e67c2-102">\<傳統類比策略>元素</span><span class="sxs-lookup"><span data-stu-id="e67c2-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="e67c2-103">指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="e67c2-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="e67c2-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e67c2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e67c2-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e67c2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e67c2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<傳統類比策略>**</span><span class="sxs-lookup"><span data-stu-id="e67c2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e67c2-107">語法</span><span class="sxs-lookup"><span data-stu-id="e67c2-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e67c2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e67c2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e67c2-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e67c2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e67c2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e67c2-110">Attributes</span></span>  
  
|<span data-ttu-id="e67c2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e67c2-111">Attribute</span></span>|<span data-ttu-id="e67c2-112">描述</span><span class="sxs-lookup"><span data-stu-id="e67c2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e67c2-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e67c2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e67c2-114">指定<xref:System.Security.Principal.WindowsIdentity>不跨非同步點流動，而不考慮當前執行緒上的<xref:System.Threading.ExecutionContext>流設置。</span><span class="sxs-lookup"><span data-stu-id="e67c2-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e67c2-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="e67c2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e67c2-116">值</span><span class="sxs-lookup"><span data-stu-id="e67c2-116">Value</span></span>|<span data-ttu-id="e67c2-117">描述</span><span class="sxs-lookup"><span data-stu-id="e67c2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e67c2-118"><xref:System.Security.Principal.WindowsIdentity>流經非同步點，<xref:System.Threading.ExecutionContext>具體取決於當前執行緒的流設置。</span><span class="sxs-lookup"><span data-stu-id="e67c2-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="e67c2-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="e67c2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e67c2-120"><xref:System.Security.Principal.WindowsIdentity>無論當前執行緒上的<xref:System.Threading.ExecutionContext>流設置如何，都不會在非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="e67c2-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e67c2-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e67c2-121">Child Elements</span></span>  
 <span data-ttu-id="e67c2-122">無。</span><span class="sxs-lookup"><span data-stu-id="e67c2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e67c2-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e67c2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e67c2-124">元素</span><span class="sxs-lookup"><span data-stu-id="e67c2-124">Element</span></span>|<span data-ttu-id="e67c2-125">描述</span><span class="sxs-lookup"><span data-stu-id="e67c2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e67c2-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e67c2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e67c2-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="e67c2-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e67c2-128">備註</span><span class="sxs-lookup"><span data-stu-id="e67c2-128">Remarks</span></span>  
 <span data-ttu-id="e67c2-129">在 .NET 框架版本 1.0 和 1.1 中，<xref:System.Security.Principal.WindowsIdentity>不會流過任何使用者定義的非同步點。</span><span class="sxs-lookup"><span data-stu-id="e67c2-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="e67c2-130">從 .NET Framework 版本 2.0 開始<xref:System.Threading.ExecutionContext>，有一個物件包含有關當前正在執行的執行緒的資訊，並且它跨應用程式域中的非同步點流動。</span><span class="sxs-lookup"><span data-stu-id="e67c2-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="e67c2-131"><xref:System.Security.Principal.WindowsIdentity>包含在此執行上下文中，因此也會跨非同步點流動，這意味著如果存在類比上下文，它也會流動。</span><span class="sxs-lookup"><span data-stu-id="e67c2-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="e67c2-132">從 .NET 框架 2.0 開始，可以使用`<legacyImpersonationPolicy>`元素指定<xref:System.Security.Principal.WindowsIdentity>不跨非同步點流動的元素。</span><span class="sxs-lookup"><span data-stu-id="e67c2-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e67c2-133">通用語言運行時 （CLR） 知道僅使用託管代碼執行的類比操作，而不是在託管代碼之外執行的類比操作，例如通過平台叫用非託管代碼或直接調用 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="e67c2-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="e67c2-134">只有託管<xref:System.Security.Principal.WindowsIdentity>物件才能跨非同步點流動，除非`alwaysFlowImpersonationPolicy`元素已設置為 true （`<alwaysFlowImpersonationPolicy enabled="true"/>`。</span><span class="sxs-lookup"><span data-stu-id="e67c2-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="e67c2-135">將`alwaysFlowImpersonationPolicy`元素設置為 true 指定 Windows 標識始終跨非同步點流動，而不考慮類比的執行方式。</span><span class="sxs-lookup"><span data-stu-id="e67c2-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="e67c2-136">有關跨非同步點的流式非託管類比的詳細資訊，請參閱[\<始終 FlowImpersonation 策略>元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="e67c2-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="e67c2-137">您可以通過兩種其他方式更改此預設行為：</span><span class="sxs-lookup"><span data-stu-id="e67c2-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="e67c2-138">在基於每個執行緒的託管代碼中。</span><span class="sxs-lookup"><span data-stu-id="e67c2-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="e67c2-139">通過使用<xref:System.Threading.ExecutionContext>修改 和<xref:System.Security.SecurityContext>設置<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>，可以使用 或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法，從而在每個執行緒的基礎上禁止流。</span><span class="sxs-lookup"><span data-stu-id="e67c2-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="e67c2-140">在調用非託管主機介面以載入通用語言運行時 （CLR）。</span><span class="sxs-lookup"><span data-stu-id="e67c2-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="e67c2-141">如果使用非託管託管介面（而不是簡單的託管可執行檔）來載入 CLR，則可以在[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的調用中指定一個特殊的標誌。</span><span class="sxs-lookup"><span data-stu-id="e67c2-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="e67c2-142">要為整個過程啟用相容性模式，將`flags` [CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)的參數設置為STARTUP_LEGACY_IMPERSONATION。</span><span class="sxs-lookup"><span data-stu-id="e67c2-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="e67c2-143">有關詳細資訊，請參閱[\<始終 FlowImpersonaton 策略>元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="e67c2-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e67c2-144">組態檔</span><span class="sxs-lookup"><span data-stu-id="e67c2-144">Configuration File</span></span>  
 <span data-ttu-id="e67c2-145">在 .NET 框架應用程式中，此元素只能在應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="e67c2-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="e67c2-146">對於ASP.NET應用程式，可以在\<Windows 資料夾>_Microsoft.NET_Framework_vx.x.xxx 目錄中的 aspnet.config 檔中配置類比流。</span><span class="sxs-lookup"><span data-stu-id="e67c2-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="e67c2-147">預設情況下ASP.NET使用以下配置設置禁用 aspnet.config 檔中的類比流：</span><span class="sxs-lookup"><span data-stu-id="e67c2-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="e67c2-148">在ASP.NET中，如果要改為允許類比流，則必須顯式使用以下配置設置：</span><span class="sxs-lookup"><span data-stu-id="e67c2-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e67c2-149">範例</span><span class="sxs-lookup"><span data-stu-id="e67c2-149">Example</span></span>  
 <span data-ttu-id="e67c2-150">下面的示例演示如何指定不跨非同步點流式到 Windows 標識的舊行為。</span><span class="sxs-lookup"><span data-stu-id="e67c2-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e67c2-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e67c2-151">See also</span></span>

- [<span data-ttu-id="e67c2-152">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e67c2-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e67c2-153">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e67c2-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e67c2-154">\<源流類比策略>元素</span><span class="sxs-lookup"><span data-stu-id="e67c2-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
