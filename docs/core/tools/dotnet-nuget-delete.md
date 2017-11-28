---
title: "dotnet nuget delete 命令 - .NET Core CLI"
description: "dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 65fe52f07ed823b4f7518c5b1f2da1f7a61b0371
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="08d9c-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="08d9c-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="08d9c-104">name</span><span class="sxs-lookup"><span data-stu-id="08d9c-104">Name</span></span>

<span data-ttu-id="08d9c-105">`dotnet nuget delete` - 從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="08d9c-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="08d9c-106">概要</span><span class="sxs-lookup"><span data-stu-id="08d9c-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="08d9c-107">說明</span><span class="sxs-lookup"><span data-stu-id="08d9c-107">Description</span></span>

<span data-ttu-id="08d9c-108">`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="08d9c-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="08d9c-109">對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="08d9c-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="08d9c-110">引數</span><span class="sxs-lookup"><span data-stu-id="08d9c-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="08d9c-111">要刪除的套件。</span><span class="sxs-lookup"><span data-stu-id="08d9c-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="08d9c-112">要刪除的套件版本。</span><span class="sxs-lookup"><span data-stu-id="08d9c-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="08d9c-113">選項</span><span class="sxs-lookup"><span data-stu-id="08d9c-113">Options</span></span>

`-h|--help`

<span data-ttu-id="08d9c-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="08d9c-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="08d9c-115">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="08d9c-115">Specifies the server URL.</span></span> <span data-ttu-id="08d9c-116">支援的 nuget.org URL 包括 `http://www.nuget.org`、`http://www.nuget.org/api/v3` 和 `http://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="08d9c-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="08d9c-117">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="08d9c-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="08d9c-118">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="08d9c-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="08d9c-119">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="08d9c-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="08d9c-120">強制命令列輸出採用英文。</span><span class="sxs-lookup"><span data-stu-id="08d9c-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="08d9c-121">範例</span><span class="sxs-lookup"><span data-stu-id="08d9c-121">Examples</span></span>

<span data-ttu-id="08d9c-122">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：</span><span class="sxs-lookup"><span data-stu-id="08d9c-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="08d9c-123">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：</span><span class="sxs-lookup"><span data-stu-id="08d9c-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`