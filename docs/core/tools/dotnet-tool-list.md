---
title: dotnet tool list 命令
description: Dotnet 工具清單命令會列出電腦上安裝的 .NET 工具。
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634281"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="9fc55-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="9fc55-103">dotnet tool list</span></span>

<span data-ttu-id="9fc55-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="9fc55-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9fc55-105">名稱</span><span class="sxs-lookup"><span data-stu-id="9fc55-105">Name</span></span>

<span data-ttu-id="9fc55-106">`dotnet tool list` -列出電腦上目前已安裝之指定型別的所有 [.net 工具](global-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="9fc55-106">`dotnet tool list` - Lists all [.NET tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9fc55-107">概要</span><span class="sxs-lookup"><span data-stu-id="9fc55-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="9fc55-108">描述</span><span class="sxs-lookup"><span data-stu-id="9fc55-108">Description</span></span>

<span data-ttu-id="9fc55-109">此 `dotnet tool list` 命令會提供一種方式，讓您列出電腦上安裝的所有 .net 全域、工具路徑或本機工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-109">The `dotnet tool list` command provides a way for you to list all .NET global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="9fc55-110">此命令會列出封裝名稱、安裝的版本，以及工具命令。</span><span class="sxs-lookup"><span data-stu-id="9fc55-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="9fc55-111">若要使用命令，您可以指定下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9fc55-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="9fc55-112">若要列出安裝在預設位置的通用工具，請使用 `--global` 選項</span><span class="sxs-lookup"><span data-stu-id="9fc55-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="9fc55-113">若要列出在自訂位置安裝的通用工具，請使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="9fc55-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="9fc55-114">若要列出本機工具，請使用 `--local` 選項或省略 `--global` 、 `--tool-path` 和 `--local` 選項。</span><span class="sxs-lookup"><span data-stu-id="9fc55-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="9fc55-115">**從 .NET Core SDK 3.0 開始，可以使用本機工具。**</span><span class="sxs-lookup"><span data-stu-id="9fc55-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="9fc55-116">選項</span><span class="sxs-lookup"><span data-stu-id="9fc55-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="9fc55-117">列出使用者範圍的通用工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-117">Lists user-wide global tools.</span></span> <span data-ttu-id="9fc55-118">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="9fc55-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="9fc55-119">省略 `--global` 和 `--tool-path` 列出本機工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9fc55-120">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="9fc55-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="9fc55-121">列出目前目錄的本機工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="9fc55-122">無法與 `--global` 或 `--tool-path` 選項結合。</span><span class="sxs-lookup"><span data-stu-id="9fc55-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="9fc55-123">`--global`即使未指定，也會同時省略和 `--tool-path` 列出本機工具 `--local` 。</span><span class="sxs-lookup"><span data-stu-id="9fc55-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="9fc55-124">指定要在其中尋找通用工具的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="9fc55-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="9fc55-125">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="9fc55-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="9fc55-126">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="9fc55-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="9fc55-127">省略 `--global` 和 `--tool-path` 列出本機工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="9fc55-128">範例</span><span class="sxs-lookup"><span data-stu-id="9fc55-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="9fc55-129">列出所有在您的電腦上全使用者安裝的通用工具 (目前的使用者設定檔) 。</span><span class="sxs-lookup"><span data-stu-id="9fc55-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="9fc55-130">列出特定 Windows 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="9fc55-131">列出特定 Linux/macOS 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="9fc55-132">**`dotnet tool list`** 或 **`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="9fc55-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="9fc55-133">列出目前目錄中所有可用的本機工具。</span><span class="sxs-lookup"><span data-stu-id="9fc55-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fc55-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fc55-134">See also</span></span>

- [<span data-ttu-id="9fc55-135">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="9fc55-135">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="9fc55-136">教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具</span><span class="sxs-lookup"><span data-stu-id="9fc55-136">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="9fc55-137">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="9fc55-137">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
