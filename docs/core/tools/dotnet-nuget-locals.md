---
title: "dotnet-nuget-locals 命令 - .NET Core CLI | Microsoft Docs"
description: "dotnet-nuget-locals 命令會清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。"
keywords: "dotnet-nuget-locals, CLI, CLI 命令, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: d0acfaa6ff1a11f49a0d3751b675ea94bd6ae3a3
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-nuget-locals"></a>dotnet-nuget locals

## <a name="name"></a>名稱

`dotnet-nuget locals` - 清除或列出本機 NuGet 資源。 

## <a name="synopsis"></a>概要

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a>說明

`dotnet nuget locals` 命令會清除或列出 http-request 快取、暫時快取，或整部電腦全域套件資料夾中的本機 NuGet 資源。

## <a name="arguments"></a>引數

`CACHE_LOCATION`

下列其中一個值：

`all`

指出指定的作業會套用至所有快取類型：http-request 快取、全域套件快取和暫時快取。

`http-cache`

指出指定的作業只套用至 http-request 快取。 其他快取位置不受影響。

`global-packages`

指出指定的作業只套用至全域套件快取。 其他快取位置不受影響。

`temp`

指出指定的作業只套用至暫時快取。 其他快取位置不受影響。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-c|--clear`

清除選項會針對指定的快取類型執行清除作業。 系統會以遞迴方式刪除快取目錄的內容。 執行的使用者/群組必須具有快取目錄中檔案的權限。 如果沒有權限，則會顯示錯誤，指出尚未清除的檔案/資料夾。

`-l|--list`

list 選項是用來顯示指定之快取類型的位置。 

`--force-english-output`

強制命令列輸出採用英文。

## <a name="examples"></a>範例

顯示所有本機快取目錄的路徑 (http-cache 目錄、global-packages 快取目錄及暫時快取目錄)：

`dotnet nuget locals –l all`

顯示本機 http-cache 目錄的路徑：

`dotnet nuget locals --list http-cache`

清除所有本機快取目錄的所有檔案 (http-cache 目錄、global-packages 快取目錄及暫時快取目錄)：

`dotnet nuget locals --clear all`

清除本機 global-packages 快取目錄中的所有檔案：

`dotnet nuget locals -c global-packages`

清除本機暫時快取目錄中的所有檔案：

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>疑難排解

如需使用 `dotnet nuget locals` 命令時常見的問題與錯誤資訊，請參閱[管理 NuGet 快取](https://docs.microsoft.com/nuget/consume-packages/managing-the-nuget-cache)。

