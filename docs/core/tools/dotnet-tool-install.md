---
title: dotnet tool install 命令
description: dotnet 工具安裝命令在您的電腦上安裝指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 1e142773d1f981a8dc3b552d5a23d2864cdd82c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146459"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet tool install`- 在機器上安裝指定的[.NET 核心工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME> <--tool-path>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <-h|--help>
```

## <a name="description"></a>描述

該`dotnet tool install`命令為您提供了在電腦上安裝 .NET Core 工具的方法。 要使用 該命令，請指定以下安裝選項之一：

* 要在預設位置安裝全域工具，請使用 選項`--global`。
* 要在自訂位置安裝全域工具，請使用 選項`--tool-path`。
* 要安裝本地工具，請省略 和`--global``--tool-path`選項。

**本地工具可從 .NET 核心 SDK 3.0 開始。**

預設情況下，當您指定 或`-g``--global`選項時，全域工具將安裝在以下目錄中：

| OS          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

本地工具將添加到目前的目錄下的 *.config*目錄中*的工具清單.json*檔中。 如果清單檔尚不存在，請通過運行以下命令創建它：

```dotnetcli
dotnet new tool-manifest
```

有關詳細資訊，請參閱[安裝本地工具](global-tools.md#install-a-local-tool)。

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

  包含要安裝的 .NET Core 工具的 NuGet 包的名稱/ID。

## <a name="options"></a>選項。

- **`add-source <SOURCE>`**

  新增其他 NuGet 套件來源以在安裝期間使用。

- **`configfile <FILE>`**

  要使用的 NuGet 組態檔 (*nuget.config*)。

- **`framework <FRAMEWORK>`**

  指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。 根據預設，.NET Core SDK 會嘗試選擇最適當的目標 Framework。

- **`-g|--global`**

  指定安裝為使用者範圍。 無法與 `--tool-path` 選項合併使用。 省略兩者`--global`並`--tool-path`指定本地工具安裝。

- **`-h|--help`**

  印出命令的簡短說明。

- **`tool-path <PATH>`**

  指定要安裝通用工具的位置。 PATH 可為絕對路徑或相對路徑。 如果 PATH 不存在，命令會嘗試建立它。 省略兩者`--global`並`--tool-path`指定本地工具安裝。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

- **`--version <VERSION_NUMBER>`**

  要安裝的工具版本。 根據預設，會安裝最新的穩定套件版本。 請使用此選項來安裝預覽版本或較舊版本的工具。

## <a name="examples"></a>範例

- **`dotnet tool install -g dotnetsay`**

  在預設位置將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝。

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝到特定的 Windows 目錄中。

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝到特定的 Linux/macOS 目錄中。

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)的版本 2.0.0 安裝為全域工具。

- **`dotnet tool install dotnetsay`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為目前的目錄的本地工具。

## <a name="see-also"></a>另請參閱

- [.NET 核心工具](global-tools.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具](global-tools-how-to-use.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具](local-tools-how-to-use.md)
