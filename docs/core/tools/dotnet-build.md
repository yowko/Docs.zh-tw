---
title: "dotnet-build 命令 | Microsoft Docs"
description: "dotnet-build 命令會建置專案和其所有相依性。"
keywords: "dotnet-build, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: bb64da75a2e7bc2d379bc1685b4187493792db78

---

#<a name="dotnet-build"></a>dotnet-build

> [!WARNING]
> 本主題適用於 .NET Core 工具 Preview 2。 .NET Core 工具 RC4 版本，請參閱 [dotnet-build (.NET Core 工具 RC4)](../preview3/tools/dotnet-build.md) 主題。

## <a name="name"></a>名稱 
`dotnet-build` - 建置專案和其所有相依性。 

## <a name="synopsis"></a>概要

`dotnet build [--help] [--output]  
    [--build-base-path] [--framework]  
    [--configuration]  [--runtime] [--version-suffix]
    [--build-profile]  [--no-incremental] [--no-dependencies]
    [<project>]`

## <a name="description"></a>描述

`dotnet build` 命令會將來源專案中的多個來源檔案和其相依性建置成二進位檔。 產生的二進位檔預設為中繼語言 (IL)，並且具有 DLL 擴充功能。 
`dotnet build` 也會放置 `\*.deps` 檔案，這個檔案概述主機執行應用程式所需的作業。  

建置需要有鎖定檔案，這表示您必須在建置程式碼之前執行 [`dotnet restore`](dotnet-restore.md)。

開始進行任何編譯之前，`build` 動詞會分析專案和其相依性來進行累加安全性檢查。
如果所有檢查都通過，則建置會繼續對專案和其相依性進行累加編譯；否則，會回復為非累加編譯。 透過設定檔旗標，使用者可以選擇接收如何改善其建置時間的其他資訊。

相依性圖形中需要編譯的所有專案都必須通過下列安全性檢查，才能累加編譯程序︰
- 不使用前置/後置編譯指令碼
- 無法從 PATH 載入編譯工具 (例如，resgen、編譯器)
- 僅使用已知的編譯器 (csc、vbc、fsc)

若要建置可執行的應用程式，而不是程式庫，您需要 project.json 檔案中的[特殊組態](project-json.md#emitentrypoint)區段：

```json
{ 
    "buildOptions": {
      "emitEntryPoint": true
    }
}
```

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-o|--output <OUTPUT_DIRECTORY>`

在其中放置已建置的二進位檔的目錄。 當您指定這個選項時，也需要定義 `--framework`。

`-b|--build-base-path <OUTPUT_DIRECTORY>`

在其中放置暫時輸出的目錄。

`-f|--framework <FRAMEWORK>`

針對特定架構進行編譯。 架構需要定義於 [project.json](project-json.md#frameworks) 檔案中。

`-c|--configuration [Debug|Release]`

定義用來建置的組態。  如果省略，會預設為 `Debug`。

`-r|--runtime <RUNTIME_IDENTIFIER>`

要建置的目標執行階段。 如需您可以使用的執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 

`--version-suffix <VERSION_SUFFIX>`

定義 [project.json](project-json.md#version) 檔案的 version 欄位中應該取代的 `*`。 格式遵循 NuGet 的版本指導方針。 

`--build-profile`

印出累加安全性檢查，而使用者需要進行解決，才能自動開啟累加編譯。

`--no-incremental`

針對累加建置，將建置標示為不安全。 這會關閉累加編譯，並強制全新重建專案相依性圖形。

`--no-dependencies`

忽略專案對專案參考，並且只會建置指定要建置的根專案。

## <a name="examples"></a>範例

建置專案和其相依性：

`dotnet build`

使用發行組態來建置專案和其相依性︰

`dotnet build --configuration Release`

針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 16.04)：

`dotnet build --runtime ubuntu.16.04-x64`


<!--HONumber=Feb17_HO2-->


