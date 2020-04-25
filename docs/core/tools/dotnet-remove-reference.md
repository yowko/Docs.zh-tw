---
title: dotnet remove reference 命令
description: dotnet remove reference 命令提供方便的選項，以移除專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158329"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet remove reference`-移除專案對專案（P2P）參考。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a>描述

`dotnet remove reference` 命令提供方便的選項，以從專案中移除專案參考。

## <a name="arguments"></a>引數

`PROJECT`

目標專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

`PROJECT_REFERENCES`

要移除的專案對專案 (P2P) 參考。 您可以指定一或多個專案。 以 Unix/Linux 為基礎的終端機上支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。

## <a name="options"></a>選項。

- **`-h|--help`**

  印出命令的簡短說明。

- **`-f|--framework <FRAMEWORK>`**

  只有在以使用 TFM 格式的特定[架構](../../standard/frameworks.md)為目標時，才會移除參考。

## <a name="examples"></a>範例

- 從指定的專案中移除專案參考：

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- 從目前目錄中的專案移除多個專案參考：

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- 在 Unix/Linux 上使用 Glob 模式移除多個專案參考︰

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
