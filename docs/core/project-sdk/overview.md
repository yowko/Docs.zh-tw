---
title: .NET Core 專案 SDK 總覽
description: 深入瞭解 .NET Core 專案 Sdk。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: c41b25bf7933e7b1f6cb50da5e52dc0b312f5c74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626246"
---
# <a name="net-core-project-sdks"></a>.NET Core 專案 Sdk

.NET Core 專案與軟體發展工具組（SDK）相關聯。 每個專案 SDK 都是一組 MSBuild[目標](/visualstudio/msbuild/msbuild-targets)和[相關聯](/visualstudio/msbuild/msbuild-tasks)的工作，負責編譯、封裝和發行程式碼。

## <a name="available-sdks"></a>可用的 Sdk

下列 Sdk 適用于 .NET Core：

| ID | 描述 | 存放庫|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET Core SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | .NET Core [WEB SDK](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | .NET Core [RAZOR SDK](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET Core 背景工作角色服務 SDK |
| `Microsoft.NET.Sdk.WindowsDesktop` | .NET Core WinForms 和 WPF SDK |

.NET Core SDK 是適用于 .NET Core 的基底 SDK。 其他 Sdk 會參考 .NET Core SDK，而與其他 Sdk 相關聯的專案則具有所有可用的 .NET Core SDK 屬性。 例如，Web SDK 取決於 .NET Core SDK 和 Razor SDK。

您也可以撰寫自己的 SDK，以透過 NuGet 散發。

## <a name="project-files"></a>專案檔

.NET Core 專案是以[MSBuild](/visualstudio/msbuild/msbuild)格式為基礎。 專案檔，其副檔名如 *.csproj*適用于C#專案，而 *.fsproj*用於F#專案，則為 XML 格式。 MSBuild 專案檔的根項目是[專案](/visualstudio/msbuild/project-element-msbuild)元素。 `Project` 元素具有選擇性的 `Sdk` 屬性，可指定要使用的 SDK （和版本）。 若要使用 .NET Core 工具並建立您的程式碼，請將 `Sdk` 屬性設定為[可用 sdk](#available-sdks)資料表中的其中一個識別碼。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

若要指定來自 NuGet 的 SDK，請在名稱結尾包含版本，或指定*global.asax*檔案中的名稱和版本。

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

另一個指定 SDK 的方法是使用最上層[SDK](/visualstudio/msbuild/sdk-element-msbuild)元素：

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

以下列其中一種方式參考 SDK，可大幅簡化 .NET Core 的專案檔案。 評估專案時，MSBuild 會在專案檔頂端新增 `Sdk.props` 的隱含匯入，並在底部 `Sdk.targets`。

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
> 在 Windows 電腦上，您可以在 *%ProgramFiles%\dotnet\sdk\\[version] \Sdks\Microsoft.NET.Sdk\Sdk*資料夾中找到 *.props*和*sdk .targets*檔案。

### <a name="preprocess-the-project-file"></a>前置處理專案檔

在 SDK 之後，您可以看到完全展開的專案，而它的目標是使用 `dotnet msbuild -preprocess` 命令所包含。 [`dotnet msbuild`](../tools/dotnet-msbuild.md)命令的前置[處理參數會](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)顯示哪些檔案已匯入、其來源，以及其對組建的貢獻，而不需要實際建立專案。

如果專案有多個目標架構，請將命令的結果指定為 MSBuild 屬性，只將其焦點放在一個架構上。 例如：

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>預設編譯包括

編譯專案的預設 [包含] 和 [排除]，以及在 SDK 中定義的內嵌資源。 不同于非 SDK .NET Framework 專案，您不需要在專案檔中指定這些專案，因為預設值會涵蓋最常見的使用案例。 這會導致較小的專案檔，而且更容易瞭解，並視需要手動編輯。

下表顯示 .NET Core SDK 中包含和排除的元素和哪些[glob](https://en.wikipedia.org/wiki/Glob_(programming)) ：

| 元素           | 包含 Glob                              | 排除 Glob                                                  | 移除 Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| 編譯           | \*\*/\*.cs (或其他語言副檔名) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | N/A                      |
| 內嵌資源  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs、\*\*/\*.resx |

> [!NOTE]
> [`./bin`] 和 [`./obj`] 資料夾（由 `$(BaseOutputPath)` 和 `$(BaseIntermediateOutputPath)` MSBuild 屬性工作表示）預設會從 glob 中排除。 [排除] 是以屬性 `$(DefaultItemExcludes)`表示。

如果您在專案檔中明確定義這些專案，您可能會收到下列錯誤：

**包含重複的編譯專案。根據預設，.NET SDK 會包含專案目錄中的編譯專案。您可以從專案檔中移除這些專案，或者，如果您想要在專案檔中明確包含 ' EnableDefaultCompileItems ' 屬性，請將其設定為 ' false '。**

若要解決此錯誤，請移除符合上表所列隱含專案的明確 `Compile` 專案，或將 `EnableDefaultCompileItems` 屬性設定為 `false`，這會停用隱含包含：

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

例如，如果您想要指定一些檔案來與您的應用程式一起發佈，您仍然可以使用已知的 MSBuild 機制，例如，`Content` 元素。

`EnableDefaultCompileItems` 只會停用 `Compile` glob，但不會影響其他 glob，例如也適用于 \*.cs 專案的隱含 `None` glob。 因此，方案總管在 Visual Studio 會將 \*.cs 專案顯示為專案的一部分，包括做為 `None` 專案。 若要停用隱含 `None` glob，請將 `EnableDefaultNoneItems` 設定為 `false`：

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

若要停用*所有*隱含 glob，請將 `EnableDefaultItems` 屬性設定為 `false`：

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>自訂群組建

有各種方式可[自訂群組建](/visualstudio/msbuild/customize-your-build)。 您可能想要覆寫屬性，方法是將它當做引數傳遞給[msbuild](/visualstudio/msbuild/msbuild-command-line-reference)或[dotnet](../tools/index.md)命令。 您也可以將屬性加入至專案檔或 *.props*檔案。 如需 .NET Core 專案的實用屬性清單，請參閱[.NET Core SDK 專案的 MSBuild 屬性](msbuild-props.md)。

## <a name="see-also"></a>另請參閱

- [安裝 .NET Core](../install/index.md)
- [如何使用 MSBuild 專案 Sdk](/visualstudio/msbuild/how-to-use-project-sdk)
