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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>MSBuild 屬性為 .NET 核心 SDK 專案

本頁介紹用於配置 .NET Core 專案的 MSBuild 屬性。

> [!NOTE]
> 此頁正在進行中，不會列出 .NET Core SDK 的所有有用的 MSBuild 屬性。 有關常見 MSBuild 屬性的清單，請參閱[常見 MSBuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。

## <a name="framework-properties"></a>框架屬性

- [目標框架](#targetframework)
- [目標框架](#targetframeworks)
- [淨標準隱式包版本](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>目標框架

該`TargetFramework`屬性指定應用的目標框架版本，該版本隱式引用[元包](../packages.md#metapackages)。 有關有效目標框架名字物件的清單，請參閱 SDK[樣式專案中的目標框架](../../standard/frameworks.md#supported-target-framework-versions)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

有關詳細資訊，請參閱[SDK 樣式專案中的目標框架](../../standard/frameworks.md)。

### <a name="targetframeworks"></a>目標框架

當您希望`TargetFrameworks`應用以多個平臺為目標時，請使用 該屬性。 有關有效目標框架名字物件的清單，請參閱 SDK[樣式專案中的目標框架](../../standard/frameworks.md#supported-target-framework-versions)。

> [!NOTE]
> 如果`TargetFramework`指定了（單數），則忽略此屬性。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

有關詳細資訊，請參閱[SDK 樣式專案中的目標框架](../../standard/frameworks.md)。

### <a name="netstandardimplicitpackageversion"></a>淨標準隱式包版本

> [!NOTE]
> 此屬性僅適用于使用`netstandard1.x`的專案。 它不適用於使用`netstandard2.x`的專案。

如果要指定`NetStandardImplicitPackageVersion`低於[元包](../packages.md#metapackages)版本的框架版本，請使用 該屬性。 以下示例中的專案檔案以目標為目標`netstandard1.3`，但使用`NETStandard.Library`的 1.6.0 版本。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>發佈屬性

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [使用應用主機](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

屬性`RuntimeIdentifier`允許您為專案指定單個[運行時識別碼 （RID）。](../rid-catalog.md) RID 允許發佈獨立式部署。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

該`RuntimeIdentifiers`屬性允許您為專案指定[運行時識別碼 （DD）](../rid-catalog.md)的分號分隔清單。 如果需要為多個運行時發佈，請使用此屬性。 `RuntimeIdentifiers`在還原時使用，以確保正確的資產在圖形中。

> [!TIP]
> `RuntimeIdentifier`（單數）在只需要單個運行時時，可以提供更快的生成。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>使用應用主機

該`UseAppHost`屬性在 .NET Core SDK 的 2.1.400 版本中引入。 它控制是否為部署創建本機可執行檔。 自包含部署需要本機可執行檔。

在 .NET Core 3.0 和更高版本中，預設情況下將創建與框架相關的可執行檔。 將`UseAppHost`屬性設置為`false`禁用可執行檔的生成。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

有關部署的詳細資訊，請參閱[.NET 核心應用程式部署](../deploying/index.md)。

## <a name="compile-properties"></a>編譯屬性

### <a name="langversion"></a>朗吉

屬性`LangVersion`允許您指定特定的程式設計語言版本。 例如，如果要訪問 C# 預覽功能，則設置為`LangVersion``preview`。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

有關詳細資訊，請參閱[C# 語言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。

## <a name="nuget-packages"></a>NuGet 套件

- [PackageReference](#packagereference)
- [資產目標回退](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

該專案`PackageReference`允許您指定 NuGet 依賴項。 例如，您可能希望引用單個包而不是[元包](../packages.md#metapackages)。 `Include` 屬性會指定套件識別碼。 以下示例中的專案檔案程式碼片段引用[System.Runtime](https://www.nuget.org/packages/System.Runtime/)包。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

有關詳細資訊，請參閱[專案檔案中的包引用](/nuget/consume-packages/package-references-in-project-files)。

### <a name="assettargetfallback"></a>資產目標回退

該`AssetTargetFallback`屬性允許您為專案引用的專案和專案使用的 NuGet 包指定其他相容的框架版本。 例如，如果使用指定包依賴項，`PackageReference`但該包不包含與專案的相容的資產`TargetFramework`，則`AssetTargetFallback`屬性將發揮作用。 使用 中`AssetTargetFallback`指定的每個目標框架重新檢查引用包的相容性。

您可以將該`AssetTargetFallback`屬性設置為一個或多個[目標框架版本](../../standard/frameworks.md#supported-target-framework-versions)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>打包和復原目標

MSBuild 15.1 `pack` `restore`引入了創建和還原 NuGet 包作為構建的一部分的目標。 有關這些目標的 MSBuild 屬性的資訊，請參閱`PackageTargetFallback` [NuGet 打包並還原為 MSBuild 目標](/nuget/reference/msbuild-targets)。

## <a name="see-also"></a>另請參閱

- [MSBuild 架構引用](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [常見 MSBuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)
- [用於 NuGet 包的 MS 構建屬性](/nuget/reference/msbuild-targets#pack-target)
- [用於 NuGet 還原的 MSBuild 屬性](/nuget/reference/msbuild-targets#restore-properties)
- [自訂生成](/visualstudio/msbuild/customize-your-build)
