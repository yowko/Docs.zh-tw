---
title: dotnet new 的自訂範本
description: 了解任何 .NET 專案或檔案類型的自訂範本。
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 738c6b07f77bdbf6fd946253f95c8691e4172f31
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410355"
---
# <a name="custom-templates-for-dotnet-new"></a>dotnet new 的自訂範本

[.NET Core SDK](https://www.microsoft.com/net/download/core) \(英文\) 具有許多已經安裝並可供您使用的範本。 [`dotnet new` 命令](dotnet-new.md)不僅是使用範本的方式，也是安裝及解除安裝範本的方式。 從 .NET Core 2.0 開始，您可以建立任何專案類型的自訂範本，例如應用程式、服務、工具或類別庫。 您甚至可以建立會輸出一或多個獨立檔案的範本，例如組態檔。

您可以直接參考 NuGet *.nupkg* 檔案，或指定包含範本的檔案系統目錄，來從任何 NuGet 摘要上的 NuGet 套件安裝自訂的範本。 範本引擎提供可讓您取代值、包含與排除檔案，以及在範本被使用時執行自訂處理作業的功能。

範本引擎是開放原始碼，而線上程式碼存放庫位於 GitHub 的 [dotnet/templating](https://github.com/dotnet/templating/)。 如需範本範例，請瀏覽 [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) 存放庫。 GitHub 的 [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (dotnet new 的可用範本) 中，有包括協力廠商範本在內的更多範本。 如需建立與使用自訂範本的詳細資訊，請參閱[如何建立您自己的 dotnet new 範本](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)以及 [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)。

若要遵循逐步解說並建立範本，請參閱[建立 dotnet new 的自訂範本](~/docs/core/tutorials/create-custom-template.md)教學課程。

### <a name="net-default-templates"></a>.NET 預設範本

當您安裝 [.NET Core SDK](https://www.microsoft.com/net/download/core) 時，您會收到十多個用於建立專案和檔案的內建範本，包括主控台應用程式、類別庫、單元測試專案，ASP.NET Core 應用程式 (包括 [Angular](https://angular.io/) 和 [React](https://facebook.github.io/react/) 專案) 和組態檔。 若要列出內建範本，請執行搭配 `-l|--list` 選項執行 `dotnet new` 命令：

```console
dotnet new --list
```

## <a name="configuration"></a>Configuration

範本是由下列部分組成：

- 來源檔案和資料夾。
- 設定檔 (*template.json*)。

### <a name="source-files-and-folders"></a>來源檔案和資料夾

來源檔案和資料夾包含您想要範本引擎在 `dotnet new <TEMPLATE>` 命令被執行時使用的任何檔案和資料夾。 範本引擎的設計是將「可執行專案」  用為原始程式碼以產生專案。 這有幾項優點：

- 範本引擎不需要您將特殊權杖插入專案的原始程式碼。
- 程式碼檔案不是特殊的檔案，也不使用範本引擎以任何方式修改。 因此，通常在處理專案時使用的工具也用來處理範本內容。
- 您會建置、執行和偵錯範本專案，就如同您對任何其他專案一樣。
- 您可以將 *./.template.config/template.json* 設定檔新增至專案，來快速地從現有專案建立範本。

儲存在範本中的檔案和資料夾不限於正式的 .NET 專案類型。 來源檔案和資料夾可由您想要在範本被使用時建立的任何內容組成，即使範本引擎只會產生單一檔案作為其輸出。

由範本產生的檔案可以根據您在 *template.json* 設定檔中所提供的邏輯和設定進行修改。 使用者可以將選項傳遞至 `dotnet new <TEMPLATE>` 命令來覆寫這些設定。 自訂邏輯的常見範例之一，是針對由範本所部署之程式碼檔案中的類別或變數提供名稱。

### <a name="templatejson"></a>template.json

*template.json* 檔案放在範本根目錄的 *.template.config* 資料夾中。 檔案向範本引擎提供組態資訊。 最小的組態需要下表顯示的成員，這即足以建立具有功能的範本。

| 成員            | 類型          | 說明 |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | *template.json* 檔案的 JSON 結構描述。 支援 JSON 結構描述的編輯器，會在指定結構描述時，啟用 JSON 編輯功能。 例如，[Visual Studio Code](https://code.visualstudio.com/) 需要此成員才能啟用 IntelliSense。 使用 `http://json.schemastore.org/template` 的值。 |
| `author`          | 字串        | 範本的作者。 |
| `classifications` | array(string) | 搜尋範本時，使用者可能用來尋找範本的零或多個範本特性。 當它出現在使用 `dotnet new -l|--list` 命令產生的範本清單中時，分類也會出現在「標記」  資料行中。 |
| `identity`        | 字串        | 此範本的唯一名稱。 |
| `name`            | 字串        | 使用者應該會看到的範本名稱。 |
| `shortName`       | 字串        | 適用於選取要套用至環境之範本的預設速記名稱；此環境中的範本名稱是由使用者指定，而不是透過 GUI 選取。 例如，從命令提示字元以 CLI 命令使用範本時，簡短名稱很有用。 |

*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。 如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。

#### <a name="example"></a>範例

例如，這是包含下列兩個內容檔案的範本資料夾：*console.cs* 和 *readme.txt*。 請注意，有一個名為 *.template.config* 且包含 *template.json* 檔案的必要資料夾。

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

*template.json* 檔案看起來如下所示：

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

*mytemplate* 資料夾為可安裝的範本套件。 安裝套件之後，便可以搭配 `dotnet new` 命令使用 `shortName`。 例如，`dotnet new adatumconsole` 會將 `console.cs` 和 `readme.txt` 檔案輸出至目前的資料夾。

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>將範本封裝在 NuGet 套件中 (nupkg 檔案)

自訂範本會搭配 [dotnet pack](dotnet-pack.md) 命令和 *.csproj* 檔案進行封裝。 或者，[NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) \(部分機器翻譯\) 可以搭配 [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) \(部分機器翻譯\) 命令和 *.nuspec* 檔案使用。 不過，NuGet 在 Windows 上需要 .NET Framework，在 Linux 和 MacOS 上則需要 [Mono](https://www.mono-project.com/) \(英文\)。

*.csproj* 檔案與傳統的程式碼專案 *.csproj* 檔案具有些微的不同。 請注意下列設定：

01. 已加入 `<PackageType>` 設定並將其設定為 `Template`。
01. 已加入 `<PackageVersion>` 設定並將其設定為有效的 [NuGet 版本號碼](/nuget/reference/package-versioning)。
01. 已加入 `<PackageId>` 設定並將其設定為唯一識別碼。 此識別碼是用來將範本套件解除安裝，並由 NuGet 摘要用來註冊您的範本套件。
01. 應該設定的一般中繼資料：`<Title>`、`<Authors>`、`<Description>`，以及 `<PackageTags>`。
01. 必須設定 `<TargetFramework>` 設定，即使由範本程序所產生的二進位檔不會被使用。 在下列範例中，它被設定為 `netstandard2.0`。

具有 *.nupkg* NuGet 套件的範本套件，會要求將所有範本都儲存在套件內的 *content* 資料夾中。 還有幾個設定需要被加入至 *.csproj* 檔案，以確保可以將所產生的 *.nupkg* 安裝為範本套件：

01. `<IncludeContentInPack>` 設定已被設定為 `true`，以將專案設定為 **content** 的任何檔案包含在 NuGet 套件中。
01. `<IncludeBuildOutput>` 設定已被設定為 `false`，以將編譯器所產生的所有二進位檔從 NuGet 套件排除。
01. `<ContentTargetFolders>` 設定已被設定為 `content`。 這能確保設定為 **content** 的檔案都會被儲存在 NuGet 套件中的 *content* 資料夾內。 NuGet 套件中的這個資料夾會由 dotnet 範本系統進行剖析。

排除所有程式碼檔案來使範本專案不會對它們進行編譯的簡單方式，是在專案檔中於 `<ItemGroup>` 元素內使用 `<Compile Remove="**\*" />` 項目。

建構範本套件的簡單方式，是將所有範本置於個別的資料夾中，然後將每個範本資料夾置於與 *.csproj* 檔案相同目錄中的 *templates* 資料夾內。 如此一來，您便可以使用單一專案項目來將 *templates* 中的所有檔案和資料夾包含為 **content**。 在 `<ItemGroup>` 元素內，建立 `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` 項目。

以下是遵循上述所有指導方針的範例 *.csproj* 檔案。 它會將 *templates* 子資料夾封裝至 *content* 套件資料夾，並將所有程式碼檔案排除於編譯程序之外。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>
    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

下列範例示範使用 *.csproj* 來建立範本套件的檔案和資料夾結構。 *MyDotnetTemplates.csproj* 檔案和 *templates* 資料夾皆位於名為 *project_folder* 之目錄的根位置。 *templates* 資料夾包含兩個範本，*mytemplate1* 和 *mytemplate2*。 每個範本都具有內容檔案，以及具有 *template.json* 設定檔的 *.template.config* 資料夾。

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a>安裝範本

使用 [dotnet new -i|--install](dotnet-new.md) 命令來安裝套件。

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>從儲存在 nuget.org 的 NuGet 套件安裝範本

使用 NuGet 套件識別碼來安裝範本套件。

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>從本機 nupkg 檔案安裝範本

提供 *.nupkg* NuGet 套件檔案的路徑。

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>從檔案系統目錄安裝範本

可以從範本資料夾 (例如上述範例中的 *mytemplate1* 資料夾) 安裝範本。 指定 *.template.config* 資料夾的資料夾路徑。 範本資料夾的路徑並不需要是絕對路徑。 不過，若要將從某個資料夾安裝的範本解除安裝，便需要絕對路徑。

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>取得已安裝範本的清單

沒有任何其他參數的解除安裝命令，將會列出所有已安裝的範本。

```console
dotnet new -u
```

該命令會傳回類似下列輸出的內容：

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

`Currently installed items:` 之後的第一層項目，是用來將範本解除安裝的識別碼。 而在上述範例中，系統會列出 `Microsoft.DotNet.Common.ItemTemplates` 和 `Microsoft.DotNet.Common.ProjectTemplates.3.0`。 如果範本是使用檔案系統路徑安裝，此識別碼將會是 *.template.config* 資料夾的資料夾路徑。

## <a name="uninstalling-a-template"></a>解除安裝範本

使用 [dotnet new -u|--uninstall](dotnet-new.md) 命令來解除安裝套件。

如果套件是由 NuGet 摘要或直接由 *.nupkg* 檔案安裝，請提供識別碼。

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

如果套件是透過指定 *.template.config* 資料夾路徑的方式安裝，請使用該**絕對**路徑來將套件解除安裝。 您可以在由 `dotnet new -u` 命令所提供的輸出中查看範本的絕對路徑。 如需詳細資訊，請參閱上面的[取得已安裝範本的清單](#get-a-list-of-installed-templates)小節。

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>使用自訂範本建立專案

在安裝範本之後，如同處理任何其他預先安裝的範本一樣，執行 `dotnet new <TEMPLATE>` 命令使用範本。 您也可以指定 `dotnet new` 命令的[選項](dotnet-new.md#options)，包括您在範本設定中設定的範本特定選項。 直接將範本的簡短名稱提供給命令：

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>另請參閱

- [建立 dotnet new 的自訂範本 (教學課程)](../tutorials/create-custom-template.md)
- [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)
- [dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)
- [如何建立您自己的 dotnet new 範本](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [JSON 結構描述保存區的 *template.json* 結構描述](http://json.schemastore.org/template)
