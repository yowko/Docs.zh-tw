---
title: 適用於 .NET Core 之 csproj 格式的新增項目
description: 深入了解現有和 .NET Core csproj 檔案之間的差異
ms.topic: reference
ms.date: 04/08/2019
ms.openlocfilehash: 4f45362fbb3df053b95156b8e633903f011a85ad
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062869"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="c6680-103">適用於 .NET Core 之 csproj 格式的新增項目</span><span class="sxs-lookup"><span data-stu-id="c6680-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="c6680-104">本文件概述從 *project.json* 改為使用 *csproj* 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至專案檔的變更。</span><span class="sxs-lookup"><span data-stu-id="c6680-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="c6680-105">如需一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件。</span><span class="sxs-lookup"><span data-stu-id="c6680-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="c6680-106">隱含套件參考</span><span class="sxs-lookup"><span data-stu-id="c6680-106">Implicit package references</span></span>

<span data-ttu-id="c6680-107">會根據您專案檔之 `<TargetFramework>` 或 `<TargetFrameworks>` 屬性中指定的目標架構來隱含參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="c6680-108">如果指定了 `<TargetFramework>`，則會忽略 `<TargetFrameworks>`，與順序無關。</span><span class="sxs-lookup"><span data-stu-id="c6680-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="c6680-109">建議</span><span class="sxs-lookup"><span data-stu-id="c6680-109">Recommendations</span></span>

