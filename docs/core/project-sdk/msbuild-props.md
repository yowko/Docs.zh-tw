---
title: 適用于 .NET 的 MSBuild 屬性
description: .NET Core SDK 所瞭解之 MSBuild 屬性和專案的參考。
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 115c4f32e856dee64abe0c607b8ee595a65692e6
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164382"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="4a47b-103">.NET Core SDK 專案的 MSBuild 參考</span><span class="sxs-lookup"><span data-stu-id="4a47b-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="4a47b-104">此頁面是您可以用來設定 .NET Core 專案之 MSBuild 屬性和專案的參考。</span><span class="sxs-lookup"><span data-stu-id="4a47b-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="4a47b-105">此頁面為進行中的工作，且不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="4a47b-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="4a47b-106">如需一般 MSBuild 屬性的清單，請參閱[一般 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="4a47b-107">架構屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-107">Framework properties</span></span>

- [<span data-ttu-id="4a47b-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="4a47b-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="4a47b-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="4a47b-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="4a47b-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="4a47b-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="4a47b-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="4a47b-111">TargetFramework</span></span>

<span data-ttu-id="4a47b-112">`TargetFramework`屬性會指定應用程式的目標 framework 版本。</span><span class="sxs-lookup"><span data-stu-id="4a47b-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="4a47b-113">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="4a47b-114">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="4a47b-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="4a47b-115">TargetFrameworks</span></span>

<span data-ttu-id="4a47b-116">`TargetFrameworks`當您想要讓應用程式以多個平臺為目標時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="4a47b-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="4a47b-117">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="4a47b-118">如果 `TargetFramework` 指定了（單數），則會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="4a47b-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="4a47b-119">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="4a47b-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="4a47b-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="4a47b-121">這個屬性僅適用于使用 `netstandard1.x` 的專案。</span><span class="sxs-lookup"><span data-stu-id="4a47b-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="4a47b-122">它不適用於使用的專案 `netstandard2.x` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="4a47b-123">`NetStandardImplicitPackageVersion`當您想要指定的 framework 版本低於中繼套件版本時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="4a47b-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="4a47b-124">下列範例中的專案檔會以為目標， `netstandard1.3` 但會使用的1.6.0 版本 `NETStandard.Library` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="4a47b-125">封裝屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-125">Package properties</span></span>

<span data-ttu-id="4a47b-126">您可以指定 `PackageId` 、 `PackageVersion` 、、和等屬性， `PackageIcon` `Title` `Description` 以描述從專案建立的封裝。</span><span class="sxs-lookup"><span data-stu-id="4a47b-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="4a47b-127">如需這些和其他屬性的詳細資訊，請參閱[pack target](/nuget/reference/msbuild-targets#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="4a47b-128">發行屬性和專案</span><span class="sxs-lookup"><span data-stu-id="4a47b-128">Publish properties and items</span></span>

- [<span data-ttu-id="4a47b-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="4a47b-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="4a47b-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="4a47b-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="4a47b-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="4a47b-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="4a47b-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="4a47b-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="4a47b-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="4a47b-133">RuntimeIdentifier</span></span>

<span data-ttu-id="4a47b-134">`RuntimeIdentifier`屬性可讓您指定專案的單一[執行時間識別碼（RID）](../rid-catalog.md) 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="4a47b-135">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="4a47b-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="4a47b-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="4a47b-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="4a47b-137">`RuntimeIdentifiers`屬性可讓您指定專案的[執行時間識別碼（rid）清單（](../rid-catalog.md)以分號分隔）。</span><span class="sxs-lookup"><span data-stu-id="4a47b-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="4a47b-138">如果您需要針對多個執行時間發行，請使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="4a47b-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="4a47b-139">`RuntimeIdentifiers`會在還原時使用，以確保正確的資產在圖形中。</span><span class="sxs-lookup"><span data-stu-id="4a47b-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="4a47b-140">`RuntimeIdentifier`（單數）可以在只需要單一執行時間時提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="4a47b-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="4a47b-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="4a47b-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="4a47b-142">`TrimmerRootAssembly`專案可讓您將元件從[*修剪*](../deploying/trim-self-contained.md)中排除。</span><span class="sxs-lookup"><span data-stu-id="4a47b-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="4a47b-143">修剪是從封裝的應用程式中移除執行時間未使用元件的程式。</span><span class="sxs-lookup"><span data-stu-id="4a47b-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="4a47b-144">在某些情況下，修剪可能會不正確地移除所需的參考。</span><span class="sxs-lookup"><span data-stu-id="4a47b-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="4a47b-145">下列 XML 會將 `System.Security` 元件從修剪中排除。</span><span class="sxs-lookup"><span data-stu-id="4a47b-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="4a47b-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="4a47b-146">UseAppHost</span></span>

<span data-ttu-id="4a47b-147">`UseAppHost`屬性是在 .NET Core SDK 的2.1.400 版本中引進。</span><span class="sxs-lookup"><span data-stu-id="4a47b-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="4a47b-148">它會控制是否針對部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="4a47b-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="4a47b-149">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="4a47b-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="4a47b-150">在 .NET Core 3.0 和更新版本中，預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="4a47b-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="4a47b-151">將 `UseAppHost` 屬性設定為 `false` ，以停用可執行檔的產生。</span><span class="sxs-lookup"><span data-stu-id="4a47b-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="4a47b-152">如需部署的詳細資訊，請參閱[.Net Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="4a47b-153">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-153">Compile properties</span></span>

- [<span data-ttu-id="4a47b-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="4a47b-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="4a47b-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="4a47b-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="4a47b-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="4a47b-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="4a47b-157">`EmbeddedResourceUseDependentUponConvention`屬性會定義是否從與資源檔共置的原始程式檔中的類型資訊產生資源資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="4a47b-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="4a47b-158">例如 *，如果 form1.vb 與* *Form1.cs*位於相同的資料夾中，而且 `EmbeddedResourceUseDependentUponConvention` 設定為 `true` ，則產生的 *.resources*檔案會從*Form1.cs*中所定義的第一個類型取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="4a47b-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="4a47b-159">例如，如果 `MyNamespace.Form1` 是*Form1.cs*中所定義的第一個型別，則產生的檔案名會是*MyNamespace*。</span><span class="sxs-lookup"><span data-stu-id="4a47b-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="4a47b-160">如果 `LogicalName` `ManifestResourceName` `DependentUpon` 已為專案指定、或中繼資料 `EmbeddedResource` ，則該資源檔產生的資訊清單檔案名會改為根據該中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4a47b-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="4a47b-161">根據預設，在新的 .NET Core 專案中，這個屬性會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="4a47b-162">如果設定為 `false` ，且未 `LogicalName` `ManifestResourceName` `DependentUpon` 針對專案檔中的專案指定、或中繼資料 `EmbeddedResource` ，則資源資訊清單檔案名會以專案的根命名空間和 *.resx*檔案的相對檔案路徑為基礎。</span><span class="sxs-lookup"><span data-stu-id="4a47b-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="4a47b-163">如需詳細資訊，請參閱[資源資訊清單檔案的命名方式](../resources/manifest-file-names.md)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="4a47b-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="4a47b-164">LangVersion</span></span>

<span data-ttu-id="4a47b-165">`LangVersion`屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="4a47b-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="4a47b-166">例如，如果您想要存取 c # preview 功能，請將設定 `LangVersion` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="4a47b-167">如需詳細資訊，請參閱[c # 語言版本](../../csharp/language-reference/configure-language-version.md#override-a-default)設定。</span><span class="sxs-lookup"><span data-stu-id="4a47b-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="4a47b-168">執行時間設定屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-168">Run-time configuration properties</span></span>

<span data-ttu-id="4a47b-169">您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="4a47b-169">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="4a47b-170">如需其他設定執行時間行為方式的相關資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-170">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="4a47b-171">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="4a47b-171">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="4a47b-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="4a47b-172">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="4a47b-173">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="4a47b-173">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="4a47b-174">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="4a47b-174">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="4a47b-175">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="4a47b-175">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="4a47b-176">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="4a47b-176">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="4a47b-177">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="4a47b-177">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="4a47b-178">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="4a47b-178">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="4a47b-179">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="4a47b-179">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="4a47b-180">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="4a47b-180">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="4a47b-181">`ConcurrentGarbageCollection`屬性會設定是否啟用[背景（並行）垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-181">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="4a47b-182">將值設定為 `false` ，以停用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4a47b-182">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="4a47b-183">如需詳細資訊，請參閱 system.string [. [並行/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)]。</span><span class="sxs-lookup"><span data-stu-id="4a47b-183">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="4a47b-184">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="4a47b-184">InvariantGlobalization</span></span>

<span data-ttu-id="4a47b-185">`InvariantGlobalization`屬性會設定應用程式是否以*全球化不變*模式執行，這表示它無法存取特定文化特性的資料。</span><span class="sxs-lookup"><span data-stu-id="4a47b-185">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="4a47b-186">將值設定為 `true` ，以在全球化-不變模式下執行。</span><span class="sxs-lookup"><span data-stu-id="4a47b-186">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="4a47b-187">如需詳細資訊，請參閱不[變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-187">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="4a47b-188">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="4a47b-188">RetainVMGarbageCollection</span></span>

<span data-ttu-id="4a47b-189">屬性會將 `RetainVMGarbageCollection` 垃圾收集行程設定為將已刪除的記憶體區段放在待命清單上以供日後使用或釋放它們。</span><span class="sxs-lookup"><span data-stu-id="4a47b-189">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="4a47b-190">將值設定為，會 `true` 指示垃圾收集行程將區段放在待命清單上。</span><span class="sxs-lookup"><span data-stu-id="4a47b-190">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="4a47b-191">如需詳細資訊，請參閱[RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-191">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="4a47b-192">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="4a47b-192">ServerGarbageCollection</span></span>

<span data-ttu-id="4a47b-193">屬性會設定 `ServerGarbageCollection` 應用程式是否使用[工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-193">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="4a47b-194">將值設定為 `true` ，以使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4a47b-194">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="4a47b-195">如需詳細資訊，請參閱[system.object/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-195">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="4a47b-196">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="4a47b-196">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="4a47b-197">屬性會設定背景 `ThreadPoolMaxThreads` 工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="4a47b-197">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="4a47b-198">如需詳細資訊，請參閱[執行緒上限](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-198">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="4a47b-199">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="4a47b-199">ThreadPoolMinThreads</span></span>

<span data-ttu-id="4a47b-200">屬性會設定背景 `ThreadPoolMinThreads` 工作執行緒集區的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="4a47b-200">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="4a47b-201">如需詳細資訊，請參閱[最小線程](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-201">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="4a47b-202">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="4a47b-202">TieredCompilation</span></span>

<span data-ttu-id="4a47b-203">屬性會設定 `TieredCompilation` 即時（JIT）編譯器是否使用[分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-203">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="4a47b-204">將值設定為 `false` ，以停用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="4a47b-204">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="4a47b-205">如需詳細資訊，請參閱[分層式編譯](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-205">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="4a47b-206">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="4a47b-206">TieredCompilationQuickJit</span></span>

<span data-ttu-id="4a47b-207">屬性會設定 `TieredCompilationQuickJit` JIT 編譯程式是否使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="4a47b-207">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="4a47b-208">將值設為 `false` 以停用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="4a47b-208">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="4a47b-209">如需詳細資訊，請參閱[快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-209">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="4a47b-210">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="4a47b-210">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="4a47b-211">屬性會設定 `TieredCompilationQuickJitForLoops` JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="4a47b-211">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="4a47b-212">將值設定為 `true` ，以啟用包含迴圈之方法的快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="4a47b-212">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="4a47b-213">如需詳細資訊，請參閱[快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-213">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="4a47b-214">參考屬性和專案</span><span class="sxs-lookup"><span data-stu-id="4a47b-214">Reference properties and items</span></span>

- [<span data-ttu-id="4a47b-215">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="4a47b-215">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="4a47b-216">PackageReference</span><span class="sxs-lookup"><span data-stu-id="4a47b-216">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="4a47b-217">專案參考</span><span class="sxs-lookup"><span data-stu-id="4a47b-217">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="4a47b-218">參考</span><span class="sxs-lookup"><span data-stu-id="4a47b-218">Reference</span></span>](#reference)
- [<span data-ttu-id="4a47b-219">還原屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-219">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="4a47b-220">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="4a47b-220">AssetTargetFallback</span></span>

<span data-ttu-id="4a47b-221">`AssetTargetFallback`屬性可讓您為專案參考和 NuGet 套件指定其他相容的架構版本。</span><span class="sxs-lookup"><span data-stu-id="4a47b-221">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="4a47b-222">例如，如果您使用指定封裝相依性， `PackageReference` 但該套件並未包含與您專案的相容的資產 `TargetFramework` ，則該 `AssetTargetFallback` 屬性會開始播放。</span><span class="sxs-lookup"><span data-stu-id="4a47b-222">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="4a47b-223">所參考封裝的相容性是使用中指定的每個目標架構來間隔 `AssetTargetFallback` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-223">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="4a47b-224">您可以將 `AssetTargetFallback` 屬性設定為一個或多個[目標 framework 版本](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-224">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="4a47b-225">PackageReference</span><span class="sxs-lookup"><span data-stu-id="4a47b-225">PackageReference</span></span>

<span data-ttu-id="4a47b-226">`PackageReference`專案會定義 NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="4a47b-226">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="4a47b-227">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a47b-227">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="4a47b-228">`Version`屬性會指定版本或版本範圍。</span><span class="sxs-lookup"><span data-stu-id="4a47b-228">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="4a47b-229">如需有關如何指定最小版本、最大版本、範圍或完全相符的詳細資訊，請參閱[版本範圍](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-229">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="4a47b-230">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="4a47b-231">下列範例中的專案檔程式碼片段會參考[system.webserver](https://www.nuget.org/packages/System.Runtime/)封裝。</span><span class="sxs-lookup"><span data-stu-id="4a47b-231">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="4a47b-232">如需詳細資訊，請參閱[專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-232">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="4a47b-233">專案參考</span><span class="sxs-lookup"><span data-stu-id="4a47b-233">ProjectReference</span></span>

<span data-ttu-id="4a47b-234">`ProjectReference`專案會定義對另一個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="4a47b-234">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="4a47b-235">參考的專案會新增為 NuGet 套件相依性，亦即，它會被視為與相同 `PackageReference` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-235">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="4a47b-236">`Include`屬性會指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a47b-236">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="4a47b-237">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-237">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="4a47b-238">下列範例中的專案檔程式碼片段會參考名為的專案 `Project2` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-238">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="4a47b-239">參考</span><span class="sxs-lookup"><span data-stu-id="4a47b-239">Reference</span></span>

<span data-ttu-id="4a47b-240">`Reference`專案會定義元件檔的參考。</span><span class="sxs-lookup"><span data-stu-id="4a47b-240">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="4a47b-241">`Include`屬性會指定檔案名，而 `HintPath` 中繼資料會指定元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a47b-241">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="4a47b-242">還原屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-242">Restore properties</span></span>

<span data-ttu-id="4a47b-243">還原參考的套件會安裝其所有的直接相依性，以及這些相依性的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="4a47b-243">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="4a47b-244">您可以藉由指定如和的屬性來自訂封裝還原 `RestorePackagesPath` `RestoreIgnoreFailedSources` 。</span><span class="sxs-lookup"><span data-stu-id="4a47b-244">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="4a47b-245">如需這些和其他屬性的詳細資訊，請參閱[還原目標](/nuget/reference/msbuild-targets#restore-target)。</span><span class="sxs-lookup"><span data-stu-id="4a47b-245">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="4a47b-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a47b-246">See also</span></span>

- [<span data-ttu-id="4a47b-247">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="4a47b-247">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="4a47b-248">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-248">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="4a47b-249">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-249">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="4a47b-250">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="4a47b-250">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="4a47b-251">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="4a47b-251">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
