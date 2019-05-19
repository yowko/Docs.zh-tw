---
title: dotnet nuget locals 命令
description: dotnet nuget locals 命令會清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 0a9fd7876aa4d1907eb37e6bac54295d938d36d3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632415"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="d65ff-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="d65ff-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d65ff-104">名稱</span><span class="sxs-lookup"><span data-stu-id="d65ff-104">Name</span></span>

<span data-ttu-id="d65ff-105">`dotnet nuget locals` - 清除或列出本機 NuGet 資源。</span><span class="sxs-lookup"><span data-stu-id="d65ff-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d65ff-106">概要</span><span class="sxs-lookup"><span data-stu-id="d65ff-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d65ff-107">說明</span><span class="sxs-lookup"><span data-stu-id="d65ff-107">Description</span></span>

<span data-ttu-id="d65ff-108">`dotnet nuget locals` 命令會清除或列出 http-request 快取、暫時快取，或整部電腦全域套件資料夾中的本機 NuGet 資源。</span><span class="sxs-lookup"><span data-stu-id="d65ff-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="d65ff-109">引數</span><span class="sxs-lookup"><span data-stu-id="d65ff-109">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="d65ff-110">要列出或清除的快取位置。</span><span class="sxs-lookup"><span data-stu-id="d65ff-110">The cache location to list or clear.</span></span> <span data-ttu-id="d65ff-111">它接受下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="d65ff-111">It accepts one of the following values:</span></span>

  * <span data-ttu-id="d65ff-112">`all` - 指出指定的作業會套用至所有快取類型：http-request 快取、全域套件快取和暫時快取。</span><span class="sxs-lookup"><span data-stu-id="d65ff-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="d65ff-113">`http-cache` - 指出指定的作業只套用至 http-request 快取。</span><span class="sxs-lookup"><span data-stu-id="d65ff-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="d65ff-114">其他快取位置不受影響。</span><span class="sxs-lookup"><span data-stu-id="d65ff-114">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="d65ff-115">`global-packages` - 指出指定的作業只套用至全域套件快取。</span><span class="sxs-lookup"><span data-stu-id="d65ff-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="d65ff-116">其他快取位置不受影響。</span><span class="sxs-lookup"><span data-stu-id="d65ff-116">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="d65ff-117">`temp` - 指出指定的作業只套用至暫時快取。</span><span class="sxs-lookup"><span data-stu-id="d65ff-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="d65ff-118">其他快取位置不受影響。</span><span class="sxs-lookup"><span data-stu-id="d65ff-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="d65ff-119">選項</span><span class="sxs-lookup"><span data-stu-id="d65ff-119">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="d65ff-120">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d65ff-120">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="d65ff-121">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="d65ff-121">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="d65ff-122">清除選項會針對指定的快取類型執行清除作業。</span><span class="sxs-lookup"><span data-stu-id="d65ff-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="d65ff-123">系統會以遞迴方式刪除快取目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="d65ff-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="d65ff-124">執行的使用者/群組必須具有快取目錄中檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="d65ff-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="d65ff-125">如果沒有權限，則會顯示錯誤，指出尚未清除的檔案/資料夾。</span><span class="sxs-lookup"><span data-stu-id="d65ff-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="d65ff-126">list 選項是用來顯示指定之快取類型的位置。</span><span class="sxs-lookup"><span data-stu-id="d65ff-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="d65ff-127">範例</span><span class="sxs-lookup"><span data-stu-id="d65ff-127">Examples</span></span>

* <span data-ttu-id="d65ff-128">顯示所有本機快取目錄的路徑 (http-cache 目錄、global-packages 快取目錄及暫時快取目錄)：</span><span class="sxs-lookup"><span data-stu-id="d65ff-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="d65ff-129">顯示本機 http-cache 目錄的路徑：</span><span class="sxs-lookup"><span data-stu-id="d65ff-129">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="d65ff-130">清除所有本機快取目錄的所有檔案 (http-cache 目錄、global-packages 快取目錄及暫時快取目錄)：</span><span class="sxs-lookup"><span data-stu-id="d65ff-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="d65ff-131">清除本機 global-packages 快取目錄中的所有檔案：</span><span class="sxs-lookup"><span data-stu-id="d65ff-131">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="d65ff-132">清除本機暫時快取目錄中的所有檔案：</span><span class="sxs-lookup"><span data-stu-id="d65ff-132">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="d65ff-133">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d65ff-133">Troubleshooting</span></span>

<span data-ttu-id="d65ff-134">如需使用 `dotnet nuget locals` 命令時常見的問題與錯誤資訊，請參閱[管理 NuGet 快取](/nuget/consume-packages/managing-the-nuget-cache)。</span><span class="sxs-lookup"><span data-stu-id="d65ff-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
