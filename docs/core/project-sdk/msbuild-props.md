---
title: 適用于 Microsoft .NET 的 MSBuild 屬性
description: .NET Core SDK 所瞭解的 MSBuild 屬性和專案的參考。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 866253a0526741f5554971a5202c179106503951
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598016"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="763f7-103">.NET Core SDK 專案的 MSBuild 參考</span><span class="sxs-lookup"><span data-stu-id="763f7-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="763f7-104">此頁面是您可以用來設定 .NET Core 專案的 MSBuild 屬性和專案的參考。</span><span class="sxs-lookup"><span data-stu-id="763f7-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="763f7-105">此頁面為進行中的工作，不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="763f7-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="763f7-106">如需常見 MSBuild 屬性的清單，請參閱 [一般的 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="763f7-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="763f7-107">架構屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-107">Framework properties</span></span>

- [<span data-ttu-id="763f7-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="763f7-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="763f7-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="763f7-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="763f7-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="763f7-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="763f7-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="763f7-111">TargetFramework</span></span>

<span data-ttu-id="763f7-112">`TargetFramework`屬性會指定應用程式的目標 framework 版本。</span><span class="sxs-lookup"><span data-stu-id="763f7-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="763f7-113">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="763f7-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="763f7-114">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="763f7-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="763f7-115">TargetFrameworks</span></span>

<span data-ttu-id="763f7-116">`TargetFrameworks`當您想要讓應用程式以多個平臺為目標時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="763f7-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="763f7-117">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="763f7-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="763f7-118">如果 `TargetFramework` 指定了 (單數) ，就會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="763f7-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="763f7-119">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="763f7-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="763f7-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="763f7-121">這個屬性只適用于使用 `netstandard1.x` 的專案。</span><span class="sxs-lookup"><span data-stu-id="763f7-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="763f7-122">它不適用於使用的專案 `netstandard2.x` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="763f7-123">`NetStandardImplicitPackageVersion`當您想要指定的 framework 版本低於中繼套件版本時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="763f7-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="763f7-124">下列範例中的專案檔會以 `netstandard1.3` 1.6.0 版本為目標，但會使用 `NETStandard.Library` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="763f7-125">封裝屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-125">Package properties</span></span>

<span data-ttu-id="763f7-126">您可以指定屬性，例如 `PackageId` 、 `PackageVersion` 、 `PackageIcon` 、 `Title` 和， `Description` 以描述從專案建立的封裝。</span><span class="sxs-lookup"><span data-stu-id="763f7-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="763f7-127">如需這些屬性和其他屬性的詳細資訊，請參閱 [套件目標](/nuget/reference/msbuild-targets#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="763f7-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="763f7-128">發佈屬性和專案</span><span class="sxs-lookup"><span data-stu-id="763f7-128">Publish properties and items</span></span>

- [<span data-ttu-id="763f7-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="763f7-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="763f7-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="763f7-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="763f7-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="763f7-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="763f7-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="763f7-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="763f7-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="763f7-133">RuntimeIdentifier</span></span>

<span data-ttu-id="763f7-134">`RuntimeIdentifier`屬性可讓您為專案指定[ (RID) ](../rid-catalog.md)的單一執行時間識別碼。</span><span class="sxs-lookup"><span data-stu-id="763f7-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="763f7-135">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="763f7-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="763f7-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="763f7-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="763f7-137">`RuntimeIdentifiers`屬性可讓您為專案指定以分號分隔的[執行時間識別碼清單， (rid) ](../rid-catalog.md) 。</span><span class="sxs-lookup"><span data-stu-id="763f7-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="763f7-138">如果您需要發行多個執行時間，請使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="763f7-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="763f7-139">`RuntimeIdentifiers` 會在還原時使用，以確保圖表中有正確的資產。</span><span class="sxs-lookup"><span data-stu-id="763f7-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="763f7-140">`RuntimeIdentifier` (單數) 可以在只需要單一執行時間時提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="763f7-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="763f7-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="763f7-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="763f7-142">`TrimmerRootAssembly`專案可讓您從[*修剪*](../deploying/trim-self-contained.md)中排除元件。</span><span class="sxs-lookup"><span data-stu-id="763f7-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="763f7-143">修剪是從封裝的應用程式中移除執行時間未使用部分的進程。</span><span class="sxs-lookup"><span data-stu-id="763f7-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="763f7-144">在某些情況下，修剪可能會不正確地移除必要的參考。</span><span class="sxs-lookup"><span data-stu-id="763f7-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="763f7-145">下列 XML 會將 `System.Security` 元件從修剪中排除。</span><span class="sxs-lookup"><span data-stu-id="763f7-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="763f7-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="763f7-146">UseAppHost</span></span>

<span data-ttu-id="763f7-147">此 `UseAppHost` 屬性是在 .NET Core SDK 的2.1.400 版本中引進。</span><span class="sxs-lookup"><span data-stu-id="763f7-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="763f7-148">它會控制是否為部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="763f7-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="763f7-149">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="763f7-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="763f7-150">在 .NET Core 3.0 和更新版本中，依預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="763f7-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="763f7-151">將 `UseAppHost` 屬性設為， `false` 以停用產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="763f7-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="763f7-152">如需部署的詳細資訊，請參閱 [.Net Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="763f7-153">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-153">Compile properties</span></span>

- [<span data-ttu-id="763f7-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="763f7-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="763f7-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="763f7-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="763f7-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="763f7-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="763f7-157">`EmbeddedResourceUseDependentUponConvention`屬性定義是否從原始程式檔中的型別資訊產生資源資訊清單檔案名，而這些來源檔案與資源檔共存。</span><span class="sxs-lookup"><span data-stu-id="763f7-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="763f7-158">例如，如果 *Form1* 與 *Form1.cs*位於相同的資料夾中，而且 `EmbeddedResourceUseDependentUponConvention` 設定為 `true` ，則產生的 *.resources* 檔會從 *Form1.cs*中定義的第一個類型取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="763f7-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="763f7-159">例如，如果 `MyNamespace.Form1` 是*Form1.cs*中所定義的第一個型別，則產生的檔案名會是*MyNamespace。*</span><span class="sxs-lookup"><span data-stu-id="763f7-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="763f7-160">如果 `LogicalName` 為 `ManifestResourceName` `DependentUpon` 專案指定、或中繼資料 `EmbeddedResource` ，則會改為以該中繼資料為基礎，產生該資源檔的資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="763f7-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="763f7-161">根據預設，在新的 .NET Core 專案中，這個屬性會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="763f7-162">如果設定為 `false` ，且 `LogicalName` 專案檔中的專案未指定任何、 `ManifestResourceName` 或 `DependentUpon` 中繼資料 `EmbeddedResource` ，則資源資訊清單檔案名會以專案的根命名空間和 .resx 檔案的相對檔案路徑為基礎 *。*</span><span class="sxs-lookup"><span data-stu-id="763f7-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="763f7-163">如需詳細資訊，請參閱 [資源資訊清單檔案的命名方式](../resources/manifest-file-names.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="763f7-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="763f7-164">LangVersion</span></span>

<span data-ttu-id="763f7-165">`LangVersion`屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="763f7-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="763f7-166">例如，如果您想要存取 c # 預覽功能，請將設定 `LangVersion` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="763f7-167">如需詳細資訊，請參閱 [c # 語言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。</span><span class="sxs-lookup"><span data-stu-id="763f7-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="763f7-168">程式碼分析屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="763f7-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="763f7-169">AnalysisLevel</span></span>

<span data-ttu-id="763f7-170">`AnalysisLevel`屬性可讓您指定程式碼分析層級。</span><span class="sxs-lookup"><span data-stu-id="763f7-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="763f7-171">例如，如果您想要存取預覽程式碼分析器，請將設定 `AnalysisLevel` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="763f7-172">預設值是 `latest`。</span><span class="sxs-lookup"><span data-stu-id="763f7-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="763f7-173">下表顯示可用的選項。</span><span class="sxs-lookup"><span data-stu-id="763f7-173">The following table shows the available options.</span></span>

| <span data-ttu-id="763f7-174">值</span><span class="sxs-lookup"><span data-stu-id="763f7-174">Value</span></span> | <span data-ttu-id="763f7-175">意義</span><span class="sxs-lookup"><span data-stu-id="763f7-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="763f7-176">使用已發行的最新程式碼分析器。</span><span class="sxs-lookup"><span data-stu-id="763f7-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="763f7-177">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="763f7-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="763f7-178">使用最新的程式碼分析器，即使它們處於預覽狀態也一樣。</span><span class="sxs-lookup"><span data-stu-id="763f7-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="763f7-179">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="763f7-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="763f7-180">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="763f7-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="763f7-181">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="763f7-181">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="763f7-182">`CodeAnalysisTreatWarningsAsErrors`屬性可讓您設定是否應將程式碼分析警告視為警告並中斷組建。</span><span class="sxs-lookup"><span data-stu-id="763f7-182">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code analysis warnings should be treated as warnings and break the build.</span></span> <span data-ttu-id="763f7-183">如果您在 `-warnaserror` 建立專案時使用旗標，也會將 [.net 程式碼分析](../../fundamentals/productivity/code-analysis.md) 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="763f7-183">If you use the `-warnaserror` flag when you build your projects, [.NET code analysis](../../fundamentals/productivity/code-analysis.md) warnings are also treated as errors.</span></span> <span data-ttu-id="763f7-184">如果您只想要將編譯器警告視為錯誤，您可以 `CodeAnalysisTreatWarningsAsErrors` 在專案檔中將 MSBuild 屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-184">If you only want compiler warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="763f7-185">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="763f7-185">EnableNETAnalyzers</span></span>

<span data-ttu-id="763f7-186">針對以 .NET 5.0 或更新版本為目標的專案，預設會啟用[.net 程式碼分析](../../fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-186">[.NET Code analysis](../../fundamentals/productivity/code-analysis.md) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="763f7-187">您可以藉由將屬性設定為 true，為以舊版 .NET 為目標的專案啟用 .NET 程式碼分析 `EnableNETAnalyzers` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-187">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to true.</span></span> <span data-ttu-id="763f7-188">若要在任何專案中停用程式碼分析，請將這個屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-188">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="763f7-189">針對以 .net 5.0 之前的 .NET 版本為目標的專案啟用 .NET 程式碼分析的另一種方式，是將 [AnalysisLevel](#analysislevel) 屬性設定為 `latest` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-189">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="763f7-190">執行時間設定屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-190">Run-time configuration properties</span></span>

<span data-ttu-id="763f7-191">您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="763f7-191">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="763f7-192">如需設定執行時間行為之其他方式的詳細資訊，請參閱 [.Net Core 執行時間設定](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-192">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="763f7-193">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="763f7-193">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="763f7-194">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="763f7-194">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="763f7-195">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="763f7-195">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="763f7-196">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="763f7-196">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="763f7-197">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="763f7-197">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="763f7-198">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="763f7-198">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="763f7-199">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="763f7-199">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="763f7-200">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="763f7-200">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="763f7-201">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="763f7-201">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="763f7-202">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="763f7-202">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="763f7-203">`ConcurrentGarbageCollection`屬性會設定是否啟用[背景 (並行) 垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-203">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="763f7-204">將值設定為 `false` ，以停用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="763f7-204">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="763f7-205">如需詳細資訊，請參閱 [背景 GC](../run-time-config/garbage-collector.md#background-gc)。</span><span class="sxs-lookup"><span data-stu-id="763f7-205">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="763f7-206">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="763f7-206">InvariantGlobalization</span></span>

<span data-ttu-id="763f7-207">`InvariantGlobalization`屬性會設定應用程式是否以*全球化不變的*模式執行，這表示它無法存取特定文化特性的資料。</span><span class="sxs-lookup"><span data-stu-id="763f7-207">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="763f7-208">將值設定為 `true` ，以在全球化非變異模式中執行。</span><span class="sxs-lookup"><span data-stu-id="763f7-208">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="763f7-209">如需詳細資訊，請參閱不 [變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="763f7-209">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="763f7-210">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="763f7-210">RetainVMGarbageCollection</span></span>

<span data-ttu-id="763f7-211">屬性會將 `RetainVMGarbageCollection` 垃圾收集行程設定為將已刪除的記憶體區段放置於待命清單上，以供日後使用或釋放它們。</span><span class="sxs-lookup"><span data-stu-id="763f7-211">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="763f7-212">將此值設定為可 `true` 告知垃圾收集行程將區段放在待命清單上。</span><span class="sxs-lookup"><span data-stu-id="763f7-212">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="763f7-213">如需詳細資訊，請參閱 [保留 VM](../run-time-config/garbage-collector.md#retain-vm)。</span><span class="sxs-lookup"><span data-stu-id="763f7-213">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="763f7-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="763f7-214">ServerGarbageCollection</span></span>

<span data-ttu-id="763f7-215">屬性會設定 `ServerGarbageCollection` 應用程式是使用 [工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="763f7-215">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="763f7-216">將值設定為，以 `true` 使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="763f7-216">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="763f7-217">如需詳細資訊，請參閱 [工作站與伺服器](../run-time-config/garbage-collector.md#workstation-vs-server)。</span><span class="sxs-lookup"><span data-stu-id="763f7-217">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="763f7-218">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="763f7-218">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="763f7-219">屬性會設定背景 `ThreadPoolMaxThreads` 工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="763f7-219">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="763f7-220">如需詳細資訊，請參閱 [最大執行緒數目](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="763f7-220">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="763f7-221">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="763f7-221">ThreadPoolMinThreads</span></span>

<span data-ttu-id="763f7-222">`ThreadPoolMinThreads`屬性會為背景工作執行緒集區設定執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="763f7-222">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="763f7-223">如需詳細資訊，請參閱 [最小線程](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="763f7-223">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="763f7-224">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="763f7-224">TieredCompilation</span></span>

<span data-ttu-id="763f7-225">屬性會設定 `TieredCompilation` 及時 (JIT) 編譯器是否使用 [分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="763f7-225">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="763f7-226">將值設定為 `false` ，以停用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="763f7-226">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="763f7-227">如需詳細資訊，請參閱 [分層式編譯](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="763f7-227">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="763f7-228">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="763f7-228">TieredCompilationQuickJit</span></span>

<span data-ttu-id="763f7-229">屬性會設定 `TieredCompilationQuickJit` jit 編譯器是否使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="763f7-229">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="763f7-230">將值設定為 `false` ，以停用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="763f7-230">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="763f7-231">如需詳細資訊，請參閱 [快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="763f7-231">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="763f7-232">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="763f7-232">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="763f7-233">`TieredCompilationQuickJitForLoops`屬性會設定 jit 編譯器是否在包含迴圈的方法上使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="763f7-233">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="763f7-234">將值設定為， `true` 以在包含迴圈的方法上啟用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="763f7-234">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="763f7-235">如需詳細資訊，請參閱 [快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="763f7-235">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="763f7-236">參考屬性和專案</span><span class="sxs-lookup"><span data-stu-id="763f7-236">Reference properties and items</span></span>

- [<span data-ttu-id="763f7-237">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="763f7-237">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="763f7-238">PackageReference</span><span class="sxs-lookup"><span data-stu-id="763f7-238">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="763f7-239">專案參考</span><span class="sxs-lookup"><span data-stu-id="763f7-239">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="763f7-240">參考</span><span class="sxs-lookup"><span data-stu-id="763f7-240">Reference</span></span>](#reference)
- [<span data-ttu-id="763f7-241">還原屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-241">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="763f7-242">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="763f7-242">AssetTargetFallback</span></span>

<span data-ttu-id="763f7-243">`AssetTargetFallback`屬性可讓您為專案參考和 NuGet 套件指定其他相容的架構版本。</span><span class="sxs-lookup"><span data-stu-id="763f7-243">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="763f7-244">例如，如果您使用指定套件相依性， `PackageReference` 但該套件未包含與您的專案相容的資產 `TargetFramework` ，則此 `AssetTargetFallback` 屬性會進入 play。</span><span class="sxs-lookup"><span data-stu-id="763f7-244">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="763f7-245">參考封裝的相容性是使用中所指定的每一個目標架構來間隔 `AssetTargetFallback` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-245">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="763f7-246">您可以將 `AssetTargetFallback` 屬性設定為一或多個 [目標 framework 版本](../../standard/frameworks.md#supported-target-frameworks)。</span><span class="sxs-lookup"><span data-stu-id="763f7-246">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="763f7-247">PackageReference</span><span class="sxs-lookup"><span data-stu-id="763f7-247">PackageReference</span></span>

<span data-ttu-id="763f7-248">`PackageReference`專案會定義 NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="763f7-248">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="763f7-249">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="763f7-249">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="763f7-250">`Version`屬性會指定版本或版本範圍。</span><span class="sxs-lookup"><span data-stu-id="763f7-250">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="763f7-251">如需有關如何指定最小版本、最大版本、範圍或完全相符的詳細資訊，請參閱 [版本範圍](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="763f7-251">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="763f7-252">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-252">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="763f7-253">下列範例中的專案檔程式碼片段會參考 [system.object](https://www.nuget.org/packages/System.Runtime/) 套件。</span><span class="sxs-lookup"><span data-stu-id="763f7-253">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="763f7-254">如需詳細資訊，請參閱 [專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="763f7-254">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="763f7-255">專案參考</span><span class="sxs-lookup"><span data-stu-id="763f7-255">ProjectReference</span></span>

<span data-ttu-id="763f7-256">`ProjectReference`專案會定義另一個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="763f7-256">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="763f7-257">參考的專案會新增為 NuGet 套件相依性，亦即，它會被視為與相同 `PackageReference` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-257">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="763f7-258">`Include`屬性會指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="763f7-258">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="763f7-259">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-259">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="763f7-260">下列範例中的專案檔程式碼片段會參考名為的專案 `Project2` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-260">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="763f7-261">參考資料</span><span class="sxs-lookup"><span data-stu-id="763f7-261">Reference</span></span>

<span data-ttu-id="763f7-262">`Reference`專案會定義元件檔的參考。</span><span class="sxs-lookup"><span data-stu-id="763f7-262">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="763f7-263">`Include`屬性會指定檔案名，而 `HintPath` 中繼資料會指定元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="763f7-263">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="763f7-264">還原屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-264">Restore properties</span></span>

<span data-ttu-id="763f7-265">還原參考的封裝會安裝其所有直接相依性，以及這些相依性的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="763f7-265">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="763f7-266">您可以藉由指定屬性（例如和）來自訂封裝還原 `RestorePackagesPath` `RestoreIgnoreFailedSources` 。</span><span class="sxs-lookup"><span data-stu-id="763f7-266">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="763f7-267">如需這些屬性和其他屬性的詳細資訊，請參閱 [還原目標](/nuget/reference/msbuild-targets#restore-target)。</span><span class="sxs-lookup"><span data-stu-id="763f7-267">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="763f7-268">另請參閱</span><span class="sxs-lookup"><span data-stu-id="763f7-268">See also</span></span>

- [<span data-ttu-id="763f7-269">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="763f7-269">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="763f7-270">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-270">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="763f7-271">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-271">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="763f7-272">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="763f7-272">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="763f7-273">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="763f7-273">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
