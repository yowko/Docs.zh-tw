---
title: dotnet tool update 命令
description: Dotnet tool update 命令會更新您電腦上指定的 .NET Core 工具。
ms.date: 07/08/2020
ms.openlocfilehash: a212fbb40af68019c1bc9a63963d960292be6b08
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308867"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool update`-在您的電腦上更新指定的[.Net Core 工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a>描述

此 `dotnet tool update` 命令可讓您將電腦上的 .Net Core 工具更新為套件的最新穩定版本。 此命令會解除安裝並重新安裝工具，並有效地更新它。 若要使用命令，您可以指定下列其中一個選項：

* 若要更新已安裝在預設位置中的全域工具，請使用 `--global` 選項
* 若要更新已安裝在自訂位置的全域工具，請使用 `--tool-path` 選項。
* 若要更新本機工具，請使用 `--local` 選項。

**從 .NET Core SDK 3.0 開始提供本機工具。**

## <a name="arguments"></a>引數

- **`PACKAGE_ID`**

  包含要更新之 .NET Core 通用工具之 NuGet 套件的名稱/識別碼。 您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。

## <a name="options"></a>選項

- **`--add-source <SOURCE>`**

  新增其他 NuGet 套件來源以在安裝期間使用。

- **`--configfile <FILE>`**

  要使用的 NuGet 組態檔 (*nuget.config*)。

- **`--disable-parallel`**

  防止平行還原多個專案。

- **`--framework <FRAMEWORK>`**

  指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。

- **`--ignore-failed-sources`**

  將套件來源失敗視為警告。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。

- **`--local`**

  更新工具和本機工具資訊清單。 無法與 `--global` 選項或選項結合使用 `--tool-path` 。

- **`--no-cache`**

  不要快取套件和 HTTP 要求。

- **`--tool-manifest <PATH>`**

  資訊清單檔案的路徑。

- **`--tool-path <PATH>`**

  指定安裝通用工具的位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略 `--global` 和都會 `--tool-path` 指定要更新的工具是本機工具。

- **`--version <VERSION>`**

  要更新的工具套件版本範圍。 這不能用來降級版本，您必須 `uninstall` 先更新版本。

- **`-g|--global`**

  指定更新適用於使用者範圍工具。 無法與 `--tool-path` 選項合併使用。 省略 `--global` 和都會 `--tool-path` 指定要更新的工具是本機工具。

- **`-h|--help`**

  印出命令的簡短說明。

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

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具更新為最新的修補程式版本，其主要版本為 `2` ，而次要版本為 `0` 。

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具更新為指定範圍內的最低版本 `(> 2.0.0 && < 2.1.4)` ，將 `2.1.0` 會安裝版本。 如需有關語義版本控制範圍的詳細資訊，請參閱[NuGet 封裝版本範圍](/nuget/concepts/package-versioning#version-ranges)。

## <a name="see-also"></a>另請參閱

- [.NET Core 工具](global-tools.md)
- [語意化版本控制系統](https://semver.org)
- [教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 通用工具](global-tools-how-to-use.md)
- [教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具](local-tools-how-to-use.md)
