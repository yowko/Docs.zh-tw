---
title: dotnet remove package 命令 - .NET Core CLI
description: dotnet remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 6a18be1a853119be245623e8fa0a0e44ed819e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-remove-package"></a>dotnet remove package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet remove package` - 從專案檔中移除套件參考。

## <a name="synopsis"></a>概要

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>描述

`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。

## <a name="arguments"></a>引數

`PROJECT`

指定專案檔。 如果未指定，命令會在目前的目錄中搜尋一個方案檔。

`PACKAGE_NAME`

要移除的套件參考。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

## <a name="examples"></a>範例

從目前目錄中的專案移除 `Newtonsoft.Json` NuGet 套件：

`dotnet remove package Newtonsoft.Json`
