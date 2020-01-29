---
title: dotnet nuget delete 命令
description: dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733129"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget delete` - 從伺服器刪除或取消列出套件。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>描述

`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。 對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。

## <a name="arguments"></a>Arguments

* **`PACKAGE_NAME`**

  要刪除的套件名稱/識別碼。

* **`PACKAGE_VERSION`**

  要刪除的套件版本。

## <a name="options"></a>選項

* **`--force-english-output`**

  強制使用非變異英文文化特性來執行應用程式。

* **`-h|--help`**

  印出命令的簡短說明。

* **`--interactive`**

  允許命令進行封鎖及要求對驗證之類的作業採取手動動作。 自 .NET Core 2.2 SDK 起可用的選項。

* **`-k|--api-key <API_KEY>`**

  伺服器的 API 金鑰。

* **`--no-service-endpoint`**

  不會將 "api/v2/package" 附加至來源 URL。 自 .NET Core 2.1 SDK 起可用的選項。

* **`--non-interactive`**

  不提示使用者輸入或確認。

* **`-s|--source <SOURCE>`**

  指定伺服器 URL。 支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。 對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。

## <a name="examples"></a>範例

* 刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* 刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
