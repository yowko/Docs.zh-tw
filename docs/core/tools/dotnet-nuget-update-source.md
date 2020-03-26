---
title: 點網 nuget 更新源命令
description: dotnet nuget 更新源命令更新 NuGet 設定檔中的現有源。
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148544"
---
# <a name="dotnet-nuget-update-source"></a>點網 nuget 更新源

**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget update source`- 更新 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a>描述

該`dotnet nuget update source`命令更新 NuGet 設定檔中的現有源。

## <a name="arguments"></a>引數

- **`NAME`**

  源的名稱。

## <a name="options"></a>選項。

- **`--configfile`**

  NuGet 設定檔。 如果指定，將僅使用此檔中的設置。 如果未指定，將使用目前的目錄中的設定檔層次結構。 有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

- **`-p|--password`**

  連接到經過身份驗證的源時使用的密碼。

- **`-s|--source`**

  包源的路徑。

- **`--store-password-in-clear-text`**

  通過禁用密碼加密，支援存儲可擕式包源憑據。

- **`-u|--username`**

  連接到經過身份驗證的源時使用的使用者名。

- **`--valid-authentication-types`**

  此源的有效身份驗證類型的 Comma 分隔清單。 `basic`如果伺服器通告 NTLM 或協商，並且必須使用基本機制發送憑據，例如將 PAT 與本地 Azure DevOps 伺服器一起使用時，請對此進行設置。 其他有效值包括`negotiate` `kerberos`、`ntlm`和`digest`， 但這些值不太可能有用。

## <a name="examples"></a>範例

- 更新名稱為 的`mySource`源：

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔中的包源部分](/nuget/reference/nuget-config-file#package-source-sections)

- [源命令 （nuget.exe）](/nuget/reference/cli-reference/cli-ref-sources)
