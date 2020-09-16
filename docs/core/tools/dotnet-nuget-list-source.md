---
title: dotnet nuget list source 命令
description: Dotnet nuget list source 命令會列出您的 NuGet 設定檔中的所有現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537886"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget list source

本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet nuget list source` -列出所有已設定的 NuGet 來源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a>描述

此 `dotnet nuget list source` 命令會從您的 NuGet 設定檔中列出所有現有的來源。

## <a name="options"></a>選項

- **`--configfile <FILE>`**

  NuGet 設定檔案。 如果指定，則只會使用來自此檔案的設定。 如果未指定，將會使用目前目錄中的設定檔階層。 如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。

- **`--format [Detailed|Short]`**

  清單命令輸出的格式： `Detailed` (預設) 和 `Short` 。

## <a name="examples"></a>範例

- 列出來自目前目錄的已設定來源：

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源區段](/nuget/reference/nuget-config-file#package-source-sections)

- [來源命令 ( # A0) ](/nuget/reference/cli-reference/cli-ref-sources)
