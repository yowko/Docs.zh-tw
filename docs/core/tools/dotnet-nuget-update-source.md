---
title: dotnet nuget 更新來源命令
description: Dotnet nuget 更新來源命令會更新您 NuGet 設定檔中的現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: a8658c78c095ad4b9272d97200e1d6466cbe658b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537850"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet nuget update source` -更新 NuGet 來源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>描述

此 `dotnet nuget update source` 命令會更新您 NuGet 設定檔中的現有來源。

## <a name="arguments"></a>引數

- **`NAME`**

  來源的名稱。

## <a name="options"></a>選項

- **`--configfile <FILE>`**

  NuGet 設定檔案。 如果指定，則只會使用來自此檔案的設定。 如果未指定，將會使用目前目錄中的設定檔階層。 如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。

- **`-p|--password <PASSWORD>`**

  連接到已驗證的來源時，所要使用的密碼。

- **`-s|--source <SOURCE>`**

  套件來源的路徑。

- **`--store-password-in-clear-text`**

  藉由停用密碼加密，啟用儲存便攜套件來源認證。

- **`-u|--username <USER>`**

  連接到已驗證的來源時，所要使用的使用者名稱。

- **`--valid-authentication-types <TYPES>`**

  此來源的有效驗證類型清單（以逗號分隔）。 將此設定為， `basic` 如果伺服器通告 NTLM 或 Negotiate，而且您的認證必須使用基本機制傳送，例如，搭配內部部署 Azure DevOps Server 使用 PAT。 其他有效的值包括 `negotiate` 、 `kerberos` 、 `ntlm` 和 `digest` ，但這些值不太可能很有用。

## <a name="examples"></a>範例

- 以下列名稱更新來源 `mySource` ：

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源區段](/nuget/reference/nuget-config-file#package-source-sections)

- [來源命令 ( # A0) ](/nuget/reference/cli-reference/cli-ref-sources)
