---
title: 將 WPF 應用程式移植到 .NET Core 3.0
description: 教導您如何將 .NET Framework Windows Presentation Foundation 應用程式移植到適用於 Windows 的 .NET Core 3.0。
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 4ff3ca9610e7fa9355931ca2013def1157fab8b2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216193"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>作法：將 WPF 傳統型應用程式移植到 .NET Core

本文說明如何將 Windows Presentation Foundation (WPF) 傳統型應用程式從 .NET Framework 移植到 .NET Core 3.0。 .NET Core 3.0 SDK 支援 WPF 應用程式。 WPF 仍然是僅限 Windows 的架構，只能在 Windows 上執行。 本範例使用 .NET Core SDK CLI 來建立和管理您的專案。

在此文章中，各種不同的名稱會用來識別用於移轉的檔案類型。 在移轉您的專案時，您的檔案會有不同的名稱，因此請在心裡將它們與下面所列的項目進行比對：

| 檔案 | 描述 |
| ---- | ----------- |
| **MyApps.sln** | 方案檔的名稱。 |
| **MyWPF.csproj** | 要移植的 .NET Framework WPF 專案的名稱。 |
| **MyWPFCore.csproj** | 您所建立的新 .NET Core 專案的名稱。 |
| **MyAppCore.exe** | .NET Core WPF 應用程式可執行檔。 |

>[!IMPORTANT]
>雖然本文使用 C# 作為目標語言，相同的步驟仍然適用於 VB.NET，唯一的不同在於 VB.NET 使用 *.vbproj* 和 *.vb* 檔案，而非 *.csproj* 和 *.cs* 檔案。

## <a name="prerequisites"></a>必要條件

- 適用於您想要執行之任何設計工具工作的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 。

  安裝下列 Visual Studio 工作負載：
  - .NET 桌面開發
  - .NET 跨平台開發

