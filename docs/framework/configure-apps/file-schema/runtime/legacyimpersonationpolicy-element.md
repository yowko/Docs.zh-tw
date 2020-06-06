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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154100"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="4ad3e-102">\<legacyImpersonationPolicy> 項目</span><span class="sxs-lookup"><span data-stu-id="4ad3e-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="4ad3e-103">指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="4ad3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ad3e-104">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ad3e-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4ad3e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4ad3e-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ad3e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4ad3e-107">Attributes</span></span>  
  
|<span data-ttu-id="4ad3e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4ad3e-108">Attribute</span></span>|<span data-ttu-id="4ad3e-109">描述</span><span class="sxs-lookup"><span data-stu-id="4ad3e-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4ad3e-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="4ad3e-111">指定不 <xref:System.Security.Principal.WindowsIdentity> 流經非同步點，而不論 <xref:System.Threading.ExecutionContext> 目前線程上的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-111">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4ad3e-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="4ad3e-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="4ad3e-113">值</span><span class="sxs-lookup"><span data-stu-id="4ad3e-113">Value</span></span>|<span data-ttu-id="4ad3e-114">描述</span><span class="sxs-lookup"><span data-stu-id="4ad3e-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4ad3e-115"><xref:System.Security.Principal.WindowsIdentity>根據目前線程的流程設定，在非同步點之間流動 <xref:System.Threading.ExecutionContext> 。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-115"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="4ad3e-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4ad3e-117"><xref:System.Security.Principal.WindowsIdentity>不會流經非同步點，而不論 <xref:System.Threading.ExecutionContext> 目前線程上的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-117"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ad3e-118">子元素</span><span class="sxs-lookup"><span data-stu-id="4ad3e-118">Child Elements</span></span>  
 <span data-ttu-id="4ad3e-119">無。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ad3e-120">父項目</span><span class="sxs-lookup"><span data-stu-id="4ad3e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4ad3e-121">元素</span><span class="sxs-lookup"><span data-stu-id="4ad3e-121">Element</span></span>|<span data-ttu-id="4ad3e-122">描述</span><span class="sxs-lookup"><span data-stu-id="4ad3e-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4ad3e-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4ad3e-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad3e-125">備註</span><span class="sxs-lookup"><span data-stu-id="4ad3e-125">Remarks</span></span>  
 <span data-ttu-id="4ad3e-126">在 .NET Framework 版本1.0 和1.1 中，不 <xref:System.Security.Principal.WindowsIdentity> 會流經任何使用者定義的非同步點。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-126">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="4ad3e-127">從 .NET Framework 版本2.0 開始，有一個 <xref:System.Threading.ExecutionContext> 物件包含目前執行中線程的相關資訊，而且它會在應用程式域內的非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-127">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="4ad3e-128"><xref:System.Security.Principal.WindowsIdentity>會包含在這個執行內容中，因此也會流經非同步點，這表示如果模擬內容存在，它也會流動。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-128">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="4ad3e-129">從 .NET Framework 2.0 開始，您可以使用 `<legacyImpersonationPolicy>` 元素來指定不 <xref:System.Security.Principal.WindowsIdentity> 流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-129">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ad3e-130">通用語言執行平臺（CLR）會感知僅使用 managed 程式碼執行的模擬作業，而不是在 managed 程式碼外部執行的模擬，例如透過平台叫用來進行非受控程式碼，或透過直接呼叫 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-130">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="4ad3e-131">除非專案 <xref:System.Security.Principal.WindowsIdentity> `alwaysFlowImpersonationPolicy` 已設定為 true （），否則只有 managed 物件可以流經非同步點 `<alwaysFlowImpersonationPolicy enabled="true"/>` 。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-131">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="4ad3e-132">將專案設定 `alwaysFlowImpersonationPolicy` 為 true，會指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-132">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="4ad3e-133">如需有關跨非同步點流動非受控模擬的詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy> 元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-133">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="4ad3e-134">您可以透過兩種其他方式來改變此預設行為：</span><span class="sxs-lookup"><span data-stu-id="4ad3e-134">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="4ad3e-135">在 managed 程式碼中，以每個執行緒為基礎。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-135">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="4ad3e-136">您可以 <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> 使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> 、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> 或方法來修改和設定，以隱藏每個執行緒的流程 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-136">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="4ad3e-137">在非受控裝載介面的呼叫中，載入 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-137">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="4ad3e-138">如果使用非受控裝載介面（而不是簡單的 managed 可執行檔）來載入 CLR，您可以在呼叫[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式中指定特殊旗標。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-138">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="4ad3e-139">若要啟用整個進程的相容性模式，請將 `flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式的參數設定為 STARTUP_LEGACY_IMPERSONATION。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-139">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="4ad3e-140">如需詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy> 元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-140">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4ad3e-141">組態檔</span><span class="sxs-lookup"><span data-stu-id="4ad3e-141">Configuration File</span></span>  
 <span data-ttu-id="4ad3e-142">在 .NET Framework 應用程式中，這個元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-142">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="4ad3e-143">針對 ASP.NET 應用程式，可以在 \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet .config 檔案中設定模擬流程 \<Windows Folder> 。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-143">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="4ad3e-144">ASP.NET 預設會使用下列設定來停用 aspnet .config 檔案中的模擬流程：</span><span class="sxs-lookup"><span data-stu-id="4ad3e-144">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="4ad3e-145">在 ASP.NET 中，如果您想要改為允許模擬的流程，則必須明確地使用下列設定：</span><span class="sxs-lookup"><span data-stu-id="4ad3e-145">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="4ad3e-146">範例</span><span class="sxs-lookup"><span data-stu-id="4ad3e-146">Example</span></span>  
 <span data-ttu-id="4ad3e-147">下列範例示範如何指定不會跨非同步點傳送 Windows 識別的舊版行為。</span><span class="sxs-lookup"><span data-stu-id="4ad3e-147">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ad3e-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad3e-148">See also</span></span>

- [<span data-ttu-id="4ad3e-149">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="4ad3e-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4ad3e-150">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="4ad3e-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4ad3e-151">\<alwaysFlowImpersonationPolicy>元素</span><span class="sxs-lookup"><span data-stu-id="4ad3e-151">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
