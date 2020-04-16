---
title: 點網 nuget 更新來源指令
description: dotnet nuget 更新來源指令更新 NuGet 設定檔中的現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463483"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget update source`- 更新 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>描述

該`dotnet nuget update source`指令更新 NuGet 設定檔中的現有來源。

## <a name="arguments"></a>引數

- **`NAME`**

  源的名稱。

## <a name="options"></a>選項。

- **`--configfile <FILE>`**

  NuGet 設定檔。 如果指定,將僅使用此檔中的設置。 如果未指定,將使用當前目錄中的設定檔層次結構。 有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

- **`-p|--password <PASSWORD>`**

  連接到經過身份驗證的源時使用的密碼。

- **`-s|--source <SOURCE>`**

  包源的路徑。

- **`--store-password-in-clear-text`**

  通過禁用密碼加密,支援存儲便攜式包源憑據。

- **`-u|--username <USER>`**

  連接到經過身份驗證的源時使用的使用者名。

- **`--valid-authentication-types <TYPES>`**

  此源的有效身份驗證類型的 Comma 分隔清單。 `basic`如果伺服器通告 NTLM 或協商,並且必須使用基本機制發送認證,例如將 PAT 與本地 Azure DevOps 伺服器一起使用時,請對此進行設置。 其他有效值包括`negotiate``kerberos`、`ntlm``digest`和, 但這些值不太可能有用。

## <a name="examples"></a>範例

- 更新名稱為`mySource`的 來源:

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源部份](/nuget/reference/nuget-config-file#package-source-sections)

- [來源指令 (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
