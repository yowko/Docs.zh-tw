---
title: '&lt;啟動&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 60699f0335bb35589341558800cfd64503d0aa0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="19b07-102">&lt;啟動&gt;項目</span><span class="sxs-lookup"><span data-stu-id="19b07-102">&lt;startup&gt; Element</span></span>
<span data-ttu-id="19b07-103">指定 common language runtime 啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="19b07-103">Specifies common language runtime startup information.</span></span>  
  
 <span data-ttu-id="19b07-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="19b07-104">\<configuration></span></span>  
<span data-ttu-id="19b07-105">\<啟動 ></span><span class="sxs-lookup"><span data-stu-id="19b07-105">\<startup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b07-106">語法</span><span class="sxs-lookup"><span data-stu-id="19b07-106">Syntax</span></span>  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19b07-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="19b07-107">Attributes and Elements</span></span>  
 <span data-ttu-id="19b07-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="19b07-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19b07-109">屬性</span><span class="sxs-lookup"><span data-stu-id="19b07-109">Attributes</span></span>  
  
|<span data-ttu-id="19b07-110">屬性</span><span class="sxs-lookup"><span data-stu-id="19b07-110">Attribute</span></span>|<span data-ttu-id="19b07-111">描述</span><span class="sxs-lookup"><span data-stu-id="19b07-111">Description</span></span>|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="19b07-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="19b07-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="19b07-113">指定是否要啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]執行階段啟用原則，或使用[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]啟用原則。</span><span class="sxs-lookup"><span data-stu-id="19b07-113">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="19b07-114">useLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="19b07-114">useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
  
|<span data-ttu-id="19b07-115">值</span><span class="sxs-lookup"><span data-stu-id="19b07-115">Value</span></span>|<span data-ttu-id="19b07-116">描述</span><span class="sxs-lookup"><span data-stu-id="19b07-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="19b07-117">啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]所選的執行階段，也就是繫結舊版執行階段啟用技術的執行階段啟用原則 (例如[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) 至執行階段從組態檔，而不是選擇須它們在 CLR 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="19b07-117">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="19b07-118">因此，如果選擇 4 或更新版本的 CLR 版本，則從組態檔，建立與舊版.NET Framework 的混合模式組件會載入與所選的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="19b07-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="19b07-119">將此值設定防止 CLR 1.1 版或 CLR 2.0 版載入到相同的程序，確實停用的同處理序並存的功能。</span><span class="sxs-lookup"><span data-stu-id="19b07-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|  
|`false`|<span data-ttu-id="19b07-120">使用預設的啟用原則的[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本中，也就是允許舊版執行階段啟用技術，載入程序中的 CLR 版本 1.1 或 2.0。</span><span class="sxs-lookup"><span data-stu-id="19b07-120">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="19b07-121">設定此值可防止在載入到.NET Framework 4 或更新版本，除非其建置.NET Framework 4 或更新版本的混合模式組件。</span><span class="sxs-lookup"><span data-stu-id="19b07-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="19b07-122">預設值為這個值。</span><span class="sxs-lookup"><span data-stu-id="19b07-122">This value is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19b07-123">子項目</span><span class="sxs-lookup"><span data-stu-id="19b07-123">Child Elements</span></span>  
  
|<span data-ttu-id="19b07-124">項目</span><span class="sxs-lookup"><span data-stu-id="19b07-124">Element</span></span>|<span data-ttu-id="19b07-125">描述</span><span class="sxs-lookup"><span data-stu-id="19b07-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19b07-126">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="19b07-126">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="19b07-127">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="19b07-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="19b07-128">執行階段版本 1.1 或更新版本建置的應用程式應該使用 **\<supportedRuntime >** 項目。</span><span class="sxs-lookup"><span data-stu-id="19b07-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="19b07-129">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="19b07-129">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="19b07-130">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="19b07-130">Specifies which versions of the common language runtime the application supports.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19b07-131">父項目</span><span class="sxs-lookup"><span data-stu-id="19b07-131">Parent Elements</span></span>  
  
|<span data-ttu-id="19b07-132">項目</span><span class="sxs-lookup"><span data-stu-id="19b07-132">Element</span></span>|<span data-ttu-id="19b07-133">描述</span><span class="sxs-lookup"><span data-stu-id="19b07-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="19b07-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="19b07-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19b07-135">備註</span><span class="sxs-lookup"><span data-stu-id="19b07-135">Remarks</span></span>  
 <span data-ttu-id="19b07-136">**\<SupportedRuntime >** 使用 1.1 版或更新版本的執行階段所建置的所有應用程式應該使用項目。</span><span class="sxs-lookup"><span data-stu-id="19b07-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="19b07-137">只支援 1.0 版的執行階段建置的應用程式必須使用 **\<requiredRuntime >** 項目。</span><span class="sxs-lookup"><span data-stu-id="19b07-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>  
  
 <span data-ttu-id="19b07-138">在 Microsoft Internet Explorer 所裝載的應用程式的啟動程式碼會忽略**\<啟動 >** 項目和其子項目。</span><span class="sxs-lookup"><span data-stu-id="19b07-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="19b07-139">UseLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="19b07-139">The useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
 <span data-ttu-id="19b07-140">這個屬性很有用，如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)，而且希望這些路徑啟用 CLR，而不是較早的版本中，第 4 版或如果您的應用程式使用建置[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]但具有相依性的較舊版本的.NET framework 建置的混合模式組件。</span><span class="sxs-lookup"><span data-stu-id="19b07-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="19b07-141">在這些情況下，將屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="19b07-141">In those scenarios, set the attribute to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19b07-142">將屬性設定為`true`CLR 1.1 版或 CLR 2.0 版可防止載入到相同的程序，確實停用的同處理序並存的功能 (請參閱[-並存執行 COM interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32))。</span><span class="sxs-lookup"><span data-stu-id="19b07-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19b07-143">範例</span><span class="sxs-lookup"><span data-stu-id="19b07-143">Example</span></span>  
 <span data-ttu-id="19b07-144">下列範例顯示如何在組態檔中指定的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="19b07-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19b07-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19b07-145">See Also</span></span>  
 [<span data-ttu-id="19b07-146">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="19b07-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="19b07-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="19b07-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="19b07-148">\<PaveOver> 指定要使用哪一個執行階段版本</span><span class="sxs-lookup"><span data-stu-id="19b07-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [<span data-ttu-id="19b07-149">COM interop-並存執行</span><span class="sxs-lookup"><span data-stu-id="19b07-149">Side-by-Side Execution for COM Interop</span></span>](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [<span data-ttu-id="19b07-150">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="19b07-150">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
