---
title: "dotnet-publish 命令 | Microsoft Docs"
description: "dotnet-publish 命令會將 .NET Core 專案發行到目錄中。"
keywords: "dotnet-publish, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 78487673d8fa07286605fb806f30083747b17386
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>名稱

`dotnet-publish` - 將應用程式及其所有相依性封裝到資料夾，以準備進行發行。

## <a name="synopsis"></a>概要

```
dotnet publish [project] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity]
dotnet publish [-h|--help]
```

## <a name="description"></a>說明

`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 輸出會包含下列內容：

1. 組件中的中繼語言 (IL) 程式碼，副檔名為 `*.dll`。
2. *deps.json* 檔案，其中包含專案的所有相依性。 
3. *Runtime.config.json* 檔案，指定應用程式預期的共用執行階段，以及執行階段的其他組態選項 (例如記憶體回收類型)。
4. 應用程式的所有相依性。 這些相依性會從 NuGet 快取複製到輸出資料夾。 

`dotnet publish` 命令的輸出已準備好部署到遠端電腦開始執行，這是準備將應用程式部署到另一部電腦 (例如伺服器) 開始執行之唯一正式支援的方法。 根據專案指定的部署類型，遠端電腦上必須已安裝 .NET Core 共用執行階段。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)主題。

## <a name="arguments"></a>引數

`project` 

要發行的專案，如果未指定 `project`，則預設為目前目錄。 

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-f|--framework <FRAMEWORK>`

發行所指定目標架構的應用程式。 必須在專案檔中指定此目標架構。

`-r|--runtime <RUNTIME_IDENTIFIER>`

發行所指定執行階段的應用程式。 建立[獨立性部署](../deploying/index.md#self-contained-deployments-scd)時會使用此選項。 如需您可以使用的執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 預設值為發行[架構相依應用程式](../deploying/index.md#framework-dependent-deployments-fdd)。

`-o|--output <OUTPUT_PATH>`

指定在其中放置目錄的路徑。 如果未指定，可攜式應用程式將預設為 *_./bin/[configuration]/[framework]/_*，獨立部署則將預設為 *_./bin/[configuration]/[framework]/[runtime]_*。

`-c|--configuration {Debug|Release}`

要在建置專案時使用的組態。 預設值是 `Debug`。

`--version-suffix <VERSION_SUFFIX>`

定義專案檔的 version 欄位中應該取代的 `*`。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

發行目前目錄中找到的專案：

`dotnet publish`

使用指定的專案檔發行應用程式：

`dotnet publish ~/projects/app1/app1.csproj`
    
使用 `netcoreapp1.1` 架構發行目前目錄中找到的專案：

`dotnet publish --framework netcoreapp1.1`
    
使用 `netcoreapp1.1` 架構和 `OS X 10.10` 的執行階段來發行目前應用程式 (這個 RID 必須存在於專案檔中)。

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a>請參閱
* [架構](../../standard/frameworks.md)
* [執行階段識別項 (RID) 目錄](../rid-catalog.md)
