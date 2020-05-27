---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802757"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a>描述

`dotnet list reference` 命令提供方便的選項，以列出指定專案的專案參考。

## <a name="arguments"></a>引數

* **`PROJECT`**

  要處理的專案檔。 如果未指定檔案，此命令將會在目前的目錄中搜尋一個檔案。

## <a name="options"></a>選項

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
