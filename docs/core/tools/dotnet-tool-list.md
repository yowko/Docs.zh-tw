---
title: dotnet tool list 命令
description: dotnet 工具清單命令列出了安裝在電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847868"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="0fcad-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="0fcad-103">dotnet tool list</span></span>

<span data-ttu-id="0fcad-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="0fcad-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0fcad-105">名稱</span><span class="sxs-lookup"><span data-stu-id="0fcad-105">Name</span></span>

<span data-ttu-id="0fcad-106">`dotnet tool list`- 列出電腦上當前安裝的指定類型的所有[.NET 核心工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0fcad-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0fcad-107">概要</span><span class="sxs-lookup"><span data-stu-id="0fcad-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="0fcad-108">描述</span><span class="sxs-lookup"><span data-stu-id="0fcad-108">Description</span></span>

<span data-ttu-id="0fcad-109">該`dotnet tool list`命令提供了一種列出電腦上安裝的所有 .NET Core 全域、工具路徑或本地工具的方法。</span><span class="sxs-lookup"><span data-stu-id="0fcad-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="0fcad-110">該命令列出包名稱、已安裝的版本和工具命令。</span><span class="sxs-lookup"><span data-stu-id="0fcad-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="0fcad-111">要使用 該命令，請指定以下命令之一：</span><span class="sxs-lookup"><span data-stu-id="0fcad-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="0fcad-112">安裝在預設位置的全域工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-112">A global tool installed in the default location.</span></span> <span data-ttu-id="0fcad-113">使用選項`--global`</span><span class="sxs-lookup"><span data-stu-id="0fcad-113">Use the `--global` option</span></span>
* <span data-ttu-id="0fcad-114">安裝在自訂位置的全域工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="0fcad-115">使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="0fcad-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="0fcad-116">本地工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-116">A local tool.</span></span> <span data-ttu-id="0fcad-117">省略 和`--global``--tool-path`選項。</span><span class="sxs-lookup"><span data-stu-id="0fcad-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="0fcad-118">**本地工具可從 .NET 核心 SDK 3.0 開始。**</span><span class="sxs-lookup"><span data-stu-id="0fcad-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="0fcad-119">選項。</span><span class="sxs-lookup"><span data-stu-id="0fcad-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="0fcad-120">列出使用者範圍的全域工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-120">Lists user-wide global tools.</span></span> <span data-ttu-id="0fcad-121">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="0fcad-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="0fcad-122">省略和`--global``--tool-path`列出本地工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0fcad-123">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="0fcad-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="0fcad-124">指定查找全域工具的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="0fcad-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="0fcad-125">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="0fcad-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="0fcad-126">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="0fcad-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="0fcad-127">省略和`--global``--tool-path`列出本地工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="0fcad-128">範例</span><span class="sxs-lookup"><span data-stu-id="0fcad-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="0fcad-129">列出電腦上安裝的使用者範圍的所有全域工具（當前使用者設定檔）。</span><span class="sxs-lookup"><span data-stu-id="0fcad-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="0fcad-130">列出特定 Windows 目錄中的全域工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="0fcad-131">列出來自特定 Linux/macOS 目錄的全域工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="0fcad-132">列出目前的目錄中可用的所有本地工具。</span><span class="sxs-lookup"><span data-stu-id="0fcad-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fcad-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fcad-133">See also</span></span>

- [<span data-ttu-id="0fcad-134">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="0fcad-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="0fcad-135">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="0fcad-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="0fcad-136">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="0fcad-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