- 在解決方案中運作的 WPF 專案，可以毫無問題地建置並執行。
- 安裝最新的 [.NET Core 3.0](https://aka.ms/netcore3download) 預覽。

>[!NOTE]
>**Visual Studio 2017** 不支援 .NET Core 3.0 專案。 **Visual Studio 2019** 支援 .NET Core 3.0 專案，但針對 .NET Core WPF 視覺化設計工具僅具有有限的支援。 若要使用完整受到支援的視覺化設計工具，您在您的解決方案中必須擁有 .NET Framework WPF 專案，且該專案必須和 .NET Core 專案共用其檔案。

### <a name="consider"></a>Consider

移植 .NET Framework WPF 應用程式時，您必須考量幾件事。

01. 請檢查您的應用程式是否適合移轉。

    使用 [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) 確定您的專案是否將移轉至 .NET Core 3.0。 如果您的專案有.NET Core 3.0 的問題，則分析器可協助您找出這些問題。

01. 您正在使用不同版本的 WPF。

    當 .NET Core 3.0 Preview 1 發行時，WPF 會在 GitHub 上進入開放原始碼。 .NET Core WPF 的程式碼是 .NET Framework WPF 程式碼基底的分支。 很可能存在一些差異，而您的應用程式將無法移植。

01. [Windows 相容性套件][compat-pack]可能可以協助您進行遷移。

    .NET Core 3.0 中不提供 .NET Framework 中提供的某些 API。 [Windows 相容性套件][compat-pack]新增了許多 API，並且可能可以協助您的 WPF 應用程式，使其與 .NET Core 相容。

01. 更新專案所使用的 NuGet 套件。

    在任何移轉之前使用最新版本的 NuGet 套件永遠是最好的作法。 如果您的應用程式會參考任何 NuGet 套件，請將它們更新為最新版本。 請確定您的應用程式建置成功。 升級後，如果有任何套件錯誤，請將套件降級為不會中斷程式碼的最新版本。

01. Visual Studio 2019 尚不支援 .NET Core 3.0 的 WPF 設計工具

    目前，如果要使用 Visual Studio 中的 WPF 設計工具，則需要保留現有的 .NET Framework WPF 專案檔案。

## <a name="create-a-new-sdk-project"></a>建立新的 SDK 專案

您所建立的新 .NET Core 3.0 專案必須與 .NET Framework 專案位於不同的目錄中。 如果它們都在相同的目錄中，則可能會與 **obj** 目錄中產生的檔案發生衝突。 在此範例中，您將在 **SolutionFolder** 目錄中建立名為 **MyWPFAppCore** 的目錄：

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

接下來，您需要在 **MyWPFAppCore** 目錄中建立 **MyWPFCore.csproj** 專案。 您可以使用選擇的文字編輯器以手動方式建立此檔案。 貼上下列 XML：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

如果您不想以手動方式建立專案檔案，則您可以使用 Visual Studio 或 .NET Core SDK 產生專案。 但是，您必須刪除專案範本所產生的所有其他檔案，專案檔除外。 若要使用 SDK，請從 **SolutionFolder** 目錄執行下列命令：

```dotnetcli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

建立 **MyWPFCore.csproj** 後，您的目錄結構應該如下所示：

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

您需要使用 Visual Studio 或 **SolutionFolder** 目錄中的 .NET Core CLI，將 **MyWPFCore.csproj** 專案新增到 **MyApps.sln**：

```dotnetcli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>修正組件資訊產生

使用 .NET Framework 所建立的 Windows Presentation Foundation 專案包含 `AssemblyInfo.cs` 檔案，該檔案包含組件屬性，例如要產生的組件版本。 SDK 樣式專案會根據 SDK 專案檔自動為您產生此資訊。 同時具有兩種類型的「組件資訊」會發生衝突。 藉由停用自動產生來解決此問題，這會強制專案使用現有的 `AssemblyInfo.cs` 檔案。

加入至主要 `<PropertyGroup>` 節點有三個設定。 

- **GenerateAssemblyInfo**\
當您將此屬性設定為 `false`，它就不會產生組件屬性。 這可以避免與 .NET Framework 專案中的現有 `AssemblyInfo.cs` 檔案衝突。

- **AssemblyName**\
這個屬性的值是您在編譯時所建立的二進位輸出。 該名稱不需要加入副檔名。 例如，使用 `MyCoreApp` 產生 `MyCoreApp.exe`。

- **RootNamespace**\
專案使用的預設命名空間。 這應該與 .NET Framework 專案的預設命名空間相符。

將這三個元素新增至 `MyWPFCore.csproj` 檔案中的 `<PropertyGroup>` 節點：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>加入原始程式碼
現在，**MyWPFCore.csproj** 專案不會進行編譯任何程式碼。 根據預設，.NET Core 專案會自動包含目前目錄和任何子目錄中的所有原始程式碼。 您必須使用相對路徑，將專案設定為包含 .NET Framework 專案中的程式碼。 如果您的 .NET Framework 專案使用 **.resx** 檔案作為視窗和控制項的圖示和資源，那麼您還需要包含這些檔案。 

第一個新增至專案所需的 `<ItemGroup>` 節點包含代表應用程式使用之啟動組態和資源 **App.xaml** 檔案。 **App.xaml** 檔案也隨附一個 **App.xaml.cs**檔案，但它會自動包含在不同的 `<ItemGroup>` 中。

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

接著，將下列 `<ItemGroup>` 節點新增至您的專案。 每個陳述式都包含一個檔案 Glob 模式，其中包含子目錄。 它包含您專案的原始程式碼、任何設定檔案和任何資源。 **Obj** 目錄會遭到明確排除。

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

接下來，包括另一個 `<ItemGroup>` 節點，其中專案中的每個 **xaml** 檔案都含有一個 `<Page>` 項目，但 **App.xaml** 檔案除外。 這些包含所有 **xaml** 格式的視窗、頁面和資源。 您無法在這裡使用 glob 模式，而且必須針對每個檔案新增一個項目，並指出使用了 `<Generator>`。

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>新增 NuGet 套件

將 .NET Framework 專案參考的每個 NuGet 套件新增至 .NET Core 專案。 

很可能您的 .NET Framework WPF 應用程式有一個 **packages.config** 檔案，其中包含您的專案所參考的 NuGet 套件的清單。 您可以查看這份清單以判斷要新增至 .NET Core 專案的 NuGet 套件。 例如，如果 .NET Framework 專案參考 `MahApps.Metro` NuGet 封裝，則使用 Visual Studio 將其新增至專案。 您也可以使用 .NET Core CLI，從 **SolutionFolder** 目錄新增封裝參考：

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

上述命令會將下列 NuGet 參考新增到 **MyWPFCore.csproj** 專案中：

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>編譯的問題

如果您在編譯專案時遇到問題，則您可能正在使用 .NET Framework 中提供但不適用於 .NET Core 的一些僅限 Windows 的 API。 您可以嘗試將 [Windows 相容性套件][compat-pack] NuGet 套件新增到您的專案。 此套件只能在 Windows 上執行，並為 .NET Core 和 .NET Standard 專案新增了大約 20,000 個 Windows API。

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

上一個命令會將下列內容新增到 **MyWPFCore.csproj** 專案：

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>WPF 設計工具

如此文章所述，Visual Studio 2019 僅支援 .NET Framework 專案中的 WPF 設計工具。 藉由建立並排.NET Core 專案，您可以在使用 .NET Framework 專案設計表單時，同時使用 .NET Core 測試您的專案。 您的方案檔包含 .NET Framework 和 .NET Core 專案。 在 .NET Framework 專案中新增和設計您的表單和控制項，且根據我們新增至 .NET Core 專案的檔案 Glob 模式，任何新的或已變更的檔案將自動包含在 .NET Core 專案中。

一旦 Visual Studio 2019 支援 WPF Form 設計工具，您就可以將 .NET Core 專案檔案的內容複製/貼上到 .NET Framework 專案檔案中。 然後刪除新增了 `<Source>` 和 `<EmbeddedResource>` 項目的檔案 Glob 模式。 修正應用程式所使用之任何專案參考的路徑。 這會有效地將 .NET Framework 專案升級至 .NET Core 專案。

## <a name="next-steps"></a>後續步驟

- 深入了解 [Windows 相容性套件][compat-pack]。
- 觀看[有關移植](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) .NET Framework WPF 專案到 .NET Core 的影片。

[compat-pack]: windows-compat-pack.md
