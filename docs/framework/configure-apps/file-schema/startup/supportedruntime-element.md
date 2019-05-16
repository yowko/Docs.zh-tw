---
title: <supportedRuntime> 組態項目-.NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: cc55809ecaffa4cab4fa4336f9f7f5c06debde2d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634208"
---
# <a name="supportedruntime-element"></a><span data-ttu-id="3231a-102">\<Supportedruntime> > 項目</span><span class="sxs-lookup"><span data-stu-id="3231a-102">\<supportedRuntime> element</span></span>

<span data-ttu-id="3231a-103">指定哪個 common language runtime 版本，並選擇性地應用程式的.NET Framework 版本支援。</span><span class="sxs-lookup"><span data-stu-id="3231a-103">Specifies which common language runtime version and, optionally, .NET Framework version the application supports.</span></span>  

[<span data-ttu-id="3231a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3231a-104">\<configuration></span></span>](../configuration-element.md)  
<span data-ttu-id="3231a-105">&nbsp;&nbsp;[\<startup>](../startup/startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="3231a-105">&nbsp;&nbsp;[\<startup>](../startup/startup-element.md)</span></span>  
<span data-ttu-id="3231a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**</span><span class="sxs-lookup"><span data-stu-id="3231a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="3231a-107">語法</span><span class="sxs-lookup"><span data-stu-id="3231a-107">Syntax</span></span>

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a><span data-ttu-id="3231a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3231a-108">Attributes</span></span>

|<span data-ttu-id="3231a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3231a-109">Attribute</span></span>|<span data-ttu-id="3231a-110">描述</span><span class="sxs-lookup"><span data-stu-id="3231a-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3231a-111">**version**</span><span class="sxs-lookup"><span data-stu-id="3231a-111">**version**</span></span>|<span data-ttu-id="3231a-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3231a-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3231a-113">字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-113">A string value that specifies the version of the common language runtime (CLR) that this application supports.</span></span> <span data-ttu-id="3231a-114">有效值`version`屬性，請參閱[「 執行階段版本 」 值](#version)一節。</span><span class="sxs-lookup"><span data-stu-id="3231a-114">For valid values of the `version` attribute, see the ["runtime version" values](#version) section.</span></span> <span data-ttu-id="3231a-115">**注意：** 透過.NET Framework 3.5 中，「*執行階段版本*"值的形式*主要*。*次要*。*建置*。</span><span class="sxs-lookup"><span data-stu-id="3231a-115">**Note:**  Through the .NET Framework 3.5, the "*runtime version*" value takes the form *major*.*minor*.*build*.</span></span> <span data-ttu-id="3231a-116">從 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，只需要主要和次要版本號碼 (也就是 "v4.0"，不需要 "v4.0.30319")。</span><span class="sxs-lookup"><span data-stu-id="3231a-116">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], only the major and minor version numbers are required (that is, "v4.0" instead of "v4.0.30319").</span></span> <span data-ttu-id="3231a-117">建議使用較短的字串。</span><span class="sxs-lookup"><span data-stu-id="3231a-117">The shorter string is recommended.</span></span>|
|<span data-ttu-id="3231a-118">**sku**</span><span class="sxs-lookup"><span data-stu-id="3231a-118">**sku**</span></span>|<span data-ttu-id="3231a-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3231a-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3231a-120">字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-120">A string value that specifies the stock-keeping unit (SKU), which in turn specifies which .NET Framework release this application supports.</span></span><br /><br /> <span data-ttu-id="3231a-121">從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3231a-121">Starting with the .NET Framework 4.0, the use of the `sku` attribute is recommended.</span></span>  <span data-ttu-id="3231a-122">該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-122">When present, it indicates the version of the .NET Framework that the app targets.</span></span><br /><br /> <span data-ttu-id="3231a-123">如需 sku 屬性的有效值，請參閱[「 sku 識別碼 」 值](#sku)一節。</span><span class="sxs-lookup"><span data-stu-id="3231a-123">For valid values of the sku attribute, see the ["sku id" values](#sku) section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3231a-124">備註</span><span class="sxs-lookup"><span data-stu-id="3231a-124">Remarks</span></span>

