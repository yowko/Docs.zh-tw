---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 12/03/2018
ms.openlocfilehash: c0b88c4a0af4469d7ddc9e0a9368bb1b2d9d20b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632402"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>說明

`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。

## <a name="arguments"></a>引數

* **`PROJECT`**

  指定要用於列出參考的專案檔。 如果未指定，命令會在目前的目錄中搜尋專案檔。

## <a name="options"></a>選項

* **`-h|--help`**

  印出命令的簡短說明。

## <a name="examples"></a>範例

* 列出指定專案的專案參考：

  ```console
  dotnet list app/app.csproj reference
  ```

* 列出目前目錄中專案的專案參考：

  ```console
  dotnet list reference
  ```
