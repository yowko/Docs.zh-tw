---
title: "dotnet-clean 命令 | Microsoft Docs"
description: "dotnet-clean 命令會清除目前的目錄。"
keywords: "dotnet-clean, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3c00f4616932318b5dc5d77cbdf6c645696a4226
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-clean"></a>dotnet-clean

## <a name="name"></a>名稱

`dotnet-clean` - 清除專案的輸出。 

## <a name="synopsis"></a>概要

```
dotnet clean [project] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity]
dotnet clean [--help] 
```

## <a name="description"></a>說明

`dotnet clean` 命令會清除前一個組建的輸出。 命令會當成 MSBuild 目標來實作，因此得以評估專案。 只會清除在建置期間建立的輸出。 中繼 (`obj`) 和最後輸出 (`bin`) 這兩個資料夾都會清除。 

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-o|--output <OUTPUT_DIRECTORY>`

在其中放置所建置二進位檔的目錄。 當您指定這個選項時，也需要定義 `--framework`。 如果您未在建置時間內指定此屬性，即不必指定要加以清除。

`-f|--framework <FRAMEWORK>`

在建置時間指定的架構。 如果您未在建置時間內指定此屬性，即不必指定要加以清除。 架構必須定義於[專案檔](csproj.md)中。

`-c|--configuration [Debug|Release]`

定義組建據以執行的組態。  如果省略，會預設為 `Debug`。 如果您未在建置時間內指定此屬性，即不必指定要加以清除。

`-v|--verbosity <Quiet|Minimal|Normal|Diag>`

定義詳細資訊以用於 `dotnet clean` 命令的引動過程。 詳細資訊層級是標準 [MSBuild 詳細資訊層級](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)。 

## <a name="examples"></a>範例

清除專案的預設組建︰

`dotnet clean`

清除使用發行組態來建置的專案︰

`dotnet clean --configuration Release`

