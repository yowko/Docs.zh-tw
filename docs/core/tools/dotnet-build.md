---
title: "dotnet-build 命令 | Microsoft Docs"
description: "dotnet-build 命令會建置專案和其所有相依性。"
keywords: "dotnet-build, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 17c2db54f871795c370a6475c21e36736a6b46c3
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>名稱

`dotnet-build` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

```
dotnet build [project] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity]
dotnet build [--help]
```

## <a name="description"></a>描述
`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。 這些二進位檔包括用於偵錯的符號檔 (具有 `*.pdb` 副檔名)，以及中繼語言 (IL) 中的專案程式碼 (副檔名為 `*.dll`)。 另外會產生 JSON 檔案，該檔案會列出應用程式的所有相依性 (副檔名為 `*.deps.json`)。 最後，還會產生 `runtime.config.json` 檔案。 此檔案會指定所建置之程式碼將執行的共用執行階段和版本。 

如果專案具有協力廠商相依性 (例如來自 NuGet 的程式庫)，這些相依性將會從 NuGet 快取解析，而不會透過專案的建置輸出提供。 因此，`dotnet build` 的結果尚未準備好轉移到另一部電腦開始執行。 這與 .NET Framework 的行為相反；在 .NET Framework 中，建置可執行檔專案 (應用程式) 將會產生可在任何已安裝 .NET Framework 的電腦上執行的輸出。 若要在 .NET Core 中取得類似體驗，您必須使用 [dotnet publish](dotnet-publish.md) 命令。 您可以在 [.NET Core 應用程式部署](../deploying/index.md)文件中找到詳細資訊。 

建置會要求 *assets.json* 檔案 (列出應用程式所有相依性的檔案) 確實存在，這表示您必須先執行 [`dotnet restore`](dotnet-restore.md)，才能建置專案。 缺乏資產檔案表示工具無法解析發生錯誤的參考組件。 

`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行組建和累加組建。 請參閱 [MSBuild 文件](https://docs.microsoft.com/visualstudio/msbuild/msbuild)以取得這些主題的詳細資訊。 

除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `/p`，以及用於定義記錄器的 `/l`。 您可以在 [`dotnet msbuild`](dotnet-msbuild.md) 命令文件中深入了解這些選項。 如果您想要知道何時 

專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。 下列範例顯示將產生可執行程式碼的專案： 


```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

若要產生程式庫，只要省略該屬性即可。 輸出中的主要差異在於程式庫的 IL DLL 將不會包含任何進入點，而且無法執行。 

## <a name="arguments"></a>引數

`project`

要建置的專案檔。
如果未指定專案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 `proj` 的檔案，並使用該檔案。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-o|--output <OUTPUT_DIRECTORY>`

在其中放置已建置的二進位檔的目錄。 當您指定這個選項時，也需要定義 `--framework`。

`-f|--framework <FRAMEWORK>`

針對特定架構進行編譯。 架構必須定義於[專案檔](csproj.md)中。

`-c|--configuration [Debug|Release]`

定義用來建置的組態。 如果省略，會預設為 `Debug`。

`-r|--runtime [RUNTIME_IDENTIFIER]`

要建置的目標執行階段。 如需您可以使用的執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

`--version-suffix [VERSION_SUFFIX]`

定義專案檔的 version 欄位中應該取代的 `*`。 格式遵循 NuGet 的版本指導方針。

`--no-incremental`

針對累加建置，將建置標示為不安全。 這會關閉累加編譯，並強制全新重建專案相依性圖形。

`--no-dependencies`

忽略專案對專案參考，並且只會建置指定要建置的根專案。

`-v|--verbosity`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

建置專案和其相依性：

`dotnet build`

使用發行組態來建置專案和其相依性︰

`dotnet build --configuration Release`

針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 16.04)：

`dotnet build --runtime ubuntu.16.04-x64`
