---
title: dotnet tool list 命令
description: Dotnet tool list 命令會列出安裝在您電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: bb74cfeaf441cf8a1a030d97d16655f85d8267d1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543452"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool list`-列出目前安裝在您電腦上之指定類型的所有[.Net Core 工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a>描述

`dotnet tool list` 命令可讓您列出電腦上所安裝的所有 .NET Core 全域、工具路徑或本機工具。 此命令會列出封裝名稱、已安裝的版本，以及工具命令。  若要使用命令，您可以指定下列其中一項：

* 預設位置中安裝的通用工具。 使用 [`--global`] 選項
* 安裝在自訂位置的通用工具。 使用 `--tool-path` 選項。
* 本機工具。 省略 `--global` 並 `--tool-path` 選項。

**從 .NET Core SDK 3.0 開始提供本機工具。**

## <a name="options"></a>選項。

- **`-g|--global`**

  列出使用者範圍的通用工具。 無法與 `--tool-path` 選項合併使用。 省略 `--global` 和 `--tool-path` 會列出本機工具。 

- **`-h|--help`**

  印出命令的簡短說明。

- **`--tool-path <PATH>`**

  指定要在其中尋找通用工具的自訂位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略 `--global` 和 `--tool-path` 會列出本機工具。 

## <a name="examples"></a>範例

- **`dotnet tool list -g`**

  列出電腦上全使用者安裝的所有通用工具（目前的使用者設定檔）。

- **`dotnet tool list --tool-path c:\global-tools`**

  列出特定 Windows 目錄中的通用工具。

- **`dotnet tool list --tool-path ~/bin`**

  列出特定 Linux/macOS 目錄中的通用工具。

- **`dotnet tool list`**

  列出目前目錄中所有可用的本機工具。

## <a name="see-also"></a>另請參閱

- [.NET Core 工具](global-tools.md)
