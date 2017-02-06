---
title: "dotnet-restore 命令 | Microsoft Docs"
description: "了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。"
keywords: "dotnet-restore, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fd7a5769-afbe-4838-bbaf-3ae0cfcbb914
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: b2dbd39583b58c5d977d88edfc4770f6d9855ec1

---

#<a name="dotnet-restore-tooling-preview-4"></a>dotnet-restore (工具 Preview 4)

> [!WARNING]
> 此主題適用於 Visual Studio 2017 RC - .NET Core 工具 Preview 4。 .NET Core 工具 Preview 2 版本，請參閱 [dotnet-restore](../../tools/dotnet-restore.md) 主題。

## <a name="name"></a>名稱

`dotnet-restore` - 還原專案的相依性和工具。

## <a name="synopsis"></a>概要

`dotnet restore [root] [--help] [--source]  
    [--packages] [--disable-parallel] [--configfile] 
    [--no-cache] [--ignore-failed-sources] [--no-dependencies]`

## <a name="description"></a>說明

`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。 預設會平行完成相依性和工具的還原。

若要還原相依性，NuGet 需要套件所在的摘要。 摘要通常是透過 NuGet.config 組態檔所提供；安裝 CLI 工具時，會出現預設摘要。 在專案目錄中建立專屬 NuGet.config 檔案，即可指定多個摘要。 在命令提示字元上，也可以根據叫用來指定摘要。 

針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。 如果未指定，則會使用預設 NuGet 套件快取。 它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中 (例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*)。

針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。

## <a name="options"></a>選項

`[root]` 
    
要還原之專案檔的選用路徑。 

`-h|--help`

印出命令的簡短說明。

`-s|--source <SOURCE>`

指定要在還原作業期間使用的 NuGet 套件來源。 這會覆寫 NuGet.config 檔案中指定的所有來源。 多次指定這個選項，即可提供多個來源。

`--packages <PACKAGES_DIRECTORY]`

指定要在其中放置已還原套件的目錄。 

`--disable-parallel`

停用平行還原多個專案。 

`--configfile <FILE>`

要用於還原作業的 NuGet 組態檔 (NuGet.config)。

`--no-cache`

指定不要快取套件和 HTTP 要求。

` --ignore-failed-sources`

如果有套件符合版本需求，則只會警告有關失敗的來源。

`--no-dependencies`

還原具有 P2P 參考的專案時，請勿還原參考，您應該只還原根專案。 

## <a name="examples"></a>範例

還原目前目錄中專案的相依性和工具︰

`dotnet restore` 

還原在指定路徑中找到之 `app1` 專案的相依性和工具︰

`dotnet restore ~/projects/app1/app1.csproj`
    
使用提供為後援來源的檔案路徑，還原目前目錄中專案的相依性和工具︰

`dotnet restore -f c:\packages\mypackages` 

使用提供為後援來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具︰

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

還原目前目錄中專案的相依性和工具，並且只在輸出中顯示錯誤︰

`dotnet restore --verbosity Error`



<!--HONumber=Jan17_HO3-->


