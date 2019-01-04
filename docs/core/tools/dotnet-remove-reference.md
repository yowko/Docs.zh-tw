---
title: dotnet remove reference 命令
description: dotnet remove reference 命令提供方便的選項，以移除專案對專案參考。
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170609"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet remove reference` - 移除專案對專案參考。

## <a name="synopsis"></a>概要

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>說明

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
