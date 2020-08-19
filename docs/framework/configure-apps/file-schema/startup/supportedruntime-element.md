---
title: <supportedRuntime> configuration 元素-.NET
ms.date: 04/02/2019
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: cc221c71b68c21b61b5fa27e0972b9e9156dbc3b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558669"
---
# <a name="supportedruntime-element"></a><span data-ttu-id="f494a-102">\<supportedRuntime> 項目</span><span class="sxs-lookup"><span data-stu-id="f494a-102">\<supportedRuntime> element</span></span>

<span data-ttu-id="f494a-103">指定應用程式支援的 common language runtime 版本，以及選擇性的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-103">Specifies which common language runtime version and, optionally, .NET Framework version the application supports.</span></span>  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**  

## <a name="syntax"></a><span data-ttu-id="f494a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f494a-104">Syntax</span></span>

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a><span data-ttu-id="f494a-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f494a-105">Attributes</span></span>

|<span data-ttu-id="f494a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f494a-106">Attribute</span></span>|<span data-ttu-id="f494a-107">描述</span><span class="sxs-lookup"><span data-stu-id="f494a-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f494a-108">**version**</span><span class="sxs-lookup"><span data-stu-id="f494a-108">**version**</span></span>|<span data-ttu-id="f494a-109">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f494a-109">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f494a-110">字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-110">A string value that specifies the version of the common language runtime (CLR) that this application supports.</span></span> <span data-ttu-id="f494a-111">如需屬性的有效值 `version` ，請參閱「 [執行階段版本」值](#version) 一節。</span><span class="sxs-lookup"><span data-stu-id="f494a-111">For valid values of the `version` attribute, see the ["runtime version" values](#version) section.</span></span> <span data-ttu-id="f494a-112">**注意：**  透過 .NET Framework 3.5，「*執行階段版本*」值的格式會是「 *主要*」。*次要*。*build*。</span><span class="sxs-lookup"><span data-stu-id="f494a-112">**Note:**  Through the .NET Framework 3.5, the "*runtime version*" value takes the form *major*.*minor*.*build*.</span></span> <span data-ttu-id="f494a-113">從 .NET Framework 4 開始，只需要主要和次要版本號碼 (也就是 "v4.0" 而非 "v 4.0.30319" ) 。</span><span class="sxs-lookup"><span data-stu-id="f494a-113">Beginning with the .NET Framework 4, only the major and minor version numbers are required (that is, "v4.0" instead of "v4.0.30319").</span></span> <span data-ttu-id="f494a-114">建議使用較短的字串。</span><span class="sxs-lookup"><span data-stu-id="f494a-114">The shorter string is recommended.</span></span>|
|<span data-ttu-id="f494a-115">**sku**</span><span class="sxs-lookup"><span data-stu-id="f494a-115">**sku**</span></span>|<span data-ttu-id="f494a-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f494a-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f494a-117">字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-117">A string value that specifies the stock-keeping unit (SKU), which in turn specifies which .NET Framework release this application supports.</span></span><br /><br /> <span data-ttu-id="f494a-118">從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f494a-118">Starting with the .NET Framework 4.0, the use of the `sku` attribute is recommended.</span></span>  <span data-ttu-id="f494a-119">該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-119">When present, it indicates the version of the .NET Framework that the app targets.</span></span><br /><br /> <span data-ttu-id="f494a-120">如需 sku 屬性的有效值，請參閱「 [sku 識別碼」值](#sku) 一節。</span><span class="sxs-lookup"><span data-stu-id="f494a-120">For valid values of the sku attribute, see the ["sku id" values](#sku) section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f494a-121">備註</span><span class="sxs-lookup"><span data-stu-id="f494a-121">Remarks</span></span>

<span data-ttu-id="f494a-122">如果專案 **\<supportedRuntime>** 不存在於應用程式佈建檔中，則會使用用來建立應用程式的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-122">If the **\<supportedRuntime>** element is not present in the application configuration file, the version of the runtime used to build the application is used.</span></span>

