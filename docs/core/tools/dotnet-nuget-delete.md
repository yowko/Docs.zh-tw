---
title: dotnet nuget delete 命令 - .NET Core CLI
description: dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: f4aa027a465c4adea1de13853063d03e8e295411
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180872"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet nuget delete` - 從伺服器刪除或取消列出套件。

## <a name="synopsis"></a>概要

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a>描述

`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。 對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。

## <a name="arguments"></a>引數

`PACKAGE_NAME`

要刪除的套件名稱/識別碼。

`PACKAGE_VERSION`

要刪除的套件版本。

## <a name="options"></a>選項

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--force-english-output`

 強制使用非變異英文文化特性來執行應用程式。

`-h|--help`

印出命令的簡短說明。

`-k|--api-key <API_KEY>`

伺服器的 API 金鑰。

`--no-service-endpoint` 不會將 "api/v2/package" 附加至來源 URL。

`--non-interactive`

不提示使用者輸入或確認。

`-s|--source <SOURCE>`

指定伺服器 URL。 支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。 對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force-english-output`

 強制使用非變異英文文化特性來執行應用程式。

`-h|--help`

印出命令的簡短說明。

`-k|--api-key <API_KEY>`

伺服器的 API 金鑰。

`--non-interactive`

不提示使用者輸入或確認。

`-s|--source <SOURCE>`

指定伺服器 URL。 支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。 對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--force-english-output`

 強制使用非變異英文文化特性來執行應用程式。

`-h|--help`

印出命令的簡短說明。

`-k|--api-key <API_KEY>`

伺服器的 API 金鑰。

`--non-interactive`

不提示使用者輸入或確認。

`-s|--source <SOURCE>`

指定伺服器 URL。 支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。 對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。

---

## <a name="examples"></a>範例

刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
