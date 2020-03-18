---
title: dotnet remove package 命令
description: dotnet remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503641"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="f6fa7-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="f6fa7-103">dotnet remove package</span></span>

<span data-ttu-id="f6fa7-104">**本文適用于：✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="f6fa7-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f6fa7-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f6fa7-105">Name</span></span>

<span data-ttu-id="f6fa7-106">`dotnet remove package` - 從專案檔中移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="f6fa7-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6fa7-107">概要</span><span class="sxs-lookup"><span data-stu-id="f6fa7-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f6fa7-108">描述</span><span class="sxs-lookup"><span data-stu-id="f6fa7-108">Description</span></span>

<span data-ttu-id="f6fa7-109">`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="f6fa7-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="f6fa7-110">引數</span><span class="sxs-lookup"><span data-stu-id="f6fa7-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f6fa7-111">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="f6fa7-111">Specifies the project file.</span></span> <span data-ttu-id="f6fa7-112">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="f6fa7-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="f6fa7-113">要移除的套件參考。</span><span class="sxs-lookup"><span data-stu-id="f6fa7-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="f6fa7-114">選項。</span><span class="sxs-lookup"><span data-stu-id="f6fa7-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f6fa7-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f6fa7-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f6fa7-116">範例</span><span class="sxs-lookup"><span data-stu-id="f6fa7-116">Examples</span></span>

- <span data-ttu-id="f6fa7-117">從`Newtonsoft.Json`目前的目錄中的專案中刪除 NuGet 包：</span><span class="sxs-lookup"><span data-stu-id="f6fa7-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
