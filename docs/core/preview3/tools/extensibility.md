---
title: ".NET Core CLI 擴充性模型 | Microsoft Docs"
description: ".NET Core CLI 擴充性模型"
keywords: "CLI, 擴充性, 自訂命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 02/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
translationtype: Human Translation
ms.sourcegitcommit: 5a1ba8984d93795e4628a7b911307d513e8de8d1
ms.openlocfilehash: 1b6bc46639fda60e4a23c1ea66d0d0ca8b58acb7

---

# <a name="net-core-cli-extensibility-model-net-core-tools-rc4"></a>.NET Core CLI 擴充性模型 (.NET Core 工具 RC4)

> [!WARNING]
> 本主題適用於 .NET Core 工具 RC4。 .NET Core 工具 Preview 2 版本，請參閱 [.NET Core CLI 擴充性模型](../../tools/dotnet-test.md)主題。

## <a name="overview"></a>概觀
本文件將涵蓋如何擴充 CLI 工具的主要方法，並說明驅動所有項目的案例。 它將會概述如何使用這些工具，以及提供如何建置這兩種工具的簡短附註。 

## <a name="how-to-extend-cli-tools"></a>如何擴充 CLI 工具
RC4 CLI 工具可以三種主要方式擴充：

1. 透過個別專案的 NuGet 套件
2. 透過具有自訂目標的 NuGet 套件  
3. 透過系統的 PATH

上述三種擴充機制並不互斥；您可以全部使用、使用其中一個，或者混合使用。 選擇哪一個主要取決於您嘗試使用擴充功能達成的目標。

## <a name="per-project-based-extensibility"></a>個別專案擴充性
每個專案的工具都是以 NuGet 套件形式散發的[架構相依部署](../deploying/index.md)。 工具僅適用於參考它們以及還原它們的專案內容；因為將會找不到命令，所以專案內容外部的叫用 (例如，包含專案的目錄外部) 會失敗。

