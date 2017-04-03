---
title: "dotnet-test 命令 - .NET Core CLI | Microsoft Docs"
description: "`dotnet test` 命令是用來在指定的專案中執行單元測試。"
keywords: "dotnet-test, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 26b5834135db8041995a137f5008d00cdf14d820
ms.lasthandoff: 03/22/2017

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>名稱

`dotnet-test` - 用來執行單元測試的 .NET 測試驅動程式。

## <a name="synopsis"></a>概要

`dotnet test [<PROJECT>] [-s|--settings] [-t|--list-tests] [--filter] [-a|--test-adapter-path] [-l|--logger] [-c|--configuration] [-f|--framework] [-o|--output] [-d|--diag] [--no-build] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>描述

`dotnet test` 命令是用來在指定的專案中執行單元測試。 單元測試是與單元測試架構 (例如 MSText、NUnit 或 xUnit) 具有相依性的類別庫專案，以及該單元測試架構的 dotnet 測試執行器。 這些會封裝為 NuGet 套件，並還原為專案的一般相依性。

測試專案也必須指定測試執行器。 這是使用一般 `<PackageReference>` 元素所指定，如下列範例專案檔中所示：

[!code-xml[XUnit 基本範本](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="options"></a>選項

`PROJECT`
    
指定測試專案的路徑。 如果省略，則會預設為目前目錄。

`-h|--help`

印出命令的簡短說明。

`-s|--settings <SETTINGS_FILE>`

執行測試時要使用的設定。 

`-t|--list-tests`

列出在目前專案中探索到的所有測試。 

`--filter <EXPRESSION>`

使用指定的運算式篩選出目前專案中的測試。 如需有關篩選支援的詳細資訊，請參閱[使用 TestCaseFilter 在 Visual Studio 中執行選擇性單元測試 (英文)](https://aka.ms/vstest-filtering)。

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

在測試執行中，從指定的路徑使用自訂測試配接器。 

`-l|--logger <LoggerUri/FriendlyName>`

指定測試結果的記錄器。 

`-c|--configuration <CONFIGURATION>`

用來建置的組態。 預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。

`-f|--framework <FRAMEWORK>`

尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。

`-o|--output <OUTPUT_DIRECTORY>`

在其中尋找要執行的二進位檔的目錄。

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。 

`--no-build` 

請不要在執行之前建置測試專案。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

執行目前目錄之專案中的測試：

`dotnet test` 

執行 `test1` 專案中的測試︰

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>請參閱

* [目標架構](../../standard/frameworks.md)
* [執行階段識別項 (RID) 目錄](../rid-catalog.md)
