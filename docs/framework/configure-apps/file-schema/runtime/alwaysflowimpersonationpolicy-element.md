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
ms.openlocfilehash: 164492eb1abc7329481f158963118b47d2c4aebc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252867"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="eecb2-102">\<alwaysFlowImpersonationPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="eecb2-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="eecb2-103">指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="eecb2-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="eecb2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eecb2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eecb2-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="eecb2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="eecb2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<alwaysFlowImpersonationPolicy>** </span><span class="sxs-lookup"><span data-stu-id="eecb2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="eecb2-107">語法</span><span class="sxs-lookup"><span data-stu-id="eecb2-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eecb2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eecb2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eecb2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="eecb2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eecb2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="eecb2-110">Attributes</span></span>  
  
|<span data-ttu-id="eecb2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="eecb2-111">Attribute</span></span>|<span data-ttu-id="eecb2-112">說明</span><span class="sxs-lookup"><span data-stu-id="eecb2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="eecb2-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="eecb2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="eecb2-114">指出 Windows 身分識別是否流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="eecb2-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="eecb2-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="eecb2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="eecb2-116">值</span><span class="sxs-lookup"><span data-stu-id="eecb2-116">Value</span></span>|<span data-ttu-id="eecb2-117">說明</span><span class="sxs-lookup"><span data-stu-id="eecb2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="eecb2-118">Windows 識別不會流經非同步點, 除非模擬是透過 managed 方法 (例如) <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>來執行。</span><span class="sxs-lookup"><span data-stu-id="eecb2-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="eecb2-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="eecb2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="eecb2-120">無論模擬的執行方式為何, Windows 身分識別一律會流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="eecb2-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eecb2-121">子元素</span><span class="sxs-lookup"><span data-stu-id="eecb2-121">Child Elements</span></span>  
 <span data-ttu-id="eecb2-122">無。</span><span class="sxs-lookup"><span data-stu-id="eecb2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eecb2-123">父項目</span><span class="sxs-lookup"><span data-stu-id="eecb2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eecb2-124">項目</span><span class="sxs-lookup"><span data-stu-id="eecb2-124">Element</span></span>|<span data-ttu-id="eecb2-125">說明</span><span class="sxs-lookup"><span data-stu-id="eecb2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eecb2-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="eecb2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="eecb2-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="eecb2-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eecb2-128">備註</span><span class="sxs-lookup"><span data-stu-id="eecb2-128">Remarks</span></span>  
 <span data-ttu-id="eecb2-129">在 .NET Framework 版本1.0 和1.1 中, Windows 識別不會流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="eecb2-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="eecb2-130">在 .NET Framework 版本2.0 中, 有一個<xref:System.Threading.ExecutionContext>物件包含目前執行中線程的相關資訊, 並會在應用程式域內的非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="eecb2-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="eecb2-131">也會在流經非同步點的資訊中流動, 但前提是使用 managed 方法 (例如) <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>來達成模擬, 而不是透過其他方式 (例如平台叫用) 來達成。 <xref:System.Security.Principal.WindowsIdentity></span><span class="sxs-lookup"><span data-stu-id="eecb2-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="eecb2-132">此元素可用來指定 Windows 識別會在非同步點之間流動, 不論模擬的達成方式為何。</span><span class="sxs-lookup"><span data-stu-id="eecb2-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="eecb2-133">您可以透過兩種其他方式來改變此預設行為:</span><span class="sxs-lookup"><span data-stu-id="eecb2-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="eecb2-134">在 managed 程式碼中, 以每個執行緒為基礎。</span><span class="sxs-lookup"><span data-stu-id="eecb2-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="eecb2-135"><xref:System.Threading.ExecutionContext>您可以使用、或<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>方法來修改和<xref:System.Security.SecurityContext>設定, 以隱藏每個執行緒的流程。 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="eecb2-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="eecb2-136">在非受控裝載介面的呼叫中, 載入 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="eecb2-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="eecb2-137">如果使用非受控裝載介面 (而不是簡單的 managed 可執行檔) 來載入 CLR, 您可以在呼叫[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式中指定特殊旗標。</span><span class="sxs-lookup"><span data-stu-id="eecb2-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="eecb2-138">若要啟用整個進程的相容性模式, 請將`flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式的參數`STARTUP_ALWAYSFLOW_IMPERSONATION`設定為。</span><span class="sxs-lookup"><span data-stu-id="eecb2-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="eecb2-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="eecb2-139">Configuration File</span></span>  
 <span data-ttu-id="eecb2-140">在 .NET Framework 應用程式中, 這個元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="eecb2-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="eecb2-141">針對 ASP.NET 應用程式, 可以在\<Windows 資料夾 > \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet .config 檔案中設定模擬流程。</span><span class="sxs-lookup"><span data-stu-id="eecb2-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="eecb2-142">ASP.NET 預設會使用下列設定來停用 aspnet .config 檔案中的模擬流程:</span><span class="sxs-lookup"><span data-stu-id="eecb2-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="eecb2-143">在 ASP.NET 中, 如果您想要改為允許模擬的流程, 則必須明確地使用下列設定:</span><span class="sxs-lookup"><span data-stu-id="eecb2-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="eecb2-144">範例</span><span class="sxs-lookup"><span data-stu-id="eecb2-144">Example</span></span>  
 <span data-ttu-id="eecb2-145">下列範例示範如何指定 Windows 身分識別流經非同步點, 即使透過 managed 方法以外的方式來達成模擬也是一樣。</span><span class="sxs-lookup"><span data-stu-id="eecb2-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eecb2-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eecb2-146">See also</span></span>

- [<span data-ttu-id="eecb2-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="eecb2-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eecb2-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="eecb2-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="eecb2-149">\<legacyImpersonationPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="eecb2-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
