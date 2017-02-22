---
title: "dotnet-pack 命令 | Microsoft Docs"
description: "dotnet-pack 命令會建立 .NET Core 專案的 NuGet 套件。"
keywords: "dotnet-pack, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8b4b8cef-f56c-4a10-aa01-fde8bfaae53e
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: d439dc83cc4538b44634197f3dce1bf7ad2ad6c7

---

#<a name="dotnet-pack"></a>dotnet-pack

> [!WARNING]
> 本主題適用於 .NET Core 工具 Preview 2。 .NET Core 工具 RC4 版本，請參閱 [dotnet-pack (.NET Core 工具 RC4)](../preview3/tools/dotnet-pack.md) 主題。

## <a name="name"></a>名稱

`dotnet-pack` - 將程式碼封裝到 NuGet 套件。

## <a name="synopsis"></a>概要

`dotnet pack [--help] [--output]  
    [--no-build] [--build-base-path]  
    [--configuration]  [--version-suffix]
    [project]`  

## <a name="description"></a>描述

`dotnet pack` 命令會建置專案，並建立 NuGet 套件。 這項作業的結果是兩個具有 `nupkg` 擴充功能的套件。 其中一個套件包含程式碼，另一個套件則包含偵錯符號。 

正在封裝之專案的 NuGet 相依性會新增至 nuspec 檔案，因此可以在安裝套件時進行解析。 專案對專案參考不會封裝到專案內。 目前，如果您有專案對專案相依性，則一個專案需要有一個套件。

`dotnet pack` 預設會先建置專案。 如果您想要避免這種情況，請傳遞 `--no-build` 選項。 例如，這可能適用於您知道先前剛建立程式碼的持續整合 (CI) 組建案例。 

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`[project]` 
    
要封裝的專案。 它可以是 [project.json](project-json.md) 檔案或目錄的路徑。 省略時，將預設為目前的目錄。 

`-o|--output <OUTPUT_DIRECTORY>`

將已建置的套件放置在指定的目錄中。 

`--no-build`

請不要在封裝之前建置專案。 

`--build-base-path`

將暫存的組建成品放在指定的目錄中。 它們預設會移至目前目錄中的 `obj` 目錄。 

`-c|--configuration <Debug|Release>`

要在建置專案時使用的組態。 如果未指定，將預設為 `Debug`。

`--version-suffix`

使用指定的字串，更新 `-*` 套件版本尾碼中的星號。

## <a name="examples"></a>範例

封裝目前目錄中的專案：

`dotnet pack`

封裝 app1 專案：

`dotnet pack ~/projects/app1/project.json`
    
封裝目前目錄中的專案，並將產生的套件放置到指定的資料夾中：

`dotnet pack --output nupkgs`

將目前目錄中的專案封裝到指定的資料夾，並略過建置步驟︰

`dotnet pack --no-build --output nupkgs`

封裝目前的專案，並使用指定的尾碼來更新產生的套件版本。 例如，版本 `1.0.0-*` 將會更新為 `1.0.0-ci-1234`。

`dotnet pack --version-suffix "ci-1234"`


<!--HONumber=Feb17_HO2-->


