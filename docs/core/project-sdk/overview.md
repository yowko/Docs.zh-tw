---
title: .NET 核心專案 SDK 概述
description: 瞭解 .NET 核心專案 SDK。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399172"
---
# <a name="net-core-project-sdks"></a>.NET 核心專案 SDK

.NET 核心專案與軟體發展工具組 （SDK） 相關聯。 每個專案 SDK 是一組 MSBuild[目標](/visualstudio/msbuild/msbuild-targets)和相關[任務](/visualstudio/msbuild/msbuild-tasks)，負責編譯、打包和發佈代碼。

## <a name="available-sdks"></a>可用 SDK

以下 SDK 可用於 .NET 核心：

| ID | 描述 | 回購|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET 核心 SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | .NET 核心[Web SDK](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | .NET 核心[剃刀 SDK](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET 核心工作人員服務 SDK |
| `Microsoft.NET.Sdk.WindowsDesktop` | .NET 核心贏形和 WPF SDK |

.NET 核心 SDK 是 .NET 核心的基本 SDK。 其他 SDK 引用 .NET 核心 SDK，與其他 SDK 關聯的專案具有所有可用的 .NET Core SDK 屬性。 例如，Web SDK 取決於 .NET 核心 SDK 和 Razor SDK。

您還可以創作自己的 SDK，這些 SDK 可通過 NuGet 進行分發。

## <a name="project-files"></a>專案檔

.NET 核心專案基於[MSBuild](/visualstudio/msbuild/msbuild)格式。 專案檔案具有像 C# 專案的 *.csproj*和*F# 專案的 .fsproj*這樣的副檔名，它們採用 XML 格式。 MSBuild 專案檔案的根項目是[專案](/visualstudio/msbuild/project-element-msbuild)元素。 該`Project`元素具有一個`Sdk`可選屬性，用於指定要使用的 SDK（和版本）。 要使用 .NET Core 工具並生成代碼，請`Sdk`將屬性設置為[可用 SDK](#available-sdks)表中的其中一個 ID。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

要指定來自 NuGet 的 SDK，請在名稱末尾包括版本，或在*global.json*檔中指定名稱和版本。

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

指定 SDK 的另一種方法是使用頂級[SDK](/visualstudio/msbuild/sdk-element-msbuild)元素：

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

以以下方式之一引用 SDK 大大簡化了 .NET Core 的專案檔案。 在評估專案時，MSBuild 在專案檔案的頂部`Sdk.props`和`Sdk.targets`底部添加了隱式導入。

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> 在 Windows 電腦上 *，Sdk.props*和*Sdk.target*檔可以在 *%程式檔%_dotnet_sdk\\[版本]Sdks_Microsoft.NET.Sdk_Sdk*資料夾中找到。

### <a name="preprocess-the-project-file"></a>預處理專案檔案

在 SDK 及其目標包含在 SDK 之後，您可以看到完全擴展的專案，使用`dotnet msbuild -preprocess`命令包括該專案。 命令[preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)的預[`dotnet msbuild`](../tools/dotnet-msbuild.md)處理開關顯示導入的檔、其源及其對生成的貢獻，而無需實際生成專案。

如果專案有多個目標框架，則將命令的結果僅將其指定為 MSBuild 屬性，將命令的結果集中在一個框架上。 例如：

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>預設編譯包括

編譯項的預設值包括和排除，嵌入資源在 SDK 中定義。 與非 SDK .NET 框架專案不同，您不需要在專案檔案中指定這些專案，因為預設值涵蓋最常見的用例。 這將導致較小的專案檔案，更容易理解，以及手動編輯，如果需要的話。

下表顯示了 .NET 核心 SDK 中包括和排除哪些元素和哪些[globs：](https://en.wikipedia.org/wiki/Glob_(programming))

| 元素           | 包含 Glob                              | 排除 Glob                                                  | 移除 Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| 編譯           | \*\*/\*.cs (或其他語言副檔名) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | N/A                      |
| 內嵌資源  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs、\*\*/\*.resx |

> [!NOTE]
> 預設情況下`./bin`，`./obj`由`$(BaseOutputPath)`和`$(BaseIntermediateOutputPath)`MSBuild 屬性工作表示 的 和 資料夾從 globs 中排除。 排除由 屬性`$(DefaultItemExcludes)`表示。

如果在專案檔案中顯式定義這些專案，則可能會收到以下錯誤：

**包括重複編譯項。預設情況下，.NET SDK 包括專案目錄中的編譯項。如果要在專案檔案中顯式包含這些專案，可以從專案檔案中刪除這些專案，也可以將"啟用預設編譯專案"屬性設置為"false"。**

要解決錯誤，請刪除與上表中`Compile`列出的隱式項匹配的顯式項，或將`EnableDefaultCompileItems`屬性設置為`false`，該屬性將禁用隱式包含：

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

例如，如果要指定某些要隨應用發佈的檔，您仍可以使用已知的 MSBuild 機制，例如`Content`元素。

`EnableDefaultCompileItems`僅禁用`Compile`globs，但不會影響其他 globs，如也適用于`None`\*.cs 項的隱式 glob。 因此，視覺化工作室中的解決方案資源管理器將 .cs 項作為專案的一部分進行，\*作為`None`專案包含在內。 要禁用隱式`None`glob，`EnableDefaultNoneItems`請`false`設置為 ：

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

要禁用*所有*隱式 globs，`EnableDefaultItems`請將`false`屬性設置為 ：

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>自訂生成

有各種方法來[自訂生成](/visualstudio/msbuild/customize-your-build)。 您可能希望通過將屬性作為參數傳遞給[msbuild](/visualstudio/msbuild/msbuild-command-line-reference)或[dotnet](../tools/index.md)命令來覆蓋該屬性。 您還可以將屬性添加到專案檔案或*目錄.Build.props 檔*。 有關 .NET Core 專案的有用屬性清單，請參閱[.NET Core SDK 專案的 MSBuild 屬性](msbuild-props.md)。

### <a name="custom-targets"></a>自訂目標

.NET Core 專案可以打包自訂 MSBuild 目標和屬性，供使用包的專案使用。 當您想要：

- 擴展生成過程。
- 訪問生成過程的專案，如生成的檔。
- 檢查調用生成的配置。

通過將`<package_id>.targets`檔放在表單中或`<package_id>.props`（例如）`Contoso.Utility.UsefulStuff.targets`在專案的*生成*資料夾中來添加自訂生成目標或屬性。

以下 XML 是 *.csproj*檔中的一個片段，[`dotnet pack`](../tools/dotnet-pack.md)用於指示命令打包什麼。 元素`<ItemGroup Label="dotnet pack instructions">`將目的檔案放入包內的*生成*資料夾中。 該`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`元素將程式集和 *.json*檔放入*生成*資料夾中。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

要在專案中使用自訂目標，請添加指向`PackageReference`包及其版本的元素。 與工具不同，自訂目標包包含在使用項的依賴項關閉中。

您可以配置如何使用自訂目標。 由於它是 MSBuild 目標，它可以依賴于給定的目標、在另一個目標之後運行，或者使用 命令`dotnet msbuild -t:<target-name>`手動調用。 但是，為了提供更好的使用者體驗，您可以合併每個專案工具和自訂目標。 在這種情況下，每個專案工具接受所需的任何參數，並將其轉換為執行目標所需的[`dotnet msbuild`](../tools/dotnet-msbuild.md)調用。 您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。

## <a name="see-also"></a>另請參閱

- [安裝 .NET Core](../install/index.md)
- [如何使用 MSBuild 專案 SDK](/visualstudio/msbuild/how-to-use-project-sdk)
- [使用 NuGet 打包自訂 MSBuild 目標和道具](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
