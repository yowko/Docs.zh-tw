---
title: 點網工具還原命令
description: dotnet 工具還原命令在您的電腦上安裝目前的目錄範圍內的 .NET Core 本地工具。
ms.date: 02/14/2020
ms.openlocfilehash: cb46f70afb58e482b6aedfddfbf5f3a0c40674f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146433"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet tool restore`- 在電腦上安裝目前的目錄範圍內的 .NET Core 本地工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [-interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a>描述

該`dotnet tool restore`命令查找目前的目錄範圍內的工具清單檔，並安裝其中列出的工具。 有關清單檔的資訊，請參閱[安裝本地工具和](global-tools.md#install-a-local-tool)[調用本地工具](global-tools.md#invoke-a-local-tool)。

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

包含要安裝的 .NET Core 工具的 NuGet 包的名稱/ID。

## <a name="options"></a>選項。

- **`--configfile <FILE>`**

  要使用的 NuGet 組態檔 (*nuget.config*)。

- **`--add-source <SOURCE>`**

  新增其他 NuGet 套件來源以在安裝期間使用。

- **`--tool-manifest <PATH>`**

  清單檔的路徑。

- **`--disable-parallel`**

  防止並行還原多個專案。

- **`--ignore-failed-sources`**

  將包源故障視為警告。

- **`--no-cache`**

  不要緩存包和 HTTP 請求。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。

- **`-h|--help`**

  印出命令的簡短說明。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="example"></a>範例

- **`dotnet tool restore`**

  還原目前的目錄的本地工具。

## <a name="see-also"></a>另請參閱

- [.NET 核心工具](global-tools.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具](local-tools-how-to-use.md)
