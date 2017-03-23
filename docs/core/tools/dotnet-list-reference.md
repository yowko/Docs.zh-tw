---
title: "dotnet-list reference 命令 | Microsoft Docs"
description: "dotnet-list reference 命令提供方便的選項，以列出專案對專案參考。"
keywords: "dotnet-list, CLI, CLI 命令, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: e95aa43bfed78d72ef1ea5f3883ae64e06ffaa99
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-list-reference"></a>dotnet-list reference

## <a name="name"></a>名稱

`dotnet-list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

```
dotnet list [project] reference
dotnet list reference [-h|--help]
```

## <a name="description"></a>說明

`dotnet list reference` 命令提供方便的選項，以列出指定專案的專案參考。

## <a name="arguments"></a>引數

`project`

要列出參考的專案檔。 如果未指定，命令會在目前的目錄中搜尋一個方案檔。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

## <a name="examples"></a>範例

列出指定專案的專案參考：

`dotnet list app/app.csproj reference`

列出目前目錄中專案的專案參考：

`dotnet list reference`

