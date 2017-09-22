---
title: "dotnet nuget delete 命令 - .NET Core CLI"
description: "dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 65fe52f07ed823b4f7518c5b1f2da1f7a61b0371
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet nuget delete` - 從伺服器刪除或取消列出套件。

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
