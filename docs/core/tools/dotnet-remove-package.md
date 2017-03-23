---
title: "dotnet-remove package 命令 | Microsoft Docs"
description: "dotnet-remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。"
keywords: "dotnet-remove, CLI, CLI 命令, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2fcc8d37-16b3-4581-8038-832160e72d36
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 87c80ad193df9cc3e0feabc41bb58f1d8dda23cd
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-remove-package"></a>dotnet-remove package

## <a name="name"></a>名稱

`dotnet-remove package` - 從專案檔中移除套件參考。

## <a name="synopsis"></a>概要

```
dotnet remove [project] package <package_name>
dotnet remove package [-h|--help]
```

## <a name="description"></a>描述

`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。

## <a name="arguments"></a>引數

`project`

要處理的專案檔。 如果未指定，命令會在目前的目錄中搜尋一個方案檔。

`package_name`

要移除的套件參考。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

## <a name="examples"></a>範例

從目前目錄中的專案移除 `Newtonsoft.Json` NuGet 套件：

`dotnet remove package Newtonsoft.Json`
