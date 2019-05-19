---
title: dotnet nuget delete 命令
description: dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: e1362413aa6458674518d68340634741994b34a3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632050"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="b56d7-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="b56d7-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b56d7-104">名稱</span><span class="sxs-lookup"><span data-stu-id="b56d7-104">Name</span></span>

<span data-ttu-id="b56d7-105">`dotnet nuget delete` - 從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="b56d7-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b56d7-106">概要</span><span class="sxs-lookup"><span data-stu-id="b56d7-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b56d7-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b56d7-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b56d7-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b56d7-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="b56d7-109">說明</span><span class="sxs-lookup"><span data-stu-id="b56d7-109">Description</span></span>

<span data-ttu-id="b56d7-110">`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="b56d7-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="b56d7-111">對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="b56d7-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="b56d7-112">引數</span><span class="sxs-lookup"><span data-stu-id="b56d7-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="b56d7-113">要刪除的套件名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="b56d7-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="b56d7-114">要刪除的套件版本。</span><span class="sxs-lookup"><span data-stu-id="b56d7-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="b56d7-115">選項</span><span class="sxs-lookup"><span data-stu-id="b56d7-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b56d7-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b56d7-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="b56d7-117">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b56d7-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="b56d7-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b56d7-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="b56d7-119">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="b56d7-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="b56d7-120">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b56d7-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="b56d7-121">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="b56d7-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="b56d7-122">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="b56d7-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="b56d7-123">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b56d7-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="b56d7-124">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="b56d7-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="b56d7-125">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="b56d7-125">Specifies the server URL.</span></span> <span data-ttu-id="b56d7-126">支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="b56d7-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="b56d7-127">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="b56d7-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b56d7-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b56d7-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="b56d7-129">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b56d7-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="b56d7-130">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b56d7-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="b56d7-131">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="b56d7-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="b56d7-132">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="b56d7-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="b56d7-133">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="b56d7-133">Specifies the server URL.</span></span> <span data-ttu-id="b56d7-134">支援的 nuget.org URL 包括 `https://www.nuget.org`、`https://www.nuget.org/api/v3` 和 `https://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="b56d7-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="b56d7-135">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="b56d7-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="b56d7-136">範例</span><span class="sxs-lookup"><span data-stu-id="b56d7-136">Examples</span></span>

* <span data-ttu-id="b56d7-137">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：</span><span class="sxs-lookup"><span data-stu-id="b56d7-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="b56d7-138">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：</span><span class="sxs-lookup"><span data-stu-id="b56d7-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
