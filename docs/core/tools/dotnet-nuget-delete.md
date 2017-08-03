---
title: "dotnet-nuget-delete 命令 - .NET Core CLI"
description: "dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。"
keywords: "dotnet-nuget-delete, CLI, CLI 命令, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ce6886f2f4cc8cc633cfc61215fe17550f746c91
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-nuget-delete"></a>dotnet-nuget delete

## <a name="name"></a>名稱

`dotnet-nuget-delete` - 從伺服器刪除或取消列出套件。

## <a name="synopsis"></a>概要

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a>說明

`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。 對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。

## <a name="arguments"></a>引數

`PACKAGE_NAME`

要刪除的套件。

`PACKAGE_VERSION`

要刪除的套件版本。

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

## <a name="examples"></a>範例

刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`

