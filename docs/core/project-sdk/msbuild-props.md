---
title: 適用于 Microsoft .NET 的 MSBuild 屬性
description: .NET SDK 瞭解的 MSBuild 屬性和專案參考。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: e7deb8c32fd01452524122e41f758ab037020ee4
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970703"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="a6a34-103">.NET SDK 專案的 MSBuild 參考</span><span class="sxs-lookup"><span data-stu-id="a6a34-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="a6a34-104">此頁面是 MSBuild 屬性和專案的參考，您可以使用這些屬性來設定 .NET 專案。</span><span class="sxs-lookup"><span data-stu-id="a6a34-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="a6a34-105">此頁面為進行中的工作，不會列出 .NET SDK 的所有實用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a34-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="a6a34-106">如需常見 MSBuild 屬性的清單，請參閱 [一般的 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="a6a34-107">架構屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-107">Framework properties</span></span>

- [<span data-ttu-id="a6a34-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a6a34-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="a6a34-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="a6a34-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="a6a34-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="a6a34-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="a6a34-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a6a34-111">TargetFramework</span></span>

<span data-ttu-id="a6a34-112">`TargetFramework`屬性會指定應用程式的目標 framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a6a34-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="a6a34-113">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="a6a34-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="a6a34-114">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="a6a34-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="a6a34-115">TargetFrameworks</span></span>

<span data-ttu-id="a6a34-116">`TargetFrameworks`當您想要讓應用程式以多個平臺為目標時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a34-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="a6a34-117">如需有效的目標 framework 名字標記清單，請參閱 [SDK 樣式專案中的目標](../../standard/frameworks.md#supported-target-frameworks)framework。</span><span class="sxs-lookup"><span data-stu-id="a6a34-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="a6a34-118">如果 `TargetFramework` 指定了 (單數) ，就會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a34-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="a6a34-119">如需詳細資訊，請參閱 [SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="a6a34-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="a6a34-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="a6a34-121">這個屬性只適用于使用 `netstandard1.x` 的專案。</span><span class="sxs-lookup"><span data-stu-id="a6a34-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="a6a34-122">它不適用於使用的專案 `netstandard2.x` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="a6a34-123">`NetStandardImplicitPackageVersion`當您想要指定的 framework 版本低於中繼套件版本時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a34-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="a6a34-124">下列範例中的專案檔會以 `netstandard1.3` 1.6.0 版本為目標，但會使用 `NETStandard.Library` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="a6a34-125">封裝屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-125">Package properties</span></span>

<span data-ttu-id="a6a34-126">您可以指定屬性，例如 `PackageId` 、 `PackageVersion` 、 `PackageIcon` 、 `Title` 和， `Description` 以描述從專案建立的封裝。</span><span class="sxs-lookup"><span data-stu-id="a6a34-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="a6a34-127">如需這些屬性和其他屬性的詳細資訊，請參閱 [套件目標](/nuget/reference/msbuild-targets#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="a6a34-128">發佈屬性和專案</span><span class="sxs-lookup"><span data-stu-id="a6a34-128">Publish properties and items</span></span>

- [<span data-ttu-id="a6a34-129">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a6a34-129">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="a6a34-130">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a6a34-130">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="a6a34-131">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="a6a34-131">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="a6a34-132">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="a6a34-132">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="a6a34-133">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="a6a34-133">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="a6a34-134">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a6a34-134">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="a6a34-135">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a6a34-135">UseAppHost</span></span>](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="a6a34-136">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a6a34-136">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="a6a34-137">`AppendTargetFrameworkToOutputPath`屬性控制是否要將[目標 framework 標記 (TFM) ](../../standard/frameworks.md)附加至[OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)) 所定義的輸出路徑 (。</span><span class="sxs-lookup"><span data-stu-id="a6a34-137">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="a6a34-138">.NET SDK 會自動將目標 framework （如果有的話）附加至輸出路徑的執行時間識別碼。</span><span class="sxs-lookup"><span data-stu-id="a6a34-138">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="a6a34-139">設定 `AppendTargetFrameworkToOutputPath` 以 `false` 防止將 TFM 附加至輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="a6a34-139">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="a6a34-140">但是，如果沒有 TFM 在輸出路徑中，多個組建成品可能會互相覆寫。</span><span class="sxs-lookup"><span data-stu-id="a6a34-140">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="a6a34-141">例如，針對 .NET 5.0 應用程式，輸出路徑會從變更 `bin\Debug\net5.0` 為， `bin\Debug` 並具有下列設定：</span><span class="sxs-lookup"><span data-stu-id="a6a34-141">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="a6a34-142">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a6a34-142">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="a6a34-143">`AppendRuntimeIdentifierToOutputPath`屬性控制是否要將[執行時間識別碼 (RID) ](../rid-catalog.md)附加至輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="a6a34-143">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="a6a34-144">.NET SDK 會自動將目標 framework （如果有的話）附加至輸出路徑的執行時間識別碼。</span><span class="sxs-lookup"><span data-stu-id="a6a34-144">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="a6a34-145">設定 `AppendRuntimeIdentifierToOutputPath` 以 `false` 防止將 RID 附加至輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="a6a34-145">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="a6a34-146">例如，針對 .NET 5.0 應用程式和的 RID `win10-x64` ，輸出路徑會從變更為， `bin\Debug\net5.0\win10-x64` `bin\Debug\net5.0` 並具有下列設定：</span><span class="sxs-lookup"><span data-stu-id="a6a34-146">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="a6a34-147">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="a6a34-147">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="a6a34-148">`CopyLocalLockFileAssemblies`屬性適用于具有其他程式庫相依性的外掛程式專案。</span><span class="sxs-lookup"><span data-stu-id="a6a34-148">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="a6a34-149">如果您將此屬性設定為 `true` ，任何 NuGet 套件相依性都會複製到輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="a6a34-149">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="a6a34-150">這表示您可以使用的輸出， `dotnet build` 在任何電腦上執行您的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="a6a34-150">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="a6a34-151">或者，您可以使用 `dotnet publish` 來發行類別庫。</span><span class="sxs-lookup"><span data-stu-id="a6a34-151">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="a6a34-152">如需詳細資訊，請參閱 [dotnet publish](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-152">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="a6a34-153">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="a6a34-153">RuntimeIdentifier</span></span>

<span data-ttu-id="a6a34-154">`RuntimeIdentifier`屬性可讓您為專案指定[ (RID) ](../rid-catalog.md)的單一執行時間識別碼。</span><span class="sxs-lookup"><span data-stu-id="a6a34-154">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a6a34-155">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="a6a34-155">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="a6a34-156">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="a6a34-156">RuntimeIdentifiers</span></span>

<span data-ttu-id="a6a34-157">`RuntimeIdentifiers`屬性可讓您為專案指定以分號分隔的[執行時間識別碼清單， (rid) ](../rid-catalog.md) 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-157">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a6a34-158">如果您需要發行多個執行時間，請使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a34-158">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="a6a34-159">`RuntimeIdentifiers` 會在還原時使用，以確保圖表中有正確的資產。</span><span class="sxs-lookup"><span data-stu-id="a6a34-159">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="a6a34-160">`RuntimeIdentifier` (單數) 可以在只需要單一執行時間時提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="a6a34-160">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="a6a34-161">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a6a34-161">TrimmerRootAssembly</span></span>

<span data-ttu-id="a6a34-162">`TrimmerRootAssembly`專案可讓您從 [*修剪*](../deploying/trim-self-contained.md)中排除元件。</span><span class="sxs-lookup"><span data-stu-id="a6a34-162">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="a6a34-163">修剪是從封裝的應用程式中移除執行時間未使用部分的進程。</span><span class="sxs-lookup"><span data-stu-id="a6a34-163">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="a6a34-164">在某些情況下，修剪可能會不正確地移除必要的參考。</span><span class="sxs-lookup"><span data-stu-id="a6a34-164">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="a6a34-165">下列 XML 會將 `System.Security` 元件從修剪中排除。</span><span class="sxs-lookup"><span data-stu-id="a6a34-165">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="a6a34-166">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a6a34-166">UseAppHost</span></span>

<span data-ttu-id="a6a34-167">`UseAppHost`屬性控制是否為部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a6a34-167">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="a6a34-168">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a6a34-168">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="a6a34-169">在 .NET Core 3.0 和更新版本中，依預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a6a34-169">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="a6a34-170">將 `UseAppHost` 屬性設為， `false` 以停用產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a6a34-170">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="a6a34-171">如需部署的詳細資訊，請參閱 [.net 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-171">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="a6a34-172">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-172">Compile properties</span></span>

- [<span data-ttu-id="a6a34-173">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="a6a34-173">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="a6a34-174">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a6a34-174">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="a6a34-175">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="a6a34-175">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="a6a34-176">`EmbeddedResourceUseDependentUponConvention`屬性定義是否從原始程式檔中的型別資訊產生資源資訊清單檔案名，而這些來源檔案與資源檔共存。</span><span class="sxs-lookup"><span data-stu-id="a6a34-176">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="a6a34-177">例如，如果 *Form1* 與 *Form1.cs* 位於相同的資料夾中，而且 `EmbeddedResourceUseDependentUponConvention` 設定為 `true` ，則產生的 *.resources* 檔會從 *Form1.cs* 中定義的第一個類型取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="a6a34-177">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="a6a34-178">例如，如果 `MyNamespace.Form1` 是 *Form1.cs* 中所定義的第一個型別，則產生的檔案名會是 *MyNamespace。*</span><span class="sxs-lookup"><span data-stu-id="a6a34-178">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="a6a34-179">如果 `LogicalName` 為 `ManifestResourceName` `DependentUpon` 專案指定、或中繼資料 `EmbeddedResource` ，則會改為以該中繼資料為基礎，產生該資源檔的資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="a6a34-179">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="a6a34-180">根據預設，在新的 .NET 專案中，這個屬性會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-180">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="a6a34-181">如果設定為 `false` ，且 `LogicalName` 專案檔中的專案未指定任何、 `ManifestResourceName` 或 `DependentUpon` 中繼資料 `EmbeddedResource` ，則資源資訊清單檔案名會以專案的根命名空間和 .resx 檔案的相對檔案路徑為基礎 *。*</span><span class="sxs-lookup"><span data-stu-id="a6a34-181">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="a6a34-182">如需詳細資訊，請參閱 [資源資訊清單檔案的命名方式](../resources/manifest-file-names.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-182">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="a6a34-183">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a6a34-183">LangVersion</span></span>

<span data-ttu-id="a6a34-184">`LangVersion`屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="a6a34-184">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="a6a34-185">例如，如果您想要存取 c # 預覽功能，請將設定 `LangVersion` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-185">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="a6a34-186">如需詳細資訊，請參閱 [c # 語言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-186">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="a6a34-187">預設專案包含屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-187">Default item inclusion properties</span></span>

- [<span data-ttu-id="a6a34-188">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="a6a34-188">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="a6a34-189">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="a6a34-189">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="a6a34-190">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-190">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="a6a34-191">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-191">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="a6a34-192">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-192">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="a6a34-193">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-193">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="a6a34-194">如需詳細資訊，請參閱 [預設包含和排除](overview.md#default-includes-and-excludes)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-194">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="a6a34-195">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="a6a34-195">DefaultItemExcludes</span></span>

<span data-ttu-id="a6a34-196">您 `DefaultItemExcludes` 可以使用屬性來定義應從包含、排除和移除 glob 中排除之檔案和資料夾的 glob 模式。</span><span class="sxs-lookup"><span data-stu-id="a6a34-196">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="a6a34-197">根據預設， */bin* 和 *./obj* 資料夾會從 glob 模式中排除。</span><span class="sxs-lookup"><span data-stu-id="a6a34-197">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="a6a34-198">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="a6a34-198">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="a6a34-199">您 `DefaultExcludesInProjectFolder` 可以使用屬性來定義專案資料夾中檔案和資料夾的 glob 模式，這些檔案和資料夾應從 include、exclude 和 remove glob 中排除。</span><span class="sxs-lookup"><span data-stu-id="a6a34-199">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="a6a34-200">根據預設，以句點開頭的資料夾 (`.`) （例如， *git* 和 *.*.）會從 glob 模式中排除。</span><span class="sxs-lookup"><span data-stu-id="a6a34-200">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="a6a34-201">這個屬性與屬性非常類似 `DefaultItemExcludes` ，不同之處在于它只會考慮專案資料夾中的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="a6a34-201">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="a6a34-202">當 glob 模式不慎比對專案資料夾外的相對路徑專案時，請使用屬性， `DefaultExcludesInProjectFolder` 而非 `DefaultItemExcludes` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a34-202">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="a6a34-203">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-203">EnableDefaultItems</span></span>

<span data-ttu-id="a6a34-204">`EnableDefaultItems`屬性會控制編譯專案、內嵌資源專案和專案是否 `None` 會以隱含方式包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="a6a34-204">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="a6a34-205">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="a6a34-205">The default value is `true`.</span></span> <span data-ttu-id="a6a34-206">將 `EnableDefaultItems` 屬性設為， `false` 以停用所有隱含檔案包含。</span><span class="sxs-lookup"><span data-stu-id="a6a34-206">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="a6a34-207">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-207">EnableDefaultCompileItems</span></span>

<span data-ttu-id="a6a34-208">`EnableDefaultCompileItems`屬性會控制編譯專案是否會以隱含方式包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="a6a34-208">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="a6a34-209">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="a6a34-209">The default value is `true`.</span></span> <span data-ttu-id="a6a34-210">將 `EnableDefaultCompileItems` 屬性設為， `false` 以停用隱含包含 \* .cs 和其他語言擴充檔。</span><span class="sxs-lookup"><span data-stu-id="a6a34-210">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="a6a34-211">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-211">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="a6a34-212">`EnableDefaultEmbeddedResourceItems`屬性會控制內嵌的資源專案是否會以隱含方式包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="a6a34-212">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="a6a34-213">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="a6a34-213">The default value is `true`.</span></span> <span data-ttu-id="a6a34-214">將 `EnableDefaultEmbeddedResourceItems` 屬性設為， `false` 以停用隱含包含內嵌的資源檔。</span><span class="sxs-lookup"><span data-stu-id="a6a34-214">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="a6a34-215">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="a6a34-215">EnableDefaultNoneItems</span></span>

<span data-ttu-id="a6a34-216">`EnableDefaultNoneItems`屬性會控制在 `None` 組建程式) 中， (沒有角色之檔案的專案是否會以隱含方式包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="a6a34-216">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="a6a34-217">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="a6a34-217">The default value is `true`.</span></span> <span data-ttu-id="a6a34-218">將 `EnableDefaultNoneItems` 屬性設為， `false` 以停用隱含包含 `None` 專案。</span><span class="sxs-lookup"><span data-stu-id="a6a34-218">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="a6a34-219">程式碼分析屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-219">Code analysis properties</span></span>

- [<span data-ttu-id="a6a34-220">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="a6a34-220">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="a6a34-221">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="a6a34-221">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="a6a34-222">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="a6a34-222">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="a6a34-223">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="a6a34-223">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="a6a34-224">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="a6a34-224">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="a6a34-225">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="a6a34-225">AnalysisLevel</span></span>

<span data-ttu-id="a6a34-226">`AnalysisLevel`屬性可讓您指定程式碼分析層級。</span><span class="sxs-lookup"><span data-stu-id="a6a34-226">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="a6a34-227">例如，如果您想要存取預覽程式碼分析器，請將設定 `AnalysisLevel` 為 `preview` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-227">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="a6a34-228">預設值是 `latest`。</span><span class="sxs-lookup"><span data-stu-id="a6a34-228">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="a6a34-229">下表顯示可用的選項。</span><span class="sxs-lookup"><span data-stu-id="a6a34-229">The following table shows the available options.</span></span>

| <span data-ttu-id="a6a34-230">值</span><span class="sxs-lookup"><span data-stu-id="a6a34-230">Value</span></span> | <span data-ttu-id="a6a34-231">意義</span><span class="sxs-lookup"><span data-stu-id="a6a34-231">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="a6a34-232">使用已發行的最新程式碼分析器。</span><span class="sxs-lookup"><span data-stu-id="a6a34-232">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="a6a34-233">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="a6a34-233">This is the default.</span></span> |
| `preview` | <span data-ttu-id="a6a34-234">使用最新的程式碼分析器，即使它們處於預覽狀態也一樣。</span><span class="sxs-lookup"><span data-stu-id="a6a34-234">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="a6a34-235">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="a6a34-235">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="a6a34-236">即使有較新的規則，也會使用針對 .NET 5.0 版本啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="a6a34-236">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="a6a34-237">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="a6a34-237">AnalysisMode</span></span>

<span data-ttu-id="a6a34-238">從 .NET 5.0 開始，.NET SDK 隨附所有「CA」程式 [代碼品質規則](../../fundamentals/code-analysis/quality-rules/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-238">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="a6a34-239">依預設，只 [會啟用部分規則](../../fundamentals/code-analysis/overview.md#enabled-rules) 做為組建警告。</span><span class="sxs-lookup"><span data-stu-id="a6a34-239">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="a6a34-240">`AnalysisMode`屬性可讓您自訂預設啟用的規則集。</span><span class="sxs-lookup"><span data-stu-id="a6a34-240">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="a6a34-241">您可以切換至更積極的 (退出) 分析模式或更保守的 (加入) 分析模式。</span><span class="sxs-lookup"><span data-stu-id="a6a34-241">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="a6a34-242">例如，如果您想要預設啟用所有規則作為組建警告，請將值設定為 `AllEnabledByDefault` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-242">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="a6a34-243">下表顯示可用的選項。</span><span class="sxs-lookup"><span data-stu-id="a6a34-243">The following table shows the available options.</span></span>

| <span data-ttu-id="a6a34-244">值</span><span class="sxs-lookup"><span data-stu-id="a6a34-244">Value</span></span> | <span data-ttu-id="a6a34-245">意義</span><span class="sxs-lookup"><span data-stu-id="a6a34-245">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="a6a34-246">預設模式，其中某些規則會啟用為組建警告，某些規則會啟用為 Visual Studio IDE 建議，並停用其餘部分。</span><span class="sxs-lookup"><span data-stu-id="a6a34-246">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="a6a34-247">積極或退出模式，預設會啟用所有規則作為組建警告。</span><span class="sxs-lookup"><span data-stu-id="a6a34-247">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="a6a34-248">您可以選擇性地 [退出宣告](../../fundamentals/code-analysis/configuration-options.md) 個別規則來停用它們。</span><span class="sxs-lookup"><span data-stu-id="a6a34-248">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="a6a34-249">保守或加入宣告模式，預設會停用所有規則。</span><span class="sxs-lookup"><span data-stu-id="a6a34-249">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="a6a34-250">您可以選擇性地 [選擇](../../fundamentals/code-analysis/configuration-options.md) 加入個別規則來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="a6a34-250">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="a6a34-251">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="a6a34-251">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="a6a34-252">`CodeAnalysisTreatWarningsAsErrors`屬性可讓您設定是否要將程式碼品質分析警告 (CAxxxx) 應該視為警告並中斷組建。</span><span class="sxs-lookup"><span data-stu-id="a6a34-252">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="a6a34-253">如果您在 `-warnaserror` 建立專案時使用旗標，則也會將 [.net 程式碼品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis) 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="a6a34-253">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="a6a34-254">如果您不想將程式碼品質分析警告視為錯誤，您可以 `CodeAnalysisTreatWarningsAsErrors` 在專案檔中將 MSBuild 屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-254">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="a6a34-255">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="a6a34-255">EnableNETAnalyzers</span></span>

<span data-ttu-id="a6a34-256">針對以 .NET 5.0 或更新版本為目標的專案，預設會啟用[.net 程式碼品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-256">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="a6a34-257">您可以藉由將屬性設定為，為以舊版 .NET 為目標的專案啟用 .NET 程式碼分析 `EnableNETAnalyzers` `true` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-257">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="a6a34-258">若要在任何專案中停用程式碼分析，請將這個屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-258">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="a6a34-259">針對以 .net 5.0 之前的 .NET 版本為目標的專案啟用 .NET 程式碼分析的另一種方式，是將 [AnalysisLevel](#analysislevel) 屬性設定為 `latest` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-259">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="a6a34-260">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="a6a34-260">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="a6a34-261">這項功能目前為實驗性，而且在 .NET 5 和 .NET 6 版本之間可能會變更。</span><span class="sxs-lookup"><span data-stu-id="a6a34-261">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="a6a34-262">根據預設， [.net 程式碼樣式分析](../../fundamentals/code-analysis/overview.md#code-style-analysis)會在所有 .net 專案的組建上停用。</span><span class="sxs-lookup"><span data-stu-id="a6a34-262">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="a6a34-263">您可以藉由將屬性設定為，啟用 .NET 專案的程式碼樣式分析 `EnforceCodeStyleInBuild` `true` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-263">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="a6a34-264">所有 [設定](../../fundamentals/code-analysis/overview.md#code-style-analysis) 為警告或錯誤的程式碼樣式規則，都會在組建和報告違規時執行。</span><span class="sxs-lookup"><span data-stu-id="a6a34-264">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="a6a34-265">執行時間設定屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-265">Run-time configuration properties</span></span>

<span data-ttu-id="a6a34-266">您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="a6a34-266">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="a6a34-267">如需設定執行時間行為之其他方式的詳細資訊，請參閱 [執行時間設定](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-267">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="a6a34-268">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a6a34-268">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="a6a34-269">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="a6a34-269">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="a6a34-270">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a6a34-270">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="a6a34-271">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a6a34-271">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="a6a34-272">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a6a34-272">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="a6a34-273">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a6a34-273">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="a6a34-274">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a6a34-274">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="a6a34-275">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="a6a34-275">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="a6a34-276">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="a6a34-276">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="a6a34-277">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a6a34-277">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="a6a34-278">`ConcurrentGarbageCollection`屬性會設定是否啟用[背景 (並行) 垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-278">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="a6a34-279">將值設定為 `false` ，以停用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a6a34-279">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="a6a34-280">如需詳細資訊，請參閱 [背景 GC](../run-time-config/garbage-collector.md#background-gc)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-280">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="a6a34-281">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="a6a34-281">InvariantGlobalization</span></span>

<span data-ttu-id="a6a34-282">`InvariantGlobalization`屬性會設定應用程式是否以 *全球化不變的* 模式執行，這表示它無法存取特定文化特性的資料。</span><span class="sxs-lookup"><span data-stu-id="a6a34-282">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="a6a34-283">將值設定為 `true` ，以在全球化非變異模式中執行。</span><span class="sxs-lookup"><span data-stu-id="a6a34-283">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="a6a34-284">如需詳細資訊，請參閱不 [變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-284">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="a6a34-285">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a6a34-285">RetainVMGarbageCollection</span></span>

<span data-ttu-id="a6a34-286">屬性會將 `RetainVMGarbageCollection` 垃圾收集行程設定為將已刪除的記憶體區段放置於待命清單上，以供日後使用或釋放它們。</span><span class="sxs-lookup"><span data-stu-id="a6a34-286">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="a6a34-287">將此值設定為可 `true` 告知垃圾收集行程將區段放在待命清單上。</span><span class="sxs-lookup"><span data-stu-id="a6a34-287">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="a6a34-288">如需詳細資訊，請參閱 [保留 VM](../run-time-config/garbage-collector.md#retain-vm)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-288">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="a6a34-289">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a6a34-289">ServerGarbageCollection</span></span>

<span data-ttu-id="a6a34-290">屬性會設定 `ServerGarbageCollection` 應用程式是使用 [工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-290">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="a6a34-291">將值設定為，以 `true` 使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a6a34-291">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="a6a34-292">如需詳細資訊，請參閱 [工作站與伺服器](../run-time-config/garbage-collector.md#workstation-vs-server)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-292">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="a6a34-293">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a6a34-293">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="a6a34-294">屬性會設定背景 `ThreadPoolMaxThreads` 工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="a6a34-294">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a6a34-295">如需詳細資訊，請參閱 [最大執行緒數目](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-295">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="a6a34-296">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a6a34-296">ThreadPoolMinThreads</span></span>

<span data-ttu-id="a6a34-297">`ThreadPoolMinThreads`屬性會為背景工作執行緒集區設定執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="a6a34-297">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a6a34-298">如需詳細資訊，請參閱 [最小線程](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-298">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="a6a34-299">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a6a34-299">TieredCompilation</span></span>

<span data-ttu-id="a6a34-300">屬性會設定 `TieredCompilation` 及時 (JIT) 編譯器是否使用 [分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-300">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="a6a34-301">將值設定為 `false` ，以停用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="a6a34-301">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="a6a34-302">如需詳細資訊，請參閱 [分層式編譯](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-302">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="a6a34-303">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="a6a34-303">TieredCompilationQuickJit</span></span>

<span data-ttu-id="a6a34-304">屬性會設定 `TieredCompilationQuickJit` jit 編譯器是否使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="a6a34-304">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="a6a34-305">將值設定為 `false` ，以停用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="a6a34-305">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="a6a34-306">如需詳細資訊，請參閱 [快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-306">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="a6a34-307">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="a6a34-307">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="a6a34-308">`TieredCompilationQuickJitForLoops`屬性會設定 jit 編譯器是否在包含迴圈的方法上使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="a6a34-308">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a6a34-309">將值設定為， `true` 以在包含迴圈的方法上啟用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="a6a34-309">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a6a34-310">如需詳細資訊，請參閱 [快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-310">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="a6a34-311">參考屬性和專案</span><span class="sxs-lookup"><span data-stu-id="a6a34-311">Reference properties and items</span></span>

- [<span data-ttu-id="a6a34-312">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a6a34-312">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="a6a34-313">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="a6a34-313">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="a6a34-314">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a6a34-314">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="a6a34-315">專案參考</span><span class="sxs-lookup"><span data-stu-id="a6a34-315">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="a6a34-316">參考</span><span class="sxs-lookup"><span data-stu-id="a6a34-316">Reference</span></span>](#reference)
- [<span data-ttu-id="a6a34-317">還原相關的屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-317">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="a6a34-318">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a6a34-318">AssetTargetFallback</span></span>

<span data-ttu-id="a6a34-319">`AssetTargetFallback`屬性可讓您為專案參考和 NuGet 套件指定其他相容的架構版本。</span><span class="sxs-lookup"><span data-stu-id="a6a34-319">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="a6a34-320">例如，如果您使用指定套件相依性， `PackageReference` 但該套件未包含與您的專案相容的資產 `TargetFramework` ，則此 `AssetTargetFallback` 屬性會進入 play。</span><span class="sxs-lookup"><span data-stu-id="a6a34-320">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="a6a34-321">參考封裝的相容性是使用中所指定的每一個目標架構來間隔 `AssetTargetFallback` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-321">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="a6a34-322">您可以將 `AssetTargetFallback` 屬性設定為一或多個 [目標 framework 版本](../../standard/frameworks.md#supported-target-frameworks)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-322">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="a6a34-323">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="a6a34-323">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="a6a34-324">以 `DisableImplicitFrameworkReferences` `FrameworkReference` .net Core 3.0 和更新版本為目標時，屬性會控制隱含專案。</span><span class="sxs-lookup"><span data-stu-id="a6a34-324">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="a6a34-325">以 .NET Core 2.1 或 .NET Standard 2.0 和更早版本為目標時，它會在中繼套件中控制封裝的隱含 [PackageReference](#packagereference) 專案。</span><span class="sxs-lookup"><span data-stu-id="a6a34-325">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="a6a34-326"> (中繼套件是以架構為基礎的封裝，其中只包含其他封裝的相依性。 ) 此屬性也會控制以 `System` .NET Framework 為 `System.Core` 目標時的隱含參考，例如和。</span><span class="sxs-lookup"><span data-stu-id="a6a34-326">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="a6a34-327">將這個屬性設定為， `true` 以停用隱含 `FrameworkReference` 或 [PackageReference](#packagereference) 專案。</span><span class="sxs-lookup"><span data-stu-id="a6a34-327">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="a6a34-328">如果您將此屬性設定為 `true` ，您可以只將明確參考新增至所需的架構或封裝。</span><span class="sxs-lookup"><span data-stu-id="a6a34-328">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="a6a34-329">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a6a34-329">PackageReference</span></span>

<span data-ttu-id="a6a34-330">`PackageReference`專案會定義 NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="a6a34-330">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="a6a34-331">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="a6a34-331">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="a6a34-332">`Version`屬性會指定版本或版本範圍。</span><span class="sxs-lookup"><span data-stu-id="a6a34-332">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="a6a34-333">如需有關如何指定最小版本、最大版本、範圍或完全相符的詳細資訊，請參閱 [版本範圍](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-333">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="a6a34-334">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-334">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="a6a34-335">下列範例中的專案檔程式碼片段會參考 [system.object](https://www.nuget.org/packages/System.Runtime/) 套件。</span><span class="sxs-lookup"><span data-stu-id="a6a34-335">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="a6a34-336">如需詳細資訊，請參閱 [專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-336">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="a6a34-337">專案參考</span><span class="sxs-lookup"><span data-stu-id="a6a34-337">ProjectReference</span></span>

<span data-ttu-id="a6a34-338">`ProjectReference`專案會定義另一個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="a6a34-338">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="a6a34-339">參考的專案會新增為 NuGet 套件相依性，亦即，它會被視為與相同 `PackageReference` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-339">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="a6a34-340">`Include`屬性會指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a6a34-340">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="a6a34-341">您也可以將下列中繼資料加入至專案參考： `IncludeAssets` 、 `ExcludeAssets` 和 `PrivateAssets` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-341">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="a6a34-342">下列範例中的專案檔程式碼片段會參考名為的專案 `Project2` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-342">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="a6a34-343">參考資料</span><span class="sxs-lookup"><span data-stu-id="a6a34-343">Reference</span></span>

<span data-ttu-id="a6a34-344">`Reference`專案會定義元件檔的參考。</span><span class="sxs-lookup"><span data-stu-id="a6a34-344">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="a6a34-345">`Include`屬性會指定檔案名，而 `HintPath` 中繼資料會指定元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a6a34-345">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="a6a34-346">還原相關的屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-346">Restore-related properties</span></span>

<span data-ttu-id="a6a34-347">還原參考的封裝會安裝其所有直接相依性，以及這些相依性的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="a6a34-347">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="a6a34-348">您可以藉由指定屬性（例如和）來自訂封裝還原 `RestorePackagesPath` `RestoreIgnoreFailedSources` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-348">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="a6a34-349">如需這些屬性和其他屬性的詳細資訊，請參閱 [還原目標](/nuget/reference/msbuild-targets#restore-target)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-349">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a><span data-ttu-id="a6a34-350">執行屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-350">Run properties</span></span>

<span data-ttu-id="a6a34-351">下列屬性是用來使用命令來啟動應用程式 [`dotnet run`](../tools/dotnet-run.md) ：</span><span class="sxs-lookup"><span data-stu-id="a6a34-351">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="a6a34-352">RunArguments</span><span class="sxs-lookup"><span data-stu-id="a6a34-352">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="a6a34-353">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="a6a34-353">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="a6a34-354">RunArguments</span><span class="sxs-lookup"><span data-stu-id="a6a34-354">RunArguments</span></span>

<span data-ttu-id="a6a34-355">`RunArguments`屬性會定義在應用程式執行時傳遞給該應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="a6a34-355">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="a6a34-356">您可以使用的[ `--` 選項 `dotnet run` ](../tools/dotnet-run.md#options)，指定要傳遞至應用程式的其他引數。</span><span class="sxs-lookup"><span data-stu-id="a6a34-356">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="a6a34-357">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="a6a34-357">RunWorkingDirectory</span></span>

<span data-ttu-id="a6a34-358">`RunWorkingDirectory`屬性會定義要在其中啟動應用程式進程的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="a6a34-358">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="a6a34-359">它可以是絕對路徑或相對於專案目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="a6a34-359">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="a6a34-360">如果您未指定目錄， `OutDir` 則會使用做為工作目錄。</span><span class="sxs-lookup"><span data-stu-id="a6a34-360">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a><span data-ttu-id="a6a34-361">裝載屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-361">Hosting properties</span></span>

- [<span data-ttu-id="a6a34-362">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="a6a34-362">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="a6a34-363">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="a6a34-363">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="a6a34-364">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="a6a34-364">EnableComHosting</span></span>

<span data-ttu-id="a6a34-365">`EnableComHosting`屬性工作表示元件提供 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6a34-365">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="a6a34-366">將設定 `EnableComHosting` 為 `true` 也表示 [EnableDynamicLoading](#enabledynamicloading) 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-366">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="a6a34-367">如需詳細資訊，請參閱 [將 .net 元件公開至 COM](../native-interop/expose-components-to-com.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a34-367">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="a6a34-368">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="a6a34-368">EnableDynamicLoading</span></span>

<span data-ttu-id="a6a34-369">`EnableDynamicLoading`屬性工作表示元件是動態載入的元件。</span><span class="sxs-lookup"><span data-stu-id="a6a34-369">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="a6a34-370">元件可以是 COM 連結 [庫](/windows/win32/com/the-component-object-model) 或可 [從原生主機使用](../tutorials/netcore-hosting.md)的非 com 程式庫。</span><span class="sxs-lookup"><span data-stu-id="a6a34-370">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="a6a34-371">將這個屬性設定為 `true` 具有下列效果：</span><span class="sxs-lookup"><span data-stu-id="a6a34-371">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="a6a34-372">會產生檔案 *上的.runtimeconfig.js* 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-372">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="a6a34-373">[向前](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) 復原是設定為 `LatestMinor` 。</span><span class="sxs-lookup"><span data-stu-id="a6a34-373">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="a6a34-374">NuGet 參考會在本機複製。</span><span class="sxs-lookup"><span data-stu-id="a6a34-374">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="a6a34-375">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6a34-375">See also</span></span>

- [<span data-ttu-id="a6a34-376">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="a6a34-376">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="a6a34-377">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-377">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="a6a34-378">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-378">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="a6a34-379">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="a6a34-379">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="a6a34-380">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="a6a34-380">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
