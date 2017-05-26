---
title: "dotnet 命令 - .NET Core CLI | Microsoft Docs"
description: "了解 dotnet 命令 (.NET Core CLI 工具的泛型驅動程式) 和其用法。"
keywords: "dotnet, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/20/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 256e468e-eaaa-4715-b5fb-8cbddcf80e69
ms.translationtype: Human Translation
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 02779e1ac5db1a7a68ddede6d30063366270dc50
ms.contentlocale: zh-tw
ms.lasthandoff: 04/10/2017

---

# <a name="dotnet-command"></a>dotnet 命令

## <a name="name"></a>名稱

`dotnet` - 用於執行命令列命令的一般驅動程式。

## <a name="synopsis"></a>概要

`dotnet [command] [arguments] [--version] [--info] [-d|--diagnostics] [-v|--verbose] [--fx-version] [--additionalprobingpath] [-h|--help]`

## <a name="description"></a>說明

`dotnet` 是命令列介面 (CLI) 工具鏈的泛型驅動程式。 它會自行叫用，提供簡短的使用方式指示。

每個特定功能都是當成命令來實作。 若要使用這個功能，請在 `dotnet` 之後指定這個命令 (例如 [`dotnet build`](dotnet-build.md))。 這個命令後面的所有引數都是它自己的引數。

`dotnet` 唯一自行作為命令使用的時機是執行[與 Framework 相依的應用程式](../deploying/index.md)。 在 `dotnet` 動詞之後指定應用程式 DLL，以執行應用程式 (例如，`dotnet myapp.dll`)。

## <a name="options"></a>選項

`-v|--verbose`

啟用詳細資訊輸出。

`-d|--diagnostics`

啟用診斷輸出。

`--fx-version <VERSION>`

用來執行應用程式之已安裝共用架構的版本。

`--additionalprobingpath <PATH>`

包含探查原則和要探查之組件的路徑。

`--version`

印出 CLI 工具的版本。

`--info`

印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。

`-h|--help`

印出命令的簡短說明。 如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。

## <a name="dotnet-commands"></a>dotnet 命令

### <a name="general"></a>一般

命令 | 函式
--- | ---
[dotnet-build](dotnet-build.md) | 建置 .NET Core 應用程式。
[dotnet-clean](dotnet-clean.md) | 清除建置輸出。
[dotnet-migrate](dotnet-migrate.md) | 將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。
[dotnet-msbuild](dotnet-msbuild.md) | 提供對 MSBuild 命令列的存取。
[dotnet-new](dotnet-new.md) | 初始化指定範本的 C# 或 F# 專案。
[dotnet-pack](dotnet-pack.md) | 建立您程式碼的 NuGet 套件。
[dotnet-publish](dotnet-publish.md) | 發行 .NET 與 Framework 相依的應用程式或獨立應用程式。
[dotnet-restore](dotnet-restore.md) | 還原所指定應用程式的相依性。
[dotnet-run](dotnet-run.md) | 從原始檔執行應用程式。
[dotnet-sln](dotnet-sln.md) | 要在方案檔中新增、移除及列出專案的選項。
[dotnet-test](dotnet-test.md) | 使用測試執行器執行測試。

### <a name="project-references"></a>專案參考

命令 | 函式
--- | ---
[dotnet-add reference](dotnet-add-reference.md) | 新增專案參考。
[dotnet-list reference](dotnet-list-reference.md) | 列出專案參考。
[dotnet-remove reference](dotnet-remove-reference.md) | 移除專案參考。

### <a name="nuget-packages"></a>NuGet 套件

命令 | 函式
--- | ---
[dotnet-add package](dotnet-add-package.md) | 新增 NuGet 套件。
[dotnet-remove package](dotnet-remove-package.md) | 移除 NuGet 套件。

### <a name="nuget-commands"></a>NuGet 命令

命令 | 函式
--- | ---
[dotnet-nuget delete](dotnet-nuget-delete.md) | 從伺服器刪除或取消列出套件。
[dotnet-nuget locals](dotnet-nuget-locals.md) | 清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。
[dotnet-nuget push](dotnet-nuget-push.md) | 將套件推送至伺服器並發行。

## <a name="examples"></a>範例

初始化可編譯和執行的範例 .NET Core 主控台應用程式：

`dotnet new console`

還原所指定應用程式的相依性：

`dotnet restore`

建置所指定目錄中的專案和其相依性：

`dotnet build`

執行名稱為 `myapp.dll` 的與 Framework 相依的應用程式：

`dotnet myapp.dll`

## <a name="environment-variables"></a>環境變數

`DOTNET_PACKAGES`

主要套件快取。 如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。

`DOTNET_SERVICING`

指定載入執行階段時，共用主機所使用的服務索引位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。 設定為 `true` 取消遙測功能 (可接受的值為 `true`、`1` 或 `yes`)；否則，設定為 `false` 加入遙測功能 (可接受的值為 `false`、`0` 或 `no`)。 如果未設定，預設值為 `false`，且遙測功能為使用中。

