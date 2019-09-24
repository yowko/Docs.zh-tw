---
title: 適用於 .NET Core 之 csproj 格式的新增項目
description: 深入了解現有和 .NET Core csproj 檔案之間的差異
ms.date: 04/08/2019
ms.openlocfilehash: 89ab22f0c5e69f29ff31e13d46dce8ba278d08da
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216198"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="6d32c-103">適用於 .NET Core 之 csproj 格式的新增項目</span><span class="sxs-lookup"><span data-stu-id="6d32c-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="6d32c-104">本文件概述從 *project.json* 改為使用 *csproj* 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至專案檔的變更。</span><span class="sxs-lookup"><span data-stu-id="6d32c-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="6d32c-105">如需一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="6d32c-106">隱含套件參考</span><span class="sxs-lookup"><span data-stu-id="6d32c-106">Implicit package references</span></span>

<span data-ttu-id="6d32c-107">會根據您專案檔之 `<TargetFramework>` 或 `<TargetFrameworks>` 屬性中指定的目標架構來隱含參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="6d32c-108">如果指定了 `<TargetFramework>`，則會忽略 `<TargetFrameworks>`，與順序無關。</span><span class="sxs-lookup"><span data-stu-id="6d32c-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="6d32c-109">如需詳細資訊，請參閱[套件、中繼套件和架構](../packages.md)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-109">For more information, see [Packages, metapackages and frameworks](../packages.md).</span></span> 

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

### <a name="recommendations"></a><span data-ttu-id="6d32c-110">建議</span><span class="sxs-lookup"><span data-stu-id="6d32c-110">Recommendations</span></span>

<span data-ttu-id="6d32c-111">由於會隱含參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件，因此建議使用下列最佳做法：</span><span class="sxs-lookup"><span data-stu-id="6d32c-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="6d32c-112">以 .NET Core 或 .NET Standard 為目標時，絕不透過專案檔中的 `<PackageReference>` 項目明確參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="6d32c-113">如果您以 .NET Core 為目標時需要特定版本的執行階段，您應該使用專案中的 `<RuntimeFrameworkVersion>` 屬性 (例如 `1.0.4`)，而不是參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  * <span data-ttu-id="6d32c-114">如果您使用[獨立性部署](../deploying/index.md#self-contained-deployments-scd)，並需要 1.0.0 LTS 執行階段的特定更新程式版本，就可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="6d32c-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="6d32c-115">如果您以 .NET Standard 為目標時需要特定版本的 `NETStandard.Library` 中繼套件，您可以使用 `<NetStandardImplicitPackageVersion>` 屬性並設定所需的版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="6d32c-116">請不要在 .NET Framework 專案中明確地新增或更新 `Microsoft.NETCore.App` 或 `NETStandard.Library` 中繼套件的參考。</span><span class="sxs-lookup"><span data-stu-id="6d32c-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="6d32c-117">如果使用 .NET Standard 型 NuGet 套件時需要任何版本的 `NETStandard.Library`，NuGet 會自動安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="6d32c-118">某些套件參考的隱含版本</span><span class="sxs-lookup"><span data-stu-id="6d32c-118">Implicit version for some package references</span></span>

