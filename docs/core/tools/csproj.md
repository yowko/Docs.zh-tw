---
title: 適用於 .NET Core 之 csproj 格式的新增項目
description: 深入了解現有和 .NET Core csproj 檔案之間的差異
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: 1e356d0123328fe703f672c38cb5ee7799cb574c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218228"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="9c7a7-103">適用於 .NET Core 之 csproj 格式的新增項目</span><span class="sxs-lookup"><span data-stu-id="9c7a7-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="9c7a7-104">本文件概述從 *project.json* 改為使用 *csproj* 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至專案檔的變更。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="9c7a7-105">如需一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="9c7a7-106">隱含套件參考</span><span class="sxs-lookup"><span data-stu-id="9c7a7-106">Implicit package references</span></span>
<span data-ttu-id="9c7a7-107">會根據您專案檔之 `<TargetFramework>` 或 `<TargetFrameworks>` 屬性中指定的目標架構來隱含參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="9c7a7-108">如果指定了 `<TargetFramework>`，則會忽略 `<TargetFrameworks>`，與順序無關。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="9c7a7-109">建議</span><span class="sxs-lookup"><span data-stu-id="9c7a7-109">Recommendations</span></span>
<span data-ttu-id="9c7a7-110">由於會隱含參考 `Microsoft.NETCore.App` 或 `NetStandard.Library` 中繼套件，因此建議使用下列最佳做法：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="9c7a7-111">以 .NET Core 或 .NET Standard 為目標時，絕不透過專案檔中的 `<PackageReference>` 項目明確參考 `Microsoft.NETCore.App` 或 `NetStandard.Library` 中繼套件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="9c7a7-112">如果您以 .NET Core 為目標時需要特定版本的執行階段，您應該使用專案中的 `<RuntimeFrameworkVersion>` 屬性 (例如 `1.0.4`)，而不是參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="9c7a7-113">如果您使用[獨立性部署](../deploying/index.md#self-contained-deployments-scd)，並需要 1.0.0 LTS 執行階段的特定更新程式版本，就可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="9c7a7-114">如果您以 .NET Standard 為目標時需要特定版本的 `NetStandard.Library` 中繼套件，您可以使用 `<NetStandardImplicitPackageVersion>` 屬性並設定所需的版本。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="9c7a7-115">請不要在 .NET Framework 專案中明確地新增或更新 `Microsoft.NETCore.App` 或 `NetStandard.Library` 中繼套件的參考。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="9c7a7-116">如果使用 .NET Standard 型 NuGet 套件時需要任何版本的 `NetStandard.Library`，NuGet 會自動安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="9c7a7-117">.NET Core 專案中包含預設編譯</span><span class="sxs-lookup"><span data-stu-id="9c7a7-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="9c7a7-118">隨著改為使用最新 SDK 版本中的 *csproj* 格式，編譯項目的預設包含項目和排除項目以及內嵌資源都已移至 SDK 屬性檔。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="9c7a7-119">這表示您不再需要於專案檔中指定這些項目。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="9c7a7-120">這樣做的主要原因是為了讓專案檔更為簡潔。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="9c7a7-121">SDK 中的預設值應該涵蓋最常見的使用案例，而不需要在每個建立的專案中重複這些項目。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="9c7a7-122">這會產生較小的專案檔，而更容易了解及視需要手動編輯。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="9c7a7-123">下表顯示 SDK 中會同時包含及排除的元素與 [Glob (英文)](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="9c7a7-124">元素</span><span class="sxs-lookup"><span data-stu-id="9c7a7-124">Element</span></span>           | <span data-ttu-id="9c7a7-125">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="9c7a7-125">Include glob</span></span>                              | <span data-ttu-id="9c7a7-126">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="9c7a7-126">Exclude glob</span></span>                                                  | <span data-ttu-id="9c7a7-127">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="9c7a7-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="9c7a7-128">編譯</span><span class="sxs-lookup"><span data-stu-id="9c7a7-128">Compile</span></span>           | <span data-ttu-id="9c7a7-129">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="9c7a7-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="9c7a7-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="9c7a7-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="9c7a7-131">N/A</span><span class="sxs-lookup"><span data-stu-id="9c7a7-131">N/A</span></span>                        |
| <span data-ttu-id="9c7a7-132">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="9c7a7-132">EmbeddedResource</span></span>  | <span data-ttu-id="9c7a7-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="9c7a7-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="9c7a7-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="9c7a7-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="9c7a7-135">N/A</span><span class="sxs-lookup"><span data-stu-id="9c7a7-135">N/A</span></span>                        |
| <span data-ttu-id="9c7a7-136">無</span><span class="sxs-lookup"><span data-stu-id="9c7a7-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="9c7a7-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="9c7a7-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="9c7a7-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="9c7a7-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="9c7a7-139">如果您的專案有 Glob，而且您嘗試使用最新的 SDK 建置專案，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="9c7a7-140">包含了重複的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="9c7a7-141">.NET SDK 預設會包含您專案目錄中的編譯項目。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="9c7a7-142">您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="9c7a7-143">若要解決此錯誤，您可以明確移除符合上表所列項目的 `Compile` 項目，或將 `<EnableDefaultCompileItems>` 屬性設定為 `false`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="9c7a7-144">將此屬性設定為 `false` 會覆寫隱含包含項目，而且其行為會還原成必須在專案中指定預設 Glob 的舊版 SDK。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="9c7a7-145">這項變更不會修改其他包含項目的主要機制。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="9c7a7-146">不過，如果您想要指定某些檔案由應用程式發行，您仍然可以使用 *csproj* 中已知的機制來執行這項作業 (例如 `<Content>` 項目)。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="9c7a7-147">`<EnableDefaultCompileItems>` 只會停用 `Compile` GLOB，而不會影響隱含 `None` GLOB 這類其他 GLOB，後者也會套用至 \*.cs 項目。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="9c7a7-148">因此，方案總管會繼續將 \*.cs 項目顯示為包含為 `None` 項目之專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="9c7a7-149">透過類似的方式，您可以使用 `<EnableDefaultNoneItems>` 停用隱含 `None` GLOB。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="9c7a7-150">若要停用**所有隱含 GLOB**，您可以將 `<EnableDefaultItems>` 屬性設定為 `false`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="9c7a7-151">建議</span><span class="sxs-lookup"><span data-stu-id="9c7a7-151">Recommendation</span></span>
<span data-ttu-id="9c7a7-152">使用 csproj 時，建議您從專案中移除預設 Glob，並只使用 Glob 新增您的應用程式/程式庫在各種情況下 (例如執行階段與 NuGet 套件) 所需之成品的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="9c7a7-153">如何以 MSBuild 查看專案的方式查看整個專案</span><span class="sxs-lookup"><span data-stu-id="9c7a7-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="9c7a7-154">雖然那些 csproj 變更可大幅簡化專案檔，在包括 SDK 和其目標之後，您可能會想要以 MSBuild 查看專案的方式查看完全展開的專案。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="9c7a7-155">使用 [`dotnet msbuild`](dotnet-msbuild.md) 命令的 [`/pp` 切換](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) 對專案進行前置處理，它可以在不需要實際建置專案的情況下，顯示匯入的檔案、檔案的來源，以及該檔案對組建的貢獻：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="9c7a7-156">如果專案具有多個目標架構，系統應該會透過將它們的其中之一指定為 MSBuild 屬性，來使命令的結果專注於該目標架構：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="9c7a7-157">新增項目</span><span class="sxs-lookup"><span data-stu-id="9c7a7-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="9c7a7-158">Sdk 屬性</span><span class="sxs-lookup"><span data-stu-id="9c7a7-158">Sdk attribute</span></span> 
<span data-ttu-id="9c7a7-159">*.csproj* 檔案的 `<Project>` 項目有一個新屬性，稱為 `Sdk`。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="9c7a7-160">`Sdk` 會指定專案將使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="9c7a7-161">如[分層文件](cli-msbuild-architecture.md)所述，SDK 是可建置 .NET Core 程式碼的一組 MSBuild [工作](/visualstudio/msbuild/msbuild-tasks)和[目標](/visualstudio/msbuild/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="9c7a7-162">我們提供內含 .NET Core 工具的兩個主要 SDK：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="9c7a7-163">識別碼為 `Microsoft.NET.Sdk` 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="9c7a7-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="9c7a7-164">識別碼為 `Microsoft.NET.Sdk.Web` 的 .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="9c7a7-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="9c7a7-165">您必須在 `<Project>` 項目中將 `Sdk` 屬性設定為上述其中一個識別碼，才能使用 .NET Core 工具並建置您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="9c7a7-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="9c7a7-166">PackageReference</span></span>
<span data-ttu-id="9c7a7-167">在專案中指定 NuGet 相依性的項目。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="9c7a7-168">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="9c7a7-169">版本</span><span class="sxs-lookup"><span data-stu-id="9c7a7-169">Version</span></span>
<span data-ttu-id="9c7a7-170">`Version` 指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="9c7a7-171">該屬性採用 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="9c7a7-172">預設行為是確切的版本相符。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="9c7a7-173">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="9c7a7-174">IncludeAssets、ExcludeAssets 和 PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="9c7a7-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="9c7a7-175">`IncludeAssets` 屬性指定應取用由 `<PackageReference>` 所指定屬於套件的何種資產。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="9c7a7-176">`ExcludeAssets` 屬性指定不應取用屬於由 `<PackageReference>` 所指定套件的何種資產。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="9c7a7-177">`PrivateAssets` 屬性指定應取用屬於由 `<PackageReference>` 所指定套件的何種資產，但是它們不應該傳遞至下一個專案。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c7a7-178">`PrivateAssets` 相當於 *project.json*/*xproj* `SuppressParent` 項目。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="9c7a7-179">這些屬性可包含下列一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="9c7a7-180">`Compile` – lib 資料夾的內容可供編譯。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="9c7a7-181">`Runtime` – 會散發 runtime 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="9c7a7-182">`ContentFiles` - 會使用 *contentfiles* 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="9c7a7-183">`Build` – 會使用組建資料夾中的屬性/目標。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="9c7a7-184">`Native` – 原生資產內容會複製到執行階段輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="9c7a7-185">`Analyzers` – 會使用分析器。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="9c7a7-186">另外，該屬性也可以包含︰</span><span class="sxs-lookup"><span data-stu-id="9c7a7-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="9c7a7-187">`None` – 未使用任何資產。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="9c7a7-188">`All` – 會使用所有資產。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="9c7a7-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="9c7a7-189">DotNetCliToolReference</span></span>
<span data-ttu-id="9c7a7-190">`<DotNetCliToolReference>` 項目指定使用者想要在專案內容中還原的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="9c7a7-191">它會取代 *project.json* 中的 `tools` 節點。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="9c7a7-192">版本</span><span class="sxs-lookup"><span data-stu-id="9c7a7-192">Version</span></span>
<span data-ttu-id="9c7a7-193">`Version` 指定要還原的套件版本。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="9c7a7-194">該屬性採用 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)配置的規則。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="9c7a7-195">預設行為是確切的版本相符。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="9c7a7-196">例如，指定 `Version="1.2.3"` 相當於 NuGet 標記法 `[1.2.3]`，表示確切的套件版本 1.2.3。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="9c7a7-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="9c7a7-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="9c7a7-198">`<RuntimeIdentifiers>` 項目可讓您針對專案指定以分號分隔的[執行階段識別碼 (RID)](../rid-catalog.md) 清單。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9c7a7-199">RID 允許發行獨立部署。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="9c7a7-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="9c7a7-200">RuntimeIdentifier</span></span>
<span data-ttu-id="9c7a7-201">`<RuntimeIdentifier>` 項目可讓您針對專案只指定一個[執行階段識別項 (RID)](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9c7a7-202">RID 允許發行獨立部署。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="9c7a7-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9c7a7-203">PackageTargetFallback</span></span> 
<span data-ttu-id="9c7a7-204">`<PackageTargetFallback>` 項目可讓您指定一組要在還原套件時使用的相容目標。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="9c7a7-205">其設計目的是為了讓使用 dotnet [TxM (目標 x Moniker)](/nuget/schema/target-frameworks) 的套件能和未宣告 dotnet TxM 的套件一起運作。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="9c7a7-206">如果您的專案使用 dotnet TxM，除非您將 `<PackageTargetFallback>` 新增至專案，以讓非 dotnet 平台變成能與 dotnet 相容，否則其相依的所有套件也必須要有 dotnet TxM。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="9c7a7-207">下列範例可為專案中的所有目標提供後援：</span><span class="sxs-lookup"><span data-stu-id="9c7a7-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="9c7a7-208">下列範例只會為 `netcoreapp1.0` 目標指定後援︰</span><span class="sxs-lookup"><span data-stu-id="9c7a7-208">The following example specifies the fallbacks only for the `netcoreapp1.0` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="9c7a7-209">NuGet 中繼資料屬性</span><span class="sxs-lookup"><span data-stu-id="9c7a7-209">NuGet metadata properties</span></span>
<span data-ttu-id="9c7a7-210">隨著改為使用 MSbuild，我們已經將封裝 NuGet 套件時使用的輸入中繼資料從 *project.json* 移動到 *.csproj* 檔。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="9c7a7-211">此輸入是 MSBuild 屬性，因此必須移至 `<PropertyGroup>` 群組。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="9c7a7-212">使用 `dotnet pack` 命令或屬於 SDK 一部分的 `Pack` MSBuild 目標時，會將下列的屬性清單當成封裝處理序的輸入使用。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="9c7a7-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="9c7a7-213">IsPackable</span></span>
<span data-ttu-id="9c7a7-214">布林值，指定是否可封裝專案。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="9c7a7-215">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="9c7a7-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="9c7a7-216">PackageVersion</span></span>
<span data-ttu-id="9c7a7-217">指定所產生之套件的版本。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="9c7a7-218">接受所有形式的 NuGet 版本字串。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="9c7a7-219">預設為 `$(Version)` 的值，也就是專案中的屬性 `Version`。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="9c7a7-220">PackageId</span><span class="sxs-lookup"><span data-stu-id="9c7a7-220">PackageId</span></span>
<span data-ttu-id="9c7a7-221">指定所產生之套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="9c7a7-222">如果未指定，`pack` 作業會預設為使用 `AssemblyName` 或目錄名稱作為套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="9c7a7-223">標題</span><span class="sxs-lookup"><span data-stu-id="9c7a7-223">Title</span></span>
<span data-ttu-id="9c7a7-224">套件的易記標題，通常會用於 UI 顯示，以及 nuget.org 和 Visual Studio 套件管理員中。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="9c7a7-225">如果未指定，則會改用套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="9c7a7-226">作者</span><span class="sxs-lookup"><span data-stu-id="9c7a7-226">Authors</span></span>
<span data-ttu-id="9c7a7-227">以分號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些名稱會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="9c7a7-228">描述</span><span class="sxs-lookup"><span data-stu-id="9c7a7-228">Description</span></span>
<span data-ttu-id="9c7a7-229">UI 顯示中的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="9c7a7-230">Copyright</span><span class="sxs-lookup"><span data-stu-id="9c7a7-230">Copyright</span></span>
<span data-ttu-id="9c7a7-231">套件的著作權詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="9c7a7-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="9c7a7-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="9c7a7-233">布林值，指定在安裝套件時，用戶端是否必須提示取用者接受套件授權。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="9c7a7-234">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="9c7a7-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="9c7a7-235">PackageLicenseUrl</span></span>
<span data-ttu-id="9c7a7-236">適用於套件的授權 URL。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="9c7a7-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="9c7a7-237">PackageProjectUrl</span></span>
<span data-ttu-id="9c7a7-238">套件首頁的 URL，通常會顯示在 UI 顯示及 nuget.org 中。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="9c7a7-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="9c7a7-239">PackageIconUrl</span></span>
<span data-ttu-id="9c7a7-240">具有透明背景之 64x64 映像的 URL，該映像會用作套件在 UI 顯示中的圖示。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="9c7a7-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="9c7a7-241">PackageReleaseNotes</span></span>
<span data-ttu-id="9c7a7-242">套件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="9c7a7-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="9c7a7-243">PackageTags</span></span>
<span data-ttu-id="9c7a7-244">以分號分隔的標記清單，用以指定套件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="9c7a7-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="9c7a7-245">PackageOutputPath</span></span>
<span data-ttu-id="9c7a7-246">決定要置放所封裝之套件的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="9c7a7-247">預設為 `$(OutputPath)`。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="9c7a7-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="9c7a7-248">IncludeSymbols</span></span>
<span data-ttu-id="9c7a7-249">此布林值會指出在封裝專案時，套件是否應該建立額外的符號套件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="9c7a7-250">此套件的副檔名為 *.symbols.nupkg*，將連同 DLL 和其他輸出檔一起複製 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="9c7a7-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="9c7a7-251">IncludeSource</span></span>
<span data-ttu-id="9c7a7-252">此布林值會指出封裝處理序是否應該建立來源套件。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="9c7a7-253">來源套件包含程式庫的原始程式碼及 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="9c7a7-254">原始程式檔會放在所產生之套件檔案中的 `src/ProjectName` 目錄底下。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="9c7a7-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="9c7a7-255">IsTool</span></span>
<span data-ttu-id="9c7a7-256">指定是否要將所有輸出檔複製到 *tools* 資料夾，而不是 *lib* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="9c7a7-257">請注意，這與 `DotNetCliTool` 不同，該項目是藉由在 *.csproj* 檔案中設定 `PackageType` 所指定。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="9c7a7-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="9c7a7-258">RepositoryUrl</span></span>
<span data-ttu-id="9c7a7-259">指定存放庫的 URL，此存放庫是套件原始程式碼的所在位置及 (或) 正在建置的來源位置。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="9c7a7-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="9c7a7-260">RepositoryType</span></span>
<span data-ttu-id="9c7a7-261">指定存放庫的類型。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-261">Specifies the type of the repository.</span></span> <span data-ttu-id="9c7a7-262">預設值為 "git"。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="9c7a7-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="9c7a7-263">NoPackageAnalysis</span></span>
<span data-ttu-id="9c7a7-264">指定封裝不應該在建置套件之後執行套件分析。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="9c7a7-265">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="9c7a7-265">MinClientVersion</span></span>
<span data-ttu-id="9c7a7-266">指定可安裝此套件的最低 NuGet 用戶端版本，此作業是由 nuget.exe 和 Visual Studio 套件管理員強制執行。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="9c7a7-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="9c7a7-267">IncludeBuildOutput</span></span>
<span data-ttu-id="9c7a7-268">此布林值會指定是否應該將建置輸出組建封裝成 *.nupkg* 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="9c7a7-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="9c7a7-269">IncludeContentInPack</span></span>
<span data-ttu-id="9c7a7-270">此布林值會指定是否有任何類型為 `Content` 的項目會自動包含於所產生的套件中。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="9c7a7-271">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="9c7a7-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="9c7a7-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="9c7a7-273">指定要放置輸出組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="9c7a7-274">輸出組件 (及其他輸出檔) 會複製到其相關的架構資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="9c7a7-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="9c7a7-275">ContentTargetFolders</span></span>
<span data-ttu-id="9c7a7-276">如果未指定 `PackagePath`，此屬性會指定所有內容檔案應移至的預設位置。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="9c7a7-277">預設值為 "content;contentFiles"。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="9c7a7-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="9c7a7-278">NuspecFile</span></span>
<span data-ttu-id="9c7a7-279">正用於封裝之 *.nuspec* 檔案的相對或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c7a7-280">如果指定 *.nuspec* 檔案，則會**單獨**使用此檔案來封裝資訊，而不會使用專案中的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="9c7a7-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="9c7a7-281">NuspecBasePath</span></span>
<span data-ttu-id="9c7a7-282">*.nuspec* 檔案的基底路徑。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="9c7a7-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="9c7a7-283">NuspecProperties</span></span>
<span data-ttu-id="9c7a7-284">以分號分隔的索引鍵=值組清單。</span><span class="sxs-lookup"><span data-stu-id="9c7a7-284">Semicolon separated list of key=value pairs.</span></span>
