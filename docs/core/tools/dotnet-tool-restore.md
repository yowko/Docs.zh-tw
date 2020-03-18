---
title: 點網工具還原命令
description: dotnet 工具還原命令在您的電腦上安裝目前的目錄範圍內的 .NET Core 本地工具。
ms.date: 02/14/2020
ms.openlocfilehash: cb46f70afb58e482b6aedfddfbf5f3a0c40674f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146433"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="faaf2-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="faaf2-103">dotnet tool restore</span></span>

<span data-ttu-id="faaf2-104">**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="faaf2-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="faaf2-105">名稱</span><span class="sxs-lookup"><span data-stu-id="faaf2-105">Name</span></span>

<span data-ttu-id="faaf2-106">`dotnet tool restore`- 在電腦上安裝目前的目錄範圍內的 .NET Core 本地工具。</span><span class="sxs-lookup"><span data-stu-id="faaf2-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="faaf2-107">概要</span><span class="sxs-lookup"><span data-stu-id="faaf2-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [-interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="faaf2-108">描述</span><span class="sxs-lookup"><span data-stu-id="faaf2-108">Description</span></span>

<span data-ttu-id="faaf2-109">該`dotnet tool restore`命令查找目前的目錄範圍內的工具清單檔，並安裝其中列出的工具。</span><span class="sxs-lookup"><span data-stu-id="faaf2-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="faaf2-110">有關清單檔的資訊，請參閱[安裝本地工具和](global-tools.md#install-a-local-tool)[調用本地工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="faaf2-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="faaf2-111">引數</span><span class="sxs-lookup"><span data-stu-id="faaf2-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="faaf2-112">包含要安裝的 .NET Core 工具的 NuGet 包的名稱/ID。</span><span class="sxs-lookup"><span data-stu-id="faaf2-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="faaf2-113">選項。</span><span class="sxs-lookup"><span data-stu-id="faaf2-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="faaf2-114">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="faaf2-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="faaf2-115">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="faaf2-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="faaf2-116">清單檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="faaf2-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="faaf2-117">防止並行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="faaf2-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="faaf2-118">將包源故障視為警告。</span><span class="sxs-lookup"><span data-stu-id="faaf2-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="faaf2-119">不要緩存包和 HTTP 請求。</span><span class="sxs-lookup"><span data-stu-id="faaf2-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="faaf2-120">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="faaf2-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="faaf2-121">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="faaf2-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="faaf2-122">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="faaf2-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="faaf2-123">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="faaf2-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="faaf2-124">範例</span><span class="sxs-lookup"><span data-stu-id="faaf2-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="faaf2-125">還原目前的目錄的本地工具。</span><span class="sxs-lookup"><span data-stu-id="faaf2-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="faaf2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faaf2-126">See also</span></span>

- [<span data-ttu-id="faaf2-127">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="faaf2-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="faaf2-128">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="faaf2-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
