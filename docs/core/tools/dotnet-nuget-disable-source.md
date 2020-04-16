---
title: 點網 nuget 停用來源指令
description: dotnet nuget 停用來源命令關閉 NuGet 設定檔中的現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 54acb40b1944eaff347107e8f3439578ec8e0f3c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463573"
---
# <a name="dotnet-nuget-disable-source"></a>dotnet nuget disable source

**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget disable source`- 停用 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a>描述

這個`dotnet nuget disable source`指令關閉 NuGet 設定檔中的現有來源。

## <a name="arguments"></a>引數

- **`NAME`**

  源的名稱。

## <a name="options"></a>選項。

- **`--configfile <FILE>`**

  NuGet 設定檔。 如果指定,將僅使用此檔中的設置。 如果未指定,將使用當前目錄中的設定檔層次結構。 有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

## <a name="examples"></a>範例

- 關閉名為的`mySource`源:

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源部份](/nuget/reference/nuget-config-file#package-source-sections)

- [來源指令 (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
