---
title: MS 為 Microsoft.NET.sdk 構建屬性
description: 對 .NET 核心 SDK 理解的 MSBuild 屬性的引用。
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399179"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="45b51-103">MSBuild 屬性為 .NET 核心 SDK 專案</span><span class="sxs-lookup"><span data-stu-id="45b51-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="45b51-104">本頁介紹用於配置 .NET Core 專案的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="45b51-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="45b51-105">此頁正在進行中，不會列出 .NET Core SDK 的所有有用的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="45b51-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="45b51-106">有關常見 MSBuild 屬性的清單，請參閱[常見 MSBuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="45b51-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="45b51-107">框架屬性</span><span class="sxs-lookup"><span data-stu-id="45b51-107">Framework properties</span></span>

- [<span data-ttu-id="45b51-108">目標框架</span><span class="sxs-lookup"><span data-stu-id="45b51-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="45b51-109">目標框架</span><span class="sxs-lookup"><span data-stu-id="45b51-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="45b51-110">淨標準隱式包版本</span><span class="sxs-lookup"><span data-stu-id="45b51-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="45b51-111">目標框架</span><span class="sxs-lookup"><span data-stu-id="45b51-111">TargetFramework</span></span>

<span data-ttu-id="45b51-112">該`TargetFramework`屬性指定應用的目標框架版本，該版本隱式引用[元包](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="45b51-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="45b51-113">有關有效目標框架名字物件的清單，請參閱 SDK[樣式專案中的目標框架](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="45b51-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="45b51-114">有關詳細資訊，請參閱[SDK 樣式專案中的目標框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="45b51-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="45b51-115">目標框架</span><span class="sxs-lookup"><span data-stu-id="45b51-115">TargetFrameworks</span></span>

<span data-ttu-id="45b51-116">當您希望`TargetFrameworks`應用以多個平臺為目標時，請使用 該屬性。</span><span class="sxs-lookup"><span data-stu-id="45b51-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="45b51-117">有關有效目標框架名字物件的清單，請參閱 SDK[樣式專案中的目標框架](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="45b51-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="45b51-118">如果`TargetFramework`指定了（單數），則忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="45b51-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="45b51-119">有關詳細資訊，請參閱[SDK 樣式專案中的目標框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="45b51-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="45b51-120">淨標準隱式包版本</span><span class="sxs-lookup"><span data-stu-id="45b51-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="45b51-121">此屬性僅適用于使用`netstandard1.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="45b51-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="45b51-122">它不適用於使用`netstandard2.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="45b51-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="45b51-123">如果要指定`NetStandardImplicitPackageVersion`低於[元包](../packages.md#metapackages)版本的框架版本，請使用 該屬性。</span><span class="sxs-lookup"><span data-stu-id="45b51-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="45b51-124">以下示例中的專案檔案以目標為目標`netstandard1.3`，但使用`NETStandard.Library`的 1.6.0 版本。</span><span class="sxs-lookup"><span data-stu-id="45b51-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="45b51-125">發佈屬性</span><span class="sxs-lookup"><span data-stu-id="45b51-125">Publish properties</span></span>

- [<span data-ttu-id="45b51-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="45b51-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="45b51-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="45b51-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="45b51-128">使用應用主機</span><span class="sxs-lookup"><span data-stu-id="45b51-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="45b51-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="45b51-129">RuntimeIdentifier</span></span>

<span data-ttu-id="45b51-130">屬性`RuntimeIdentifier`允許您為專案指定單個[運行時識別碼 （RID）。](../rid-catalog.md)</span><span class="sxs-lookup"><span data-stu-id="45b51-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="45b51-131">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="45b51-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="45b51-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="45b51-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="45b51-133">該`RuntimeIdentifiers`屬性允許您為專案指定[運行時識別碼 （DD）](../rid-catalog.md)的分號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="45b51-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="45b51-134">如果需要為多個運行時發佈，請使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="45b51-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="45b51-135">`RuntimeIdentifiers`在還原時使用，以確保正確的資產在圖形中。</span><span class="sxs-lookup"><span data-stu-id="45b51-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="45b51-136">`RuntimeIdentifier`（單數）在只需要單個運行時時，可以提供更快的生成。</span><span class="sxs-lookup"><span data-stu-id="45b51-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="45b51-137">使用應用主機</span><span class="sxs-lookup"><span data-stu-id="45b51-137">UseAppHost</span></span>

<span data-ttu-id="45b51-138">該`UseAppHost`屬性在 .NET Core SDK 的 2.1.400 版本中引入。</span><span class="sxs-lookup"><span data-stu-id="45b51-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="45b51-139">它控制是否為部署創建本機可執行檔。</span><span class="sxs-lookup"><span data-stu-id="45b51-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="45b51-140">自包含部署需要本機可執行檔。</span><span class="sxs-lookup"><span data-stu-id="45b51-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="45b51-141">在 .NET Core 3.0 和更高版本中，預設情況下將創建與框架相關的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="45b51-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="45b51-142">將`UseAppHost`屬性設置為`false`禁用可執行檔的生成。</span><span class="sxs-lookup"><span data-stu-id="45b51-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="45b51-143">有關部署的詳細資訊，請參閱[.NET 核心應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="45b51-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="45b51-144">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="45b51-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="45b51-145">朗吉</span><span class="sxs-lookup"><span data-stu-id="45b51-145">LangVersion</span></span>

<span data-ttu-id="45b51-146">屬性`LangVersion`允許您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="45b51-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="45b51-147">例如，如果要訪問 C# 預覽功能，則設置為`LangVersion``preview`。</span><span class="sxs-lookup"><span data-stu-id="45b51-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="45b51-148">有關詳細資訊，請參閱[C# 語言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。</span><span class="sxs-lookup"><span data-stu-id="45b51-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="45b51-149">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="45b51-149">NuGet packages</span></span>

- [<span data-ttu-id="45b51-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="45b51-150">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="45b51-151">資產目標回退</span><span class="sxs-lookup"><span data-stu-id="45b51-151">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="45b51-152">PackageReference</span><span class="sxs-lookup"><span data-stu-id="45b51-152">PackageReference</span></span>

<span data-ttu-id="45b51-153">該專案`PackageReference`允許您指定 NuGet 依賴項。</span><span class="sxs-lookup"><span data-stu-id="45b51-153">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="45b51-154">例如，您可能希望引用單個包而不是[元包](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="45b51-154">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="45b51-155">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="45b51-155">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="45b51-156">以下示例中的專案檔案程式碼片段引用[System.Runtime](https://www.nuget.org/packages/System.Runtime/)包。</span><span class="sxs-lookup"><span data-stu-id="45b51-156">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="45b51-157">有關詳細資訊，請參閱[專案檔案中的包引用](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="45b51-157">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="45b51-158">資產目標回退</span><span class="sxs-lookup"><span data-stu-id="45b51-158">AssetTargetFallback</span></span>

<span data-ttu-id="45b51-159">該`AssetTargetFallback`屬性允許您為專案引用的專案和專案使用的 NuGet 包指定其他相容的框架版本。</span><span class="sxs-lookup"><span data-stu-id="45b51-159">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="45b51-160">例如，如果使用指定包依賴項，`PackageReference`但該包不包含與專案的相容的資產`TargetFramework`，則`AssetTargetFallback`屬性將發揮作用。</span><span class="sxs-lookup"><span data-stu-id="45b51-160">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="45b51-161">使用 中`AssetTargetFallback`指定的每個目標框架重新檢查引用包的相容性。</span><span class="sxs-lookup"><span data-stu-id="45b51-161">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="45b51-162">您可以將該`AssetTargetFallback`屬性設置為一個或多個[目標框架版本](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="45b51-162">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="45b51-163">打包和復原目標</span><span class="sxs-lookup"><span data-stu-id="45b51-163">Pack and restore targets</span></span>

<span data-ttu-id="45b51-164">MSBuild 15.1 `pack` `restore`引入了創建和還原 NuGet 包作為構建的一部分的目標。</span><span class="sxs-lookup"><span data-stu-id="45b51-164">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="45b51-165">有關這些目標的 MSBuild 屬性的資訊，請參閱`PackageTargetFallback` [NuGet 打包並還原為 MSBuild 目標](/nuget/reference/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="45b51-165">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="45b51-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45b51-166">See also</span></span>

- [<span data-ttu-id="45b51-167">MSBuild 架構引用</span><span class="sxs-lookup"><span data-stu-id="45b51-167">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="45b51-168">常見 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="45b51-168">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="45b51-169">用於 NuGet 包的 MS 構建屬性</span><span class="sxs-lookup"><span data-stu-id="45b51-169">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="45b51-170">用於 NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="45b51-170">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="45b51-171">自訂生成</span><span class="sxs-lookup"><span data-stu-id="45b51-171">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
