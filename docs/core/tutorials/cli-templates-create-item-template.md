---
title: 針對 dotnet new 建立項目範本 - .NET Core CLI
description: 了解如何針對 dotnet new 命令建立項目範本。 項目範本可能會包含數個檔案。
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 4d47146913ed83ff3dd029558f79f23b4f54ce19
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849503"
---
# <a name="tutorial-create-an-item-template"></a>教學課程：建立項目範本

透過 .NET Core，您可以建立及部署能產生專案、檔案，甚至是資源的範本。 此教學課程是指導您如何建立、安裝及解除安裝能搭配 `dotnet new` 命令使用之範的本系列文章第一部分。

在這部分的系列文章中，您將了解如何：

> [!div class="checklist"]
> * 針對項目範本建立類別
> * 建立範本設定資料夾和檔案
> * 從檔案路徑安裝範本
> * 測試項目範本
> * 將項目範本解除安裝

## <a name="prerequisites"></a>必要條件

* [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) 或更新版本。
* 請參閱參考文章 [dotnet new 的自訂範本](../tools/custom-templates.md)。

  該參考文章會說明範本的基本概念及構成方式。 那些資訊有一部分會在此重述。

* 開啟終端機並瀏覽至 _working\templates\\_ 資料夾。

## <a name="create-the-required-folders"></a>建立必要的資料夾

本系列文章會使用「工作資料夾」來存放您的範本來源，並使用「測試資料夾」來測試您的範本。 工作資料夾和測試資料夾應該放在相同的父資料夾中。

首先，請建立父資料夾；其名稱並不重要。 然後，建立名為 _working_ 的子資料夾。 在 _working_ 資料夾中，建立名為 _templates_ 的子資料夾。

接下來，在父資料夾底下建立名為 _test_ 的資料夾。 資料夾結構看起來應如下所示：

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>建立項目範本

項目範本是特定類型的範本，其會包含一或多個檔案。 這些範本類型很適合在您想要產生設定、程式碼或方案檔之類的項目時使用。 在此範例中，您將會建立能將擴充方法加入字串類型的類別。

在您的終端機中，瀏覽至 _working\templates\\_ 資料夾，並建立名為 _extensions_ 的新子資料夾。 進入該資料夾。

```console
working
└───templates
    └───extensions
```

建立名為 _CommonExtensions.cs_ 的新檔案，並使用您慣用的文字編輯器開啟它。 此類別將會提供名為 `Reverse` 的擴充方法，其能反轉字串的內容。 貼上下列程式碼並儲存檔案：

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

您已經建立範本的內容，現在您需要在範本的根資料夾建立範本設定。

## <a name="create-the-template-config"></a>建立範本設定

.NET Core 會將範本辨識為存在於範本根目錄中的特殊資料夾及設定檔。 在此教學課程中，您的範本資料夾是位於 _working\templates\extensions\\_ 。

當您建立範本時，範本資料夾中的所有檔案和資料夾都會包含為範本的一部分，除了特殊設定資料夾之外。 此設定資料夾名為 _.template.config_。

首先，建立名為 _.template.config_ 的新子資料夾，然後進入它。 然後，建立名為 _template.json_ 的新檔案。 您的資料夾結構看起來應該像這樣：

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

使用您慣用的文字編輯器開啟 _template.json_，然後貼上下列 JSON 程式碼並儲存它：

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

此設定檔會包含您範本的所有設定。 您可以看見基本設定 (例如 `name` 和 `shortName`)，但還有設定為 `item` 的 `tags/type` 值。 這會將您的範本分類為項目範本。 您可以建立的範本類型本身並無限制。 `item` 和 `project` 值是 .NET Core 建議的常用名稱，它們可以讓使用者輕鬆篩選其想要尋找的範本類型。

`classifications` 項目代表您執行 `dotnet new` 並取得範本清單時所會看見的 [標籤] 欄。 使用者也可以根據分類標籤搜尋。 不要將 \*.json 檔案中的 `tags` 屬性與 `classifications` 標籤清單混淆在一起。 它們是不同的東西，但不幸地具有類似的名稱。 *template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。 如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。

您已經具備有效的 _.template.config/template.json_ 檔案，現在您的範本已經準備好並可供安裝。 在您的終端機中，瀏覽至 _extensions_ 資料夾，並執行下列命令以安裝位於目前資料夾中的範本：

* **在 Windows 上**：`dotnet new -i .\`
* **在 Linux 或 MacOS 上**：`dotnet new -i ./`

此命令會輸出已安裝範本的清單，其中應該會包含您的範本。

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a>測試項目範本

您已經安裝項目範本，現在請測試它。 瀏覽至 _test/_ 資料夾並使用 `dotnet new console` 建立新的主控台應用程式。 這會產生工作專案，其可讓您使用 `dotnet run` 命令輕鬆地進行測試。

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

接下來，執行 `dotnet new stringext` 以從範本產生 _CommonExtensions.cs_。

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

變更 _Program.cs_ 中的程式碼，以搭配由範本所提供的擴充方法來反轉 `"Hello World"` 字串。

```csharp
Console.WriteLine("Hello World!".Reverse());
```

再次執行該程式，您將會看到結果已被反轉。

```console
C:\test> dotnet run
!dlroW olleH
```

恭喜您！ 您已透過 .NET Core 建立並部署項目範本。 為了針對此教學課程系列的下一部份做準備，您必須將您所建立的範本解除安裝。 同時，請務必刪除 _test_ 資料夾中的所有檔案。 這能讓您回到最原始的狀態，並準備好進行此教學課程的下一個主要區段。

## <a name="uninstall-the-template"></a>解除安裝範本

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>後續步驟

在此教學課程中，您已建立項目範本。 若要了解如何建立專案範本，請繼續進行此教學課程系列。

> [!div class="nextstepaction"]
> [建立專案範本](cli-templates-create-project-template.md)
