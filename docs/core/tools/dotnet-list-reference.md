---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463651"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**本文適用於:✔️** .NET Core 2.x SDK 和更高版本

## <a name="name"></a>名稱

`dotnet list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

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
