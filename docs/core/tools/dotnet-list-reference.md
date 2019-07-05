---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421835"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="57a6b-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="57a6b-103">dotnet list reference</span></span>

<span data-ttu-id="57a6b-104">**本主題適用於：✓** .NET Core 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="57a6b-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="57a6b-105">名稱</span><span class="sxs-lookup"><span data-stu-id="57a6b-105">Name</span></span>

<span data-ttu-id="57a6b-106">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="57a6b-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="57a6b-107">概要</span><span class="sxs-lookup"><span data-stu-id="57a6b-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="57a6b-108">說明</span><span class="sxs-lookup"><span data-stu-id="57a6b-108">Description</span></span>

<span data-ttu-id="57a6b-109">`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。</span><span class="sxs-lookup"><span data-stu-id="57a6b-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="57a6b-110">引數</span><span class="sxs-lookup"><span data-stu-id="57a6b-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="57a6b-111">指定要用來列出參考的專案或解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="57a6b-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="57a6b-112">如果未指定，命令會在目前的目錄中搜尋專案檔。</span><span class="sxs-lookup"><span data-stu-id="57a6b-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="57a6b-113">選項</span><span class="sxs-lookup"><span data-stu-id="57a6b-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="57a6b-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="57a6b-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="57a6b-115">範例</span><span class="sxs-lookup"><span data-stu-id="57a6b-115">Examples</span></span>

* <span data-ttu-id="57a6b-116">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="57a6b-116">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="57a6b-117">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="57a6b-117">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```
