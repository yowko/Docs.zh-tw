---
title: 點網 nuget 添加源命令
description: dotnet nuget 添加源命令向 NuGet 設定檔添加新的包源。
ms.date: 03/20/2020
ms.openlocfilehash: c1e398699c7482a69b750cde718e6f9178b5c4bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148565"
---
# <a name="dotnet-nuget-add-source"></a>點網 nuget 添加源

**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget add source`- 添加 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a>描述

該`dotnet nuget add source`命令向 NuGet 設定檔添加新的包源。

## <a name="arguments"></a>引數

- **`PACKAGE_SOURCE_PATH`**

  包源的路徑。

## <a name="options"></a>選項。

- **`--configfile`**

  NuGet 設定檔。 如果指定，將僅使用此檔中的設置。 如果未指定，將使用目前的目錄中的設定檔層次結構。 有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

- **`-n|--name`**

  源的名稱。

- **`-p|--password`**

  連接到經過身份驗證的源時使用的密碼。

- **`--store-password-in-clear-text`**

  通過禁用密碼加密，支援存儲可擕式包源憑據。

- **`-u|--username`**

  連接到經過身份驗證的源時使用的使用者名。

- **`--valid-authentication-types`**

  此源的有效身份驗證類型的 Comma 分隔清單。 `basic`如果伺服器通告 NTLM 或協商，並且必須使用基本機制發送憑據，例如將 PAT 與本地 Azure DevOps 伺服器一起使用時，請對此進行設置。 其他有效值包括`negotiate` `kerberos`、`ntlm`和`digest`， 但這些值不太可能有用。

## <a name="examples"></a>範例

- 添加`nuget.org`為源：

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- 添加`c:\packages`為本地源：

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- 添加需要身份驗證的源：

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- 添加需要身份驗證的源（然後轉到安裝憑據提供程式）：

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔中的包源部分](/nuget/reference/nuget-config-file#package-source-sections)

- [源命令 （nuget.exe）](/nuget/reference/cli-reference/cli-ref-sources)
