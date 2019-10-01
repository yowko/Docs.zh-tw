---
title: <supportedRuntime> 設定元素-.NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 5e7fc5f81468ff7c4eba8145ee42a4c7cf8bc0b8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697512"
---
# <a name="supportedruntime-element"></a><span data-ttu-id="a3157-102">@no__t 0supportedRuntime > 元素</span><span class="sxs-lookup"><span data-stu-id="a3157-102">\<supportedRuntime> element</span></span>

<span data-ttu-id="a3157-103">指定應用程式支援的 common language runtime 版本和（選擇性） .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-103">Specifies which common language runtime version and, optionally, .NET Framework version the application supports.</span></span>  

[<span data-ttu-id="a3157-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a3157-104">\<configuration></span></span>](../configuration-element.md)  
<span data-ttu-id="a3157-105">&nbsp;&nbsp;[\<startup>](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3157-105">&nbsp;&nbsp;[\<startup>](startup-element.md)</span></span>  
<span data-ttu-id="a3157-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime>**</span><span class="sxs-lookup"><span data-stu-id="a3157-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a3157-107">語法</span><span class="sxs-lookup"><span data-stu-id="a3157-107">Syntax</span></span>

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a><span data-ttu-id="a3157-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a3157-108">Attributes</span></span>

|<span data-ttu-id="a3157-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a3157-109">Attribute</span></span>|<span data-ttu-id="a3157-110">描述</span><span class="sxs-lookup"><span data-stu-id="a3157-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a3157-111">**version**</span><span class="sxs-lookup"><span data-stu-id="a3157-111">**version**</span></span>|<span data-ttu-id="a3157-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a3157-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3157-113">字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-113">A string value that specifies the version of the common language runtime (CLR) that this application supports.</span></span> <span data-ttu-id="a3157-114">如需 `version` 屬性的有效值，請參閱「[執行階段版本」值](#version)一節。</span><span class="sxs-lookup"><span data-stu-id="a3157-114">For valid values of the `version` attribute, see the ["runtime version" values](#version) section.</span></span> <span data-ttu-id="a3157-115">**注意：** 透過 .NET Framework 3.5，「*執行階段版本*」值會採用*主要*格式。*次要*。*build*。</span><span class="sxs-lookup"><span data-stu-id="a3157-115">**Note:**  Through the .NET Framework 3.5, the "*runtime version*" value takes the form *major*.*minor*.*build*.</span></span> <span data-ttu-id="a3157-116">從 .NET Framework 4 開始，只需要主要和次要版本號碼（也就是 "v4.0"，而不是 "v 4.0.30319"）。</span><span class="sxs-lookup"><span data-stu-id="a3157-116">Beginning with the .NET Framework 4, only the major and minor version numbers are required (that is, "v4.0" instead of "v4.0.30319").</span></span> <span data-ttu-id="a3157-117">建議使用較短的字串。</span><span class="sxs-lookup"><span data-stu-id="a3157-117">The shorter string is recommended.</span></span>|
|<span data-ttu-id="a3157-118">**sku**</span><span class="sxs-lookup"><span data-stu-id="a3157-118">**sku**</span></span>|<span data-ttu-id="a3157-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a3157-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3157-120">字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-120">A string value that specifies the stock-keeping unit (SKU), which in turn specifies which .NET Framework release this application supports.</span></span><br /><br /> <span data-ttu-id="a3157-121">從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a3157-121">Starting with the .NET Framework 4.0, the use of the `sku` attribute is recommended.</span></span>  <span data-ttu-id="a3157-122">該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-122">When present, it indicates the version of the .NET Framework that the app targets.</span></span><br /><br /> <span data-ttu-id="a3157-123">如需 sku 屬性的有效值，請參閱「 [sku 識別碼」值](#sku)一節。</span><span class="sxs-lookup"><span data-stu-id="a3157-123">For valid values of the sku attribute, see the ["sku id" values](#sku) section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a3157-124">備註</span><span class="sxs-lookup"><span data-stu-id="a3157-124">Remarks</span></span>

<span data-ttu-id="a3157-125">如果 **@no__t 1supportedRuntime >** 元素不存在於應用程式佈建檔中，則會使用用來建立應用程式的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-125">If the **\<supportedRuntime>** element is not present in the application configuration file, the version of the runtime used to build the application is used.</span></span>

<span data-ttu-id="a3157-126">**\<Supportedruntime>** 項目應由使用 1.1 版或更新版本的執行階段所建置的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3157-126">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="a3157-127">為了僅支援1.0 版執行時間所建立的應用程式，必須使用[@no__t 1requiredRuntime 的 >](../startup/requiredruntime-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a3157-127">Applications built to support only version 1.0 of the runtime must use the [\<requiredRuntime>](../startup/requiredruntime-element.md) element.</span></span>

> [!NOTE]
> <span data-ttu-id="a3157-128">如果您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定設定檔，您必須針對所有版本的執行時間使用 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a3157-128">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="a3157-129">當您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，會忽略 `<supportedRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a3157-129">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
<span data-ttu-id="a3157-130">針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-130">For apps that support versions of the runtime from the .NET Framework 1.1 through 3.5, when multiple versions of the runtime are supported, the first element should specify the most preferred version of the runtime, and the last element should specify the least preferred version.</span></span> <span data-ttu-id="a3157-131">對於支援 .NET Framework 4.0 或更新版本的應用程式，`version` 屬性會指出 CLR 版本，這對 .NET Framework 4 和更新版本而言是通用的，而 `sku` 屬性則表示應用程式以為目標的單一 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-131">For apps that support the .NET Framework 4.0 or later versions, the `version` attribute indicates the CLR version, which is common to the .NET Framework 4 and later versions, and the `sku` attribute indicates the single .NET Framework version that the app targets.</span></span> 

<span data-ttu-id="a3157-132">如果具有 `sku` 屬性的 **@no__t 1supportedRuntime >** 元素出現在設定檔中，而已安裝的 .NET Framework 版本低於指定的支援版本，則表示應用程式無法執行，而是會顯示訊息，要求安裝支援的版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-132">If the **\<supportedRuntime>** element with the `sku` attribute is present in the configuration file and the installed .NET Framework version is lower then the specified supported version, the application fails to run and instead displays a message asking to install the supported version.</span></span> <span data-ttu-id="a3157-133">否則，應用程式會嘗試在任何已安裝的版本上執行，但如果它與該版本不完全相容，則可能會發生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="a3157-133">Otherwise, the application attempts to run on any installed version, but it may behave unexpectedly if it is not fully compatible with that version.</span></span> <span data-ttu-id="a3157-134">（如需 .NET Framework 版本之間的相容性差異，請參閱[.NET Framework 中的應用程式相容性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)）。因此，我們建議您在應用程式佈建檔中包含這個元素，以便更輕鬆地進行錯誤診斷。</span><span class="sxs-lookup"><span data-stu-id="a3157-134">(For compatibility differences between versions of .NET Framework, see [Application compatibility in the .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Therefore, we recommend that you include this element in the application configuration file for easier error diagnostics.</span></span> <span data-ttu-id="a3157-135">（當建立新專案時，Visual Studio 自動產生的設定檔案已包含此檔案）。</span><span class="sxs-lookup"><span data-stu-id="a3157-135">(The configuration file automatically generated by Visual Studio when creating a new project already contains it.)</span></span>
  
> [!NOTE]
> <span data-ttu-id="a3157-136">如果您的應用程式使用舊版啟動路徑，例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式，而您想要讓這些路徑啟用 CLR 的第4版，而不是舊版，或如果您的應用程式是以 .NET Framework 4 建立，但有相依性在以舊版 .NET Framework 建立的混合模式元件上，在支援的執行時間清單中指定 .NET Framework 4 是不夠的。</span><span class="sxs-lookup"><span data-stu-id="a3157-136">If your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework, it is not sufficient to specify the .NET Framework 4 in the list of supported runtimes.</span></span> <span data-ttu-id="a3157-137">此外，您必須在設定檔中的[@no__t 1startup > 元素](../startup/startup-element.md)中，將 `useLegacyV2RuntimeActivationPolicy` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a3157-137">In addition, in the [\<startup> element](../startup/startup-element.md) in your configuration file, you must set the `useLegacyV2RuntimeActivationPolicy` attribute to `true`.</span></span> <span data-ttu-id="a3157-138">不過，將此屬性設定為 `true` 表示以舊版 .NET Framework 建立的所有元件都是使用 .NET Framework 4 來執行，而不是以其所建立的執行時間。</span><span class="sxs-lookup"><span data-stu-id="a3157-138">However, setting this attribute to `true` means that all components built with earlier versions of the .NET Framework are run using the .NET Framework 4 instead of the runtimes they were built with.</span></span>

<span data-ttu-id="a3157-139">建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。</span><span class="sxs-lookup"><span data-stu-id="a3157-139">We recommend that you test applications with all the .NET Framework versions that they can run on.</span></span>

<a name="version"></a> 
## <a name="runtime-version-values"></a><span data-ttu-id="a3157-140">「執行階段版本」值</span><span class="sxs-lookup"><span data-stu-id="a3157-140">"runtime version" values</span></span>
<span data-ttu-id="a3157-141">@No__t-0 屬性會指定給定應用程式所需的 Common Language Runtime （CLR）版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-141">The `runtime` attribute specifies the Common Language Runtime (CLR) version that is required for a given application.</span></span> <span data-ttu-id="a3157-142">請注意，所有 .NET Framework v4. x 版本都會指定 `v4.0` CLR。</span><span class="sxs-lookup"><span data-stu-id="a3157-142">Note that all .NET Framework v4.x versions specify the `v4.0` CLR.</span></span> <span data-ttu-id="a3157-143">下表列出 `version` 屬性的*執行階段版本*值的有效值。</span><span class="sxs-lookup"><span data-stu-id="a3157-143">The following table lists valid values for the *runtime version* value of the `version` attribute.</span></span>

|<span data-ttu-id="a3157-144">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="a3157-144">.NET Framework version</span></span>|<span data-ttu-id="a3157-145">`version` 屬性</span><span class="sxs-lookup"><span data-stu-id="a3157-145">`version` attribute</span></span>|
|----------------------------|-------------------------|
|<span data-ttu-id="a3157-146">1.0</span><span class="sxs-lookup"><span data-stu-id="a3157-146">1.0</span></span>|<span data-ttu-id="a3157-147">"v1.0.3705"</span><span class="sxs-lookup"><span data-stu-id="a3157-147">"v1.0.3705"</span></span>|
|<span data-ttu-id="a3157-148">1.1</span><span class="sxs-lookup"><span data-stu-id="a3157-148">1.1</span></span>|<span data-ttu-id="a3157-149">"v1.1.4322"</span><span class="sxs-lookup"><span data-stu-id="a3157-149">"v1.1.4322"</span></span>|
|<span data-ttu-id="a3157-150">2.0</span><span class="sxs-lookup"><span data-stu-id="a3157-150">2.0</span></span>|<span data-ttu-id="a3157-151">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="a3157-151">"v2.0.50727"</span></span>|
|<span data-ttu-id="a3157-152">3.0</span><span class="sxs-lookup"><span data-stu-id="a3157-152">3.0</span></span>|<span data-ttu-id="a3157-153">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="a3157-153">"v2.0.50727"</span></span>|
|<span data-ttu-id="a3157-154">3.5</span><span class="sxs-lookup"><span data-stu-id="a3157-154">3.5</span></span>|<span data-ttu-id="a3157-155">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="a3157-155">"v2.0.50727"</span></span>|
|<span data-ttu-id="a3157-156">4.0-4.8</span><span class="sxs-lookup"><span data-stu-id="a3157-156">4.0-4.8</span></span>|<span data-ttu-id="a3157-157">"v4.0"</span><span class="sxs-lookup"><span data-stu-id="a3157-157">"v4.0"</span></span>|

## <a name="sku"></a><span data-ttu-id="a3157-158">「sku 識別碼」值</span><span class="sxs-lookup"><span data-stu-id="a3157-158">"sku id" values</span></span>

<span data-ttu-id="a3157-159">@No__t-0 屬性會使用目標 framework 名字標記（TFM）來指出應用程式以其為目標且需要執行的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-159">The `sku` attribute uses a target framework moniker (TFM) to indicate the version of the .NET Framework that the app targets and requires to run.</span></span> <span data-ttu-id="a3157-160">下表列出 `sku` 屬性支援的有效值，從 .NET Framework 4 開始。</span><span class="sxs-lookup"><span data-stu-id="a3157-160">The following table lists valid values that are supported by the `sku` attribute, starting with the .NET Framework 4.</span></span>

|<span data-ttu-id="a3157-161">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="a3157-161">.NET Framework version</span></span>|<span data-ttu-id="a3157-162">`sku` 屬性</span><span class="sxs-lookup"><span data-stu-id="a3157-162">`sku` attribute</span></span>|
|----------------------------|---------------------|
|<span data-ttu-id="a3157-163">4.0</span><span class="sxs-lookup"><span data-stu-id="a3157-163">4.0</span></span>|<span data-ttu-id="a3157-164">".NETFramework,Version=v4.0"</span><span class="sxs-lookup"><span data-stu-id="a3157-164">".NETFramework,Version=v4.0"</span></span>|
|<span data-ttu-id="a3157-165">4.0，Client Profile</span><span class="sxs-lookup"><span data-stu-id="a3157-165">4.0, Client Profile</span></span>|<span data-ttu-id="a3157-166">".NETFramework,Version=v4.0,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="a3157-166">".NETFramework,Version=v4.0,Profile=Client"</span></span>|
|<span data-ttu-id="a3157-167">4.0，平台更新 1</span><span class="sxs-lookup"><span data-stu-id="a3157-167">4.0, platform update 1</span></span>|<span data-ttu-id="a3157-168">"..Netframework，Version = v 4.0.1 "</span><span class="sxs-lookup"><span data-stu-id="a3157-168">".NETFramework,Version=v4.0.1"</span></span>|
|<span data-ttu-id="a3157-169">4.0，Client Profile，更新 1</span><span class="sxs-lookup"><span data-stu-id="a3157-169">4.0, Client Profile, update 1</span></span>|<span data-ttu-id="a3157-170">"..Netframework，Version = v 4.0.1，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="a3157-170">".NETFramework,Version=v4.0.1,Profile=Client"</span></span>|
|<span data-ttu-id="a3157-171">4.0，平台更新 2</span><span class="sxs-lookup"><span data-stu-id="a3157-171">4.0, platform update 2</span></span>|<span data-ttu-id="a3157-172">"..Netframework，Version = v 4.0.2 "</span><span class="sxs-lookup"><span data-stu-id="a3157-172">".NETFramework,Version=v4.0.2"</span></span>|
|<span data-ttu-id="a3157-173">4.0，Client Profile，更新 2</span><span class="sxs-lookup"><span data-stu-id="a3157-173">4.0, Client Profile, update 2</span></span>|<span data-ttu-id="a3157-174">"..Netframework，Version = v 4.0.2，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="a3157-174">".NETFramework,Version=v4.0.2,Profile=Client"</span></span>|
|<span data-ttu-id="a3157-175">4.0，平台更新 3</span><span class="sxs-lookup"><span data-stu-id="a3157-175">4.0, platform update 3</span></span>|<span data-ttu-id="a3157-176">"..Netframework，Version = v 4.0.3 "</span><span class="sxs-lookup"><span data-stu-id="a3157-176">".NETFramework,Version=v4.0.3"</span></span>|
|<span data-ttu-id="a3157-177">4.0，Client Profile，更新 3</span><span class="sxs-lookup"><span data-stu-id="a3157-177">4.0, Client Profile, update 3</span></span>|<span data-ttu-id="a3157-178">"..Netframework，Version = v 4.0.3，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="a3157-178">".NETFramework,Version=v4.0.3,Profile=Client"</span></span>|
|<span data-ttu-id="a3157-179">4.5</span><span class="sxs-lookup"><span data-stu-id="a3157-179">4.5</span></span>|<span data-ttu-id="a3157-180">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="a3157-180">".NETFramework,Version=v4.5"</span></span>|
|<span data-ttu-id="a3157-181">4.5.1</span><span class="sxs-lookup"><span data-stu-id="a3157-181">4.5.1</span></span>|<span data-ttu-id="a3157-182">".NETFramework,Version=v4.5.1"</span><span class="sxs-lookup"><span data-stu-id="a3157-182">".NETFramework,Version=v4.5.1"</span></span>|
|<span data-ttu-id="a3157-183">4.5.2</span><span class="sxs-lookup"><span data-stu-id="a3157-183">4.5.2</span></span>|<span data-ttu-id="a3157-184">".NETFramework,Version=v4.5.2"</span><span class="sxs-lookup"><span data-stu-id="a3157-184">".NETFramework,Version=v4.5.2"</span></span>|
|<span data-ttu-id="a3157-185">4.6</span><span class="sxs-lookup"><span data-stu-id="a3157-185">4.6</span></span>|<span data-ttu-id="a3157-186">".NETFramework,Version=v4.6"</span><span class="sxs-lookup"><span data-stu-id="a3157-186">".NETFramework,Version=v4.6"</span></span>|
|<span data-ttu-id="a3157-187">4.6.1</span><span class="sxs-lookup"><span data-stu-id="a3157-187">4.6.1</span></span>|<span data-ttu-id="a3157-188">".NETFramework,Version=v4.6.1"</span><span class="sxs-lookup"><span data-stu-id="a3157-188">".NETFramework,Version=v4.6.1"</span></span>|
|<span data-ttu-id="a3157-189">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a3157-189">4.6.2</span></span>|<span data-ttu-id="a3157-190">".NETFramework,Version=v4.6.2"</span><span class="sxs-lookup"><span data-stu-id="a3157-190">".NETFramework,Version=v4.6.2"</span></span>|
|<span data-ttu-id="a3157-191">4.7</span><span class="sxs-lookup"><span data-stu-id="a3157-191">4.7</span></span>|<span data-ttu-id="a3157-192">".NETFramework,Version=v4.7"</span><span class="sxs-lookup"><span data-stu-id="a3157-192">".NETFramework,Version=v4.7"</span></span>|
|<span data-ttu-id="a3157-193">4.7.1</span><span class="sxs-lookup"><span data-stu-id="a3157-193">4.7.1</span></span>|<span data-ttu-id="a3157-194">".NETFramework,Version=v4.7.1"</span><span class="sxs-lookup"><span data-stu-id="a3157-194">".NETFramework,Version=v4.7.1"</span></span>|
|<span data-ttu-id="a3157-195">4.7.2</span><span class="sxs-lookup"><span data-stu-id="a3157-195">4.7.2</span></span>|<span data-ttu-id="a3157-196">"..Netframework，Version = v 4.7.2 "</span><span class="sxs-lookup"><span data-stu-id="a3157-196">".NETFramework,Version=v4.7.2"</span></span>|
|<span data-ttu-id="a3157-197">4.8</span><span class="sxs-lookup"><span data-stu-id="a3157-197">4.8</span></span>|<span data-ttu-id="a3157-198">"..Netframework，Version = v 4.8 "</span><span class="sxs-lookup"><span data-stu-id="a3157-198">".NETFramework,Version=v4.8"</span></span>|

## <a name="example"></a><span data-ttu-id="a3157-199">範例</span><span class="sxs-lookup"><span data-stu-id="a3157-199">Example</span></span>

<span data-ttu-id="a3157-200">下列範例將示範如何在設定檔中指定支援的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a3157-200">The following example shows how to specify the supported runtime version in a configuration file.</span></span> <span data-ttu-id="a3157-201">設定檔指出應用程式以 .NET Framework 4.7 為目標。</span><span class="sxs-lookup"><span data-stu-id="a3157-201">The configuration file indicates that the app targets the .NET Framework 4.7.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="a3157-202">組態檔</span><span class="sxs-lookup"><span data-stu-id="a3157-202">Configuration file</span></span>

<span data-ttu-id="a3157-203">這個項目可以在應用程式組態檔中使用。</span><span class="sxs-lookup"><span data-stu-id="a3157-203">This element can be used in the application configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3157-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3157-204">See also</span></span>

- [<span data-ttu-id="a3157-205">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a3157-205">Startup Settings Schema</span></span>](../startup/index.md)
- [<span data-ttu-id="a3157-206">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a3157-206">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a3157-207">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="a3157-207">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
