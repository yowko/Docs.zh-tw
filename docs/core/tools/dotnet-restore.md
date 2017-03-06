---
title: "dotnet-restore 命令 | Microsoft Docs"
description: "了解如何使用 dotnet restore 命令來還原相依性和專案特有工具"
keywords: "dotnet-restore, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 60489b25-38de-47e6-bed1-59d9f42e2d46
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: df8174aa3252568d7112305af07e6399d96ca32f

---

#<a name="dotnet-restore"></a>dotnet-restore

> [!WARNING]
> 本主題適用於 .NET Core 工具 Preview 2。 .NET Core 工具 RC4 版本，請參閱 [dotnet-restore (.NET Core 工具 RC4)](../preview3/tools/dotnet-restore.md) 主題。

## <a name="name"></a>名稱

`dotnet-restore` - 還原專案的相依性和工具。

## <a name="synopsis"></a>概要

`dotnet restore [root] [--help] [--force-english-output] [--source]  
    [--packages] [--disable-parallel] [--fallbacksource] [--configfile] 
    [--no-cache] [--infer-runtimes] [--verbosity] [--ignore-failed-sources]`

## <a name="description"></a>描述

`dotnet restore` 命令會使用 NuGet 來還原相依性以及 [project.json](project-json.md) 檔案中所指定的專案特有工具。 預設會平行完成相依性和工具的還原。

若要還原相依性，NuGet 需要套件所在的摘要。 摘要通常是透過 NuGet.config 組態檔所提供；安裝 CLI 工具時，會出現預設摘要。 在專案目錄中建立專屬 NuGet.config 檔案，即可指定多個摘要。 在命令提示字元上，也可以根據叫用來指定摘要。 

針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。 如果未指定，則會使用預設 NuGet 套件快取。 它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中 (例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*)。

針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其 [project.json](project-json.md) 中所指定的工具相依性。 

## <a name="options"></a>選項

`[root]` 
    
 要還原的專案或專案資料夾清單。 每個值都可以是 [project.json](project-json.md) 或 [global.json](global-json.md) 檔案或資料夾的路徑。 如果指定資料夾，則還原作業會以遞迴方式搜尋所有子目錄中的 [project.json](project-json.md) 檔案，並針對每個找到的 [project.json](project-json.md) 檔案進行還原。

`-h|--help`

印出命令的簡短說明。

 `--force-english-output`

強制使用非變異英文文化特性來執行應用程式。

`-s|--source <SOURCE>`

指定要在還原作業期間使用的 NuGet 套件來源。 這會覆寫 NuGet.config 檔案中指定的所有來源。 多次指定這個選項，即可提供多個來源。

`--packages <PACKAGES_DIRECTORY]`

指定要在其中放置已還原套件的目錄。 

`--disable-parallel`

停用平行還原多個專案。 

`-f|--fallbacksource <FEED>`

指定要在還原作業中於所有其他來源都失敗時用作後援的套件來源清單。 允許所有有效的摘要格式。 多次指定這個選項，即可提供多個後援來源。

`--configfile <FILE>`

要用於還原作業的 NuGet 組態檔 (NuGet.config)。

`--no-cache`

指定不要快取套件和 HTTP 要求。

`--infer-runtimes`

允許 NuGet 推斷傳統存放庫的執行階段識別項 (RID) 的暫時選項。

`--verbosity [LEVEL]`

要使用的記錄的詳細資訊。 允許值：`Debug`、`Verbose`、`Information`、`Minimal`、`Warning` 或 `Error`。

` --ignore-failed-sources`

如果有套件符合版本需求，則只會警告有關失敗的來源。

## <a name="examples"></a>範例

還原目前目錄中專案的相依性和工具︰

`dotnet restore` 

還原在指定路徑中找到之 `app1` 專案的相依性和工具︰

`dotnet restore ~/projects/app1/project.json`
    
使用提供為後援來源的檔案路徑，還原目前目錄中專案的相依性和工具︰

`dotnet restore -f c:\packages\mypackages` 

使用提供為後援來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具︰

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

還原目前目錄中專案的相依性和工具，並且只在輸出中顯示錯誤︰

`dotnet restore --verbosity Error`


<!--HONumber=Feb17_HO2-->