這些工具非常適合做為組建伺服器，因為不需要專案檔以外的任何項目。 建置流程會執行所建置專案的還原，並且可以使用這些工具。 語言專案 (例如 F#) 也在這個分類中；畢竟，每個專案都只能以一種特定語言撰寫。 

最後，這個擴充性模型支援建立存取專案的已建置輸出所需的工具。 例如，[ASP.NET](https://www.asp.net/) MVC 應用程式中的各種 Razor 檢視工具都會落入這個分類。 

### <a name="consuming-per-project-tools"></a>使用個別專案工具
使用這些工具，需要您針對希望用在專案檔的各個工具新增 `<DotNetCliToolReference>` 元素。 在 `<DotNetCliToolReference>` 元素內部，您會參考工具所在的套件，並指定您需要的版本。 執行 `dotnet restore` 之後，會還原工具和其相依性。 

針對需要載入專案建置輸出來執行的工具，通常在專案檔中的一般相依性下方會列出另一個相依性。 因為 CLI 的 RC4 版本使用 MSBuild 作為其建置引擎，建議您將工具的這些部分撰寫為自訂的 MSBuild 目標與工作，如此一來它們就可以參與整體的建置程序。 此外，它們可以輕鬆取得透過建置所產生的任何與全部資料，例如輸出檔的位置、目前正在建置的設定等。RC4 中的此資訊全部會變成一組可從任何目標讀取的 MSBuild 屬性。 我們稍後會在此文件中說明如何使用 NuGet 新增自訂目標。 

讓我們檢閱在簡單專案中新增僅限簡單工具的工具的範例。 假設有一個稱為 `dotnet-api-search` 的範例命令可讓您搜尋 NuGet 套件以尋找指定的 API，則以下是使用該工具的主控台應用程式專案檔：


```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1/TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` 元素會以類似於 `<PackageReference>` 元素的方式結構化。 它需要最少包含工具和其版本的套件的套件識別項。 

### <a name="building-tools"></a>建置工具
如前所述，工具只是可攜式主控台應用程式。 在建置任何主控台應用程式時會建立一個。 在您建立它之後，將使用 [`dotnet pack`](dotnet-pack.md) 命令來建立包含您程式碼、其相依性相關資訊等的 NuGet 套件 (nupkg)。 套件名稱可以是作者想要的任何名稱，但在應用程式內，實際工具二進位檔必須符合 `dotnet-<command>` 的慣例，`dotnet` 才能叫用它。 

> [!NOTE]
> 在 RC3 之前版本的 .NET Core 命令列工具中，`dotnet pack` 命令中的 Bug 導致無法使用該工具來將 `runtime.config.json` 封裝。 缺少該檔案會導致在執行階段發生錯誤。 如果您遇到這個問題，請務必更新至最新的工具，並再次嘗試 `dotnet pack`。 

因為工具是可攜式應用程式，所以使用工具的使用者必須具有用來建置工具的 .NET Core 程式庫版本，才能執行工具。 工具所使用以及 .NET Core 程式庫內未包含的任何其他相依性都會進行還原並放到 NuGet 快取中。 因此，會使用 .NET Core 程式庫中的組件以及 NuGet 快取中的組件來執行整個工具。 

這類工具的相依性圖形必須與使用這些工具之專案的相依性圖形完全分開。 還原程序會先還原專案的相依性，接著還原每個工具和其相依性。 

您可以在 [.NET Core CLI 存放庫](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestProjects)中找到更多範例和這類不同的組合。 您也可以在相同的存放庫中查看[所使用工具的實作](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages)。 

### <a name="custom-targets"></a>自訂目標
NuGet 現在已具備封裝自訂 MSBuild 目標和 props 檔案的功能，您可以在 [NuGet 文件網站](https://docs.microsoft.com/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package)上找到相關的官方文件。 隨著在 CLI 中改為使用 MSBuild，相同的擴充機制也適用於 .NET Core 專案。 當您想要擴充建置程序或者想要在建置程序中存取任何構件 (例如產生的檔案或檢查呼叫建置的組態等)，您可以使用這種類型的擴充性。 

下面包含範例目標的專案檔，以供參考。 它示範如何使用新的 `csproj` 語法來指示 `dotnet pack` 命令要封裝的項目，以將目標檔案以及組件放入套件內的 `build` 資料夾。 請記錄下面將 `Label` 屬性設定為「dotnet 組件指示」的 `<ItemGroup>`。 

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
    <Content Include="build\*.targets;$(OutputPath)\*.dll;$(OutputPath)\*.json">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
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

使用自訂目標取決於您的設定方式。 因為它是一般的 MSBuild 目標，它可以依存在給定的目標上、在另一個目標之後執行，也可以使用 `dotnet msbuild /t:<target-name>` 命令手動叫用。 

不過，如果您希望為您的使用者提供更好的使用者體驗，您可以結合每個專案工具和自訂目標。 在此案例中，每個專案工具基本上會只接受任何需要的參數，且會將參數轉譯為將執行目標的必要 `dotnet msbuild` 引動過程。 您可以在 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 專案中的 [MVP Summit 2016 Hackathon 範例](https://github.com/dotnet/MVPSummitHackathon2016)儲存機制，查看此類協同作用範例。 

### <a name="path-based-extensibility"></a>PATH 擴充性
PATH 擴充性通常用於開發電腦，而在開發電腦中，您需要有概念上涵蓋多個單一專案的工具。 這個擴充功能機制的主要缺點是繫結至工具所在的電腦。 如果您需要在另一部電腦上使用它，則必須部署它。

這種模式的 CLI 工具組擴充性十分簡單。 如 [.NET Core CLI 概觀](index.md)中所涵蓋，`dotnet` 驅動程式可以執行任何在 `dotnet-<command>` 慣例後面命名的命令。 預設解析邏輯會先探查數個位置，最後再轉到系統 PATH。 如果要求的命令存在於系統 PATH 中，而且是可叫用的二進位檔，`dotnet` 驅動程式將會叫用它。 

二進位檔幾乎是作業系統可以執行的任何項目。 在 Unix 系統上，這表示任何透過 `chmod +x` 設定執行位元的項目。 在 Windows 上，這表示 Windows 知道如何執行的任何項目。 

例如，讓我們查看十分簡單的 `dotnet clean` 命令實作。 我們將使用 `bash` 來實作這個命令。 這個命令只會刪除目前目錄中的 `bin/` 和 `obj/` 目錄。 如果將 `--lock` 引數傳遞給它，則也會刪除 `project.lock.json` 檔案。 這個命令的全部內容如下。 

```bash
#!/bin/bash

# Delete the bin and obj dirs
rm -rf bin/ obj/

LOCK_FILE=$1
if [[ "$LOCK_FILE" = "--lock" ]]; then
    rm project.lock.json
fi


echo "Cleaning complete..."
```

在 macOS 上，我們可以將這個指令碼儲存為 `dotnet-clean`，並使用 `chmod +x dotnet-clean` 設定其可執行位元。 我們接著可以使用 `ln -s dotnet-clean /usr/local/bin/` 命令，以在 `/usr/local/bin` 中建立其符號連結。 這可能會使用 `dotnet clean` 語法來叫用 clean 命令。 測試方式是建立應用程式，並在其上執行 `dotnet build`，然後執行 `dotnet clean`。 

## <a name="conclusion"></a>結論
.NET Core CLI 工具允許三個主要擴充點。 個別專案工具都包含在專案內容內，但允許透過還原輕鬆地進行安裝。 自訂目標可讓您輕鬆地透過自訂工作擴充建置程序。 PATH 工具適用於可在單一電腦上使用的一般跨專案工具。 




<!--HONumber=Feb17_HO2-->


