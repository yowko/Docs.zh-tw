---
title: .NET Core 專案 SDK 總覽
titleSuffix: ''
description: 深入瞭解 .NET Core 專案 Sdk。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 873c06007307c5892c4828f987486b4dd98dc9ae
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187921"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="6b67d-103">.NET Core 專案 Sdk</span><span class="sxs-lookup"><span data-stu-id="6b67d-103">.NET Core project SDKs</span></span>

<span data-ttu-id="6b67d-104">.NET Core 專案與軟體發展工具組 (SDK) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="6b67d-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="6b67d-105">每個 *專案 SDK* 都是一組 MSBuild [目標](/visualstudio/msbuild/msbuild-targets) 和相關聯的工作，負責編譯、封裝和 [發行程式碼](/visualstudio/msbuild/msbuild-tasks) 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="6b67d-106">參考專案 SDK 的專案有時也稱為「 *SDK 樣式專案*」。</span><span class="sxs-lookup"><span data-stu-id="6b67d-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="6b67d-107">可用的 Sdk</span><span class="sxs-lookup"><span data-stu-id="6b67d-107">Available SDKs</span></span>

<span data-ttu-id="6b67d-108">下列 Sdk 適用于 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="6b67d-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="6b67d-109">ID</span><span class="sxs-lookup"><span data-stu-id="6b67d-109">ID</span></span> | <span data-ttu-id="6b67d-110">描述</span><span class="sxs-lookup"><span data-stu-id="6b67d-110">Description</span></span> | <span data-ttu-id="6b67d-111">存放庫</span><span class="sxs-lookup"><span data-stu-id="6b67d-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="6b67d-112">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6b67d-112">The .NET Core SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="6b67d-113">.NET Core [WEB SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="6b67d-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="6b67d-114">.NET Core [RAZOR SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="6b67d-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="6b67d-115">.NET Core 背景工作角色服務 SDK</span><span class="sxs-lookup"><span data-stu-id="6b67d-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="6b67d-116">.NET Core WinForms 和 WPF SDK</span><span class="sxs-lookup"><span data-stu-id="6b67d-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="6b67d-117">.NET Core SDK 是適用于 .NET Core 的基底 SDK。</span><span class="sxs-lookup"><span data-stu-id="6b67d-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="6b67d-118">其他 Sdk 會參考 .NET Core SDK，而與其他 Sdk 相關聯的專案則具有所有可用的 .NET Core SDK 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b67d-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="6b67d-119">例如，Web SDK 取決於 .NET Core SDK 和 Razor SDK。</span><span class="sxs-lookup"><span data-stu-id="6b67d-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="6b67d-120">您也可以撰寫自己的 SDK，以透過 NuGet 散發。</span><span class="sxs-lookup"><span data-stu-id="6b67d-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="6b67d-121">專案檔</span><span class="sxs-lookup"><span data-stu-id="6b67d-121">Project files</span></span>

<span data-ttu-id="6b67d-122">.NET Core 專案是以 [MSBuild](/visualstudio/msbuild/msbuild) 格式為基礎。</span><span class="sxs-lookup"><span data-stu-id="6b67d-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="6b67d-123">專案檔，其副檔名如 *.csproj* （適用于 c # 專案）和 *.fsproj* （適用于 F # 專案）都是 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="6b67d-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="6b67d-124">MSBuild 專案檔的根項目是 [專案](/visualstudio/msbuild/project-element-msbuild) 元素。</span><span class="sxs-lookup"><span data-stu-id="6b67d-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="6b67d-125">`Project`元素具有選擇性 `Sdk` 屬性，可指定要使用哪個 SDK (和版本) 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="6b67d-126">若要使用 .NET Core 工具並建立您的程式碼，請將 `Sdk` 屬性設定為 [可用 sdk](#available-sdks) 資料表中的其中一個識別碼。</span><span class="sxs-lookup"><span data-stu-id="6b67d-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="6b67d-127">若要指定來自 NuGet 的 SDK，請在名稱結尾包含版本，或在檔案的 *global.js* 中指定名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="6b67d-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="6b67d-128">另一個指定 SDK 的方法是使用最上層 [SDK](/visualstudio/msbuild/sdk-element-msbuild) 元素：</span><span class="sxs-lookup"><span data-stu-id="6b67d-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="6b67d-129">以下列其中一種方式參考 SDK，可大幅簡化 .NET Core 的專案檔案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="6b67d-130">評估專案時，MSBuild 會 `Sdk.props` 在專案檔的頂端和底部新增隱含的匯入 `Sdk.targets` 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="6b67d-131">在 Windows 電腦上，您可以在 *%ProgramFiles%\dotnet\sdk \\ [version] \Sdks\Microsoft.NET.Sdk\Sdk*資料夾中找到 *.props*和*sdk .targets*檔案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="6b67d-132">前置處理專案檔</span><span class="sxs-lookup"><span data-stu-id="6b67d-132">Preprocess the project file</span></span>

<span data-ttu-id="6b67d-133">您可以看到在 SDK 之後，MSBuild 會看到完全展開的專案，而其目標則是使用命令所包含 `dotnet msbuild -preprocess` 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="6b67d-134">命令[preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)的前置處理參數 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 會顯示哪些檔案已匯入、其來源，以及它們對組建的貢獻，而不需要實際建立專案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="6b67d-135">如果專案有多個目標架構，請將命令的結果指定為 MSBuild 屬性，只將其焦點放在一個架構上。</span><span class="sxs-lookup"><span data-stu-id="6b67d-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="6b67d-136">例如：</span><span class="sxs-lookup"><span data-stu-id="6b67d-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="6b67d-137">預設編譯包括</span><span class="sxs-lookup"><span data-stu-id="6b67d-137">Default compilation includes</span></span>

<span data-ttu-id="6b67d-138">在 SDK 中定義了編譯專案、內嵌資源和專案的預設值 [包含] 和 [排除] `None` 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="6b67d-139">不同于非 SDK .NET Framework 專案，您不需要在專案檔中指定這些專案，因為預設值會涵蓋最常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="6b67d-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="6b67d-140">這可讓專案檔變得更小且更容易瞭解，並視需要手動進行編輯。</span><span class="sxs-lookup"><span data-stu-id="6b67d-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="6b67d-141">下表顯示 .NET Core SDK 中包含和排除哪些元素和哪些 [glob](https://en.wikipedia.org/wiki/Glob_(programming)) ：</span><span class="sxs-lookup"><span data-stu-id="6b67d-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="6b67d-142">元素</span><span class="sxs-lookup"><span data-stu-id="6b67d-142">Element</span></span>           | <span data-ttu-id="6b67d-143">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="6b67d-143">Include glob</span></span>                              | <span data-ttu-id="6b67d-144">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="6b67d-144">Exclude glob</span></span>                                                  | <span data-ttu-id="6b67d-145">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="6b67d-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="6b67d-146">編譯</span><span class="sxs-lookup"><span data-stu-id="6b67d-146">Compile</span></span>           | <span data-ttu-id="6b67d-147">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="6b67d-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="6b67d-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6b67d-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="6b67d-149">N/A</span><span class="sxs-lookup"><span data-stu-id="6b67d-149">N/A</span></span>                      |
| <span data-ttu-id="6b67d-150">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="6b67d-150">EmbeddedResource</span></span>  | <span data-ttu-id="6b67d-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="6b67d-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="6b67d-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6b67d-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6b67d-153">N/A</span><span class="sxs-lookup"><span data-stu-id="6b67d-153">N/A</span></span>                      |
| <span data-ttu-id="6b67d-154">無</span><span class="sxs-lookup"><span data-stu-id="6b67d-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="6b67d-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6b67d-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6b67d-156">\*\*/\*.cs、\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="6b67d-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="6b67d-157">和 `./bin` `./obj` MSBuild 屬性所表示的和資料夾 `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` 預設會從 glob 中排除。</span><span class="sxs-lookup"><span data-stu-id="6b67d-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="6b67d-158">排除會以屬性工作表示 `$(DefaultItemExcludes)` 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="6b67d-159">建置錯誤</span><span class="sxs-lookup"><span data-stu-id="6b67d-159">Build errors</span></span>

<span data-ttu-id="6b67d-160">如果您在專案檔中明確定義這些專案，您可能會收到類似下列的「NETSDK1022」組建錯誤：</span><span class="sxs-lookup"><span data-stu-id="6b67d-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="6b67d-161">包含重複的 ' Compile ' 專案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="6b67d-162">根據預設，.NET SDK 會包含專案目錄中的「編譯」專案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="6b67d-163">您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。</span><span class="sxs-lookup"><span data-stu-id="6b67d-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="6b67d-164">包含重複的 ' EmbeddedResource ' 專案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="6b67d-165">根據預設，.NET SDK 會在您的專案目錄中包含 ' EmbeddedResource ' 專案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="6b67d-166">您可以從專案檔中移除這些專案，或者，如果您想要在專案檔中明確包含 ' EnableDefaultEmbeddedResourceItems ' 屬性，請將其設定為 ' false '。</span><span class="sxs-lookup"><span data-stu-id="6b67d-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="6b67d-167">若要解決錯誤，請執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="6b67d-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="6b67d-168">移除 `Compile` `EmbeddedResource` `None` 符合上表所列隱含專案的明確、或專案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="6b67d-169">將 `EnableDefaultItems` 屬性設定為 `false` ，以停用所有隱含檔案包含：</span><span class="sxs-lookup"><span data-stu-id="6b67d-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="6b67d-170">如果您想要指定要與您的應用程式一起發佈的檔案，您仍然可以針對該專案使用已知的 MSBuild 機制，例如 `Content` 元素。</span><span class="sxs-lookup"><span data-stu-id="6b67d-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="6b67d-171">藉 `Compile` `EmbeddedResource` `None` 由將 `EnableDefaultCompileItems` 、 `EnableDefaultEmbeddedResourceItems` 或 `EnableDefaultNoneItems` 屬性設定為 `false` ，選擇性地停用、或 glob：</span><span class="sxs-lookup"><span data-stu-id="6b67d-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="6b67d-172">如果您只停 `Compile` 用 glob，Visual Studio 中的方案總管仍會 \* 將 .cs 專案顯示為專案的一部分，包括做為 `None` 專案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="6b67d-173">若要停用隱含 `None` glob，請將設 `EnableDefaultNoneItems` 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="6b67d-174">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="6b67d-174">Customize the build</span></span>

<span data-ttu-id="6b67d-175">有各種方式可 [自訂群組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="6b67d-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="6b67d-176">您可能想要覆寫屬性，方法是將它當做引數傳遞給 [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) 或 [dotnet](../tools/index.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="6b67d-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="6b67d-177">您也可以將屬性加入至專案檔或 *.props* 檔案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="6b67d-178">如需 .NET Core 專案的實用屬性清單，請參閱 [.NET Core SDK 專案的 MSBuild 參考](msbuild-props.md)。</span><span class="sxs-lookup"><span data-stu-id="6b67d-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="6b67d-179">自訂目標</span><span class="sxs-lookup"><span data-stu-id="6b67d-179">Custom targets</span></span>

<span data-ttu-id="6b67d-180">.NET Core 專案可以封裝自訂的 MSBuild 目標和屬性，以供取用套件的專案使用。</span><span class="sxs-lookup"><span data-stu-id="6b67d-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="6b67d-181">當您想要執行下列動作時，請使用這類型的擴充性：</span><span class="sxs-lookup"><span data-stu-id="6b67d-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="6b67d-182">擴充組建進程。</span><span class="sxs-lookup"><span data-stu-id="6b67d-182">Extend the build process.</span></span>
- <span data-ttu-id="6b67d-183">存取組建進程的構件，例如產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="6b67d-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="6b67d-184">檢查用來叫用組建的設定。</span><span class="sxs-lookup"><span data-stu-id="6b67d-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="6b67d-185">您可以新增自訂群組建目標或屬性，方法是將檔案放在表單 `<package_id>.targets` 或 `<package_id>.props` (中，例如， `Contoso.Utility.UsefulStuff.targets`) 在專案的 [ *組建* ] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6b67d-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="6b67d-186">下列 XML 是來自 *.csproj* 檔案的程式碼片段，可指示 [`dotnet pack`](../tools/dotnet-pack.md) 命令要封裝的內容。</span><span class="sxs-lookup"><span data-stu-id="6b67d-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="6b67d-187">元素會將 `<ItemGroup Label="dotnet pack instructions">` 目標檔案放入封裝內的 *build* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6b67d-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="6b67d-188">元素會將 `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 元件和 *json* 檔案放入 *build* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6b67d-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="6b67d-189">若要使用專案中的自訂目標，請加入 `PackageReference` 指向封裝及其版本的元素。</span><span class="sxs-lookup"><span data-stu-id="6b67d-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="6b67d-190">與工具不同的是，自訂目標封裝會包含在取用專案的相依性結束項中。</span><span class="sxs-lookup"><span data-stu-id="6b67d-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="6b67d-191">您可以設定如何使用自訂目標。</span><span class="sxs-lookup"><span data-stu-id="6b67d-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="6b67d-192">由於它是 MSBuild 目標，它可以相依于指定的目標，在另一個目標之後執行，或使用命令以手動方式叫用 `dotnet msbuild -t:<target-name>` 。</span><span class="sxs-lookup"><span data-stu-id="6b67d-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="6b67d-193">不過，為了提供更好的使用者體驗，您可以結合每個專案工具和自訂目標。</span><span class="sxs-lookup"><span data-stu-id="6b67d-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="6b67d-194">在此案例中，每個專案工具會接受所需的任何參數，並將它轉譯成 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 執行目標的必要調用。</span><span class="sxs-lookup"><span data-stu-id="6b67d-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="6b67d-195">您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。</span><span class="sxs-lookup"><span data-stu-id="6b67d-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b67d-196">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b67d-196">See also</span></span>

- [<span data-ttu-id="6b67d-197">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="6b67d-197">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="6b67d-198">如何使用 MSBuild 專案 Sdk</span><span class="sxs-lookup"><span data-stu-id="6b67d-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="6b67d-199">使用 NuGet 封裝自訂 MSBuild 目標和 .props</span><span class="sxs-lookup"><span data-stu-id="6b67d-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
