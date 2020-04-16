---
title: dotnet tool list 命令
description: dotnet 工具清單命令列出了安裝在電腦上的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463352"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="6579d-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="6579d-103">dotnet tool list</span></span>

<span data-ttu-id="6579d-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="6579d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6579d-105">名稱</span><span class="sxs-lookup"><span data-stu-id="6579d-105">Name</span></span>

<span data-ttu-id="6579d-106">`dotnet tool list`- 列出電腦上目前安裝的指定類型的所有[.NET 核心工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="6579d-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6579d-107">概要</span><span class="sxs-lookup"><span data-stu-id="6579d-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="6579d-108">描述</span><span class="sxs-lookup"><span data-stu-id="6579d-108">Description</span></span>

<span data-ttu-id="6579d-109">該`dotnet tool list`指令提供了一種列出電腦上安裝的所有 .NET Core 全域、工具路徑或本地工具的方法。</span><span class="sxs-lookup"><span data-stu-id="6579d-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="6579d-110">該命令列出包名稱、已安裝的版本和工具命令。</span><span class="sxs-lookup"><span data-stu-id="6579d-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="6579d-111">要使用 此指令,請指定以下指令之一:</span><span class="sxs-lookup"><span data-stu-id="6579d-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="6579d-112">安裝在預設位置的全域工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-112">A global tool installed in the default location.</span></span> <span data-ttu-id="6579d-113">使用選項`--global`</span><span class="sxs-lookup"><span data-stu-id="6579d-113">Use the `--global` option</span></span>
* <span data-ttu-id="6579d-114">安裝在自定義位置的全域工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="6579d-115">使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="6579d-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="6579d-116">本地工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-116">A local tool.</span></span> <span data-ttu-id="6579d-117">省略和`--global``--tool-path`選項。</span><span class="sxs-lookup"><span data-stu-id="6579d-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="6579d-118">**本地工具可從 .NET 核心 SDK 3.0 開始。**</span><span class="sxs-lookup"><span data-stu-id="6579d-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="6579d-119">選項。</span><span class="sxs-lookup"><span data-stu-id="6579d-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="6579d-120">列出用戶範圍的全域工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-120">Lists user-wide global tools.</span></span> <span data-ttu-id="6579d-121">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="6579d-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="6579d-122">省略和`--global``--tool-path`列出本地工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6579d-123">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="6579d-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="6579d-124">指定查找全域工具的自定義位置。</span><span class="sxs-lookup"><span data-stu-id="6579d-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="6579d-125">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="6579d-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="6579d-126">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="6579d-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="6579d-127">省略和`--global``--tool-path`列出本地工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="6579d-128">範例</span><span class="sxs-lookup"><span data-stu-id="6579d-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="6579d-129">列出電腦上安裝的使用者範圍的所有全域工具(當前使用者配置檔)。</span><span class="sxs-lookup"><span data-stu-id="6579d-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="6579d-130">列出特定 Windows 目錄中的全域工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="6579d-131">列出來自特定 Linux/macOS 目錄的全域工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="6579d-132">列出目前目錄中可用的所有本地工具。</span><span class="sxs-lookup"><span data-stu-id="6579d-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="6579d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6579d-133">See also</span></span>

- [<span data-ttu-id="6579d-134">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="6579d-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="6579d-135">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="6579d-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="6579d-136">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="6579d-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