<span data-ttu-id="3231a-125">如果 **\<Supportedruntime> >** 項目不存在於應用程式組態檔，會使用用來建置應用程式的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-125">If the **\<supportedRuntime>** element is not present in the application configuration file, the version of the runtime used to build the application is used.</span></span>

<span data-ttu-id="3231a-126"> *\*\<Supportedruntime> >** 項目應由使用 1.1 版或更新版本的執行階段所建置的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="3231a-126">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="3231a-127">若要只支援 1.0 版的執行階段所建置的應用程式必須使用[ \<Requiredruntime> >](../startup/requiredruntime-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="3231a-127">Applications built to support only version 1.0 of the runtime must use the [\<requiredRuntime>](../startup/requiredruntime-element.md) element.</span></span>

> [!NOTE]
> <span data-ttu-id="3231a-128">如果您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定組態檔，您必須使用`<requiredRuntime>`的執行階段的所有版本的項目。</span><span class="sxs-lookup"><span data-stu-id="3231a-128">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="3231a-129">`<supportedRuntime>`當您使用時，便會忽略元素[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)。</span><span class="sxs-lookup"><span data-stu-id="3231a-129">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
<span data-ttu-id="3231a-130">針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-130">For apps that support versions of the runtime from the .NET Framework 1.1 through 3.5, when multiple versions of the runtime are supported, the first element should specify the most preferred version of the runtime, and the last element should specify the least preferred version.</span></span> <span data-ttu-id="3231a-131">針對支援的.NET Framework 4.0 或更新版本中，應用程式`version`屬性會指出 CLR 版本，也就是一般.NET Framework 4 和更新版本，而`sku`屬性表示的單一.NET Framework 版本，應用程式的目標。</span><span class="sxs-lookup"><span data-stu-id="3231a-131">For apps that support the .NET Framework 4.0 or later versions, the `version` attribute indicates the CLR version, which is common to the .NET Framework 4 and later versions, and the `sku` attribute indicates the single .NET Framework version that the app targets.</span></span> 

<span data-ttu-id="3231a-132">如果 **\<Supportedruntime> >** 項目`sku`屬性已出現在組態檔，並已安裝的.NET Framework 版本是較低，則指定的支援的版本，應用程式無法執行，而是會顯示訊息，要求您安裝支援的版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-132">If the **\<supportedRuntime>** element with the `sku` attribute is present in the configuration file and the installed .NET Framework version is lower then the specified supported version, the application fails to run and instead displays a message asking to install the supported version.</span></span> <span data-ttu-id="3231a-133">否則應用程式會嘗試在任何已安裝的版本上執行，但它可能會出現非預期行為如果不是與該版本完全相容。</span><span class="sxs-lookup"><span data-stu-id="3231a-133">Otherwise, the application attempts to run on any installed version, but it may behave unexpectedly if it is not fully compatible with that version.</span></span> <span data-ttu-id="3231a-134">(如需.NET Framework 版本之間的相容性差異，請參閱[.NET Framework 中的應用程式相容性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)。)因此，我們建議您更輕鬆的錯誤診斷的應用程式組態檔中包含這個項目。</span><span class="sxs-lookup"><span data-stu-id="3231a-134">(For compatibility differences between versions of .NET Framework, see [Application compatibility in the .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Therefore, we recommend that you include this element in the application configuration file for easier error diagnostics.</span></span> <span data-ttu-id="3231a-135">（已建立新專案時，自動產生 Visual studio 的組態檔包含它）。</span><span class="sxs-lookup"><span data-stu-id="3231a-135">(The configuration file automatically generated by Visual Studio when creating a new project already contains it.)</span></span>
  
> [!NOTE]
> <span data-ttu-id="3231a-136">如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx 函式](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)，和您想要這些路徑來啟動第 4 版的 clr，而不是較早的版本，或如果您的應用程式以建置[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]具有相依性，但以舊版.NET Framework 建置的混合模式組件，它並不足以指定[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]中支援的執行階段的清單。</span><span class="sxs-lookup"><span data-stu-id="3231a-136">If your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework, it is not sufficient to specify the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the list of supported runtimes.</span></span> <span data-ttu-id="3231a-137">此外，在[\<啟動 > 項目](../startup/startup-element.md)在您的組態檔，您必須設定`useLegacyV2RuntimeActivationPolicy`屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="3231a-137">In addition, in the [\<startup> element](../startup/startup-element.md) in your configuration file, you must set the `useLegacyV2RuntimeActivationPolicy` attribute to `true`.</span></span> <span data-ttu-id="3231a-138">但是，將這個屬性設定為 `true`，即表示以舊版 .NET Framework 建置的所有元件都會使用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 執行，而不是原本建置時所使用的執行階段。</span><span class="sxs-lookup"><span data-stu-id="3231a-138">However, setting this attribute to `true` means that all components built with earlier versions of the .NET Framework are run using the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] instead of the runtimes they were built with.</span></span>

