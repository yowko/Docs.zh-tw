---
title: 點網 nuget 啟用源命令
description: dotnet nuget 啟用源命令支援 NuGet 設定檔中的現有源。
ms.date: 03/20/2020
ms.openlocfilehash: 1f18e7db6a6c8631bb432676dd97dabfad5b0ab8
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148558"
---
# <a name="dotnet-nuget-enable-source"></a>點網 nuget 啟用源

**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget enable source`- 啟用 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget enable source <NAME> [--configfile]
dotnet nuget enable source [-h|--help]
```

## <a name="description"></a>描述

該`dotnet nuget enable source`命令啟用 NuGet 設定檔中的現有源。

## <a name="arguments"></a>引數

- **`NAME`**

  源的名稱。

## <a name="options"></a>選項。

- **`--configfile`**

  NuGet 設定檔。 如果指定，將僅使用此檔中的設置。 如果未指定，將使用目前的目錄中的設定檔層次結構。 有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

## <a name="examples"></a>範例

- 啟用名稱為 的`mySource`源：

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔中的包源部分](/nuget/reference/nuget-config-file#package-source-sections)

- [源命令 （nuget.exe）](/nuget/reference/cli-reference/cli-ref-sources)
