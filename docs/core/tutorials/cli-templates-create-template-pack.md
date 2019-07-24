---
title: 建立適用於 dotnet new 的範本套件
description: 了解如何建立將會針對 dotnet new 命令建置範本套件的 csproj 檔案。
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: df8c33856195ba7feacd32203e4a885997b50ad2
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870627"
---
# <a name="tutorial-create-a-template-pack"></a>教學課程：建立範本套件

透過 .NET Core，您可以建立及部署能產生專案、檔案，甚至是資源的範本。 此教學課程是指導您如何建立、安裝及解除安裝能搭配 `dotnet new` 命令使用之範的本系列文章第三部分。

在這部分的系列文章中，您將了解如何：

> [!div class="checklist"]
> * 建立 _.csproj* 專案以建置範本套件
> * 設定專案檔以用於封裝
> * 從 NuGet 套件檔案安裝範本
> * 依套件識別碼將範本解除安裝

## <a name="prerequisites"></a>必要條件

* 完成此教學課程系列的[第 1 部分](cli-templates-create-item-template.md)和[第 2 部分](cli-templates-create-project-template.md)。

  此教學課程會使用在此教學課程系列的前兩個部分中所建立的兩個範本。 您可以使用不同的範本，前提是您必須將該範本以資料夾的形式複製到 _working\templates\\_ 資料夾中。

* 開啟終端機並瀏覽至 _working\templates\\_ 資料夾。

## <a name="create-a-template-pack-project"></a>建立範本套件專案

範本套件是將一或多個範本封裝到檔案內。 當您安裝或解除安裝套件時，包含在套件中的所有範本也都會相對地被新增或移除。 此教學課程系列之前的部分皆僅處理個別的範本。 若要共用未封裝的範本，您必須複製範本資料夾並透過該資料夾來安裝。 由於範本套件可以在其中具有多個範本且為單一檔案，因此共用會變得更加容易。

範本套件是以 NuGet 套件 ( _.nupkg_) 檔案來代表。 此外，和任何 NuGet 套件相同，您可以將範本套件上傳至 NuGet 摘要。 `dotnet new -i` 命令支援從 NuGet 套件摘要安裝範本套件。 此外，您可以直接從 _.nupkg_ 檔案安裝範本套件。

通常，您可以使用 C# 專案檔來編譯程式碼並產生二進位檔。 不過，專案也可以用來產生範本套件。 透過變更 _.csproj_ 的設定，您會防止它編譯任何程式碼，並改為使它將您範本的所有資產包含為資源。 在建置此專案之後，它會產生範本套件 NuGet 套件。

您建立的套件將會包含先前所建立的[項目範本](cli-templates-create-item-template.md)和[專案範本](cli-templates-create-project-template.md)。 由於我們將這兩個範本分組到 _working\templates\\_ 資料夾，我們可以針對 _.csproj_ 檔案使用 _working_ 資料夾。

在您的終端機中，瀏覽至 _working_ 資料夾。 建立新專案，並將名稱設定為 `templatepack`，然後將輸出資料夾設定為目前的資料夾。

```console
dotnet new console -n templatepack -o .
```

`-n` 參數會將 _.csproj_ 檔案名稱設定為 _templatepack.csproj_，而 `-o` 參數則會在目前的目錄中建立檔案。 您應該會看到類似以下輸出的結果。

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

接下來，在您慣用的編輯器中開啟 _templatepack.csproj_ 檔案，並以下列 XML 取代其內容：

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

上面 XML 中的 `<PropertyGroup>` 設定會被分成三個群組。 第一個群組會處理 NuGet 套件的必要屬性。 三個 `<Package` 設定和用來在 NuGet 摘要上識別您套件的 NuGet 套件屬性有關。 特別是 `<PacakgeId>` 值，其是用來透過單一名稱 (而非目錄路徑) 將範本套件解除安裝。 它也可以用來從 NuGet 摘要安裝範本套件。 其餘的設定 (例如 `<Title>` 和 `<Tags>`) 都與顯示在 NuGet 摘要上的中繼資料有關。 如需 NuGet 設定的詳細資訊，請參閱 [NuGet 和 MSBuild 屬性](/nuget/reference/msbuild-targets)。

必須設定 `<TargetFramework>` 設定，來使 MSBuild 能在您執行封裝命令以編譯及封裝專案時能夠正常執行。

最後的三個設定與在建立 NuGet 套件時正確設定專案，以將範本包含在 NuGet 套件中適當的資料夾有關。

`<ItemGroup>` 包含兩個設定。 首先，`<Content>` 設定會將 _templates_ 資料夾中的所有項目包含為內容。 它也會排除任何 _bin_ 資料夾或 _obj_ 資料夾，以防止包含任何已編譯的程式碼 (如果您已測試並編譯您的範本的話)。 再來，`<Compile>` 設定會將所有程式碼檔案排除在編譯之外，無論它們位於何處。 此設定能防止用來建立範本套件的專案嘗試編譯 _templates_ 資料夾階層中的程式碼。

## <a name="build-and-install"></a>建置及安裝

儲存此檔案，然後執行封裝命令

```console
dotnet pack
```

此命令將會建置您的專案，然後在 _working\bin\Debug_ 資料夾中建立 NuGet 套件。

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

接下來，請使用 `dotnet new -i PATH_TO_NUPKG_FILE` 命令來安裝範本套件檔案。

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

如果您將 NuGet 套件上傳至 NuGet 摘要，您可以使用 `dotnet new -i PACKAGEID` 命令；其中 `PACKAGEID` 和 _.csproj_ 檔案中的 `<PackageId>` 設定相同。 此套件識別碼和 NuGet 套件識別碼相同。

## <a name="uninstall-the-template-pack"></a>將範本套件解除安裝

無論您安裝範本套件的方法為何 (直接透過 _.nupkg_ 檔案或是透過 NuGet 摘要)，移除範本套件的方法也是相同的。 使用您想要解除安裝之範本的 `<PackageId>`。 您可以透過執行 `dotnet new -u` 命令來取得已安裝範本的清單。

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

執行 `dotnet new -u AdatumCorporation.Utility.Templates` 來將範本解除安裝。 `dotnet new` 命令將會輸出說明資訊，其應該會省略您先前所安裝的範本。

恭喜您！ 您已安裝並解除安裝範本套件。 

## <a name="next-steps"></a>後續步驟

若要深入了解範本 (您已經了解其大部分的內容)，請參閱 [dotnet new 的自訂範本](../tools/custom-templates.md)一文。

* [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)
* [dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)
* [JSON 結構描述保存區的 *template.json* 結構描述](http://json.schemastore.org/template)
