---
title: dotnet nuget delete 命令 - .NET Core CLI
description: dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 1b58136d0bc04947f0a5baba320e5e6b3e45e2f1
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728410"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="5bbe7-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="5bbe7-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5bbe7-104">名稱</span><span class="sxs-lookup"><span data-stu-id="5bbe7-104">Name</span></span>

<span data-ttu-id="5bbe7-105">`dotnet nuget delete` - 從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5bbe7-106">概要</span><span class="sxs-lookup"><span data-stu-id="5bbe7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5bbe7-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bbe7-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5bbe7-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5bbe7-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5bbe7-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5bbe7-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="5bbe7-110">描述</span><span class="sxs-lookup"><span data-stu-id="5bbe7-110">Description</span></span>

<span data-ttu-id="5bbe7-111">`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="5bbe7-112">對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="5bbe7-113">引數</span><span class="sxs-lookup"><span data-stu-id="5bbe7-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5bbe7-114">要刪除的套件名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="5bbe7-115">要刪除的套件版本。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="5bbe7-116">選項</span><span class="sxs-lookup"><span data-stu-id="5bbe7-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5bbe7-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bbe7-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="5bbe7-118">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5bbe7-119">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5bbe7-120">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-120">The API key for the server.</span></span>

<span data-ttu-id="5bbe7-121">`--no-service-endpoint` 不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-121">`--no-service-endpoint` Doesn't append "api/v2/package" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="5bbe7-122">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5bbe7-123">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-123">Specifies the server URL.</span></span> <span data-ttu-id="5bbe7-124">支援的 nuget.org URL 包括 `http://www.nuget.org`、`http://www.nuget.org/api/v3` 和 `http://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-124">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5bbe7-125">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5bbe7-126">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5bbe7-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="5bbe7-127">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5bbe7-128">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5bbe7-129">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="5bbe7-130">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5bbe7-131">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-131">Specifies the server URL.</span></span> <span data-ttu-id="5bbe7-132">支援的 nuget.org URL 包括 `http://www.nuget.org`、`http://www.nuget.org/api/v3` 和 `http://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-132">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5bbe7-133">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5bbe7-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5bbe7-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="5bbe7-135">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5bbe7-136">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5bbe7-137">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="5bbe7-138">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5bbe7-139">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-139">Specifies the server URL.</span></span> <span data-ttu-id="5bbe7-140">支援的 nuget.org URL 包括 `http://www.nuget.org`、`http://www.nuget.org/api/v3` 和 `http://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-140">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5bbe7-141">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="5bbe7-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="5bbe7-142">範例</span><span class="sxs-lookup"><span data-stu-id="5bbe7-142">Examples</span></span>

<span data-ttu-id="5bbe7-143">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：</span><span class="sxs-lookup"><span data-stu-id="5bbe7-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="5bbe7-144">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：</span><span class="sxs-lookup"><span data-stu-id="5bbe7-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
