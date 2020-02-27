---
title: dotnet tool install 命令
description: Dotnet tool install 命令會在您的電腦上安裝指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 837d12bc807ad95ccdbd9c0e087c7d45418c6e74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626030"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool install`-在您的電腦上安裝指定的[.Net Core 工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>描述

`dotnet tool install` 命令提供一種方式，讓您在電腦上安裝 .NET Core 工具。 若要使用命令，您可以指定下列其中一個安裝選項：

* 若要在預設位置安裝全域工具，請使用 [`--global`] 選項。
* 若要在自訂位置安裝全域工具，請使用 [`--tool-path`] 選項。
* 若要安裝本機工具，請省略 `--global` 並 `--tool-path` 選項。

**從 .NET Core SDK 3.0 開始提供本機工具。**

當您指定 [`-g`] 或 [`--global`] 選項時，通用工具預設會安裝在下列目錄中：

| OS          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

本機工具會新增至目前目錄下 *.config*目錄中的*工具資訊清單. json*檔案。 如果資訊清單檔案尚不存在，請執行下列命令來建立檔案：

```dotnetcli
dotnet new tool-manifest
```

如需詳細資訊，請參閱[安裝本機工具](global-tools.md#install-a-local-tool)。

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

  包含要安裝之 .NET Core 工具的 NuGet 套件的名稱/識別碼。

## <a name="options"></a>選項。

- **`add-source <SOURCE>`**

  新增其他 NuGet 套件來源以在安裝期間使用。

- **`configfile <FILE>`**

  要使用的 NuGet 組態檔 (*nuget.config*)。

- **`framework <FRAMEWORK>`**

  指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。 根據預設，.NET Core SDK 會嘗試選擇最適當的目標 Framework。

- **`-g|--global`**

  指定安裝為使用者範圍。 無法與 `--tool-path` 選項合併使用。 省略 `--global` 和 `--tool-path` 指定本機工具安裝。 

- **`-h|--help`**

  印出命令的簡短說明。

- **`tool-path <PATH>`**

  指定要安裝通用工具的位置。 PATH 可為絕對路徑或相對路徑。 如果 PATH 不存在，命令會嘗試建立它。 省略 `--global` 和 `--tool-path` 指定本機工具安裝。 

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

- **`--version <VERSION_NUMBER>`**

  要安裝的工具版本。 根據預設，會安裝最新的穩定套件版本。 請使用此選項來安裝預覽版本或較舊版本的工具。

## <a name="examples"></a>範例

- **`dotnet tool install -g dotnetsay`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為預設位置中的通用工具。

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為特定 Windows 目錄中的通用工具。

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為特定 Linux/macOS 目錄中的通用工具。

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)的版本2.0.0 安裝為通用工具。

- **`dotnet tool install dotnetsay`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為目前目錄的本機工具。

## <a name="see-also"></a>另請參閱

- [.NET Core 工具](global-tools.md)
