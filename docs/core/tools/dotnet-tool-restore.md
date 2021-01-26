---
title: dotnet tool restore 命令
description: Dotnet tool restore 命令會在您的電腦上安裝目前目錄範圍內的 .NET 本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 87bdfb77cda361b800f107c565cbbed6ad75ec78
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794864"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool restore` -安裝目前目錄範圍內的 .NET 本機工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [--tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a>描述

此 `dotnet tool restore` 命令會尋找目前目錄範圍內的工具資訊清單檔，並安裝其中所列的工具。 如需資訊清單檔案的相關資訊，請參閱 [安裝本機工具](global-tools.md#install-a-local-tool) 和叫 [用本機工具](global-tools.md#invoke-a-local-tool)。

## <a name="options"></a>選項。

- **`--configfile <FILE>`**

  要使用的 NuGet 組態檔 (*nuget.config*)。

- **`--add-source <SOURCE>`**

  新增其他 NuGet 套件來源以在安裝期間使用。

- **`--tool-manifest <PATH>`**

  資訊清單檔案的路徑。

- **`--disable-parallel`**

  防止平行還原多個專案。

- **`--ignore-failed-sources`**

  將封裝來源失敗視為警告。

- **`--no-cache`**

  請勿快取套件和 HTTP 要求。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。

- **`-h|--help`**

  印出命令的簡短說明。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="example"></a>範例

- **`dotnet tool restore`**

  還原目前目錄的本機工具。

## <a name="see-also"></a>另請參閱

- [.NET 工具](global-tools.md)
- [教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具](local-tools-how-to-use.md)
