---
title: .NET 核心專案 SDK 概述
description: 瞭解 .NET 核心專案 SDK。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399172"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="21554-103">.NET 核心專案 SDK</span><span class="sxs-lookup"><span data-stu-id="21554-103">.NET Core project SDKs</span></span>

<span data-ttu-id="21554-104">.NET 核心專案與軟體發展工具組 （SDK） 相關聯。</span><span class="sxs-lookup"><span data-stu-id="21554-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="21554-105">每個專案 SDK 是一組 MSBuild[目標](/visualstudio/msbuild/msbuild-targets)和相關[任務](/visualstudio/msbuild/msbuild-tasks)，負責編譯、打包和發佈代碼。</span><span class="sxs-lookup"><span data-stu-id="21554-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="21554-106">可用 SDK</span><span class="sxs-lookup"><span data-stu-id="21554-106">Available SDKs</span></span>

<span data-ttu-id="21554-107">以下 SDK 可用於 .NET 核心：</span><span class="sxs-lookup"><span data-stu-id="21554-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="21554-108">ID</span><span class="sxs-lookup"><span data-stu-id="21554-108">ID</span></span> | <span data-ttu-id="21554-109">描述</span><span class="sxs-lookup"><span data-stu-id="21554-109">Description</span></span> | <span data-ttu-id="21554-110">回購</span><span class="sxs-lookup"><span data-stu-id="21554-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="21554-111">.NET 核心 SDK</span><span class="sxs-lookup"><span data-stu-id="21554-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="21554-112">.NET 核心[Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="21554-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="21554-113">.NET 核心[剃刀 SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="21554-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="21554-114">.NET 核心工作人員服務 SDK</span><span class="sxs-lookup"><span data-stu-id="21554-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="21554-115">.NET 核心贏形和 WPF SDK</span><span class="sxs-lookup"><span data-stu-id="21554-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="21554-116">.NET 核心 SDK 是 .NET 核心的基本 SDK。</span><span class="sxs-lookup"><span data-stu-id="21554-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="21554-117">其他 SDK 引用 .NET 核心 SDK，與其他 SDK 關聯的專案具有所有可用的 .NET Core SDK 屬性。</span><span class="sxs-lookup"><span data-stu-id="21554-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="21554-118">例如，Web SDK 取決於 .NET 核心 SDK 和 Razor SDK。</span><span class="sxs-lookup"><span data-stu-id="21554-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="21554-119">您還可以創作自己的 SDK，這些 SDK 可通過 NuGet 進行分發。</span><span class="sxs-lookup"><span data-stu-id="21554-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="21554-120">專案檔</span><span class="sxs-lookup"><span data-stu-id="21554-120">Project files</span></span>

<span data-ttu-id="21554-121">.NET 核心專案基於[MSBuild](/visualstudio/msbuild/msbuild)格式。</span><span class="sxs-lookup"><span data-stu-id="21554-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="21554-122">專案檔案具有像 C# 專案的 *.csproj*和*F# 專案的 .fsproj*這樣的副檔名，它們採用 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="21554-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="21554-123">MSBuild 專案檔案的根項目是[專案](/visualstudio/msbuild/project-element-msbuild)元素。</span><span class="sxs-lookup"><span data-stu-id="21554-123">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="21554-124">該`Project`元素具有一個`Sdk`可選屬性，用於指定要使用的 SDK（和版本）。</span><span class="sxs-lookup"><span data-stu-id="21554-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="21554-125">要使用 .NET Core 工具並生成代碼，請`Sdk`將屬性設置為[可用 SDK](#available-sdks)表中的其中一個 ID。</span><span class="sxs-lookup"><span data-stu-id="21554-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="21554-126">要指定來自 NuGet 的 SDK，請在名稱末尾包括版本，或在*global.json*檔中指定名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="21554-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="21554-127">指定 SDK 的另一種方法是使用頂級[SDK](/visualstudio/msbuild/sdk-element-msbuild)元素：</span><span class="sxs-lookup"><span data-stu-id="21554-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="21554-128">以以下方式之一引用 SDK 大大簡化了 .NET Core 的專案檔案。</span><span class="sxs-lookup"><span data-stu-id="21554-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="21554-129">在評估專案時，MSBuild 在專案檔案的頂部`Sdk.props`和`Sdk.targets`底部添加了隱式導入。</span><span class="sxs-lookup"><span data-stu-id="21554-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="21554-130">在 Windows 電腦上 *，Sdk.props*和*Sdk.target*檔可以在 *%程式檔%_dotnet_sdk\\[版本]Sdks_Microsoft.NET.Sdk_Sdk*資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="21554-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="21554-131">預處理專案檔案</span><span class="sxs-lookup"><span data-stu-id="21554-131">Preprocess the project file</span></span>

<span data-ttu-id="21554-132">在 SDK 及其目標包含在 SDK 之後，您可以看到完全擴展的專案，使用`dotnet msbuild -preprocess`命令包括該專案。</span><span class="sxs-lookup"><span data-stu-id="21554-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="21554-133">命令[preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)的預[`dotnet msbuild`](../tools/dotnet-msbuild.md)處理開關顯示導入的檔、其源及其對生成的貢獻，而無需實際生成專案。</span><span class="sxs-lookup"><span data-stu-id="21554-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="21554-134">如果專案有多個目標框架，則將命令的結果僅將其指定為 MSBuild 屬性，將命令的結果集中在一個框架上。</span><span class="sxs-lookup"><span data-stu-id="21554-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="21554-135">例如：</span><span class="sxs-lookup"><span data-stu-id="21554-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="21554-136">預設編譯包括</span><span class="sxs-lookup"><span data-stu-id="21554-136">Default compilation includes</span></span>

<span data-ttu-id="21554-137">編譯項的預設值包括和排除，嵌入資源在 SDK 中定義。</span><span class="sxs-lookup"><span data-stu-id="21554-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="21554-138">與非 SDK .NET 框架專案不同，您不需要在專案檔案中指定這些專案，因為預設值涵蓋最常見的用例。</span><span class="sxs-lookup"><span data-stu-id="21554-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="21554-139">這將導致較小的專案檔案，更容易理解，以及手動編輯，如果需要的話。</span><span class="sxs-lookup"><span data-stu-id="21554-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="21554-140">下表顯示了 .NET 核心 SDK 中包括和排除哪些元素和哪些[globs：](https://en.wikipedia.org/wiki/Glob_(programming))</span><span class="sxs-lookup"><span data-stu-id="21554-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="21554-141">元素</span><span class="sxs-lookup"><span data-stu-id="21554-141">Element</span></span>           | <span data-ttu-id="21554-142">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="21554-142">Include glob</span></span>                              | <span data-ttu-id="21554-143">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="21554-143">Exclude glob</span></span>                                                  | <span data-ttu-id="21554-144">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="21554-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="21554-145">編譯</span><span class="sxs-lookup"><span data-stu-id="21554-145">Compile</span></span>           | <span data-ttu-id="21554-146">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="21554-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="21554-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="21554-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="21554-148">N/A</span><span class="sxs-lookup"><span data-stu-id="21554-148">N/A</span></span>                      |
| <span data-ttu-id="21554-149">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="21554-149">EmbeddedResource</span></span>  | <span data-ttu-id="21554-150">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="21554-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="21554-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="21554-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="21554-152">N/A</span><span class="sxs-lookup"><span data-stu-id="21554-152">N/A</span></span>                      |
| <span data-ttu-id="21554-153">None</span><span class="sxs-lookup"><span data-stu-id="21554-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="21554-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="21554-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="21554-155">\*\*/\*.cs、\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="21554-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="21554-156">預設情況下`./bin`，`./obj`由`$(BaseOutputPath)`和`$(BaseIntermediateOutputPath)`MSBuild 屬性工作表示 的 和 資料夾從 globs 中排除。</span><span class="sxs-lookup"><span data-stu-id="21554-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="21554-157">排除由 屬性`$(DefaultItemExcludes)`表示。</span><span class="sxs-lookup"><span data-stu-id="21554-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="21554-158">如果在專案檔案中顯式定義這些專案，則可能會收到以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="21554-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="21554-159">**包括重複編譯項。預設情況下，.NET SDK 包括專案目錄中的編譯項。如果要在專案檔案中顯式包含這些專案，可以從專案檔案中刪除這些專案，也可以將"啟用預設編譯專案"屬性設置為"false"。**</span><span class="sxs-lookup"><span data-stu-id="21554-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="21554-160">要解決錯誤，請刪除與上表中`Compile`列出的隱式項匹配的顯式項，或將`EnableDefaultCompileItems`屬性設置為`false`，該屬性將禁用隱式包含：</span><span class="sxs-lookup"><span data-stu-id="21554-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="21554-161">例如，如果要指定某些要隨應用發佈的檔，您仍可以使用已知的 MSBuild 機制，例如`Content`元素。</span><span class="sxs-lookup"><span data-stu-id="21554-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="21554-162">`EnableDefaultCompileItems`僅禁用`Compile`globs，但不會影響其他 globs，如也適用于`None`\*.cs 項的隱式 glob。</span><span class="sxs-lookup"><span data-stu-id="21554-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="21554-163">因此，視覺化工作室中的解決方案資源管理器將 .cs 項作為專案的一部分進行，\*作為`None`專案包含在內。</span><span class="sxs-lookup"><span data-stu-id="21554-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="21554-164">要禁用隱式`None`glob，`EnableDefaultNoneItems`請`false`設置為 ：</span><span class="sxs-lookup"><span data-stu-id="21554-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="21554-165">要禁用*所有*隱式 globs，`EnableDefaultItems`請將`false`屬性設置為 ：</span><span class="sxs-lookup"><span data-stu-id="21554-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="21554-166">自訂生成</span><span class="sxs-lookup"><span data-stu-id="21554-166">Customize the build</span></span>

<span data-ttu-id="21554-167">有各種方法來[自訂生成](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="21554-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="21554-168">您可能希望通過將屬性作為參數傳遞給[msbuild](/visualstudio/msbuild/msbuild-command-line-reference)或[dotnet](../tools/index.md)命令來覆蓋該屬性。</span><span class="sxs-lookup"><span data-stu-id="21554-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="21554-169">您還可以將屬性添加到專案檔案或*目錄.Build.props 檔*。</span><span class="sxs-lookup"><span data-stu-id="21554-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="21554-170">有關 .NET Core 專案的有用屬性清單，請參閱[.NET Core SDK 專案的 MSBuild 屬性](msbuild-props.md)。</span><span class="sxs-lookup"><span data-stu-id="21554-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="21554-171">自訂目標</span><span class="sxs-lookup"><span data-stu-id="21554-171">Custom targets</span></span>

<span data-ttu-id="21554-172">.NET Core 專案可以打包自訂 MSBuild 目標和屬性，供使用包的專案使用。</span><span class="sxs-lookup"><span data-stu-id="21554-172">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="21554-173">當您想要：</span><span class="sxs-lookup"><span data-stu-id="21554-173">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="21554-174">擴展生成過程。</span><span class="sxs-lookup"><span data-stu-id="21554-174">Extend the build process.</span></span>
- <span data-ttu-id="21554-175">訪問生成過程的專案，如生成的檔。</span><span class="sxs-lookup"><span data-stu-id="21554-175">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="21554-176">檢查調用生成的配置。</span><span class="sxs-lookup"><span data-stu-id="21554-176">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="21554-177">通過將`<package_id>.targets`檔放在表單中或`<package_id>.props`（例如）`Contoso.Utility.UsefulStuff.targets`在專案的*生成*資料夾中來添加自訂生成目標或屬性。</span><span class="sxs-lookup"><span data-stu-id="21554-177">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="21554-178">以下 XML 是 *.csproj*檔中的一個片段，[`dotnet pack`](../tools/dotnet-pack.md)用於指示命令打包什麼。</span><span class="sxs-lookup"><span data-stu-id="21554-178">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="21554-179">元素`<ItemGroup Label="dotnet pack instructions">`將目的檔案放入包內的*生成*資料夾中。</span><span class="sxs-lookup"><span data-stu-id="21554-179">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="21554-180">該`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`元素將程式集和 *.json*檔放入*生成*資料夾中。</span><span class="sxs-lookup"><span data-stu-id="21554-180">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="21554-181">要在專案中使用自訂目標，請添加指向`PackageReference`包及其版本的元素。</span><span class="sxs-lookup"><span data-stu-id="21554-181">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="21554-182">與工具不同，自訂目標包包含在使用項的依賴項關閉中。</span><span class="sxs-lookup"><span data-stu-id="21554-182">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="21554-183">您可以配置如何使用自訂目標。</span><span class="sxs-lookup"><span data-stu-id="21554-183">You can configure how to use the custom target.</span></span> <span data-ttu-id="21554-184">由於它是 MSBuild 目標，它可以依賴于給定的目標、在另一個目標之後運行，或者使用 命令`dotnet msbuild -t:<target-name>`手動調用。</span><span class="sxs-lookup"><span data-stu-id="21554-184">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="21554-185">但是，為了提供更好的使用者體驗，您可以合併每個專案工具和自訂目標。</span><span class="sxs-lookup"><span data-stu-id="21554-185">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="21554-186">在這種情況下，每個專案工具接受所需的任何參數，並將其轉換為執行目標所需的[`dotnet msbuild`](../tools/dotnet-msbuild.md)調用。</span><span class="sxs-lookup"><span data-stu-id="21554-186">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="21554-187">您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。</span><span class="sxs-lookup"><span data-stu-id="21554-187">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="21554-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21554-188">See also</span></span>

- [<span data-ttu-id="21554-189">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="21554-189">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="21554-190">如何使用 MSBuild 專案 SDK</span><span class="sxs-lookup"><span data-stu-id="21554-190">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="21554-191">使用 NuGet 打包自訂 MSBuild 目標和道具</span><span class="sxs-lookup"><span data-stu-id="21554-191">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
