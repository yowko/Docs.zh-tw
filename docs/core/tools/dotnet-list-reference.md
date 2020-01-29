---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733217"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="fff7f-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="fff7f-103">dotnet list reference</span></span>

<span data-ttu-id="fff7f-104">**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="fff7f-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="fff7f-105">Name</span><span class="sxs-lookup"><span data-stu-id="fff7f-105">Name</span></span>

<span data-ttu-id="fff7f-106">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="fff7f-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fff7f-107">概要</span><span class="sxs-lookup"><span data-stu-id="fff7f-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="fff7f-108">描述</span><span class="sxs-lookup"><span data-stu-id="fff7f-108">Description</span></span>

<span data-ttu-id="fff7f-109">`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。</span><span class="sxs-lookup"><span data-stu-id="fff7f-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="fff7f-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="fff7f-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="fff7f-111">指定要用來列出參考的專案或解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="fff7f-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="fff7f-112">如果未指定，命令會在目前的目錄中搜尋專案檔。</span><span class="sxs-lookup"><span data-stu-id="fff7f-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="fff7f-113">選項</span><span class="sxs-lookup"><span data-stu-id="fff7f-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="fff7f-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="fff7f-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="fff7f-115">範例</span><span class="sxs-lookup"><span data-stu-id="fff7f-115">Examples</span></span>

* <span data-ttu-id="fff7f-116">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="fff7f-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="fff7f-117">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="fff7f-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
