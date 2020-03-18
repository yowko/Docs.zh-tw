---
title: dotnet tool update 命令
description: dotnet 工具更新命令更新您電腦上的指定的 .NET 核心工具。
ms.date: 02/14/2020
ms.openlocfilehash: 497b052a8b9cfa9dca8d80316075fe7565d6b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847816"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet tool update`- 更新機器上指定的[.NET 核心工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME> <--tool-path>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <-h|--help>
```

## <a name="description"></a>描述

該`dotnet tool update`命令提供了一種將電腦上的 .NET Core 工具更新到包的最新穩定版本的方法。 此命令會解除安裝並重新安裝工具，並有效地更新它。 要使用 該命令，請指定以下選項之一：

* 要更新安裝在預設位置的全域工具，請使用 選項`--global`
* 要更新安裝在自訂位置的全域工具，請使用 選項`--tool-path`。
* 要更新本地工具，請省略 和`--global``--tool-path`選項。

**本地工具可從 .NET 核心 SDK 3.0 開始。**

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

  包含要更新的 .NET Core 全域工具的 NuGet 包的名稱/ID。 您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。

## <a name="options"></a>選項。

- **`--add-source <SOURCE>`**

  新增其他 NuGet 套件來源以在安裝期間使用。

- **`--configfile <FILE>`**

  要使用的 NuGet 組態檔 (*nuget.config*)。

- **`--framework <FRAMEWORK>`**

  指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。

- **`-g|--global`**

  指定更新適用於使用者範圍工具。 無法與 `--tool-path` 選項合併使用。 省略兩者`--global`並`--tool-path`指定要更新的工具是本地工具。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--tool-path <PATH>`**

  指定安裝全域工具的位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略兩者`--global`並`--tool-path`指定要更新的工具是本地工具。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

- **`dotnet tool update -g dotnetsay`**

  更新[點網路賽](https://www.nuget.org/packages/dotnetsay/)全域工具。

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  更新位於特定 Windows 目錄中的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)全域工具。

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  更新位於特定 Linux/macOS 目錄中的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)全域工具。

- **`dotnet tool update dotnetsay`**

  更新為目前的目錄安裝的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)本地工具。

## <a name="see-also"></a>另請參閱

- [.NET 核心工具](global-tools.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具](global-tools-how-to-use.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具](local-tools-how-to-use.md)
