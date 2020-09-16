---
title: dotnet nuget remove source 命令
description: Dotnet nuget remove source 命令會從您的 NuGet 設定檔中移除現有的來源。
ms.date: 03/20/2020
ms.openlocfilehash: b5575c31c0008d6e3e5a2e52906a076614217dd0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537883"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget remove source

本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet nuget remove source` -移除 NuGet 來源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a>描述

此 `dotnet nuget remove source` 命令會從您的 NuGet 設定檔中移除現有的來源。

## <a name="arguments"></a>引數

- **`NAME`**

  來源的名稱。

## <a name="options"></a>選項

- **`--configfile`**

  NuGet 設定檔案。 如果指定，則只會使用來自此檔案的設定。 如果未指定，將會使用目前目錄中的設定檔階層。 如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。

## <a name="examples"></a>範例

- 移除名稱為的來源 `mySource` ：

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源區段](/nuget/reference/nuget-config-file#package-source-sections)

- [來源命令 ( # A0) ](/nuget/reference/cli-reference/cli-ref-sources)
