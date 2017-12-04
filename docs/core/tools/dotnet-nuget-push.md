---
title: "dotnet nuget push 命令 - .NET Core CLI"
description: "dotnet nuget push 命令會將套件推送至伺服器並發行。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: dc4250ab7417c9f19babdf37c556daf7c3bd6a81
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet nuget push` - 將套件推送至伺服器並發行。

## <a name="synopsis"></a>概要

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>說明

`dotnet nuget push` 命令會將套件推送至伺服器並發行。 推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。 如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。 NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。

## <a name="arguments"></a>引數

`ROOT`

指定套件和 API 金鑰的路徑，以推送套件至伺服器。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-s|--source <SOURCE>`

指定伺服器 URL。 除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。

`--symbol-source <SOURCE>`

指定符號伺服器 URL。

`-t|--timeout <TIMEOUT>`

指定推送至伺服器的逾時 (以秒為單位)。 預設為 300 秒 (5 分鐘)。 指定 0 (零秒) 會套用預設值。

`-k|--api-key <API_KEY>`

伺服器的 API 金鑰。

`--symbol-api-key <API_KEY>`

符號伺服器的 API 金鑰。

`-d|--disable-buffering`

推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。

`-n|--no-symbols`

不推送符號 (即使存在)。

`--force-english-output`

強制所有記錄的輸出採用英文。

## <a name="examples"></a>範例

若有 API 金鑰，將 *foo.nupkg* 推送至預設推送來源：

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

若有 API 金鑰，將 *foo.nupkg* 推送至自訂推送來源 `http://customsource`：

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

將 *foo.nupkg* 推送至預設推送來源：

`dotnet nuget push foo.nupkg`

將 *foo.symbols.nupkg* 推送至預設符號來源：

`dotnet nuget push foo.symbols.nupkg`

將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：

`dotnet nuget push foo.nupkg --timeout 360`

將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：

`dotnet nuget push *.nupkg`

將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源，指定自訂組態檔 *./config/My.Config*：

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源，並以最詳細的方式傳回命令執行結果：

`dotnet nuget push *.nupkg --verbosity detailed`
