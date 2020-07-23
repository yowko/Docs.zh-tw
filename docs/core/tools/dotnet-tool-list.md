---
title: dotnet tool list 命令
description: Dotnet tool list 命令會列出安裝在您電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 4035c5be233232e53c6d7150485f737108c1e18d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925458"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="4b476-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="4b476-103">dotnet tool list</span></span>

<span data-ttu-id="4b476-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="4b476-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4b476-105">Name</span><span class="sxs-lookup"><span data-stu-id="4b476-105">Name</span></span>

<span data-ttu-id="4b476-106">`dotnet tool list`-列出目前安裝在您電腦上之指定類型的所有[.Net Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4b476-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4b476-107">概要</span><span class="sxs-lookup"><span data-stu-id="4b476-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="4b476-108">描述</span><span class="sxs-lookup"><span data-stu-id="4b476-108">Description</span></span>

<span data-ttu-id="4b476-109">此 `dotnet tool list` 命令可讓您列出電腦上所安裝的所有 .Net Core 全域、工具路徑或本機工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="4b476-110">此命令會列出封裝名稱、已安裝的版本，以及工具命令。</span><span class="sxs-lookup"><span data-stu-id="4b476-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="4b476-111">若要使用命令，您可以指定下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4b476-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="4b476-112">若要列出安裝在預設位置的全域工具，請使用 `--global` 選項</span><span class="sxs-lookup"><span data-stu-id="4b476-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="4b476-113">若要列出自訂位置中安裝的通用工具，請使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="4b476-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="4b476-114">若要列出本機工具，請使用 `--local` 選項，或省略 `--global` 、 `--tool-path` 和 `--local` 選項。</span><span class="sxs-lookup"><span data-stu-id="4b476-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="4b476-115">**從 .NET Core SDK 3.0 開始提供本機工具。**</span><span class="sxs-lookup"><span data-stu-id="4b476-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="4b476-116">選項。</span><span class="sxs-lookup"><span data-stu-id="4b476-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="4b476-117">列出使用者範圍的通用工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-117">Lists user-wide global tools.</span></span> <span data-ttu-id="4b476-118">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="4b476-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="4b476-119">省略 `--global` 和都會 `--tool-path` 列出本機工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4b476-120">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4b476-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="4b476-121">列出目前目錄的本機工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="4b476-122">無法與 `--global` 或 `--tool-path` 選項結合。</span><span class="sxs-lookup"><span data-stu-id="4b476-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="4b476-123">`--global` `--tool-path` 即使未指定，也會省略和列出本機工具 `--local` 。</span><span class="sxs-lookup"><span data-stu-id="4b476-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="4b476-124">指定要在其中尋找通用工具的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="4b476-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="4b476-125">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="4b476-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="4b476-126">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="4b476-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="4b476-127">省略 `--global` 和都會 `--tool-path` 列出本機工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="4b476-128">範例</span><span class="sxs-lookup"><span data-stu-id="4b476-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="4b476-129">列出電腦上全使用者安裝的所有通用工具（目前的使用者設定檔）。</span><span class="sxs-lookup"><span data-stu-id="4b476-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="4b476-130">列出特定 Windows 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="4b476-131">列出特定 Linux/macOS 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="4b476-132">**`dotnet tool list`** 或**`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="4b476-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="4b476-133">列出目前目錄中所有可用的本機工具。</span><span class="sxs-lookup"><span data-stu-id="4b476-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b476-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b476-134">See also</span></span>

- [<span data-ttu-id="4b476-135">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="4b476-135">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="4b476-136">教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="4b476-136">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="4b476-137">教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具</span><span class="sxs-lookup"><span data-stu-id="4b476-137">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
