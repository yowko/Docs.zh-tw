---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117680"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="9b163-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="9b163-103">dotnet list reference</span></span>

<span data-ttu-id="9b163-104">**本主題適用於：✓** .NET Core 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="9b163-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="9b163-105">名稱</span><span class="sxs-lookup"><span data-stu-id="9b163-105">Name</span></span>

<span data-ttu-id="9b163-106">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="9b163-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9b163-107">概要</span><span class="sxs-lookup"><span data-stu-id="9b163-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="9b163-108">描述</span><span class="sxs-lookup"><span data-stu-id="9b163-108">Description</span></span>

<span data-ttu-id="9b163-109">`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。</span><span class="sxs-lookup"><span data-stu-id="9b163-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="9b163-110">引數</span><span class="sxs-lookup"><span data-stu-id="9b163-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="9b163-111">指定要用來列出參考的專案或解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="9b163-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="9b163-112">如果未指定，命令會在目前的目錄中搜尋專案檔。</span><span class="sxs-lookup"><span data-stu-id="9b163-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="9b163-113">選項</span><span class="sxs-lookup"><span data-stu-id="9b163-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="9b163-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="9b163-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="9b163-115">範例</span><span class="sxs-lookup"><span data-stu-id="9b163-115">Examples</span></span>

* <span data-ttu-id="9b163-116">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="9b163-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="9b163-117">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="9b163-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
