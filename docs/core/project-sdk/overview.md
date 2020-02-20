---
title: .NET Core 專案 SDK 總覽
description: 深入瞭解 .NET Core 專案 Sdk。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: b1b839f81b1b4a8d20dbb34d3d2fc000c64acb8a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453801"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="e28ba-103">.NET Core 專案 Sdk</span><span class="sxs-lookup"><span data-stu-id="e28ba-103">.NET Core project SDKs</span></span>

<span data-ttu-id="e28ba-104">.NET Core 專案與軟體發展工具組（SDK）相關聯。</span><span class="sxs-lookup"><span data-stu-id="e28ba-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="e28ba-105">每個專案 SDK 都是一組 MSBuild[目標](/visualstudio/msbuild/msbuild-targets)和[相關聯](/visualstudio/msbuild/msbuild-tasks)的工作，負責編譯、封裝和發行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e28ba-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="e28ba-106">可用的 Sdk</span><span class="sxs-lookup"><span data-stu-id="e28ba-106">Available SDKs</span></span>

<span data-ttu-id="e28ba-107">下列 Sdk 適用于 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="e28ba-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="e28ba-108">ID</span><span class="sxs-lookup"><span data-stu-id="e28ba-108">ID</span></span> | <span data-ttu-id="e28ba-109">描述</span><span class="sxs-lookup"><span data-stu-id="e28ba-109">Description</span></span> | <span data-ttu-id="e28ba-110">存放庫</span><span class="sxs-lookup"><span data-stu-id="e28ba-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="e28ba-111">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e28ba-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="e28ba-112">.NET Core [WEB SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="e28ba-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="e28ba-113">.NET Core [RAZOR SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="e28ba-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="e28ba-114">.NET Core 背景工作角色服務 SDK</span><span class="sxs-lookup"><span data-stu-id="e28ba-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="e28ba-115">.NET Core WinForms 和 WPF SDK</span><span class="sxs-lookup"><span data-stu-id="e28ba-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="e28ba-116">.NET Core SDK 是適用于 .NET Core 的基底 SDK。</span><span class="sxs-lookup"><span data-stu-id="e28ba-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="e28ba-117">其他 Sdk 會參考 .NET Core SDK，而與其他 Sdk 相關聯的專案則具有所有可用的 .NET Core SDK 屬性。</span><span class="sxs-lookup"><span data-stu-id="e28ba-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="e28ba-118">例如，Web SDK 取決於 .NET Core SDK 和 Razor SDK。</span><span class="sxs-lookup"><span data-stu-id="e28ba-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="e28ba-119">您也可以撰寫自己的 SDK，以透過 NuGet 散發。</span><span class="sxs-lookup"><span data-stu-id="e28ba-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="e28ba-120">專案檔</span><span class="sxs-lookup"><span data-stu-id="e28ba-120">Project files</span></span>

<span data-ttu-id="e28ba-121">.NET Core 專案是以[MSBuild](/visualstudio/msbuild/msbuild)格式為基礎。</span><span class="sxs-lookup"><span data-stu-id="e28ba-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="e28ba-122">專案檔，其副檔名如 *.csproj*適用于C#專案，而 *.fsproj*用於F#專案，則為 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="e28ba-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="e28ba-123">MSBuild 專案檔的根項目是[專案](/msbuild/project-element-msbuild)元素。</span><span class="sxs-lookup"><span data-stu-id="e28ba-123">The root element of an MSBuild project file is the [Project](/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="e28ba-124">`Project` 元素具有選擇性的 `Sdk` 屬性，可指定要使用的 SDK （和版本）。</span><span class="sxs-lookup"><span data-stu-id="e28ba-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="e28ba-125">若要使用 .NET Core 工具並建立您的程式碼，請將 `Sdk` 屬性設定為[可用 sdk](#available-sdks)資料表中的其中一個識別碼。</span><span class="sxs-lookup"><span data-stu-id="e28ba-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="e28ba-126">若要指定來自 NuGet 的 SDK，請在名稱結尾包含版本，或指定*global.asax*檔案中的名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="e28ba-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="e28ba-127">另一個指定 SDK 的方法是使用最上層[SDK](/visualstudio/msbuild/sdk-element-msbuild)元素：</span><span class="sxs-lookup"><span data-stu-id="e28ba-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="e28ba-128">以下列其中一種方式參考 SDK，可大幅簡化 .NET Core 的專案檔案。</span><span class="sxs-lookup"><span data-stu-id="e28ba-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="e28ba-129">評估專案時，MSBuild 會在專案檔頂端新增 `Sdk.props` 的隱含匯入，並在底部 `Sdk.targets`。</span><span class="sxs-lookup"><span data-stu-id="e28ba-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="e28ba-130">在 Windows 電腦上，您可以在 *%ProgramFiles%\dotnet\sdk\\[version] \Sdks\Microsoft.NET.Sdk\Sdk*資料夾中找到 *.props*和*sdk .targets*檔案。</span><span class="sxs-lookup"><span data-stu-id="e28ba-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="e28ba-131">前置處理專案檔</span><span class="sxs-lookup"><span data-stu-id="e28ba-131">Preprocess the project file</span></span>

<span data-ttu-id="e28ba-132">在 SDK 之後，您可以看到完全展開的專案，而它的目標是使用 `dotnet msbuild -preprocess` 命令所包含。</span><span class="sxs-lookup"><span data-stu-id="e28ba-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="e28ba-133">[`dotnet msbuild`](../tools/dotnet-msbuild.md)命令的前置[處理參數會](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)顯示哪些檔案已匯入、其來源，以及其對組建的貢獻，而不需要實際建立專案。</span><span class="sxs-lookup"><span data-stu-id="e28ba-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="e28ba-134">如果專案有多個目標架構，請將命令的結果指定為 MSBuild 屬性，只將其焦點放在一個架構上。</span><span class="sxs-lookup"><span data-stu-id="e28ba-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="e28ba-135">例如：</span><span class="sxs-lookup"><span data-stu-id="e28ba-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="e28ba-136">預設編譯包括</span><span class="sxs-lookup"><span data-stu-id="e28ba-136">Default compilation includes</span></span>

<span data-ttu-id="e28ba-137">編譯專案的預設 [包含] 和 [排除]，以及在 SDK 中定義的內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="e28ba-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="e28ba-138">不同于非 SDK .NET Framework 專案，您不需要在專案檔中指定這些專案，因為預設值會涵蓋最常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="e28ba-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="e28ba-139">這會導致較小的專案檔，而且更容易瞭解，並視需要手動編輯。</span><span class="sxs-lookup"><span data-stu-id="e28ba-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="e28ba-140">下表顯示 .NET Core SDK 中包含和排除的元素和哪些[glob](https://en.wikipedia.org/wiki/Glob_(programming)) ：</span><span class="sxs-lookup"><span data-stu-id="e28ba-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="e28ba-141">元素</span><span class="sxs-lookup"><span data-stu-id="e28ba-141">Element</span></span>           | <span data-ttu-id="e28ba-142">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="e28ba-142">Include glob</span></span>                              | <span data-ttu-id="e28ba-143">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="e28ba-143">Exclude glob</span></span>                                                  | <span data-ttu-id="e28ba-144">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="e28ba-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="e28ba-145">編譯</span><span class="sxs-lookup"><span data-stu-id="e28ba-145">Compile</span></span>           | <span data-ttu-id="e28ba-146">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="e28ba-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="e28ba-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e28ba-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="e28ba-148">N/A</span><span class="sxs-lookup"><span data-stu-id="e28ba-148">N/A</span></span>                      |
| <span data-ttu-id="e28ba-149">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="e28ba-149">EmbeddedResource</span></span>  | <span data-ttu-id="e28ba-150">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="e28ba-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="e28ba-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e28ba-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="e28ba-152">N/A</span><span class="sxs-lookup"><span data-stu-id="e28ba-152">N/A</span></span>                      |
| <span data-ttu-id="e28ba-153">None</span><span class="sxs-lookup"><span data-stu-id="e28ba-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="e28ba-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e28ba-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="e28ba-155">\*\*/\*.cs、\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="e28ba-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="e28ba-156">[`./bin`] 和 [`./obj`] 資料夾（由 `$(BaseOutputPath)` 和 `$(BaseIntermediateOutputPath)` MSBuild 屬性工作表示）預設會從 glob 中排除。</span><span class="sxs-lookup"><span data-stu-id="e28ba-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="e28ba-157">[排除] 是以屬性 `$(DefaultItemExcludes)`表示。</span><span class="sxs-lookup"><span data-stu-id="e28ba-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="e28ba-158">如果您在專案檔中明確定義這些專案，您可能會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="e28ba-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="e28ba-159">**包含重複的編譯專案。根據預設，.NET SDK 會包含專案目錄中的編譯專案。您可以從專案檔中移除這些專案，或者，如果您想要在專案檔中明確包含 ' EnableDefaultCompileItems ' 屬性，請將其設定為 ' false '。**</span><span class="sxs-lookup"><span data-stu-id="e28ba-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="e28ba-160">若要解決此錯誤，請移除符合上表所列隱含專案的明確 `Compile` 專案，或將 `EnableDefaultCompileItems` 屬性設定為 `false`，這會停用隱含包含：</span><span class="sxs-lookup"><span data-stu-id="e28ba-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="e28ba-161">例如，如果您想要指定一些檔案來與您的應用程式一起發佈，您仍然可以使用已知的 MSBuild 機制，例如，`Content` 元素。</span><span class="sxs-lookup"><span data-stu-id="e28ba-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="e28ba-162">`EnableDefaultCompileItems` 只會停用 `Compile` glob，但不會影響其他 glob，例如也適用于 \*.cs 專案的隱含 `None` glob。</span><span class="sxs-lookup"><span data-stu-id="e28ba-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="e28ba-163">因此，方案總管在 Visual Studio 會將 \*.cs 專案顯示為專案的一部分，包括做為 `None` 專案。</span><span class="sxs-lookup"><span data-stu-id="e28ba-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="e28ba-164">若要停用隱含 `None` glob，請將 `EnableDefaultNoneItems` 設定為 `false`：</span><span class="sxs-lookup"><span data-stu-id="e28ba-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="e28ba-165">若要停用*所有*隱含 glob，請將 `EnableDefaultItems` 屬性設定為 `false`：</span><span class="sxs-lookup"><span data-stu-id="e28ba-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="e28ba-166">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="e28ba-166">Customize the build</span></span>

<span data-ttu-id="e28ba-167">有各種方式可[自訂群組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="e28ba-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="e28ba-168">您可能想要覆寫屬性，方法是將它當做引數傳遞給[msbuild](/visualstudio/msbuild/msbuild-command-line-reference)或[dotnet](../tools/index.md)命令。</span><span class="sxs-lookup"><span data-stu-id="e28ba-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="e28ba-169">您也可以將屬性加入至專案檔或 *.props*檔案。</span><span class="sxs-lookup"><span data-stu-id="e28ba-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="e28ba-170">如需 .NET Core 專案的實用屬性清單，請參閱[.NET Core SDK 專案的 MSBuild 屬性](msbuild-props.md)。</span><span class="sxs-lookup"><span data-stu-id="e28ba-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e28ba-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e28ba-171">See also</span></span>

- [<span data-ttu-id="e28ba-172">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="e28ba-172">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="e28ba-173">如何使用 MSBuild 專案 Sdk</span><span class="sxs-lookup"><span data-stu-id="e28ba-173">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
