---
title: <supportedRuntime>configuration 元素-.NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: ecbe73593e5b8b87909499f6fff7e865e29b1ec8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "82796037"
---
# <a name="supportedruntime-element"></a><span data-ttu-id="f7761-102">\<supportedRuntime> 項目</span><span class="sxs-lookup"><span data-stu-id="f7761-102">\<supportedRuntime> element</span></span>

<span data-ttu-id="f7761-103">指定應用程式支援的 common language runtime 版本和（選擇性） .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-103">Specifies which common language runtime version and, optionally, .NET Framework version the application supports.</span></span>  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**  

## <a name="syntax"></a><span data-ttu-id="f7761-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7761-104">Syntax</span></span>

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a><span data-ttu-id="f7761-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f7761-105">Attributes</span></span>

|<span data-ttu-id="f7761-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f7761-106">Attribute</span></span>|<span data-ttu-id="f7761-107">描述</span><span class="sxs-lookup"><span data-stu-id="f7761-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f7761-108">**version**</span><span class="sxs-lookup"><span data-stu-id="f7761-108">**version**</span></span>|<span data-ttu-id="f7761-109">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7761-109">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f7761-110">字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-110">A string value that specifies the version of the common language runtime (CLR) that this application supports.</span></span> <span data-ttu-id="f7761-111">如需屬性的有效值 `version` ，請參閱「[執行階段版本」值](#version)一節。</span><span class="sxs-lookup"><span data-stu-id="f7761-111">For valid values of the `version` attribute, see the ["runtime version" values](#version) section.</span></span> <span data-ttu-id="f7761-112">**注意：** 透過 .NET Framework 3.5，「*執行階段版本*」值會採用*主要*格式。*次要*。*build*。</span><span class="sxs-lookup"><span data-stu-id="f7761-112">**Note:**  Through the .NET Framework 3.5, the "*runtime version*" value takes the form *major*.*minor*.*build*.</span></span> <span data-ttu-id="f7761-113">從 .NET Framework 4 開始，只需要主要和次要版本號碼（也就是 "v4.0"，而不是 "v 4.0.30319"）。</span><span class="sxs-lookup"><span data-stu-id="f7761-113">Beginning with the .NET Framework 4, only the major and minor version numbers are required (that is, "v4.0" instead of "v4.0.30319").</span></span> <span data-ttu-id="f7761-114">建議使用較短的字串。</span><span class="sxs-lookup"><span data-stu-id="f7761-114">The shorter string is recommended.</span></span>|
|<span data-ttu-id="f7761-115">**sku**</span><span class="sxs-lookup"><span data-stu-id="f7761-115">**sku**</span></span>|<span data-ttu-id="f7761-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7761-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f7761-117">字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-117">A string value that specifies the stock-keeping unit (SKU), which in turn specifies which .NET Framework release this application supports.</span></span><br /><br /> <span data-ttu-id="f7761-118">從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f7761-118">Starting with the .NET Framework 4.0, the use of the `sku` attribute is recommended.</span></span>  <span data-ttu-id="f7761-119">該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-119">When present, it indicates the version of the .NET Framework that the app targets.</span></span><br /><br /> <span data-ttu-id="f7761-120">如需 sku 屬性的有效值，請參閱「 [sku 識別碼」值](#sku)一節。</span><span class="sxs-lookup"><span data-stu-id="f7761-120">For valid values of the sku attribute, see the ["sku id" values](#sku) section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7761-121">備註</span><span class="sxs-lookup"><span data-stu-id="f7761-121">Remarks</span></span>

<span data-ttu-id="f7761-122">如果專案 **\<supportedRuntime>** 不存在於應用程式佈建檔中，則會使用用來建立應用程式的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-122">If the **\<supportedRuntime>** element is not present in the application configuration file, the version of the runtime used to build the application is used.</span></span>