<span data-ttu-id="3231a-139">建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。</span><span class="sxs-lookup"><span data-stu-id="3231a-139">We recommend that you test applications with all the .NET Framework versions that they can run on.</span></span>

<a name="version"></a> 
## <a name="runtime-version-values"></a><span data-ttu-id="3231a-140">「執行階段版本」值</span><span class="sxs-lookup"><span data-stu-id="3231a-140">"runtime version" values</span></span>
<span data-ttu-id="3231a-141">`runtime`屬性會指定給定的應用程式需要的 Common Language Runtime (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-141">The `runtime` attribute specifies the Common Language Runtime (CLR) version that is required for a given application.</span></span> <span data-ttu-id="3231a-142">請注意，所有的.NET Framework v4.x 版本指定`v4.0`CLR。</span><span class="sxs-lookup"><span data-stu-id="3231a-142">Note that all .NET Framework v4.x versions specify the `v4.0` CLR.</span></span> <span data-ttu-id="3231a-143">下表列出的有效值*執行階段版本*的值`version`屬性。</span><span class="sxs-lookup"><span data-stu-id="3231a-143">The following table lists valid values for the *runtime version* value of the `version` attribute.</span></span>

|<span data-ttu-id="3231a-144">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="3231a-144">.NET Framework version</span></span>|<span data-ttu-id="3231a-145">`version` 屬性</span><span class="sxs-lookup"><span data-stu-id="3231a-145">`version` attribute</span></span>|
|----------------------------|-------------------------|
|<span data-ttu-id="3231a-146">1.0</span><span class="sxs-lookup"><span data-stu-id="3231a-146">1.0</span></span>|<span data-ttu-id="3231a-147">"v1.0.3705"</span><span class="sxs-lookup"><span data-stu-id="3231a-147">"v1.0.3705"</span></span>|
|<span data-ttu-id="3231a-148">1.1</span><span class="sxs-lookup"><span data-stu-id="3231a-148">1.1</span></span>|<span data-ttu-id="3231a-149">"v1.1.4322"</span><span class="sxs-lookup"><span data-stu-id="3231a-149">"v1.1.4322"</span></span>|
|<span data-ttu-id="3231a-150">2.0</span><span class="sxs-lookup"><span data-stu-id="3231a-150">2.0</span></span>|<span data-ttu-id="3231a-151">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="3231a-151">"v2.0.50727"</span></span>|
|<span data-ttu-id="3231a-152">3.0</span><span class="sxs-lookup"><span data-stu-id="3231a-152">3.0</span></span>|<span data-ttu-id="3231a-153">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="3231a-153">"v2.0.50727"</span></span>|
|<span data-ttu-id="3231a-154">3.5</span><span class="sxs-lookup"><span data-stu-id="3231a-154">3.5</span></span>|<span data-ttu-id="3231a-155">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="3231a-155">"v2.0.50727"</span></span>|
|<span data-ttu-id="3231a-156">4.0-4.8</span><span class="sxs-lookup"><span data-stu-id="3231a-156">4.0-4.8</span></span>|<span data-ttu-id="3231a-157">"v4.0"</span><span class="sxs-lookup"><span data-stu-id="3231a-157">"v4.0"</span></span>|

## <a name="sku"></a> <span data-ttu-id="3231a-158">「 sku 識別碼 」 值</span><span class="sxs-lookup"><span data-stu-id="3231a-158">"sku id" values</span></span>

<span data-ttu-id="3231a-159">`sku`屬性會使用目標 framework moniker (TFM)，以指出應用程式為目標，且要求要執行的.NET framework 版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-159">The `sku` attribute uses a target framework moniker (TFM) to indicate the version of the .NET Framework that the app targets and requires to run.</span></span> <span data-ttu-id="3231a-160">下表列出支援的有效值`sku`屬性，從.NET Framework 4 開始。</span><span class="sxs-lookup"><span data-stu-id="3231a-160">The following table lists valid values that are supported by the `sku` attribute, starting with the .NET Framework 4.</span></span>

|<span data-ttu-id="3231a-161">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="3231a-161">.NET Framework version</span></span>|<span data-ttu-id="3231a-162">`sku` 屬性</span><span class="sxs-lookup"><span data-stu-id="3231a-162">`sku` attribute</span></span>|
|----------------------------|---------------------|
|<span data-ttu-id="3231a-163">4.0</span><span class="sxs-lookup"><span data-stu-id="3231a-163">4.0</span></span>|<span data-ttu-id="3231a-164">".NETFramework,Version=v4.0"</span><span class="sxs-lookup"><span data-stu-id="3231a-164">".NETFramework,Version=v4.0"</span></span>|
|<span data-ttu-id="3231a-165">4.0，Client Profile</span><span class="sxs-lookup"><span data-stu-id="3231a-165">4.0, Client Profile</span></span>|<span data-ttu-id="3231a-166">".NETFramework,Version=v4.0,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="3231a-166">".NETFramework,Version=v4.0,Profile=Client"</span></span>|
|<span data-ttu-id="3231a-167">4.0，平台更新 1</span><span class="sxs-lookup"><span data-stu-id="3231a-167">4.0, platform update 1</span></span>|<span data-ttu-id="3231a-168">".NETFramework,Version=v4.0.1"</span><span class="sxs-lookup"><span data-stu-id="3231a-168">".NETFramework,Version=v4.0.1"</span></span>|
|<span data-ttu-id="3231a-169">4.0，Client Profile，更新 1</span><span class="sxs-lookup"><span data-stu-id="3231a-169">4.0, Client Profile, update 1</span></span>|<span data-ttu-id="3231a-170">".NETFramework,Version=v4.0.1,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="3231a-170">".NETFramework,Version=v4.0.1,Profile=Client"</span></span>|
|<span data-ttu-id="3231a-171">4.0，平台更新 2</span><span class="sxs-lookup"><span data-stu-id="3231a-171">4.0, platform update 2</span></span>|<span data-ttu-id="3231a-172">".NETFramework,Version=v4.0.2"</span><span class="sxs-lookup"><span data-stu-id="3231a-172">".NETFramework,Version=v4.0.2"</span></span>|
|<span data-ttu-id="3231a-173">4.0，Client Profile，更新 2</span><span class="sxs-lookup"><span data-stu-id="3231a-173">4.0, Client Profile, update 2</span></span>|<span data-ttu-id="3231a-174">".NETFramework,Version=v4.0.2,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="3231a-174">".NETFramework,Version=v4.0.2,Profile=Client"</span></span>|
|<span data-ttu-id="3231a-175">4.0，平台更新 3</span><span class="sxs-lookup"><span data-stu-id="3231a-175">4.0, platform update 3</span></span>|<span data-ttu-id="3231a-176">".NETFramework,Version=v4.0.3"</span><span class="sxs-lookup"><span data-stu-id="3231a-176">".NETFramework,Version=v4.0.3"</span></span>|
|<span data-ttu-id="3231a-177">4.0，Client Profile，更新 3</span><span class="sxs-lookup"><span data-stu-id="3231a-177">4.0, Client Profile, update 3</span></span>|<span data-ttu-id="3231a-178">".NETFramework,Version=v4.0.3,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="3231a-178">".NETFramework,Version=v4.0.3,Profile=Client"</span></span>|
|<span data-ttu-id="3231a-179">4.5</span><span class="sxs-lookup"><span data-stu-id="3231a-179">4.5</span></span>|<span data-ttu-id="3231a-180">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="3231a-180">".NETFramework,Version=v4.5"</span></span>|
|<span data-ttu-id="3231a-181">4.5.1</span><span class="sxs-lookup"><span data-stu-id="3231a-181">4.5.1</span></span>|<span data-ttu-id="3231a-182">".NETFramework,Version=v4.5.1"</span><span class="sxs-lookup"><span data-stu-id="3231a-182">".NETFramework,Version=v4.5.1"</span></span>|
|<span data-ttu-id="3231a-183">4.5.2</span><span class="sxs-lookup"><span data-stu-id="3231a-183">4.5.2</span></span>|<span data-ttu-id="3231a-184">".NETFramework,Version=v4.5.2"</span><span class="sxs-lookup"><span data-stu-id="3231a-184">".NETFramework,Version=v4.5.2"</span></span>|
|<span data-ttu-id="3231a-185">4.6</span><span class="sxs-lookup"><span data-stu-id="3231a-185">4.6</span></span>|<span data-ttu-id="3231a-186">".NETFramework,Version=v4.6"</span><span class="sxs-lookup"><span data-stu-id="3231a-186">".NETFramework,Version=v4.6"</span></span>|
|<span data-ttu-id="3231a-187">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3231a-187">4.6.1</span></span>|<span data-ttu-id="3231a-188">".NETFramework,Version=v4.6.1"</span><span class="sxs-lookup"><span data-stu-id="3231a-188">".NETFramework,Version=v4.6.1"</span></span>|
|<span data-ttu-id="3231a-189">4.6.2</span><span class="sxs-lookup"><span data-stu-id="3231a-189">4.6.2</span></span>|<span data-ttu-id="3231a-190">".NETFramework,Version=v4.6.2"</span><span class="sxs-lookup"><span data-stu-id="3231a-190">".NETFramework,Version=v4.6.2"</span></span>|
|<span data-ttu-id="3231a-191">4.7</span><span class="sxs-lookup"><span data-stu-id="3231a-191">4.7</span></span>|<span data-ttu-id="3231a-192">".NETFramework,Version=v4.7"</span><span class="sxs-lookup"><span data-stu-id="3231a-192">".NETFramework,Version=v4.7"</span></span>|
|<span data-ttu-id="3231a-193">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3231a-193">4.7.1</span></span>|<span data-ttu-id="3231a-194">".NETFramework,Version=v4.7.1"</span><span class="sxs-lookup"><span data-stu-id="3231a-194">".NETFramework,Version=v4.7.1"</span></span>|
|<span data-ttu-id="3231a-195">4.7.2</span><span class="sxs-lookup"><span data-stu-id="3231a-195">4.7.2</span></span>|<span data-ttu-id="3231a-196">".NETFramework，版本 = v4.7.2"</span><span class="sxs-lookup"><span data-stu-id="3231a-196">".NETFramework,Version=v4.7.2"</span></span>|
|<span data-ttu-id="3231a-197">4.8</span><span class="sxs-lookup"><span data-stu-id="3231a-197">4.8</span></span>|<span data-ttu-id="3231a-198">".NETFramework,Version=v4.8"</span><span class="sxs-lookup"><span data-stu-id="3231a-198">".NETFramework,Version=v4.8"</span></span>|

## <a name="example"></a><span data-ttu-id="3231a-199">範例</span><span class="sxs-lookup"><span data-stu-id="3231a-199">Example</span></span>

<span data-ttu-id="3231a-200">下列範例將示範如何在設定檔中指定支援的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="3231a-200">The following example shows how to specify the supported runtime version in a configuration file.</span></span> <span data-ttu-id="3231a-201">組態檔會指出應用程式的目標.NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="3231a-201">The configuration file indicates that the app targets the .NET Framework 4.7.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="3231a-202">組態檔</span><span class="sxs-lookup"><span data-stu-id="3231a-202">Configuration file</span></span>

<span data-ttu-id="3231a-203">這個項目可以在應用程式組態檔中使用。</span><span class="sxs-lookup"><span data-stu-id="3231a-203">This element can be used in the application configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="3231a-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3231a-204">See also</span></span>

- [<span data-ttu-id="3231a-205">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3231a-205">Startup Settings Schema</span></span>](../startup/index.md)
- [<span data-ttu-id="3231a-206">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3231a-206">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3231a-207">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="3231a-207">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
