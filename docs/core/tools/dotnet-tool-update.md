---
title: dotnet tool update 命令
description: Dotnet tool update 命令會更新您電腦上指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 80e807a0fc06ad762334f888e701f6d9c448369a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156942"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool update`-在您的電腦上更新指定的[.Net Core 工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a>描述

`dotnet tool update` 命令可讓您將電腦上的 .NET Core 工具更新為套件的最新穩定版本。 此命令會解除安裝並重新安裝工具，並有效地更新它。 若要使用命令，您可以指定下列其中一個選項：

* 若要更新已安裝在預設位置中的全域工具，請使用 [`--global`] 選項
* 若要更新已安裝在自訂位置的全域工具，請使用 [`--tool-path`] 選項。
* 若要更新本機工具，請省略 `--global` 並 `--tool-path` 選項。

**從 .NET Core SDK 3.0 開始提供本機工具。**

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

  包含要更新之 .NET Core 通用工具之 NuGet 套件的名稱/識別碼。 您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。

## <a name="options"></a>選項。

- **`--add-source <SOURCE>`**

  新增其他 NuGet 套件來源以在安裝期間使用。

- **`--configfile <FILE>`**

  要使用的 NuGet 組態檔 (*nuget.config*)。

- **`--framework <FRAMEWORK>`**

  指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。

- **`-g|--global`**

  指定更新適用於使用者範圍工具。 無法與 `--tool-path` 選項合併使用。 省略 `--global` 和 `--tool-path` 指定要更新的工具是本機工具。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--tool-path <PATH>`**

  指定安裝通用工具的位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略 `--global` 和 `--tool-path` 指定要更新的工具是本機工具。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

- **`dotnet tool update -g dotnetsay`**

  更新[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  更新位於特定 Windows 目錄中的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  更新位於特定 Linux/macOS 目錄中的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。

- **`dotnet tool update dotnetsay`**

  更新針對目前的目錄所安裝的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)本機工具。

## <a name="see-also"></a>另請參閱

- [.NET Core 工具](global-tools.md)
