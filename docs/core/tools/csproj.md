---
title: 適用於 .NET Core 之 csproj 格式的新增項目
description: 深入了解現有和 .NET Core csproj 檔案之間的差異
author: blackdwarf
ms.date: 09/22/2017
ms.openlocfilehash: bc81dc5c201fea6caa752248c2b59636bd7465ec
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286568"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="99d1d-103">適用於 .NET Core 之 csproj 格式的新增項目</span><span class="sxs-lookup"><span data-stu-id="99d1d-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="99d1d-104">本文件概述從 *project.json* 改為使用 *csproj* 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至專案檔的變更。</span><span class="sxs-lookup"><span data-stu-id="99d1d-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="99d1d-105">如需一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="99d1d-106">隱含套件參考</span><span class="sxs-lookup"><span data-stu-id="99d1d-106">Implicit package references</span></span>
<span data-ttu-id="99d1d-107">會根據您專案檔之 `<TargetFramework>` 或 `<TargetFrameworks>` 屬性中指定的目標架構來隱含參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="99d1d-108">如果指定了 `<TargetFramework>`，則會忽略 `<TargetFrameworks>`，與順序無關。</span><span class="sxs-lookup"><span data-stu-id="99d1d-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="99d1d-109">建議</span><span class="sxs-lookup"><span data-stu-id="99d1d-109">Recommendations</span></span>
<span data-ttu-id="99d1d-110">由於會隱含參考 `Microsoft.NETCore.App` 或 `NetStandard.Library` 中繼套件，因此建議使用下列最佳做法：</span><span class="sxs-lookup"><span data-stu-id="99d1d-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="99d1d-111">以 .NET Core 或 .NET Standard 為目標時，絕不透過專案檔中的 `<PackageReference>` 項目明確參考 `Microsoft.NETCore.App` 或 `NetStandard.Library` 中繼套件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="99d1d-112">如果您以 .NET Core 為目標時需要特定版本的執行階段，您應該使用專案中的 `<RuntimeFrameworkVersion>` 屬性 (例如 `1.0.4`)，而不是參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="99d1d-113">如果您使用[獨立性部署](../deploying/index.md#self-contained-deployments-scd)，並需要 1.0.0 LTS 執行階段的特定更新程式版本，就可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="99d1d-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="99d1d-114">如果您以 .NET Standard 為目標時需要特定版本的 `NetStandard.Library` 中繼套件，您可以使用 `<NetStandardImplicitPackageVersion>` 屬性並設定所需的版本。</span><span class="sxs-lookup"><span data-stu-id="99d1d-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="99d1d-115">請不要在 .NET Framework 專案中明確地新增或更新 `Microsoft.NETCore.App` 或 `NetStandard.Library` 中繼套件的參考。</span><span class="sxs-lookup"><span data-stu-id="99d1d-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="99d1d-116">如果使用 .NET Standard 型 NuGet 套件時需要任何版本的 `NetStandard.Library`，NuGet 會自動安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="99d1d-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="99d1d-117">.NET Core 專案中包含預設編譯</span><span class="sxs-lookup"><span data-stu-id="99d1d-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="99d1d-118">隨著改為使用最新 SDK 版本中的 *csproj* 格式，編譯項目的預設包含項目和排除項目以及內嵌資源都已移至 SDK 屬性檔。</span><span class="sxs-lookup"><span data-stu-id="99d1d-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="99d1d-119">這表示您不再需要於專案檔中指定這些項目。</span><span class="sxs-lookup"><span data-stu-id="99d1d-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="99d1d-120">這樣做的主要原因是為了讓專案檔更為簡潔。</span><span class="sxs-lookup"><span data-stu-id="99d1d-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="99d1d-121">SDK 中的預設值應該涵蓋最常見的使用案例，而不需要在每個建立的專案中重複這些項目。</span><span class="sxs-lookup"><span data-stu-id="99d1d-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="99d1d-122">這會產生較小的專案檔，而更容易了解及視需要手動編輯。</span><span class="sxs-lookup"><span data-stu-id="99d1d-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="99d1d-123">下表顯示 SDK 中會同時包含及排除的元素與 [Glob (英文)](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="99d1d-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="99d1d-124">元素</span><span class="sxs-lookup"><span data-stu-id="99d1d-124">Element</span></span>           | <span data-ttu-id="99d1d-125">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="99d1d-125">Include glob</span></span>                              | <span data-ttu-id="99d1d-126">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="99d1d-126">Exclude glob</span></span>                                                  | <span data-ttu-id="99d1d-127">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="99d1d-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="99d1d-128">編譯</span><span class="sxs-lookup"><span data-stu-id="99d1d-128">Compile</span></span>           | <span data-ttu-id="99d1d-129">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="99d1d-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="99d1d-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="99d1d-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="99d1d-131">N/A</span><span class="sxs-lookup"><span data-stu-id="99d1d-131">N/A</span></span>                        |
| <span data-ttu-id="99d1d-132">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="99d1d-132">EmbeddedResource</span></span>  | <span data-ttu-id="99d1d-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="99d1d-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="99d1d-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="99d1d-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="99d1d-135">N/A</span><span class="sxs-lookup"><span data-stu-id="99d1d-135">N/A</span></span>                        |
| <span data-ttu-id="99d1d-136">無</span><span class="sxs-lookup"><span data-stu-id="99d1d-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="99d1d-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="99d1d-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="99d1d-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="99d1d-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="99d1d-139">如果您的專案有 Glob，而且您嘗試使用最新的 SDK 建置專案，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="99d1d-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="99d1d-140">包含了重複的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="99d1d-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="99d1d-141">.NET SDK 預設會包含您專案目錄中的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="99d1d-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="99d1d-142">您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。</span><span class="sxs-lookup"><span data-stu-id="99d1d-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="99d1d-143">若要解決此錯誤，您可以明確移除符合上表所列項目的 `Compile` 項目，或將 `<EnableDefaultCompileItems>` 屬性設定為 `false`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="99d1d-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="99d1d-144">將此屬性設定為 `false` 會覆寫隱含包含項目，而且其行為會還原成必須在專案中指定預設 Glob 的舊版 SDK。</span><span class="sxs-lookup"><span data-stu-id="99d1d-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="99d1d-145">這項變更不會修改其他包含項目的主要機制。</span><span class="sxs-lookup"><span data-stu-id="99d1d-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="99d1d-146">不過，如果您想要指定某些檔案由應用程式發行，您仍然可以使用 *csproj* 中已知的機制來執行這項作業 (例如 `<Content>` 項目)。</span><span class="sxs-lookup"><span data-stu-id="99d1d-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="99d1d-147">`<EnableDefaultCompileItems>` 只會停用 `Compile` GLOB，而不會影響隱含 `None` GLOB 這類其他 GLOB，後者也會套用至 \*.cs 項目。</span><span class="sxs-lookup"><span data-stu-id="99d1d-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="99d1d-148">因此，方案總管會繼續將 \*.cs 項目顯示為包含為 `None` 項目之專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="99d1d-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="99d1d-149">透過類似的方式，您可以使用 `<EnableDefaultNoneItems>` 停用隱含 `None` GLOB。</span><span class="sxs-lookup"><span data-stu-id="99d1d-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="99d1d-150">若要停用**所有隱含 GLOB**，您可以將 `<EnableDefaultItems>` 屬性設定為 `false`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="99d1d-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="99d1d-151">如何以 MSBuild 查看專案的方式查看整個專案</span><span class="sxs-lookup"><span data-stu-id="99d1d-151">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="99d1d-152">雖然那些 csproj 變更可大幅簡化專案檔，在包括 SDK 和其目標之後，您可能會想要以 MSBuild 查看專案的方式查看完全展開的專案。</span><span class="sxs-lookup"><span data-stu-id="99d1d-152">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="99d1d-153">使用 [`dotnet msbuild`](dotnet-msbuild.md) 命令的 [`/pp` 切換](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) 對專案進行前置處理，它可以在不需要實際建置專案的情況下，顯示匯入的檔案、檔案的來源，以及該檔案對組建的貢獻：</span><span class="sxs-lookup"><span data-stu-id="99d1d-153">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="99d1d-154">如果專案具有多個目標架構，系統應該會透過將它們的其中之一指定為 MSBuild 屬性，來使命令的結果專注於該目標架構：</span><span class="sxs-lookup"><span data-stu-id="99d1d-154">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="99d1d-155">新增項目</span><span class="sxs-lookup"><span data-stu-id="99d1d-155">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="99d1d-156">Sdk 屬性</span><span class="sxs-lookup"><span data-stu-id="99d1d-156">Sdk attribute</span></span> 
<span data-ttu-id="99d1d-157">*.csproj* 檔案的 `<Project>` 項目有一個新屬性，稱為 `Sdk`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-157">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="99d1d-158">`Sdk` 會指定專案將使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="99d1d-158">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="99d1d-159">如[分層文件](cli-msbuild-architecture.md)所述，SDK 是可建置 .NET Core 程式碼的一組 MSBuild [工作](/visualstudio/msbuild/msbuild-tasks)和[目標](/visualstudio/msbuild/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="99d1d-159">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="99d1d-160">我們隨 .NET Core 工具提供三個主要 SDK：</span><span class="sxs-lookup"><span data-stu-id="99d1d-160">We ship three main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="99d1d-161">識別碼為 `Microsoft.NET.Sdk` 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="99d1d-161">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="99d1d-162">識別碼為 `Microsoft.NET.Sdk.Web` 的 .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="99d1d-162">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="99d1d-163">識別碼為 `Microsoft.NET.Sdk.Razor` 的 .NET Core Razor 類別庫 SDK</span><span class="sxs-lookup"><span data-stu-id="99d1d-163">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>

