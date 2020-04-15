---
title: .NET 核心專案 SDK 概述
description: 瞭解 .NET 核心專案 SDK。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: d0ac01dca31dffea482745126e00c34b1da20774
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389661"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="b6fab-103">.NET 核心專案 SDK</span><span class="sxs-lookup"><span data-stu-id="b6fab-103">.NET Core project SDKs</span></span>

<span data-ttu-id="b6fab-104">.NET 核心專案與軟體開發工具組 (SDK) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="b6fab-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="b6fab-105">每個專案*SDK*是一組 MSBuild[目標](/visualstudio/msbuild/msbuild-targets)和相關[任務](/visualstudio/msbuild/msbuild-tasks),負責編譯、打包和發佈代碼。</span><span class="sxs-lookup"><span data-stu-id="b6fab-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="b6fab-106">參考專案 SDK 的項目有時為*SDK 樣式專案*。</span><span class="sxs-lookup"><span data-stu-id="b6fab-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="b6fab-107">可用 SDK</span><span class="sxs-lookup"><span data-stu-id="b6fab-107">Available SDKs</span></span>

<span data-ttu-id="b6fab-108">以下 SDK 可用於 .NET 核心:</span><span class="sxs-lookup"><span data-stu-id="b6fab-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="b6fab-109">ID</span><span class="sxs-lookup"><span data-stu-id="b6fab-109">ID</span></span> | <span data-ttu-id="b6fab-110">描述</span><span class="sxs-lookup"><span data-stu-id="b6fab-110">Description</span></span> | <span data-ttu-id="b6fab-111">回購</span><span class="sxs-lookup"><span data-stu-id="b6fab-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="b6fab-112">.NET 核心 SDK</span><span class="sxs-lookup"><span data-stu-id="b6fab-112">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="b6fab-113">.NET 核心[Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="b6fab-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="b6fab-114">.NET 核心[剃刀 SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="b6fab-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="b6fab-115">.NET 核心工作人員服務 SDK</span><span class="sxs-lookup"><span data-stu-id="b6fab-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="b6fab-116">.NET 核心贏形和 WPF SDK</span><span class="sxs-lookup"><span data-stu-id="b6fab-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="b6fab-117">.NET 核心 SDK 是 .NET 核心的基本 SDK。</span><span class="sxs-lookup"><span data-stu-id="b6fab-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="b6fab-118">其他 SDK 引用 .NET 核心 SDK,與其他 SDK 關聯的專案具有所有可用的 .NET Core SDK 屬性。</span><span class="sxs-lookup"><span data-stu-id="b6fab-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="b6fab-119">例如,Web SDK 取決於 .NET 核心 SDK 和 Razor SDK。</span><span class="sxs-lookup"><span data-stu-id="b6fab-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="b6fab-120">您還可以創作自己的 SDK,這些 SDK 可透過 NuGet 進行分發。</span><span class="sxs-lookup"><span data-stu-id="b6fab-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="b6fab-121">專案檔</span><span class="sxs-lookup"><span data-stu-id="b6fab-121">Project files</span></span>

<span data-ttu-id="b6fab-122">.NET 核心項目基於[MSBuild](/visualstudio/msbuild/msbuild)格式。</span><span class="sxs-lookup"><span data-stu-id="b6fab-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="b6fab-123">專案檔具有像 C# 專案的 *.csproj*和*F# 專案的 .fsproj*這樣的擴展名,它們採用 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="b6fab-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="b6fab-124">MSBuild 專案檔的根元素是[專案](/visualstudio/msbuild/project-element-msbuild)元素。</span><span class="sxs-lookup"><span data-stu-id="b6fab-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="b6fab-125">該`Project`元素具有一`Sdk`個 可選屬性,用於指定要使用的 SDK(和版本)。</span><span class="sxs-lookup"><span data-stu-id="b6fab-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="b6fab-126">要使用 .NET Core 工具並生成`Sdk`代碼,請將屬性設置為[可用 SDK](#available-sdks)表中的其中一個 ID。</span><span class="sxs-lookup"><span data-stu-id="b6fab-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="b6fab-127">要指定來自 NuGet 的 SDK,請在名稱末尾包括版本,或在*global.json*檔中指定名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="b6fab-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="b6fab-128">指定 SDK 的另一種方法是使用頂級[SDK](/visualstudio/msbuild/sdk-element-msbuild)元素:</span><span class="sxs-lookup"><span data-stu-id="b6fab-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="b6fab-129">以以下方式之一引用 SDK 大大簡化了 .NET Core 的專案檔。</span><span class="sxs-lookup"><span data-stu-id="b6fab-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="b6fab-130">在評估專案時,MSBuild 在專案檔的`Sdk.props`頂部`Sdk.targets`和底部添加了隱式導入。</span><span class="sxs-lookup"><span data-stu-id="b6fab-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="b6fab-131">在 Windows 電腦上 *,Sdk.props*和*Sdk.target*檔案可以在 *%程式檔%_dotnet_sdk\\[版本]Sdks_Microsoft.NET.Sdk_Sdk*資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="b6fab-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="b6fab-132">預寫專案檔案</span><span class="sxs-lookup"><span data-stu-id="b6fab-132">Preprocess the project file</span></span>

<span data-ttu-id="b6fab-133">在 SDK 及其目標包含在 SDK 之後,您可以看到完全擴展`dotnet msbuild -preprocess`的專案,使用命令包括該專案。</span><span class="sxs-lookup"><span data-stu-id="b6fab-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="b6fab-134">命令[preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)的預[`dotnet msbuild`](../tools/dotnet-msbuild.md)處理開關顯示導入的檔、其源及其對生成的貢獻,而無需實際生成專案。</span><span class="sxs-lookup"><span data-stu-id="b6fab-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="b6fab-135">如果專案有多個目標框架,則將命令的結果僅將其指定為 MSBuild 屬性,將命令的結果集中在一個框架上。</span><span class="sxs-lookup"><span data-stu-id="b6fab-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="b6fab-136">例如：</span><span class="sxs-lookup"><span data-stu-id="b6fab-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="b6fab-137">預設編譯包括</span><span class="sxs-lookup"><span data-stu-id="b6fab-137">Default compilation includes</span></span>

<span data-ttu-id="b6fab-138">編譯項的預設值包括和排除,嵌入資源在 SDK 中定義。</span><span class="sxs-lookup"><span data-stu-id="b6fab-138">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="b6fab-139">與非 SDK .NET 框架專案不同,您不需要在專案檔中指定這些項目,因為預設值涵蓋最常見的用例。</span><span class="sxs-lookup"><span data-stu-id="b6fab-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="b6fab-140">這將導致較小的專案檔,更容易理解,以及手動編輯,如果需要的話。</span><span class="sxs-lookup"><span data-stu-id="b6fab-140">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="b6fab-141">下表顯示了 .NET 核心 SDK 中包括和排除哪些元素和哪些[globs:](https://en.wikipedia.org/wiki/Glob_(programming))</span><span class="sxs-lookup"><span data-stu-id="b6fab-141">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="b6fab-142">項目</span><span class="sxs-lookup"><span data-stu-id="b6fab-142">Element</span></span>           | <span data-ttu-id="b6fab-143">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="b6fab-143">Include glob</span></span>                              | <span data-ttu-id="b6fab-144">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="b6fab-144">Exclude glob</span></span>                                                  | <span data-ttu-id="b6fab-145">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="b6fab-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="b6fab-146">編譯</span><span class="sxs-lookup"><span data-stu-id="b6fab-146">Compile</span></span>           | <span data-ttu-id="b6fab-147">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="b6fab-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="b6fab-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b6fab-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="b6fab-149">N/A</span><span class="sxs-lookup"><span data-stu-id="b6fab-149">N/A</span></span>                      |
| <span data-ttu-id="b6fab-150">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="b6fab-150">EmbeddedResource</span></span>  | <span data-ttu-id="b6fab-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b6fab-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="b6fab-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b6fab-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b6fab-153">N/A</span><span class="sxs-lookup"><span data-stu-id="b6fab-153">N/A</span></span>                      |
| <span data-ttu-id="b6fab-154">None</span><span class="sxs-lookup"><span data-stu-id="b6fab-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="b6fab-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b6fab-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b6fab-156">\*\*/\*.cs、\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b6fab-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="b6fab-157">預設情況下`./bin`,`./obj``$(BaseOutputPath)`由`$(BaseIntermediateOutputPath)`和 MSBuild 屬性表示 的和 資料夾從 globs 中排除。</span><span class="sxs-lookup"><span data-stu-id="b6fab-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="b6fab-158">排除由屬性`$(DefaultItemExcludes)`表示。</span><span class="sxs-lookup"><span data-stu-id="b6fab-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="b6fab-159">如果在項目檔中顯示式定義這些項目,則可能會收到以下錯誤:</span><span class="sxs-lookup"><span data-stu-id="b6fab-159">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="b6fab-160">**包括重複編譯項。默認情況下,.NET SDK 包括專案目錄中的編譯項。如果要在專案檔中顯式包含這些專案,可以從專案檔中刪除這些專案,也可以將"啟用預設編譯專案"屬性設置為"false"。**</span><span class="sxs-lookup"><span data-stu-id="b6fab-160">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="b6fab-161">要解決錯誤,請刪除與上表中`Compile`列出的隱式項匹配的顯式項,或`EnableDefaultCompileItems`將 屬性`false`設定為 ,該屬性將禁用隱式包含:</span><span class="sxs-lookup"><span data-stu-id="b6fab-161">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="b6fab-162">例如,如果要指定某些要隨應用發佈的檔,您仍可以使用已知的 MSBuild 機制`Content`,例如元素。</span><span class="sxs-lookup"><span data-stu-id="b6fab-162">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="b6fab-163">`EnableDefaultCompileItems`僅禁用`Compile`globs,但不會影響其他 globs,如`None`\*也適用於 .cs 項的隱式 glob。</span><span class="sxs-lookup"><span data-stu-id="b6fab-163">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="b6fab-164">因此,視覺化工作室中的解決方案資源管理員將 .cs 項作為專案的一部分進行\*,`None`作為專案包含在內。</span><span class="sxs-lookup"><span data-stu-id="b6fab-164">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="b6fab-165">要關閉隱用的`None``EnableDefaultNoneItems`glob,`false`請設定為 :</span><span class="sxs-lookup"><span data-stu-id="b6fab-165">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="b6fab-166">要關閉*所有*隱式 globs,`EnableDefaultItems`請`false`將 屬性設定為 :</span><span class="sxs-lookup"><span data-stu-id="b6fab-166">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="b6fab-167">自訂產生</span><span class="sxs-lookup"><span data-stu-id="b6fab-167">Customize the build</span></span>

<span data-ttu-id="b6fab-168">有各種方法來[自訂產生](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="b6fab-168">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="b6fab-169">您可能希望透過將屬性作為參數傳遞給[msbuild](/visualstudio/msbuild/msbuild-command-line-reference)或[dotnet](../tools/index.md)命令來覆蓋該屬性。</span><span class="sxs-lookup"><span data-stu-id="b6fab-169">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="b6fab-170">您還可以將屬性加入項目檔案或*目錄.Build.props 檔案*。</span><span class="sxs-lookup"><span data-stu-id="b6fab-170">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="b6fab-171">有關 .NET Core 專案的有用屬性清單,請參閱[.NET Core SDK 專案的 MSBuild 屬性](msbuild-props.md)。</span><span class="sxs-lookup"><span data-stu-id="b6fab-171">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="b6fab-172">自訂目標</span><span class="sxs-lookup"><span data-stu-id="b6fab-172">Custom targets</span></span>

<span data-ttu-id="b6fab-173">.NET Core 專案可以打包自定義 MSBuild 目標和屬性,供使用包的專案使用。</span><span class="sxs-lookup"><span data-stu-id="b6fab-173">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="b6fab-174">當您想要:</span><span class="sxs-lookup"><span data-stu-id="b6fab-174">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="b6fab-175">擴展生成過程。</span><span class="sxs-lookup"><span data-stu-id="b6fab-175">Extend the build process.</span></span>
- <span data-ttu-id="b6fab-176">訪問生成過程的專案,如生成的檔。</span><span class="sxs-lookup"><span data-stu-id="b6fab-176">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="b6fab-177">檢查調用生成的配置。</span><span class="sxs-lookup"><span data-stu-id="b6fab-177">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="b6fab-178">以將`<package_id>.targets`檔案放在窗體中`<package_id>.props`或 (`Contoso.Utility.UsefulStuff.targets`例如) 在專案的*生成*資料夾中來添加自定義生成目標或屬性。</span><span class="sxs-lookup"><span data-stu-id="b6fab-178">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="b6fab-179">以下 XML 是 *.csproj*檔中的[`dotnet pack`](../tools/dotnet-pack.md)一個片段, 用於指示命令打包什麼。</span><span class="sxs-lookup"><span data-stu-id="b6fab-179">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="b6fab-180">元素`<ItemGroup Label="dotnet pack instructions">`將目標檔放入包內的*生成*資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b6fab-180">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="b6fab-181">該`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`元素將程式集和 *.json*檔放入*生成*資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b6fab-181">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="b6fab-182">要在專案中使用自定義目標,請添加指向`PackageReference`包及其版本的元素。</span><span class="sxs-lookup"><span data-stu-id="b6fab-182">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="b6fab-183">與工具不同,自定義目標包包含在使用項的依賴項關閉中。</span><span class="sxs-lookup"><span data-stu-id="b6fab-183">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="b6fab-184">您可以設定如何使用自定義目標。</span><span class="sxs-lookup"><span data-stu-id="b6fab-184">You can configure how to use the custom target.</span></span> <span data-ttu-id="b6fab-185">由於它是 MSBuild 目標,它可以依賴於給定的目標、在另一個目標之後運行,或者`dotnet msbuild -t:<target-name>`使用命令手動調用。</span><span class="sxs-lookup"><span data-stu-id="b6fab-185">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="b6fab-186">但是,為了提供更好的用戶體驗,您可以合併每個專案工具和自定義目標。</span><span class="sxs-lookup"><span data-stu-id="b6fab-186">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="b6fab-187">在這種情況下,每個專案工具接受所需的任何參數,並將其轉換為執行目標所需的[`dotnet msbuild`](../tools/dotnet-msbuild.md)調用。</span><span class="sxs-lookup"><span data-stu-id="b6fab-187">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="b6fab-188">您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。</span><span class="sxs-lookup"><span data-stu-id="b6fab-188">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6fab-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6fab-189">See also</span></span>

- [<span data-ttu-id="b6fab-190">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="b6fab-190">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="b6fab-191">如何使用 MSBuild 專案 SDK</span><span class="sxs-lookup"><span data-stu-id="b6fab-191">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="b6fab-192">使用 NuGet 打包自訂 MSBuild 目標和道具</span><span class="sxs-lookup"><span data-stu-id="b6fab-192">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
