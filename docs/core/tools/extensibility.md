---
title: ".NET Core CLI 擴充性模型"
description: "了解如何擴充命令列介面 (CLI) 工具。"
keywords: "CLI, 擴充性, 自訂命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
ms.translationtype: HT
ms.sourcegitcommit: 434b27f6c2d44c63b4ce4deee094ac6c322cf2b5
ms.openlocfilehash: 62de584fe5d7f1029e73e4c8c5f9b428c567751a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---

# <a name="net-core-cli-tools-extensibility-model"></a>.NET Core CLI 工具擴充性模型

本文件涵蓋不同的方式可擴充 .NET Core 命令列介面 (CLI) 工具，並說明可驅動其中所有項目的案例。
您會看到如何使用這些工具，以及如何建置不同類型的工具。

## <a name="how-to-extend-cli-tools"></a>如何擴充 CLI 工具
CLI 工具可以透過三種主要方式進行擴充：

1. [透過個別專案的 NuGet 套件](#per-project-based-extensibility)

  個別專案工具都包含在專案內容內，但允許透過還原輕鬆地進行安裝。

2. [透過具有自訂目標的 NuGet 套件](#custom-targets)

  自訂目標可讓您輕鬆地透過自訂工作擴充建置程序。

3. [透過系統的 PATH](#path-based-extensibility)

  PATH 工具適用於可在單一電腦上使用的一般跨專案工具。

上述這三種擴充性機制都不是專用的。 您可以使用其中一個、全部或其組合。 選擇哪一個主要取決於您嘗試使用延伸模組達成的目標。

## <a name="per-project-based-extensibility"></a>個別專案擴充性
個別專案工具是以 NuGet 套件形式散發的[架構相依部署](../deploying/index.md#framework-dependent-deployments-fdd)。 工具只可用於參考它們以及還原它們之專案的內容中。 因為找不到命令，所以專案內容外部 (例如，包含專案的目錄外部) 的引動過程會失敗。

這些工具非常適合做為組建伺服器，因為不需要專案檔以外的任何項目。 建置流程會執行所建置專案的還原，並且可以使用這些工具。 因為每個專案都只能以一種特定語言撰寫，所以語言專案 (例如 F#) 也在這個分類中。

最後，這個擴充性模型支援建立存取專案的已建置輸出所需的工具。 例如，[ASP.NET](https://www.asp.net/) MVC 應用程式中的各種 Razor 檢視工具都會落入這個分類。

### <a name="consuming-per-project-tools"></a>使用個別專案工具
使用這些工具，需要您針對要使用的每個工具在專案檔中新增 `<DotNetCliToolReference>` 項目。 在 `<DotNetCliToolReference>` 項目內部，您會參考工具所在的套件，並指定您需要的版本。 執行 [`dotnet restore`](dotnet-restore.md) 之後，會還原工具和其相依性。

針對需要載入專案建置輸出來執行的工具，通常在專案檔中的一般相依性下方會列出另一個相依性。 因為 CLI 使用 MSBuild 作為其建置引擎，所以建議您將工具的這些部分撰寫為自訂 MSBuild [目標](/visualstudio/msbuild/msbuild-targets)及[工作](/visualstudio/msbuild/msbuild-tasks)，這樣它們就可以參與整體建置程序。 此外，它們可以輕鬆取得透過建置所產生的任何與全部資料，例如輸出檔的位置、目前正在建置的組態等。這項資訊全部會變成一組可從任何目標讀取的 MSBuild 屬性。 您稍後會在此文件中看到如何使用 NuGet 新增自訂目標。

讓我們檢閱在簡單專案中新增僅限簡單工具的工具的範例。 假設有一個稱為 `dotnet-api-search` 的範例命令可讓您搜尋 NuGet 套件以尋找指定的 API，則以下是使用該工具的主控台應用程式專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` 元素會以類似於 `<PackageReference>` 元素的方式結構化。 它需要包含可還原之工具及其版本之套件的套件識別碼。

### <a name="building-tools"></a>建置工具
如前所述，工具只是可攜式主控台應用程式。 建置工具的方式與建置任何其他主控台應用程式一樣。
在您建置它之後，請使用 [`dotnet pack`](dotnet-pack.md) 命令來建立包含您程式碼、其相依性相關資訊等的 NuGet 套件 (.nupkg 檔案)。 您可以提供任何套件名稱，但在應用程式內，實際工具二進位檔必須符合 `dotnet-<command>` 的慣例，`dotnet` 才能叫用它。

> [!NOTE]
> 在 RC3 之前版本的 .NET Core 命令列工具中，`dotnet pack` 命令中的 Bug 導致無法使用該工具來將 `runtime.config.json` 封裝。 缺少該檔案會導致在執行階段發生錯誤。 如果您遇到這個問題，請務必更新至最新的工具，並再次嘗試 `dotnet pack`。

因為工具是可攜式應用程式，所以使用工具的使用者必須具有用來建置工具的 .NET Core 程式庫版本，才能執行工具。 工具所使用以及 .NET Core 程式庫內未包含的任何其他相依性都會進行還原並放到 NuGet 快取中。 因此，會使用 .NET Core 程式庫中的組件以及 NuGet 快取中的組件來執行整個工具。

這類工具的相依性圖形必須與使用這些工具之專案的相依性圖形完全分開。 還原程序會先還原專案的相依性，接著還原每個工具及其相依性。

您可以在 [.NET Core CLI 存放庫](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestProjects)中找到更多範例和這類不同的組合。
您也可以在相同的存放庫中查看[所使用工具的實作](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestPackages)。

### <a name="custom-targets"></a>自訂目標
NuGet 可以[封裝自訂 MSBuild 目標及屬性檔案](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package)。 隨著 .NET Core CLI 改為使用 MSBuild，相同的擴充機制現在也適用於 .NET Core 專案。 如果您想要擴充建置程序，或想要在建置程序中存取任何成品 (例如產生的檔案或檢查叫用建置的組態等)，可以使用這種類型的擴充性。

在下列範例中，您可以使用 `csproj` 語法看到目標的專案檔。 這會指示 [`dotnet pack`](dotnet-pack.md) 命令要封裝的內容，並將目標檔案及組件放入套件內的 *build* 資料夾。 請注意，`<ItemGroup>` 項目的 `Label` 屬性設定為 `dotnet pack instructions`，並具有其下定義的 [目標]。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
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
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

取用自訂目標的方式是提供 `<PackageReference>`，它必須指向套件以及其在要擴充之專案中的版本。 與其他工具不同，自訂目標套件會被包含到取用自訂目標之專案的相依性閉包 (Closure) 中。

使用自訂目標取決於您的設定方式。 因為它是 MSBuild 目標，所以可以依存在給定的目標上、在另一個目標之後執行，也可以使用 `dotnet msbuild /t:<target-name>` 命令手動叫用。

不過，如果您要為使用者提供更好的使用者體驗，則可以結合個別專案工具和自訂目標。 在此案例中，個別專案工具基本上會只接受任何需要的參數，且會將參數轉譯為將執行目標的必要 [`dotnet msbuild`](dotnet-msbuild.md) 引動過程。 您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。

### <a name="path-based-extensibility"></a>PATH 擴充性
PATH 擴充性通常用於開發電腦，而在開發電腦中，您需要有概念上涵蓋多個單一專案的工具。 這個延伸模組機制的主要缺點是繫結至工具所在的電腦。 如果您需要在另一部電腦上使用它，則必須部署它。

這種模式的 CLI 工具組擴充性十分簡單。 如 [.NET Core CLI 概觀](index.md)中所涵蓋，`dotnet` 驅動程式可以執行任何在 `dotnet-<command>` 慣例後面命名的命令。 預設解析邏輯會先探查數個位置，最後回復到系統路徑。 如果要求的命令存在於系統 PATH 中，而且是可叫用的二進位檔，`dotnet` 驅動程式將會叫用它。

檔案必須是可執行檔。 在 Unix 系統上，這表示任何透過 `chmod +x` 設定執行位元的項目。 在 Windows 中，您可以使用 *cmd* 檔案。

讓我們查看十分簡單的 "Hello World" 工具的實作。 我們將在 Windows 上使用 `bash` 及 `cmd`。
下列命令只會將 "Hello World" 回應到主控台。

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

在 macOS 上，我們可以將這個指令碼儲存為 `dotnet-hello`，並使用 `chmod +x dotnet-hello` 設定其可執行位元。 我們接著可以使用 `ln -s <full_path>/dotnet-hello /usr/local/bin/` 命令，以在 `/usr/local/bin` 中建立其符號連結。 這可能會使用 `dotnet hello` 語法來叫用此命令。

在 Windows 中，可以將這個指令碼儲存為 `dotnet-hello.cmd`，並將它放在系統路徑中的位置 (也可以將它新增至已在路徑中的資料夾)。 在此之後，您只要使用 `dotnet hello`，就能執行這個範例。

