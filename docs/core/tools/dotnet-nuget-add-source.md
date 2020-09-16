---
title: dotnet nuget add source 命令
description: Dotnet nuget add source 命令會將新的套件來源新增至您的 NuGet 設定檔。
ms.date: 03/20/2020
ms.openlocfilehash: b847d987de2d88cb3452d32d1bc84232a1e20b6e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537969"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet nuget add source` -新增 NuGet 來源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>描述

此 `dotnet nuget add source` 命令會將新的套件來源新增至您的 NuGet 設定檔。

## <a name="arguments"></a>引數

- **`PACKAGE_SOURCE_PATH`**

  套件來源的路徑。

## <a name="options"></a>選項

- **`--configfile <FILE>`**

  NuGet 設定檔案。 如果指定，則只會使用來自此檔案的設定。 如果未指定，將會使用目前目錄中的設定檔階層。 如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。

- **`-n|--name <SOURCE_NAME>`**

  來源的名稱。

- **`-p|--password <PASSWORD>`**

  連接到已驗證的來源時，所要使用的密碼。

- **`--store-password-in-clear-text`**

  藉由停用密碼加密，啟用儲存便攜套件來源認證。

- **`-u|--username <USER>`**

  連接到已驗證的來源時，所要使用的使用者名稱。

- **`--valid-authentication-types <TYPES>`**

  此來源的有效驗證類型清單（以逗號分隔）。 將此設定為， `basic` 如果伺服器通告 NTLM 或 Negotiate，而且您的認證必須使用基本機制傳送，例如，搭配內部部署 Azure DevOps Server 使用 PAT。 其他有效的值包括 `negotiate` 、 `kerberos` 、 `ntlm` 和 `digest` ，但這些值不太可能很有用。

## <a name="examples"></a>範例

- 新增 `nuget.org` 為來源：

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- 新增 `c:\packages` 為本機來源：

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- 新增需要驗證的來源：

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- 新增需要驗證的來源 (然後 go 安裝認證提供者) ：

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源區段](/nuget/reference/nuget-config-file#package-source-sections)

- [來源命令 ( # A0) ](/nuget/reference/cli-reference/cli-ref-sources)
