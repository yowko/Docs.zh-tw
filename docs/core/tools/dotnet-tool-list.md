---
title: dotnet tool list 命令
description: dotnet 工具清單命令列出了安裝在電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847868"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet tool list`- 列出電腦上當前安裝的指定類型的所有[.NET 核心工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a>描述

該`dotnet tool list`命令提供了一種列出電腦上安裝的所有 .NET Core 全域、工具路徑或本地工具的方法。 該命令列出包名稱、已安裝的版本和工具命令。  要使用 該命令，請指定以下命令之一：

* 安裝在預設位置的全域工具。 使用選項`--global`
* 安裝在自訂位置的全域工具。 使用 `--tool-path` 選項。
* 本地工具。 省略 和`--global``--tool-path`選項。

**本地工具可從 .NET 核心 SDK 3.0 開始。**

## <a name="options"></a>選項。

- **`-g|--global`**

  列出使用者範圍的全域工具。 無法與 `--tool-path` 選項合併使用。 省略和`--global``--tool-path`列出本地工具。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--tool-path <PATH>`**

  指定查找全域工具的自訂位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略和`--global``--tool-path`列出本地工具。

## <a name="examples"></a>範例

- **`dotnet tool list -g`**

  列出電腦上安裝的使用者範圍的所有全域工具（當前使用者設定檔）。

- **`dotnet tool list --tool-path c:\global-tools`**

  列出特定 Windows 目錄中的全域工具。

- **`dotnet tool list --tool-path ~/bin`**

  列出來自特定 Linux/macOS 目錄的全域工具。

- **`dotnet tool list`**

  列出目前的目錄中可用的所有本地工具。

## <a name="see-also"></a>另請參閱

- [.NET 核心工具](global-tools.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具](global-tools-how-to-use.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具](local-tools-how-to-use.md)
