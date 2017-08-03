---
title: "dotnet-clean 命令 - .NET Core CLI"
description: "dotnet-clean 命令會清除目前的目錄。"
keywords: "dotnet-clean, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 10222781d5bff596d1b7883bc73097758e878235
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-clean"></a>dotnet-clean

## <a name="name"></a>名稱

`dotnet-clean` - 清除專案的輸出。 

## <a name="synopsis"></a>概要

`dotnet clean [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>描述

`dotnet clean` 命令會清除前一個組建的輸出。 它會實作為 [MSBuild 目標](/visualstudio/msbuild/msbuild-targets)，因此命令在執行的時候會評估專案。 只會清除在建置期間建立的輸出。 中繼 (*obj*) 和最後輸出 (*bin*) 這兩個資料夾都會清除。

## <a name="arguments"></a>引數

`PROJECT`

要清除的 MSBuild 專案。 如果未指定專案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 的檔案，並使用該檔案。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-o|--output <OUTPUT_DIRECTORY>`

在其中放置建置輸出的目錄。 如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。

`-f|--framework <FRAMEWORK>`

在建置時間指定的[架構](../../standard/frameworks.md)。 架構必須定義於[專案檔](csproj.md)中。 如果在建置階段指定架構，則您必須在清除時指定該架構。

`-c|--configuration <CONFIGURATION>`

定義組態。 如果省略，會預設為 `Debug`。 如果在建置階段指定此屬性，清除時才需要使用它。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的層級為 q[uiet]、m[inimal]、n[ormal]、d[etailed] 和 diag[nostic]。

## <a name="examples"></a>範例

清除專案的預設組建︰

`dotnet clean`

清除使用發行組態來建置的專案︰

`dotnet clean --configuration Release`

