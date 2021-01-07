---
title: .NET 專案 SDK 總覽
titleSuffix: ''
description: 瞭解 .NET 專案 Sdk。
ms.date: 09/17/2020
ms.topic: conceptual
ms.openlocfilehash: 270735c9eef9f1930680687917317ac8bdf39e6d
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970690"
---
# <a name="net-project-sdks"></a><span data-ttu-id="b240c-103">.NET 專案 Sdk</span><span class="sxs-lookup"><span data-stu-id="b240c-103">.NET project SDKs</span></span>

<span data-ttu-id="b240c-104">.NET Core 和 .NET 5.0 和更新版本的專案與軟體發展工具組 (SDK) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="b240c-104">.NET Core and .NET 5.0 and later projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="b240c-105">每個 *專案 SDK* 都是一組 MSBuild [目標](/visualstudio/msbuild/msbuild-targets) 和 [相關聯的工作](/visualstudio/msbuild/msbuild-tasks) ，負責編譯、封裝和發佈程式碼。</span><span class="sxs-lookup"><span data-stu-id="b240c-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="b240c-106">參考專案 SDK 的專案有時稱為 *SDK 樣式專案*。</span><span class="sxs-lookup"><span data-stu-id="b240c-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="b240c-107">可用的 Sdk</span><span class="sxs-lookup"><span data-stu-id="b240c-107">Available SDKs</span></span>

<span data-ttu-id="b240c-108">以下是可用的 Sdk：</span><span class="sxs-lookup"><span data-stu-id="b240c-108">The following SDKs are available:</span></span>

| <span data-ttu-id="b240c-109">ID</span><span class="sxs-lookup"><span data-stu-id="b240c-109">ID</span></span> | <span data-ttu-id="b240c-110">描述</span><span class="sxs-lookup"><span data-stu-id="b240c-110">Description</span></span> | <span data-ttu-id="b240c-111">存放庫</span><span class="sxs-lookup"><span data-stu-id="b240c-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="b240c-112">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="b240c-112">The .NET SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="b240c-113">.NET [WEB SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="b240c-113">The .NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="b240c-114">.NET [RAZOR SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="b240c-114">The .NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="b240c-115">.NET Worker 服務 SDK</span><span class="sxs-lookup"><span data-stu-id="b240c-115">The .NET Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="b240c-116">WinForms 和 WPF SDK\*</span><span class="sxs-lookup"><span data-stu-id="b240c-116">The WinForms and WPF SDK\*</span></span> | <span data-ttu-id="b240c-117"><https://github.com/dotnet/winforms> 和 <https://github.com/dotnet/wpf></span><span class="sxs-lookup"><span data-stu-id="b240c-117"><https://github.com/dotnet/winforms> and <https://github.com/dotnet/wpf></span></span> |

<span data-ttu-id="b240c-118">.NET SDK 是適用于 .NET 的基底 SDK。</span><span class="sxs-lookup"><span data-stu-id="b240c-118">The .NET SDK is the base SDK for .NET.</span></span> <span data-ttu-id="b240c-119">其他 Sdk 參考 .NET SDK，而與其他 Sdk 相關聯的專案則具有所有可用的 .NET SDK 屬性。</span><span class="sxs-lookup"><span data-stu-id="b240c-119">The other SDKs reference the .NET SDK, and projects that are associated with the other SDKs have all the .NET SDK properties available to them.</span></span> <span data-ttu-id="b240c-120">例如，Web SDK 取決於 .NET SDK 和 Razor SDK。</span><span class="sxs-lookup"><span data-stu-id="b240c-120">The Web SDK, for example, depends on both the .NET SDK and the Razor SDK.</span></span>

<span data-ttu-id="b240c-121">您也可以撰寫可透過 NuGet 散發的您自己的 SDK。</span><span class="sxs-lookup"><span data-stu-id="b240c-121">You can also author your own SDK that can be distributed via NuGet.</span></span>

