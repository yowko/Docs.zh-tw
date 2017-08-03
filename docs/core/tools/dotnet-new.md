---
title: "dotnet-new 命令 - .NET Core CLI"
description: "dotnet-new 命令會在目前的目錄中建立新的 .NET Core 專案。"
keywords: "dotnet-new, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 56033295b2448b045d5a51dbd84d5429aed77451
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-new"></a>dotnet-new

## <a name="name"></a>名稱

`dotnet-new` - 根據指定的範本建立新的專案、組態檔或方案。

## <a name="synopsis"></a>概要

```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>描述

`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。 

命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。

## <a name="arguments"></a>引數

`TEMPLATE`

要在叫用命令時具現化的範本。 每個範本可能會有您可以傳遞的特定選項。 如需詳細資訊，請參閱[範本選項](#template-options)。

此命令包含預設的範本清單。 使用 `dotnet new -all` 以取得可用範本的清單。 下表顯示隨 SDK 預先安裝的範本。 範本的預設語言會顯示在方括號內。

|範本描述  | 範本名稱  | 語言 |
|----------------------|----------------|-----------|
| 主控台應用程式  | 主控台        | [C#]、F#  |
| 類別庫        | classlib       | [C#]、F#  |
| 單元測試專案    | mstest         | [C#]、F#  |
| xUnit 測試專案   | xunit          | [C#]、F#  |
| 空的 ASP.NET Core   | web            | [C#]      |
| ASP.NET Core Web 應用程式 | mvc            | [C#]、F#  |
| ASP.NET Core Web API | webapi         | [C#]      |
| Nuget 組態         | nugetconfig    |           |
| Web 組態           | webconfig      |           |
| 方案檔        | sln            |           |

## <a name="options"></a>選項

`-h|--help`

印出命令的說明。 可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。

`-l|--list`

列出包含指定名稱的範本。 如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。 例如，如果目錄中已包含專案，則不會列出所有專案範本。

`-lang|--language {C#|F#}`

要建立的範本語言。 接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。 並非所有範本都適用。

`-n|--name <OUTPUT_NAME>`

所建立輸出的名稱。 如果未指定名稱，則會使用目前目錄的名稱。

`-o|--output <OUTPUT_DIRECTORY>`

放置所產生輸出的位置。 預設為目前的目錄。

`-all|--show-all`

單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。 在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。 當輸出目錄中已包含專案時，這是必要選項。

## <a name="template-options"></a>範本選項

每個專案範本都可能會有其他可用的選項。 核心範本會有下列選項：

**console、xunit、mstest、web、webapi**

`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。 值：`netcoreapp1.0` 或 `netcoreapp1.1` (預設值：`netcoreapp1.0`)

**mvc**

`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。 值：`netcoreapp1.0` 或 `netcoreapp1.1` (`Default: netcoreapp1.0`)

`-au|--auth` - 要使用的驗證類型。 值：`None` 或 `Individual` (預設值：`None`)

`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。 值：`true` 或 `false` (預設值：`false`)

**classlib**

`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。 值：`netcoreapp1.0`、`netcoreapp1.1`，或從 `netstandard1.0` 到 `netstandard1.6` (預設值：`netstandard1.4`)

## <a name="examples"></a>範例

在目前的目錄中建立 F# 主控台應用程式專案：

`dotnet new console -lang f#` 
   
未經驗證即在目前的目錄中，建立以 .NET Core 1.0 為目標新的 ASP.NET Core C# MVC 應用程式專案：  

`dotnet new mvc -au None -f netcoreapp1.0`
 
建立以 .NET Core 1.1 為目標的新 xUnit 應用程式：

`dotnet new xunit --framework netcoreapp1.1`

列出 MVC 可用的所有範本：

`dotnet new mvc -l`

