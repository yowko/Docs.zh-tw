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
ms.openlocfilehash: cd09598800b74c4807163bc921806f5b470e0d24
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252503"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="5006f-102">\<legacyImpersonationPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="5006f-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="5006f-103">指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="5006f-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="5006f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5006f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5006f-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5006f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5006f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="5006f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5006f-107">語法</span><span class="sxs-lookup"><span data-stu-id="5006f-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5006f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5006f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5006f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5006f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5006f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5006f-110">Attributes</span></span>  
  
|<span data-ttu-id="5006f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5006f-111">Attribute</span></span>|<span data-ttu-id="5006f-112">描述</span><span class="sxs-lookup"><span data-stu-id="5006f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5006f-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5006f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5006f-114">指定不流經非同步點，而不論目前線程上的<xref:System.Threading.ExecutionContext>流程設定為何。<xref:System.Security.Principal.WindowsIdentity></span><span class="sxs-lookup"><span data-stu-id="5006f-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5006f-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="5006f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5006f-116">值</span><span class="sxs-lookup"><span data-stu-id="5006f-116">Value</span></span>|<span data-ttu-id="5006f-117">說明</span><span class="sxs-lookup"><span data-stu-id="5006f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5006f-118"><xref:System.Security.Principal.WindowsIdentity>根據目前線程的流程設定， <xref:System.Threading.ExecutionContext>在非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="5006f-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="5006f-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5006f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5006f-120"><xref:System.Security.Principal.WindowsIdentity>不會流經非同步點，而不論<xref:System.Threading.ExecutionContext>目前線程上的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="5006f-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5006f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="5006f-121">Child Elements</span></span>  
 <span data-ttu-id="5006f-122">無。</span><span class="sxs-lookup"><span data-stu-id="5006f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5006f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="5006f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5006f-124">項目</span><span class="sxs-lookup"><span data-stu-id="5006f-124">Element</span></span>|<span data-ttu-id="5006f-125">說明</span><span class="sxs-lookup"><span data-stu-id="5006f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5006f-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5006f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5006f-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="5006f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5006f-128">備註</span><span class="sxs-lookup"><span data-stu-id="5006f-128">Remarks</span></span>  
 <span data-ttu-id="5006f-129">在 .NET Framework 版本1.0 和1.1 中，不<xref:System.Security.Principal.WindowsIdentity>會流經任何使用者定義的非同步點。</span><span class="sxs-lookup"><span data-stu-id="5006f-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="5006f-130">從 .NET Framework 版本2.0 開始，有一個<xref:System.Threading.ExecutionContext>物件包含目前執行中線程的相關資訊，而且它會在應用程式域內的非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="5006f-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="5006f-131"><xref:System.Security.Principal.WindowsIdentity>會包含在這個執行內容中，因此也會流經非同步點，這表示如果模擬內容存在，它也會流動。</span><span class="sxs-lookup"><span data-stu-id="5006f-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="5006f-132">從 .NET Framework 2.0 開始，您可以使用`<legacyImpersonationPolicy>`元素來<xref:System.Security.Principal.WindowsIdentity>指定不流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="5006f-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5006f-133">通用語言執行平臺（CLR）會感知僅使用 managed 程式碼執行的模擬作業，而不是在 managed 程式碼外部執行的模擬，例如透過平台叫用來進行非受控程式碼，或透過直接呼叫 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="5006f-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="5006f-134">除非專案<xref:System.Security.Principal.WindowsIdentity>已設定為 true （`<alwaysFlowImpersonationPolicy enabled="true"/>`），否則只有managed物件可以流經非同步點。`alwaysFlowImpersonationPolicy`</span><span class="sxs-lookup"><span data-stu-id="5006f-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="5006f-135">`alwaysFlowImpersonationPolicy`將專案設定為 true，會指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="5006f-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="5006f-136">如需有關跨非同步點流動非受控模擬的詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy > 元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="5006f-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="5006f-137">您可以透過兩種其他方式來改變此預設行為：</span><span class="sxs-lookup"><span data-stu-id="5006f-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="5006f-138">在 managed 程式碼中，以每個執行緒為基礎。</span><span class="sxs-lookup"><span data-stu-id="5006f-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="5006f-139"><xref:System.Threading.ExecutionContext>您可以使用、或<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>方法來修改和<xref:System.Security.SecurityContext>設定，以隱藏每個執行緒的流程。 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5006f-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="5006f-140">在非受控裝載介面的呼叫中，載入 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="5006f-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="5006f-141">如果使用非受控裝載介面（而不是簡單的 managed 可執行檔）來載入 CLR，您可以在呼叫[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式中指定特殊旗標。</span><span class="sxs-lookup"><span data-stu-id="5006f-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="5006f-142">若要啟用整個進程的相容性模式，請將`flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式的參數設定為 STARTUP_LEGACY_IMPERSONATION。</span><span class="sxs-lookup"><span data-stu-id="5006f-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="5006f-143">如需詳細資訊，請參閱[ \<alwaysFlowImpersonationPolicy > 元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="5006f-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5006f-144">組態檔</span><span class="sxs-lookup"><span data-stu-id="5006f-144">Configuration File</span></span>  
 <span data-ttu-id="5006f-145">在 .NET Framework 應用程式中，這個元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="5006f-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="5006f-146">針對 ASP.NET 應用程式，可以在\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet .config 檔案中設定模擬流程。</span><span class="sxs-lookup"><span data-stu-id="5006f-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="5006f-147">ASP.NET 預設會使用下列設定來停用 aspnet .config 檔案中的模擬流程：</span><span class="sxs-lookup"><span data-stu-id="5006f-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="5006f-148">在 ASP.NET 中，如果您想要改為允許模擬的流程，則必須明確地使用下列設定：</span><span class="sxs-lookup"><span data-stu-id="5006f-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="5006f-149">範例</span><span class="sxs-lookup"><span data-stu-id="5006f-149">Example</span></span>  
 <span data-ttu-id="5006f-150">下列範例示範如何指定不會跨非同步點傳送 Windows 識別的舊版行為。</span><span class="sxs-lookup"><span data-stu-id="5006f-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5006f-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5006f-151">See also</span></span>

- [<span data-ttu-id="5006f-152">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5006f-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5006f-153">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5006f-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5006f-154">\<alwaysFlowImpersonationPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="5006f-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
