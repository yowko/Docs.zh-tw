---
title: 點網工具還原命令
description: dotnet 工具還原命令在您的電腦上安裝當前目錄範圍內的 .NET Core 本地工具。
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389621"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**本文適用於:✔️** .NET Core 3.0 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet tool restore`- 在電腦上安裝當前目錄範圍內的 .NET Core 本地工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a>描述

該`dotnet tool restore`命令查找目前目錄範圍內的工具清單檔,並安裝其中列出的工具。 關於清單檔案的資訊,請參考[本地端工具與](global-tools.md#install-a-local-tool)[呼叫本地端工具](global-tools.md#invoke-a-local-tool)。

## <a name="arguments"></a>引數

- **`PACKAGE_NAME`**

包含要安裝的 .NET Core 工具的 NuGet 套件的名稱/ ID。

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

  還原當前目錄的本地工具。

## <a name="see-also"></a>另請參閱

- [.NET 核心工具](global-tools.md)
- [教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具](local-tools-how-to-use.md)
