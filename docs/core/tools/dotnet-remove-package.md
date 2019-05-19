---
title: dotnet remove package 命令
description: dotnet remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。
ms.date: 05/29/2018
ms.openlocfilehash: cbdeacff78ef20c9a73010e10a771a724b23792e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632440"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet remove package` - 從專案檔中移除套件參考。

## <a name="synopsis"></a>概要

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>說明

`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。

## <a name="arguments"></a>引數

`PROJECT`

指定專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

`PACKAGE_NAME`

要移除的套件參考。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

## <a name="examples"></a>範例

從目前目錄中的專案移除 `Newtonsoft.Json` NuGet 套件：

`dotnet remove package Newtonsoft.Json`
