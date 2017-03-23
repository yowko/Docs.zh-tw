---
title: "dotnet-nuget-delete 命令 | Microsoft Docs"
description: "dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。"
keywords: "dotnet-nuget-delete, CLI, CLI 命令, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 2ce157e3f32f3e899245e38bb4520b17be3e0b32
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-nuget-delete"></a>dotnet-nuget-delete

## <a name="name"></a>名稱

`dotnet-nuget-delete` - 從伺服器刪除或取消列出套件。 

## <a name="synopsis"></a>概要

```
dotnet nuget delete [<package_name> <package_version>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output]
dotnet nuget delete [-h|--help]
```

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

## <a name="examples"></a>範例

刪除 MyPackage 套件 1.0 版：

`dotnet nuget delete MyPackage 1.0` 

刪除 MyPackage 套件 1.0 版，不提示使用者輸入認證或其他輸入：

`dotnet nuget delete MyPackage 1.0 --non-interactive`

