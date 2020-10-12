---
title: dotnet nuget 驗證命令
description: Dotnet nuget verify 命令會驗證已簽署的套件。
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 6cb368e2b6c203f3774b4450c0831c5d6b2dc0e8
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957139"
---
# <a name="dotnet-nuget-verify"></a>dotnet nuget 驗證

本文**適用于：** ✔️ .net 5.0.100-rc. x SDK 和更新版本

## <a name="name"></a>Name

`dotnet nuget verify` -驗證已簽署的 NuGet 套件。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a>描述

此 `dotnet nuget verify` 命令會驗證已簽署的 NuGet 套件。

## <a name="arguments"></a>引數

- **`package-path(s)`**

  指定要驗證的封裝 (的檔案路徑) 。 您可以傳入多個位置引數來驗證多個封裝。

## <a name="options"></a>選項

- **`--all`**

  指定所有可能的驗證都應該在封裝 (s) 上執行。 依預設，只 `signatures` 會驗證。

> [!NOTE]
> 此命令目前僅支援 `signature` 驗證。

- **`--certificate-fingerprint <FINGERPRINT>`**

  確認簽署者憑證符合其中一個指定的 `SHA256` 指紋。 您可以多次提供這個選項來提供多個指紋。

* **`-v|--verbosity <LEVEL>`**

  設定 MSBuild 詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設為 `normal`。

* **`-h|--help`**

  印出命令的簡短說明。

## <a name="examples"></a>範例

- 確認 *foo. nupkg*：

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- 確認已*指定目錄中的*多個 NuGet 套件- *foo. nupkg*和 nupkg 檔案：

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- 使用指定的憑證指紋確認 *foo. nupkg* 簽章相符：

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- 確認 *foo. nupkg* 簽章與其中一個指定的憑證指紋相符：

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
