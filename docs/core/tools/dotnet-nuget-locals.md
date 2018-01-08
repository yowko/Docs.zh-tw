---
title: "dotnet nuget locals 命令 - .NET Core CLI"
description: "dotnet nuget locals 命令會清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 9c8df8e457a9883b86abd0505c0c682d849bc7b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="6d8a6-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="6d8a6-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6d8a6-104">名稱</span><span class="sxs-lookup"><span data-stu-id="6d8a6-104">Name</span></span>

<span data-ttu-id="6d8a6-105">`dotnet nuget locals` - 清除或列出本機 NuGet 資源。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6d8a6-106">概要</span><span class="sxs-lookup"><span data-stu-id="6d8a6-106">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="6d8a6-107">描述</span><span class="sxs-lookup"><span data-stu-id="6d8a6-107">Description</span></span>

<span data-ttu-id="6d8a6-108">`dotnet nuget locals` 命令會清除或列出 http-request 快取、暫時快取，或整部電腦全域套件資料夾中的本機 NuGet 資源。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="6d8a6-109">引數</span><span class="sxs-lookup"><span data-stu-id="6d8a6-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="6d8a6-110">下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="6d8a6-110">One of the following values:</span></span>

* <span data-ttu-id="6d8a6-111">`all` - 指出指定的作業會套用至所有快取類型：http-request 快取、全域套件快取和暫時快取。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-111">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="6d8a6-112">`http-cache` - 指出指定的作業只套用至 http-request 快取。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-112">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="6d8a6-113">其他快取位置不受影響。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-113">The other cache locations are not affected.</span></span>
* <span data-ttu-id="6d8a6-114">`global-packages` - 指出指定的作業只套用至全域套件快取。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-114">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="6d8a6-115">其他快取位置不受影響。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-115">The other cache locations are not affected.</span></span>
* <span data-ttu-id="6d8a6-116">`temp` - 指出指定的作業只套用至暫時快取。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-116">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="6d8a6-117">其他快取位置不受影響。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-117">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="6d8a6-118">選項</span><span class="sxs-lookup"><span data-stu-id="6d8a6-118">Options</span></span>

`-h|--help`

<span data-ttu-id="6d8a6-119">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-119">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="6d8a6-120">清除選項會針對指定的快取類型執行清除作業。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-120">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="6d8a6-121">系統會以遞迴方式刪除快取目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-121">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="6d8a6-122">執行的使用者/群組必須具有快取目錄中檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-122">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="6d8a6-123">如果沒有權限，則會顯示錯誤，指出尚未清除的檔案/資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-123">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="6d8a6-124">list 選項是用來顯示指定之快取類型的位置。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-124">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="6d8a6-125">強制命令列輸出採用英文。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-125">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="6d8a6-126">範例</span><span class="sxs-lookup"><span data-stu-id="6d8a6-126">Examples</span></span>

<span data-ttu-id="6d8a6-127">顯示所有本機快取目錄的路徑 (http-cache 目錄、global-packages 快取目錄及暫時快取目錄)：</span><span class="sxs-lookup"><span data-stu-id="6d8a6-127">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="6d8a6-128">顯示本機 http-cache 目錄的路徑：</span><span class="sxs-lookup"><span data-stu-id="6d8a6-128">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="6d8a6-129">清除所有本機快取目錄的所有檔案 (http-cache 目錄、global-packages 快取目錄及暫時快取目錄)：</span><span class="sxs-lookup"><span data-stu-id="6d8a6-129">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="6d8a6-130">清除本機 global-packages 快取目錄中的所有檔案：</span><span class="sxs-lookup"><span data-stu-id="6d8a6-130">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="6d8a6-131">清除本機暫時快取目錄中的所有檔案：</span><span class="sxs-lookup"><span data-stu-id="6d8a6-131">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="6d8a6-132">疑難排解</span><span class="sxs-lookup"><span data-stu-id="6d8a6-132">Troubleshooting</span></span>

<span data-ttu-id="6d8a6-133">如需使用 `dotnet nuget locals` 命令時常見的問題與錯誤資訊，請參閱[管理 NuGet 快取](/nuget/consume-packages/managing-the-nuget-cache)。</span><span class="sxs-lookup"><span data-stu-id="6d8a6-133">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>