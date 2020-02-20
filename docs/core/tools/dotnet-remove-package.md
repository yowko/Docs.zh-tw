---
title: dotnet remove package 命令
description: dotnet remove package 命令提供方便的選項，以移除專案的 NuGet 套件參考。
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503641"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="22cc2-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="22cc2-103">dotnet remove package</span></span>

<span data-ttu-id="22cc2-104">**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="22cc2-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="22cc2-105">名稱</span><span class="sxs-lookup"><span data-stu-id="22cc2-105">Name</span></span>

<span data-ttu-id="22cc2-106">`dotnet remove package` - 從專案檔中移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="22cc2-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="22cc2-107">概要</span><span class="sxs-lookup"><span data-stu-id="22cc2-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="22cc2-108">描述</span><span class="sxs-lookup"><span data-stu-id="22cc2-108">Description</span></span>

<span data-ttu-id="22cc2-109">`dotnet remove package` 命令提供方便的選項，以從專案中移除 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="22cc2-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="22cc2-110">引數</span><span class="sxs-lookup"><span data-stu-id="22cc2-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="22cc2-111">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="22cc2-111">Specifies the project file.</span></span> <span data-ttu-id="22cc2-112">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="22cc2-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="22cc2-113">要移除的套件參考。</span><span class="sxs-lookup"><span data-stu-id="22cc2-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="22cc2-114">選項。</span><span class="sxs-lookup"><span data-stu-id="22cc2-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="22cc2-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="22cc2-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="22cc2-116">範例</span><span class="sxs-lookup"><span data-stu-id="22cc2-116">Examples</span></span>

- <span data-ttu-id="22cc2-117">從目前目錄中的專案移除 `Newtonsoft.Json` NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="22cc2-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
