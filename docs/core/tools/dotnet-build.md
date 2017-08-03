---
title: "dotnet-build 命令 - .NET Core CLI"
description: "dotnet-build 命令會建置專案和其所有相依性。"
keywords: "dotnet-build, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2006b15978f384e53e43a0a2562e81d10582abd
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>名稱

`dotnet-build` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

`dotnet build [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>描述

`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。 二進位檔將專案程式碼包含在副檔名為 *.dll* 的中繼語言 (IL) 檔案中，以及副檔名為 *.pdb* 且用於偵錯的符號檔。 產生相依性的 JSON 檔案 (*\*.deps.json*)，其中列出應用程式的相依性。 產生 *\*.runtimeconfig.json* 檔案，其中指定應用程式的共用執行階段及其版本。

如果專案對於第三方有相依性 (例如來自 NuGet 的程式庫)，這些相依性將會從 NuGet 快取解析，而不會透過專案的建置輸出提供。 因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。 這與 .NET Framework 的行為相反。在 .NET Framework 中，建置可執行檔專案 (應用程式) 所產生的輸出，可在任何已安裝 .NET Framework 的電腦上執行。 若要在 .NET Core 中擁有類似體驗，您可以使用 [dotnet publish](dotnet-publish.md) 命令。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。 

建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。 檔案會在您建置專案前執行 [`dotnet restore`](dotnet-restore.md) 的時候建立。 如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。

`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。 如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。 

除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `/p`，以及用於定義記錄器的 `/l`。 請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)，以深入了解這些選項。 

專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。 下列範例顯示將產生可執行程式碼的專案：

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

若要產生程式庫，只要省略 `<OutputType>` 屬性即可。 建置輸出的主要差別在於，程式庫的 IL DLL 不包含進入點，而且無法執行。 

## <a name="arguments"></a>引數

`PROJECT`

要建置的專案檔。 如果未指定專案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 的檔案，並使用該檔案。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-o|--output <OUTPUT_DIRECTORY>`

在其中放置已建置的二進位檔的目錄。 當您指定這個選項時，也需要定義 `--framework`。

`-f|--framework <FRAMEWORK>`

針對特定[架構](../../standard/frameworks.md)進行編譯。 架構必須定義於[專案檔](csproj.md)中。

`-c|--configuration <CONFIGURATION>`

定義組建組態。 如果省略，則組建組態的預設值為 `Debug`。 使用 `Release` 建置發行組態。

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

`--version-suffix <VERSION_SUFFIX>`

定義專案檔版本欄位中星號 (`*`) 的版本尾碼。 格式遵循 NuGet 的版本指導方針。

`--no-incremental`

針對累加建置，將建置標示為不安全。 這會關閉累加編譯，並強制全新重建專案的相依性關係圖。

`--no-dependencies`

忽略專案對專案 (P2P) 參考，並且只建置指定要建置的根專案。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

建置專案和其相依性：

`dotnet build`

使用發行組態來建置專案和其相依性︰

`dotnet build --configuration Release`

針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 16.04)：

`dotnet build --runtime ubuntu.16.04-x64`

