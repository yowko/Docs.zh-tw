---
title: 預設探查-.NET Core
description: 介紹 .NET Core 的 AssemblyLoadCoNtext，以找出相依性的預設探查邏輯。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608420"
---
# <a name="default-probing"></a><span data-ttu-id="68a66-103">預設探查</span><span class="sxs-lookup"><span data-stu-id="68a66-103">Default probing</span></span>

<span data-ttu-id="68a66-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例負責找出元件的相依性。</span><span class="sxs-lookup"><span data-stu-id="68a66-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="68a66-105">本文描述 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 實例的探查邏輯。</span><span class="sxs-lookup"><span data-stu-id="68a66-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="68a66-106">主控制項設定的探查屬性</span><span class="sxs-lookup"><span data-stu-id="68a66-106">Host configured probing properties</span></span>

<span data-ttu-id="68a66-107">當執行時間啟動時，執行時間主機會提供一組可設定探查路徑的命名探查屬性 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="68a66-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="68a66-108">每個探查屬性都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="68a66-108">Each probing property is optional.</span></span> <span data-ttu-id="68a66-109">如果有的話，每個屬性都是包含絕對路徑的分隔清單的字串值。</span><span class="sxs-lookup"><span data-stu-id="68a66-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="68a66-110">分隔符號是 Windows 上的 '; '，其他所有平臺上的 '： '。</span><span class="sxs-lookup"><span data-stu-id="68a66-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="68a66-111">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="68a66-111">Property Name</span></span>                 |<span data-ttu-id="68a66-112">描述</span><span class="sxs-lookup"><span data-stu-id="68a66-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="68a66-113">平臺和應用程式元件檔案路徑的清單。</span><span class="sxs-lookup"><span data-stu-id="68a66-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="68a66-114">搜尋附屬資源元件的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="68a66-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="68a66-115">搜尋非受控 (原生) 程式庫的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="68a66-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="68a66-116">搜尋 managed 元件的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="68a66-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="68a66-117">目錄路徑清單，以搜尋 managed 元件的原生映射。</span><span class="sxs-lookup"><span data-stu-id="68a66-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="68a66-118">屬性的填入方式為何？</span><span class="sxs-lookup"><span data-stu-id="68a66-118">How are the properties populated?</span></span>

<span data-ttu-id="68a66-119">有兩個主要案例可以根據檔案\* \<myapp> 上的.deps.js\*是否存在來填入屬性。</span><span class="sxs-lookup"><span data-stu-id="68a66-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="68a66-120">當\* \*.deps.json\*檔案存在時，會將它剖析為填入探查屬性。</span><span class="sxs-lookup"><span data-stu-id="68a66-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="68a66-121">當檔案\* \*.deps.js\*不存在時，會假設應用程式的目錄包含所有相依性。</span><span class="sxs-lookup"><span data-stu-id="68a66-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="68a66-122">目錄的內容會用來填入探查屬性。</span><span class="sxs-lookup"><span data-stu-id="68a66-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="68a66-123">此外，任何參考架構的檔案\* \*.deps.js\*也會以同樣的方式進行剖析。</span><span class="sxs-lookup"><span data-stu-id="68a66-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="68a66-124">最後，您 `ADDITIONAL_DEPS` 可以使用環境變數來新增其他相依性。</span><span class="sxs-lookup"><span data-stu-id="68a66-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>  <span data-ttu-id="68a66-125">`dotnet.exe` 也包含 `--additional-deps` 可在應用程式啟動時設定此值的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="68a66-125">`dotnet.exe` also contains an `--additional-deps` optional parameter to set this value on application startup.</span></span>

<span data-ttu-id="68a66-126">`APP_PATHS`和 `APP_NI_PATHS` 屬性預設不會填入，並且會針對大部分的應用程式省略。</span><span class="sxs-lookup"><span data-stu-id="68a66-126">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

<span data-ttu-id="68a66-127">您可以透過存取應用程式所使用之檔案上的所有\* \*.deps.js\*清單 `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` 。</span><span class="sxs-lookup"><span data-stu-id="68a66-127">The list of all *\*.deps.json* files used by the application can be accessed via `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")`.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="68a66-128">如何? 從 managed 程式碼查看探查屬性？</span><span class="sxs-lookup"><span data-stu-id="68a66-128">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="68a66-129"><xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType>使用上表中的屬性名稱呼叫函式，即可取得每個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a66-129">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="68a66-130">如何? debug 探查屬性的結構？</span><span class="sxs-lookup"><span data-stu-id="68a66-130">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="68a66-131">啟用特定環境變數時，.NET Core 執行時間主機會輸出有用的追蹤訊息：</span><span class="sxs-lookup"><span data-stu-id="68a66-131">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="68a66-132">環境變數</span><span class="sxs-lookup"><span data-stu-id="68a66-132">Environment Variable</span></span>        |<span data-ttu-id="68a66-133">描述</span><span class="sxs-lookup"><span data-stu-id="68a66-133">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="68a66-134">啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="68a66-134">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="68a66-135">追蹤檔案路徑，而不是預設值 `stderr` 。</span><span class="sxs-lookup"><span data-stu-id="68a66-135">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="68a66-136">將詳細資訊從 1 (最低) 設定為 4 (最高) 。</span><span class="sxs-lookup"><span data-stu-id="68a66-136">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="68a66-137">Managed 元件預設探查</span><span class="sxs-lookup"><span data-stu-id="68a66-137">Managed assembly default probing</span></span>

<span data-ttu-id="68a66-138">探查以找出受管理的元件時，會依 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 序查看：</span><span class="sxs-lookup"><span data-stu-id="68a66-138">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="68a66-139"><xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` 移除檔案副檔名) 之後，符合 (的檔案。</span><span class="sxs-lookup"><span data-stu-id="68a66-139">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="68a66-140">具有通用副檔名的原生映射元件檔 `APP_NI_PATHS` 。</span><span class="sxs-lookup"><span data-stu-id="68a66-140">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="68a66-141">`APP_PATHS`具有一般副檔名的元件檔。</span><span class="sxs-lookup"><span data-stu-id="68a66-141">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="68a66-142">附屬 (資源) 元件探查</span><span class="sxs-lookup"><span data-stu-id="68a66-142">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="68a66-143">若要尋找特定文化特性的附屬元件，請建立一組檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="68a66-143">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="68a66-144">針對中的每個路徑 `PLATFORM_RESOURCE_ROOTS` `APP_PATHS` ，然後附加 <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 字串、目錄分隔符號、 <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 字串和副檔名 ' .dll '。</span><span class="sxs-lookup"><span data-stu-id="68a66-144">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="68a66-145">如果有任何相符的檔案存在，請嘗試載入並將其傳回。</span><span class="sxs-lookup"><span data-stu-id="68a66-145">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="68a66-146">非受控 (原生) 程式庫探查</span><span class="sxs-lookup"><span data-stu-id="68a66-146">Unmanaged (native) library probing</span></span>

<span data-ttu-id="68a66-147">探查以找出未受管理的程式庫時， `NATIVE_DLL_SEARCH_DIRECTORIES` 會搜尋是否有相符的程式庫。</span><span class="sxs-lookup"><span data-stu-id="68a66-147">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
