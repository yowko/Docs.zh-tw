---
title: 建立適用於 dotnet new 的專案範本
description: 了解如何針對 dotnet new 命令建立專案範本。
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 3455720d729f813d9b6f32e433adffa4dc40dce4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926140"
---
# <a name="tutorial-create-a-project-template"></a>教學課程：建立專案範本

透過 .NET Core，您可以建立及部署能產生專案、檔案，甚至是資源的範本。 此教學課程是指導您如何建立、安裝及解除安裝能搭配 `dotnet new` 命令使用之範的本系列文章第二部分。

在這部分的系列文章中，您將了解如何：

> [!div class="checklist"]
>
> * 建立專案範本的資源
> * 建立範本設定資料夾和檔案
> * 從檔案路徑安裝範本
> * 測試項目範本
> * 將項目範本解除安裝

## <a name="prerequisites"></a>必要條件

* 完成此教學課程系列的[第 1 部分](cli-templates-create-item-template.md)。
* 開啟終端機並瀏覽至 _working\templates\\_ 資料夾。

## <a name="create-a-project-template"></a>建立專案範本

專案範本能產生可立即執行的專案，讓使用者能以一組已可運作的程式碼來輕鬆開始。 .NET Core 包含幾個專案範本，例如主控台應用程式或類別庫。 在此範例中，您將會建立新的主控台專案，其能啟用 C# 8.0 並產生 `async main` 進入點。

在您的終端機中，瀏覽至 _working\templates\\_ 資料夾，並建立名為 _consoleasync_ 的新子資料夾。 進入該子資料夾，然後執行 `dotnet new console` 以產生標準主控台應用程式。 您將會編輯由此範本所產生的檔案來建立新的範本。

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>修改 Program.cs

開啟 _program.cs_ 檔案。 該主控台專案不會使用非同步進入點，因次讓我們來加入它。 將程式碼變更為下列程式碼，然後儲存檔案：

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a>修改 consoleasync.csproj

讓我們將專案使用的 C# 語言版本更新為 8.0 版。 編輯 _consoleasync.csproj_ 檔案並將 `<LangVersion>` 設定加入 `<PropertyGroup>` 節點。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>建置專案

在您完成專案範本之前，您應該測試它以確保其能正確編譯及執行。 在終端機中執行 `dotnet run` 命令，您應該會看見下列輸出：

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

您可以將使用 `dotnet run` 所建立的 _obj_ 和 _bin_ 資料夾刪除。 刪除這些檔案能確保您的範本只會包含與範本相關的檔案，而不會包含因建置動作而產生的任何檔案。

您已經建立範本的內容，現在您需要在範本的根資料夾建立範本設定。

## <a name="create-the-template-config"></a>建立範本設定

.NET Core 會將範本辨識為存在於範本根目錄中的特殊資料夾及設定檔。 在此教學課程中，您的範本資料夾是位於 _working\templates\consoleasync\\_ 。

當您建立範本時，範本資料夾中的所有檔案和資料夾都會包含為範本的一部分，除了特殊設定資料夾之外。 此設定資料夾名為 _.template.config_。

首先，建立名為 _.template.config_ 的新子資料夾，然後進入它。 然後，建立名為 _template.json_ 的新檔案。 您的資料夾結構看起來應該像這樣：

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

使用您慣用的文字編輯器開啟 _template.json_，然後貼上下列 JSON 程式碼並儲存它：

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

此設定檔會包含您範本的所有設定。 您可以看見基本設定 (例如 `name` 和 `shortName`)，但還有設定為 `project` 的 `tags/type` 值。 這會將您的範本指定為專案範本。 您可以建立的範本類型本身並無限制。 `item` 和 `project` 值是 .NET Core 建議的常用名稱，它們可以讓使用者輕鬆篩選其想要尋找的範本類型。

`classifications` 項目代表您執行 `dotnet new` 並取得範本清單時所會看見的 [標籤] 欄。 使用者也可以根據分類標籤搜尋。 不要將 JSON 檔案中的 `tags` 屬性與 `classifications` 標籤清單混淆在一起。 它們是不同的東西，但不幸地具有類似的名稱。 *template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。 如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。

您已經具備有效的 _.template.config/template.json_ 檔案，現在您的範本已經準備好並可供安裝。 在您安裝範本之前，請確定您已將不想要包含在範本中的所有額外檔案資料夾和檔案刪除，例如 _bin_ 或 _obj_ 資料夾。 在您的終端機中，瀏覽至 _consoleasync_ 資料夾，並執行 `dotnet new -i .\` 以安裝位於目前資料夾中的範本。 如果您是使用 Linux 或 MacOS 作業系統，請使用正斜線：`dotnet new -i ./`。

此命令會輸出已安裝範本的清單，其中應該會包含您的範本。

```console
C:\working\templates\consoleasync> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a>測試專案範本

您已經安裝項目範本，現在請測試它。 瀏覽至 _test_ 資料夾並使用 `dotnet new console` 建立新的主控台應用程式。 這會產生工作專案，其可讓您使用 `dotnet run` 命令輕鬆地進行測試。

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

恭喜您！ 您已透過 .NET Core 建立並部署專案範本。 為了針對此教學課程系列的下一部份做準備，您必須將您所建立的範本解除安裝。 同時，請務必刪除 _test_ 資料夾中的所有檔案。 這能讓您回到最原始的狀態，並準備好進行此教學課程的下一個主要區段。

### <a name="uninstall-the-template"></a>解除安裝範本

由於您是依檔案路徑來安裝範本，您必須使用**絕對**檔案路徑來將它解除安裝。 您可以透過執行 `dotnet new -u` 命令來查看已安裝範本的清單。 您的範本應該會被列在最後。 使用列出的路徑來搭配 `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` 命令將您的範本解除安裝。

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>後續步驟

在此教學課程中，您已建立專案範本。 若要了解如何將項目和專案範本封裝為易於使用的單一檔案，請繼續進行此教學課程系列。

> [!div class="nextstepaction"]
> [建立範本套件](cli-templates-create-template-pack.md)
