---
title: "dotnet-nuget-push 命令 | .NET Core SDK"
description: "dotnet-nuget-push 命令會將套件推送至伺服器並發行。"
keywords: "dotnet-nuget-push, CLI, CLI 命令, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 11/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f54d9adf-94f8-41cc-bb52-42f7ca3be6ff
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 04369a7f478cc77b6351f2fbee05d4e4ec8b19fb

---

#<a name="dotnet-nuget-push"></a>dotnet-nuget-push

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>名稱 
`dotnet-nuget-push` - 將套件推送至伺服器並發行。 

## <a name="synopsis"></a>概要

`dotnet nuget push [<package>] [--help] [--source] [--symbols-source] 
    [--timeout] [--api-key] [--symbol-api-key] [--disable-buffering] [--no-symbols] 
    [--force-english-output] [--config-file] [--verbosity]`

## <a name="description"></a>說明

`dotnet nuget push` 命令會將套件推送至伺服器並發行。 推送命令會使用在系統的 NuGet 組態檔，或是組態檔的鏈結中找到的伺服器及認證詳細資料。 如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](https://docs.nuget.org/ndocs/consume-packages/configuring-nuget-behavior)。 NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始載入任何 *nuget.config* 或 *.nuget\nuget.config*，並在目前目錄結束。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-s|--source <SOURCE>`

指定伺服器 URL。 除非在 NuGet 組態檔中設定 DefaultPushSource 設定值，否則此選項為必要。

`--symbols-source <SOURCE>`

指定符號伺服器 URL。

`-t|--timeout <TIMEOUT>`

指定推送至伺服器的逾時 (以秒為單位)。 預設為 300 秒 (5 分鐘)。 指定 0 也會提供此預設值。

`-k|--api-key <API_KEY>`

伺服器的 API 金鑰。

`--symbol-api-key <API_KEY>`

符號伺服器的 API 金鑰。

`-d|--disable-buffering`

推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。

`-n|--no-symbols`

不推送符號 (即使存在)。

`--force-english-output`

強制所有記錄的輸出採用英文。 與在非英文的電腦上產生英文輸出的彈性相同，此選項提供的跨平台一致性對於抓取記錄檔文字的自動化工具而言是非常實用的功能。

`--config-file <FILE>`

專用於此命令的 NuGet 組態檔，它會取代使用標準組態檔探索和鏈結程序找到的其他組態檔。 這個路徑可為絕對路徑或相對路徑。
如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](https://docs.nuget.org/ndocs/consume-packages/configuring-nuget-behavior)。 

`--verbosity <LEVEL>`

在輸出中顯示此詳細資料數量。 Level 可為 `normal`、`quiet` 或 `detailed`。

## <a name="examples"></a>範例

將 foo.nupkg 推送至預設推送來源，提供 API 金鑰：

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

將 foo.nupkg 推送至自訂推送來源 `http://customsource`，提供 API 金鑰：

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/` 

將 foo.nupkg 推送至預設推送來源：

`dotnet nuget push foo.nupkg` 

將 foo.symbols.nupkg 推送至預設符號來源：

`dotnet nuget push foo.symbols.nupkg`

將 foo.nupkg 推送至預設推送來源，指定 360 秒逾時：

`dotnet nuget push foo.nupkg --timeout 360`

將目前目錄中的所有 .nupkg 檔案推送至預設推送來源：

`dotnet nuget push *.nupkg`

將目前目錄中的所有.nupkg 檔案推送至預設推送來源，指定自訂組態檔 *./config/My.Config*：

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

將目前目錄中的所有 .nupkg 檔案推送至預設推送來源，並以最詳細的方式傳回命令執行結果：

`dotnet nuget push *.nupkg --verbosity detailed`



<!--HONumber=Nov16_HO3-->


