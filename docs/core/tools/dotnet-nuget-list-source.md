---
title: 點網 nuget 清單源命令
description: dotnet nuget 清單源命令列出了來自 NuGet 設定檔中的所有現有源。
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148572"
---
# <a name="dotnet-nuget-list-source"></a>點網 nuget 清單源

**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget list source`- 列出所有配置的 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a>描述

該`dotnet nuget list source`命令列出了來自 NuGet 設定檔中的所有現有源。

## <a name="options"></a>選項。

- **`--configfile`**

  NuGet 設定檔。 如果指定，將僅使用此檔中的設置。 如果未指定，將使用目前的目錄中的設定檔層次結構。 有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

- **`--format`**

  清單命令輸出的格式：（`Detailed`預設值）和`Short`。

## <a name="examples"></a>範例

- 列出目前的目錄中配置的源：

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔中的包源部分](/nuget/reference/nuget-config-file#package-source-sections)

- [源命令 （nuget.exe）](/nuget/reference/cli-reference/cli-ref-sources)
