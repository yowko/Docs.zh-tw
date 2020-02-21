---
title: dotnet tool uninstall 命令
description: Dotnet tool uninstall 命令會從您的電腦卸載指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 82dad0206d9c3e2ef0f41c353f4a608f10e4f127
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543439"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool uninstall`-從您的電腦卸載指定的[.Net Core 工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>描述

`dotnet tool uninstall` 命令提供一種方式，讓您從電腦卸載 .NET Core 工具。 若要使用命令，您可以指定下列其中一個選項：

* 若要卸載安裝在預設位置的全域工具，請使用 [`--global`] 選項。
* 若要卸載安裝在自訂位置的全域工具，請使用 [`--tool-path`] 選項。
* 若要卸載本機工具，請省略 `--global` 並 `--tool-path` 選項。

**從 .NET Core SDK 3.0 開始提供本機工具。**

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

  包含要卸載之 .NET Core 工具之 NuGet 套件的名稱/識別碼。 您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。

## <a name="options"></a>選項。

- **`-g|--global`**

  指定要從使用者範圍安裝中移除此工具。 無法與 `--tool-path` 選項合併使用。 省略 `--global` 和 `--tool-path` 指定要移除的工具是本機工具。 

- **`-h|--help`**

  印出命令的簡短說明。

- **`--tool-path <PATH>`**

  指定要卸載工具的位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略 `--global` 和 `--tool-path` 指定要移除的工具是本機工具。 

## <a name="examples"></a>範例

- **`dotnet tool uninstall -g dotnetsay`**

  卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  從特定的 Windows 目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  從特定的 Linux/macOS 目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。

- **`dotnet tool uninstall dotnetsay`**

  從目前的目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)本機工具。

## <a name="see-also"></a>另請參閱

- [.NET Core 工具](global-tools.md)