<span data-ttu-id="99d1d-164">您必須在 `<Project>` 項目中將 `Sdk` 屬性設定為上述其中一個識別碼，才能使用 .NET Core 工具並建置您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="99d1d-164">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="99d1d-165">PackageReference</span><span class="sxs-lookup"><span data-stu-id="99d1d-165">PackageReference</span></span>
<span data-ttu-id="99d1d-166">在專案中指定 NuGet 相依性的項目。</span><span class="sxs-lookup"><span data-stu-id="99d1d-166">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="99d1d-167">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="99d1d-167">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="99d1d-168">版本</span><span class="sxs-lookup"><span data-stu-id="99d1d-168">Version</span></span>
<span data-ttu-id="99d1d-169">`Version` 指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="99d1d-169">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="99d1d-170">該屬性採用 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="99d1d-170">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="99d1d-171">預設行為是確切的版本相符。</span><span class="sxs-lookup"><span data-stu-id="99d1d-171">The default behavior is an exact version match.</span></span> <span data-ttu-id="99d1d-172">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。</span><span class="sxs-lookup"><span data-stu-id="99d1d-172">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="99d1d-173">IncludeAssets、ExcludeAssets 和 PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="99d1d-173">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="99d1d-174">`IncludeAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。</span><span class="sxs-lookup"><span data-stu-id="99d1d-174">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="99d1d-175">`ExcludeAssets` 屬性指定不應取用哪些資產 (屬於由 `<PackageReference>` 所指定的套件)。</span><span class="sxs-lookup"><span data-stu-id="99d1d-175">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="99d1d-176">`PrivateAssets` 屬性指定應取用哪些資產 (屬於由 `<PackageReference>` 所指定但未流向下一個專案的套件)。</span><span class="sxs-lookup"><span data-stu-id="99d1d-176">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="99d1d-177">`PrivateAssets` 相當於 *project.json*/*xproj* `SuppressParent` 項目。</span><span class="sxs-lookup"><span data-stu-id="99d1d-177">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="99d1d-178">這些屬性可包含下列一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="99d1d-178">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="99d1d-179">`Compile` – lib 資料夾的內容可供編譯。</span><span class="sxs-lookup"><span data-stu-id="99d1d-179">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="99d1d-180">`Runtime` – 會散發 runtime 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="99d1d-180">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="99d1d-181">`ContentFiles` - 會使用 *contentfiles* 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="99d1d-181">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="99d1d-182">`Build` – 會使用組建資料夾中的屬性/目標。</span><span class="sxs-lookup"><span data-stu-id="99d1d-182">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="99d1d-183">`Native` – 原生資產內容會複製到執行階段輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="99d1d-183">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="99d1d-184">`Analyzers` – 會使用分析器。</span><span class="sxs-lookup"><span data-stu-id="99d1d-184">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="99d1d-185">另外，該屬性也可以包含︰</span><span class="sxs-lookup"><span data-stu-id="99d1d-185">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="99d1d-186">`None` – 未使用任何資產。</span><span class="sxs-lookup"><span data-stu-id="99d1d-186">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="99d1d-187">`All` – 會使用所有資產。</span><span class="sxs-lookup"><span data-stu-id="99d1d-187">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="99d1d-188">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="99d1d-188">DotNetCliToolReference</span></span>
<span data-ttu-id="99d1d-189">`<DotNetCliToolReference>` 項目指定使用者想要在專案內容中還原的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="99d1d-189">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="99d1d-190">它會取代 *project.json* 中的 `tools` 節點。</span><span class="sxs-lookup"><span data-stu-id="99d1d-190">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="99d1d-191">版本</span><span class="sxs-lookup"><span data-stu-id="99d1d-191">Version</span></span>
<span data-ttu-id="99d1d-192">`Version` 指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="99d1d-192">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="99d1d-193">該屬性採用 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="99d1d-193">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="99d1d-194">預設行為是確切的版本相符。</span><span class="sxs-lookup"><span data-stu-id="99d1d-194">The default behavior is an exact version match.</span></span> <span data-ttu-id="99d1d-195">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。</span><span class="sxs-lookup"><span data-stu-id="99d1d-195">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="99d1d-196">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="99d1d-196">RuntimeIdentifiers</span></span>
<span data-ttu-id="99d1d-197">`<RuntimeIdentifiers>` 項目可讓您針對專案指定以分號分隔的[執行階段識別碼 (RID)](../rid-catalog.md) 清單。</span><span class="sxs-lookup"><span data-stu-id="99d1d-197">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="99d1d-198">RID 允許發行獨立部署。</span><span class="sxs-lookup"><span data-stu-id="99d1d-198">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="99d1d-199">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="99d1d-199">RuntimeIdentifier</span></span>
<span data-ttu-id="99d1d-200">`<RuntimeIdentifier>` 項目可讓您針對專案只指定一個[執行階段識別項 (RID)](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="99d1d-200">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="99d1d-201">RID 允許發行獨立部署。</span><span class="sxs-lookup"><span data-stu-id="99d1d-201">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="99d1d-202">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="99d1d-202">PackageTargetFallback</span></span> 
<span data-ttu-id="99d1d-203">`<PackageTargetFallback>` 項目可讓您指定一組要在還原套件時使用的相容目標。</span><span class="sxs-lookup"><span data-stu-id="99d1d-203">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="99d1d-204">其設計目的是為了讓使用 dotnet [TxM (目標 x Moniker)](/nuget/schema/target-frameworks) 的套件能和未宣告 dotnet TxM 的套件一起運作。</span><span class="sxs-lookup"><span data-stu-id="99d1d-204">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="99d1d-205">如果您的專案使用 dotnet TxM，除非您將 `<PackageTargetFallback>` 新增至專案，以讓非 dotnet 平台變成能與 dotnet 相容，否則其相依的所有套件也必須要有 dotnet TxM。</span><span class="sxs-lookup"><span data-stu-id="99d1d-205">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="99d1d-206">下列範例可為專案中的所有目標提供後援：</span><span class="sxs-lookup"><span data-stu-id="99d1d-206">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="99d1d-207">下列範例只會為 `netcoreapp2.1` 目標指定後援︰</span><span class="sxs-lookup"><span data-stu-id="99d1d-207">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="99d1d-208">NuGet 中繼資料屬性</span><span class="sxs-lookup"><span data-stu-id="99d1d-208">NuGet metadata properties</span></span>
<span data-ttu-id="99d1d-209">隨著改為使用 MSBuild，我們已經將封裝 NuGet 套件時使用的輸入中繼資料從 *project.json* 移動到 *.csproj* 檔。</span><span class="sxs-lookup"><span data-stu-id="99d1d-209">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="99d1d-210">此輸入是 MSBuild 屬性，因此必須移至 `<PropertyGroup>` 群組。</span><span class="sxs-lookup"><span data-stu-id="99d1d-210">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="99d1d-211">使用 `dotnet pack` 命令或屬於 SDK 一部分的 `Pack` MSBuild 目標時，會將下列的屬性清單當成封裝處理序的輸入使用。</span><span class="sxs-lookup"><span data-stu-id="99d1d-211">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="99d1d-212">IsPackable</span><span class="sxs-lookup"><span data-stu-id="99d1d-212">IsPackable</span></span>
<span data-ttu-id="99d1d-213">布林值，指定是否可封裝專案。</span><span class="sxs-lookup"><span data-stu-id="99d1d-213">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="99d1d-214">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-214">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="99d1d-215">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="99d1d-215">PackageVersion</span></span>
<span data-ttu-id="99d1d-216">指定所產生之套件的版本。</span><span class="sxs-lookup"><span data-stu-id="99d1d-216">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="99d1d-217">接受所有形式的 NuGet 版本字串。</span><span class="sxs-lookup"><span data-stu-id="99d1d-217">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="99d1d-218">預設為 `$(Version)` 的值，也就是專案中的屬性 `Version`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-218">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="99d1d-219">PackageId</span><span class="sxs-lookup"><span data-stu-id="99d1d-219">PackageId</span></span>
<span data-ttu-id="99d1d-220">指定所產生之套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="99d1d-220">Specifies the name for the resulting package.</span></span> <span data-ttu-id="99d1d-221">如果未指定，`pack` 作業會預設為使用 `AssemblyName` 或目錄名稱作為套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="99d1d-221">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="99d1d-222">標題</span><span class="sxs-lookup"><span data-stu-id="99d1d-222">Title</span></span>
<span data-ttu-id="99d1d-223">套件的易記標題，通常會用於 UI 顯示，以及 nuget.org 和 Visual Studio 套件管理員中。</span><span class="sxs-lookup"><span data-stu-id="99d1d-223">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="99d1d-224">如果未指定，則會改用套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="99d1d-224">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="99d1d-225">作者</span><span class="sxs-lookup"><span data-stu-id="99d1d-225">Authors</span></span>
<span data-ttu-id="99d1d-226">以分號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些名稱會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-226">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="99d1d-227">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="99d1d-227">PackageDescription</span></span>

<span data-ttu-id="99d1d-228">UI 顯示中的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="99d1d-228">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="99d1d-229">說明</span><span class="sxs-lookup"><span data-stu-id="99d1d-229">Description</span></span>
<span data-ttu-id="99d1d-230">組件的完整描述。</span><span class="sxs-lookup"><span data-stu-id="99d1d-230">A long description for the assembly.</span></span> <span data-ttu-id="99d1d-231">如果未指定 `PackageDescription`，則此屬性也會用來作為套件的描述。</span><span class="sxs-lookup"><span data-stu-id="99d1d-231">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="99d1d-232">Copyright</span><span class="sxs-lookup"><span data-stu-id="99d1d-232">Copyright</span></span>
<span data-ttu-id="99d1d-233">套件的著作權詳細資料。</span><span class="sxs-lookup"><span data-stu-id="99d1d-233">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="99d1d-234">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="99d1d-234">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="99d1d-235">布林值，指定在安裝套件時，用戶端是否必須提示取用者接受套件授權。</span><span class="sxs-lookup"><span data-stu-id="99d1d-235">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="99d1d-236">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-236">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="99d1d-237">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="99d1d-237">PackageLicenseUrl</span></span>
<span data-ttu-id="99d1d-238">適用於套件的授權 URL。</span><span class="sxs-lookup"><span data-stu-id="99d1d-238">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="99d1d-239">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="99d1d-239">PackageProjectUrl</span></span>
<span data-ttu-id="99d1d-240">套件首頁的 URL，通常會顯示在 UI 顯示及 nuget.org 中。</span><span class="sxs-lookup"><span data-stu-id="99d1d-240">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="99d1d-241">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="99d1d-241">PackageIconUrl</span></span>
<span data-ttu-id="99d1d-242">具有透明背景之 64x64 映像的 URL，該映像會用作套件在 UI 顯示中的圖示。</span><span class="sxs-lookup"><span data-stu-id="99d1d-242">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="99d1d-243">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="99d1d-243">PackageReleaseNotes</span></span>
<span data-ttu-id="99d1d-244">套件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="99d1d-244">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="99d1d-245">PackageTags</span><span class="sxs-lookup"><span data-stu-id="99d1d-245">PackageTags</span></span>
<span data-ttu-id="99d1d-246">以分號分隔的標記清單，用以指定套件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-246">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="99d1d-247">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="99d1d-247">PackageOutputPath</span></span>
<span data-ttu-id="99d1d-248">決定要置放所封裝之套件的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="99d1d-248">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="99d1d-249">預設為 `$(OutputPath)`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-249">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="99d1d-250">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="99d1d-250">IncludeSymbols</span></span>
<span data-ttu-id="99d1d-251">此布林值會指出在封裝專案時，套件是否應該建立額外的符號套件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-251">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="99d1d-252">此套件的副檔名為 *.symbols.nupkg*，將連同 DLL 和其他輸出檔一起複製 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="99d1d-252">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="99d1d-253">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="99d1d-253">IncludeSource</span></span>
<span data-ttu-id="99d1d-254">此布林值會指出封裝處理序是否應該建立來源套件。</span><span class="sxs-lookup"><span data-stu-id="99d1d-254">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="99d1d-255">來源套件包含程式庫的原始程式碼及 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="99d1d-255">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="99d1d-256">原始程式檔會放在所產生之套件檔案中的 `src/ProjectName` 目錄底下。</span><span class="sxs-lookup"><span data-stu-id="99d1d-256">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="99d1d-257">IsTool</span><span class="sxs-lookup"><span data-stu-id="99d1d-257">IsTool</span></span>
<span data-ttu-id="99d1d-258">指定是否要將所有輸出檔複製到 *tools* 資料夾，而不是 *lib* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="99d1d-258">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="99d1d-259">請注意，這與 `DotNetCliTool` 不同，該項目是藉由在 *.csproj* 檔案中設定 `PackageType` 所指定。</span><span class="sxs-lookup"><span data-stu-id="99d1d-259">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="99d1d-260">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="99d1d-260">RepositoryUrl</span></span>
<span data-ttu-id="99d1d-261">指定存放庫的 URL，此存放庫是套件原始程式碼的所在位置及 (或) 正在建置的來源位置。</span><span class="sxs-lookup"><span data-stu-id="99d1d-261">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="99d1d-262">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="99d1d-262">RepositoryType</span></span>
<span data-ttu-id="99d1d-263">指定存放庫的類型。</span><span class="sxs-lookup"><span data-stu-id="99d1d-263">Specifies the type of the repository.</span></span> <span data-ttu-id="99d1d-264">預設值為 "git"。</span><span class="sxs-lookup"><span data-stu-id="99d1d-264">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="99d1d-265">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="99d1d-265">NoPackageAnalysis</span></span>
<span data-ttu-id="99d1d-266">指定封裝不應該在建置套件之後執行套件分析。</span><span class="sxs-lookup"><span data-stu-id="99d1d-266">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="99d1d-267">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="99d1d-267">MinClientVersion</span></span>
<span data-ttu-id="99d1d-268">指定可安裝此套件的最低 NuGet 用戶端版本，此作業是由 nuget.exe 和 Visual Studio 套件管理員強制執行。</span><span class="sxs-lookup"><span data-stu-id="99d1d-268">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="99d1d-269">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="99d1d-269">IncludeBuildOutput</span></span>
<span data-ttu-id="99d1d-270">此布林值會指定是否應該將建置輸出組建封裝成 *.nupkg* 檔案。</span><span class="sxs-lookup"><span data-stu-id="99d1d-270">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="99d1d-271">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="99d1d-271">IncludeContentInPack</span></span>
<span data-ttu-id="99d1d-272">此布林值會指定是否有任何類型為 `Content` 的項目會自動包含於所產生的套件中。</span><span class="sxs-lookup"><span data-stu-id="99d1d-272">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="99d1d-273">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-273">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="99d1d-274">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="99d1d-274">BuildOutputTargetFolder</span></span>
<span data-ttu-id="99d1d-275">指定要放置輸出組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="99d1d-275">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="99d1d-276">輸出組件 (及其他輸出檔) 會複製到其相關的架構資料夾中。</span><span class="sxs-lookup"><span data-stu-id="99d1d-276">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="99d1d-277">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="99d1d-277">ContentTargetFolders</span></span>
<span data-ttu-id="99d1d-278">如果未指定 `PackagePath`，此屬性會指定所有內容檔案應移至的預設位置。</span><span class="sxs-lookup"><span data-stu-id="99d1d-278">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="99d1d-279">預設值為 "content;contentFiles"。</span><span class="sxs-lookup"><span data-stu-id="99d1d-279">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="99d1d-280">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="99d1d-280">NuspecFile</span></span>
<span data-ttu-id="99d1d-281">正用於封裝之 *.nuspec* 檔案的相對或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="99d1d-281">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="99d1d-282">如果指定 *.nuspec* 檔案，則會**單獨**使用此檔案來封裝資訊，而不會使用專案中的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="99d1d-282">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="99d1d-283">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="99d1d-283">NuspecBasePath</span></span>
<span data-ttu-id="99d1d-284">*.nuspec* 檔案的基底路徑。</span><span class="sxs-lookup"><span data-stu-id="99d1d-284">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="99d1d-285">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="99d1d-285">NuspecProperties</span></span>
<span data-ttu-id="99d1d-286">以分號分隔的索引鍵=值組清單。</span><span class="sxs-lookup"><span data-stu-id="99d1d-286">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="99d1d-287">AssemblyInfo 屬性</span><span class="sxs-lookup"><span data-stu-id="99d1d-287">AssemblyInfo properties</span></span>
<span data-ttu-id="99d1d-288">[組件屬性](../../framework/app-domains/set-assembly-attributes.md)，通常存在於 AssemblyInfo 檔案，現在會自動從屬性產生。</span><span class="sxs-lookup"><span data-stu-id="99d1d-288">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="99d1d-289">每個屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="99d1d-289">Properties per attribute</span></span>

<span data-ttu-id="99d1d-290">每個屬性 (Attribute) 有一個屬性 (Property)，控制其內容，另一個則是停用其產生，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="99d1d-290">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="99d1d-291">屬性</span><span class="sxs-lookup"><span data-stu-id="99d1d-291">Attribute</span></span>                                                      | <span data-ttu-id="99d1d-292">屬性</span><span class="sxs-lookup"><span data-stu-id="99d1d-292">Property</span></span>               | <span data-ttu-id="99d1d-293">要停用的屬性</span><span class="sxs-lookup"><span data-stu-id="99d1d-293">Property to disable</span></span>                             |
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

<span data-ttu-id="99d1d-294">附註：</span><span class="sxs-lookup"><span data-stu-id="99d1d-294">Notes:</span></span>

* <span data-ttu-id="99d1d-295">`AssemblyVersion` 和 `FileVersion` 預設為採用沒有後置詞的 `$(Version)` 值。</span><span class="sxs-lookup"><span data-stu-id="99d1d-295">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="99d1d-296">例如，如果 `$(Version)` 是 `1.2.3-beta.4`，則此值會是 `1.2.3`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-296">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="99d1d-297">`InformationalVersion` 預設為 `$(Version)` 的值。</span><span class="sxs-lookup"><span data-stu-id="99d1d-297">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="99d1d-298">如果有屬性，則 `InformationalVersion` 會附加 `$(SourceRevisionId)`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-298">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="99d1d-299">可以使用 `IncludeSourceRevisionInInformationalVersion` 來加以停用。</span><span class="sxs-lookup"><span data-stu-id="99d1d-299">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="99d1d-300">也會針對 NuGet 中繼資料使用 `Copyright` 和 `Description` 屬性。</span><span class="sxs-lookup"><span data-stu-id="99d1d-300">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="99d1d-301">`Configuration` 與所有建置程序共用，並且是透過 `dotnet` 命令的 `--configuration` 參數來設定。</span><span class="sxs-lookup"><span data-stu-id="99d1d-301">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="99d1d-302">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="99d1d-302">GenerateAssemblyInfo</span></span> 
<span data-ttu-id="99d1d-303">布林值，啟用或停用所有 AssemblyInfo 產生。</span><span class="sxs-lookup"><span data-stu-id="99d1d-303">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="99d1d-304">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="99d1d-304">The default value is `true`.</span></span> 

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="99d1d-305">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="99d1d-305">GeneratedAssemblyInfoFile</span></span> 
<span data-ttu-id="99d1d-306">產生組件資訊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="99d1d-306">The path of the generated assembly info file.</span></span> <span data-ttu-id="99d1d-307">預設為 `$(IntermediateOutputPath)` (obj) 目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="99d1d-307">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
