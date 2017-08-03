---
title: ".NET Core 工具遙測"
description: "探索收集使用量資訊以進行分析的 .NET Core 工具遙測功能。"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1816b9fbad1f671820c9f970674c8af2147a230e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-tools-telemetry"></a>.NET Core 工具遙測

.NET Core 工具包含收集使用資訊的[遙測功能](https://github.com/dotnet/cli/pull/2145)。 .NET 小組必須了解如何使用這些工具，讓我們可以進行改善。

所收集的資料是匿名的，而且將會以彙總形式發行，讓 Microsoft 和社群工程師根據 [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) 來使用。

## <a name="scope"></a>範圍

`dotnet` 命令用來啟動應用程式和 .NET Core 工具。 `dotnet` 命令本身不會收集遙測資料。 它是透過收集遙測資料的 `dotnet` 命令所執行的 .NET Core 工具。

.NET Core 命令 (未啟用遙測)：

- `dotnet`
- `dotnet [path-to-app]`

.NET Core 工具[命令](index.md) (已啟用遙測)，例如：

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="behavior"></a>行為

預設會啟用 .NET Core 工具遙測功能。 您可以將 DOTNET_CLI_TELEMETRY_OPTOUT 環境變數 (例如，macOS/Linux 上的 `export`、Windows 上的 `set`) 設定為 true (例如，"true", 1)，來選擇遙測功能。

## <a name="data-points"></a>資料點

這個功能會收集下列資料部分︰

- 正在使用的命令 (例如，"build"、"restore")
- 命令的 ExitCode
- 針對測試專案，是正在使用的測試執行器
- 叫用的時間戳記
- 使用的架構
- 執行階段識別碼是否存在於 "runtimes" 節點中
- 正在使用的 CLI 版本

這個功能不會收集任何個人資料 (例如使用者名稱或電子郵件)。 它將不會掃描您的程式碼，也不會擷取可視為機密的任何專案層級資料，例如名稱、存放庫或作者 (如果您在 project.json 中進行設定)。 我們想要知道工具的用途，而不是您正在使用工具所建置的項目。 如果您發現收集的是機密資料，則是錯誤。 請[提出問題](https://github.com/dotnet/cli/issues)，將會進行修正。

## <a name="license"></a>使用權

Microsoft 的 .NET Core 散發是使用 [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) 所授權。 這包含下面重新列印的 "DATA" 區段以啟用遙測。

[.NET NuGet 套件](https://www.nuget.org/profiles/dotnetframework)使用這個相同的授權，但未啟用遙測 (請參閱上方的[範圍](#scope))。

> 2. 資料。 軟體可能會收集和您及您使用軟體之方式有關的資訊，並將該資訊傳送給 Microsoft。 Microsoft 可能會使用此資訊以改善產品與服務。 您可以前往 http://go.microsoft.com/fwlink/?LinkId=528096，以在說明文件及隱私權聲明中深入了解資料收集和使用方式的相關資訊。 使用軟體即代表您同意這些做法。

## <a name="disclosure"></a>公開

.NET Core 工具會在您第一次執行其中一個命令時顯示下列文字 (例如，`dotnet restore`)。 這個「第一次執行」經驗是 Microsoft 如何通知您有關資料收集。 這個相同的體驗一開始也會將 .NET Core SDK 中的程式庫填入 NuGet 快取，避免要求這些程式庫的 NuGet.org (或其他 NuGet 摘要)。

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.

Configuring...
-------------------
A command is running to initially populate your local package cache, to improve restore speed and enable offline access. This command will take up to a minute to complete and will only happen once.
```