<span data-ttu-id="f494a-123">**\<supportedRuntime>** 使用1.1 版或更新版本的執行時間所建立的所有應用程式都應該使用元素。</span><span class="sxs-lookup"><span data-stu-id="f494a-123">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="f494a-124">為了僅支援1.0 版執行時間所建立的應用程式，必須使用 [\<requiredRuntime>](requiredruntime-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="f494a-124">Applications built to support only version 1.0 of the runtime must use the [\<requiredRuntime>](requiredruntime-element.md) element.</span></span>

> [!NOTE]
> <span data-ttu-id="f494a-125">如果您使用 [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 函式來指定設定檔，則必須將專案 `<requiredRuntime>` 用於所有版本的執行時間。</span><span class="sxs-lookup"><span data-stu-id="f494a-125">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="f494a-126">`<supportedRuntime>`當您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，會忽略元素。</span><span class="sxs-lookup"><span data-stu-id="f494a-126">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
<span data-ttu-id="f494a-127">針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-127">For apps that support versions of the runtime from the .NET Framework 1.1 through 3.5, when multiple versions of the runtime are supported, the first element should specify the most preferred version of the runtime, and the last element should specify the least preferred version.</span></span> <span data-ttu-id="f494a-128">針對支援 .NET Framework 4.0 或更新版本的應用程式，此 `version` 屬性會指出 .NET Framework 4 和更新版本通用的 CLR 版本，而此 `sku` 屬性會指出應用程式所針對的單一 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-128">For apps that support the .NET Framework 4.0 or later versions, the `version` attribute indicates the CLR version, which is common to the .NET Framework 4 and later versions, and the `sku` attribute indicates the single .NET Framework version that the app targets.</span></span>

<span data-ttu-id="f494a-129">如果 **\<supportedRuntime>** `sku` 設定檔中有屬性的專案，而且安裝的 .NET Framework 版本低於指定的支援版本，則應用程式無法執行，而會顯示一則訊息，要求您安裝支援的版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-129">If the **\<supportedRuntime>** element with the `sku` attribute is present in the configuration file and the installed .NET Framework version is lower then the specified supported version, the application fails to run and instead displays a message asking to install the supported version.</span></span> <span data-ttu-id="f494a-130">否則，應用程式會嘗試在任何已安裝的版本上執行，但如果未與該版本完全相容，則可能會發生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="f494a-130">Otherwise, the application attempts to run on any installed version, but it may behave unexpectedly if it is not fully compatible with that version.</span></span> <span data-ttu-id="f494a-131"> (.NET Framework 版本之間的相容性差異，請參閱 [.NET Framework 中的應用程式相容性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)) 。因此，建議您在應用程式佈建檔中包含此元素，以簡化錯誤診斷。</span><span class="sxs-lookup"><span data-stu-id="f494a-131">(For compatibility differences between versions of .NET Framework, see [Application compatibility in the .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Therefore, we recommend that you include this element in the application configuration file for easier error diagnostics.</span></span> <span data-ttu-id="f494a-132"> (在建立新專案時，Visual Studio 自動產生的設定檔案。 ) </span><span class="sxs-lookup"><span data-stu-id="f494a-132">(The configuration file automatically generated by Visual Studio when creating a new project already contains it.)</span></span>
  
> [!NOTE]
> <span data-ttu-id="f494a-133">如果您的應用程式使用舊版啟動路徑（例如 [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式），而您想要讓這些路徑啟用 CLR 的第4版，而不是舊版，或如果您的應用程式是使用 .NET Framework 4 建立的，但相依于使用舊版 .NET Framework 所建立的混合模式元件，則在支援的執行時間清單中指定 .NET Framework 4 並不夠。</span><span class="sxs-lookup"><span data-stu-id="f494a-133">If your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework, it is not sufficient to specify the .NET Framework 4 in the list of supported runtimes.</span></span> <span data-ttu-id="f494a-134">此外，您必須在設定檔的[ \<startup> 元素](startup-element.md)中，將 `useLegacyV2RuntimeActivationPolicy` 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f494a-134">In addition, in the [\<startup> element](startup-element.md) in your configuration file, you must set the `useLegacyV2RuntimeActivationPolicy` attribute to `true`.</span></span> <span data-ttu-id="f494a-135">但是，將此屬性設定為， `true` 表示使用舊版 .NET Framework 所建立的所有元件都會使用 .NET Framework 4 來執行，而不是使用建立它們的執行時間。</span><span class="sxs-lookup"><span data-stu-id="f494a-135">However, setting this attribute to `true` means that all components built with earlier versions of the .NET Framework are run using the .NET Framework 4 instead of the runtimes they were built with.</span></span>

<span data-ttu-id="f494a-136">建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。</span><span class="sxs-lookup"><span data-stu-id="f494a-136">We recommend that you test applications with all the .NET Framework versions that they can run on.</span></span>

<a name="version"></a>
## <a name="runtime-version-values"></a><span data-ttu-id="f494a-137">「執行階段版本」值</span><span class="sxs-lookup"><span data-stu-id="f494a-137">"runtime version" values</span></span>
<span data-ttu-id="f494a-138">`runtime`屬性指定特定應用程式所需的 Common Language Runtime (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-138">The `runtime` attribute specifies the Common Language Runtime (CLR) version that is required for a given application.</span></span> <span data-ttu-id="f494a-139">請注意，所有 .NET Framework v4. x 版本都會指定 `v4.0` CLR。</span><span class="sxs-lookup"><span data-stu-id="f494a-139">Note that all .NET Framework v4.x versions specify the `v4.0` CLR.</span></span> <span data-ttu-id="f494a-140">下表列出屬性之 *執行階段版本* 值的有效值 `version` 。</span><span class="sxs-lookup"><span data-stu-id="f494a-140">The following table lists valid values for the *runtime version* value of the `version` attribute.</span></span>

|<span data-ttu-id="f494a-141">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="f494a-141">.NET Framework version</span></span>|<span data-ttu-id="f494a-142">`version` 屬性</span><span class="sxs-lookup"><span data-stu-id="f494a-142">`version` attribute</span></span>|
|----------------------------|-------------------------|
|<span data-ttu-id="f494a-143">1.0</span><span class="sxs-lookup"><span data-stu-id="f494a-143">1.0</span></span>|<span data-ttu-id="f494a-144">"v1.0.3705"</span><span class="sxs-lookup"><span data-stu-id="f494a-144">"v1.0.3705"</span></span>|
|<span data-ttu-id="f494a-145">1.1</span><span class="sxs-lookup"><span data-stu-id="f494a-145">1.1</span></span>|<span data-ttu-id="f494a-146">"v1.1.4322"</span><span class="sxs-lookup"><span data-stu-id="f494a-146">"v1.1.4322"</span></span>|
|<span data-ttu-id="f494a-147">2.0</span><span class="sxs-lookup"><span data-stu-id="f494a-147">2.0</span></span>|<span data-ttu-id="f494a-148">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="f494a-148">"v2.0.50727"</span></span>|
|<span data-ttu-id="f494a-149">3.0</span><span class="sxs-lookup"><span data-stu-id="f494a-149">3.0</span></span>|<span data-ttu-id="f494a-150">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="f494a-150">"v2.0.50727"</span></span>|
|<span data-ttu-id="f494a-151">3.5</span><span class="sxs-lookup"><span data-stu-id="f494a-151">3.5</span></span>|<span data-ttu-id="f494a-152">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="f494a-152">"v2.0.50727"</span></span>|
|<span data-ttu-id="f494a-153">4.0-4。8</span><span class="sxs-lookup"><span data-stu-id="f494a-153">4.0-4.8</span></span>|<span data-ttu-id="f494a-154">"v4.0"</span><span class="sxs-lookup"><span data-stu-id="f494a-154">"v4.0"</span></span>|

## <a name="sku-id-values"></a><a name="sku"></a> <span data-ttu-id="f494a-155">「sku 識別碼」值</span><span class="sxs-lookup"><span data-stu-id="f494a-155">"sku id" values</span></span>

<span data-ttu-id="f494a-156">`sku`屬性使用目標 framework 標記 (TFM) 來指出應用程式的目標 .NET Framework 版本，以及執行所需的版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-156">The `sku` attribute uses a target framework moniker (TFM) to indicate the version of the .NET Framework that the app targets and requires to run.</span></span> <span data-ttu-id="f494a-157">下表列出屬性所支援的有效值 `sku` （從 .NET Framework 4 開始）。</span><span class="sxs-lookup"><span data-stu-id="f494a-157">The following table lists valid values that are supported by the `sku` attribute, starting with the .NET Framework 4.</span></span>

|<span data-ttu-id="f494a-158">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="f494a-158">.NET Framework version</span></span>|<span data-ttu-id="f494a-159">`sku` 屬性</span><span class="sxs-lookup"><span data-stu-id="f494a-159">`sku` attribute</span></span>|
|----------------------------|---------------------|
|<span data-ttu-id="f494a-160">4.0</span><span class="sxs-lookup"><span data-stu-id="f494a-160">4.0</span></span>|<span data-ttu-id="f494a-161">".NETFramework,Version=v4.0"</span><span class="sxs-lookup"><span data-stu-id="f494a-161">".NETFramework,Version=v4.0"</span></span>|
|<span data-ttu-id="f494a-162">4.0，Client Profile</span><span class="sxs-lookup"><span data-stu-id="f494a-162">4.0, Client Profile</span></span>|<span data-ttu-id="f494a-163">".NETFramework,Version=v4.0,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="f494a-163">".NETFramework,Version=v4.0,Profile=Client"</span></span>|
|<span data-ttu-id="f494a-164">4.0，平台更新 1</span><span class="sxs-lookup"><span data-stu-id="f494a-164">4.0, platform update 1</span></span>|<span data-ttu-id="f494a-165">"..Netframework，Version = v 4.0.1 "</span><span class="sxs-lookup"><span data-stu-id="f494a-165">".NETFramework,Version=v4.0.1"</span></span>|
|<span data-ttu-id="f494a-166">4.0，Client Profile，更新 1</span><span class="sxs-lookup"><span data-stu-id="f494a-166">4.0, Client Profile, update 1</span></span>|<span data-ttu-id="f494a-167">"..Netframework，Version = v 4.0.1，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="f494a-167">".NETFramework,Version=v4.0.1,Profile=Client"</span></span>|
|<span data-ttu-id="f494a-168">4.0，平台更新 2</span><span class="sxs-lookup"><span data-stu-id="f494a-168">4.0, platform update 2</span></span>|<span data-ttu-id="f494a-169">"..Netframework，Version = v 4.0.2 "</span><span class="sxs-lookup"><span data-stu-id="f494a-169">".NETFramework,Version=v4.0.2"</span></span>|
|<span data-ttu-id="f494a-170">4.0，Client Profile，更新 2</span><span class="sxs-lookup"><span data-stu-id="f494a-170">4.0, Client Profile, update 2</span></span>|<span data-ttu-id="f494a-171">"..Netframework，Version = v 4.0.2，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="f494a-171">".NETFramework,Version=v4.0.2,Profile=Client"</span></span>|
|<span data-ttu-id="f494a-172">4.0，平台更新 3</span><span class="sxs-lookup"><span data-stu-id="f494a-172">4.0, platform update 3</span></span>|<span data-ttu-id="f494a-173">"..Netframework，Version = v 4.0.3 "</span><span class="sxs-lookup"><span data-stu-id="f494a-173">".NETFramework,Version=v4.0.3"</span></span>|
|<span data-ttu-id="f494a-174">4.0，Client Profile，更新 3</span><span class="sxs-lookup"><span data-stu-id="f494a-174">4.0, Client Profile, update 3</span></span>|<span data-ttu-id="f494a-175">"..Netframework，Version = v 4.0.3，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="f494a-175">".NETFramework,Version=v4.0.3,Profile=Client"</span></span>|
|<span data-ttu-id="f494a-176">4.5</span><span class="sxs-lookup"><span data-stu-id="f494a-176">4.5</span></span>|<span data-ttu-id="f494a-177">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="f494a-177">".NETFramework,Version=v4.5"</span></span>|
|<span data-ttu-id="f494a-178">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f494a-178">4.5.1</span></span>|<span data-ttu-id="f494a-179">".NETFramework,Version=v4.5.1"</span><span class="sxs-lookup"><span data-stu-id="f494a-179">".NETFramework,Version=v4.5.1"</span></span>|
|<span data-ttu-id="f494a-180">4.5.2</span><span class="sxs-lookup"><span data-stu-id="f494a-180">4.5.2</span></span>|<span data-ttu-id="f494a-181">".NETFramework,Version=v4.5.2"</span><span class="sxs-lookup"><span data-stu-id="f494a-181">".NETFramework,Version=v4.5.2"</span></span>|
|<span data-ttu-id="f494a-182">4.6</span><span class="sxs-lookup"><span data-stu-id="f494a-182">4.6</span></span>|<span data-ttu-id="f494a-183">".NETFramework,Version=v4.6"</span><span class="sxs-lookup"><span data-stu-id="f494a-183">".NETFramework,Version=v4.6"</span></span>|
|<span data-ttu-id="f494a-184">4.6.1</span><span class="sxs-lookup"><span data-stu-id="f494a-184">4.6.1</span></span>|<span data-ttu-id="f494a-185">".NETFramework,Version=v4.6.1"</span><span class="sxs-lookup"><span data-stu-id="f494a-185">".NETFramework,Version=v4.6.1"</span></span>|
|<span data-ttu-id="f494a-186">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f494a-186">4.6.2</span></span>|<span data-ttu-id="f494a-187">"..Netframework，Version = v 4.6.2 "</span><span class="sxs-lookup"><span data-stu-id="f494a-187">".NETFramework,Version=v4.6.2"</span></span>|
|<span data-ttu-id="f494a-188">4.7</span><span class="sxs-lookup"><span data-stu-id="f494a-188">4.7</span></span>|<span data-ttu-id="f494a-189">"..Netframework，Version = 4.7 4.7 "</span><span class="sxs-lookup"><span data-stu-id="f494a-189">".NETFramework,Version=v4.7"</span></span>|
|<span data-ttu-id="f494a-190">4.7.1</span><span class="sxs-lookup"><span data-stu-id="f494a-190">4.7.1</span></span>|<span data-ttu-id="f494a-191">"..Netframework，Version = v 4.7.1 "</span><span class="sxs-lookup"><span data-stu-id="f494a-191">".NETFramework,Version=v4.7.1"</span></span>|
|<span data-ttu-id="f494a-192">4.7.2</span><span class="sxs-lookup"><span data-stu-id="f494a-192">4.7.2</span></span>|<span data-ttu-id="f494a-193">"..Netframework，Version = v 4.7.2 "</span><span class="sxs-lookup"><span data-stu-id="f494a-193">".NETFramework,Version=v4.7.2"</span></span>|
|<span data-ttu-id="f494a-194">4.8</span><span class="sxs-lookup"><span data-stu-id="f494a-194">4.8</span></span>|<span data-ttu-id="f494a-195">"..Netframework，Version = 4。8</span><span class="sxs-lookup"><span data-stu-id="f494a-195">".NETFramework,Version=v4.8"</span></span>|

## <a name="example"></a><span data-ttu-id="f494a-196">範例</span><span class="sxs-lookup"><span data-stu-id="f494a-196">Example</span></span>

<span data-ttu-id="f494a-197">下列範例將示範如何在設定檔中指定支援的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="f494a-197">The following example shows how to specify the supported runtime version in a configuration file.</span></span> <span data-ttu-id="f494a-198">設定檔表示應用程式以 .NET Framework 4.7 為目標。</span><span class="sxs-lookup"><span data-stu-id="f494a-198">The configuration file indicates that the app targets the .NET Framework 4.7.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="f494a-199">組態檔</span><span class="sxs-lookup"><span data-stu-id="f494a-199">Configuration file</span></span>

<span data-ttu-id="f494a-200">這個項目可以在應用程式組態檔中使用。</span><span class="sxs-lookup"><span data-stu-id="f494a-200">This element can be used in the application configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="f494a-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f494a-201">See also</span></span>

- [<span data-ttu-id="f494a-202">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f494a-202">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f494a-203">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f494a-203">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f494a-204">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="f494a-204">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
