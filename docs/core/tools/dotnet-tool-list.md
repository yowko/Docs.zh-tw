---
title: dotnet tool list 命令
description: Dotnet tool list 命令會列出安裝在您電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 4035c5be233232e53c6d7150485f737108c1e18d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925458"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>Name

`dotnet tool list`-列出目前安裝在您電腦上之指定類型的所有[.Net Core 工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>描述

此 `dotnet tool list` 命令可讓您列出電腦上所安裝的所有 .Net Core 全域、工具路徑或本機工具。 此命令會列出封裝名稱、已安裝的版本，以及工具命令。  若要使用命令，您可以指定下列其中一項：

* 若要列出安裝在預設位置的全域工具，請使用 `--global` 選項
* 若要列出自訂位置中安裝的通用工具，請使用 `--tool-path` 選項。
* 若要列出本機工具，請使用 `--local` 選項，或省略 `--global` 、 `--tool-path` 和 `--local` 選項。

**從 .NET Core SDK 3.0 開始提供本機工具。**

## <a name="options"></a>選項。

- **`-g|--global`**

  列出使用者範圍的通用工具。 無法與 `--tool-path` 選項合併使用。 省略 `--global` 和都會 `--tool-path` 列出本機工具。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--local`**

  列出目前目錄的本機工具。 無法與 `--global` 或 `--tool-path` 選項結合。 `--global` `--tool-path` 即使未指定，也會省略和列出本機工具 `--local` 。

- **`--tool-path <PATH>`**

  指定要在其中尋找通用工具的自訂位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略 `--global` 和都會 `--tool-path` 列出本機工具。

## <a name="examples"></a>範例

- **`dotnet tool list -g`**

  列出電腦上全使用者安裝的所有通用工具（目前的使用者設定檔）。

- **`dotnet tool list --tool-path c:\global-tools`**

  列出特定 Windows 目錄中的通用工具。

- **`dotnet tool list --tool-path ~/bin`**

  列出特定 Linux/macOS 目錄中的通用工具。

- **`dotnet tool list`** 或**`dotnet tool list --local`**

  列出目前目錄中所有可用的本機工具。

## <a name="see-also"></a>另請參閱

- [.NET Core 工具](global-tools.md)
- [教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 通用工具](global-tools-how-to-use.md)
- [教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具](local-tools-how-to-use.md)
