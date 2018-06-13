---
title: '&lt;alwaysFlowImpersonationPolicy&gt;項目'
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
ms.openlocfilehash: 5cc704bbf8631936dbbeb3539ea5ed0d8499f378
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752269"
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a><span data-ttu-id="a296c-102">&lt;alwaysFlowImpersonationPolicy&gt;項目</span><span class="sxs-lookup"><span data-stu-id="a296c-102">&lt;alwaysFlowImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="a296c-103">指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="a296c-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="a296c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a296c-104">\<configuration></span></span>  
<span data-ttu-id="a296c-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="a296c-105">\<runtime></span></span>  
<span data-ttu-id="a296c-106">\<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="a296c-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a296c-107">語法</span><span class="sxs-lookup"><span data-stu-id="a296c-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a296c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a296c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a296c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a296c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a296c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a296c-110">Attributes</span></span>  
  
|<span data-ttu-id="a296c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a296c-111">Attribute</span></span>|<span data-ttu-id="a296c-112">描述</span><span class="sxs-lookup"><span data-stu-id="a296c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a296c-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a296c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a296c-114">指出是否 Windows 身分識別流動到非同步的點。</span><span class="sxs-lookup"><span data-stu-id="a296c-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a296c-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="a296c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a296c-116">值</span><span class="sxs-lookup"><span data-stu-id="a296c-116">Value</span></span>|<span data-ttu-id="a296c-117">描述</span><span class="sxs-lookup"><span data-stu-id="a296c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a296c-118">身分識別不會流動到非同步的點，除非透過執行模擬的 Windows managed 方法例如<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>。</span><span class="sxs-lookup"><span data-stu-id="a296c-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="a296c-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a296c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a296c-120">Windows 識別一律流動到非同步的點，無論模擬執行的方式。</span><span class="sxs-lookup"><span data-stu-id="a296c-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a296c-121">子項目</span><span class="sxs-lookup"><span data-stu-id="a296c-121">Child Elements</span></span>  
 <span data-ttu-id="a296c-122">無。</span><span class="sxs-lookup"><span data-stu-id="a296c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a296c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a296c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a296c-124">項目</span><span class="sxs-lookup"><span data-stu-id="a296c-124">Element</span></span>|<span data-ttu-id="a296c-125">描述</span><span class="sxs-lookup"><span data-stu-id="a296c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a296c-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a296c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a296c-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a296c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a296c-128">備註</span><span class="sxs-lookup"><span data-stu-id="a296c-128">Remarks</span></span>  
 <span data-ttu-id="a296c-129">在.NET framework 1.0 和 1.1 版中，Windows 身分識別不會流動到非同步的點。</span><span class="sxs-lookup"><span data-stu-id="a296c-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="a296c-130">在.NET Framework 2.0 版中，沒有<xref:System.Threading.ExecutionContext>物件，包含目前執行的執行緒的相關資訊，並傳送到非同步應用程式定義域中的點。</span><span class="sxs-lookup"><span data-stu-id="a296c-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="a296c-131"><xref:System.Security.Principal.WindowsIdentity>也流程一部分的資訊提供使用達成模擬流動到非同步的點，管理方法例如<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>並不能透過其他方式如平台叫用原生方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="a296c-132">這個項目用來指定 Windows 身分識別沒有流經非同步的點，無論模擬所達成的效果。</span><span class="sxs-lookup"><span data-stu-id="a296c-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="a296c-133">您可以變更此預設行為，另外兩種方式：</span><span class="sxs-lookup"><span data-stu-id="a296c-133">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="a296c-134">在每個執行緒為基礎的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a296c-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="a296c-135">您可以藉由修改隱藏每個執行緒為基礎的流程<xref:System.Threading.ExecutionContext>和<xref:System.Security.SecurityContext>設定使用<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>， <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>，或<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="a296c-136">在載入 common language runtime (CLR) 的 unmanaged 裝載介面的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a296c-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="a296c-137">如果載入 CLR 用於 unmanaged 裝載介面 （而不是簡單的 managed 可執行檔），您可以呼叫中指定的特殊旗標[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="a296c-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="a296c-138">若要啟用的整個程序的相容性模式，`flags`參數[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)至`STARTUP_ALWAYSFLOW_IMPERSONATION`。</span><span class="sxs-lookup"><span data-stu-id="a296c-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a296c-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="a296c-139">Configuration File</span></span>  
 <span data-ttu-id="a296c-140">在.NET Framework 應用程式中，此項目只可以用於與應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="a296c-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="a296c-141">可以位於 aspnet.config 檔案中設定 ASP.NET 應用程式，模擬流程\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄。</span><span class="sxs-lookup"><span data-stu-id="a296c-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="a296c-142">預設的 ASP.NET 中，會停用模擬流程 aspnet.config 檔案中的使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="a296c-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="a296c-143">在 ASP.NET 中，如果您想要允許的模擬流程相反地，您必須明確地使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="a296c-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="a296c-144">範例</span><span class="sxs-lookup"><span data-stu-id="a296c-144">Example</span></span>  
 <span data-ttu-id="a296c-145">下列範例會示範如何指定 Windows 身分識別流動到非同步的點，即使模擬透過 managed 方法以外的方式來達成。</span><span class="sxs-lookup"><span data-stu-id="a296c-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a296c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a296c-146">See Also</span></span>  
 [<span data-ttu-id="a296c-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a296c-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a296c-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a296c-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a296c-149">\<legacyImpersonationPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="a296c-149">\<legacyImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
