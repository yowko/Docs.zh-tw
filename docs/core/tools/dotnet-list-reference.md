---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421835"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**本主題適用於：✓** .NET Core 1.x SDK 和更新版本

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>名稱

`dotnet list reference` - 列出專案對專案參考。

## <a name="synopsis"></a>概要

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>說明

`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。

## <a name="arguments"></a>引數

* **`PROJECT | SOLUTION`**

  指定要用來列出參考的專案或解決方案檔。 如果未指定，命令會在目前的目錄中搜尋專案檔。

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
