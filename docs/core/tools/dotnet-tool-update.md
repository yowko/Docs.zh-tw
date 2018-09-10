---
title: dotnet tool update 命令 - .NET Core CLI
description: dotnet tool update 命令會更新您電腦上指定的 .NET Core 通用工具。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 90b0dc91f74d890420dc7185642aa89100cadba8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069389"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>名稱

`dotnet tool update` - 在您的電腦上更新指定的 [.NET Core 通用工具](global-tools.md)。

## <a name="synopsis"></a>概要

```console
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>描述

`dotnet tool update` 命令可讓您將電腦上的 .NET Core 通用工具更新為套件的最新穩定版本。 此命令會解除安裝並重新安裝工具，並有效地更新它。 若要使用此命令，您必須使用 `--global` 選項指定您要更新使用者範圍安裝中的工具，或使用 `--tool-path` 選項指定安裝工具的路徑。

## <a name="arguments"></a>引數

`PACKAGE_NAME`

包含要更新之 .NET Core 通用工具的 NuGet 套件的名稱/識別碼。 您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。

## <a name="options"></a>選項

`--add-source <SOURCE>`

新增其他 NuGet 套件來源以在安裝期間使用。

`--configfile <FILE>`

要使用的 NuGet 組態檔 (*nuget.config*)。

`--framework <FRAMEWORK>`

指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。

`-g|--global`

指定更新適用於使用者範圍工具。 無法與 `--tool-path` 選項合併使用。 如果未指定此選項，您必須指定 `--tool-path` 選項。

`-h|--help`

印出命令的簡短說明。

`--tool-path <PATH>`

指定安裝通用工具的位置。 PATH 可為絕對路徑或相對路徑。 無法與 `--global` 選項合併使用。 如果未指定此選項，您必須指定 `--global` 選項。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

更新 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool update -g dotnetsay`

從特定的 Windows 資料夾中更新 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool update dotnetsay --tool-path c:\global-tools`

從特定的 Windows 資料夾中更新 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>另請參閱

* [.NET Core 通用工具](global-tools.md)