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
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="81ff8-102">\<alwaysFlowImpersonationPolicy> 項目</span><span class="sxs-lookup"><span data-stu-id="81ff8-102">\<alwaysFlowImpersonationPolicy> Element</span></span>

<span data-ttu-id="81ff8-103">指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="81ff8-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="81ff8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="81ff8-104">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81ff8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="81ff8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="81ff8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="81ff8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81ff8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="81ff8-107">Attributes</span></span>  
  
|<span data-ttu-id="81ff8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="81ff8-108">Attribute</span></span>|<span data-ttu-id="81ff8-109">描述</span><span class="sxs-lookup"><span data-stu-id="81ff8-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="81ff8-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="81ff8-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="81ff8-111">指出 Windows 身分識別是否流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="81ff8-111">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="81ff8-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="81ff8-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="81ff8-113">值</span><span class="sxs-lookup"><span data-stu-id="81ff8-113">Value</span></span>|<span data-ttu-id="81ff8-114">描述</span><span class="sxs-lookup"><span data-stu-id="81ff8-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="81ff8-115">除非透過 managed 方法（例如）執行模擬，否則 Windows 身分識別不會在非同步點之間流動 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="81ff8-115">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="81ff8-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="81ff8-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="81ff8-117">Windows 身分識別一律會流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="81ff8-117">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81ff8-118">子元素</span><span class="sxs-lookup"><span data-stu-id="81ff8-118">Child Elements</span></span>  

 <span data-ttu-id="81ff8-119">無。</span><span class="sxs-lookup"><span data-stu-id="81ff8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81ff8-120">父項目</span><span class="sxs-lookup"><span data-stu-id="81ff8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="81ff8-121">項目</span><span class="sxs-lookup"><span data-stu-id="81ff8-121">Element</span></span>|<span data-ttu-id="81ff8-122">描述</span><span class="sxs-lookup"><span data-stu-id="81ff8-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="81ff8-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="81ff8-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="81ff8-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="81ff8-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81ff8-125">備註</span><span class="sxs-lookup"><span data-stu-id="81ff8-125">Remarks</span></span>  

 <span data-ttu-id="81ff8-126">在 .NET Framework 1.0 和1.1 版中，Windows 身分識別不會在非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="81ff8-126">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="81ff8-127">在 .NET Framework 2.0 版中，有一個 <xref:System.Threading.ExecutionContext> 物件包含目前執行中線程的相關資訊，並在應用程式域內的非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="81ff8-127">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="81ff8-128"><xref:System.Security.Principal.WindowsIdentity>它也會在流經非同步點的資訊中流動，但前提是使用 managed 方法（例如 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> ，而不是透過其他方法（例如平台叫用）來達到模擬。</span><span class="sxs-lookup"><span data-stu-id="81ff8-128">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="81ff8-129">這個元素可用來指定 Windows 身分識別會在非同步點之間流動，而不論模擬的達成方式為何。</span><span class="sxs-lookup"><span data-stu-id="81ff8-129">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="81ff8-130">您可以透過兩種其他方式來改變這個預設行為：</span><span class="sxs-lookup"><span data-stu-id="81ff8-130">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="81ff8-131">在 managed 程式碼中，以每個執行緒為基礎。</span><span class="sxs-lookup"><span data-stu-id="81ff8-131">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="81ff8-132">您可以 <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> 使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> 、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> 或方法修改和設定，以每個執行緒為基礎來隱藏流程 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="81ff8-132">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="81ff8-133">在非受控裝載介面的呼叫中，將 common language runtime 載入 (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="81ff8-133">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="81ff8-134">如果使用非受控裝載介面 (而非簡單的 managed 可執行檔) 用來載入 CLR，您可以在 [CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的呼叫中指定特殊旗標。</span><span class="sxs-lookup"><span data-stu-id="81ff8-134">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="81ff8-135">若要啟用整個進程的相容性模式，請將 `flags` [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的參數設定為 `STARTUP_ALWAYSFLOW_IMPERSONATION` 。</span><span class="sxs-lookup"><span data-stu-id="81ff8-135">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="81ff8-136">組態檔</span><span class="sxs-lookup"><span data-stu-id="81ff8-136">Configuration File</span></span>  

 <span data-ttu-id="81ff8-137">在 .NET Framework 應用程式中，這個元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="81ff8-137">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="81ff8-138">針對 ASP.NET 應用程式，您可以在 \Microsoft.NET\Framework\vx.x.xxxx 目錄中找到的 aspnet.config 檔案中設定模擬流程 \<Windows Folder> 。</span><span class="sxs-lookup"><span data-stu-id="81ff8-138">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="81ff8-139">ASP.NET 預設會使用下列設定來停用 aspnet.config 檔案中的模擬流程：</span><span class="sxs-lookup"><span data-stu-id="81ff8-139">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="81ff8-140">在 ASP.NET 中，如果您想要改為允許模擬的流程，您必須明確地使用下列設定：</span><span class="sxs-lookup"><span data-stu-id="81ff8-140">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="81ff8-141">範例</span><span class="sxs-lookup"><span data-stu-id="81ff8-141">Example</span></span>  

 <span data-ttu-id="81ff8-142">下列範例示範如何指定 Windows 身分識別流經非同步點，即使是透過 managed 方法以外的方式來達成模擬也是一樣。</span><span class="sxs-lookup"><span data-stu-id="81ff8-142">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81ff8-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81ff8-143">See also</span></span>

- [<span data-ttu-id="81ff8-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="81ff8-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="81ff8-145">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="81ff8-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="81ff8-146">\<legacyImpersonationPolicy> 元素</span><span class="sxs-lookup"><span data-stu-id="81ff8-146">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
