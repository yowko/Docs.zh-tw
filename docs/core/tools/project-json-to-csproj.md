---
title: project.json 與 csproj 比較
description: 查看 project.json 與 csproj 項目的對應。
author: natemcmaster
ms.date: 03/13/2017
ms.custom: seodec18
ms.openlocfilehash: 581ff7cd3fe02e22d481c8386776317a5251cc5c
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168894"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="ac526-103">project.json 與 csproj 屬性的對應</span><span class="sxs-lookup"><span data-stu-id="ac526-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="ac526-104">作者：[Nate McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="ac526-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="ac526-105">在 .NET Core 工具開發期間，有項重要的設計變更導致不再支援 *project.json* 檔案，相反地，.NET Core 專案會改為使用 MSBuild/csproj 格式。</span><span class="sxs-lookup"><span data-stu-id="ac526-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="ac526-106">本文說明如何以 MSBuild/csproj 格式表示 *project.json* 中的設定，讓您了解如何使用此新的格式，並了解將專案升級至最新版的工具時，移轉工具所做的變更。</span><span class="sxs-lookup"><span data-stu-id="ac526-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="ac526-107">csproj 格式</span><span class="sxs-lookup"><span data-stu-id="ac526-107">The csproj format</span></span>

<span data-ttu-id="ac526-108">新格式 \*.csproj 是以 XML 為基礎的格式。</span><span class="sxs-lookup"><span data-stu-id="ac526-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="ac526-109">下列範例顯示使用 `Microsoft.NET.Sdk` 之 .NET Core 專案的根節點。</span><span class="sxs-lookup"><span data-stu-id="ac526-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="ac526-110">若是 Web 專案，所使用的 SDK 會是 `Microsoft.NET.Sdk.Web`。</span><span class="sxs-lookup"><span data-stu-id="ac526-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="ac526-111">常見的最上層屬性</span><span class="sxs-lookup"><span data-stu-id="ac526-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="ac526-112">名稱</span><span class="sxs-lookup"><span data-stu-id="ac526-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="ac526-113">不再支援此屬性。</span><span class="sxs-lookup"><span data-stu-id="ac526-113">No longer supported.</span></span> <span data-ttu-id="ac526-114">在 csproj 中，這是由目錄名稱所定義的專案檔名所決定。</span><span class="sxs-lookup"><span data-stu-id="ac526-114">In csproj, this is determined by the project filename, which is defined by the directory name.</span></span> <span data-ttu-id="ac526-115">例如，`MyProjectName.csproj`。</span><span class="sxs-lookup"><span data-stu-id="ac526-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="ac526-116">根據預設，專案檔名也會指定 `<AssemblyName>` 和 `<PackageId>` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ac526-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="ac526-117">如果 `buildOptions\outputName` 屬性定義於 project.json，則 `<AssemblyName>` 會有與 `<PackageId>` 不同的值。</span><span class="sxs-lookup"><span data-stu-id="ac526-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="ac526-118">如需詳細資訊，請參閱[其他常見的建置選項](#other-common-build-options)。</span><span class="sxs-lookup"><span data-stu-id="ac526-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="ac526-119">版本</span><span class="sxs-lookup"><span data-stu-id="ac526-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="ac526-120">使用 `VersionPrefix` 和 `VersionSuffix` 屬性：</span><span class="sxs-lookup"><span data-stu-id="ac526-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="ac526-121">您也可以使用 `Version` 屬性，但此屬性可能會在封裝期間覆寫版本設定：</span><span class="sxs-lookup"><span data-stu-id="ac526-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="ac526-122">其他常見的根層級選項</span><span class="sxs-lookup"><span data-stu-id="ac526-122">Other common root-level options</span></span>

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a><span data-ttu-id="ac526-123">frameworks</span><span class="sxs-lookup"><span data-stu-id="ac526-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="ac526-124">一個目標架構</span><span class="sxs-lookup"><span data-stu-id="ac526-124">One target framework</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a><span data-ttu-id="ac526-125">多個目標架構</span><span class="sxs-lookup"><span data-stu-id="ac526-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="ac526-126">使用 `TargetFrameworks` 屬性，定義您的目標架構清單。</span><span class="sxs-lookup"><span data-stu-id="ac526-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="ac526-127">使用分號來分隔多個架構值。</span><span class="sxs-lookup"><span data-stu-id="ac526-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="ac526-128">相依性</span><span class="sxs-lookup"><span data-stu-id="ac526-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac526-129">如果相依性是**專案**而不是套件，則格式會不同。</span><span class="sxs-lookup"><span data-stu-id="ac526-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="ac526-130">如需詳細資訊，請參閱[相依性類型](#dependency-type)一節。</span><span class="sxs-lookup"><span data-stu-id="ac526-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="ac526-131">NETStandard.Library 中繼套件</span><span class="sxs-lookup"><span data-stu-id="ac526-131">NETStandard.Library metapackage</span></span>

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="ac526-132">Microsoft.NETCore.App 中繼套件</span><span class="sxs-lookup"><span data-stu-id="ac526-132">Microsoft.NETCore.App metapackage</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

<span data-ttu-id="ac526-133">請注意，移轉專案中的 `<RuntimeFrameworkVersion>` 值取決於您已安裝的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="ac526-133">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="ac526-134">最上層相依性</span><span class="sxs-lookup"><span data-stu-id="ac526-134">Top-level dependencies</span></span>

```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a><span data-ttu-id="ac526-135">每個架構相依性</span><span class="sxs-lookup"><span data-stu-id="ac526-135">Per-framework dependencies</span></span>

```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a><span data-ttu-id="ac526-136">匯入</span><span class="sxs-lookup"><span data-stu-id="ac526-136">imports</span></span>

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a><span data-ttu-id="ac526-137">相依性類型</span><span class="sxs-lookup"><span data-stu-id="ac526-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="ac526-138">類型︰專案</span><span class="sxs-lookup"><span data-stu-id="ac526-138">type: project</span></span>

```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="ac526-139">這會破壞 `dotnet pack --version-suffix $suffix` 判斷專案參考之相依性版本的方式。</span><span class="sxs-lookup"><span data-stu-id="ac526-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="ac526-140">類型︰組建</span><span class="sxs-lookup"><span data-stu-id="ac526-140">type: build</span></span>

```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a><span data-ttu-id="ac526-141">類型：平台</span><span class="sxs-lookup"><span data-stu-id="ac526-141">type: platform</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

<span data-ttu-id="ac526-142">此設定在 csproj 中沒有對應項。</span><span class="sxs-lookup"><span data-stu-id="ac526-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="ac526-143">runtimes</span><span class="sxs-lookup"><span data-stu-id="ac526-143">runtimes</span></span>

```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="ac526-144">獨立應用程式 (獨立性部署)</span><span class="sxs-lookup"><span data-stu-id="ac526-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="ac526-145">在 project.json 中，定義 `runtimes` 區段表示應用程式在建置和發行期間是獨立的。</span><span class="sxs-lookup"><span data-stu-id="ac526-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="ac526-146">在 MSBuild 中，所有專案在建置期間都是「可攜式」，但可發行為獨立專案。</span><span class="sxs-lookup"><span data-stu-id="ac526-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="ac526-147">如需詳細資訊，請參閱[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd)。</span><span class="sxs-lookup"><span data-stu-id="ac526-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span>

## <a name="tools"></a><span data-ttu-id="ac526-148">tools</span><span class="sxs-lookup"><span data-stu-id="ac526-148">tools</span></span>

```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="ac526-149">在 csproj 中不支援對工具進行 `imports`。</span><span class="sxs-lookup"><span data-stu-id="ac526-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="ac526-150">需要 imports 的工具將無法搭配新的 `Microsoft.NET.Sdk` 使用。</span><span class="sxs-lookup"><span data-stu-id="ac526-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="ac526-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="ac526-151">buildOptions</span></span>

<span data-ttu-id="ac526-152">另請參閱[檔案](#files)。</span><span class="sxs-lookup"><span data-stu-id="ac526-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="ac526-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="ac526-153">emitEntryPoint</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="ac526-154">如果 `emitEntryPoint` 為 `false`，則 `OutputType` 的值會轉換成預設值 `Library`：</span><span class="sxs-lookup"><span data-stu-id="ac526-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a><span data-ttu-id="ac526-155">keyFile</span><span class="sxs-lookup"><span data-stu-id="ac526-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="ac526-156">`keyFile` 項目在 MSBuild 中已擴充成三個屬性：</span><span class="sxs-lookup"><span data-stu-id="ac526-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="ac526-157">其他常見的建置選項</span><span class="sxs-lookup"><span data-stu-id="ac526-157">Other common build options</span></span>

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a><span data-ttu-id="ac526-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="ac526-158">packOptions</span></span>

<span data-ttu-id="ac526-159">另請參閱[檔案](#files)。</span><span class="sxs-lookup"><span data-stu-id="ac526-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="ac526-160">常見的封裝選項</span><span class="sxs-lookup"><span data-stu-id="ac526-160">Common pack options</span></span>

```json
{
  "packOptions": {
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

<span data-ttu-id="ac526-161">MSBuild 中的 `owners` 項目沒有對應項。</span><span class="sxs-lookup"><span data-stu-id="ac526-161">There is no equivalent for the `owners` element in MSBuild.</span></span>
<span data-ttu-id="ac526-162">對於 `summary`，您可以使用 MSBuild `<Description>` 屬性，即使 `summary` 的值不會自動移轉至該屬性亦然，因為該屬性會對應至 [`description`](#other-common-root-level-options) 項目。</span><span class="sxs-lookup"><span data-stu-id="ac526-162">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="ac526-163">指令碼</span><span class="sxs-lookup"><span data-stu-id="ac526-163">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="ac526-164">其在 MSBuild 中的對應項是 [targets](/visualstudio/msbuild/msbuild-targets)：</span><span class="sxs-lookup"><span data-stu-id="ac526-164">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="ac526-165">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="ac526-165">runtimeOptions</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

<span data-ttu-id="ac526-166">除了 "System.GC.Server" 屬性，此群組中的所有其他設定都會放置在專案資料夾中名為 *runtimeconfig.template.json* 的檔案，其選項會在移轉程序期間上移至根物件：</span><span class="sxs-lookup"><span data-stu-id="ac526-166">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

<span data-ttu-id="ac526-167">"System.GC.Server" 屬性會移轉至 csproj 檔案：</span><span class="sxs-lookup"><span data-stu-id="ac526-167">The "System.GC.Server" property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="ac526-168">不過，您可以在 csproj as 中設定上述所有值及 MSBuild 屬性：</span><span class="sxs-lookup"><span data-stu-id="ac526-168">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="ac526-169">共用</span><span class="sxs-lookup"><span data-stu-id="ac526-169">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="ac526-170">在 csproj 中不支援。</span><span class="sxs-lookup"><span data-stu-id="ac526-170">Not supported in csproj.</span></span> <span data-ttu-id="ac526-171">您必須改為在 *.nuspec* 檔案中建立包含內容檔。</span><span class="sxs-lookup"><span data-stu-id="ac526-171">You must instead create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="ac526-172">如需詳細資訊，請參閱[包含內容檔](/nuget/schema/nuspec#including-content-files)。</span><span class="sxs-lookup"><span data-stu-id="ac526-172">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="ac526-173">個檔案</span><span class="sxs-lookup"><span data-stu-id="ac526-173">files</span></span>

<span data-ttu-id="ac526-174">在 *project.json* 中，可擴充組建和套件以從其他資料夾進行編譯和內嵌。</span><span class="sxs-lookup"><span data-stu-id="ac526-174">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="ac526-175">在 MSBuild 中，這會使用[目](/visualstudio/msbuild/common-msbuild-project-items)來完成。</span><span class="sxs-lookup"><span data-stu-id="ac526-175">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="ac526-176">以下是常見慣例範例：</span><span class="sxs-lookup"><span data-stu-id="ac526-176">The following example is a common conversion:</span></span>

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="ac526-177">.NET Core SDK 會自動新增許多預設 [Glob 模式](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="ac526-177">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="ac526-178">如需詳細資訊，請參閱 [Default Compile Item Values](https://aka.ms/sdkimplicititems) (預設編譯項目值)。</span><span class="sxs-lookup"><span data-stu-id="ac526-178">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="ac526-179">所有 MSBuild `ItemGroup` 項目都支援 `Include`、`Exclude` 和 `Remove`。</span><span class="sxs-lookup"><span data-stu-id="ac526-179">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="ac526-180">您可以使用 `PackagePath="path"` 修改 .nupkg 內的套件配置。</span><span class="sxs-lookup"><span data-stu-id="ac526-180">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="ac526-181">除了 `Content`，大多數項目群組都需要明確地新增 `Pack="true"`，以包含在套件中。</span><span class="sxs-lookup"><span data-stu-id="ac526-181">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="ac526-182">因為 MSBuild `<IncludeContentInPack>` 屬性預設會設定為 `true`，所以會將 `Content` 放在套件的 *content* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ac526-182">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="ac526-183">如需詳細資訊，請參閱 [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package) (在套件中包含內容)。</span><span class="sxs-lookup"><span data-stu-id="ac526-183">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="ac526-184">`PackagePath="%(Identity)"` 是將套件路徑設定為專案相關檔案路徑的捷徑。</span><span class="sxs-lookup"><span data-stu-id="ac526-184">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="ac526-185">testRunner</span><span class="sxs-lookup"><span data-stu-id="ac526-185">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="ac526-186">xUnit</span><span class="sxs-lookup"><span data-stu-id="ac526-186">xUnit</span></span>

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a><span data-ttu-id="ac526-187">MSTest</span><span class="sxs-lookup"><span data-stu-id="ac526-187">MSTest</span></span>

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="ac526-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac526-188">See Also</span></span>

* [<span data-ttu-id="ac526-189">CLI 中變更的高階概觀</span><span class="sxs-lookup"><span data-stu-id="ac526-189">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
