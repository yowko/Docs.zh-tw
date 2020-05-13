---
title: .NET Core 專案 SDK 總覽
titleSuffix: ''
description: 深入瞭解 .NET Core 專案 Sdk。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 88ec1bf2c4917c69b80b997d090219097694d2bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206052"
---
# <a name="net-core-project-sdks"></a>.NET Core 專案 Sdk

.NET Core 專案與軟體發展工具組（SDK）相關聯。 每個*專案 SDK*都是一組 MSBuild[目標](/visualstudio/msbuild/msbuild-targets)和相關聯的工作，負責編譯、封裝和[發行程式碼](/visualstudio/msbuild/msbuild-tasks)。 參考專案 SDK 的專案有時也稱為「 *SDK 樣式專案*」。

## <a name="available-sdks"></a>可用的 Sdk

下列 Sdk 適用于 .NET Core：

| 識別碼 | 描述 | 存放庫|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET Core SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | .NET Core [WEB SDK](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | .NET Core [RAZOR SDK](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET Core 背景工作角色服務 SDK |
| `Microsoft.NET.Sdk.WindowsDesktop` | .NET Core WinForms 和 WPF SDK |

.NET Core SDK 是適用于 .NET Core 的基底 SDK。 其他 Sdk 會參考 .NET Core SDK，而與其他 Sdk 相關聯的專案則具有所有可用的 .NET Core SDK 屬性。 例如，Web SDK 取決於 .NET Core SDK 和 Razor SDK。

您也可以撰寫自己的 SDK，以透過 NuGet 散發。

## <a name="project-files"></a>專案檔

.NET Core 專案是以[MSBuild](/visualstudio/msbuild/msbuild)格式為基礎。 專案檔，其副檔名如 *.csproj* （適用于 c # 專案）和 *.fsproj* （適用于 F # 專案）都是 XML 格式。 MSBuild 專案檔的根項目是[專案](/visualstudio/msbuild/project-element-msbuild)元素。 `Project`元素具有選擇性 `Sdk` 屬性，可指定要使用的 SDK （和版本）。 若要使用 .NET Core 工具並建立您的程式碼，請將 `Sdk` 屬性設定為[可用 sdk](#available-sdks)資料表中的其中一個識別碼。

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

以下列其中一種方式參考 SDK，可大幅簡化 .NET Core 的專案檔案。 評估專案時，MSBuild 會 `Sdk.props` 在專案檔的頂端和底部新增隱含的匯入 `Sdk.targets` 。

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
> 在 Windows 電腦上，您可以在 *%ProgramFiles%\dotnet\sdk \\ [version] \Sdks\Microsoft.NET.Sdk\Sdk*資料夾中找到 *.props*和*sdk .targets*檔案。

### <a name="preprocess-the-project-file"></a>前置處理專案檔

您可以看到在 SDK 之後，MSBuild 會看到完全展開的專案，而其目標則是使用命令所包含 `dotnet msbuild -preprocess` 。 命令[preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)的前置處理參數 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 會顯示哪些檔案已匯入、其來源，以及它們對組建的貢獻，而不需要實際建立專案。

如果專案有多個目標架構，請將命令的結果指定為 MSBuild 屬性，只將其焦點放在一個架構上。 例如：

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>預設編譯包括

在 SDK 中定義了編譯專案、內嵌資源和專案的預設值 [包含] 和 [排除] `None` 。 不同于非 SDK .NET Framework 專案，您不需要在專案檔中指定這些專案，因為預設值會涵蓋最常見的使用案例。 這可讓專案檔變得更小且更容易瞭解，並視需要手動進行編輯。

下表顯示 .NET Core SDK 中包含和排除哪些元素和哪些[glob](https://en.wikipedia.org/wiki/Glob_(programming)) ：

| 元素           | 包含 Glob                              | 排除 Glob                                                  | 移除 Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| 編譯           | \*\*/\*.cs (或其他語言副檔名) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | 不適用                      |
| 內嵌資源  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | 不適用                      |
| 無              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs、\*\*/\*.resx |

> [!NOTE]
> 和 `./bin` `./obj` MSBuild 屬性所表示的和資料夾 `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` 預設會從 glob 中排除。 排除會以屬性工作表示 `$(DefaultItemExcludes)` 。

#### <a name="build-errors"></a>建置錯誤

如果您在專案檔中明確定義這些專案，您可能會收到類似下列的「NETSDK1022」組建錯誤：

  > 包含重複的 ' Compile ' 專案。 根據預設，.NET SDK 會包含專案目錄中的「編譯」專案。 您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。

  > 包含重複的 ' EmbeddedResource ' 專案。 根據預設，.NET SDK 會在您的專案目錄中包含 ' EmbeddedResource ' 專案。 您可以從專案檔中移除這些專案，或者，如果您想要在專案檔中明確包含 ' EnableDefaultEmbeddedResourceItems ' 屬性，請將其設定為 ' false '。

若要解決錯誤，請執行下列其中一項動作：

- 移除 `Compile` `EmbeddedResource` `None` 符合上表所列隱含專案的明確、或專案。

- 將 `EnableDefaultItems` 屬性設定為 `false` ，以停用所有隱含檔案包含：

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  如果您想要指定要與您的應用程式一起發佈的檔案，您仍然可以針對該專案使用已知的 MSBuild 機制，例如 `Content` 元素。

- 藉 `Compile` `EmbeddedResource` `None` 由將 `EnableDefaultCompileItems` 、 `EnableDefaultEmbeddedResourceItems` 或 `EnableDefaultNoneItems` 屬性設定為 `false` ，選擇性地停用、或 glob：

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  如果您只停 `Compile` 用 glob，Visual Studio 中的方案總管仍會 \* 將 .cs 專案顯示為專案的一部分，包括做為 `None` 專案。 若要停用隱含 `None` glob，請將設 `EnableDefaultNoneItems` 為 `false` 。

## <a name="customize-the-build"></a>自訂群組建

有各種方式可[自訂群組建](/visualstudio/msbuild/customize-your-build)。 您可能想要覆寫屬性，方法是將它當做引數傳遞給[msbuild](/visualstudio/msbuild/msbuild-command-line-reference)或[dotnet](../tools/index.md)命令。 您也可以將屬性加入至專案檔或 *.props*檔案。 如需 .NET Core 專案的實用屬性清單，請參閱[.NET Core SDK 專案的 MSBuild 參考](msbuild-props.md)。

### <a name="custom-targets"></a>自訂目標

.NET Core 專案可以封裝自訂的 MSBuild 目標和屬性，以供取用套件的專案使用。 當您想要執行下列動作時，請使用這類型的擴充性：

- 擴充組建進程。
- 存取組建進程的構件，例如產生的檔案。
- 檢查用來叫用組建的設定。

您可以新增自訂群組建目標或屬性，方法是將檔案放在 `<package_id>.targets` `<package_id>.props` `Contoso.Utility.UsefulStuff.targets` 專案的 [*組建*] 資料夾中，或將檔案（例如，）放置在此。

下列 XML 是來自 *.csproj*檔案的程式碼片段，可指示 [`dotnet pack`](../tools/dotnet-pack.md) 命令要封裝的內容。 元素會將 `<ItemGroup Label="dotnet pack instructions">` 目標檔案放入封裝內的*build*資料夾中。 元素會將 `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 元件和*json*檔案放入*build*資料夾中。

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

若要使用專案中的自訂目標，請加入 `PackageReference` 指向封裝及其版本的元素。 與工具不同的是，自訂目標封裝會包含在取用專案的相依性結束項中。

您可以設定如何使用自訂目標。 由於它是 MSBuild 目標，它可以相依于指定的目標，在另一個目標之後執行，或使用命令以手動方式叫用 `dotnet msbuild -t:<target-name>` 。 不過，為了提供更好的使用者體驗，您可以結合每個專案工具和自訂目標。 在此案例中，每個專案工具會接受所需的任何參數，並將它轉譯成 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 執行目標的必要調用。 您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。

## <a name="see-also"></a>請參閱

- [安裝 .NET Core](../install/index.md)
- [如何使用 MSBuild 專案 Sdk](/visualstudio/msbuild/how-to-use-project-sdk)
- [使用 NuGet 封裝自訂 MSBuild 目標和 .props](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
