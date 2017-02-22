---
title: "dotnet-publish 命令 | Microsoft Docs"
description: "dotnet-publish 命令會將 .NET Core 專案發行到目錄中。"
keywords: "dotnet-publish, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 0d222382640fc239760f8f51c69f1f306674d7ca

---

#<a name="dotnet-publish-net-core-tools-rc4"></a>dotnet-publish (.NET Core 工具 RC4)

> [!WARNING]
> 本主題適用於 .NET Core 工具 RC4。 .NET Core 工具 Preview 2 版本，請參閱 [dotnet-publish](../../tools/dotnet-publish.md) 主題。

## <a name="name"></a>名稱

`dotnet-publish` - 將應用程式及其所有相依性封裝到資料夾，以準備進行發行。

## <a name="synopsis"></a>概要

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--output]  
    [--version-suffix] [--configuration]`

## <a name="description"></a>說明

`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 

根據可攜式應用程式的類型，產生的目錄將會包含下列各項︰

1. *架構相依部署*：應用程式的中繼語言 (IL) 程式碼和應用程式的所有受管理相依性。
2. *自封式部署*：與上面相同，並加上目標平台的整個執行階段。

如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)主題。

## <a name="options"></a>選項

`[project]` 

要發行的專案，如果未指定 `[project]`，則預設為目前目錄。 

`-h|--help`

印出命令的簡短說明。  

`-f|--framework <FRAMEWORK>`

發行所指定架構識別項 (FID) 的應用程式。 

`-r|--runtime <RUNTIME_IDENTIFIER>`

發行所指定執行階段的應用程式。 如需您可以使用的執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../../rid-catalog.md)。

`-o|--output <OUTPUT_PATH>`

指定在其中放置目錄的路徑。 如果未指定，可攜式應用程式將預設為 *_./bin/[configuration]/[framework]/_*，獨立部署則將預設為 *_./bin/[configuration]/[framework]/[runtime]_*。

`--version-suffix [VERSION_SUFFIX]`

定義專案檔的 version 欄位中應該取代的 `*`。

`-c|--configuration [Debug|Release]`

要在發行時使用的組態。 預設值是 `Debug`。

## <a name="examples"></a>範例

發行應用程式。

`dotnet publish`

使用指定的專案檔發行應用程式

`dotnet publish ~/projects/app1/app1.csproj`
    
使用 `netcoreapp1.0` 架構來發行目前應用程式：

`dotnet publish --framework netcoreapp1.0`
    
使用 `netcoreapp1.0` 架構和 `OS X 10.10` 的執行階段來發行目前應用程式 (這個 RID 必須存在於專案檔中)。

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>請參閱
* [架構](../../../standard/frameworks.md)
* [執行階段識別項 (RID) 目錄](../../rid-catalog.md)



<!--HONumber=Feb17_HO2-->


