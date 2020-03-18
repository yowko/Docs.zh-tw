---
title: 預設探測 - .NET 核心
description: .NET Core 的系統概述.運行時.載入程式.程式集載入上下文.預設探測邏輯以查找依賴項。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399088"
---
# <a name="default-probing"></a><span data-ttu-id="cb665-103">預設探測</span><span class="sxs-lookup"><span data-stu-id="cb665-103">Default probing</span></span>

<span data-ttu-id="cb665-104">實例<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>負責查找程式集的依賴項。</span><span class="sxs-lookup"><span data-stu-id="cb665-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="cb665-105">本文介紹了<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例的探測邏輯。</span><span class="sxs-lookup"><span data-stu-id="cb665-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="cb665-106">主機配置的探測屬性</span><span class="sxs-lookup"><span data-stu-id="cb665-106">Host configured probing properties</span></span>

<span data-ttu-id="cb665-107">啟動運行時時，執行階段主機提供一組命名探測屬性，這些屬性配置<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>探測路徑。</span><span class="sxs-lookup"><span data-stu-id="cb665-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="cb665-108">每個探測屬性都是可選的。</span><span class="sxs-lookup"><span data-stu-id="cb665-108">Each probing property is optional.</span></span> <span data-ttu-id="cb665-109">如果存在，則每個屬性都是包含絕對路徑的分隔清單的字串值。</span><span class="sxs-lookup"><span data-stu-id="cb665-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="cb665-110">分隔符號在 Windows 上為";"在所有其他平臺上為"："。</span><span class="sxs-lookup"><span data-stu-id="cb665-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="cb665-111">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="cb665-111">Property Name</span></span>                 |<span data-ttu-id="cb665-112">描述</span><span class="sxs-lookup"><span data-stu-id="cb665-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="cb665-113">平臺和應用程式程式集檔路徑的清單。</span><span class="sxs-lookup"><span data-stu-id="cb665-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="cb665-114">用於搜索附屬資來源程式集的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="cb665-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="cb665-115">用於搜索非託管（本機）庫的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="cb665-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="cb665-116">用於搜索託管程式集的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="cb665-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="cb665-117">用於搜索託管程式集的本機映射的目錄路徑清單。</span><span class="sxs-lookup"><span data-stu-id="cb665-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="cb665-118">屬性是如何填充的？</span><span class="sxs-lookup"><span data-stu-id="cb665-118">How are the properties populated?</span></span>

<span data-ttu-id="cb665-119">根據*\<myapp>.deps.json*檔是否存在，填充屬性有兩種主要方案。</span><span class="sxs-lookup"><span data-stu-id="cb665-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="cb665-120">當*\*.deps.json*檔存在時，將對其進行分析以填充探測屬性。</span><span class="sxs-lookup"><span data-stu-id="cb665-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="cb665-121">當*\*.deps.json*檔不存在時，假定應用程式的目錄包含所有依賴項。</span><span class="sxs-lookup"><span data-stu-id="cb665-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="cb665-122">目錄的內容用於填充探測屬性。</span><span class="sxs-lookup"><span data-stu-id="cb665-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="cb665-123">此外，任何引用框架的*\*.deps.json*檔也會得到類似的解析。</span><span class="sxs-lookup"><span data-stu-id="cb665-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="cb665-124">最後，環境變數`ADDITIONAL_DEPS`可用於添加其他依賴項。</span><span class="sxs-lookup"><span data-stu-id="cb665-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="cb665-125">如何查看來自託管代碼的探測屬性？</span><span class="sxs-lookup"><span data-stu-id="cb665-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="cb665-126">每個屬性都可以通過從上表中<xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType>調用具有屬性名稱的函數來可用。</span><span class="sxs-lookup"><span data-stu-id="cb665-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="cb665-127">如何調試探測屬性的構造？</span><span class="sxs-lookup"><span data-stu-id="cb665-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="cb665-128">啟用某些環境變數時，.NET Core 執行階段主機將輸出有用的跟蹤消息：</span><span class="sxs-lookup"><span data-stu-id="cb665-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="cb665-129">環境變數</span><span class="sxs-lookup"><span data-stu-id="cb665-129">Environment Variable</span></span>        |<span data-ttu-id="cb665-130">描述</span><span class="sxs-lookup"><span data-stu-id="cb665-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="cb665-131">啟用跟蹤。</span><span class="sxs-lookup"><span data-stu-id="cb665-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="cb665-132">跟蹤到檔路徑而不是預設`stderr`。</span><span class="sxs-lookup"><span data-stu-id="cb665-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="cb665-133">將詳細程度從 1（最低）設置為 4（最高）。</span><span class="sxs-lookup"><span data-stu-id="cb665-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="cb665-134">託管程式集預設探測</span><span class="sxs-lookup"><span data-stu-id="cb665-134">Managed assembly default probing</span></span>

<span data-ttu-id="cb665-135">當探測以查找託管程式集時，請<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>按以下順序查看：</span><span class="sxs-lookup"><span data-stu-id="cb665-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="cb665-136">與 in<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>`TRUSTED_PLATFORM_ASSEMBLIES`匹配的檔（刪除檔副檔名後）。</span><span class="sxs-lookup"><span data-stu-id="cb665-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="cb665-137">具有常見檔副檔名`APP_NI_PATHS`的本機映射程式集檔。</span><span class="sxs-lookup"><span data-stu-id="cb665-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="cb665-138">程式集檔與`APP_PATHS`通用檔副檔名。</span><span class="sxs-lookup"><span data-stu-id="cb665-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="cb665-139">衛星（資源）程式集探測</span><span class="sxs-lookup"><span data-stu-id="cb665-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="cb665-140">要查找特定區域性的附屬程式集，構造一組檔路徑。</span><span class="sxs-lookup"><span data-stu-id="cb665-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="cb665-141">`PLATFORM_RESOURCE_ROOTS`對於 中的每個路徑，`APP_PATHS`然後，追加<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>字串、目錄分隔符號、<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>字串和副檔名".dll"。</span><span class="sxs-lookup"><span data-stu-id="cb665-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="cb665-142">如果存在任何匹配檔，請嘗試載入並返回它。</span><span class="sxs-lookup"><span data-stu-id="cb665-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="cb665-143">非託管（本機）庫探測</span><span class="sxs-lookup"><span data-stu-id="cb665-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="cb665-144">當探測以查找非託管庫時，`NATIVE_DLL_SEARCH_DIRECTORIES`將搜索 查找匹配的庫。</span><span class="sxs-lookup"><span data-stu-id="cb665-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
