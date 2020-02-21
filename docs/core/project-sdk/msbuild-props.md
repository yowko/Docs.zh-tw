---
title: 適用于 .NET 的 MSBuild 屬性
description: .NET Core SDK 所瞭解之 MSBuild 屬性的參考。
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503817"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="59bc8-103">.NET Core SDK 專案的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="59bc8-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="59bc8-104">此頁面描述用於設定 .NET Core 專案的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="59bc8-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="59bc8-105">此頁面為進行中的工作，且不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="59bc8-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="59bc8-106">如需一般 MSBuild 屬性的清單，請參閱[一般 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="59bc8-107">架構屬性</span><span class="sxs-lookup"><span data-stu-id="59bc8-107">Framework properties</span></span>

- [<span data-ttu-id="59bc8-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="59bc8-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="59bc8-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="59bc8-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="59bc8-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="59bc8-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="59bc8-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="59bc8-111">TargetFramework</span></span>

<span data-ttu-id="59bc8-112">`TargetFramework` 屬性會指定應用程式的目標 framework 版本，其會隱含地參考[中繼套件](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="59bc8-113">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="59bc8-114">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="59bc8-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="59bc8-115">TargetFrameworks</span></span>

<span data-ttu-id="59bc8-116">當您想要讓應用程式以多個平臺為目標時，請使用 `TargetFrameworks` 屬性。</span><span class="sxs-lookup"><span data-stu-id="59bc8-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="59bc8-117">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="59bc8-118">如果指定 `TargetFramework` （單數），則會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="59bc8-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="59bc8-119">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="59bc8-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="59bc8-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="59bc8-121">此屬性僅適用于使用 `netstandard1.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="59bc8-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="59bc8-122">它不適用於使用 `netstandard2.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="59bc8-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="59bc8-123">當您想要指定低於[中繼套件](../packages.md#metapackages)版本的 framework 版本時，請使用 `NetStandardImplicitPackageVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="59bc8-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="59bc8-124">下列範例中的專案檔是以 `netstandard1.3` 為目標，但使用 `NETStandard.Library`的1.6.0 版本。</span><span class="sxs-lookup"><span data-stu-id="59bc8-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="59bc8-125">發佈屬性</span><span class="sxs-lookup"><span data-stu-id="59bc8-125">Publish properties</span></span>

- [<span data-ttu-id="59bc8-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="59bc8-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="59bc8-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="59bc8-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="59bc8-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="59bc8-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="59bc8-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="59bc8-129">RuntimeIdentifier</span></span>

<span data-ttu-id="59bc8-130">`RuntimeIdentifier` 屬性可讓您指定專案的單一[執行時間識別碼（RID）](../rid-catalog.md) 。</span><span class="sxs-lookup"><span data-stu-id="59bc8-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="59bc8-131">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="59bc8-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="59bc8-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="59bc8-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="59bc8-133">`RuntimeIdentifiers` 屬性可讓您指定專案的[執行時間識別碼（rid）清單（](../rid-catalog.md)以分號分隔）。</span><span class="sxs-lookup"><span data-stu-id="59bc8-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="59bc8-134">如果您需要針對多個執行時間發行，請使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="59bc8-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="59bc8-135">`RuntimeIdentifiers` 會在還原時使用，以確保正確的資產在圖形中。</span><span class="sxs-lookup"><span data-stu-id="59bc8-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="59bc8-136">當只需要單一執行時間時，`RuntimeIdentifier` （單數）可以提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="59bc8-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="59bc8-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="59bc8-137">UseAppHost</span></span>

<span data-ttu-id="59bc8-138">`UseAppHost` 屬性是在 .NET Core SDK 的2.1.400 版本中引進。</span><span class="sxs-lookup"><span data-stu-id="59bc8-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="59bc8-139">它會控制是否針對部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="59bc8-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="59bc8-140">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="59bc8-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="59bc8-141">在 .NET Core 3.0 和更新版本中，預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="59bc8-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="59bc8-142">將 [`UseAppHost`] 屬性設定為 [`false`]，以停用可執行檔的產生。</span><span class="sxs-lookup"><span data-stu-id="59bc8-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="59bc8-143">如需部署的詳細資訊，請參閱[.Net Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="59bc8-144">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="59bc8-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="59bc8-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="59bc8-145">LangVersion</span></span>

<span data-ttu-id="59bc8-146">`LangVersion` 屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="59bc8-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="59bc8-147">例如，如果您想要存取C#預覽功能，請將 `LangVersion` 設定為 `preview`。</span><span class="sxs-lookup"><span data-stu-id="59bc8-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="59bc8-148">如需詳細資訊，請參閱[ C#語言版本](../../csharp/language-reference/configure-language-version.md#override-a-default)設定。</span><span class="sxs-lookup"><span data-stu-id="59bc8-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="59bc8-149">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="59bc8-149">NuGet packages</span></span>

- [<span data-ttu-id="59bc8-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="59bc8-150">PackageReference</span></span>](#packagereference)

### <a name="packagereference"></a><span data-ttu-id="59bc8-151">PackageReference</span><span class="sxs-lookup"><span data-stu-id="59bc8-151">PackageReference</span></span>

<span data-ttu-id="59bc8-152">`PackageReference` 專案可讓您指定 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="59bc8-152">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="59bc8-153">例如，您可能想要參考單一封裝，而不是[中繼套件](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-153">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="59bc8-154">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="59bc8-154">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="59bc8-155">下列範例中的專案檔程式碼片段會參考[system.webserver](https://www.nuget.org/packages/System.Runtime/)封裝。</span><span class="sxs-lookup"><span data-stu-id="59bc8-155">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="59bc8-156">如需詳細資訊，請參閱[專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-156">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="pack-and-restore-targets"></a><span data-ttu-id="59bc8-157">套件和還原目標</span><span class="sxs-lookup"><span data-stu-id="59bc8-157">Pack and restore targets</span></span>

<span data-ttu-id="59bc8-158">MSBuild 15.1 引進了 `pack` 和 `restore` 目標，可在組建中建立和還原 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="59bc8-158">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="59bc8-159">如需這些目標之 MSBuild 屬性的相關資訊，包括 `PackageTargetFallback`，請參閱[NuGet 套件和還原為 MSBuild 目標](/nuget/reference/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="59bc8-159">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="59bc8-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59bc8-160">See also</span></span>

- [<span data-ttu-id="59bc8-161">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="59bc8-161">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="59bc8-162">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="59bc8-162">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="59bc8-163">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="59bc8-163">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="59bc8-164">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="59bc8-164">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="59bc8-165">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="59bc8-165">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
