---
title: .NET 專案 SDK 總覽
titleSuffix: ''
description: 瞭解 .NET 專案 Sdk。
ms.date: 09/17/2020
ms.topic: conceptual
ms.openlocfilehash: 6b6651f674f09d5d0d18ddb873096037ad3b2ba5
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247565"
---
# <a name="net-project-sdks"></a>.NET 專案 Sdk

.NET Core 和 .NET 5.0 和更新版本的專案與軟體發展工具組 (SDK) 相關聯。 每個 *專案 SDK* 都是一組 MSBuild [目標](/visualstudio/msbuild/msbuild-targets) 和 [相關聯的工作](/visualstudio/msbuild/msbuild-tasks) ，負責編譯、封裝和發佈程式碼。 參考專案 SDK 的專案有時稱為 *SDK 樣式專案*。

## <a name="available-sdks"></a>可用的 Sdk

以下是可用的 Sdk：

| ID | 描述 | 存放庫|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET SDK | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | .NET [WEB SDK](/aspnet/core/razor-pages/web-sdk) | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | .NET [RAZOR SDK](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET Worker 服務 SDK |
| `Microsoft.NET.Sdk.WindowsDesktop` | WinForms 和 WPF SDK\* | <https://github.com/dotnet/winforms> 和 <https://github.com/dotnet/wpf> |

.NET SDK 是適用于 .NET 的基底 SDK。 其他 Sdk 參考 .NET SDK，而與其他 Sdk 相關聯的專案則具有所有可用的 .NET SDK 屬性。 例如，Web SDK 取決於 .NET SDK 和 Razor SDK。

您也可以撰寫可透過 NuGet 散發的您自己的 SDK。

\* 從 .NET 5.0 開始，Windows Forms 和 Windows Presentation Foundation (WPF) 專案應指定 .NET SDK (`Microsoft.NET.Sdk`) 而不是 `Microsoft.NET.Sdk.WindowsDesktop` 。 針對這些專案，將設定 `TargetFramework` 為 `net5.0-windows` 和或， `UseWPF` `UseWindowsForms` `true` 將會自動匯入 Windows 桌面 SDK。 如果您的專案是以 .NET 5.0 或更新版本為目標並指定 `Microsoft.NET.Sdk.WindowsDesktop` SDK，您將會收到組建警告 NETSDK1137。

## <a name="project-files"></a>專案檔

.NET 專案是以 [MSBuild](/visualstudio/msbuild/msbuild) 格式為基礎。 具有適用于 c # 專案的 *.csproj* 和適用于 F # 專案之 *>.fsproj* 的專案檔為 XML 格式。 MSBuild 專案檔的根項目是 [專案](/visualstudio/msbuild/project-element-msbuild) 元素。 `Project`元素具有選擇性 `Sdk` 屬性，可指定要使用的 SDK (和版本) 。 若要使用 .NET 工具並建立您的程式碼，請將 `Sdk` 屬性設定為 [可用 sdk](#available-sdks) 資料表中的其中一個識別碼。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

若要指定來自 NuGet 的 SDK，請在名稱的結尾包含版本，或在檔案的 *global.js* 中指定名稱和版本。

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

指定 SDK 的另一種方式是使用最上層 [sdk](/visualstudio/msbuild/sdk-element-msbuild) 元素：

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

使用其中一種方式來參考 SDK，可大幅簡化 .NET 的專案檔。 評估專案時，MSBuild 會在專案檔的 `Sdk.props` 頂端和底部加入隱含的匯入 `Sdk.targets` 。

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

您可以看到完全展開的專案，因為 MSBuild 會在 SDK 之後看到它，並使用命令來包含其目標 `dotnet msbuild -preprocess` 。 命令的前置 [處理參數](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) 會顯示要匯入的檔案 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 、其來源，以及其對組建的貢獻，而不會實際建立專案。

如果專案有多個目標架構，請將命令的結果指定為 MSBuild 屬性，以只將命令的結果放在一個架構上。 例如：

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>預設編譯包含

編譯專案、內嵌資源和專案的預設包含和排除 `None` 會定義在 SDK 中。 不同于非 SDK .NET Framework 專案，您不需要在專案檔中指定這些專案，因為預設值涵蓋最常見的使用案例。 如果需要的話，這會讓專案檔更小且更容易瞭解並手動編輯。

下表顯示 .NET SDK 中包含和排除哪些元素和哪些 [glob](https://en.wikipedia.org/wiki/Glob_(programming)) ：

| 項目           | 包含 Glob                              | 排除 Glob                                                  | 移除 Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| 編譯           | \*\*/\*.cs (或其他語言副檔名) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | N/A                      |
| 內嵌資源  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/A                      |
| 無              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs、\*\*/\*.resx |

> [!NOTE]
> 和 `./bin` `./obj` MSBuild 屬性代表的和資料夾， `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` 預設會從 glob 中排除。 排除會以屬性工作表示 `$(DefaultItemExcludes)` 。

#### <a name="build-errors"></a>建置錯誤

如果您在專案檔中明確定義任何這些專案，您可能會收到類似下列的「NETSDK1022」組建錯誤：

  > 包含重複的 ' Compile ' 專案。 .NET SDK 預設會在您的專案目錄中包含 [編譯] 專案。 您可以從專案檔中移除這些項目；如果您想要在專案檔中明確包含這些項目，您可以將 'EnableDefaultCompileItems' 屬性設定為 'false'。

  > 包含重複的 ' EmbeddedResource ' 專案。 .NET SDK 預設會在您的專案目錄中包含 ' EmbeddedResource ' 專案。 您可以從專案檔中移除這些專案，或將 ' EnableDefaultEmbeddedResourceItems ' 屬性設定為 ' false '，如果您想要將它們明確包含在專案檔中。

若要解決錯誤，請執行下列其中一項動作：

- 移除符合上 `Compile` `EmbeddedResource` 表所 `None` 列之隱含專案的明確、或專案。

- 將 `EnableDefaultItems` 屬性設為， `false` 以停用所有隱含檔案包含：

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  如果您想要指定要與應用程式一起發行的檔案，您仍然可以針對該專案使用已知的 MSBuild 機制，例如 `Content` 元素。

- 藉 `Compile` `EmbeddedResource` `None` 由將 `EnableDefaultCompileItems` 、 `EnableDefaultEmbeddedResourceItems` 或 `EnableDefaultNoneItems` 屬性設定為 `false` ，選擇性地停用、或 glob：

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  如果您只停 `Compile` 用 glob，方案總管在 Visual Studio 仍會 \* 將 .cs 專案顯示為專案的一部分，包含為 `None` 專案。 若要停用隱含 `None` glob，請將設定 `EnableDefaultNoneItems` 為 `false` 。

## <a name="customize-the-build"></a>自訂群組建

[自訂群組建](/visualstudio/msbuild/customize-your-build)的方式有很多種。 您可以藉由將屬性做為引數傳遞至 [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) 或 [dotnet](../tools/index.md) 命令，來覆寫該屬性。 您也可以將屬性加入至專案檔或 *.props* 檔案。 如需 .NET 專案的實用屬性清單，請參閱 [.NET SDK 專案的 MSBuild 參考](msbuild-props.md)。

### <a name="custom-targets"></a>自訂目標

.NET 專案可以封裝自訂 MSBuild 目標和屬性，以供取用封裝的專案使用。 當您想要執行下列動作時，請使用這類型的擴充性：

- 擴充組建流程。
- 存取組建進程的構件，例如產生的檔案。
- 檢查用來叫用組建的設定。

您可以藉由將檔案放入表單或 (來新增自訂群組建目標或屬性 `<package_id>.targets` `<package_id>.props` ，例如， `Contoso.Utility.UsefulStuff.targets` 在專案的 [ *組建* ] 資料夾中) 。

下列 XML 是來自 *.csproj* 檔案的程式碼片段，指示 [`dotnet pack`](../tools/dotnet-pack.md) 命令要封裝的內容。 元素會將 `<ItemGroup Label="dotnet pack instructions">` 目標檔案放入封裝內的 *組建* 資料夾中。 元素會將 `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 元件和 *json* 檔案放入 *組建* 資料夾。

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

若要在專案中使用自訂目標，請新增 `PackageReference` 指向封裝及其版本的專案。 與工具不同的是，自訂目標套件包含在取用專案的相依性關閉中。

您可以設定如何使用自訂目標。 因為它是 MSBuild 目標，所以它可以相依于指定的目標、在另一個目標之後執行，或使用命令手動叫用 `dotnet msbuild -t:<target-name>` 。 不過，若要提供更好的使用者體驗，您可以結合每個專案工具和自訂目標。 在此案例中，每個專案工具會接受任何需要的參數，並將其轉譯為執行目標所需的 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 調用。 您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。

## <a name="see-also"></a>另請參閱

- [安裝 .NET Core](../install/index.yml)
- [如何使用 MSBuild 專案 Sdk](/visualstudio/msbuild/how-to-use-project-sdk)
- [使用 NuGet 封裝自訂 MSBuild 目標和 .props](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
