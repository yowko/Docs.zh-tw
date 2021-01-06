---
title: 適用于 Microsoft .NET 的 MSBuild 屬性
description: .NET SDK 瞭解的 MSBuild 屬性和專案參考。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 27944a6726f8d74a3b00c7c774faa8037c0f2f0e
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899622"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="74caf-103">.NET SDK 專案的 MSBuild 參考</span><span class="sxs-lookup"><span data-stu-id="74caf-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="74caf-104">此頁面是 MSBuild 屬性和專案的參考，您可以使用這些屬性來設定 .NET 專案。</span><span class="sxs-lookup"><span data-stu-id="74caf-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="74caf-105">此頁面為進行中的工作，不會列出 .NET SDK 的所有實用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="74caf-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="74caf-106">如需常見 MSBuild 屬性的清單，請參閱 [一般的 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="74caf-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="74caf-107">架構屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-107">Framework properties</span></span>

- [<span data-ttu-id="74caf-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="74caf-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="74caf-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="74caf-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="74caf-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="74caf-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="74caf-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="74caf-111">TargetFramework</span></span>

<span data-ttu-id="74caf-112">`TargetFramework`屬性會指定應用程式的目標 framework 版本。</span><span class="sxs-lookup"><span data-stu-id="74caf-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="74caf-113">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="74caf-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="74caf-114">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="74caf-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="74caf-115">TargetFrameworks</span></span>

<span data-ttu-id="74caf-116">`TargetFrameworks`當您想要讓應用程式以多個平臺為目標時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="74caf-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="74caf-117">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="74caf-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="74caf-118">如果 `TargetFramework` 指定了 (單數) ，就會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="74caf-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="74caf-119">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="74caf-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="74caf-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="74caf-121">這個屬性只適用于使用 `netstandard1.x` 的專案。</span><span class="sxs-lookup"><span data-stu-id="74caf-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="74caf-122">它不適用於使用的專案 `netstandard2.x` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="74caf-123">`NetStandardImplicitPackageVersion`當您想要指定的 framework 版本低於中繼套件版本時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="74caf-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="74caf-124">下列範例中的專案檔會以 `netstandard1.3` 1.6.0 版本為目標，但會使用 `NETStandard.Library` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="74caf-125">封裝屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-125">Package properties</span></span>

<span data-ttu-id="74caf-126">您可以指定屬性，例如 `PackageId` 、 `PackageVersion` 、 `PackageIcon` 、 `Title` 和， `Description` 以描述從專案建立的封裝。</span><span class="sxs-lookup"><span data-stu-id="74caf-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="74caf-127">如需這些屬性和其他屬性的詳細資訊，請參閱 [套件目標](/nuget/reference/msbuild-targets#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="74caf-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="74caf-128">發佈屬性和專案</span><span class="sxs-lookup"><span data-stu-id="74caf-128">Publish properties and items</span></span>

- [<span data-ttu-id="74caf-129">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="74caf-129">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="74caf-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="74caf-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="74caf-131">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="74caf-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="74caf-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="74caf-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="74caf-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="74caf-133">UseAppHost</span></span>](#useapphost)

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="74caf-134">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="74caf-134">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="74caf-135">`CopyLocalLockFileAssemblies`屬性適用于具有其他程式庫相依性的外掛程式專案。</span><span class="sxs-lookup"><span data-stu-id="74caf-135">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="74caf-136">如果您將此屬性設定為 `true` ，任何 NuGet 套件相依性都會複製到輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="74caf-136">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="74caf-137">這表示您可以使用的輸出， `dotnet build` 在任何電腦上執行您的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="74caf-137">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="74caf-138">或者，您可以使用 `dotnet publish` 來發行類別庫。</span><span class="sxs-lookup"><span data-stu-id="74caf-138">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="74caf-139">如需詳細資訊，請參閱 [dotnet publish](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-139">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="74caf-140">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="74caf-140">RuntimeIdentifier</span></span>

<span data-ttu-id="74caf-141">`RuntimeIdentifier`屬性可讓您為專案指定[ (RID) ](../rid-catalog.md)的單一執行時間識別碼。</span><span class="sxs-lookup"><span data-stu-id="74caf-141">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="74caf-142">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="74caf-142">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="74caf-143">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="74caf-143">RuntimeIdentifiers</span></span>

<span data-ttu-id="74caf-144">`RuntimeIdentifiers`屬性可讓您為專案指定以分號分隔的[執行時間識別碼清單， (rid) ](../rid-catalog.md) 。</span><span class="sxs-lookup"><span data-stu-id="74caf-144">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="74caf-145">如果您需要發行多個執行時間，請使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="74caf-145">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="74caf-146">`RuntimeIdentifiers` 會在還原時使用，以確保圖表中有正確的資產。</span><span class="sxs-lookup"><span data-stu-id="74caf-146">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="74caf-147">`RuntimeIdentifier` (單數) 可以在只需要單一執行時間時提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="74caf-147">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="74caf-148">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="74caf-148">TrimmerRootAssembly</span></span>

<span data-ttu-id="74caf-149">`TrimmerRootAssembly`專案可讓您從 [*修剪*](../deploying/trim-self-contained.md)中排除元件。</span><span class="sxs-lookup"><span data-stu-id="74caf-149">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="74caf-150">修剪是從封裝的應用程式中移除執行時間未使用部分的進程。</span><span class="sxs-lookup"><span data-stu-id="74caf-150">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="74caf-151">在某些情況下，修剪可能會不正確地移除必要的參考。</span><span class="sxs-lookup"><span data-stu-id="74caf-151">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="74caf-152">下列 XML 會將 `System.Security` 元件從修剪中排除。</span><span class="sxs-lookup"><span data-stu-id="74caf-152">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="74caf-153">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="74caf-153">UseAppHost</span></span>

<span data-ttu-id="74caf-154">`UseAppHost`屬性控制是否為部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="74caf-154">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="74caf-155">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="74caf-155">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="74caf-156">在 .NET Core 3.0 和更新版本中，依預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="74caf-156">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="74caf-157">將 `UseAppHost` 屬性設為， `false` 以停用產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="74caf-157">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="74caf-158">如需部署的詳細資訊，請參閱 [.net 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-158">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="74caf-159">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-159">Compile properties</span></span>

- [<span data-ttu-id="74caf-160">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="74caf-160">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="74caf-161">LangVersion</span><span class="sxs-lookup"><span data-stu-id="74caf-161">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="74caf-162">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="74caf-162">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="74caf-163">`EmbeddedResourceUseDependentUponConvention`屬性定義是否從原始程式檔中的型別資訊產生資源資訊清單檔案名，而這些來源檔案與資源檔共存。</span><span class="sxs-lookup"><span data-stu-id="74caf-163">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="74caf-164">例如，如果 *Form1* 與 *Form1.cs* 位於相同的資料夾中，而且 `EmbeddedResourceUseDependentUponConvention` 設定為 `true` ，則產生的 *.resources* 檔會從 *Form1.cs* 中定義的第一個類型取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="74caf-164">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="74caf-165">例如，如果 `MyNamespace.Form1` 是 *Form1.cs* 中所定義的第一個型別，則產生的檔案名會是 *MyNamespace。*</span><span class="sxs-lookup"><span data-stu-id="74caf-165">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="74caf-166">如果 `LogicalName` 為 `ManifestResourceName` `DependentUpon` 專案指定、或中繼資料 `EmbeddedResource` ，則會改為以該中繼資料為基礎，產生該資源檔的資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="74caf-166">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="74caf-167">根據預設，在新的 .NET 專案中，這個屬性會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-167">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="74caf-168">如果設定為 `false` ，且 `LogicalName` 專案檔中的專案未指定任何、 `ManifestResourceName` 或 `DependentUpon` 中繼資料 `EmbeddedResource` ，則資源資訊清單檔案名會以專案的根命名空間和 .resx 檔案的相對檔案路徑為基礎 *。*</span><span class="sxs-lookup"><span data-stu-id="74caf-168">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="74caf-169">如需詳細資訊，請參閱 [資源資訊清單檔案的命名方式](../resources/manifest-file-names.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-169">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="74caf-170">LangVersion</span><span class="sxs-lookup"><span data-stu-id="74caf-170">LangVersion</span></span>

<span data-ttu-id="74caf-171">`LangVersion`屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="74caf-171">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="74caf-172">例如，如果您想要存取 c # 預覽功能，請將設定 `LangVersion` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-172">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="74caf-173">如需詳細資訊，請參閱 [c # 語言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。</span><span class="sxs-lookup"><span data-stu-id="74caf-173">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="74caf-174">程式碼分析屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-174">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="74caf-175">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="74caf-175">AnalysisLevel</span></span>

<span data-ttu-id="74caf-176">`AnalysisLevel`屬性可讓您指定程式碼分析層級。</span><span class="sxs-lookup"><span data-stu-id="74caf-176">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="74caf-177">例如，如果您想要存取預覽程式碼分析器，請將設定 `AnalysisLevel` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-177">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="74caf-178">預設值是 `latest`。</span><span class="sxs-lookup"><span data-stu-id="74caf-178">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="74caf-179">下表顯示可用的選項。</span><span class="sxs-lookup"><span data-stu-id="74caf-179">The following table shows the available options.</span></span>

| <span data-ttu-id="74caf-180">值</span><span class="sxs-lookup"><span data-stu-id="74caf-180">Value</span></span> | <span data-ttu-id="74caf-181">意義</span><span class="sxs-lookup"><span data-stu-id="74caf-181">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="74caf-182">使用已發行的最新程式碼分析器。</span><span class="sxs-lookup"><span data-stu-id="74caf-182">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="74caf-183">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="74caf-183">This is the default.</span></span> |
| `preview` | <span data-ttu-id="74caf-184">使用最新的程式碼分析器，即使它們處於預覽狀態也一樣。</span><span class="sxs-lookup"><span data-stu-id="74caf-184">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="74caf-185">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="74caf-185">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="74caf-186">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="74caf-186">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="74caf-187">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="74caf-187">AnalysisMode</span></span>

<span data-ttu-id="74caf-188">從 .NET 5.0 開始，.NET SDK 隨附所有「CA」程式 [代碼品質規則](../../fundamentals/code-analysis/quality-rules/index.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-188">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="74caf-189">依預設，只 [會啟用部分規則](../../fundamentals/code-analysis/overview.md#enabled-rules) 做為組建警告。</span><span class="sxs-lookup"><span data-stu-id="74caf-189">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="74caf-190">`AnalysisMode`屬性可讓您自訂預設啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="74caf-190">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="74caf-191">您可以切換至更積極的 (退出) 分析模式或更保守的 (加入) 分析模式。</span><span class="sxs-lookup"><span data-stu-id="74caf-191">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="74caf-192">例如，如果您想要預設啟用所有規則作為組建警告，請將值設定為 `AllEnabledByDefault` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-192">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="74caf-193">下表顯示可用的選項。</span><span class="sxs-lookup"><span data-stu-id="74caf-193">The following table shows the available options.</span></span>

| <span data-ttu-id="74caf-194">值</span><span class="sxs-lookup"><span data-stu-id="74caf-194">Value</span></span> | <span data-ttu-id="74caf-195">意義</span><span class="sxs-lookup"><span data-stu-id="74caf-195">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="74caf-196">預設模式，其中某些規則會啟用為組建警告，某些規則會啟用為 Visual Studio IDE 建議，並停用其餘部分。</span><span class="sxs-lookup"><span data-stu-id="74caf-196">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="74caf-197">積極或退出模式，預設會啟用所有規則作為組建警告。</span><span class="sxs-lookup"><span data-stu-id="74caf-197">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="74caf-198">您可以選擇性地 [退出宣告](../../fundamentals/code-analysis/configuration-options.md) 個別規則來停用它們。</span><span class="sxs-lookup"><span data-stu-id="74caf-198">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="74caf-199">保守或加入宣告模式，預設會停用所有規則。</span><span class="sxs-lookup"><span data-stu-id="74caf-199">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="74caf-200">您可以選擇性地 [選擇](../../fundamentals/code-analysis/configuration-options.md) 加入個別規則來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="74caf-200">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="74caf-201">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="74caf-201">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="74caf-202">`CodeAnalysisTreatWarningsAsErrors`屬性可讓您設定是否要將程式碼品質分析警告 (CAxxxx) 應該視為警告並中斷組建。</span><span class="sxs-lookup"><span data-stu-id="74caf-202">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="74caf-203">如果您在 `-warnaserror` 建立專案時使用旗標，則也會將 [.net 程式碼品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis) 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="74caf-203">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="74caf-204">如果您不想將程式碼品質分析警告視為錯誤，您可以 `CodeAnalysisTreatWarningsAsErrors` 在專案檔中將 MSBuild 屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-204">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="74caf-205">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="74caf-205">EnableNETAnalyzers</span></span>

<span data-ttu-id="74caf-206">針對以 .NET 5.0 或更新版本為目標的專案，預設會啟用[.net 程式碼品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)。</span><span class="sxs-lookup"><span data-stu-id="74caf-206">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="74caf-207">您可以藉由將屬性設定為，為以舊版 .NET 為目標的專案啟用 .NET 程式碼分析 `EnableNETAnalyzers` `true` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-207">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="74caf-208">若要在任何專案中停用程式碼分析，請將這個屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-208">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="74caf-209">針對以 .net 5.0 之前的 .NET 版本為目標的專案啟用 .NET 程式碼分析的另一種方式，是將 [AnalysisLevel](#analysislevel) 屬性設定為 `latest` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-209">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="74caf-210">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="74caf-210">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="74caf-211">這項功能目前為實驗性，而且在 .NET 5 和 .NET 6 版本之間可能會變更。</span><span class="sxs-lookup"><span data-stu-id="74caf-211">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="74caf-212">根據預設， [.net 程式碼樣式分析](../../fundamentals/code-analysis/overview.md#code-style-analysis)會在所有 .net 專案的組建上停用。</span><span class="sxs-lookup"><span data-stu-id="74caf-212">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="74caf-213">您可以藉由將屬性設定為，啟用 .NET 專案的程式碼樣式分析 `EnforceCodeStyleInBuild` `true` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-213">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="74caf-214">所有 [設定](../../fundamentals/code-analysis/overview.md#code-style-analysis) 為警告或錯誤的程式碼樣式規則，都會在組建和報告違規時執行。</span><span class="sxs-lookup"><span data-stu-id="74caf-214">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="74caf-215">執行時間設定屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-215">Run-time configuration properties</span></span>

<span data-ttu-id="74caf-216">您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="74caf-216">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="74caf-217">如需設定執行時間行為之其他方式的詳細資訊，請參閱 [執行時間設定](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-217">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="74caf-218">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="74caf-218">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="74caf-219">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="74caf-219">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="74caf-220">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="74caf-220">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="74caf-221">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="74caf-221">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="74caf-222">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="74caf-222">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="74caf-223">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="74caf-223">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="74caf-224">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="74caf-224">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="74caf-225">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="74caf-225">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="74caf-226">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="74caf-226">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="74caf-227">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="74caf-227">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="74caf-228">`ConcurrentGarbageCollection`屬性會設定是否啟用[背景 (並行) 垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-228">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="74caf-229">將值設定為 `false` ，以停用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="74caf-229">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="74caf-230">如需詳細資訊，請參閱 [背景 GC](../run-time-config/garbage-collector.md#background-gc)。</span><span class="sxs-lookup"><span data-stu-id="74caf-230">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="74caf-231">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="74caf-231">InvariantGlobalization</span></span>

<span data-ttu-id="74caf-232">`InvariantGlobalization`屬性會設定應用程式是否以 *全球化不變的* 模式執行，這表示它無法存取特定文化特性的資料。</span><span class="sxs-lookup"><span data-stu-id="74caf-232">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="74caf-233">將值設定為 `true` ，以在全球化非變異模式中執行。</span><span class="sxs-lookup"><span data-stu-id="74caf-233">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="74caf-234">如需詳細資訊，請參閱不 [變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="74caf-234">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="74caf-235">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="74caf-235">RetainVMGarbageCollection</span></span>

<span data-ttu-id="74caf-236">屬性會將 `RetainVMGarbageCollection` 垃圾收集行程設定為將已刪除的記憶體區段放置於待命清單上，以供日後使用或釋放它們。</span><span class="sxs-lookup"><span data-stu-id="74caf-236">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="74caf-237">將此值設定為可 `true` 告知垃圾收集行程將區段放在待命清單上。</span><span class="sxs-lookup"><span data-stu-id="74caf-237">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="74caf-238">如需詳細資訊，請參閱 [保留 VM](../run-time-config/garbage-collector.md#retain-vm)。</span><span class="sxs-lookup"><span data-stu-id="74caf-238">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="74caf-239">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="74caf-239">ServerGarbageCollection</span></span>

<span data-ttu-id="74caf-240">屬性會設定 `ServerGarbageCollection` 應用程式是使用 [工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-240">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="74caf-241">將值設定為，以 `true` 使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="74caf-241">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="74caf-242">如需詳細資訊，請參閱 [工作站與伺服器](../run-time-config/garbage-collector.md#workstation-vs-server)。</span><span class="sxs-lookup"><span data-stu-id="74caf-242">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="74caf-243">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="74caf-243">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="74caf-244">屬性會設定背景 `ThreadPoolMaxThreads` 工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="74caf-244">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="74caf-245">如需詳細資訊，請參閱 [最大執行緒數目](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="74caf-245">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="74caf-246">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="74caf-246">ThreadPoolMinThreads</span></span>

<span data-ttu-id="74caf-247">`ThreadPoolMinThreads`屬性會為背景工作執行緒集區設定執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="74caf-247">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="74caf-248">如需詳細資訊，請參閱 [最小線程](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="74caf-248">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="74caf-249">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="74caf-249">TieredCompilation</span></span>

<span data-ttu-id="74caf-250">屬性會設定 `TieredCompilation` 及時 (JIT) 編譯器是否使用 [分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="74caf-250">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="74caf-251">將值設定為 `false` ，以停用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="74caf-251">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="74caf-252">如需詳細資訊，請參閱 [分層式編譯](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="74caf-252">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="74caf-253">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="74caf-253">TieredCompilationQuickJit</span></span>

<span data-ttu-id="74caf-254">屬性會設定 `TieredCompilationQuickJit` jit 編譯器是否使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="74caf-254">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="74caf-255">將值設定為 `false` ，以停用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="74caf-255">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="74caf-256">如需詳細資訊，請參閱 [快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="74caf-256">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="74caf-257">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="74caf-257">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="74caf-258">`TieredCompilationQuickJitForLoops`屬性會設定 jit 編譯器是否在包含迴圈的方法上使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="74caf-258">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="74caf-259">將值設定為， `true` 以在包含迴圈的方法上啟用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="74caf-259">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="74caf-260">如需詳細資訊，請參閱 [快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="74caf-260">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="74caf-261">參考屬性和專案</span><span class="sxs-lookup"><span data-stu-id="74caf-261">Reference properties and items</span></span>

- [<span data-ttu-id="74caf-262">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="74caf-262">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="74caf-263">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="74caf-263">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="74caf-264">PackageReference</span><span class="sxs-lookup"><span data-stu-id="74caf-264">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="74caf-265">專案參考</span><span class="sxs-lookup"><span data-stu-id="74caf-265">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="74caf-266">參考</span><span class="sxs-lookup"><span data-stu-id="74caf-266">Reference</span></span>](#reference)
- [<span data-ttu-id="74caf-267">還原相關的屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-267">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="74caf-268">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="74caf-268">AssetTargetFallback</span></span>

<span data-ttu-id="74caf-269">`AssetTargetFallback`屬性可讓您為專案參考和 NuGet 套件指定其他相容的架構版本。</span><span class="sxs-lookup"><span data-stu-id="74caf-269">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="74caf-270">例如，如果您使用指定套件相依性， `PackageReference` 但該套件未包含與您的專案相容的資產 `TargetFramework` ，則此 `AssetTargetFallback` 屬性會進入 play。</span><span class="sxs-lookup"><span data-stu-id="74caf-270">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="74caf-271">參考封裝的相容性是使用中所指定的每一個目標架構來間隔 `AssetTargetFallback` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-271">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="74caf-272">您可以將 `AssetTargetFallback` 屬性設定為一或多個 [目標 framework 版本](../../standard/frameworks.md#supported-target-frameworks)。</span><span class="sxs-lookup"><span data-stu-id="74caf-272">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="74caf-273">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="74caf-273">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="74caf-274">以 `DisableImplicitFrameworkReferences` `FrameworkReference` .net Core 3.0 和更新版本為目標時，屬性會控制隱含專案。</span><span class="sxs-lookup"><span data-stu-id="74caf-274">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="74caf-275">以 .NET Core 2.1 或 .NET Standard 2.0 和更早版本為目標時，它會在中繼套件中控制封裝的隱含 [PackageReference](#packagereference) 專案。</span><span class="sxs-lookup"><span data-stu-id="74caf-275">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="74caf-276"> (中繼套件是以架構為基礎的封裝，其中只包含其他封裝的相依性。 ) 此屬性也會控制以 `System` .NET Framework 為 `System.Core` 目標時的隱含參考，例如和。</span><span class="sxs-lookup"><span data-stu-id="74caf-276">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="74caf-277">將這個屬性設定為， `true` 以停用隱含 `FrameworkReference` 或 [PackageReference](#packagereference) 專案。</span><span class="sxs-lookup"><span data-stu-id="74caf-277">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="74caf-278">如果您將此屬性設定為 `true` ，您可以只將明確參考新增至所需的架構或封裝。</span><span class="sxs-lookup"><span data-stu-id="74caf-278">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="74caf-279">PackageReference</span><span class="sxs-lookup"><span data-stu-id="74caf-279">PackageReference</span></span>

<span data-ttu-id="74caf-280">`PackageReference`專案會定義 NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="74caf-280">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="74caf-281">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="74caf-281">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="74caf-282">`Version`屬性會指定版本或版本範圍。</span><span class="sxs-lookup"><span data-stu-id="74caf-282">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="74caf-283">如需有關如何指定最小版本、最大版本、範圍或完全相符的詳細資訊，請參閱 [版本範圍](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="74caf-283">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="74caf-284">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-284">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="74caf-285">下列範例中的專案檔程式碼片段會參考 [system.object](https://www.nuget.org/packages/System.Runtime/) 套件。</span><span class="sxs-lookup"><span data-stu-id="74caf-285">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="74caf-286">如需詳細資訊，請參閱 [專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="74caf-286">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="74caf-287">專案參考</span><span class="sxs-lookup"><span data-stu-id="74caf-287">ProjectReference</span></span>

<span data-ttu-id="74caf-288">`ProjectReference`專案會定義另一個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="74caf-288">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="74caf-289">參考的專案會新增為 NuGet 套件相依性，亦即，它會被視為與相同 `PackageReference` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-289">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="74caf-290">`Include`屬性會指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="74caf-290">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="74caf-291">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-291">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="74caf-292">下列範例中的專案檔程式碼片段會參考名為的專案 `Project2` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-292">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="74caf-293">參考</span><span class="sxs-lookup"><span data-stu-id="74caf-293">Reference</span></span>

<span data-ttu-id="74caf-294">`Reference`專案會定義元件檔的參考。</span><span class="sxs-lookup"><span data-stu-id="74caf-294">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="74caf-295">`Include`屬性會指定檔案名，而 `HintPath` 中繼資料會指定元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="74caf-295">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="74caf-296">還原相關的屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-296">Restore-related properties</span></span>

<span data-ttu-id="74caf-297">還原參考的封裝會安裝其所有直接相依性，以及這些相依性的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="74caf-297">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="74caf-298">您可以藉由指定屬性（例如和）來自訂封裝還原 `RestorePackagesPath` `RestoreIgnoreFailedSources` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-298">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="74caf-299">如需這些屬性和其他屬性的詳細資訊，請參閱 [還原目標](/nuget/reference/msbuild-targets#restore-target)。</span><span class="sxs-lookup"><span data-stu-id="74caf-299">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a><span data-ttu-id="74caf-300">執行屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-300">Run properties</span></span>

<span data-ttu-id="74caf-301">下列屬性是用來使用命令來啟動應用程式 [`dotnet run`](../tools/dotnet-run.md) ：</span><span class="sxs-lookup"><span data-stu-id="74caf-301">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="74caf-302">RunArguments</span><span class="sxs-lookup"><span data-stu-id="74caf-302">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="74caf-303">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="74caf-303">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="74caf-304">RunArguments</span><span class="sxs-lookup"><span data-stu-id="74caf-304">RunArguments</span></span>

<span data-ttu-id="74caf-305">`RunArguments`屬性會定義在應用程式執行時傳遞給該應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="74caf-305">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="74caf-306">您可以使用的[ `--` 選項 `dotnet run` ](../tools/dotnet-run.md#options)，指定要傳遞至應用程式的其他引數。</span><span class="sxs-lookup"><span data-stu-id="74caf-306">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="74caf-307">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="74caf-307">RunWorkingDirectory</span></span>

<span data-ttu-id="74caf-308">`RunWorkingDirectory`屬性會定義要在其中啟動應用程式進程的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="74caf-308">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="74caf-309">如果您未指定目錄， `OutDir` 則會使用做為工作目錄。</span><span class="sxs-lookup"><span data-stu-id="74caf-309">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties-and-items"></a><span data-ttu-id="74caf-310">裝載屬性和專案</span><span class="sxs-lookup"><span data-stu-id="74caf-310">Hosting properties and items</span></span>

- [<span data-ttu-id="74caf-311">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="74caf-311">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="74caf-312">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="74caf-312">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="74caf-313">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="74caf-313">EnableComHosting</span></span>

<span data-ttu-id="74caf-314">`EnableComHosting`屬性工作表示元件提供 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="74caf-314">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="74caf-315">將設定 `EnableComHosting` 為 `true` 也表示 [EnableDynamicLoading](#enabledynamicloading) 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-315">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="74caf-316">如需詳細資訊，請參閱 [將 .net 元件公開至 COM](../native-interop/expose-components-to-com.md)。</span><span class="sxs-lookup"><span data-stu-id="74caf-316">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="74caf-317">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="74caf-317">EnableDynamicLoading</span></span>

<span data-ttu-id="74caf-318">`EnableDynamicLoading`屬性工作表示元件是動態載入的元件。</span><span class="sxs-lookup"><span data-stu-id="74caf-318">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="74caf-319">元件可以是 COM 連結 [庫](/windows/win32/com/the-component-object-model) 或可 [從原生主機使用](../tutorials/netcore-hosting.md)的非 com 程式庫。</span><span class="sxs-lookup"><span data-stu-id="74caf-319">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="74caf-320">將這個屬性設定為 `true` 具有下列效果：</span><span class="sxs-lookup"><span data-stu-id="74caf-320">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="74caf-321">會產生檔案 *上的.runtimeconfig.js* 。</span><span class="sxs-lookup"><span data-stu-id="74caf-321">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="74caf-322">[向前](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) 復原是設定為 `LatestMinor` 。</span><span class="sxs-lookup"><span data-stu-id="74caf-322">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="74caf-323">NuGet 參考會在本機複製。</span><span class="sxs-lookup"><span data-stu-id="74caf-323">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="74caf-324">請參閱</span><span class="sxs-lookup"><span data-stu-id="74caf-324">See also</span></span>

- [<span data-ttu-id="74caf-325">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="74caf-325">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="74caf-326">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-326">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="74caf-327">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-327">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="74caf-328">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="74caf-328">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="74caf-329">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="74caf-329">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
