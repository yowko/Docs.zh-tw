---
title: 適用于 Microsoft .NET 的 MSBuild 屬性
description: .NET Core SDK 所瞭解的 MSBuild 屬性和專案的參考。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: c1093a0acd5b75ae6478767d690966a30fe84a31
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656258"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="c5a31-103">.NET Core SDK 專案的 MSBuild 參考</span><span class="sxs-lookup"><span data-stu-id="c5a31-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="c5a31-104">此頁面是您可以用來設定 .NET Core 專案的 MSBuild 屬性和專案的參考。</span><span class="sxs-lookup"><span data-stu-id="c5a31-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="c5a31-105">此頁面為進行中的工作，不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="c5a31-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="c5a31-106">如需常見 MSBuild 屬性的清單，請參閱 [一般的 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="c5a31-107">架構屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-107">Framework properties</span></span>

- [<span data-ttu-id="c5a31-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="c5a31-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="c5a31-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="c5a31-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="c5a31-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="c5a31-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="c5a31-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="c5a31-111">TargetFramework</span></span>

<span data-ttu-id="c5a31-112">`TargetFramework`屬性會指定應用程式的目標 framework 版本。</span><span class="sxs-lookup"><span data-stu-id="c5a31-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="c5a31-113">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="c5a31-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="c5a31-114">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="c5a31-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="c5a31-115">TargetFrameworks</span></span>

<span data-ttu-id="c5a31-116">`TargetFrameworks`當您想要讓應用程式以多個平臺為目標時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="c5a31-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="c5a31-117">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="c5a31-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="c5a31-118">如果 `TargetFramework` 指定了 (單數) ，就會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="c5a31-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="c5a31-119">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="c5a31-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="c5a31-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="c5a31-121">這個屬性只適用于使用 `netstandard1.x` 的專案。</span><span class="sxs-lookup"><span data-stu-id="c5a31-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="c5a31-122">它不適用於使用的專案 `netstandard2.x` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="c5a31-123">`NetStandardImplicitPackageVersion`當您想要指定的 framework 版本低於中繼套件版本時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="c5a31-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="c5a31-124">下列範例中的專案檔會以 `netstandard1.3` 1.6.0 版本為目標，但會使用 `NETStandard.Library` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="c5a31-125">封裝屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-125">Package properties</span></span>

<span data-ttu-id="c5a31-126">您可以指定屬性，例如 `PackageId` 、 `PackageVersion` 、 `PackageIcon` 、 `Title` 和， `Description` 以描述從專案建立的封裝。</span><span class="sxs-lookup"><span data-stu-id="c5a31-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="c5a31-127">如需這些屬性和其他屬性的詳細資訊，請參閱 [套件目標](/nuget/reference/msbuild-targets#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="c5a31-128">發佈屬性和專案</span><span class="sxs-lookup"><span data-stu-id="c5a31-128">Publish properties and items</span></span>

- [<span data-ttu-id="c5a31-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="c5a31-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="c5a31-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="c5a31-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="c5a31-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="c5a31-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="c5a31-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="c5a31-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="c5a31-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="c5a31-133">RuntimeIdentifier</span></span>

<span data-ttu-id="c5a31-134">`RuntimeIdentifier`屬性可讓您為專案指定[ (RID) ](../rid-catalog.md)的單一執行時間識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5a31-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="c5a31-135">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="c5a31-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="c5a31-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="c5a31-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="c5a31-137">`RuntimeIdentifiers`屬性可讓您為專案指定以分號分隔的[執行時間識別碼清單， (rid) ](../rid-catalog.md) 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="c5a31-138">如果您需要發行多個執行時間，請使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="c5a31-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="c5a31-139">`RuntimeIdentifiers` 會在還原時使用，以確保圖表中有正確的資產。</span><span class="sxs-lookup"><span data-stu-id="c5a31-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="c5a31-140">`RuntimeIdentifier` (單數) 可以在只需要單一執行時間時提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="c5a31-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="c5a31-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="c5a31-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="c5a31-142">`TrimmerRootAssembly`專案可讓您從[*修剪*](../deploying/trim-self-contained.md)中排除元件。</span><span class="sxs-lookup"><span data-stu-id="c5a31-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="c5a31-143">修剪是從封裝的應用程式中移除執行時間未使用部分的進程。</span><span class="sxs-lookup"><span data-stu-id="c5a31-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="c5a31-144">在某些情況下，修剪可能會不正確地移除必要的參考。</span><span class="sxs-lookup"><span data-stu-id="c5a31-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="c5a31-145">下列 XML 會將 `System.Security` 元件從修剪中排除。</span><span class="sxs-lookup"><span data-stu-id="c5a31-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="c5a31-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="c5a31-146">UseAppHost</span></span>

<span data-ttu-id="c5a31-147">此 `UseAppHost` 屬性是在 .NET Core SDK 的2.1.400 版本中引進。</span><span class="sxs-lookup"><span data-stu-id="c5a31-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="c5a31-148">它會控制是否為部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c5a31-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="c5a31-149">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c5a31-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="c5a31-150">在 .NET Core 3.0 和更新版本中，依預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c5a31-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="c5a31-151">將 `UseAppHost` 屬性設為， `false` 以停用產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c5a31-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="c5a31-152">如需部署的詳細資訊，請參閱 [.Net Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="c5a31-153">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-153">Compile properties</span></span>

- [<span data-ttu-id="c5a31-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="c5a31-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="c5a31-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="c5a31-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="c5a31-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="c5a31-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="c5a31-157">`EmbeddedResourceUseDependentUponConvention`屬性定義是否從原始程式檔中的型別資訊產生資源資訊清單檔案名，而這些來源檔案與資源檔共存。</span><span class="sxs-lookup"><span data-stu-id="c5a31-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="c5a31-158">例如，如果 *Form1* 與 *Form1.cs*位於相同的資料夾中，而且 `EmbeddedResourceUseDependentUponConvention` 設定為 `true` ，則產生的 *.resources* 檔會從 *Form1.cs*中定義的第一個類型取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="c5a31-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="c5a31-159">例如，如果 `MyNamespace.Form1` 是*Form1.cs*中所定義的第一個型別，則產生的檔案名會是*MyNamespace。*</span><span class="sxs-lookup"><span data-stu-id="c5a31-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="c5a31-160">如果 `LogicalName` 為 `ManifestResourceName` `DependentUpon` 專案指定、或中繼資料 `EmbeddedResource` ，則會改為以該中繼資料為基礎，產生該資源檔的資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="c5a31-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="c5a31-161">根據預設，在新的 .NET Core 專案中，這個屬性會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="c5a31-162">如果設定為 `false` ，且 `LogicalName` 專案檔中的專案未指定任何、 `ManifestResourceName` 或 `DependentUpon` 中繼資料 `EmbeddedResource` ，則資源資訊清單檔案名會以專案的根命名空間和 .resx 檔案的相對檔案路徑為基礎 *。*</span><span class="sxs-lookup"><span data-stu-id="c5a31-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="c5a31-163">如需詳細資訊，請參閱 [資源資訊清單檔案的命名方式](../resources/manifest-file-names.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="c5a31-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="c5a31-164">LangVersion</span></span>

<span data-ttu-id="c5a31-165">`LangVersion`屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="c5a31-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="c5a31-166">例如，如果您想要存取 c # 預覽功能，請將設定 `LangVersion` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="c5a31-167">如需詳細資訊，請參閱 [c # 語言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="c5a31-168">程式碼分析屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="c5a31-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="c5a31-169">AnalysisLevel</span></span>

<span data-ttu-id="c5a31-170">`AnalysisLevel`屬性可讓您指定程式碼分析層級。</span><span class="sxs-lookup"><span data-stu-id="c5a31-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="c5a31-171">例如，如果您想要存取預覽程式碼分析器，請將設定 `AnalysisLevel` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="c5a31-172">預設值是 `latest`。</span><span class="sxs-lookup"><span data-stu-id="c5a31-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="c5a31-173">下表顯示可用的選項。</span><span class="sxs-lookup"><span data-stu-id="c5a31-173">The following table shows the available options.</span></span>

| <span data-ttu-id="c5a31-174">值</span><span class="sxs-lookup"><span data-stu-id="c5a31-174">Value</span></span> | <span data-ttu-id="c5a31-175">意義</span><span class="sxs-lookup"><span data-stu-id="c5a31-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="c5a31-176">使用已發行的最新程式碼分析器。</span><span class="sxs-lookup"><span data-stu-id="c5a31-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="c5a31-177">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="c5a31-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="c5a31-178">使用最新的程式碼分析器，即使它們處於預覽狀態也一樣。</span><span class="sxs-lookup"><span data-stu-id="c5a31-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="c5a31-179">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="c5a31-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="c5a31-180">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="c5a31-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="c5a31-181">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="c5a31-181">AnalysisMode</span></span>

<span data-ttu-id="c5a31-182">從 .NET 5.0 RC2 開始，.NET SDK 隨附所有「CA」程式 [代碼品質規則](/visualstudio/code-quality/code-analysis-for-managed-code-warnings)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-182">Starting with .NET 5.0 RC2, the .NET SDK ships with all of the ["CA" code quality rules](/visualstudio/code-quality/code-analysis-for-managed-code-warnings).</span></span> <span data-ttu-id="c5a31-183">依預設，只 [會啟用部分規則](../../fundamentals/productivity/code-analysis.md#enabled-rules) 做為組建警告。</span><span class="sxs-lookup"><span data-stu-id="c5a31-183">By default, only [some rules are enabled](../../fundamentals/productivity/code-analysis.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="c5a31-184">`AnalysisMode`屬性可讓您自訂預設啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="c5a31-184">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="c5a31-185">您可以切換至更積極的 (退出) 分析模式或更保守的 (加入) 分析模式。</span><span class="sxs-lookup"><span data-stu-id="c5a31-185">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="c5a31-186">例如，如果您想要預設啟用所有規則作為組建警告，請將值設定為 `AllEnabledByDefault` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-186">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="c5a31-187">下表顯示可用的選項。</span><span class="sxs-lookup"><span data-stu-id="c5a31-187">The following table shows the available options.</span></span>

| <span data-ttu-id="c5a31-188">值</span><span class="sxs-lookup"><span data-stu-id="c5a31-188">Value</span></span> | <span data-ttu-id="c5a31-189">意義</span><span class="sxs-lookup"><span data-stu-id="c5a31-189">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="c5a31-190">預設模式，其中某些規則會啟用為組建警告，某些規則會啟用為 Visual Studio IDE 建議，並停用其餘部分。</span><span class="sxs-lookup"><span data-stu-id="c5a31-190">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="c5a31-191">積極或退出模式，預設會啟用所有規則作為組建警告。</span><span class="sxs-lookup"><span data-stu-id="c5a31-191">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="c5a31-192">您可以選擇性地 [退出宣告](../../fundamentals/productivity/configure-code-analysis-rules.md) 個別規則來停用它們。</span><span class="sxs-lookup"><span data-stu-id="c5a31-192">You can selectively [opt out](../../fundamentals/productivity/configure-code-analysis-rules.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="c5a31-193">保守或加入宣告模式，預設會停用所有規則。</span><span class="sxs-lookup"><span data-stu-id="c5a31-193">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="c5a31-194">您可以選擇性地 [選擇](../../fundamentals/productivity/configure-code-analysis-rules.md) 加入個別規則來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="c5a31-194">You can selectively [opt into](../../fundamentals/productivity/configure-code-analysis-rules.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="c5a31-195">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="c5a31-195">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="c5a31-196">`CodeAnalysisTreatWarningsAsErrors`屬性可讓您設定是否要將程式碼品質分析警告 (CAxxxx) 應該視為警告並中斷組建。</span><span class="sxs-lookup"><span data-stu-id="c5a31-196">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="c5a31-197">如果您在 `-warnaserror` 建立專案時使用旗標，則也會將 [.net 程式碼品質分析](../../fundamentals/productivity/code-analysis.md#code-quality-analysis) 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5a31-197">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/productivity/code-analysis.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="c5a31-198">如果您不想將程式碼品質分析警告視為錯誤，您可以 `CodeAnalysisTreatWarningsAsErrors` 在專案檔中將 MSBuild 屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-198">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="c5a31-199">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="c5a31-199">EnableNETAnalyzers</span></span>

<span data-ttu-id="c5a31-200">針對以 .NET 5.0 或更新版本為目標的專案，預設會啟用[.net 程式碼品質分析](../../fundamentals/productivity/code-analysis.md#code-quality-analysis)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-200">[.NET code quality analysis](../../fundamentals/productivity/code-analysis.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="c5a31-201">您可以藉由將屬性設定為，為以舊版 .NET 為目標的專案啟用 .NET 程式碼分析 `EnableNETAnalyzers` `true` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-201">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="c5a31-202">若要在任何專案中停用程式碼分析，請將這個屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-202">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="c5a31-203">針對以 .net 5.0 之前的 .NET 版本為目標的專案啟用 .NET 程式碼分析的另一種方式，是將 [AnalysisLevel](#analysislevel) 屬性設定為 `latest` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-203">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="c5a31-204">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="c5a31-204">EnforceCodeStyleInBuild</span></span>

<span data-ttu-id="c5a31-205">根據預設， [.net 程式碼樣式分析](../../fundamentals/productivity/code-analysis.md#code-style-analysis)會在所有 .net 專案的組建上停用。</span><span class="sxs-lookup"><span data-stu-id="c5a31-205">[.NET code style analysis](../../fundamentals/productivity/code-analysis.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="c5a31-206">您可以藉由將屬性設定為，啟用 .NET 專案的程式碼樣式分析 `EnforceCodeStyleInBuild` `true` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-206">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="c5a31-207">所有 [設定](../../fundamentals/productivity/code-analysis.md#code-style-analysis) 為警告或錯誤的程式碼樣式規則，都會在組建和報告違規時執行。</span><span class="sxs-lookup"><span data-stu-id="c5a31-207">All code style rules that are [configured](../../fundamentals/productivity/code-analysis.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="c5a31-208">執行時間設定屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-208">Run-time configuration properties</span></span>

<span data-ttu-id="c5a31-209">您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="c5a31-209">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="c5a31-210">如需設定執行時間行為之其他方式的詳細資訊，請參閱 [.Net Core 執行時間設定](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-210">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="c5a31-211">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5a31-211">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="c5a31-212">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="c5a31-212">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="c5a31-213">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5a31-213">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="c5a31-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5a31-214">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="c5a31-215">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="c5a31-215">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="c5a31-216">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="c5a31-216">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="c5a31-217">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="c5a31-217">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="c5a31-218">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="c5a31-218">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="c5a31-219">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="c5a31-219">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="c5a31-220">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5a31-220">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="c5a31-221">`ConcurrentGarbageCollection`屬性會設定是否啟用[背景 (並行) 垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-221">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="c5a31-222">將值設定為 `false` ，以停用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="c5a31-222">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="c5a31-223">如需詳細資訊，請參閱 [背景 GC](../run-time-config/garbage-collector.md#background-gc)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-223">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="c5a31-224">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="c5a31-224">InvariantGlobalization</span></span>

<span data-ttu-id="c5a31-225">`InvariantGlobalization`屬性會設定應用程式是否以*全球化不變的*模式執行，這表示它無法存取特定文化特性的資料。</span><span class="sxs-lookup"><span data-stu-id="c5a31-225">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="c5a31-226">將值設定為 `true` ，以在全球化非變異模式中執行。</span><span class="sxs-lookup"><span data-stu-id="c5a31-226">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="c5a31-227">如需詳細資訊，請參閱不 [變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-227">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="c5a31-228">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5a31-228">RetainVMGarbageCollection</span></span>

<span data-ttu-id="c5a31-229">屬性會將 `RetainVMGarbageCollection` 垃圾收集行程設定為將已刪除的記憶體區段放置於待命清單上，以供日後使用或釋放它們。</span><span class="sxs-lookup"><span data-stu-id="c5a31-229">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="c5a31-230">將此值設定為可 `true` 告知垃圾收集行程將區段放在待命清單上。</span><span class="sxs-lookup"><span data-stu-id="c5a31-230">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="c5a31-231">如需詳細資訊，請參閱 [保留 VM](../run-time-config/garbage-collector.md#retain-vm)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-231">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="c5a31-232">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5a31-232">ServerGarbageCollection</span></span>

<span data-ttu-id="c5a31-233">屬性會設定 `ServerGarbageCollection` 應用程式是使用 [工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-233">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="c5a31-234">將值設定為，以 `true` 使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="c5a31-234">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="c5a31-235">如需詳細資訊，請參閱 [工作站與伺服器](../run-time-config/garbage-collector.md#workstation-vs-server)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-235">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="c5a31-236">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="c5a31-236">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="c5a31-237">屬性會設定背景 `ThreadPoolMaxThreads` 工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="c5a31-237">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="c5a31-238">如需詳細資訊，請參閱 [最大執行緒數目](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-238">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="c5a31-239">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="c5a31-239">ThreadPoolMinThreads</span></span>

<span data-ttu-id="c5a31-240">`ThreadPoolMinThreads`屬性會為背景工作執行緒集區設定執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="c5a31-240">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="c5a31-241">如需詳細資訊，請參閱 [最小線程](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-241">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="c5a31-242">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="c5a31-242">TieredCompilation</span></span>

<span data-ttu-id="c5a31-243">屬性會設定 `TieredCompilation` 及時 (JIT) 編譯器是否使用 [分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-243">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="c5a31-244">將值設定為 `false` ，以停用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="c5a31-244">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="c5a31-245">如需詳細資訊，請參閱 [分層式編譯](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-245">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="c5a31-246">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="c5a31-246">TieredCompilationQuickJit</span></span>

<span data-ttu-id="c5a31-247">屬性會設定 `TieredCompilationQuickJit` jit 編譯器是否使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="c5a31-247">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="c5a31-248">將值設定為 `false` ，以停用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="c5a31-248">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="c5a31-249">如需詳細資訊，請參閱 [快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-249">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="c5a31-250">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="c5a31-250">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="c5a31-251">`TieredCompilationQuickJitForLoops`屬性會設定 jit 編譯器是否在包含迴圈的方法上使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="c5a31-251">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="c5a31-252">將值設定為， `true` 以在包含迴圈的方法上啟用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="c5a31-252">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="c5a31-253">如需詳細資訊，請參閱 [快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-253">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="c5a31-254">參考屬性和專案</span><span class="sxs-lookup"><span data-stu-id="c5a31-254">Reference properties and items</span></span>

- [<span data-ttu-id="c5a31-255">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="c5a31-255">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="c5a31-256">PackageReference</span><span class="sxs-lookup"><span data-stu-id="c5a31-256">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="c5a31-257">專案參考</span><span class="sxs-lookup"><span data-stu-id="c5a31-257">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="c5a31-258">參考</span><span class="sxs-lookup"><span data-stu-id="c5a31-258">Reference</span></span>](#reference)
- [<span data-ttu-id="c5a31-259">還原屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-259">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="c5a31-260">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="c5a31-260">AssetTargetFallback</span></span>

<span data-ttu-id="c5a31-261">`AssetTargetFallback`屬性可讓您為專案參考和 NuGet 套件指定其他相容的架構版本。</span><span class="sxs-lookup"><span data-stu-id="c5a31-261">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="c5a31-262">例如，如果您使用指定套件相依性， `PackageReference` 但該套件未包含與您的專案相容的資產 `TargetFramework` ，則此 `AssetTargetFallback` 屬性會進入 play。</span><span class="sxs-lookup"><span data-stu-id="c5a31-262">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="c5a31-263">參考封裝的相容性是使用中所指定的每一個目標架構來間隔 `AssetTargetFallback` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-263">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="c5a31-264">您可以將 `AssetTargetFallback` 屬性設定為一或多個 [目標 framework 版本](../../standard/frameworks.md#supported-target-frameworks)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-264">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="c5a31-265">PackageReference</span><span class="sxs-lookup"><span data-stu-id="c5a31-265">PackageReference</span></span>

<span data-ttu-id="c5a31-266">`PackageReference`專案會定義 NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="c5a31-266">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="c5a31-267">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5a31-267">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="c5a31-268">`Version`屬性會指定版本或版本範圍。</span><span class="sxs-lookup"><span data-stu-id="c5a31-268">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="c5a31-269">如需有關如何指定最小版本、最大版本、範圍或完全相符的詳細資訊，請參閱 [版本範圍](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-269">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="c5a31-270">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-270">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="c5a31-271">下列範例中的專案檔程式碼片段會參考 [system.object](https://www.nuget.org/packages/System.Runtime/) 套件。</span><span class="sxs-lookup"><span data-stu-id="c5a31-271">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="c5a31-272">如需詳細資訊，請參閱 [專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-272">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="c5a31-273">專案參考</span><span class="sxs-lookup"><span data-stu-id="c5a31-273">ProjectReference</span></span>

<span data-ttu-id="c5a31-274">`ProjectReference`專案會定義另一個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="c5a31-274">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="c5a31-275">參考的專案會新增為 NuGet 套件相依性，亦即，它會被視為與相同 `PackageReference` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-275">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="c5a31-276">`Include`屬性會指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c5a31-276">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="c5a31-277">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-277">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="c5a31-278">下列範例中的專案檔程式碼片段會參考名為的專案 `Project2` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-278">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="c5a31-279">參考</span><span class="sxs-lookup"><span data-stu-id="c5a31-279">Reference</span></span>

<span data-ttu-id="c5a31-280">`Reference`專案會定義元件檔的參考。</span><span class="sxs-lookup"><span data-stu-id="c5a31-280">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="c5a31-281">`Include`屬性會指定檔案名，而 `HintPath` 中繼資料會指定元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="c5a31-281">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="c5a31-282">還原屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-282">Restore properties</span></span>

<span data-ttu-id="c5a31-283">還原參考的封裝會安裝其所有直接相依性，以及這些相依性的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="c5a31-283">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="c5a31-284">您可以藉由指定屬性（例如和）來自訂封裝還原 `RestorePackagesPath` `RestoreIgnoreFailedSources` 。</span><span class="sxs-lookup"><span data-stu-id="c5a31-284">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="c5a31-285">如需這些屬性和其他屬性的詳細資訊，請參閱 [還原目標](/nuget/reference/msbuild-targets#restore-target)。</span><span class="sxs-lookup"><span data-stu-id="c5a31-285">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="c5a31-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5a31-286">See also</span></span>

- [<span data-ttu-id="c5a31-287">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="c5a31-287">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="c5a31-288">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-288">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="c5a31-289">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-289">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="c5a31-290">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="c5a31-290">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="c5a31-291">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="c5a31-291">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
