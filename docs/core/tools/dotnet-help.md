---
title: dotnet help 命令
description: dotnet help 命令會顯示指定命令更詳細的線上文件。
ms.date: 02/14/2020
ms.openlocfilehash: d583142edabb24df972bdf9a06dbfe04688f9d97
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634464"
---
# <a name="dotnet-help-reference"></a>dotnet help reference

本文 **適用于：** ✔️ .net CORE 2.0 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet help` - 顯示指定命令更詳細的線上文件。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a>描述

`dotnet help` 命令會在 docs.microsoft.com 開啟參考頁面，提供指定命令的更詳細資訊。

## <a name="arguments"></a>引數

- **`COMMAND_NAME`**

  .NET CLI 命令的名稱。 如需有效 CLI 命令的清單，請參閱 [CLI 命令](index.md#cli-commands)。

## <a name="options"></a>選項

- **`-h|--help`**

  印出命令的簡短說明。

## <a name="examples"></a>範例

- 開啟 [dotnet new](dotnet-new.md) 命令的文件頁面：

  ```dotnetcli
  dotnet help new
  ```