<span data-ttu-id="6d32c-119">[`<PackageReference>`](#packagereference) 的大部分使用方式都需要設定 `Version` 屬性來指定要使用的 NuGet 套件版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="6d32c-120">不過，使用 .NET Core 2.1 或 2.2 並參考 [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) 或 [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage) 時，該屬性是不必要的。</span><span class="sxs-lookup"><span data-stu-id="6d32c-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="6d32c-121">.NET Core SDK 可以自動針對這些套件選取應使用的版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="6d32c-122">建議</span><span class="sxs-lookup"><span data-stu-id="6d32c-122">Recommendation</span></span>

<span data-ttu-id="6d32c-123">參考 `Microsoft.AspNetCore.App` 或 `Microsoft.AspNetCore.All` 套件時，請不要指定其版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="6d32c-124">若指定版本，SDK 可能會產生警告 NETSDK1071。</span><span class="sxs-lookup"><span data-stu-id="6d32c-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="6d32c-125">若要修正此警告，請移除套件版本，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6d32c-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="6d32c-126">已知問題：.NET Core 2.1 SDK 僅在專案同時使用 Microsoft.NET.Sdk.Web 時才支援此語法。</span><span class="sxs-lookup"><span data-stu-id="6d32c-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="6d32c-127">此問題已在 .NET Core 2.2 SDK 中解決。</span><span class="sxs-lookup"><span data-stu-id="6d32c-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="6d32c-128">這些針對 ASP.NET Core 中繼套件的參考，具有和大部分的一般 NuGet 套件些微不同的行為。</span><span class="sxs-lookup"><span data-stu-id="6d32c-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="6d32c-129">使用這些中繼套件之應用程式的[架構相依部署](../deploying/index.md#framework-dependent-deployments-fdd)會自動利用 ASP.NET Core 共用架構的優點。</span><span class="sxs-lookup"><span data-stu-id="6d32c-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="6d32c-130">當您使用中繼套件時，系統**不會**搭配應用程式部署來自所參考之 ASP.NET Core NuGet 套件的任何資產；ASP.NET Core 共用架構會包含這些資產。</span><span class="sxs-lookup"><span data-stu-id="6d32c-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="6d32c-131">共用架構中的資產會針對目標平台最佳化，以改善應用程式啟動時間。</span><span class="sxs-lookup"><span data-stu-id="6d32c-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="6d32c-132">如需共用架構的詳細資訊，請參閱 [.NET Core 發佈封裝](../build/distribution-packaging.md)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="6d32c-133">如果「已指定」某個版本，系統會將它視為 ASP.NET Core 共用架構適用於架構相依部署的「最小」版本，以及獨立式部署的「確切」版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="6d32c-134">這可能會導致下列結果：</span><span class="sxs-lookup"><span data-stu-id="6d32c-134">This can have the following consequences:</span></span>

* <span data-ttu-id="6d32c-135">如果安裝在伺服器上的 ASP.NET Core 版本小於 PackageReference 上所指定的版本，.NET Core 處理序將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="6d32c-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="6d32c-136">針對中繼套件的更新通常會在於裝載環境 (例如 Azure) 中推出之前，先在 NuGet.org 上提供使用。</span><span class="sxs-lookup"><span data-stu-id="6d32c-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="6d32c-137">將 PackageReference 上的版本更新為 ASP.NET Core 的版本，可能會導致已部署的應用程式發生失敗。</span><span class="sxs-lookup"><span data-stu-id="6d32c-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
* <span data-ttu-id="6d32c-138">如果應用程式是以[獨立式部署](../deploying/index.md#self-contained-deployments-scd)的形式部署，該應用程式可能不會包含針對 .NET Core 的最新安全性更新。</span><span class="sxs-lookup"><span data-stu-id="6d32c-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="6d32c-139">沒有指定版本時，獨立式部署中的 SDK 可以自動包含最新版本的 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="6d32c-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="6d32c-140">.NET Core 專案中包含預設編譯</span><span class="sxs-lookup"><span data-stu-id="6d32c-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="6d32c-141">隨著改為使用最新 SDK 版本中的 *csproj* 格式，編譯項目的預設包含項目和排除項目以及內嵌資源都已移至 SDK 屬性檔。</span><span class="sxs-lookup"><span data-stu-id="6d32c-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="6d32c-142">這表示您不再需要於專案檔中指定這些項目。</span><span class="sxs-lookup"><span data-stu-id="6d32c-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="6d32c-143">這樣做的主要原因是為了讓專案檔更為簡潔。</span><span class="sxs-lookup"><span data-stu-id="6d32c-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="6d32c-144">SDK 中的預設值應該涵蓋最常見的使用案例，而不需要在每個建立的專案中重複這些項目。</span><span class="sxs-lookup"><span data-stu-id="6d32c-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="6d32c-145">這會產生較小的專案檔，而更容易了解及視需要手動編輯。</span><span class="sxs-lookup"><span data-stu-id="6d32c-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="6d32c-146">下表顯示 SDK 中會同時包含及排除的元素與 [Glob (英文)](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="6d32c-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="6d32c-147">元素</span><span class="sxs-lookup"><span data-stu-id="6d32c-147">Element</span></span>           | <span data-ttu-id="6d32c-148">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="6d32c-148">Include glob</span></span>                              | <span data-ttu-id="6d32c-149">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="6d32c-149">Exclude glob</span></span>                                                  | <span data-ttu-id="6d32c-150">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="6d32c-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="6d32c-151">編譯</span><span class="sxs-lookup"><span data-stu-id="6d32c-151">Compile</span></span>           | <span data-ttu-id="6d32c-152">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="6d32c-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="6d32c-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6d32c-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="6d32c-154">N/A</span><span class="sxs-lookup"><span data-stu-id="6d32c-154">N/A</span></span>                      |
| <span data-ttu-id="6d32c-155">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="6d32c-155">EmbeddedResource</span></span>  | <span data-ttu-id="6d32c-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="6d32c-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="6d32c-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6d32c-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6d32c-158">N/A</span><span class="sxs-lookup"><span data-stu-id="6d32c-158">N/A</span></span>                      |
| <span data-ttu-id="6d32c-159">None</span><span class="sxs-lookup"><span data-stu-id="6d32c-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="6d32c-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6d32c-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6d32c-161">\*\*/\*.cs、\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="6d32c-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="6d32c-162">**排除 Glob** 一律會排除 `./bin` 和 `./obj` 資料夾，其分別由 `$(BaseOutputPath)` 和 `$(BaseIntermediateOutputPath)` MSBuild 屬性所代表。</span><span class="sxs-lookup"><span data-stu-id="6d32c-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="6d32c-163">整體而言，所有排除都是由 `$(DefaultItemExcludes)` 所代表。</span><span class="sxs-lookup"><span data-stu-id="6d32c-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="6d32c-164">如果您的專案有 Glob，而且您嘗試使用最新的 SDK 建置專案，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="6d32c-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="6d32c-165">包含了重複的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="6d32c-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="6d32c-166">.NET SDK 預設會包含您專案目錄中的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="6d32c-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="6d32c-167">您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。</span><span class="sxs-lookup"><span data-stu-id="6d32c-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="6d32c-168">若要解決此錯誤，您可以明確移除符合上表所列項目的 `Compile` 項目，或將 `<EnableDefaultCompileItems>` 屬性設定為 `false`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6d32c-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="6d32c-169">將此屬性設定為 `false` 會停用隱含包含項目，還原成必須在專案中指定預設 Glob 的舊版 SDK 行為。</span><span class="sxs-lookup"><span data-stu-id="6d32c-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="6d32c-170">這項變更不會修改其他包含項目的主要機制。</span><span class="sxs-lookup"><span data-stu-id="6d32c-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="6d32c-171">不過，如果您想要指定某些檔案由應用程式發行，您仍然可以使用 *csproj* 中已知的機制來執行這項作業 (例如 `<Content>` 項目)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="6d32c-172">`<EnableDefaultCompileItems>` 只會停用 `Compile` GLOB，而不會影響隱含 `None` GLOB 這類其他 GLOB，後者也會套用至 \*.cs 項目。</span><span class="sxs-lookup"><span data-stu-id="6d32c-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="6d32c-173">因此，方案總管會繼續將 \*.cs 項目顯示為包含為 `None` 項目之專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="6d32c-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="6d32c-174">透過類似的方式，您可以將 `<EnableDefaultNoneItems>` 設為 False 以停用隱含 `None` GLOB，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6d32c-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="6d32c-175">若要停用**所有隱含 GLOB**，您可以將 `<EnableDefaultItems>` 屬性設定為 `false`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6d32c-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="6d32c-176">如何以 MSBuild 查看專案的方式查看整個專案</span><span class="sxs-lookup"><span data-stu-id="6d32c-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="6d32c-177">雖然那些 csproj 變更可大幅簡化專案檔，在包括 SDK 和其目標之後，您可能會想要以 MSBuild 查看專案的方式查看完全展開的專案。</span><span class="sxs-lookup"><span data-stu-id="6d32c-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="6d32c-178">使用 [`dotnet msbuild`](dotnet-msbuild.md) 命令的 [`/pp` 切換](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) 對專案進行前置處理，它可以在不需要實際建置專案的情況下，顯示匯入的檔案、檔案的來源，以及該檔案對組建的貢獻：</span><span class="sxs-lookup"><span data-stu-id="6d32c-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="6d32c-179">如果專案具有多個目標架構，系統應該會透過將它們的其中之一指定為 MSBuild 屬性，來使命令的結果專注於該目標架構：</span><span class="sxs-lookup"><span data-stu-id="6d32c-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="6d32c-180">新增項目</span><span class="sxs-lookup"><span data-stu-id="6d32c-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="6d32c-181">Sdk 屬性</span><span class="sxs-lookup"><span data-stu-id="6d32c-181">Sdk attribute</span></span>

<span data-ttu-id="6d32c-182">*.csproj* 檔案的根 `<Project>` 元素有一個新屬性，稱為 `Sdk`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="6d32c-183">`Sdk` 會指定專案將使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="6d32c-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="6d32c-184">如[分層文件](cli-msbuild-architecture.md)所述，SDK 是可建置 .NET Core 程式碼的一組 MSBuild [工作](/visualstudio/msbuild/msbuild-tasks)和[目標](/visualstudio/msbuild/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="6d32c-185">下列 Sdk 適用于 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="6d32c-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="6d32c-186">識別碼為 `Microsoft.NET.Sdk` 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6d32c-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="6d32c-187">識別碼為 `Microsoft.NET.Sdk.Web` 的 .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="6d32c-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="6d32c-188">識別碼為 `Microsoft.NET.Sdk.Razor` 的 .NET Core Razor 類別庫 SDK</span><span class="sxs-lookup"><span data-stu-id="6d32c-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="6d32c-189">識別碼為的`Microsoft.NET.Sdk.Worker` .net core 背景工作角色服務（自 .net core 3.0 起）</span><span class="sxs-lookup"><span data-stu-id="6d32c-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="6d32c-190">具有識別碼的`Microsoft.NET.Sdk.WindowsDesktop` .net Core WinForms 和 WPF （自 .net core 3.0 起）</span><span class="sxs-lookup"><span data-stu-id="6d32c-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="6d32c-191">您必須在 `<Project>` 項目中將 `Sdk` 屬性設定為上述其中一個識別碼，才能使用 .NET Core 工具並建置您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d32c-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="6d32c-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="6d32c-192">PackageReference</span></span>

<span data-ttu-id="6d32c-193">`<PackageReference>` 項目元素會[在專案中指定 NuGet 相依性](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="6d32c-194">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="6d32c-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="6d32c-195">版本</span><span class="sxs-lookup"><span data-stu-id="6d32c-195">Version</span></span>

<span data-ttu-id="6d32c-196">必要的 `Version` 屬性會指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="6d32c-197">該屬性採用 [NuGet 版本控制](/nuget/reference/package-versioning#version-ranges-and-wildcards)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="6d32c-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="6d32c-198">預設行為是確切的版本相符。</span><span class="sxs-lookup"><span data-stu-id="6d32c-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="6d32c-199">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。</span><span class="sxs-lookup"><span data-stu-id="6d32c-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="6d32c-200">IncludeAssets、ExcludeAssets 和 PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="6d32c-200">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="6d32c-201">`IncludeAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="6d32c-202">根據預設，所有套件資產均包含在內。</span><span class="sxs-lookup"><span data-stu-id="6d32c-202">By default, all package assets are included.</span></span>

<span data-ttu-id="6d32c-203">`ExcludeAssets` 屬性指定不應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="6d32c-204">`PrivateAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定但未流向下一個專案的套件)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="6d32c-205">根據預設，當此屬性不存在時，`Analyzers`、`Build` 和 `ContentFiles` 會是私人資產。</span><span class="sxs-lookup"><span data-stu-id="6d32c-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="6d32c-206">`PrivateAssets` 相當於 *project.json*/*xproj* `SuppressParent` 項目。</span><span class="sxs-lookup"><span data-stu-id="6d32c-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="6d32c-207">這些屬性可包含下列一或多個項目，若列出不只一個，則以分號 `;` 字元分隔：</span><span class="sxs-lookup"><span data-stu-id="6d32c-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="6d32c-208">`Compile` – lib 資料夾的內容可供編譯。</span><span class="sxs-lookup"><span data-stu-id="6d32c-208">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="6d32c-209">`Runtime` – 會散發 runtime 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="6d32c-209">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="6d32c-210">`ContentFiles` - 會使用 *contentfiles* 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="6d32c-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="6d32c-211">`Build` – 會使用組建資料夾中的屬性/目標。</span><span class="sxs-lookup"><span data-stu-id="6d32c-211">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="6d32c-212">`Native` – 原生資產內容會複製到執行階段輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d32c-212">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="6d32c-213">`Analyzers` – 會使用分析器。</span><span class="sxs-lookup"><span data-stu-id="6d32c-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="6d32c-214">另外，該屬性也可以包含︰</span><span class="sxs-lookup"><span data-stu-id="6d32c-214">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="6d32c-215">`None` – 未使用任何資產。</span><span class="sxs-lookup"><span data-stu-id="6d32c-215">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="6d32c-216">`All` – 會使用所有資產。</span><span class="sxs-lookup"><span data-stu-id="6d32c-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="6d32c-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="6d32c-217">DotNetCliToolReference</span></span>
<span data-ttu-id="6d32c-218">`<DotNetCliToolReference>` 項目元素指定使用者想要在專案內容中還原的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="6d32c-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="6d32c-219">它會取代 *project.json* 中的 `tools` 節點。</span><span class="sxs-lookup"><span data-stu-id="6d32c-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="6d32c-220">版本</span><span class="sxs-lookup"><span data-stu-id="6d32c-220">Version</span></span>

<span data-ttu-id="6d32c-221">`Version` 指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="6d32c-222">該屬性採用 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="6d32c-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="6d32c-223">預設行為是確切的版本相符。</span><span class="sxs-lookup"><span data-stu-id="6d32c-223">The default behavior is an exact version match.</span></span> <span data-ttu-id="6d32c-224">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。</span><span class="sxs-lookup"><span data-stu-id="6d32c-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="6d32c-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="6d32c-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="6d32c-226">`<RuntimeIdentifiers>` 屬性元素可讓您針對專案指定以分號分隔的[執行階段識別碼 (RID)](../rid-catalog.md) 清單。</span><span class="sxs-lookup"><span data-stu-id="6d32c-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="6d32c-227">RID 允許發行獨立部署。</span><span class="sxs-lookup"><span data-stu-id="6d32c-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="6d32c-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="6d32c-228">RuntimeIdentifier</span></span>

<span data-ttu-id="6d32c-229">`<RuntimeIdentifier>` 屬性元素可讓您針對專案只指定一個[執行階段識別碼 (RID)](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="6d32c-230">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="6d32c-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="6d32c-231">如果您需要發佈以供多個執行階段使用，請改用 `<RuntimeIdentifiers>` (複數)。</span><span class="sxs-lookup"><span data-stu-id="6d32c-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="6d32c-232">只需要單一執行階段時，`<RuntimeIdentifier>` 可提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="6d32c-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="6d32c-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="6d32c-233">PackageTargetFallback</span></span>

<span data-ttu-id="6d32c-234">`<PackageTargetFallback>` 屬性元素可讓您指定一組要在還原套件時使用的相容目標。</span><span class="sxs-lookup"><span data-stu-id="6d32c-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="6d32c-235">其設計目的是為了讓使用 dotnet [TxM (目標 x Moniker)](/nuget/schema/target-frameworks) 的套件能和未宣告 dotnet TxM 的套件一起運作。</span><span class="sxs-lookup"><span data-stu-id="6d32c-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="6d32c-236">如果您的專案使用 dotnet TxM，除非您將 `<PackageTargetFallback>` 新增至專案，以讓非 dotnet 平台變成能與 dotnet 相容，否則其相依的所有套件也必須要有 dotnet TxM。</span><span class="sxs-lookup"><span data-stu-id="6d32c-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="6d32c-237">下列範例可為專案中的所有目標提供後援：</span><span class="sxs-lookup"><span data-stu-id="6d32c-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="6d32c-238">下列範例只會為 `netcoreapp2.1` 目標指定後援︰</span><span class="sxs-lookup"><span data-stu-id="6d32c-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="6d32c-239">NuGet 中繼資料屬性</span><span class="sxs-lookup"><span data-stu-id="6d32c-239">NuGet metadata properties</span></span>

<span data-ttu-id="6d32c-240">隨著改為使用 MSBuild，我們已經將封裝 NuGet 套件時使用的輸入中繼資料從 *project.json* 移動到 *.csproj* 檔。</span><span class="sxs-lookup"><span data-stu-id="6d32c-240">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="6d32c-241">此輸入是 MSBuild 屬性，因此必須移至 `<PropertyGroup>` 群組。</span><span class="sxs-lookup"><span data-stu-id="6d32c-241">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="6d32c-242">使用 `dotnet pack` 命令或屬於 SDK 一部分的 `Pack` MSBuild 目標時，會將下列的屬性清單當成封裝處理序的輸入使用。</span><span class="sxs-lookup"><span data-stu-id="6d32c-242">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="6d32c-243">IsPackable</span><span class="sxs-lookup"><span data-stu-id="6d32c-243">IsPackable</span></span>

<span data-ttu-id="6d32c-244">布林值，指定是否可封裝專案。</span><span class="sxs-lookup"><span data-stu-id="6d32c-244">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="6d32c-245">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-245">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="6d32c-246">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="6d32c-246">PackageVersion</span></span>

<span data-ttu-id="6d32c-247">指定所產生之套件的版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-247">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="6d32c-248">接受所有形式的 NuGet 版本字串。</span><span class="sxs-lookup"><span data-stu-id="6d32c-248">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="6d32c-249">預設為 `$(Version)` 的值，也就是專案中的屬性 `Version`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-249">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="6d32c-250">PackageId</span><span class="sxs-lookup"><span data-stu-id="6d32c-250">PackageId</span></span>

<span data-ttu-id="6d32c-251">指定所產生之套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d32c-251">Specifies the name for the resulting package.</span></span> <span data-ttu-id="6d32c-252">如果未指定，`pack` 作業會預設為使用 `AssemblyName` 或目錄名稱作為套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d32c-252">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="6d32c-253">標題</span><span class="sxs-lookup"><span data-stu-id="6d32c-253">Title</span></span>

<span data-ttu-id="6d32c-254">套件的易記標題，通常會用於 UI 顯示，以及 nuget.org 和 Visual Studio 套件管理員中。</span><span class="sxs-lookup"><span data-stu-id="6d32c-254">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="6d32c-255">如果未指定，則會改用套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="6d32c-255">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="6d32c-256">作者</span><span class="sxs-lookup"><span data-stu-id="6d32c-256">Authors</span></span>

<span data-ttu-id="6d32c-257">以分號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些名稱會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-257">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="6d32c-258">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="6d32c-258">PackageDescription</span></span>

<span data-ttu-id="6d32c-259">UI 顯示中的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="6d32c-259">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="6d32c-260">描述</span><span class="sxs-lookup"><span data-stu-id="6d32c-260">Description</span></span>

<span data-ttu-id="6d32c-261">組件的完整描述。</span><span class="sxs-lookup"><span data-stu-id="6d32c-261">A long description for the assembly.</span></span> <span data-ttu-id="6d32c-262">如果未指定 `PackageDescription`，則此屬性也會用來作為套件的描述。</span><span class="sxs-lookup"><span data-stu-id="6d32c-262">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="6d32c-263">Copyright</span><span class="sxs-lookup"><span data-stu-id="6d32c-263">Copyright</span></span>

<span data-ttu-id="6d32c-264">套件的著作權詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6d32c-264">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="6d32c-265">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="6d32c-265">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="6d32c-266">布林值，指定在安裝套件時，用戶端是否必須提示取用者接受套件授權。</span><span class="sxs-lookup"><span data-stu-id="6d32c-266">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="6d32c-267">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-267">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="6d32c-268">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="6d32c-268">PackageLicenseExpression</span></span>

<span data-ttu-id="6d32c-269">[SPDX 授權識別碼](https://spdx.org/licenses/) \(英文\) 或運算式。</span><span class="sxs-lookup"><span data-stu-id="6d32c-269">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="6d32c-270">例如，`Apache-2.0`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-270">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="6d32c-271">此處有 [SPDX 授權識別碼](https://spdx.org/licenses/)的完整清單。</span><span class="sxs-lookup"><span data-stu-id="6d32c-271">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="6d32c-272">在使用授權類型運算式時，NuGet.org 只接受 OSI 或 FSF 核准的授權。</span><span class="sxs-lookup"><span data-stu-id="6d32c-272">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="6d32c-273">授權運算式的確切語法使用 [ABNF](https://tools.ietf.org/html/rfc5234)，如下所述。</span><span class="sxs-lookup"><span data-stu-id="6d32c-273">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```cli
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
> <span data-ttu-id="6d32c-274">一次只能指定 `PackageLicenseExpression`、`PackageLicenseFile` 和 `PackageLicenseUrl` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="6d32c-274">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="6d32c-275">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="6d32c-275">PackageLicenseFile</span></span>

<span data-ttu-id="6d32c-276">若您使用未獲指派 SPDX 識別碼的授權，或其為自訂授權，則這會是套件內授權檔案的路徑 (否則，會優先使用 `PackageLicenseExpression`)</span><span class="sxs-lookup"><span data-stu-id="6d32c-276">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="6d32c-277">這會取代 `PackageLicenseUrl`，不能與 `PackageLicenseExpression` 合併，並需要 Visual Studio 15.9.4、.NET SDK 2.1.502 或 2.2.101 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="6d32c-277">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="6d32c-278">您必須明確地將授權檔案新增到專案，以確保其封裝妥當，使用範例：</span><span class="sxs-lookup"><span data-stu-id="6d32c-278">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="6d32c-279">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="6d32c-279">PackageLicenseUrl</span></span>

<span data-ttu-id="6d32c-280">適用於套件的授權 URL。</span><span class="sxs-lookup"><span data-stu-id="6d32c-280">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="6d32c-281">(_自 Visual Studio 15.9.4、.NET SDK 2.1.502 及 2.2.101 起淘汰_)</span><span class="sxs-lookup"><span data-stu-id="6d32c-281">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="6d32c-282">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="6d32c-282">PackageIconUrl</span></span>

<span data-ttu-id="6d32c-283">具有透明背景之 64x64 映像的 URL，該映像會用作套件在 UI 顯示中的圖示。</span><span class="sxs-lookup"><span data-stu-id="6d32c-283">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="6d32c-284">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="6d32c-284">PackageReleaseNotes</span></span>

<span data-ttu-id="6d32c-285">套件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="6d32c-285">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="6d32c-286">PackageTags</span><span class="sxs-lookup"><span data-stu-id="6d32c-286">PackageTags</span></span>

<span data-ttu-id="6d32c-287">以分號分隔的標記清單，用以指定套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-287">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="6d32c-288">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="6d32c-288">PackageOutputPath</span></span>

<span data-ttu-id="6d32c-289">決定要置放所封裝之套件的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="6d32c-289">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="6d32c-290">預設為 `$(OutputPath)`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-290">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="6d32c-291">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="6d32c-291">IncludeSymbols</span></span>
<span data-ttu-id="6d32c-292">此布林值會指出在封裝專案時，套件是否應該建立額外的符號套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-292">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="6d32c-293">符號套件的格式由 `SymbolPackageFormat` 屬性控制。</span><span class="sxs-lookup"><span data-stu-id="6d32c-293">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="6d32c-294">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="6d32c-294">SymbolPackageFormat</span></span>
<span data-ttu-id="6d32c-295">指定符號套件的格式。</span><span class="sxs-lookup"><span data-stu-id="6d32c-295">Specifies the format of the symbols package.</span></span> <span data-ttu-id="6d32c-296">如果是 "symbols.nupkg"，將使用包含 PDB、DLL 和其他輸出檔案的 *.symbols.nupkg* 副檔名建立舊版符號套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-296">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="6d32c-297">如果是 "snupkg"，將建立一個包含可攜式 PDB 的 snupkg 符號套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-297">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="6d32c-298">預設值為 "symbols.nupkg"。</span><span class="sxs-lookup"><span data-stu-id="6d32c-298">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="6d32c-299">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="6d32c-299">IncludeSource</span></span>

<span data-ttu-id="6d32c-300">此布林值會指出封裝處理序是否應該建立來源套件。</span><span class="sxs-lookup"><span data-stu-id="6d32c-300">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="6d32c-301">來源套件包含程式庫的原始程式碼及 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d32c-301">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="6d32c-302">原始程式檔會放在所產生之套件檔案中的 `src/ProjectName` 目錄底下。</span><span class="sxs-lookup"><span data-stu-id="6d32c-302">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="6d32c-303">IsTool</span><span class="sxs-lookup"><span data-stu-id="6d32c-303">IsTool</span></span>

<span data-ttu-id="6d32c-304">指定是否要將所有輸出檔複製到 *tools* 資料夾，而不是 *lib* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d32c-304">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="6d32c-305">請注意，這與 `DotNetCliTool` 不同，該項目是藉由在 *.csproj* 檔案中設定 `PackageType` 所指定。</span><span class="sxs-lookup"><span data-stu-id="6d32c-305">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="6d32c-306">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="6d32c-306">RepositoryUrl</span></span>

<span data-ttu-id="6d32c-307">指定存放庫的 URL，此存放庫是套件原始程式碼的所在位置及 (或) 正在建置的來源位置。</span><span class="sxs-lookup"><span data-stu-id="6d32c-307">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="6d32c-308">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="6d32c-308">RepositoryType</span></span>

<span data-ttu-id="6d32c-309">指定存放庫的類型。</span><span class="sxs-lookup"><span data-stu-id="6d32c-309">Specifies the type of the repository.</span></span> <span data-ttu-id="6d32c-310">預設值為 "git"。</span><span class="sxs-lookup"><span data-stu-id="6d32c-310">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="6d32c-311">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="6d32c-311">NoPackageAnalysis</span></span>

<span data-ttu-id="6d32c-312">指定封裝不應該在建置套件之後執行套件分析。</span><span class="sxs-lookup"><span data-stu-id="6d32c-312">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="6d32c-313">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="6d32c-313">MinClientVersion</span></span>

<span data-ttu-id="6d32c-314">指定可安裝此套件的最低 NuGet 用戶端版本，此作業是由 nuget.exe 和 Visual Studio 套件管理員強制執行。</span><span class="sxs-lookup"><span data-stu-id="6d32c-314">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="6d32c-315">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="6d32c-315">IncludeBuildOutput</span></span>

<span data-ttu-id="6d32c-316">此布林值會指定是否應該將建置輸出組建封裝成 *.nupkg* 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d32c-316">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="6d32c-317">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="6d32c-317">IncludeContentInPack</span></span>

<span data-ttu-id="6d32c-318">此布林值會指定是否有任何類型為 `Content` 的項目會自動包含於所產生的套件中。</span><span class="sxs-lookup"><span data-stu-id="6d32c-318">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="6d32c-319">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-319">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="6d32c-320">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="6d32c-320">BuildOutputTargetFolder</span></span>

<span data-ttu-id="6d32c-321">指定要放置輸出組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d32c-321">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="6d32c-322">輸出組件 (及其他輸出檔) 會複製到其相關的架構資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6d32c-322">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="6d32c-323">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="6d32c-323">ContentTargetFolders</span></span>

<span data-ttu-id="6d32c-324">如果未指定 `PackagePath`，此屬性會指定所有內容檔案應移至的預設位置。</span><span class="sxs-lookup"><span data-stu-id="6d32c-324">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="6d32c-325">預設值為 "content;contentFiles"。</span><span class="sxs-lookup"><span data-stu-id="6d32c-325">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="6d32c-326">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="6d32c-326">NuspecFile</span></span>

<span data-ttu-id="6d32c-327">正用於封裝之 *.nuspec* 檔案的相對或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="6d32c-327">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="6d32c-328">如果指定 *.nuspec* 檔案，則會**單獨**使用此檔案來封裝資訊，而不會使用專案中的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="6d32c-328">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="6d32c-329">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="6d32c-329">NuspecBasePath</span></span>

<span data-ttu-id="6d32c-330">*.nuspec* 檔案的基底路徑。</span><span class="sxs-lookup"><span data-stu-id="6d32c-330">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="6d32c-331">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="6d32c-331">NuspecProperties</span></span>

<span data-ttu-id="6d32c-332">以分號分隔的索引鍵=值組清單。</span><span class="sxs-lookup"><span data-stu-id="6d32c-332">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="6d32c-333">AssemblyInfo 屬性</span><span class="sxs-lookup"><span data-stu-id="6d32c-333">AssemblyInfo properties</span></span>

<span data-ttu-id="6d32c-334">[組件屬性](../../standard/assembly/set-attributes.md)，通常存在於 AssemblyInfo 檔案，現在會自動從屬性產生。</span><span class="sxs-lookup"><span data-stu-id="6d32c-334">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="6d32c-335">每個屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="6d32c-335">Properties per attribute</span></span>

<span data-ttu-id="6d32c-336">每個屬性 (Attribute) 有一個屬性 (Property)，控制其內容，另一個則是停用其產生，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="6d32c-336">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="6d32c-337">屬性</span><span class="sxs-lookup"><span data-stu-id="6d32c-337">Attribute</span></span>                                                      | <span data-ttu-id="6d32c-338">屬性</span><span class="sxs-lookup"><span data-stu-id="6d32c-338">Property</span></span>               | <span data-ttu-id="6d32c-339">要停用的屬性</span><span class="sxs-lookup"><span data-stu-id="6d32c-339">Property to disable</span></span>                             |
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

<span data-ttu-id="6d32c-340">附註：</span><span class="sxs-lookup"><span data-stu-id="6d32c-340">Notes:</span></span>

* <span data-ttu-id="6d32c-341">`AssemblyVersion` 和 `FileVersion` 預設為採用沒有後置詞的 `$(Version)` 值。</span><span class="sxs-lookup"><span data-stu-id="6d32c-341">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="6d32c-342">例如，如果 `$(Version)` 是 `1.2.3-beta.4`，則此值會是 `1.2.3`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-342">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="6d32c-343">`InformationalVersion` 預設為 `$(Version)` 的值。</span><span class="sxs-lookup"><span data-stu-id="6d32c-343">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="6d32c-344">如果有屬性，則 `InformationalVersion` 會附加 `$(SourceRevisionId)`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-344">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="6d32c-345">可以使用 `IncludeSourceRevisionInInformationalVersion` 來加以停用。</span><span class="sxs-lookup"><span data-stu-id="6d32c-345">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="6d32c-346">也會針對 NuGet 中繼資料使用 `Copyright` 和 `Description` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6d32c-346">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="6d32c-347">`Configuration` 與所有建置程序共用，並且是透過 `dotnet` 命令的 `--configuration` 參數來設定。</span><span class="sxs-lookup"><span data-stu-id="6d32c-347">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="6d32c-348">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="6d32c-348">GenerateAssemblyInfo</span></span>

<span data-ttu-id="6d32c-349">布林值，啟用或停用所有 AssemblyInfo 產生。</span><span class="sxs-lookup"><span data-stu-id="6d32c-349">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="6d32c-350">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6d32c-350">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="6d32c-351">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="6d32c-351">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="6d32c-352">產生組件資訊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6d32c-352">The path of the generated assembly info file.</span></span> <span data-ttu-id="6d32c-353">預設為 `$(IntermediateOutputPath)` (obj) 目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="6d32c-353">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
