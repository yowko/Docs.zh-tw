---
title: "dotnet-list reference 命令 - .NET Core CLI | Microsoft Docs"
description: "dotnet-list reference 命令提供方便的選項，以列出專案對專案參考。"
keywords: "dotnet-list, CLI, CLI 命令, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: fdaf2a6f66801be68507ccabe7e0f2fea5433e65
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-list-reference"></a>dotnet-list reference

## <a name="name"></a>名稱

`dotnet-list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>說明

`dotnet list reference` 命令提供方便的選項，以列出指定專案的專案參考。

## <a name="arguments"></a>引數

`PROJECT`

指定要用於列出參考的專案檔。 如果未指定，命令會在目前的目錄中搜尋專案檔。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

## <a name="examples"></a>範例

列出指定專案的專案參考：

`dotnet list app/app.csproj reference`

列出目前目錄中專案的專案參考：

`dotnet list reference`

