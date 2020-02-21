---
title: dotnet tool list 命令
description: Dotnet tool list 命令會列出安裝在您電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: bb74cfeaf441cf8a1a030d97d16655f85d8267d1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543452"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="55d2a-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="55d2a-103">dotnet tool list</span></span>

<span data-ttu-id="55d2a-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="55d2a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="55d2a-105">名稱</span><span class="sxs-lookup"><span data-stu-id="55d2a-105">Name</span></span>

<span data-ttu-id="55d2a-106">`dotnet tool list`-列出目前安裝在您電腦上之指定類型的所有[.Net Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="55d2a-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="55d2a-107">概要</span><span class="sxs-lookup"><span data-stu-id="55d2a-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="55d2a-108">描述</span><span class="sxs-lookup"><span data-stu-id="55d2a-108">Description</span></span>

<span data-ttu-id="55d2a-109">`dotnet tool list` 命令可讓您列出電腦上所安裝的所有 .NET Core 全域、工具路徑或本機工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="55d2a-110">此命令會列出封裝名稱、已安裝的版本，以及工具命令。</span><span class="sxs-lookup"><span data-stu-id="55d2a-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="55d2a-111">若要使用命令，您可以指定下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="55d2a-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="55d2a-112">預設位置中安裝的通用工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-112">A global tool installed in the default location.</span></span> <span data-ttu-id="55d2a-113">使用 [`--global`] 選項</span><span class="sxs-lookup"><span data-stu-id="55d2a-113">Use the `--global` option</span></span>
* <span data-ttu-id="55d2a-114">安裝在自訂位置的通用工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="55d2a-115">使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="55d2a-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="55d2a-116">本機工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-116">A local tool.</span></span> <span data-ttu-id="55d2a-117">省略 `--global` 並 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="55d2a-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="55d2a-118">**從 .NET Core SDK 3.0 開始提供本機工具。**</span><span class="sxs-lookup"><span data-stu-id="55d2a-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="55d2a-119">選項。</span><span class="sxs-lookup"><span data-stu-id="55d2a-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="55d2a-120">列出使用者範圍的通用工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-120">Lists user-wide global tools.</span></span> <span data-ttu-id="55d2a-121">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="55d2a-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="55d2a-122">省略 `--global` 和 `--tool-path` 會列出本機工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="55d2a-123">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="55d2a-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="55d2a-124">指定要在其中尋找通用工具的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="55d2a-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="55d2a-125">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="55d2a-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="55d2a-126">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="55d2a-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="55d2a-127">省略 `--global` 和 `--tool-path` 會列出本機工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span> 

## <a name="examples"></a><span data-ttu-id="55d2a-128">範例</span><span class="sxs-lookup"><span data-stu-id="55d2a-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="55d2a-129">列出電腦上全使用者安裝的所有通用工具（目前的使用者設定檔）。</span><span class="sxs-lookup"><span data-stu-id="55d2a-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="55d2a-130">列出特定 Windows 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="55d2a-131">列出特定 Linux/macOS 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="55d2a-132">列出目前目錄中所有可用的本機工具。</span><span class="sxs-lookup"><span data-stu-id="55d2a-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="55d2a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55d2a-133">See also</span></span>

- [<span data-ttu-id="55d2a-134">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="55d2a-134">.NET Core tools</span></span>](global-tools.md)
