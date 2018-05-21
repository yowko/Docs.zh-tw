---
title: dotnet nuget delete 命令 - .NET Core CLI
description: dotnet-nuget-delete 命令會從伺服器刪除或取消列出套件。
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 639ade54bfed5eb2de89bdb3b7f451393b4be187
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="b6f63-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="b6f63-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b6f63-104">名稱</span><span class="sxs-lookup"><span data-stu-id="b6f63-104">Name</span></span>

<span data-ttu-id="b6f63-105">`dotnet nuget delete` - 從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="b6f63-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b6f63-106">概要</span><span class="sxs-lookup"><span data-stu-id="b6f63-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="b6f63-107">描述</span><span class="sxs-lookup"><span data-stu-id="b6f63-107">Description</span></span>

<span data-ttu-id="b6f63-108">`dotnet nuget delete` 命令會從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="b6f63-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="b6f63-109">對於 [nuget.org](https://www.nuget.org/)，該動作是取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="b6f63-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="b6f63-110">引數</span><span class="sxs-lookup"><span data-stu-id="b6f63-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="b6f63-111">要刪除的套件。</span><span class="sxs-lookup"><span data-stu-id="b6f63-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="b6f63-112">要刪除的套件版本。</span><span class="sxs-lookup"><span data-stu-id="b6f63-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="b6f63-113">選項</span><span class="sxs-lookup"><span data-stu-id="b6f63-113">Options</span></span>

`-h|--help`

<span data-ttu-id="b6f63-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b6f63-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="b6f63-115">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="b6f63-115">Specifies the server URL.</span></span> <span data-ttu-id="b6f63-116">支援的 nuget.org URL 包括 `http://www.nuget.org`、`http://www.nuget.org/api/v3` 和 `http://www.nuget.org/api/v2/package`。</span><span class="sxs-lookup"><span data-stu-id="b6f63-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="b6f63-117">對於私用摘要，請取代主機名稱 (例如，`%hostname%/api/v3`)。</span><span class="sxs-lookup"><span data-stu-id="b6f63-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="b6f63-118">不提示使用者輸入或確認。</span><span class="sxs-lookup"><span data-stu-id="b6f63-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="b6f63-119">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="b6f63-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="b6f63-120">強制命令列輸出採用英文。</span><span class="sxs-lookup"><span data-stu-id="b6f63-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="b6f63-121">範例</span><span class="sxs-lookup"><span data-stu-id="b6f63-121">Examples</span></span>

<span data-ttu-id="b6f63-122">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版：</span><span class="sxs-lookup"><span data-stu-id="b6f63-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="b6f63-123">刪除 `Microsoft.AspNetCore.Mvc` 套件 1.0 版，不提示使用者輸入認證或其他輸入：</span><span class="sxs-lookup"><span data-stu-id="b6f63-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`