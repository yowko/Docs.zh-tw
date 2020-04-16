---
title: 點網 nuget 新增來源命令
description: dotnet nuget 新增來源指令向 NuGet 設定檔添加新的套件來源。
ms.date: 03/20/2020
ms.openlocfilehash: 319501e026f1c3102006b0be5357f127b8e366a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463594"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget add source`- 添加 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>描述

這個`dotnet nuget add source`指令向 NuGet 設定檔加入新的套件來源。

## <a name="arguments"></a>引數

- **`PACKAGE_SOURCE_PATH`**

  包源的路徑。

## <a name="options"></a>選項。

- **`--configfile <FILE>`**

  NuGet 設定檔。 如果指定,將僅使用此檔中的設置。 如果未指定,將使用當前目錄中的設定檔層次結構。 有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

- **`-n|--name <SOURCE_NAME>`**

  源的名稱。

- **`-p|--password <PASSWORD>`**

  連接到經過身份驗證的源時使用的密碼。

- **`--store-password-in-clear-text`**

  通過禁用密碼加密,支援存儲便攜式包源憑據。

- **`-u|--username <USER>`**

  連接到經過身份驗證的源時使用的使用者名。

- **`--valid-authentication-types <TYPES>`**

  此源的有效身份驗證類型的 Comma 分隔清單。 `basic`如果伺服器通告 NTLM 或協商,並且必須使用基本機制發送認證,例如將 PAT 與本地 Azure DevOps 伺服器一起使用時,請對此進行設置。 其他有效值包括`negotiate``kerberos`、`ntlm``digest`和, 但這些值不太可能有用。

## <a name="examples"></a>範例

- 新增`nuget.org`為來源:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- 新增`c:\packages`為本地源:

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- 新增需要認證的來源:

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- 新增需要認證的來源(然後轉到安裝認證提供者):

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源部份](/nuget/reference/nuget-config-file#package-source-sections)

- [來源指令 (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
