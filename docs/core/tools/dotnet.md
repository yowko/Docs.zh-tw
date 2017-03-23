---
title: "dotnet 命令 | Microsoft Docs"
description: "了解 dotnet 命令 (.NET Core CLI 工具的泛型驅動程式) 和其用法。"
keywords: "dotnet, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 256e468e-eaaa-4715-b5fb-8cbddcf80e69
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: e3eedff7d98245bd63d758236840568eabd05445
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-command"></a>dotnet 命令

## <a name="name"></a>名稱

`dotnet` - 用於執行命令列命令的一般驅動程式

## <a name="synopsis"></a>概要

```
dotnet [command] [arguments] [--version] [--info] [-d|--diagnostics] [-v|--verbose]
dotnet [-h|--help]
```

## <a name="description"></a>說明

`dotnet` 是命令列介面 (CLI) 工具鏈的泛型驅動程式。 自行叫用，它會提供簡短使用指示。

每個特定功能都是當成命令來實作。 若要使用這個功能，請在 `dotnet` 之後指定這個命令 (例如 [`dotnet build`](dotnet-build.md))。 這個命令後面的所有引數都是它自己的引數。

`dotnet` 當成自己的命令的唯一時間是執行可攜式應用程式。 只在 `dotnet` 動詞後面指定可攜式應用程式 DLL，來執行應用程式。

## <a name="options"></a>選項

`-v|--verbose`

啟用詳細資訊輸出。

`-d|--diagnostics`

啟用診斷輸出。

`--version`

印出 CLI 工具的版本。

`--info`

印出 CLI 工具的詳細資訊 (例如目前作業系統、版本的認可 SHA 等)。

`-h|--help`

印出命令的簡短說明。 如果只與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。

## <a name="dotnet-commands"></a>dotnet 命令

dotnet 具有下列命令：

* [dotnet-new](dotnet-new.md)
  * 初始化指定範本的 C# 或 F# 專案。
* [dotnet-restore](dotnet-restore.md)
  * 還原所指定應用程式的相依性。
* [dotnet-build](dotnet-build.md)
  * 建置 .NET Core 應用程式。
* [dotnet-publish](dotnet-publish.md)
  * 發行 .NET 可攜式或獨立應用程式。
* [dotnet-run](dotnet-run.md)
  * 從原始檔執行應用程式。
* [dotnet-test](dotnet-test.md)
  * 使用 project.json 中指定的測試執行器，來執行測試。
* [dotnet-pack](dotnet-pack.md)
  * 建立您程式碼的 NuGet 套件。
* [dotnet-migrate](dotnet-migrate.md)
  * 將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。
* [dotnet-msbuild](dotnet-msbuild.md)
  * 提供對 MSBuild 命令列的存取。
* [dotnet-clean](dotnet-clean.md)
  * 清除建置輸出。
* [dotnet-sln](dotnet-sln.md)
  * 要在方案檔中新增、移除及列出專案的選項。
* 專案修改命令
  * 參考 - 新增、移除及列出專案對專案參考。
    * [dotnet-add reference](dotnet-add-reference.md)
    * [dotnet-remove reference](dotnet-remove-reference.md)
    * [dotnet-list reference](dotnet-list-reference.md)
  * 套件 - 新增及移除專案的 NuGet 套件。
    * [dotnet-add package](dotnet-add-package.md)
    * [dotnet-remove package](dotnet-remove-package.md)

## <a name="examples"></a>範例

初始化可編譯和執行的範例 .NET Core 主控台應用程式：

`dotnet new console`

還原所指定應用程式的相依性：

`dotnet restore`

建置所指定目錄中的專案和其相依性：

`dotnet build`

執行名為 `myapp.dll` 的可攜式應用程式：`dotnet myapp.dll`

## <a name="environment"></a>環境

`DOTNET_PACKAGES`

主要套件快取。 如果未設定，會預設為 $HOME/.nuget/packages (在 Unix 上) 或 %HOME%\NuGet\Packages (在 Windows 上)。

`DOTNET_SERVICING`

指定載入執行階段時，共用主機所使用的服務索引位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。 `true` 選擇遙測功能 (接受值 true、1 或 yes)；否則為 `false` (接受值 false、0 或 no)。 如果未設定，則預設為 `false`，亦即，開啟遙測功能。
