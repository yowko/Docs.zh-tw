---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503711"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>描述

`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。

## <a name="arguments"></a>引數

* **`PROJECT | SOLUTION`**

  指定要用來列出參考的專案或解決方案檔。 如果未指定，命令會在目前的目錄中搜尋專案檔。

## <a name="options"></a>選項。

* **`-h|--help`**

  印出命令的簡短說明。

## <a name="examples"></a>範例

* 列出指定專案的專案參考：

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* 列出目前目錄中專案的專案參考：

  ```dotnetcli
  dotnet list reference
  ```
