---
title: dotnet tool uninstall 命令
description: Dotnet tool uninstall 命令會從您的電腦卸載指定的 .NET 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 34dffde8f9c930327c6b42d1d89bb4f511959fb2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634086"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool uninstall` -從您的電腦卸載指定的 [.net 工具](global-tools.md) 。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>描述

此 `dotnet tool uninstall` 命令會提供一種方法，讓您從電腦卸載 .net 工具。 若要使用命令，您可以指定下列其中一個選項：

* 若要卸載安裝在預設位置的通用工具，請使用 `--global` 選項。
* 若要卸載在自訂位置安裝的通用工具，請使用 `--tool-path` 選項。
* 若要卸載本機工具，請省略 `--global` 和 `--tool-path` 選項。

**從 .NET Core SDK 3.0 開始，可以使用本機工具。**

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

  包含要卸載之 .NET 工具的 NuGet 套件名稱/識別碼。 您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。

## <a name="options"></a>選項

- **`-g|--global`**

  指定要從使用者範圍安裝中移除此工具。 無法與 `--tool-path` 選項合併使用。 省略兩者 `--global` 並 `--tool-path` 指定要移除的工具是本機工具。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--tool-path <PATH>`**

  指定要卸載工具的位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 省略兩者 `--global` 並 `--tool-path` 指定要移除的工具是本機工具。

## <a name="examples"></a>範例

- **`dotnet tool uninstall -g dotnetsay`**

  卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool。

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  從特定的 Windows 目錄卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool。

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  從特定的 Linux/macOS 目錄中卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool。

- **`dotnet tool uninstall dotnetsay`**

  從目前目錄卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 本機工具。

## <a name="see-also"></a>另請參閱

- [.NET 工具](global-tools.md)
- [教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具](global-tools-how-to-use.md)
- [教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具](local-tools-how-to-use.md)
