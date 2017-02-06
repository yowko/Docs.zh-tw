---
title: "dotnet-nuget-locals 命令 | Microsoft Docs"
description: "dotnet-nuget-locals 命令會清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。"
keywords: "dotnet-nuget-locals, CLI, CLI 命令, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 11/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 5f8c3be091b515553eb0db0ccfaee6bb8c620cff

---

#<a name="dotnet-nuget-locals"></a>dotnet-nuget-locals

[!INCLUDE[preview-warning](../../../includes/warning.md)] 

## <a name="name"></a>名稱 
`dotnet-nuget-locals` - 清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。 

## <a name="synopsis"></a>概要

`dotnet nuget locals <cache_location> [--clear|--list] [--help] [--force-english-output]`

其中 `<cache_location>` 是下列其中一個值：`all`、`http-cache`、`packages-cache`、`global-packages` 或 `temp`。

## <a name="description"></a>說明

`dotnet nuget locals` 命令會清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。

## <a name="arguments"></a>引數

`all`

指出指定的作業應該套用至所有快取類型，也就是 http-request 快取、全域套件快取和暫時快取。

`http-cache`

指出指定的作業應該只套用至 http-request 快取。 其他快取位置不受影響。

`global-packages`

指出指定的作業應該只套用至全域套件快取。 其他快取位置不受影響。

`temp`

指出指定的作業應該只套用至暫時快取。 其他快取位置不受影響。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-c|--clear`

清除選項是用來針對指定的快取類型執行清除作業。 系統會以遞迴方式刪除快取目錄的內容。 執行的使用者/群組應該具有快取目錄內檔案的權限，才能成功進行作業。 如果沒有權限，則會顯示錯誤，指出未清除的檔案/資料夾。

`-l|--list`

list 選項是用來顯示指定之快取類型的位置。 

`--force-english-output`

強制命令列輸出採用英文。

## <a name="examples"></a>範例

顯示所有本機快取目錄的路徑，也就是 http-cache 目錄、global-packages 快取目錄及暫時快取目錄。

`dotnet nuget locals –l all`

顯示本機 http-cache 目錄的路徑：

`dotnet nuget locals --list http-cache`

清除所有本機快取目錄中的所有檔案，也就是 http-cache 目錄、global-packages 快取目錄及暫時快取目錄。

`dotnet nuget locals --clear all`

清除本機 global-packages 快取目錄中的所有檔案：

`dotnet nuget locals -c global-packages`

清除本機暫時快取目錄中的所有檔案：

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>疑難排解

如需使用 `dotnet-nuget-locals` 命令時常見的問題與錯誤資訊，請參閱[管理 NuGet 快取](https://docs.microsoft.com/nuget/consume-packages/managing-the-nuget-cache)。



<!--HONumber=Jan17_HO3-->


