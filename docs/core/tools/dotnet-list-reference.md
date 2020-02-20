---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503711"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="1ba07-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="1ba07-103">dotnet list reference</span></span>

<span data-ttu-id="1ba07-104">**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="1ba07-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1ba07-105">名稱</span><span class="sxs-lookup"><span data-stu-id="1ba07-105">Name</span></span>

<span data-ttu-id="1ba07-106">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="1ba07-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ba07-107">概要</span><span class="sxs-lookup"><span data-stu-id="1ba07-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="1ba07-108">描述</span><span class="sxs-lookup"><span data-stu-id="1ba07-108">Description</span></span>

<span data-ttu-id="1ba07-109">`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。</span><span class="sxs-lookup"><span data-stu-id="1ba07-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="1ba07-110">引數</span><span class="sxs-lookup"><span data-stu-id="1ba07-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="1ba07-111">指定要用來列出參考的專案或解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="1ba07-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="1ba07-112">如果未指定，命令會在目前的目錄中搜尋專案檔。</span><span class="sxs-lookup"><span data-stu-id="1ba07-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="1ba07-113">選項。</span><span class="sxs-lookup"><span data-stu-id="1ba07-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="1ba07-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="1ba07-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="1ba07-115">範例</span><span class="sxs-lookup"><span data-stu-id="1ba07-115">Examples</span></span>

* <span data-ttu-id="1ba07-116">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="1ba07-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="1ba07-117">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="1ba07-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
