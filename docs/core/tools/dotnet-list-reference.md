---
title: dotnet list reference 命令 - .NET Core CLI
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 946d3d523443fbe673b95dba95dbca327fde1699
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>描述

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
