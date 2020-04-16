---
title: dotnet tool list 命令
description: dotnet 工具清單命令列出了安裝在電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463352"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet tool list`- 列出電腦上目前安裝的指定類型的所有[.NET 核心工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>描述

該`dotnet tool list`指令提供了一種列出電腦上安裝的所有 .NET Core 全域、工具路徑或本地工具的方法。 該命令列出包名稱、已安裝的版本和工具命令。  要使用 此指令,請指定以下指令之一:

* 安裝在預設位置的全域工具。 使用選項`--global`
* 安裝在自定義位置的全域工具。 使用 `--tool-path` 選項。
* 本地工具。 省略和`--global``--tool-path`選項。

**本地工具可從 .NET 核心 SDK 3.0 開始。**

## <a name="options"></a>選項。

- **`-g|--global`**

  列出用戶範圍的全域工具。 無法與 `--tool-path` 選項合併使用。 省略和`--global``--tool-path`列出本地工具。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--tool-path <PATH>`**

  指定查找全域工具的自定義位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略和`--global``--tool-path`列出本地工具。

## <a name="examples"></a>範例

- **`dotnet tool list -g`**

  列出電腦上安裝的使用者範圍的所有全域工具(當前使用者配置檔)。

- **`dotnet tool list --tool-path c:\global-tools`**

  列出特定 Windows 目錄中的全域工具。

- **`dotnet tool list --tool-path ~/bin`**

  列出來自特定 Linux/macOS 目錄的全域工具。

- **`dotnet tool list`**

  列出目前目錄中可用的所有本地工具。

## <a name="see-also"></a>另請參閱

- [.NET 核心工具](global-tools.md)
- [教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心全域工具](global-tools-how-to-use.md)
- [教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具](local-tools-how-to-use.md)