<span data-ttu-id="c6680-110">由於會隱含參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件，因此建議使用下列最佳做法：</span><span class="sxs-lookup"><span data-stu-id="c6680-110">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="c6680-111">以 .NET Core 或 .NET Standard 為目標時，絕不透過專案檔中的 `<PackageReference>` 項目明確參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="c6680-112">如果您以 .NET Core 為目標時需要特定版本的執行階段，您應該使用專案中的 `<RuntimeFrameworkVersion>` 屬性 (例如 `1.0.4`)，而不是參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="c6680-113">如果您使用[獨立性部署](../deploying/index.md#publish-self-contained)，並需要 1.0.0 LTS 執行階段的特定更新程式版本，就可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="c6680-113">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="c6680-114">如果您以 .NET Standard 為目標時需要特定版本的 `NETStandard.Library` 中繼套件，您可以使用 `<NetStandardImplicitPackageVersion>` 屬性並設定所需的版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-114">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="c6680-115">請不要在 .NET Framework 專案中明確地新增或更新 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件的參考。</span><span class="sxs-lookup"><span data-stu-id="c6680-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="c6680-116">如果使用 .NET Standard 型 NuGet 套件時需要任何版本的 `NETStandard.Library`，NuGet 會自動安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-116">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="c6680-117">某些套件參考的隱含版本</span><span class="sxs-lookup"><span data-stu-id="c6680-117">Implicit version for some package references</span></span>

<span data-ttu-id="c6680-118">的大部分使用方式都 [`<PackageReference>`](#packagereference) 需要設定 `Version` 屬性，以指定要使用的 NuGet 套件版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-118">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="c6680-119">不過，使用 .NET Core 2.1 或 2.2 並參考 [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) 或 [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage) 時，該屬性是不必要的。</span><span class="sxs-lookup"><span data-stu-id="c6680-119">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="c6680-120">.NET Core SDK 可以自動針對這些套件選取應使用的版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-120">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="c6680-121">建議</span><span class="sxs-lookup"><span data-stu-id="c6680-121">Recommendation</span></span>

<span data-ttu-id="c6680-122">參考 `Microsoft.AspNetCore.App` 或 `Microsoft.AspNetCore.All` 套件時，請不要指定其版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-122">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="c6680-123">若指定版本，SDK 可能會產生警告 NETSDK1071。</span><span class="sxs-lookup"><span data-stu-id="c6680-123">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="c6680-124">若要修正此警告，請移除套件版本，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c6680-124">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="c6680-125">已知問題：.NET Core 2.1 SDK 僅在專案同時使用 Microsoft.NET.Sdk.Web 時才支援此語法。</span><span class="sxs-lookup"><span data-stu-id="c6680-125">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="c6680-126">此問題已在 .NET Core 2.2 SDK 中解決。</span><span class="sxs-lookup"><span data-stu-id="c6680-126">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="c6680-127">這些針對 ASP.NET Core 中繼套件的參考，具有和大部分的一般 NuGet 套件些微不同的行為。</span><span class="sxs-lookup"><span data-stu-id="c6680-127">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="c6680-128">使用這些中繼套件之應用程式的[架構相依部署](../deploying/index.md#publish-runtime-dependent)會自動利用 ASP.NET Core 共用架構的優點。</span><span class="sxs-lookup"><span data-stu-id="c6680-128">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="c6680-129">當您使用中繼套件時，系統**不會**搭配應用程式部署來自所參考之 ASP.NET Core NuGet 套件的任何資產；ASP.NET Core 共用架構會包含這些資產。</span><span class="sxs-lookup"><span data-stu-id="c6680-129">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="c6680-130">共用架構中的資產會針對目標平台最佳化，以改善應用程式啟動時間。</span><span class="sxs-lookup"><span data-stu-id="c6680-130">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="c6680-131">如需共用架構的詳細資訊，請參閱 [.NET Core 發佈封裝](../distribution-packaging.md)。</span><span class="sxs-lookup"><span data-stu-id="c6680-131">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="c6680-132">如果「已指定」\*\* 某個版本，系統會將它視為 ASP.NET Core 共用架構適用於架構相依部署的「最小」\*\* 版本，以及獨立式部署的「確切」\*\* 版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-132">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="c6680-133">這可能會導致下列結果：</span><span class="sxs-lookup"><span data-stu-id="c6680-133">This can have the following consequences:</span></span>

- <span data-ttu-id="c6680-134">如果安裝在伺服器上的 ASP.NET Core 版本小於 PackageReference 上所指定的版本，.NET Core 處理序將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="c6680-134">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="c6680-135">針對中繼套件的更新通常會在於裝載環境 (例如 Azure) 中推出之前，先在 NuGet.org 上提供使用。</span><span class="sxs-lookup"><span data-stu-id="c6680-135">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="c6680-136">將 PackageReference 上的版本更新為 ASP.NET Core 的版本，可能會導致已部署的應用程式發生失敗。</span><span class="sxs-lookup"><span data-stu-id="c6680-136">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="c6680-137">如果應用程式是以[獨立式部署](../deploying/index.md#publish-self-contained)的形式部署，該應用程式可能不會包含針對 .NET Core 的最新安全性更新。</span><span class="sxs-lookup"><span data-stu-id="c6680-137">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="c6680-138">沒有指定版本時，獨立式部署中的 SDK 可以自動包含最新版本的 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="c6680-138">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="c6680-139">.NET Core 專案中包含預設編譯</span><span class="sxs-lookup"><span data-stu-id="c6680-139">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="c6680-140">隨著改為使用最新 SDK 版本中的 *csproj* 格式，編譯項目的預設包含項目和排除項目以及內嵌資源都已移至 SDK 屬性檔。</span><span class="sxs-lookup"><span data-stu-id="c6680-140">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="c6680-141">這表示您不再需要於專案檔中指定這些項目。</span><span class="sxs-lookup"><span data-stu-id="c6680-141">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="c6680-142">這樣做的主要原因是為了讓專案檔更為簡潔。</span><span class="sxs-lookup"><span data-stu-id="c6680-142">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="c6680-143">SDK 中的預設值應該涵蓋最常見的使用案例，而不需要在每個建立的專案中重複這些項目。</span><span class="sxs-lookup"><span data-stu-id="c6680-143">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="c6680-144">這會產生較小的專案檔，而更容易了解及視需要手動編輯。</span><span class="sxs-lookup"><span data-stu-id="c6680-144">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="c6680-145">下表顯示 SDK 中會同時包含及排除的元素與 [Glob (英文)](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="c6680-145">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="c6680-146">項目</span><span class="sxs-lookup"><span data-stu-id="c6680-146">Element</span></span>           | <span data-ttu-id="c6680-147">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="c6680-147">Include glob</span></span>                              | <span data-ttu-id="c6680-148">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="c6680-148">Exclude glob</span></span>                                                  | <span data-ttu-id="c6680-149">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="c6680-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="c6680-150">編譯</span><span class="sxs-lookup"><span data-stu-id="c6680-150">Compile</span></span>           | <span data-ttu-id="c6680-151">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="c6680-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="c6680-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="c6680-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="c6680-153">N/A</span><span class="sxs-lookup"><span data-stu-id="c6680-153">N/A</span></span>                      |
| <span data-ttu-id="c6680-154">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="c6680-154">EmbeddedResource</span></span>  | <span data-ttu-id="c6680-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="c6680-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="c6680-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="c6680-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c6680-157">N/A</span><span class="sxs-lookup"><span data-stu-id="c6680-157">N/A</span></span>                      |
| <span data-ttu-id="c6680-158">無</span><span class="sxs-lookup"><span data-stu-id="c6680-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="c6680-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="c6680-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c6680-160">\*\*/\*.cs、\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="c6680-160">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="c6680-161">**排除 Glob** 一律會排除 `./bin` 和 `./obj` 資料夾，其分別由 `$(BaseOutputPath)` 和 `$(BaseIntermediateOutputPath)` MSBuild 屬性所代表。</span><span class="sxs-lookup"><span data-stu-id="c6680-161">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="c6680-162">整體而言，所有排除都是由 `$(DefaultItemExcludes)` 所代表。</span><span class="sxs-lookup"><span data-stu-id="c6680-162">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="c6680-163">如果您的專案有 Glob，而且您嘗試使用最新的 SDK 建置專案，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="c6680-163">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="c6680-164">包含了重複的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="c6680-164">Duplicate Compile items were included.</span></span> <span data-ttu-id="c6680-165">.NET SDK 預設會包含您專案目錄中的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="c6680-165">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="c6680-166">您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。</span><span class="sxs-lookup"><span data-stu-id="c6680-166">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="c6680-167">若要解決此錯誤，您可以明確移除符合上表所列項目的 `Compile` 項目，或將 `<EnableDefaultCompileItems>` 屬性設定為 `false`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6680-167">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="c6680-168">將此屬性設定為 `false` 會停用隱含包含項目，還原成必須在專案中指定預設 Glob 的舊版 SDK 行為。</span><span class="sxs-lookup"><span data-stu-id="c6680-168">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="c6680-169">這項變更不會修改其他包含項目的主要機制。</span><span class="sxs-lookup"><span data-stu-id="c6680-169">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="c6680-170">不過，如果您想要指定某些檔案由應用程式發行，您仍然可以使用 *csproj* 中已知的機制來執行這項作業 (例如 `<Content>` 項目)。</span><span class="sxs-lookup"><span data-stu-id="c6680-170">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="c6680-171">`<EnableDefaultCompileItems>` 只會停用 `Compile` GLOB，而不會影響隱含 `None` GLOB 這類其他 GLOB，後者也會套用至 \*.cs 項目。</span><span class="sxs-lookup"><span data-stu-id="c6680-171">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="c6680-172">因此，方案總管\*\*\*\* 會繼續將 \*.cs 項目顯示為包含為 `None` 項目之專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="c6680-172">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="c6680-173">透過類似的方式，您可以將 `<EnableDefaultNoneItems>` 設為 False 以停用隱含 `None` GLOB，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6680-173">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="c6680-174">若要停用**所有隱含 GLOB**，您可以將 `<EnableDefaultItems>` 屬性設定為 `false`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c6680-174">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="c6680-175">如何以 MSBuild 查看專案的方式查看整個專案</span><span class="sxs-lookup"><span data-stu-id="c6680-175">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="c6680-176">雖然那些 csproj 變更可大幅簡化專案檔，在包括 SDK 和其目標之後，您可能會想要以 MSBuild 查看專案的方式查看完全展開的專案。</span><span class="sxs-lookup"><span data-stu-id="c6680-176">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="c6680-177">使用 [`dotnet msbuild`](dotnet-msbuild.md) 命令的 [`/pp` 切換](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) 對專案進行前置處理，它可以在不需要實際建置專案的情況下，顯示匯入的檔案、檔案的來源，以及該檔案對組建的貢獻：</span><span class="sxs-lookup"><span data-stu-id="c6680-177">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="c6680-178">如果專案具有多個目標架構，系統應該會透過將它們的其中之一指定為 MSBuild 屬性，來使命令的結果專注於該目標架構：</span><span class="sxs-lookup"><span data-stu-id="c6680-178">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="c6680-179">新增項目</span><span class="sxs-lookup"><span data-stu-id="c6680-179">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="c6680-180">Sdk 屬性</span><span class="sxs-lookup"><span data-stu-id="c6680-180">Sdk attribute</span></span>

<span data-ttu-id="c6680-181">*.csproj* 檔案的根 `<Project>` 元素有一個新屬性，稱為 `Sdk`。</span><span class="sxs-lookup"><span data-stu-id="c6680-181">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="c6680-182">`Sdk` 會指定專案將使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="c6680-182">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="c6680-183">如[分層文件](cli-msbuild-architecture.md)所述，SDK 是可建置 .NET Core 程式碼的一組 MSBuild [工作](/visualstudio/msbuild/msbuild-tasks)和[目標](/visualstudio/msbuild/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="c6680-183">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="c6680-184">下列 Sdk 適用于 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="c6680-184">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="c6680-185">識別碼為 `Microsoft.NET.Sdk` 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c6680-185">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="c6680-186">識別碼為 `Microsoft.NET.Sdk.Web` 的 .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="c6680-186">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="c6680-187">識別碼為 `Microsoft.NET.Sdk.Razor` 的 .NET Core Razor 類別庫 SDK</span><span class="sxs-lookup"><span data-stu-id="c6680-187">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="c6680-188">自 .NET Core 3.0 起，具有 (識別碼的 .NET Core 背景工作角色服務 `Microsoft.NET.Sdk.Worker`) </span><span class="sxs-lookup"><span data-stu-id="c6680-188">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="c6680-189">自 .NET Core 3.0 之後，具有 (識別碼的 .NET Core WinForms 和 WPF `Microsoft.NET.Sdk.WindowsDesktop`) </span><span class="sxs-lookup"><span data-stu-id="c6680-189">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="c6680-190">您必須在 `<Project>` 項目中將 `Sdk` 屬性設定為上述其中一個識別碼，才能使用 .NET Core 工具並建置您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6680-190">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="c6680-191">PackageReference</span><span class="sxs-lookup"><span data-stu-id="c6680-191">PackageReference</span></span>

<span data-ttu-id="c6680-192">`<PackageReference>` 項目元素會[在專案中指定 NuGet 相依性](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="c6680-192">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="c6680-193">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6680-193">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="c6680-194">版本</span><span class="sxs-lookup"><span data-stu-id="c6680-194">Version</span></span>

<span data-ttu-id="c6680-195">必要的 `Version` 屬性會指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-195">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="c6680-196">屬性會遵循[NuGet 版本範圍](/nuget/concepts/package-versioning#version-ranges)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="c6680-196">The attribute respects the rules of the [NuGet version range](/nuget/concepts/package-versioning#version-ranges) scheme.</span></span> <span data-ttu-id="c6680-197">預設行為是最小版本（內含相符）。</span><span class="sxs-lookup"><span data-stu-id="c6680-197">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="c6680-198">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3, )` ，表示已解析的封裝將會有版本1.2.3 （如果有的話）或更高版本（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="c6680-198">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="c6680-199">IncludeAssets、ExcludeAssets 和 PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="c6680-199">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="c6680-200">`IncludeAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。</span><span class="sxs-lookup"><span data-stu-id="c6680-200">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="c6680-201">根據預設，所有套件資產均包含在內。</span><span class="sxs-lookup"><span data-stu-id="c6680-201">By default, all package assets are included.</span></span>

<span data-ttu-id="c6680-202">`ExcludeAssets` 屬性指定不應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。</span><span class="sxs-lookup"><span data-stu-id="c6680-202">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="c6680-203">`PrivateAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定但未流向下一個專案的套件)。</span><span class="sxs-lookup"><span data-stu-id="c6680-203">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="c6680-204">根據預設，當此屬性不存在時，`Analyzers`、`Build` 和 `ContentFiles` 會是私人資產。</span><span class="sxs-lookup"><span data-stu-id="c6680-204">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="c6680-205">`PrivateAssets`相當於 xproj 元素*上的project.js* / *xproj* `SuppressParent` 。</span><span class="sxs-lookup"><span data-stu-id="c6680-205">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="c6680-206">這些屬性可包含下列一或多個項目，若列出不只一個，則以分號 `;` 字元分隔：</span><span class="sxs-lookup"><span data-stu-id="c6680-206">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="c6680-207">`Compile`– *lib*資料夾的內容可供編譯。</span><span class="sxs-lookup"><span data-stu-id="c6680-207">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="c6680-208">`Runtime`–*運行*時間資料夾的內容會散發。</span><span class="sxs-lookup"><span data-stu-id="c6680-208">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="c6680-209">`ContentFiles`–使用*contentfiles*資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="c6680-209">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="c6680-210">`Build`–會使用*build*資料夾中的 .props/目標。</span><span class="sxs-lookup"><span data-stu-id="c6680-210">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="c6680-211">`Native`–原生資產的內容會複製到執行時間的*輸出*資料夾。</span><span class="sxs-lookup"><span data-stu-id="c6680-211">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="c6680-212">`Analyzers` – 會使用分析器。</span><span class="sxs-lookup"><span data-stu-id="c6680-212">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="c6680-213">另外，該屬性也可以包含︰</span><span class="sxs-lookup"><span data-stu-id="c6680-213">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="c6680-214">`None` – 未使用任何資產。</span><span class="sxs-lookup"><span data-stu-id="c6680-214">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="c6680-215">`All` – 會使用所有資產。</span><span class="sxs-lookup"><span data-stu-id="c6680-215">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="c6680-216">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="c6680-216">DotNetCliToolReference</span></span>

<span data-ttu-id="c6680-217">`<DotNetCliToolReference>` 項目元素指定使用者想要在專案內容中還原的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="c6680-217">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="c6680-218">它會取代 *project.json* 中的 `tools` 節點。</span><span class="sxs-lookup"><span data-stu-id="c6680-218">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="c6680-219">請注意 `DotNetCliToolReference` ，[現在已取代](https://github.com/dotnet/announcements/issues/107) [.net Core 本機工具](./global-tools.md#install-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="c6680-219">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](./global-tools.md#install-a-local-tool).</span></span>

#### <a name="version"></a><span data-ttu-id="c6680-220">版本</span><span class="sxs-lookup"><span data-stu-id="c6680-220">Version</span></span>

<span data-ttu-id="c6680-221">`Version` 指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="c6680-222">該屬性採用 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="c6680-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="c6680-223">預設行為是最小版本（內含相符）。</span><span class="sxs-lookup"><span data-stu-id="c6680-223">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="c6680-224">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3, )` ，表示已解析的封裝將會有版本1.2.3 （如果有的話）或更高版本（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="c6680-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="c6680-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="c6680-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="c6680-226">`<RuntimeIdentifiers>` 屬性元素可讓您針對專案指定以分號分隔的[執行階段識別碼 (RID)](../rid-catalog.md) 清單。</span><span class="sxs-lookup"><span data-stu-id="c6680-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="c6680-227">RID 允許發行獨立部署。</span><span class="sxs-lookup"><span data-stu-id="c6680-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="c6680-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="c6680-228">RuntimeIdentifier</span></span>

<span data-ttu-id="c6680-229">`<RuntimeIdentifier>` 屬性元素可讓您針對專案只指定一個[執行階段識別碼 (RID)](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="c6680-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="c6680-230">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="c6680-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="c6680-231">如果您需要發佈以供多個執行階段使用，請改用 `<RuntimeIdentifiers>` (複數)。</span><span class="sxs-lookup"><span data-stu-id="c6680-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="c6680-232">只需要單一執行階段時，`<RuntimeIdentifier>` 可提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="c6680-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="c6680-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="c6680-233">PackageTargetFallback</span></span>

<span data-ttu-id="c6680-234">`<PackageTargetFallback>` 屬性元素可讓您指定一組要在還原套件時使用的相容目標。</span><span class="sxs-lookup"><span data-stu-id="c6680-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="c6680-235">其設計目的是為了讓使用 dotnet [TxM (目標 x Moniker)](/nuget/schema/target-frameworks) 的套件能和未宣告 dotnet TxM 的套件一起運作。</span><span class="sxs-lookup"><span data-stu-id="c6680-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="c6680-236">如果您的專案使用 dotnet TxM，除非您將 `<PackageTargetFallback>` 新增至專案，以讓非 dotnet 平台變成能與 dotnet 相容，否則其相依的所有套件也必須要有 dotnet TxM。</span><span class="sxs-lookup"><span data-stu-id="c6680-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="c6680-237">下列範例可為專案中的所有目標提供後援：</span><span class="sxs-lookup"><span data-stu-id="c6680-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="c6680-238">下列範例只會為 `netcoreapp2.1` 目標指定後援︰</span><span class="sxs-lookup"><span data-stu-id="c6680-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="c6680-239">建置事件</span><span class="sxs-lookup"><span data-stu-id="c6680-239">Build events</span></span>

<span data-ttu-id="c6680-240">在專案檔中指定預先建立和後置組建事件的方式已經變更。</span><span class="sxs-lookup"><span data-stu-id="c6680-240">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="c6680-241">SDK 樣式的專案格式不建議使用 PreBuildEvent 和 Postbuildevent.bat 屬性，因為) 不會解析如 $ (ProjectDir 的宏。</span><span class="sxs-lookup"><span data-stu-id="c6680-241">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="c6680-242">例如，已不再支援下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c6680-242">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="c6680-243">在 SDK 樣式專案中，使用名為或的 MSBuild 目標， `PreBuild` `PostBuild` 並設定的 `BeforeTargets` 屬性 `PreBuild` 或的 `AfterTargets` 屬性 `PostBuild` 。</span><span class="sxs-lookup"><span data-stu-id="c6680-243">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="c6680-244">在上述範例中，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c6680-244">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="c6680-245">您可以針對 MSBuild 目標使用任何名稱，但 Visual Studio IDE 會辨識 `PreBuild` 和 `PostBuild` 目標，因此建議使用這些名稱，讓您可以編輯 Visual Studio IDE 中的命令。</span><span class="sxs-lookup"><span data-stu-id="c6680-245">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="c6680-246">NuGet 中繼資料屬性</span><span class="sxs-lookup"><span data-stu-id="c6680-246">NuGet metadata properties</span></span>

<span data-ttu-id="c6680-247">隨著移至 MSBuild，我們已將從*project.js*封裝 NuGet 套件時使用的輸入中繼資料移至 *.csproj*檔案。</span><span class="sxs-lookup"><span data-stu-id="c6680-247">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="c6680-248">此輸入是 MSBuild 屬性，因此必須移至 `<PropertyGroup>` 群組。</span><span class="sxs-lookup"><span data-stu-id="c6680-248">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="c6680-249">以下是使用 `dotnet pack` 命令或 `Pack` SDK 中的 MSBuild 目標時，用來做為封裝程式輸入的屬性清單：</span><span class="sxs-lookup"><span data-stu-id="c6680-249">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="c6680-250">IsPackable</span><span class="sxs-lookup"><span data-stu-id="c6680-250">IsPackable</span></span>

<span data-ttu-id="c6680-251">布林值，指定是否可封裝專案。</span><span class="sxs-lookup"><span data-stu-id="c6680-251">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="c6680-252">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="c6680-252">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="c6680-253">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="c6680-253">PackageVersion</span></span>

<span data-ttu-id="c6680-254">指定所產生之套件的版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-254">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="c6680-255">接受所有形式的 NuGet 版本字串。</span><span class="sxs-lookup"><span data-stu-id="c6680-255">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="c6680-256">預設為 `$(Version)` 的值，也就是專案中的屬性 `Version`。</span><span class="sxs-lookup"><span data-stu-id="c6680-256">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="c6680-257">PackageId</span><span class="sxs-lookup"><span data-stu-id="c6680-257">PackageId</span></span>

<span data-ttu-id="c6680-258">指定所產生之套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6680-258">Specifies the name for the resulting package.</span></span> <span data-ttu-id="c6680-259">如果未指定，`pack` 作業會預設為使用 `AssemblyName` 或目錄名稱作為套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6680-259">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="c6680-260">標題</span><span class="sxs-lookup"><span data-stu-id="c6680-260">Title</span></span>

<span data-ttu-id="c6680-261">套件的易記標題，通常會用於 UI 顯示，以及 nuget.org 和 Visual Studio 套件管理員中。</span><span class="sxs-lookup"><span data-stu-id="c6680-261">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="c6680-262">如果未指定，則會改用套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6680-262">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="c6680-263">Authors</span><span class="sxs-lookup"><span data-stu-id="c6680-263">Authors</span></span>

<span data-ttu-id="c6680-264">以分號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些會顯示在 nuget.org 上的 NuGet 元件庫中，並用於相同作者的交互參照封裝。</span><span class="sxs-lookup"><span data-stu-id="c6680-264">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="c6680-265">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="c6680-265">PackageDescription</span></span>

<span data-ttu-id="c6680-266">UI 顯示中的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="c6680-266">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="c6680-267">描述</span><span class="sxs-lookup"><span data-stu-id="c6680-267">Description</span></span>

<span data-ttu-id="c6680-268">組件的完整描述。</span><span class="sxs-lookup"><span data-stu-id="c6680-268">A long description for the assembly.</span></span> <span data-ttu-id="c6680-269">如果 `PackageDescription` 未指定，則此屬性也會用來做為封裝的描述。</span><span class="sxs-lookup"><span data-stu-id="c6680-269">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="c6680-270">著作權</span><span class="sxs-lookup"><span data-stu-id="c6680-270">Copyright</span></span>

<span data-ttu-id="c6680-271">套件的著作權詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c6680-271">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="c6680-272">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="c6680-272">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="c6680-273">布林值，指定在安裝套件時，用戶端是否必須提示取用者接受套件授權。</span><span class="sxs-lookup"><span data-stu-id="c6680-273">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="c6680-274">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c6680-274">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="c6680-275">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="c6680-275">DevelopmentDependency</span></span>

<span data-ttu-id="c6680-276">布林值，指定封裝是否標示為僅限開發的相依性，這可防止封裝當做其他封裝的相依性來包含。</span><span class="sxs-lookup"><span data-stu-id="c6680-276">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="c6680-277">使用 PackageReference (NuGet 4.8 +) ，此旗標也表示編譯時期資產會從編譯中排除。</span><span class="sxs-lookup"><span data-stu-id="c6680-277">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="c6680-278">如需詳細資訊，請參閱 [PackageReference 的 DevelopmentDependency 支援](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="c6680-278">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="c6680-279">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="c6680-279">PackageLicenseExpression</span></span>

<span data-ttu-id="c6680-280">[SPDX 授權識別碼](https://spdx.org/licenses/) \(英文\) 或運算式。</span><span class="sxs-lookup"><span data-stu-id="c6680-280">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="c6680-281">例如： `Apache-2.0` 。</span><span class="sxs-lookup"><span data-stu-id="c6680-281">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="c6680-282">此處有 [SPDX 授權識別碼](https://spdx.org/licenses/)的完整清單。</span><span class="sxs-lookup"><span data-stu-id="c6680-282">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="c6680-283">在使用授權類型運算式時，NuGet.org 只接受 OSI 或 FSF 核准的授權。</span><span class="sxs-lookup"><span data-stu-id="c6680-283">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="c6680-284">授權運算式的確切語法使用 [ABNF](https://tools.ietf.org/html/rfc5234)，如下所述。</span><span class="sxs-lookup"><span data-stu-id="c6680-284">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```abnf
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="c6680-285">一次只能指定 `PackageLicenseExpression`、`PackageLicenseFile` 和 `PackageLicenseUrl` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="c6680-285">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="c6680-286">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="c6680-286">PackageLicenseFile</span></span>

<span data-ttu-id="c6680-287">若您使用未獲指派 SPDX 識別碼的授權，或其為自訂授權，則這會是套件內授權檔案的路徑 (否則，會優先使用 `PackageLicenseExpression`)</span><span class="sxs-lookup"><span data-stu-id="c6680-287">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="c6680-288">取代 `PackageLicenseUrl` 、無法與結合 `PackageLicenseExpression` ，而且需要 Visual Studio 版本15.9.4 和 .net SDK 2.1.502 或2.2.101 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c6680-288">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="c6680-289">您必須明確地將授權檔案新增到專案，以確保其封裝妥當，使用範例：</span><span class="sxs-lookup"><span data-stu-id="c6680-289">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="c6680-290">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="c6680-290">PackageLicenseUrl</span></span>

<span data-ttu-id="c6680-291">適用于封裝之授權的 URL。</span><span class="sxs-lookup"><span data-stu-id="c6680-291">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="c6680-292">(_自 Visual Studio 15.9.4、.NET SDK 2.1.502 及 2.2.101 起淘汰_)</span><span class="sxs-lookup"><span data-stu-id="c6680-292">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageicon"></a><span data-ttu-id="c6680-293">PackageIcon</span><span class="sxs-lookup"><span data-stu-id="c6680-293">PackageIcon</span></span>

<span data-ttu-id="c6680-294">封裝中要當做封裝圖示使用之影像的路徑。</span><span class="sxs-lookup"><span data-stu-id="c6680-294">A path to an image in the package to use as a package icon.</span></span> <span data-ttu-id="c6680-295">閱讀更多[ `icon` 中繼資料](/nuget/reference/nuspec#icon)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c6680-295">Read more about [`icon` metadata](/nuget/reference/nuspec#icon).</span></span> <span data-ttu-id="c6680-296">[PackageIconUrl 已被取代](/nuget/reference/msbuild-targets#packageiconurl)而改用 PackageIcon。</span><span class="sxs-lookup"><span data-stu-id="c6680-296">[PackageIconUrl is deprecated](/nuget/reference/msbuild-targets#packageiconurl) in favor of PackageIcon.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="c6680-297">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="c6680-297">PackageReleaseNotes</span></span>

<span data-ttu-id="c6680-298">套件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c6680-298">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="c6680-299">PackageTags</span><span class="sxs-lookup"><span data-stu-id="c6680-299">PackageTags</span></span>

<span data-ttu-id="c6680-300">以分號分隔的標記清單，用以指定套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-300">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="c6680-301">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="c6680-301">PackageOutputPath</span></span>

<span data-ttu-id="c6680-302">決定要置放所封裝之套件的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="c6680-302">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="c6680-303">預設值為 `$(OutputPath)`。</span><span class="sxs-lookup"><span data-stu-id="c6680-303">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="c6680-304">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="c6680-304">IncludeSymbols</span></span>
<span data-ttu-id="c6680-305">此布林值會指出在封裝專案時，套件是否應該建立額外的符號套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-305">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="c6680-306">符號套件的格式由 `SymbolPackageFormat` 屬性控制。</span><span class="sxs-lookup"><span data-stu-id="c6680-306">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="c6680-307">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="c6680-307">SymbolPackageFormat</span></span>
<span data-ttu-id="c6680-308">指定符號套件的格式。</span><span class="sxs-lookup"><span data-stu-id="c6680-308">Specifies the format of the symbols package.</span></span> <span data-ttu-id="c6680-309">如果是 "symbols.nupkg"，將使用包含 PDB、DLL 和其他輸出檔案的 *.symbols.nupkg* 副檔名建立舊版符號套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-309">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="c6680-310">如果是 "snupkg"，將建立一個包含可攜式 PDB 的 snupkg 符號套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-310">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="c6680-311">預設值為 "symbols.nupkg"。</span><span class="sxs-lookup"><span data-stu-id="c6680-311">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="c6680-312">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="c6680-312">IncludeSource</span></span>

<span data-ttu-id="c6680-313">此布林值會指出封裝處理序是否應該建立來源套件。</span><span class="sxs-lookup"><span data-stu-id="c6680-313">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="c6680-314">來源套件包含程式庫的原始程式碼及 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6680-314">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="c6680-315">原始程式檔會放在所產生之套件檔案中的 `src/ProjectName` 目錄底下。</span><span class="sxs-lookup"><span data-stu-id="c6680-315">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="c6680-316">IsTool</span><span class="sxs-lookup"><span data-stu-id="c6680-316">IsTool</span></span>

<span data-ttu-id="c6680-317">指定是否要將所有輸出檔複製到 *tools* 資料夾，而不是 *lib* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c6680-317">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="c6680-318">這與不同 `DotNetCliTool` ，後者是藉由 `PackageType` 在 *.csproj*檔案中設定來指定。</span><span class="sxs-lookup"><span data-stu-id="c6680-318">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="c6680-319">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="c6680-319">RepositoryUrl</span></span>

<span data-ttu-id="c6680-320">指定存放庫的 URL，此存放庫是套件原始程式碼的所在位置及 (或) 正在建置的來源位置。</span><span class="sxs-lookup"><span data-stu-id="c6680-320">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="c6680-321">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="c6680-321">RepositoryType</span></span>

<span data-ttu-id="c6680-322">指定存放庫的類型。</span><span class="sxs-lookup"><span data-stu-id="c6680-322">Specifies the type of the repository.</span></span> <span data-ttu-id="c6680-323">預設值為 "git"。</span><span class="sxs-lookup"><span data-stu-id="c6680-323">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="c6680-324">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="c6680-324">RepositoryBranch</span></span>
<span data-ttu-id="c6680-325">指定存放庫中來源分支的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6680-325">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="c6680-326">當專案封裝在 NuGet 套件中時，會將它新增至套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c6680-326">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="c6680-327">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="c6680-327">RepositoryCommit</span></span>
<span data-ttu-id="c6680-328">選擇性存放庫認可或變更集，用來指出要建立封裝的來源。</span><span class="sxs-lookup"><span data-stu-id="c6680-328">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="c6680-329">`RepositoryUrl`您也必須指定，才能包含這個屬性。</span><span class="sxs-lookup"><span data-stu-id="c6680-329">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="c6680-330">當專案封裝在 NuGet 套件中時，此認可或變更集會新增至套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c6680-330">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="c6680-331">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="c6680-331">NoPackageAnalysis</span></span>

<span data-ttu-id="c6680-332">指定封裝不應該在建置套件之後執行套件分析。</span><span class="sxs-lookup"><span data-stu-id="c6680-332">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="c6680-333">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="c6680-333">MinClientVersion</span></span>

<span data-ttu-id="c6680-334">指定可安裝此套件的最低 NuGet 用戶端版本，此作業是由 nuget.exe 和 Visual Studio 套件管理員強制執行。</span><span class="sxs-lookup"><span data-stu-id="c6680-334">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="c6680-335">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="c6680-335">IncludeBuildOutput</span></span>

<span data-ttu-id="c6680-336">這個布林值會指定組建輸出元件是否應該封裝到*nupkg*檔中。</span><span class="sxs-lookup"><span data-stu-id="c6680-336">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="c6680-337">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="c6680-337">IncludeContentInPack</span></span>

<span data-ttu-id="c6680-338">此布林值會指定是否有任何類型為 `Content` 的項目會自動包含於所產生的套件中。</span><span class="sxs-lookup"><span data-stu-id="c6680-338">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="c6680-339">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="c6680-339">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="c6680-340">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="c6680-340">BuildOutputTargetFolder</span></span>

<span data-ttu-id="c6680-341">指定要放置輸出組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c6680-341">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="c6680-342">輸出組件 (及其他輸出檔) 會複製到其相關的架構資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c6680-342">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="c6680-343">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="c6680-343">ContentTargetFolders</span></span>

<span data-ttu-id="c6680-344">如果未指定 `PackagePath`，此屬性會指定所有內容檔案應移至的預設位置。</span><span class="sxs-lookup"><span data-stu-id="c6680-344">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="c6680-345">預設值為 "content;contentFiles"。</span><span class="sxs-lookup"><span data-stu-id="c6680-345">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="c6680-346">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="c6680-346">NuspecFile</span></span>

<span data-ttu-id="c6680-347">正用於封裝之 *.nuspec* 檔案的相對或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="c6680-347">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="c6680-348">如果指定 *.nuspec* 檔案，則會**單獨**使用此檔案來封裝資訊，而不會使用專案中的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="c6680-348">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="c6680-349">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="c6680-349">NuspecBasePath</span></span>

<span data-ttu-id="c6680-350">*.nuspec* 檔案的基底路徑。</span><span class="sxs-lookup"><span data-stu-id="c6680-350">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="c6680-351">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="c6680-351">NuspecProperties</span></span>

<span data-ttu-id="c6680-352">以分號分隔的索引鍵=值組清單。</span><span class="sxs-lookup"><span data-stu-id="c6680-352">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="c6680-353">AssemblyInfo 屬性</span><span class="sxs-lookup"><span data-stu-id="c6680-353">AssemblyInfo properties</span></span>

<span data-ttu-id="c6680-354">[組件屬性](../../standard/assembly/set-attributes.md)，通常存在於 AssemblyInfo\*\* 檔案，現在會自動從屬性產生。</span><span class="sxs-lookup"><span data-stu-id="c6680-354">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="c6680-355">每個屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="c6680-355">Properties per attribute</span></span>

<span data-ttu-id="c6680-356">如下表所示，每個屬性都有一個屬性，可控制其內容，另一個則停用其層代：</span><span class="sxs-lookup"><span data-stu-id="c6680-356">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="c6680-357">屬性</span><span class="sxs-lookup"><span data-stu-id="c6680-357">Attribute</span></span>                                                      | <span data-ttu-id="c6680-358">屬性</span><span class="sxs-lookup"><span data-stu-id="c6680-358">Property</span></span>               | <span data-ttu-id="c6680-359">要停用的屬性</span><span class="sxs-lookup"><span data-stu-id="c6680-359">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="c6680-360">注意：</span><span class="sxs-lookup"><span data-stu-id="c6680-360">Notes:</span></span>

- <span data-ttu-id="c6680-361">`AssemblyVersion` 和 `FileVersion` 預設為採用沒有後置詞的 `$(Version)` 值。</span><span class="sxs-lookup"><span data-stu-id="c6680-361">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="c6680-362">例如，如果 `$(Version)` 是 `1.2.3-beta.4`，則此值會是 `1.2.3`。</span><span class="sxs-lookup"><span data-stu-id="c6680-362">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="c6680-363">`InformationalVersion` 預設為 `$(Version)` 的值。</span><span class="sxs-lookup"><span data-stu-id="c6680-363">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="c6680-364">如果有屬性，則 `InformationalVersion` 會附加 `$(SourceRevisionId)`。</span><span class="sxs-lookup"><span data-stu-id="c6680-364">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="c6680-365">可以使用 `IncludeSourceRevisionInInformationalVersion` 來加以停用。</span><span class="sxs-lookup"><span data-stu-id="c6680-365">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="c6680-366">也會針對 NuGet 中繼資料使用 `Copyright` 和 `Description` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c6680-366">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="c6680-367">`Configuration` 與所有建置程序共用，並且是透過 `dotnet` 命令的 `--configuration` 參數來設定。</span><span class="sxs-lookup"><span data-stu-id="c6680-367">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="c6680-368">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="c6680-368">GenerateAssemblyInfo</span></span>

<span data-ttu-id="c6680-369">布林值，啟用或停用所有 AssemblyInfo 產生。</span><span class="sxs-lookup"><span data-stu-id="c6680-369">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="c6680-370">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="c6680-370">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="c6680-371">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="c6680-371">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="c6680-372">產生組件資訊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c6680-372">The path of the generated assembly info file.</span></span> <span data-ttu-id="c6680-373">預設為 `$(IntermediateOutputPath)` (obj) 目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="c6680-373">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
