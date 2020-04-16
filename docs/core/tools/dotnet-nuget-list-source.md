---
title: 點網 nuget 清單來源指令
description: dotnet nuget 清單來源命令列出了來自 NuGet 設定檔中的所有現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463545"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget list source

**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget list source`- 列出所有配置的 NuGet 源。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a>描述

這個`dotnet nuget list source`指令列出了來自 NuGet 設定檔中的所有現有來源。

## <a name="options"></a>選項。

- **`--configfile <FILE>`**

  NuGet 設定檔。 如果指定,將僅使用此檔中的設置。 如果未指定,將使用當前目錄中的設定檔層次結構。 有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。

- **`--format [Detailed|Short]`**

  清單指令輸出的格式(`Detailed`預設值)`Short`與 。

## <a name="examples"></a>範例

- 列出目前的目錄中設定的來源:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>另請參閱

- [NuGet.config 檔案中的套件來源部份](/nuget/reference/nuget-config-file#package-source-sections)

- [來源指令 (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
