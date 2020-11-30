---
title: dotnet remove package 命令
description: dotnet remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2020
ms.locfileid: "81463449"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="5458d-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="5458d-103">dotnet remove package</span></span>

<span data-ttu-id="5458d-104">本文 **適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="5458d-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5458d-105">名稱</span><span class="sxs-lookup"><span data-stu-id="5458d-105">Name</span></span>

<span data-ttu-id="5458d-106">`dotnet remove package` - 從專案檔中移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="5458d-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5458d-107">概要</span><span class="sxs-lookup"><span data-stu-id="5458d-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a><span data-ttu-id="5458d-108">描述</span><span class="sxs-lookup"><span data-stu-id="5458d-108">Description</span></span>

<span data-ttu-id="5458d-109">`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="5458d-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="5458d-110">引數</span><span class="sxs-lookup"><span data-stu-id="5458d-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="5458d-111">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="5458d-111">Specifies the project file.</span></span> <span data-ttu-id="5458d-112">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="5458d-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5458d-113">要移除的套件參考。</span><span class="sxs-lookup"><span data-stu-id="5458d-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="5458d-114">選項</span><span class="sxs-lookup"><span data-stu-id="5458d-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5458d-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5458d-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5458d-116">範例</span><span class="sxs-lookup"><span data-stu-id="5458d-116">Examples</span></span>

- <span data-ttu-id="5458d-117">`Newtonsoft.Json`從目前目錄中的專案移除 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="5458d-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
