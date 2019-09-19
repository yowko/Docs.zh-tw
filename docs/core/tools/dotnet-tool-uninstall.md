---
title: dotnet tool uninstall 命令
description: dotnet tool uninstall 命令會從您的電腦中解除安裝指定的 .NET Core 通用工具。
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117546"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>名稱

`dotnet tool uninstall` - 從您的電腦中解除安裝指定的 [.NET Core 通用工具](global-tools.md)。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>描述

`dotnet tool uninstall` 命令可讓您從電腦中解除安裝 .NET Core 通用工具。 若要使用此命令，您必須使用 `--global` 選項指定您要移除使用者範圍工具，或使用 `--tool-path` 選項指定安裝工具的路徑。

## <a name="arguments"></a>引數

`PACKAGE_NAME`

包含要解除安裝的 .NET Core 通用工具之 NuGet 套件的名稱/識別碼。 您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。

## <a name="options"></a>選項

`-g|--global`

指定要從使用者範圍安裝中移除此工具。 無法與 `--tool-path` 選項合併使用。 如果未指定此選項，您必須指定 `--tool-path` 選項。

`-h|--help`

印出命令的簡短說明。

`--tool-path <PATH>`

指定要解除安裝通用工具的位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 如果未指定此選項，您必須指定 `--global` 選項。

## <a name="examples"></a>範例

解除安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool uninstall -g dotnetsay`

從特定的 Windows 資料夾中解除安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

從特定的 Linux/macOS 資料夾中解除安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>另請參閱

- [.NET Core 通用工具](global-tools.md)
