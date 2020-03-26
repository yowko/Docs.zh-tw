---
title: 點網 nuget 刪除源命令
description: dotnet nuget 刪除源命令從 NuGet 設定檔中刪除現有源。
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148537"
---
# <a name="dotnet-nuget-remove-source"></a>點網 nuget 刪除源

**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget remove source`- 刪除 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a>描述

該`dotnet nuget remove source`命令從 NuGet 設定檔中刪除現有源。

## <a name="arguments"></a>引數

- **`NAME`**

  源的名稱。

## <a name="options"></a>選項。

- **`--configfile`**

  NuGet 設定檔。 如果指定，將僅使用此檔中的設置。 如果未指定，將使用目前的目錄中的設定檔層次結構。 有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

## <a name="examples"></a>範例

- 刪除名稱為 的`mySource`源：

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔中的包源部分](/nuget/reference/nuget-config-file#package-source-sections)

- [源命令 （nuget.exe）](/nuget/reference/cli-reference/cli-ref-sources)