<span data-ttu-id="b240c-122">\* 從 .NET 5.0 開始，Windows Forms 和 Windows Presentation Foundation (WPF) 專案應指定 .NET SDK (`Microsoft.NET.Sdk`) 而不是 `Microsoft.NET.Sdk.WindowsDesktop` 。</span><span class="sxs-lookup"><span data-stu-id="b240c-122">\* Starting in .NET 5.0, Windows Forms and Windows Presentation Foundation (WPF) projects should specify the .NET SDK (`Microsoft.NET.Sdk`) instead of `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="b240c-123">針對這些專案，將設定 `TargetFramework` 為 `net5.0-windows` 和或， `UseWPF` `UseWindowsForms` `true` 將會自動匯入 Windows 桌面 SDK。</span><span class="sxs-lookup"><span data-stu-id="b240c-123">For these projects, setting `TargetFramework` to `net5.0-windows` and `UseWPF` or `UseWindowsForms` to `true` will automatically import the Windows desktop SDK.</span></span> <span data-ttu-id="b240c-124">如果您的專案是以 .NET 5.0 或更新版本為目標並指定 `Microsoft.NET.Sdk.WindowsDesktop` SDK，您將會收到組建警告 NETSDK1137。</span><span class="sxs-lookup"><span data-stu-id="b240c-124">If your project targets .NET 5.0 or later and specifies the `Microsoft.NET.Sdk.WindowsDesktop` SDK, you'll get build warning NETSDK1137.</span></span>

## <a name="project-files"></a><span data-ttu-id="b240c-125">專案檔</span><span class="sxs-lookup"><span data-stu-id="b240c-125">Project files</span></span>

<span data-ttu-id="b240c-126">.NET 專案是以 [MSBuild](/visualstudio/msbuild/msbuild) 格式為基礎。</span><span class="sxs-lookup"><span data-stu-id="b240c-126">.NET projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="b240c-127">具有適用于 c # 專案的 *.csproj* 和適用于 F # 專案之 *>.fsproj* 的專案檔為 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="b240c-127">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="b240c-128">MSBuild 專案檔的根項目是 [專案](/visualstudio/msbuild/project-element-msbuild) 元素。</span><span class="sxs-lookup"><span data-stu-id="b240c-128">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="b240c-129">`Project`元素具有選擇性 `Sdk` 屬性，可指定要使用的 SDK (和版本) 。</span><span class="sxs-lookup"><span data-stu-id="b240c-129">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="b240c-130">若要使用 .NET 工具並建立您的程式碼，請將 `Sdk` 屬性設定為 [可用 sdk](#available-sdks) 資料表中的其中一個識別碼。</span><span class="sxs-lookup"><span data-stu-id="b240c-130">To use the .NET tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="b240c-131">若要指定來自 NuGet 的 SDK，請在名稱的結尾包含版本，或在檔案的 *global.js* 中指定名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="b240c-131">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="b240c-132">指定 SDK 的另一種方式是使用最上層 [sdk](/visualstudio/msbuild/sdk-element-msbuild) 元素：</span><span class="sxs-lookup"><span data-stu-id="b240c-132">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="b240c-133">使用其中一種方式來參考 SDK，可大幅簡化 .NET 的專案檔。</span><span class="sxs-lookup"><span data-stu-id="b240c-133">Referencing an SDK in one of these ways greatly simplifies project files for .NET.</span></span> <span data-ttu-id="b240c-134">評估專案時，MSBuild 會在專案檔的 `Sdk.props` 頂端和底部加入隱含的匯入 `Sdk.targets` 。</span><span class="sxs-lookup"><span data-stu-id="b240c-134">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="b240c-135">在 Windows 電腦上，您可以在 *%ProgramFiles%\dotnet\sdk \\ [version] \Sdks\Microsoft.NET.Sdk\Sdk* 資料夾中找到 *.props* 和 *sdk .targets* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b240c-135">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="b240c-136">前置處理專案檔</span><span class="sxs-lookup"><span data-stu-id="b240c-136">Preprocess the project file</span></span>

<span data-ttu-id="b240c-137">您可以看到完全展開的專案，因為 MSBuild 會在 SDK 之後看到它，並使用命令來包含其目標 `dotnet msbuild -preprocess` 。</span><span class="sxs-lookup"><span data-stu-id="b240c-137">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="b240c-138">命令的前置 [處理參數](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) 會顯示要匯入的檔案 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 、其來源，以及其對組建的貢獻，而不會實際建立專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-138">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="b240c-139">如果專案有多個目標架構，請將命令的結果指定為 MSBuild 屬性，以只將命令的結果放在一個架構上。</span><span class="sxs-lookup"><span data-stu-id="b240c-139">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="b240c-140">例如：</span><span class="sxs-lookup"><span data-stu-id="b240c-140">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-includes-and-excludes"></a><span data-ttu-id="b240c-141">預設包含和排除</span><span class="sxs-lookup"><span data-stu-id="b240c-141">Default includes and excludes</span></span>

<span data-ttu-id="b240c-142">[ `Compile` 專案](/visualstudio/msbuild/common-msbuild-project-items#compile)、[內嵌資源](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource)和[ `None` 專案](/visualstudio/msbuild/common-msbuild-project-items#none)的預設包含和排除會定義在 SDK 中。</span><span class="sxs-lookup"><span data-stu-id="b240c-142">The default includes and excludes for [`Compile` items](/visualstudio/msbuild/common-msbuild-project-items#compile), [embedded resources](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource), and [`None` items](/visualstudio/msbuild/common-msbuild-project-items#none) are defined in the SDK.</span></span> <span data-ttu-id="b240c-143">不同于非 SDK .NET Framework 專案，您不需要在專案檔中指定這些專案，因為預設值涵蓋最常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="b240c-143">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="b240c-144">此行為可讓專案檔更小且更容易瞭解，並以手動方式進行編輯（如有需要）。</span><span class="sxs-lookup"><span data-stu-id="b240c-144">This behavior makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="b240c-145">下表顯示 .NET SDK 中包含和排除哪些元素和哪些 [glob](https://en.wikipedia.org/wiki/Glob_(programming)) ：</span><span class="sxs-lookup"><span data-stu-id="b240c-145">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET SDK:</span></span>

| <span data-ttu-id="b240c-146">元素</span><span class="sxs-lookup"><span data-stu-id="b240c-146">Element</span></span>           | <span data-ttu-id="b240c-147">包含 Glob</span><span class="sxs-lookup"><span data-stu-id="b240c-147">Include glob</span></span>                              | <span data-ttu-id="b240c-148">排除 Glob</span><span class="sxs-lookup"><span data-stu-id="b240c-148">Exclude glob</span></span>                                                  | <span data-ttu-id="b240c-149">移除 Glob</span><span class="sxs-lookup"><span data-stu-id="b240c-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="b240c-150">編譯</span><span class="sxs-lookup"><span data-stu-id="b240c-150">Compile</span></span>           | <span data-ttu-id="b240c-151">\*\*/\*.cs (或其他語言副檔名)</span><span class="sxs-lookup"><span data-stu-id="b240c-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="b240c-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b240c-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="b240c-153">不適用</span><span class="sxs-lookup"><span data-stu-id="b240c-153">N/A</span></span>                      |
| <span data-ttu-id="b240c-154">內嵌資源</span><span class="sxs-lookup"><span data-stu-id="b240c-154">EmbeddedResource</span></span>  | <span data-ttu-id="b240c-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b240c-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="b240c-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b240c-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b240c-157">不適用</span><span class="sxs-lookup"><span data-stu-id="b240c-157">N/A</span></span>                      |
| <span data-ttu-id="b240c-158">無</span><span class="sxs-lookup"><span data-stu-id="b240c-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="b240c-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b240c-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b240c-160">\*\*/\*.cs、\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b240c-160">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="b240c-161">和 `./bin` `./obj` MSBuild 屬性代表的和資料夾， `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` 預設會從 glob 中排除。</span><span class="sxs-lookup"><span data-stu-id="b240c-161">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="b240c-162">[排除] 會以 [DefaultItemExcludes 屬性](msbuild-props.md#defaultitemexcludes)表示。</span><span class="sxs-lookup"><span data-stu-id="b240c-162">Excludes are represented by the [DefaultItemExcludes property](msbuild-props.md#defaultitemexcludes).</span></span>

#### <a name="build-errors"></a><span data-ttu-id="b240c-163">建置錯誤</span><span class="sxs-lookup"><span data-stu-id="b240c-163">Build errors</span></span>

<span data-ttu-id="b240c-164">如果您在專案檔中明確定義任何這些專案，您可能會收到類似下列的「NETSDK1022」組建錯誤：</span><span class="sxs-lookup"><span data-stu-id="b240c-164">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="b240c-165">包含重複的 ' Compile ' 專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-165">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="b240c-166">.NET SDK 預設會在您的專案目錄中包含 [編譯] 專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-166">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="b240c-167">您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。</span><span class="sxs-lookup"><span data-stu-id="b240c-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="b240c-168">包含重複的 ' EmbeddedResource ' 專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-168">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="b240c-169">.NET SDK 預設會在您的專案目錄中包含 ' EmbeddedResource ' 專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-169">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="b240c-170">您可以從專案檔中移除這些專案，或將 ' EnableDefaultEmbeddedResourceItems ' 屬性設定為 ' false '，如果您想要將它們明確包含在專案檔中。</span><span class="sxs-lookup"><span data-stu-id="b240c-170">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="b240c-171">若要解決錯誤，請執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="b240c-171">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="b240c-172">移除符合上 `Compile` `EmbeddedResource` 表所 `None` 列之隱含專案的明確、或專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-172">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="b240c-173">將 [EnableDefaultItems 屬性](msbuild-props.md#enabledefaultitems) 設定為， `false` 以停用所有隱含檔案包含：</span><span class="sxs-lookup"><span data-stu-id="b240c-173">Set the [EnableDefaultItems property](msbuild-props.md#enabledefaultitems) to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="b240c-174">如果您想要指定要與應用程式一起發行的檔案，您仍然可以針對該專案使用已知的 MSBuild 機制，例如 `Content` 元素。</span><span class="sxs-lookup"><span data-stu-id="b240c-174">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="b240c-175">選擇性地停 `Compile` `EmbeddedResource` 用、或 `None` glob，方法是將 [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems)、 [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems)或 [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) 屬性設定為 `false` ：</span><span class="sxs-lookup"><span data-stu-id="b240c-175">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems), or [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="b240c-176">如果您只停 `Compile` 用 glob，方案總管在 Visual Studio 仍會 \* 將 .cs 專案顯示為專案的一部分，包含為 `None` 專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-176">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="b240c-177">若要停用隱含 `None` glob，請將設定 `EnableDefaultNoneItems` 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="b240c-177">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="b240c-178">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="b240c-178">Customize the build</span></span>

<span data-ttu-id="b240c-179">[自訂群組建](/visualstudio/msbuild/customize-your-build)的方式有很多種。</span><span class="sxs-lookup"><span data-stu-id="b240c-179">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="b240c-180">您可以藉由將屬性做為引數傳遞至 [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) 或 [dotnet](../tools/index.md) 命令，來覆寫該屬性。</span><span class="sxs-lookup"><span data-stu-id="b240c-180">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="b240c-181">您也可以將屬性加入至專案檔或 *.props* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b240c-181">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="b240c-182">如需 .NET 專案的實用屬性清單，請參閱 [.NET SDK 專案的 MSBuild 參考](msbuild-props.md)。</span><span class="sxs-lookup"><span data-stu-id="b240c-182">For a list of useful properties for .NET projects, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="b240c-183">自訂目標</span><span class="sxs-lookup"><span data-stu-id="b240c-183">Custom targets</span></span>

<span data-ttu-id="b240c-184">.NET 專案可以封裝自訂 MSBuild 目標和屬性，以供取用封裝的專案使用。</span><span class="sxs-lookup"><span data-stu-id="b240c-184">.NET projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="b240c-185">當您想要執行下列動作時，請使用這類型的擴充性：</span><span class="sxs-lookup"><span data-stu-id="b240c-185">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="b240c-186">擴充組建流程。</span><span class="sxs-lookup"><span data-stu-id="b240c-186">Extend the build process.</span></span>
- <span data-ttu-id="b240c-187">存取組建進程的構件，例如產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="b240c-187">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="b240c-188">檢查用來叫用組建的設定。</span><span class="sxs-lookup"><span data-stu-id="b240c-188">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="b240c-189">您可以藉由將檔案放入表單或 (來新增自訂群組建目標或屬性 `<package_id>.targets` `<package_id>.props` ，例如， `Contoso.Utility.UsefulStuff.targets` 在專案的 [ *組建* ] 資料夾中) 。</span><span class="sxs-lookup"><span data-stu-id="b240c-189">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="b240c-190">下列 XML 是來自 *.csproj* 檔案的程式碼片段，指示 [`dotnet pack`](../tools/dotnet-pack.md) 命令要封裝的內容。</span><span class="sxs-lookup"><span data-stu-id="b240c-190">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="b240c-191">元素會將 `<ItemGroup Label="dotnet pack instructions">` 目標檔案放入封裝內的 *組建* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b240c-191">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="b240c-192">元素會將 `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 元件和 *json* 檔案放入 *組建* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b240c-192">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="b240c-193">若要在專案中使用自訂目標，請新增 `PackageReference` 指向封裝及其版本的專案。</span><span class="sxs-lookup"><span data-stu-id="b240c-193">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="b240c-194">與工具不同的是，自訂目標套件包含在取用專案的相依性關閉中。</span><span class="sxs-lookup"><span data-stu-id="b240c-194">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="b240c-195">您可以設定如何使用自訂目標。</span><span class="sxs-lookup"><span data-stu-id="b240c-195">You can configure how to use the custom target.</span></span> <span data-ttu-id="b240c-196">因為它是 MSBuild 目標，所以它可以相依于指定的目標、在另一個目標之後執行，或使用命令手動叫用 `dotnet msbuild -t:<target-name>` 。</span><span class="sxs-lookup"><span data-stu-id="b240c-196">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="b240c-197">不過，若要提供更好的使用者體驗，您可以結合每個專案工具和自訂目標。</span><span class="sxs-lookup"><span data-stu-id="b240c-197">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="b240c-198">在此案例中，每個專案工具會接受任何需要的參數，並將其轉譯為執行目標所需的 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 調用。</span><span class="sxs-lookup"><span data-stu-id="b240c-198">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="b240c-199">您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。</span><span class="sxs-lookup"><span data-stu-id="b240c-199">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="b240c-200">請參閱</span><span class="sxs-lookup"><span data-stu-id="b240c-200">See also</span></span>

- [<span data-ttu-id="b240c-201">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="b240c-201">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="b240c-202">如何使用 MSBuild 專案 Sdk</span><span class="sxs-lookup"><span data-stu-id="b240c-202">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="b240c-203">使用 NuGet 封裝自訂 MSBuild 目標和 .props</span><span class="sxs-lookup"><span data-stu-id="b240c-203">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
