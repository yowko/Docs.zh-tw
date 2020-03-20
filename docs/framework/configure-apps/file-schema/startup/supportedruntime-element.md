---
title: <supportedRuntime>配置元素 - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153694"
---
# <a name="supportedruntime-element"></a><span data-ttu-id="49fea-102">\<支援的運行時>元素</span><span class="sxs-lookup"><span data-stu-id="49fea-102">\<supportedRuntime> element</span></span>

<span data-ttu-id="49fea-103">指定應用程式支援哪個通用語言執行階段版本，以及可選的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-103">Specifies which common language runtime version and, optionally, .NET Framework version the application supports.</span></span>  

[<span data-ttu-id="49fea-104">\<配置></span><span class="sxs-lookup"><span data-stu-id="49fea-104">\<configuration></span></span>](../configuration-element.md)  
<span data-ttu-id="49fea-105">&nbsp;&nbsp;[\<啟動>](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="49fea-105">&nbsp;&nbsp;[\<startup>](startup-element.md)</span></span>  
<span data-ttu-id="49fea-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<支援的運行時>**</span><span class="sxs-lookup"><span data-stu-id="49fea-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="49fea-107">語法</span><span class="sxs-lookup"><span data-stu-id="49fea-107">Syntax</span></span>

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a><span data-ttu-id="49fea-108">屬性</span><span class="sxs-lookup"><span data-stu-id="49fea-108">Attributes</span></span>

|<span data-ttu-id="49fea-109">屬性</span><span class="sxs-lookup"><span data-stu-id="49fea-109">Attribute</span></span>|<span data-ttu-id="49fea-110">描述</span><span class="sxs-lookup"><span data-stu-id="49fea-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="49fea-111">**version**</span><span class="sxs-lookup"><span data-stu-id="49fea-111">**version**</span></span>|<span data-ttu-id="49fea-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="49fea-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="49fea-113">字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-113">A string value that specifies the version of the common language runtime (CLR) that this application supports.</span></span> <span data-ttu-id="49fea-114">有關`version`屬性的有效值，請參閱["執行階段版本"值](#version)部分。</span><span class="sxs-lookup"><span data-stu-id="49fea-114">For valid values of the `version` attribute, see the ["runtime version" values](#version) section.</span></span> <span data-ttu-id="49fea-115">**注：** 通過 .NET 框架 3.5，"*執行階段版本*"值採用表單*主要*。*次要*。*生成*。</span><span class="sxs-lookup"><span data-stu-id="49fea-115">**Note:**  Through the .NET Framework 3.5, the "*runtime version*" value takes the form *major*.*minor*.*build*.</span></span> <span data-ttu-id="49fea-116">從 .NET 框架 4 開始，只需要主要版本號和次要版本號（即"v4.0"而不是"v4.0.30319"）。</span><span class="sxs-lookup"><span data-stu-id="49fea-116">Beginning with the .NET Framework 4, only the major and minor version numbers are required (that is, "v4.0" instead of "v4.0.30319").</span></span> <span data-ttu-id="49fea-117">建議使用較短的字串。</span><span class="sxs-lookup"><span data-stu-id="49fea-117">The shorter string is recommended.</span></span>|
|<span data-ttu-id="49fea-118">**Sku**</span><span class="sxs-lookup"><span data-stu-id="49fea-118">**sku**</span></span>|<span data-ttu-id="49fea-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="49fea-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="49fea-120">字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-120">A string value that specifies the stock-keeping unit (SKU), which in turn specifies which .NET Framework release this application supports.</span></span><br /><br /> <span data-ttu-id="49fea-121">從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。</span><span class="sxs-lookup"><span data-stu-id="49fea-121">Starting with the .NET Framework 4.0, the use of the `sku` attribute is recommended.</span></span>  <span data-ttu-id="49fea-122">該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-122">When present, it indicates the version of the .NET Framework that the app targets.</span></span><br /><br /> <span data-ttu-id="49fea-123">有關 sku 屬性的有效值，請參閱["sku id"值](#sku)部分。</span><span class="sxs-lookup"><span data-stu-id="49fea-123">For valid values of the sku attribute, see the ["sku id" values](#sku) section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="49fea-124">備註</span><span class="sxs-lookup"><span data-stu-id="49fea-124">Remarks</span></span>

<span data-ttu-id="49fea-125">如果應用程式佈建檔中不存在**\<支援的 Runtime>** 元素，則使用用於生成應用程式的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-125">If the **\<supportedRuntime>** element is not present in the application configuration file, the version of the runtime used to build the application is used.</span></span>

<span data-ttu-id="49fea-126">\*\* \<支援的 Runtime>\*\* 元素應由使用執行階段版本 1.1 或更高版本構建的所有應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="49fea-126">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="49fea-127">為僅支援執行階段版本 1.0 而構建的應用程式必須使用[\<所需的 Runtime>](../startup/requiredruntime-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="49fea-127">Applications built to support only version 1.0 of the runtime must use the [\<requiredRuntime>](../startup/requiredruntime-element.md) element.</span></span>

> [!NOTE]
> <span data-ttu-id="49fea-128">如果使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定設定檔，則必須對運行時的所有版本使用`<requiredRuntime>`該元素。</span><span class="sxs-lookup"><span data-stu-id="49fea-128">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="49fea-129">當您`<supportedRuntime>`使用[CorBindtoRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，該元素將被忽略。</span><span class="sxs-lookup"><span data-stu-id="49fea-129">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
<span data-ttu-id="49fea-130">針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-130">For apps that support versions of the runtime from the .NET Framework 1.1 through 3.5, when multiple versions of the runtime are supported, the first element should specify the most preferred version of the runtime, and the last element should specify the least preferred version.</span></span> <span data-ttu-id="49fea-131">對於支援 .NET Framework 4.0 或更高版本的應用`version`，該屬性指示 CLR 版本（這是 .NET Framework 4 和更高版本`sku`所共有的），該屬性指示應用所針對的單個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-131">For apps that support the .NET Framework 4.0 or later versions, the `version` attribute indicates the CLR version, which is common to the .NET Framework 4 and later versions, and the `sku` attribute indicates the single .NET Framework version that the app targets.</span></span>

<span data-ttu-id="49fea-132">如果設定檔中存在`sku`**\<包含該屬性的受支援的 Runtime>** 元素，並且已安裝的 .NET Framework 版本較低，則指定的受支援版本無法運行，則應用程式將失敗，而是顯示一條消息，要求安裝受支援的版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-132">If the **\<supportedRuntime>** element with the `sku` attribute is present in the configuration file and the installed .NET Framework version is lower then the specified supported version, the application fails to run and instead displays a message asking to install the supported version.</span></span> <span data-ttu-id="49fea-133">否則，應用程式會嘗試在任何已安裝的版本上運行，但如果它與該版本不完全相容，則可能會意外。</span><span class="sxs-lookup"><span data-stu-id="49fea-133">Otherwise, the application attempts to run on any installed version, but it may behave unexpectedly if it is not fully compatible with that version.</span></span> <span data-ttu-id="49fea-134">（有關 .NET 框架版本之間的相容性差異，請參閱[.NET 框架中的應用程式相容性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)。因此，我們建議您在應用程式佈建檔中包含此元素，以便更輕鬆地進行錯誤診斷。</span><span class="sxs-lookup"><span data-stu-id="49fea-134">(For compatibility differences between versions of .NET Framework, see [Application compatibility in the .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Therefore, we recommend that you include this element in the application configuration file for easier error diagnostics.</span></span> <span data-ttu-id="49fea-135">（視覺化工作室在創建新專案時自動生成的設定檔已包含該檔。</span><span class="sxs-lookup"><span data-stu-id="49fea-135">(The configuration file automatically generated by Visual Studio when creating a new project already contains it.)</span></span>
  
> [!NOTE]
> <span data-ttu-id="49fea-136">如果應用程式使用舊版啟動路徑（如[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)），並且希望這些路徑啟動 CLR 版本 4 而不是早期版本，或者如果應用程式使用 .NET 框架 4 構建，但依賴于使用早期版本的 .NET Framework 構建的混合模式程式集，則在受支援的運行時清單中指定 .NET Framework 4 是不夠的。</span><span class="sxs-lookup"><span data-stu-id="49fea-136">If your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework, it is not sufficient to specify the .NET Framework 4 in the list of supported runtimes.</span></span> <span data-ttu-id="49fea-137">此外，在設定檔中的[\<啟動>元素](../startup/startup-element.md)中，必須將`useLegacyV2RuntimeActivationPolicy`屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="49fea-137">In addition, in the [\<startup> element](../startup/startup-element.md) in your configuration file, you must set the `useLegacyV2RuntimeActivationPolicy` attribute to `true`.</span></span> <span data-ttu-id="49fea-138">但是，將此屬性設置為`true`意味著使用 .NET Framework 的早期版本構建的所有元件都使用 .NET Framework 4 而不是它們構建的運行時運行。</span><span class="sxs-lookup"><span data-stu-id="49fea-138">However, setting this attribute to `true` means that all components built with earlier versions of the .NET Framework are run using the .NET Framework 4 instead of the runtimes they were built with.</span></span>

<span data-ttu-id="49fea-139">建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。</span><span class="sxs-lookup"><span data-stu-id="49fea-139">We recommend that you test applications with all the .NET Framework versions that they can run on.</span></span>

<a name="version"></a>
## <a name="runtime-version-values"></a><span data-ttu-id="49fea-140">「執行階段版本」值</span><span class="sxs-lookup"><span data-stu-id="49fea-140">"runtime version" values</span></span>
<span data-ttu-id="49fea-141">該`runtime`屬性指定給定應用程式所需的通用語言運行時 （CLR） 版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-141">The `runtime` attribute specifies the Common Language Runtime (CLR) version that is required for a given application.</span></span> <span data-ttu-id="49fea-142">請注意，所有 .NET 框架 v4.x`v4.0`版本都指定 CLR。</span><span class="sxs-lookup"><span data-stu-id="49fea-142">Note that all .NET Framework v4.x versions specify the `v4.0` CLR.</span></span> <span data-ttu-id="49fea-143">下表列出了`version`屬性的*執行階段版本*值的有效值。</span><span class="sxs-lookup"><span data-stu-id="49fea-143">The following table lists valid values for the *runtime version* value of the `version` attribute.</span></span>

|<span data-ttu-id="49fea-144">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="49fea-144">.NET Framework version</span></span>|<span data-ttu-id="49fea-145">`version` 屬性</span><span class="sxs-lookup"><span data-stu-id="49fea-145">`version` attribute</span></span>|
|----------------------------|-------------------------|
|<span data-ttu-id="49fea-146">1.0</span><span class="sxs-lookup"><span data-stu-id="49fea-146">1.0</span></span>|<span data-ttu-id="49fea-147">"v1.0.3705"</span><span class="sxs-lookup"><span data-stu-id="49fea-147">"v1.0.3705"</span></span>|
|<span data-ttu-id="49fea-148">1.1</span><span class="sxs-lookup"><span data-stu-id="49fea-148">1.1</span></span>|<span data-ttu-id="49fea-149">"v1.1.4322"</span><span class="sxs-lookup"><span data-stu-id="49fea-149">"v1.1.4322"</span></span>|
|<span data-ttu-id="49fea-150">2.0</span><span class="sxs-lookup"><span data-stu-id="49fea-150">2.0</span></span>|<span data-ttu-id="49fea-151">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="49fea-151">"v2.0.50727"</span></span>|
|<span data-ttu-id="49fea-152">3.0</span><span class="sxs-lookup"><span data-stu-id="49fea-152">3.0</span></span>|<span data-ttu-id="49fea-153">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="49fea-153">"v2.0.50727"</span></span>|
|<span data-ttu-id="49fea-154">3.5</span><span class="sxs-lookup"><span data-stu-id="49fea-154">3.5</span></span>|<span data-ttu-id="49fea-155">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="49fea-155">"v2.0.50727"</span></span>|
|<span data-ttu-id="49fea-156">4.0-4.8</span><span class="sxs-lookup"><span data-stu-id="49fea-156">4.0-4.8</span></span>|<span data-ttu-id="49fea-157">"v4.0"</span><span class="sxs-lookup"><span data-stu-id="49fea-157">"v4.0"</span></span>|

## <a name="sku-id-values"></a><a name="sku"></a><span data-ttu-id="49fea-158">"sku id"值</span><span class="sxs-lookup"><span data-stu-id="49fea-158">"sku id" values</span></span>

<span data-ttu-id="49fea-159">該`sku`屬性使用目標框架名字物件 （TFM） 來指示應用的目標和運行所需的 .NET 框架的版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-159">The `sku` attribute uses a target framework moniker (TFM) to indicate the version of the .NET Framework that the app targets and requires to run.</span></span> <span data-ttu-id="49fea-160">下表列出了`sku`屬性支援的有效值，從 .NET 框架 4 開始。</span><span class="sxs-lookup"><span data-stu-id="49fea-160">The following table lists valid values that are supported by the `sku` attribute, starting with the .NET Framework 4.</span></span>

|<span data-ttu-id="49fea-161">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="49fea-161">.NET Framework version</span></span>|<span data-ttu-id="49fea-162">`sku` 屬性</span><span class="sxs-lookup"><span data-stu-id="49fea-162">`sku` attribute</span></span>|
|----------------------------|---------------------|
|<span data-ttu-id="49fea-163">4.0</span><span class="sxs-lookup"><span data-stu-id="49fea-163">4.0</span></span>|<span data-ttu-id="49fea-164">".NETFramework,Version=v4.0"</span><span class="sxs-lookup"><span data-stu-id="49fea-164">".NETFramework,Version=v4.0"</span></span>|
|<span data-ttu-id="49fea-165">4.0，Client Profile</span><span class="sxs-lookup"><span data-stu-id="49fea-165">4.0, Client Profile</span></span>|<span data-ttu-id="49fea-166">".NETFramework,Version=v4.0,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="49fea-166">".NETFramework,Version=v4.0,Profile=Client"</span></span>|
|<span data-ttu-id="49fea-167">4.0，平台更新 1</span><span class="sxs-lookup"><span data-stu-id="49fea-167">4.0, platform update 1</span></span>|<span data-ttu-id="49fea-168">".NETFramework，版本=v4.0.1"</span><span class="sxs-lookup"><span data-stu-id="49fea-168">".NETFramework,Version=v4.0.1"</span></span>|
|<span data-ttu-id="49fea-169">4.0，Client Profile，更新 1</span><span class="sxs-lookup"><span data-stu-id="49fea-169">4.0, Client Profile, update 1</span></span>|<span data-ttu-id="49fea-170">".NETFramework，版本=v4.0.1，設定檔=用戶端"</span><span class="sxs-lookup"><span data-stu-id="49fea-170">".NETFramework,Version=v4.0.1,Profile=Client"</span></span>|
|<span data-ttu-id="49fea-171">4.0，平台更新 2</span><span class="sxs-lookup"><span data-stu-id="49fea-171">4.0, platform update 2</span></span>|<span data-ttu-id="49fea-172">".NETFramework，版本=v4.0.2"</span><span class="sxs-lookup"><span data-stu-id="49fea-172">".NETFramework,Version=v4.0.2"</span></span>|
|<span data-ttu-id="49fea-173">4.0，Client Profile，更新 2</span><span class="sxs-lookup"><span data-stu-id="49fea-173">4.0, Client Profile, update 2</span></span>|<span data-ttu-id="49fea-174">".NETFramework，版本=v4.0.2，設定檔=用戶端"</span><span class="sxs-lookup"><span data-stu-id="49fea-174">".NETFramework,Version=v4.0.2,Profile=Client"</span></span>|
|<span data-ttu-id="49fea-175">4.0，平台更新 3</span><span class="sxs-lookup"><span data-stu-id="49fea-175">4.0, platform update 3</span></span>|<span data-ttu-id="49fea-176">".NETFramework，版本=v4.0.3"</span><span class="sxs-lookup"><span data-stu-id="49fea-176">".NETFramework,Version=v4.0.3"</span></span>|
|<span data-ttu-id="49fea-177">4.0，Client Profile，更新 3</span><span class="sxs-lookup"><span data-stu-id="49fea-177">4.0, Client Profile, update 3</span></span>|<span data-ttu-id="49fea-178">".NETFramework，版本=v4.0.3，設定檔=用戶端"</span><span class="sxs-lookup"><span data-stu-id="49fea-178">".NETFramework,Version=v4.0.3,Profile=Client"</span></span>|
|<span data-ttu-id="49fea-179">4.5</span><span class="sxs-lookup"><span data-stu-id="49fea-179">4.5</span></span>|<span data-ttu-id="49fea-180">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="49fea-180">".NETFramework,Version=v4.5"</span></span>|
|<span data-ttu-id="49fea-181">4.5.1</span><span class="sxs-lookup"><span data-stu-id="49fea-181">4.5.1</span></span>|<span data-ttu-id="49fea-182">".NETFramework,Version=v4.5.1"</span><span class="sxs-lookup"><span data-stu-id="49fea-182">".NETFramework,Version=v4.5.1"</span></span>|
|<span data-ttu-id="49fea-183">4.5.2</span><span class="sxs-lookup"><span data-stu-id="49fea-183">4.5.2</span></span>|<span data-ttu-id="49fea-184">".NETFramework,Version=v4.5.2"</span><span class="sxs-lookup"><span data-stu-id="49fea-184">".NETFramework,Version=v4.5.2"</span></span>|
|<span data-ttu-id="49fea-185">4.6</span><span class="sxs-lookup"><span data-stu-id="49fea-185">4.6</span></span>|<span data-ttu-id="49fea-186">".NETFramework,Version=v4.6"</span><span class="sxs-lookup"><span data-stu-id="49fea-186">".NETFramework,Version=v4.6"</span></span>|
|<span data-ttu-id="49fea-187">4.6.1</span><span class="sxs-lookup"><span data-stu-id="49fea-187">4.6.1</span></span>|<span data-ttu-id="49fea-188">".NETFramework,Version=v4.6.1"</span><span class="sxs-lookup"><span data-stu-id="49fea-188">".NETFramework,Version=v4.6.1"</span></span>|
|<span data-ttu-id="49fea-189">4.6.2</span><span class="sxs-lookup"><span data-stu-id="49fea-189">4.6.2</span></span>|<span data-ttu-id="49fea-190">".NETFramework，版本=v4.6.2"</span><span class="sxs-lookup"><span data-stu-id="49fea-190">".NETFramework,Version=v4.6.2"</span></span>|
|<span data-ttu-id="49fea-191">4.7</span><span class="sxs-lookup"><span data-stu-id="49fea-191">4.7</span></span>|<span data-ttu-id="49fea-192">".NETFramework，版本=v4.7"</span><span class="sxs-lookup"><span data-stu-id="49fea-192">".NETFramework,Version=v4.7"</span></span>|
|<span data-ttu-id="49fea-193">4.7.1</span><span class="sxs-lookup"><span data-stu-id="49fea-193">4.7.1</span></span>|<span data-ttu-id="49fea-194">".NETFramework，版本=v4.7.1"</span><span class="sxs-lookup"><span data-stu-id="49fea-194">".NETFramework,Version=v4.7.1"</span></span>|
|<span data-ttu-id="49fea-195">4.7.2</span><span class="sxs-lookup"><span data-stu-id="49fea-195">4.7.2</span></span>|<span data-ttu-id="49fea-196">".NETFramework，版本=v4.7.2"</span><span class="sxs-lookup"><span data-stu-id="49fea-196">".NETFramework,Version=v4.7.2"</span></span>|
|<span data-ttu-id="49fea-197">4.8</span><span class="sxs-lookup"><span data-stu-id="49fea-197">4.8</span></span>|<span data-ttu-id="49fea-198">".NETFramework，版本=v4.8"</span><span class="sxs-lookup"><span data-stu-id="49fea-198">".NETFramework,Version=v4.8"</span></span>|

## <a name="example"></a><span data-ttu-id="49fea-199">範例</span><span class="sxs-lookup"><span data-stu-id="49fea-199">Example</span></span>

<span data-ttu-id="49fea-200">下列範例將示範如何在設定檔中指定支援的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="49fea-200">The following example shows how to specify the supported runtime version in a configuration file.</span></span> <span data-ttu-id="49fea-201">設定檔指示應用以 .NET 框架 4.7 為目標。</span><span class="sxs-lookup"><span data-stu-id="49fea-201">The configuration file indicates that the app targets the .NET Framework 4.7.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="49fea-202">組態檔</span><span class="sxs-lookup"><span data-stu-id="49fea-202">Configuration file</span></span>

<span data-ttu-id="49fea-203">這個項目可以在應用程式組態檔中使用。</span><span class="sxs-lookup"><span data-stu-id="49fea-203">This element can be used in the application configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="49fea-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49fea-204">See also</span></span>

- [<span data-ttu-id="49fea-205">啟動設置架構</span><span class="sxs-lookup"><span data-stu-id="49fea-205">Startup Settings Schema</span></span>](../startup/index.md)
- [<span data-ttu-id="49fea-206">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="49fea-206">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="49fea-207">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="49fea-207">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
