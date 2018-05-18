---
title: dotnet remove reference 命令 - .NET Core CLI
description: dotnet remove reference 命令提供方便的選項，以移除專案對專案參考。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 209f1ad62221e8a80efa161354a2c074d74b7c5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet remove reference` - 移除專案對專案參考。

## <a name="synopsis"></a>概要

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>描述

`dotnet remove reference` 命令提供方便的選項，以從專案中移除專案參考。

## <a name="arguments"></a>引數

`PROJECT`

目標專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

`PROJECT_REFERENCES`

要移除的專案對專案 (P2P) 參考。 您可以指定一或多個專案。 以 Unix/Linux 為基礎的終端機上支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-f|--framework <FRAMEWORK>`

只有在以特定[架構](../../standard/frameworks.md)為目標時，才能移除參考。

## <a name="examples"></a>範例

從指定的專案中移除專案參考：

`dotnet remove app/app.csproj reference lib/lib.csproj`

從目前目錄中的專案移除多個專案參考：

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

在 Unix/Linux 上使用 Glob 模式移除多個專案參考︰

`dotnet remove app/app.csproj reference **/*.csproj`
