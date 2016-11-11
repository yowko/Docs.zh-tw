---
title: "dotnet-publish 命令 | .NET Core SDK"
description: "dotnet-publish 命令會將 .NET Core 專案發行到目錄中。"
keywords: "dotnet-publish, CLI, CLI 命令, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8a7e1c52-5c57-4bf5-abad-727450ebeefd
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 2b00a2c6da73c2252997b63aca8fc475cac8999f

---

#<a name="dotnetpublish"></a>dotnet-publish

## <a name="name"></a>Name

`dotnet-publish` - 將應用程式及其所有相依性封裝到資料夾，以準備進行發行

## <a name="synopsis"></a>概要

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--build-base-path] [--output]  
    [--version-suffix] [--configuration] [--native-subdirectory] [--no-build]`

## <a name="description"></a>說明

`dotnet publish` 會編譯應用程式，並透過它在 [project.json](project-json.md) 檔案中所指定的相依性進行讀取，然後將產生的一組檔案發行到目錄中。 

根據可攜式應用程式的類型，產生的目錄將會包含下列各項︰

1. *可攜式應用程式* - 應用程式的中繼語言 (IL) 程式碼和所有應用程式的受管理相依性。
    * *具有原生相依性的可攜式應用程式* - 與上述相同，並且具有每個原生相依性的所支援平台的子目錄。 
2. *獨立應用程式* - 與上述相同，並加上目標平台的整個執行階段。

如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)主題。

## <a name="options"></a>選項

`[project]` 

要發行的專案，如果未指定 `[project]`，則預設為目前目錄。 這個值可以是 [project.json](project-json.md) 檔案或包含 [project.json](project-json.md) 檔案之專案目錄的路徑。 如果找不到 [project.json](project-json.md) 檔案，則 `dotnet publish` 會擲回錯誤。 

`-h|--help`

印出命令的簡短說明。  

`-f|--framework <FRAMEWORK>`

發行所指定架構識別項 (FID) 的應用程式。 如果未指定，會從 [project.json](project-json.md#frameworks) 讀取 FID。 如果找不到有效的架構，則命令會擲回錯誤。 如果找到多個有效的架構，則命令會針對所有有效的架構發行。 

`-r|--runtime <RUNTIME_IDENTIFIER>`

發行所指定執行階段的應用程式。 如需您可以使用的執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

`-b|--build-base-path <OUTPUT_DIRECTORY>`

在其中放置暫時輸出的目錄。

`-o|--output <OUTPUT_PATH>`

指定在其中放置目錄的路徑。 如果未指定，可攜式應用程式將預設為 *_./bin/[configuration]/[framework]/_*，獨立部署則將預設為 *_./bin/[configuration]/[framework]/[runtime]_*。

`--version-suffix [VERSION_SUFFIX]`

定義 project.json 檔案的 version 欄位中應該取代的 `*`。

`-c|--configuration [Debug|Release]`

要在發行時使用的組態。 預設值是 `Debug`。

`[--native-subdirectory]` 要在輸出中包含原生相依性套件資產中子目錄的暫時機制。 

`[--no-build]`請不要在發行之前建置專案。

## <a name="examples"></a>範例

使用 `project.json` 中所找到的架構來發行應用程式。 如果 `project.json` 包含 [runtimes](project-json.md#runtimes) 節點，請針對目前平台的 RID 發行。

`dotnet publish`

使用指定的 [project.json](project-json.md) 來發行應用程式：

`dotnet publish ~/projects/app1/project.json`
    
使用 `netcoreapp1.0` 架構來發行目前應用程式：

`dotnet publish --framework netcoreapp1.0`
    
使用 `OS X 10.10` 的 `netcoreapp1.0` 架構和執行階段來發行目前應用程式 (這個 RID 必須存在於 `project.json` [runtimes](project-json.md#runtimes) 節點中)：

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>請參閱
* [架構](../../standard/frameworks.md)
* [執行階段識別項 (RID) 目錄](../rid-catalog.md)


<!--HONumber=Nov16_HO1-->


