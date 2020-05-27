---
title: dotnet list reference 命令
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802757"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="5ffd0-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="5ffd0-103">dotnet list reference</span></span>

<span data-ttu-id="5ffd0-104">**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="5ffd0-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5ffd0-105">名稱</span><span class="sxs-lookup"><span data-stu-id="5ffd0-105">Name</span></span>

<span data-ttu-id="5ffd0-106">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="5ffd0-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5ffd0-107">概要</span><span class="sxs-lookup"><span data-stu-id="5ffd0-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="5ffd0-108">描述</span><span class="sxs-lookup"><span data-stu-id="5ffd0-108">Description</span></span>

<span data-ttu-id="5ffd0-109">`dotnet list reference` 命令提供方便的選項，以列出指定專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="5ffd0-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="5ffd0-110">引數</span><span class="sxs-lookup"><span data-stu-id="5ffd0-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="5ffd0-111">要處理的專案檔。</span><span class="sxs-lookup"><span data-stu-id="5ffd0-111">The project file to operate on.</span></span> <span data-ttu-id="5ffd0-112">如果未指定檔案，此命令將會在目前的目錄中搜尋一個檔案。</span><span class="sxs-lookup"><span data-stu-id="5ffd0-112">If a file is not specified, the command will search the current directory for one.</span></span>

## <a name="options"></a><span data-ttu-id="5ffd0-113">選項</span><span class="sxs-lookup"><span data-stu-id="5ffd0-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="5ffd0-114">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5ffd0-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5ffd0-115">範例</span><span class="sxs-lookup"><span data-stu-id="5ffd0-115">Examples</span></span>

* <span data-ttu-id="5ffd0-116">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="5ffd0-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="5ffd0-117">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="5ffd0-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
