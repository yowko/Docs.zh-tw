---
title: "dotnet-remove reference 命令 | Microsoft Docs"
description: "dotnet-remove reference 命令提供方便的選項，以移除專案對專案參考。"
keywords: "dotnet-remove, CLI, CLI 命令, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 889c6b7e-a313-40b1-9fd3-6a6f4c52f1d0
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 1f1a364b703c6b83a9b21ee420d62411bf9cd3ec
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-remove-reference"></a>dotnet-remove reference

## <a name="name"></a>名稱

`dotnet-remove reference` - 移除專案對專案參考。

## <a name="synopsis"></a>概要

```
dotnet remove [project] reference [-f|--framework] <project_references>
dotnet remove reference [-h|--help]
```

## <a name="description"></a>說明

`dotnet remove reference` 命令提供方便的選項，以從專案中移除專案參考。

## <a name="arguments"></a>引數

`project`

要處理的專案檔。 如果未指定，命令會在目前的目錄中搜尋一個方案檔。

`project_references`

要移除的專案對專案參考。 您可以指定一或多個專案。 Unix/Linux 型終端機上支援 Glob 模式。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-f|--framework <FRAMEWORK>`

只有在以特定架構為目標時，才能移除參考。

## <a name="examples"></a>範例

從指定的專案中移除專案參考：

`dotnet remove app/app.csproj reference lib/lib.csproj`

從目前目錄中的專案移除多個專案參考：

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

使用萬用字元模式移除多個專案參考：

`dotnet remove app/app.csproj reference **/*.csproj`
