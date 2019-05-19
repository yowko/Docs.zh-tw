---
title: dotnet help 命令
description: dotnet help 命令會顯示指定命令更詳細的線上文件。
ms.date: 12/04/2018
ms.openlocfilehash: 8694494720cdb9a540754fdf79eeb99d5dbe61ef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631994"
---
# <a name="dotnet-help-reference"></a>dotnet help reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>名稱

`dotnet help` - 顯示指定命令更詳細的線上文件。

## <a name="synopsis"></a>概要

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>說明

`dotnet help` 命令會在 docs.microsoft.com 開啟參考頁面，提供指定命令的更詳細資訊。

## <a name="arguments"></a>引數

* **`COMMAND_NAME`**

  .NET Core CLI 命令的名稱。 如需有效 CLI 命令的清單，請參閱 [CLI 命令](index.md#cli-commands)。

## <a name="options"></a>選項

* **`-h|--help`**

  印出命令的簡短說明。

## <a name="examples"></a>範例

* 開啟 [dotnet new](dotnet-new.md) 命令的文件頁面：

  ```console
  dotnet help new
  ```