<span data-ttu-id="f7761-123">專案 **\<supportedRuntime>** 應該由使用1.1 版或更新版本的執行時間所建立的所有應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="f7761-123">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="f7761-124">為了僅支援1.0 版執行時間所建立的應用程式，必須使用專案 [\<requiredRuntime>](requiredruntime-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="f7761-124">Applications built to support only version 1.0 of the runtime must use the [\<requiredRuntime>](requiredruntime-element.md) element.</span></span>

> [!NOTE]
> <span data-ttu-id="f7761-125">如果您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定設定檔，您必須 `<requiredRuntime>` 針對所有版本的執行時間使用元素。</span><span class="sxs-lookup"><span data-stu-id="f7761-125">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="f7761-126">`<supportedRuntime>`當您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，會忽略元素。</span><span class="sxs-lookup"><span data-stu-id="f7761-126">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
<span data-ttu-id="f7761-127">針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-127">For apps that support versions of the runtime from the .NET Framework 1.1 through 3.5, when multiple versions of the runtime are supported, the first element should specify the most preferred version of the runtime, and the last element should specify the least preferred version.</span></span> <span data-ttu-id="f7761-128">針對支援 .NET Framework 4.0 或更新版本的應用程式， `version` 屬性會指出 CLR 版本，這對 .NET Framework 4 和更新版本而言是通用的，而 `sku` 屬性則表示應用程式以為目標的單一 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-128">For apps that support the .NET Framework 4.0 or later versions, the `version` attribute indicates the CLR version, which is common to the .NET Framework 4 and later versions, and the `sku` attribute indicates the single .NET Framework version that the app targets.</span></span>

<span data-ttu-id="f7761-129">如果 **\<supportedRuntime>** 具有屬性的專案 `sku` 存在於設定檔中，而已安裝的 .NET Framework 版本較低，則表示指定的支援版本，應用程式無法執行，而是會顯示訊息，要求您安裝支援的版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-129">If the **\<supportedRuntime>** element with the `sku` attribute is present in the configuration file and the installed .NET Framework version is lower then the specified supported version, the application fails to run and instead displays a message asking to install the supported version.</span></span> <span data-ttu-id="f7761-130">否則，應用程式會嘗試在任何已安裝的版本上執行，但如果它與該版本不完全相容，則可能會發生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="f7761-130">Otherwise, the application attempts to run on any installed version, but it may behave unexpectedly if it is not fully compatible with that version.</span></span> <span data-ttu-id="f7761-131">（如需 .NET Framework 版本之間的相容性差異，請參閱[.NET Framework 中的應用程式相容性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)）。因此，我們建議您在應用程式佈建檔中包含這個元素，以便更輕鬆地進行錯誤診斷。</span><span class="sxs-lookup"><span data-stu-id="f7761-131">(For compatibility differences between versions of .NET Framework, see [Application compatibility in the .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Therefore, we recommend that you include this element in the application configuration file for easier error diagnostics.</span></span> <span data-ttu-id="f7761-132">（當建立新專案時，Visual Studio 自動產生的設定檔案已包含此檔案）。</span><span class="sxs-lookup"><span data-stu-id="f7761-132">(The configuration file automatically generated by Visual Studio when creating a new project already contains it.)</span></span>
  
> [!NOTE]
> <span data-ttu-id="f7761-133">如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式，而您想要讓這些路徑啟動 CLR 的第4版，而不是舊版，或如果您的應用程式是以 .NET Framework 4 建立，但相依于使用舊版 .NET Framework 所建立的混合模式元件，則在支援的執行時間清單中指定 .NET Framework 4 是不夠的。</span><span class="sxs-lookup"><span data-stu-id="f7761-133">If your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework, it is not sufficient to specify the .NET Framework 4 in the list of supported runtimes.</span></span> <span data-ttu-id="f7761-134">此外，您必須在設定檔的[ \<startup> 元素](startup-element.md)中，將 `useLegacyV2RuntimeActivationPolicy` 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f7761-134">In addition, in the [\<startup> element](startup-element.md) in your configuration file, you must set the `useLegacyV2RuntimeActivationPolicy` attribute to `true`.</span></span> <span data-ttu-id="f7761-135">不過，將此屬性設定為， `true` 表示使用舊版 .NET Framework 建立的所有元件都是使用 .NET Framework 4 來執行，而不是以建立它們的執行時間來執行。</span><span class="sxs-lookup"><span data-stu-id="f7761-135">However, setting this attribute to `true` means that all components built with earlier versions of the .NET Framework are run using the .NET Framework 4 instead of the runtimes they were built with.</span></span>

<span data-ttu-id="f7761-136">建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。</span><span class="sxs-lookup"><span data-stu-id="f7761-136">We recommend that you test applications with all the .NET Framework versions that they can run on.</span></span>

<a name="version"></a>
## <a name="runtime-version-values"></a><span data-ttu-id="f7761-137">「執行階段版本」值</span><span class="sxs-lookup"><span data-stu-id="f7761-137">"runtime version" values</span></span>
<span data-ttu-id="f7761-138">`runtime`屬性會指定給定應用程式所需的 Common Language Runtime （CLR）版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-138">The `runtime` attribute specifies the Common Language Runtime (CLR) version that is required for a given application.</span></span> <span data-ttu-id="f7761-139">請注意，所有 .NET Framework v4. x 版本都會指定 `v4.0` CLR。</span><span class="sxs-lookup"><span data-stu-id="f7761-139">Note that all .NET Framework v4.x versions specify the `v4.0` CLR.</span></span> <span data-ttu-id="f7761-140">下表列出屬性的*執行階段版本*值的有效值 `version` 。</span><span class="sxs-lookup"><span data-stu-id="f7761-140">The following table lists valid values for the *runtime version* value of the `version` attribute.</span></span>

|<span data-ttu-id="f7761-141">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="f7761-141">.NET Framework version</span></span>|<span data-ttu-id="f7761-142">`version` 屬性</span><span class="sxs-lookup"><span data-stu-id="f7761-142">`version` attribute</span></span>|
|----------------------------|-------------------------|
|<span data-ttu-id="f7761-143">1.0</span><span class="sxs-lookup"><span data-stu-id="f7761-143">1.0</span></span>|<span data-ttu-id="f7761-144">"v1.0.3705"</span><span class="sxs-lookup"><span data-stu-id="f7761-144">"v1.0.3705"</span></span>|
|<span data-ttu-id="f7761-145">1.1</span><span class="sxs-lookup"><span data-stu-id="f7761-145">1.1</span></span>|<span data-ttu-id="f7761-146">"v1.1.4322"</span><span class="sxs-lookup"><span data-stu-id="f7761-146">"v1.1.4322"</span></span>|
|<span data-ttu-id="f7761-147">2.0</span><span class="sxs-lookup"><span data-stu-id="f7761-147">2.0</span></span>|<span data-ttu-id="f7761-148">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="f7761-148">"v2.0.50727"</span></span>|
|<span data-ttu-id="f7761-149">3.0</span><span class="sxs-lookup"><span data-stu-id="f7761-149">3.0</span></span>|<span data-ttu-id="f7761-150">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="f7761-150">"v2.0.50727"</span></span>|
|<span data-ttu-id="f7761-151">3.5</span><span class="sxs-lookup"><span data-stu-id="f7761-151">3.5</span></span>|<span data-ttu-id="f7761-152">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="f7761-152">"v2.0.50727"</span></span>|
|<span data-ttu-id="f7761-153">4.0-4。8</span><span class="sxs-lookup"><span data-stu-id="f7761-153">4.0-4.8</span></span>|<span data-ttu-id="f7761-154">"v4.0"</span><span class="sxs-lookup"><span data-stu-id="f7761-154">"v4.0"</span></span>|

## <a name="sku-id-values"></a><a name="sku"></a><span data-ttu-id="f7761-155">「sku 識別碼」值</span><span class="sxs-lookup"><span data-stu-id="f7761-155">"sku id" values</span></span>

<span data-ttu-id="f7761-156">`sku`屬性會使用目標 framework 名字標記（TFM）來指出應用程式以其為目標且需要執行的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-156">The `sku` attribute uses a target framework moniker (TFM) to indicate the version of the .NET Framework that the app targets and requires to run.</span></span> <span data-ttu-id="f7761-157">下表列出屬性所支援的有效值 `sku` ，從 .NET Framework 4 開始。</span><span class="sxs-lookup"><span data-stu-id="f7761-157">The following table lists valid values that are supported by the `sku` attribute, starting with the .NET Framework 4.</span></span>

|<span data-ttu-id="f7761-158">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="f7761-158">.NET Framework version</span></span>|<span data-ttu-id="f7761-159">`sku` 屬性</span><span class="sxs-lookup"><span data-stu-id="f7761-159">`sku` attribute</span></span>|
|----------------------------|---------------------|
|<span data-ttu-id="f7761-160">4.0</span><span class="sxs-lookup"><span data-stu-id="f7761-160">4.0</span></span>|<span data-ttu-id="f7761-161">".NETFramework,Version=v4.0"</span><span class="sxs-lookup"><span data-stu-id="f7761-161">".NETFramework,Version=v4.0"</span></span>|
|<span data-ttu-id="f7761-162">4.0，Client Profile</span><span class="sxs-lookup"><span data-stu-id="f7761-162">4.0, Client Profile</span></span>|<span data-ttu-id="f7761-163">".NETFramework,Version=v4.0,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="f7761-163">".NETFramework,Version=v4.0,Profile=Client"</span></span>|
|<span data-ttu-id="f7761-164">4.0，平台更新 1</span><span class="sxs-lookup"><span data-stu-id="f7761-164">4.0, platform update 1</span></span>|<span data-ttu-id="f7761-165">"..Netframework，Version = v 4.0.1 "</span><span class="sxs-lookup"><span data-stu-id="f7761-165">".NETFramework,Version=v4.0.1"</span></span>|
|<span data-ttu-id="f7761-166">4.0，Client Profile，更新 1</span><span class="sxs-lookup"><span data-stu-id="f7761-166">4.0, Client Profile, update 1</span></span>|<span data-ttu-id="f7761-167">"..Netframework，Version = v 4.0.1，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="f7761-167">".NETFramework,Version=v4.0.1,Profile=Client"</span></span>|
|<span data-ttu-id="f7761-168">4.0，平台更新 2</span><span class="sxs-lookup"><span data-stu-id="f7761-168">4.0, platform update 2</span></span>|<span data-ttu-id="f7761-169">"..Netframework，Version = v 4.0.2 "</span><span class="sxs-lookup"><span data-stu-id="f7761-169">".NETFramework,Version=v4.0.2"</span></span>|
|<span data-ttu-id="f7761-170">4.0，Client Profile，更新 2</span><span class="sxs-lookup"><span data-stu-id="f7761-170">4.0, Client Profile, update 2</span></span>|<span data-ttu-id="f7761-171">"..Netframework，Version = v 4.0.2，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="f7761-171">".NETFramework,Version=v4.0.2,Profile=Client"</span></span>|
|<span data-ttu-id="f7761-172">4.0，平台更新 3</span><span class="sxs-lookup"><span data-stu-id="f7761-172">4.0, platform update 3</span></span>|<span data-ttu-id="f7761-173">"..Netframework，Version = v 4.0.3 "</span><span class="sxs-lookup"><span data-stu-id="f7761-173">".NETFramework,Version=v4.0.3"</span></span>|
|<span data-ttu-id="f7761-174">4.0，Client Profile，更新 3</span><span class="sxs-lookup"><span data-stu-id="f7761-174">4.0, Client Profile, update 3</span></span>|<span data-ttu-id="f7761-175">"..Netframework，Version = v 4.0.3，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="f7761-175">".NETFramework,Version=v4.0.3,Profile=Client"</span></span>|
|<span data-ttu-id="f7761-176">4.5</span><span class="sxs-lookup"><span data-stu-id="f7761-176">4.5</span></span>|<span data-ttu-id="f7761-177">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="f7761-177">".NETFramework,Version=v4.5"</span></span>|
|<span data-ttu-id="f7761-178">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f7761-178">4.5.1</span></span>|<span data-ttu-id="f7761-179">".NETFramework,Version=v4.5.1"</span><span class="sxs-lookup"><span data-stu-id="f7761-179">".NETFramework,Version=v4.5.1"</span></span>|
|<span data-ttu-id="f7761-180">4.5.2</span><span class="sxs-lookup"><span data-stu-id="f7761-180">4.5.2</span></span>|<span data-ttu-id="f7761-181">".NETFramework,Version=v4.5.2"</span><span class="sxs-lookup"><span data-stu-id="f7761-181">".NETFramework,Version=v4.5.2"</span></span>|
|<span data-ttu-id="f7761-182">4.6</span><span class="sxs-lookup"><span data-stu-id="f7761-182">4.6</span></span>|<span data-ttu-id="f7761-183">".NETFramework,Version=v4.6"</span><span class="sxs-lookup"><span data-stu-id="f7761-183">".NETFramework,Version=v4.6"</span></span>|
|<span data-ttu-id="f7761-184">4.6.1</span><span class="sxs-lookup"><span data-stu-id="f7761-184">4.6.1</span></span>|<span data-ttu-id="f7761-185">".NETFramework,Version=v4.6.1"</span><span class="sxs-lookup"><span data-stu-id="f7761-185">".NETFramework,Version=v4.6.1"</span></span>|
|<span data-ttu-id="f7761-186">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f7761-186">4.6.2</span></span>|<span data-ttu-id="f7761-187">"..Netframework，Version = v 4.6.2 "</span><span class="sxs-lookup"><span data-stu-id="f7761-187">".NETFramework,Version=v4.6.2"</span></span>|
|<span data-ttu-id="f7761-188">4.7</span><span class="sxs-lookup"><span data-stu-id="f7761-188">4.7</span></span>|<span data-ttu-id="f7761-189">"..Netframework，Version = 4.7 版」</span><span class="sxs-lookup"><span data-stu-id="f7761-189">".NETFramework,Version=v4.7"</span></span>|
|<span data-ttu-id="f7761-190">4.7.1</span><span class="sxs-lookup"><span data-stu-id="f7761-190">4.7.1</span></span>|<span data-ttu-id="f7761-191">"..Netframework，Version = v 4.7.1 "</span><span class="sxs-lookup"><span data-stu-id="f7761-191">".NETFramework,Version=v4.7.1"</span></span>|
|<span data-ttu-id="f7761-192">4.7.2</span><span class="sxs-lookup"><span data-stu-id="f7761-192">4.7.2</span></span>|<span data-ttu-id="f7761-193">"..Netframework，Version = v 4.7.2 "</span><span class="sxs-lookup"><span data-stu-id="f7761-193">".NETFramework,Version=v4.7.2"</span></span>|
|<span data-ttu-id="f7761-194">4.8</span><span class="sxs-lookup"><span data-stu-id="f7761-194">4.8</span></span>|<span data-ttu-id="f7761-195">"..Netframework，Version = v 4.8 "</span><span class="sxs-lookup"><span data-stu-id="f7761-195">".NETFramework,Version=v4.8"</span></span>|

## <a name="example"></a><span data-ttu-id="f7761-196">範例</span><span class="sxs-lookup"><span data-stu-id="f7761-196">Example</span></span>

<span data-ttu-id="f7761-197">下列範例將示範如何在設定檔中指定支援的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="f7761-197">The following example shows how to specify the supported runtime version in a configuration file.</span></span> <span data-ttu-id="f7761-198">設定檔指出應用程式以 .NET Framework 4.7 為目標。</span><span class="sxs-lookup"><span data-stu-id="f7761-198">The configuration file indicates that the app targets the .NET Framework 4.7.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="f7761-199">組態檔</span><span class="sxs-lookup"><span data-stu-id="f7761-199">Configuration file</span></span>

<span data-ttu-id="f7761-200">這個項目可以在應用程式組態檔中使用。</span><span class="sxs-lookup"><span data-stu-id="f7761-200">This element can be used in the application configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7761-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7761-201">See also</span></span>

- [<span data-ttu-id="f7761-202">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f7761-202">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f7761-203">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="f7761-203">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f7761-204">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="f7761-204">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
