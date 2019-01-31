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
ms.openlocfilehash: 60c61e5b7c176f88e8f2c2e717e60ae40f43fbf6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255249"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="f87c9-102">\<alwaysFlowImpersonationPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="f87c9-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="f87c9-103">指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="f87c9-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="f87c9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f87c9-104">\<configuration></span></span>  
<span data-ttu-id="f87c9-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="f87c9-105">\<runtime></span></span>  
<span data-ttu-id="f87c9-106">\<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="f87c9-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f87c9-107">語法</span><span class="sxs-lookup"><span data-stu-id="f87c9-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f87c9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f87c9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f87c9-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f87c9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f87c9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f87c9-110">Attributes</span></span>  
  
|<span data-ttu-id="f87c9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f87c9-111">Attribute</span></span>|<span data-ttu-id="f87c9-112">描述</span><span class="sxs-lookup"><span data-stu-id="f87c9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f87c9-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f87c9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f87c9-114">表示 Windows 身分識別是否流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="f87c9-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f87c9-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="f87c9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f87c9-116">值</span><span class="sxs-lookup"><span data-stu-id="f87c9-116">Value</span></span>|<span data-ttu-id="f87c9-117">描述</span><span class="sxs-lookup"><span data-stu-id="f87c9-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f87c9-118">身分識別不會流經非同步點，除非透過執行模擬 Windows 之類的管理方法<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>。</span><span class="sxs-lookup"><span data-stu-id="f87c9-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="f87c9-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="f87c9-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f87c9-120">Windows 識別一律流經非同步點，不論模擬的執行方式。</span><span class="sxs-lookup"><span data-stu-id="f87c9-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f87c9-121">子元素</span><span class="sxs-lookup"><span data-stu-id="f87c9-121">Child Elements</span></span>  
 <span data-ttu-id="f87c9-122">無。</span><span class="sxs-lookup"><span data-stu-id="f87c9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f87c9-123">父項目</span><span class="sxs-lookup"><span data-stu-id="f87c9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f87c9-124">項目</span><span class="sxs-lookup"><span data-stu-id="f87c9-124">Element</span></span>|<span data-ttu-id="f87c9-125">描述</span><span class="sxs-lookup"><span data-stu-id="f87c9-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f87c9-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f87c9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f87c9-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="f87c9-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f87c9-128">備註</span><span class="sxs-lookup"><span data-stu-id="f87c9-128">Remarks</span></span>  
 <span data-ttu-id="f87c9-129">在.NET framework 1.0 和 1.1 版中，Windows 身分識別不會流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="f87c9-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="f87c9-130">在.NET Framework 2.0 版中，沒有<xref:System.Threading.ExecutionContext>物件，包含目前執行中執行緒，資訊流過應用程式定義域中的非同步點。</span><span class="sxs-lookup"><span data-stu-id="f87c9-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="f87c9-131"><xref:System.Security.Principal.WindowsIdentity>也做為一部分流經非同步點中，，模擬已達到使用提供的資訊流程之類的管理方法<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>並不是透過其他方式如平台叫用原生方法。</span><span class="sxs-lookup"><span data-stu-id="f87c9-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="f87c9-132">這個項目用來指定 Windows 身分識別會流經非同步點，無論達成的模擬。</span><span class="sxs-lookup"><span data-stu-id="f87c9-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="f87c9-133">您可以變更此預設行為，另外兩種方式：</span><span class="sxs-lookup"><span data-stu-id="f87c9-133">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="f87c9-134">在每個執行緒為基礎的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f87c9-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="f87c9-135">您可以隱藏個別的執行緒上的流程，藉由修改<xref:System.Threading.ExecutionContext>並<xref:System.Security.SecurityContext>藉由設定<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>， <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>，或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="f87c9-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="f87c9-136">在呼叫 unmanaged 裝載介面載入 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="f87c9-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="f87c9-137">如果 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔） 用來載入 CLR，您可以呼叫中指定特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f87c9-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="f87c9-138">若要啟用相容性模式，整個程序，將`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)至`STARTUP_ALWAYSFLOW_IMPERSONATION`。</span><span class="sxs-lookup"><span data-stu-id="f87c9-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f87c9-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="f87c9-139">Configuration File</span></span>  
 <span data-ttu-id="f87c9-140">在.NET Framework 應用程式中，這個項目只可以用於與應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="f87c9-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="f87c9-141">針對 ASP.NET 應用程式，可以設定模擬流程 aspnet.config 檔案中找到\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。</span><span class="sxs-lookup"><span data-stu-id="f87c9-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="f87c9-142">ASP.NET 預設會使用下列組態設定，停用模擬流程 aspnet.config 檔案：</span><span class="sxs-lookup"><span data-stu-id="f87c9-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="f87c9-143">在 ASP.NET 中，如果您想要允許的模擬流程相反地，您必須明確地使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="f87c9-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="f87c9-144">範例</span><span class="sxs-lookup"><span data-stu-id="f87c9-144">Example</span></span>  
 <span data-ttu-id="f87c9-145">下列範例示範如何指定模擬可透過受管理的方法以外的方式，即使 Windows 身分識別存流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="f87c9-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f87c9-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f87c9-146">See also</span></span>
- [<span data-ttu-id="f87c9-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f87c9-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f87c9-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f87c9-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f87c9-149">\<legacyImpersonationPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="f87c9-149">\<legacyImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
