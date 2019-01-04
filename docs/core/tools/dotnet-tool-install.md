---
title: dotnet tool install 命令
description: dotnet tool install 命令會在您的電腦上安裝指定的 .NET Core 通用工具。
ms.date: 05/29/2018
ms.openlocfilehash: 251e7b04be96ac2340727fa03dbaa2d548110fa9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168711"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>名稱

`dotnet tool install` - 在您的電腦上安裝指定的 [.NET Core 通用工具](global-tools.md)。

## <a name="synopsis"></a>概要

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>說明

`dotnet tool install` 命令可讓您在電腦上安裝 .NET Core 通用工具。 若要使用此命令，您必須使用 `--global` 選項指定您要使用者範圍安裝，或使用 `--tool-path` 選項指定安裝工具的路徑。

當您指定 `-g` (或 `--global`) 選項時，通用工具預設會安裝在下列目錄中：

| 作業系統          | 路徑                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>引數

`PACKAGE_NAME`

包含要安裝的 .NET Core 通用工具之 NuGet 套件的名稱/識別碼。

## <a name="options"></a>選項

`--add-source <SOURCE>`

新增其他 NuGet 套件來源以在安裝期間使用。

`--configfile <FILE>`

要使用的 NuGet 組態檔 (*nuget.config*)。

`--framework <FRAMEWORK>`

指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。 根據預設，.NET Core SDK 會嘗試選擇最適當的目標 Framework。

`-g|--global`

指定安裝為使用者範圍。 無法與 `--tool-path` 選項合併使用。 如果未指定此選項，您必須指定 `--tool-path` 選項。

`-h|--help`

印出命令的簡短說明。

`--tool-path <PATH>`

指定要安裝通用工具的位置。 PATH 可為絕對路徑或相對路徑。 如果 PATH 不存在，命令會嘗試建立它。 無法與 `--global` 選項合併使用。 如果未指定此選項，您必須指定 `--global` 選項。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

`--version <VERSION_NUMBER>`

要安裝的工具版本。 根據預設，會安裝最新的穩定套件版本。 請使用此選項來安裝預覽版本或較舊版本的工具。

## <a name="examples"></a>範例

在預設位置中安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool install -g dotnetsay`

在特定的 Windows 資料夾中安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool install dotnetsay --tool-path c:\global-tools`

在特定的 Linux/macOS 資料夾中安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool install dotnetsay --tool-path ~/bin`

安裝 2.0.0 版的 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>另請參閱

* [.NET Core 通用工具](global-tools.md)