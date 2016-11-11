---
title: "dotnet 命令 | .NET Core SDK"
description: "了解 dotnet 命令 (.NET Core CLI 工具的泛型驅動程式) 和其用法。"
keywords: "dotnet, CLI, CLI 命令, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 93015521-2127-4fe9-8fce-ca79bcc4ff49
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 77c37ac3d4d0ba9ad1feac539debe40b0ee31161

---

#<a name="dotnet-command"></a>dotnet 命令

## <a name="name"></a>名稱

dotnet -- 用於執行命令列命令的泛型驅動程式

## <a name="synopsis"></a>概要

`dotnet [--version] [--verbose] [--info] [command] [arguments] [--help]`

## <a name="description"></a>說明
`dotnet` 是命令列介面 (CLI) 工具鏈的泛型驅動程式。 自行叫用，它會提供簡短使用指示。 

每個特定功能都是當成命令來實作。 若要使用這個功能，請在 `dotnet` 之後指定這個命令 (例如 [`dotnet build`](dotnet-build.md))。 這個命令後面的所有引數都是它自己的引數。 

`dotnet` 當成自己的命令的唯一時間是執行可攜式應用程式。 只在 `dotnet` 動詞後面指定可攜式應用程式 DLL，來執行應用程式。    

## <a name="options"></a>選項

`-v|--verbose`

啟用詳細資訊輸出。

`--version`

印出 CLI 工具的版本。

`--info`

印出 CLI 工具的詳細資訊 (例如目前作業系統、版本的認可 SHA 等)。 

`-h|--help`

印出命令的簡短說明。 如果只與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。  

## <a name="dotnet-commands"></a>dotnet 命令

dotnet 具有下列命令：

* [dotnet-new](dotnet-new.md)
   * 初始化 C# 或 F# 主控台應用程式專案。
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

## <a name="examples"></a>範例

初始化可編譯和執行的範例 .NET Core 主控台應用程式：

`dotnet new`

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


<!--HONumber=Nov16_HO1-->


