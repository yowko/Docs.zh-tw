---
title: dotnet nuget delete 命令
description: dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: a657fa273ca6b5229a1713fbcaf003217a59fd7f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612624"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="600db-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="600db-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="600db-104">名稱</span><span class="sxs-lookup"><span data-stu-id="600db-104">Name</span></span>

<span data-ttu-id="600db-105">`dotnet nuget delete` - 從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="600db-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="600db-106">概要</span><span class="sxs-lookup"><span data-stu-id="600db-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="600db-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="600db-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="600db-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="600db-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="600db-109">說明</span><span class="sxs-lookup"><span data-stu-id="600db-109">Description</span></span>

<span data-ttu-id="600db-110">`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="600db-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="600db-111">對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="600db-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="600db-112">引數</span><span class="sxs-lookup"><span data-stu-id="600db-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="600db-113">要刪除的套件名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="600db-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="600db-114">要刪除的套件版本。</span><span class="sxs-lookup"><span data-stu-id="600db-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="600db-115">選項</span><span class="sxs-lookup"><span data-stu-id="600db-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="600db-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="600db-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="600db-117">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="600db-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="600db-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="600db-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="600db-119">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="600db-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="600db-120">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="600db-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="600db-121">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="600db-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="600db-122">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="600db-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="600db-123">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="600db-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="600db-124">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="600db-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="600db-125">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="600db-125">Specifies the server URL.</span></span> <span data-ttu-id="600db-126">支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="600db-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="600db-127">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="600db-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="600db-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="600db-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="600db-129">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="600db-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="600db-130">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="600db-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="600db-131">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="600db-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="600db-132">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="600db-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="600db-133">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="600db-133">Specifies the server URL.</span></span> <span data-ttu-id="600db-134">支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="600db-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="600db-135">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="600db-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="600db-136">範例</span><span class="sxs-lookup"><span data-stu-id="600db-136">Examples</span></span>

* <span data-ttu-id="600db-137">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：</span><span class="sxs-lookup"><span data-stu-id="600db-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="600db-138">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：</span><span class="sxs-lookup"><span data-stu-id="600db-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```