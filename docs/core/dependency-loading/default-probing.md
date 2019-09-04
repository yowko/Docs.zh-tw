---
title: 預設探查-.NET Core
description: 瞭解 .net Core 的<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>探查邏輯以找出相依性。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 020b1d0342ae822021905d2e749037f45031eb22
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234640"
---
# <a name="default-probing"></a><span data-ttu-id="e6ecc-103">預設探查</span><span class="sxs-lookup"><span data-stu-id="e6ecc-103">Default probing</span></span>

<span data-ttu-id="e6ecc-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例負責尋找元件的相依性。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="e6ecc-105">本文說明<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例的探查邏輯。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="e6ecc-106">主機設定的探查屬性</span><span class="sxs-lookup"><span data-stu-id="e6ecc-106">Host configured probing properties</span></span>

<span data-ttu-id="e6ecc-107">當執行時間啟動時, 執行時間主機會提供一組命名探查屬性來<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>設定探查路徑。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="e6ecc-108">每個探查屬性都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-108">Each probing property is optional.</span></span>  <span data-ttu-id="e6ecc-109">如果有, 每個屬性都是字串值, 其中包含絕對路徑的分隔清單。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="e6ecc-110">分隔符號是 Windows 上的 '; ' 和所有其他平臺上的 ': '。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="e6ecc-111">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="e6ecc-111">Property Name</span></span>                 |<span data-ttu-id="e6ecc-112">描述</span><span class="sxs-lookup"><span data-stu-id="e6ecc-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="e6ecc-113">平臺和應用程式元件檔案路徑的清單。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="e6ecc-114">要搜尋附屬資源元件的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="e6ecc-115">要搜尋非受控 (原生) 程式庫的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="e6ecc-116">要搜尋 managed 元件的目錄路徑清單</span><span class="sxs-lookup"><span data-stu-id="e6ecc-116">List of directory paths to search for managed assemblies</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="e6ecc-117">要搜尋 managed 元件原生映射的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="e6ecc-118">屬性的填入方式為何？</span><span class="sxs-lookup"><span data-stu-id="e6ecc-118">How are the properties populated?</span></span>

<span data-ttu-id="e6ecc-119">根據`<myapp>.deps.json`檔案是否存在, 擴充屬性有兩個主要案例。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-119">There are two main scenarios for populating the properties depending on whether the `<myapp>.deps.json` file exists.</span></span>

- <span data-ttu-id="e6ecc-120">`*.deps.json`當檔案存在時, 它會經過剖析以填入探查屬性。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-120">When the `*.deps.json` file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="e6ecc-121">`*.deps.json`當檔案不存在時, 會假設應用程式的目錄包含所有相依性。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-121">When the `*.deps.json` file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="e6ecc-122">目錄的內容是用來填入探查屬性。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="e6ecc-123">此外, 任何`*.deps.json`參考架構的檔案也會以同樣的方式進行剖析。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-123">Additionally, the `*.deps.json` files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="e6ecc-124">最後, 環境變數`ADDITIONAL_DEPS`可以用來新增其他相依性。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="e6ecc-125">如何? 看到來自受控碼的探查屬性？</span><span class="sxs-lookup"><span data-stu-id="e6ecc-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="e6ecc-126">您可以使用上表中的<xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType>屬性名稱呼叫函式, 以取得每個屬性。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="e6ecc-127">如何? debug 探查屬性的結構嗎？</span><span class="sxs-lookup"><span data-stu-id="e6ecc-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="e6ecc-128">啟用特定環境變數時, .NET Core 執行時間主機將會輸出有用的追蹤訊息:</span><span class="sxs-lookup"><span data-stu-id="e6ecc-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="e6ecc-129">環境變數</span><span class="sxs-lookup"><span data-stu-id="e6ecc-129">Environment Variable</span></span>        |<span data-ttu-id="e6ecc-130">描述</span><span class="sxs-lookup"><span data-stu-id="e6ecc-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="e6ecc-131">啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="e6ecc-132">追蹤檔案路徑, 而不是預設值`stderr`。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="e6ecc-133">設定從 1 (最低) 到 4 (最高) 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="e6ecc-134">受管理元件的預設探查</span><span class="sxs-lookup"><span data-stu-id="e6ecc-134">Managed assembly default probing</span></span>

<span data-ttu-id="e6ecc-135">當探查找出 managed 元件時, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>會依序查看:</span><span class="sxs-lookup"><span data-stu-id="e6ecc-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>
- <span data-ttu-id="e6ecc-136">符合中<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES`的檔案 (移除副檔名之後)。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="e6ecc-137">中`APP_NI_PATHS`的原生映射元件檔案與通用副檔名。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="e6ecc-138">中`APP_PATHS`的元件檔和通用副檔名。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="e6ecc-139">附屬 (資源) 元件探查</span><span class="sxs-lookup"><span data-stu-id="e6ecc-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="e6ecc-140">若要尋找特定文化特性的附屬元件, 請建立一組檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="e6ecc-141">針對`PLATFORM_RESOURCE_ROOTS` <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 和中<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>的每個路徑,附加字串、目錄分隔符號、字串和副檔名'.dll'。`APP_PATHS`</span><span class="sxs-lookup"><span data-stu-id="e6ecc-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="e6ecc-142">如果有任何相符的檔案存在, 請嘗試載入並傳回它。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="e6ecc-143">非受控 (原生) 程式庫探查</span><span class="sxs-lookup"><span data-stu-id="e6ecc-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="e6ecc-144">當探查找出非受控程式庫時`NATIVE_DLL_SEARCH_DIRECTORIES` , 會搜尋尋找相符的程式庫。</span><span class="sxs-lookup"><span data-stu-id="e6ecc-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library,</span></span>
