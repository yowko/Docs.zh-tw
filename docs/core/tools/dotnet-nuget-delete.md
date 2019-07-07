---
title: dotnet nuget delete 命令
description: dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0b2ba64b70bae5e06f213457e30fedeca26a9819
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539246"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="2ba7b-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="2ba7b-103">dotnet nuget delete</span></span>

<span data-ttu-id="2ba7b-104">**本主題適用於：✓** .NET Core 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2ba7b-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="2ba7b-105">名稱</span><span class="sxs-lookup"><span data-stu-id="2ba7b-105">Name</span></span>

<span data-ttu-id="2ba7b-106">`dotnet nuget delete` - 從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2ba7b-107">概要</span><span class="sxs-lookup"><span data-stu-id="2ba7b-107">Synopsis</span></span>

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2ba7b-108">說明</span><span class="sxs-lookup"><span data-stu-id="2ba7b-108">Description</span></span>

<span data-ttu-id="2ba7b-109">`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="2ba7b-110">對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="2ba7b-111">引數</span><span class="sxs-lookup"><span data-stu-id="2ba7b-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="2ba7b-112">要刪除的套件名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="2ba7b-113">要刪除的套件版本。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="2ba7b-114">選項</span><span class="sxs-lookup"><span data-stu-id="2ba7b-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="2ba7b-115">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="2ba7b-116">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="2ba7b-117">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="2ba7b-118">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="2ba7b-119">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="2ba7b-120">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="2ba7b-121">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="2ba7b-122">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="2ba7b-123">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-123">Specifies the server URL.</span></span> <span data-ttu-id="2ba7b-124">支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="2ba7b-125">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="2ba7b-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="2ba7b-126">範例</span><span class="sxs-lookup"><span data-stu-id="2ba7b-126">Examples</span></span>

* <span data-ttu-id="2ba7b-127">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：</span><span class="sxs-lookup"><span data-stu-id="2ba7b-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="2ba7b-128">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：</span><span class="sxs-lookup"><span data-stu-id="2ba7b-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
