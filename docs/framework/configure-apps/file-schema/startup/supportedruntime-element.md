---
title: '&lt;Supportedruntime>&gt;項目'
ms.date: 04/10/2018
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 3fdc3bae488fe47732fe91cbb2ac23aae3e33b81
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084389"
---
# <a name="ltsupportedruntimegt-element"></a><span data-ttu-id="aa16f-102">&lt;Supportedruntime>&gt;項目</span><span class="sxs-lookup"><span data-stu-id="aa16f-102">&lt;supportedRuntime&gt; Element</span></span>

<span data-ttu-id="aa16f-103">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-103">Specifies which versions of the common language runtime the application supports.</span></span> <span data-ttu-id="aa16f-104">所有以 .NET Framework 1.1 (含) 以後版本建置的應用程式都應使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="aa16f-104">This element should be used by all applications built with version 1.1 or later of the .NET Framework.</span></span>  
  
[<span data-ttu-id="aa16f-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aa16f-105">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
<span data-ttu-id="aa16f-106">&nbsp;&nbsp;[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="aa16f-106">&nbsp;&nbsp;[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)</span></span>  
<span data-ttu-id="aa16f-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**</span><span class="sxs-lookup"><span data-stu-id="aa16f-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa16f-108">語法</span><span class="sxs-lookup"><span data-stu-id="aa16f-108">Syntax</span></span>
  
```xml  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## <a name="attributes"></a><span data-ttu-id="aa16f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="aa16f-109">Attributes</span></span>
  
|<span data-ttu-id="aa16f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="aa16f-110">Attribute</span></span>|<span data-ttu-id="aa16f-111">描述</span><span class="sxs-lookup"><span data-stu-id="aa16f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa16f-112">**version**</span><span class="sxs-lookup"><span data-stu-id="aa16f-112">**version**</span></span>|<span data-ttu-id="aa16f-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="aa16f-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="aa16f-114">字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-114">A string value that specifies the version of the common language runtime (CLR) that this application supports.</span></span> <span data-ttu-id="aa16f-115">有效值`version`屬性，請參閱[「 執行階段版本 」 值](#version)一節。</span><span class="sxs-lookup"><span data-stu-id="aa16f-115">For valid values of the `version` attribute, see the ["runtime version" values](#version) section.</span></span> <span data-ttu-id="aa16f-116">**注意：** 透過.NET Framework 3.5 中，「*執行階段版本*"值的形式*主要*。*次要*。*建置*。</span><span class="sxs-lookup"><span data-stu-id="aa16f-116">**Note:**  Through the .NET Framework 3.5, the "*runtime version*" value takes the form *major*.*minor*.*build*.</span></span> <span data-ttu-id="aa16f-117">從 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，只需要主要和次要版本號碼 (也就是 "v4.0"，不需要 "v4.0.30319")。</span><span class="sxs-lookup"><span data-stu-id="aa16f-117">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], only the major and minor version numbers are required (that is, "v4.0" instead of "v4.0.30319").</span></span> <span data-ttu-id="aa16f-118">建議使用較短的字串。</span><span class="sxs-lookup"><span data-stu-id="aa16f-118">The shorter string is recommended.</span></span>|  
|<span data-ttu-id="aa16f-119">**sku**</span><span class="sxs-lookup"><span data-stu-id="aa16f-119">**sku**</span></span>|<span data-ttu-id="aa16f-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="aa16f-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="aa16f-121">字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-121">A string value that specifies the stock-keeping unit (SKU), which in turn specifies which .NET Framework release this application supports.</span></span><br /><br /> <span data-ttu-id="aa16f-122">從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。</span><span class="sxs-lookup"><span data-stu-id="aa16f-122">Starting with the .NET Framework 4.0, the use of the `sku` attribute is recommended.</span></span>  <span data-ttu-id="aa16f-123">該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-123">When present, it indicates the version of the .NET Framework that the app targets.</span></span><br /><br /> <span data-ttu-id="aa16f-124">如需 sku 屬性的有效值，請參閱[「 sku 識別碼 」 值](#sku)一節。</span><span class="sxs-lookup"><span data-stu-id="aa16f-124">For valid values of the sku attribute, see the ["sku id" values](#sku) section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa16f-125">備註</span><span class="sxs-lookup"><span data-stu-id="aa16f-125">Remarks</span></span>

<span data-ttu-id="aa16f-126">如果 **\<Supportedruntime> >** 項目不存在於應用程式組態檔，會使用用來建置應用程式的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-126">If the **\<supportedRuntime>** element is not present in the application configuration file, the version of the runtime used to build the application is used.</span></span>  

<span data-ttu-id="aa16f-127"> *\*\<Supportedruntime> >** 項目應由使用 1.1 版或更新版本的執行階段所建置的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="aa16f-127">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="aa16f-128">若要只支援 1.0 版的執行階段所建置的應用程式必須使用[ \<Requiredruntime> >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="aa16f-128">Applications built to support only version 1.0 of the runtime must use the [\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa16f-129">如果您使用[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定組態檔，您必須使用`<requiredRuntime>`的執行階段的所有版本的項目。</span><span class="sxs-lookup"><span data-stu-id="aa16f-129">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="aa16f-130">`<supportedRuntime>`當您使用時，便會忽略元素[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)。</span><span class="sxs-lookup"><span data-stu-id="aa16f-130">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
<span data-ttu-id="aa16f-131">針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-131">For apps that support versions of the runtime from the .NET Framework 1.1 through 3.5, when multiple versions of the runtime are supported, the first element should specify the most preferred version of the runtime, and the last element should specify the least preferred version.</span></span> <span data-ttu-id="aa16f-132">針對支援 .NET Framework 4.0 或更新版本的應用程式，`version` 屬性會指出 CLR 版本，其對 .NET Framework 4 與更新版本而言為常用項目，而 `sku` 屬性會指出應用程式用以作為目標的單一 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-132">For apps that support the .NET Framework 4.0 or later versions, the `version` attribute indicates the CLR version, which is common to the .NET Framework 4 and later versions, and the `sku` attribute indicates single .NET Framework version that the app targets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa16f-133">如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)，和您想要這些路徑來啟動第 4 版的 clr，而不是較早的版本，或如果您的應用程式以建置[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]具有相依性，但以舊版.NET Framework 建置的混合模式組件，它並不足以指定[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]中支援的執行階段的清單。</span><span class="sxs-lookup"><span data-stu-id="aa16f-133">If your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework, it is not sufficient to specify the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the list of supported runtimes.</span></span> <span data-ttu-id="aa16f-134">此外，在[\<啟動 > 項目](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)在您的組態檔，您必須設定`useLegacyV2RuntimeActivationPolicy`屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="aa16f-134">In addition, in the [\<startup> element](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in your configuration file, you must set the `useLegacyV2RuntimeActivationPolicy` attribute to `true`.</span></span> <span data-ttu-id="aa16f-135">但是，將這個屬性設定為 `true`，即表示以舊版 .NET Framework 建置的所有元件都會使用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 執行，而不是原本建置時所使用的執行階段。</span><span class="sxs-lookup"><span data-stu-id="aa16f-135">However, setting this attribute to `true` means that all components built with earlier versions of the .NET Framework are run using the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] instead of the runtimes they were built with.</span></span>  
  
<span data-ttu-id="aa16f-136">建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。</span><span class="sxs-lookup"><span data-stu-id="aa16f-136">We recommend that you test applications with all the .NET Framework versions that they can run on.</span></span>  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a><span data-ttu-id="aa16f-137">「執行階段版本」值</span><span class="sxs-lookup"><span data-stu-id="aa16f-137">"runtime version" values</span></span>  
<span data-ttu-id="aa16f-138">`runtime`屬性會指定給定的應用程式需要的 Common Language Runtime (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-138">The `runtime` attribute specifies the Common Language Runtime (CLR) version that is required for a given application.</span></span> <span data-ttu-id="aa16f-139">請注意，所有的.NET Framework v4.x 版本指定`v4.0`CLR。</span><span class="sxs-lookup"><span data-stu-id="aa16f-139">Note that all .NET Framework v4.x versions specify the `v4.0` CLR.</span></span> <span data-ttu-id="aa16f-140">下表列出的有效值*執行階段版本*的值`version`屬性。</span><span class="sxs-lookup"><span data-stu-id="aa16f-140">The following table lists valid values for the *runtime version* value of the `version` attribute.</span></span>  

|<span data-ttu-id="aa16f-141">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="aa16f-141">.NET Framework version</span></span>|<span data-ttu-id="aa16f-142">`version` 屬性</span><span class="sxs-lookup"><span data-stu-id="aa16f-142">`version` attribute</span></span>|  
|----------------------------|-------------------------|  
|<span data-ttu-id="aa16f-143">1.0</span><span class="sxs-lookup"><span data-stu-id="aa16f-143">1.0</span></span>|<span data-ttu-id="aa16f-144">"v1.0.3705"</span><span class="sxs-lookup"><span data-stu-id="aa16f-144">"v1.0.3705"</span></span>|  
|<span data-ttu-id="aa16f-145">1.1</span><span class="sxs-lookup"><span data-stu-id="aa16f-145">1.1</span></span>|<span data-ttu-id="aa16f-146">"v1.1.4322"</span><span class="sxs-lookup"><span data-stu-id="aa16f-146">"v1.1.4322"</span></span>|  
|<span data-ttu-id="aa16f-147">2.0</span><span class="sxs-lookup"><span data-stu-id="aa16f-147">2.0</span></span>|<span data-ttu-id="aa16f-148">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="aa16f-148">"v2.0.50727"</span></span>|  
|<span data-ttu-id="aa16f-149">3.0</span><span class="sxs-lookup"><span data-stu-id="aa16f-149">3.0</span></span>|<span data-ttu-id="aa16f-150">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="aa16f-150">"v2.0.50727"</span></span>|  
|<span data-ttu-id="aa16f-151">3.5</span><span class="sxs-lookup"><span data-stu-id="aa16f-151">3.5</span></span>|<span data-ttu-id="aa16f-152">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="aa16f-152">"v2.0.50727"</span></span>|  
|<span data-ttu-id="aa16f-153">4.0-4.7.2</span><span class="sxs-lookup"><span data-stu-id="aa16f-153">4.0-4.7.2</span></span>|<span data-ttu-id="aa16f-154">"v4.0"</span><span class="sxs-lookup"><span data-stu-id="aa16f-154">"v4.0"</span></span>|  

<a name="sku"></a>   
## <a name="sku-id-values"></a><span data-ttu-id="aa16f-155">「SKU 識別碼」值</span><span class="sxs-lookup"><span data-stu-id="aa16f-155">"sku id" values</span></span>

<span data-ttu-id="aa16f-156">`sku`屬性會使用目標 framework moniker (TFM)，以指出應用程式為目標，且要求要執行的.NET framework 版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-156">The `sku` attribute uses a target framework moniker (TFM) to indicate the version of the .NET Framework that the app targets and requires to run.</span></span> <span data-ttu-id="aa16f-157">下表列出支援的有效值`sku`屬性，從.NET Framework 4 開始。</span><span class="sxs-lookup"><span data-stu-id="aa16f-157">The following table lists valid values that are supported by the `sku` attribute, starting with the .NET Framework 4.</span></span>
  
|<span data-ttu-id="aa16f-158">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="aa16f-158">.NET Framework version</span></span>|<span data-ttu-id="aa16f-159">`sku` 屬性</span><span class="sxs-lookup"><span data-stu-id="aa16f-159">`sku` attribute</span></span>|  
|----------------------------|---------------------|  
|<span data-ttu-id="aa16f-160">4.0</span><span class="sxs-lookup"><span data-stu-id="aa16f-160">4.0</span></span>|<span data-ttu-id="aa16f-161">".NETFramework,Version=v4.0"</span><span class="sxs-lookup"><span data-stu-id="aa16f-161">".NETFramework,Version=v4.0"</span></span>|  
|<span data-ttu-id="aa16f-162">4.0，Client Profile</span><span class="sxs-lookup"><span data-stu-id="aa16f-162">4.0, Client Profile</span></span>|<span data-ttu-id="aa16f-163">".NETFramework,Version=v4.0,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="aa16f-163">".NETFramework,Version=v4.0,Profile=Client"</span></span>|  
|<span data-ttu-id="aa16f-164">4.0，平台更新 1</span><span class="sxs-lookup"><span data-stu-id="aa16f-164">4.0, platform update 1</span></span>|<span data-ttu-id="aa16f-165">".NETFramework,Version=v4.0.1"</span><span class="sxs-lookup"><span data-stu-id="aa16f-165">".NETFramework,Version=v4.0.1"</span></span>|  
|<span data-ttu-id="aa16f-166">4.0，Client Profile，更新 1</span><span class="sxs-lookup"><span data-stu-id="aa16f-166">4.0, Client Profile, update 1</span></span>|<span data-ttu-id="aa16f-167">".NETFramework,Version=v4.0.1,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="aa16f-167">".NETFramework,Version=v4.0.1,Profile=Client"</span></span>|  
|<span data-ttu-id="aa16f-168">4.0，平台更新 2</span><span class="sxs-lookup"><span data-stu-id="aa16f-168">4.0, platform update 2</span></span>|<span data-ttu-id="aa16f-169">".NETFramework,Version=v4.0.2"</span><span class="sxs-lookup"><span data-stu-id="aa16f-169">".NETFramework,Version=v4.0.2"</span></span>|  
|<span data-ttu-id="aa16f-170">4.0，Client Profile，更新 2</span><span class="sxs-lookup"><span data-stu-id="aa16f-170">4.0, Client Profile, update 2</span></span>|<span data-ttu-id="aa16f-171">".NETFramework,Version=v4.0.2,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="aa16f-171">".NETFramework,Version=v4.0.2,Profile=Client"</span></span>|  
|<span data-ttu-id="aa16f-172">4.0，平台更新 3</span><span class="sxs-lookup"><span data-stu-id="aa16f-172">4.0, platform update 3</span></span>|<span data-ttu-id="aa16f-173">".NETFramework,Version=v4.0.3"</span><span class="sxs-lookup"><span data-stu-id="aa16f-173">".NETFramework,Version=v4.0.3"</span></span>|  
|<span data-ttu-id="aa16f-174">4.0，Client Profile，更新 3</span><span class="sxs-lookup"><span data-stu-id="aa16f-174">4.0, Client Profile, update 3</span></span>|<span data-ttu-id="aa16f-175">".NETFramework,Version=v4.0.3,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="aa16f-175">".NETFramework,Version=v4.0.3,Profile=Client"</span></span>|  
|<span data-ttu-id="aa16f-176">4.5</span><span class="sxs-lookup"><span data-stu-id="aa16f-176">4.5</span></span>|<span data-ttu-id="aa16f-177">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="aa16f-177">".NETFramework,Version=v4.5"</span></span>|  
|<span data-ttu-id="aa16f-178">4.5.1</span><span class="sxs-lookup"><span data-stu-id="aa16f-178">4.5.1</span></span>|<span data-ttu-id="aa16f-179">".NETFramework,Version=v4.5.1"</span><span class="sxs-lookup"><span data-stu-id="aa16f-179">".NETFramework,Version=v4.5.1"</span></span>|  
|<span data-ttu-id="aa16f-180">4.5.2</span><span class="sxs-lookup"><span data-stu-id="aa16f-180">4.5.2</span></span>|<span data-ttu-id="aa16f-181">".NETFramework,Version=v4.5.2"</span><span class="sxs-lookup"><span data-stu-id="aa16f-181">".NETFramework,Version=v4.5.2"</span></span>|  
|<span data-ttu-id="aa16f-182">4.6</span><span class="sxs-lookup"><span data-stu-id="aa16f-182">4.6</span></span>|<span data-ttu-id="aa16f-183">".NETFramework,Version=v4.6"</span><span class="sxs-lookup"><span data-stu-id="aa16f-183">".NETFramework,Version=v4.6"</span></span>|  
|<span data-ttu-id="aa16f-184">4.6.1</span><span class="sxs-lookup"><span data-stu-id="aa16f-184">4.6.1</span></span>|<span data-ttu-id="aa16f-185">".NETFramework,Version=v4.6.1"</span><span class="sxs-lookup"><span data-stu-id="aa16f-185">".NETFramework,Version=v4.6.1"</span></span>|  
|<span data-ttu-id="aa16f-186">4.6.2</span><span class="sxs-lookup"><span data-stu-id="aa16f-186">4.6.2</span></span>|<span data-ttu-id="aa16f-187">".NETFramework,Version=v4.6.2"</span><span class="sxs-lookup"><span data-stu-id="aa16f-187">".NETFramework,Version=v4.6.2"</span></span>|  
|<span data-ttu-id="aa16f-188">4.7</span><span class="sxs-lookup"><span data-stu-id="aa16f-188">4.7</span></span>|<span data-ttu-id="aa16f-189">".NETFramework,Version=v4.7"</span><span class="sxs-lookup"><span data-stu-id="aa16f-189">".NETFramework,Version=v4.7"</span></span>|
|<span data-ttu-id="aa16f-190">4.7.1</span><span class="sxs-lookup"><span data-stu-id="aa16f-190">4.7.1</span></span>|<span data-ttu-id="aa16f-191">".NETFramework,Version=v4.7.1"</span><span class="sxs-lookup"><span data-stu-id="aa16f-191">".NETFramework,Version=v4.7.1"</span></span>|
|<span data-ttu-id="aa16f-192">4.7.2</span><span class="sxs-lookup"><span data-stu-id="aa16f-192">4.7.2</span></span>|<span data-ttu-id="aa16f-193">".NETFramework，版本 = v4.7.2"</span><span class="sxs-lookup"><span data-stu-id="aa16f-193">".NETFramework,Version=v4.7.2"</span></span>|

## <a name="example"></a><span data-ttu-id="aa16f-194">範例</span><span class="sxs-lookup"><span data-stu-id="aa16f-194">Example</span></span>  
 <span data-ttu-id="aa16f-195">下列範例將示範如何在設定檔中指定支援的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="aa16f-195">The following example shows how to specify the supported runtime version in a configuration file.</span></span> <span data-ttu-id="aa16f-196">組態檔會指出應用程式的目標.NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="aa16f-196">The configuration file indicates that the app targets the .NET Framework 4.7.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />  
   </startup>  
</configuration>  
```  
  
## <a name="configuration-file"></a><span data-ttu-id="aa16f-197">組態檔</span><span class="sxs-lookup"><span data-stu-id="aa16f-197">Configuration file</span></span>

<span data-ttu-id="aa16f-198">這個項目可以在應用程式組態檔中使用。</span><span class="sxs-lookup"><span data-stu-id="aa16f-198">This element can be used in the application configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa16f-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa16f-199">See also</span></span>

- [<span data-ttu-id="aa16f-200">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="aa16f-200">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)
- [<span data-ttu-id="aa16f-201">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="aa16f-201">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="aa16f-202">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="aa16f-202">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
