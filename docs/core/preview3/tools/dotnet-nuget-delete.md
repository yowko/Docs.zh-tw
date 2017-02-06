---
title: "dotnet-nuget-delete 命令 | Microsoft Docs"
description: "dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。"
keywords: "dotnet-nuget-delete, CLI, CLI 命令, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 11/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 787b1427b1064943570cbc361042ab2f20d11088

---

#<a name="dotnet-nuget-delete"></a>dotnet-nuget-delete

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>名稱 
`dotnet-nuget-delete` - 從伺服器刪除或取消列出套件。 

## <a name="synopsis"></a>概要

`dotnet nuget delete [<package_name> <package_version>] 
    [--help] [--source] [--non-interactive] 
    [--api-key] [--force-english-output] [--verbosity] [--config-file]`

## <a name="description"></a>說明

`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。 對於 NuGet.org，該動作是取消列出套件。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-s|--source <SOURCE>`

指定伺服器 URL。 支援的 nuget.org URL 包括 `http://www.nuget.org`、`http://www.nuget.org/api/v3` 和 `http://www.nuget.org/api/v2/package`。 對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。

`--non-interactive`

不提示使用者輸入或確認。

`-k|--api-key <API_KEY>`

伺服器的 API 金鑰。

`--force-english-output`

強制命令列輸出採用英文。

`--verbosity <LEVEL>`

在輸出中顯示此詳細資料數量。 Level 可為 `normal`、`quiet` 或 `detailed`。

`--config-file <FILE>`

專用於此命令的 NuGet 組態檔，它會取代使用標準組態檔探索和鏈結程序找到的其他組態檔。 這個路徑可為絕對路徑或相對路徑。
如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

## <a name="examples"></a>範例

刪除 MyPackage 套件 1.0 版：

`dotnet nuget delete MyPackage 1.0` 

刪除 MyPackage 套件 1.0 版，不提示使用者輸入認證或其他輸入：

`dotnet nuget delete MyPackage 1.0 --non-interactive`

刪除 MyPackage 套件 1.0 版，指定自訂組態檔 *./config/My.Config*：

`dotnet nuget delete MyPackage 1.0 --config-file ./config/My.Config`

刪除 MyPackage 套件 1.0 版，並以最詳細的方式傳回命令執行結果：

`dotnet nuget delete MyPackage 1.0 --verbosity detailed`



<!--HONumber=Jan17_HO3-->


