---
title: 適用于 .NET 的 MSBuild 屬性
description: .NET Core SDK 所瞭解之 MSBuild 屬性的參考。
ms.date: 02/02/2020
ms.topic: reference
ms.openlocfilehash: f5dc2079bc313b8dd9fa5556cd941521a597ae38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453808"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>.NET Core SDK 專案的 MSBuild 屬性

此頁面描述用於設定 .NET Core 專案的 MSBuild 屬性。

> [!NOTE]
> 此頁面為進行中的工作，且不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。 如需一般 MSBuild 屬性的清單，請參閱[一般 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。

## <a name="framework-properties"></a>架構屬性

- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)
- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> 此屬性僅適用于使用 `netstandard1.x`的專案。 它不適用於使用 `netstandard2` 和更新版本的專案。

當您想要指定低於[中繼套件](../packages.md#metapackages)版本的 framework 版本時，請使用 `NetStandardImplicitPackageVersion` 屬性。 下列範例中的專案檔是以 `netstandard1.3` 為目標，但使用 `NETStandard.Library`的1.6.0 版本。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

### <a name="targetframework"></a>TargetFramework

`TargetFramework` 屬性會指定應用程式的目標 framework 版本，其會隱含地參考[中繼套件](../packages.md#metapackages)。 如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。

### <a name="targetframeworks"></a>TargetFrameworks

當您想要讓應用程式以多個平臺為目標時，請使用 `TargetFrameworks` 屬性。 如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。

> [!NOTE]
> 如果指定 `TargetFramework` （單數），則會忽略這個屬性。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。

## <a name="publish-properties"></a>發佈屬性

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`RuntimeIdentifier` 屬性可讓您指定專案的單一[執行時間識別碼（RID）](../rid-catalog.md) 。 RID 允許發佈獨立式部署。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`RuntimeIdentifiers` 屬性可讓您指定專案的[執行時間識別碼（rid）清單（](../rid-catalog.md)以分號分隔）。 如果您需要針對多個執行時間發行，請使用這個屬性。 `RuntimeIdentifiers` 會在還原時使用，以確保正確的資產在圖形中。

> [!TIP]
> 當只需要單一執行時間時，`RuntimeIdentifier` （單數）可以提供更快速的組建。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` 屬性是在 .NET Core SDK 的2.1.400 版本中引進。 它會控制是否針對部署建立原生可執行檔。 獨立部署需要原生可執行檔。

在 .NET Core 3.0 和更新版本中，預設會建立與 framework 相依的可執行檔。 將 [`UseAppHost`] 屬性設定為 [`false`]，以停用可執行檔的產生。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

如需部署的詳細資訊，請參閱[.Net Core 應用程式部署](../deploying/index.md)。

## <a name="compile-properties"></a>編譯屬性

### <a name="langversion"></a>LangVersion

`LangVersion` 屬性可讓您指定特定的程式設計語言版本。 例如，如果您想要存取C#預覽功能，請將 `LangVersion` 設定為 `preview`。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

如需詳細資訊，請參閱[ C#語言版本](../../csharp/language-reference/configure-language-version.md#override-a-default)設定。

## <a name="nuget-packages"></a>NuGet 套件

- [PackageReference](#packagereference)

### <a name="packagereference"></a>PackageReference

`PackageReference` 專案可讓您指定 NuGet 相依性。 例如，您可能想要參考單一封裝，而不是[中繼套件](../packages.md#metapackages)。 `Include` 屬性會指定套件識別碼。 下列範例中的專案檔程式碼片段會參考[system.webserver](https://www.nuget.org/packages/System.Runtime/)封裝。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

如需詳細資訊，請參閱[專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。

### <a name="pack-and-restore-targets"></a>套件和還原目標

MSBuild 15.1 引進了 `pack` 和 `restore` 目標，可在組建中建立和還原 NuGet 套件。 如需這些目標之 MSBuild 屬性的相關資訊，包括 `PackageTargetFallback`，請參閱[NuGet 套件和還原為 MSBuild 目標](/nuget/reference/msbuild-targets)。

## <a name="see-also"></a>另請參閱

- [MSBuild 架構參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [一般 MSBuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet 套件的 MSBuild 屬性](/nuget/reference/msbuild-targets#pack-target)
- [NuGet 還原的 MSBuild 屬性](/nuget/reference/msbuild-targets#restore-properties)
- [自訂群組建](/visualstudio/msbuild/customize-your-build)
