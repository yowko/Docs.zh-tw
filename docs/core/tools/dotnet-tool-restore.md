---
title: 點網工具還原命令
description: dotnet 工具還原命令在您的電腦上安裝當前目錄範圍內的 .NET Core 本地工具。
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389621"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="f49cd-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="f49cd-103">dotnet tool restore</span></span>

<span data-ttu-id="f49cd-104">**本文適用於:✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="f49cd-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f49cd-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f49cd-105">Name</span></span>

<span data-ttu-id="f49cd-106">`dotnet tool restore`- 在電腦上安裝當前目錄範圍內的 .NET Core 本地工具。</span><span class="sxs-lookup"><span data-stu-id="f49cd-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f49cd-107">概要</span><span class="sxs-lookup"><span data-stu-id="f49cd-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="f49cd-108">描述</span><span class="sxs-lookup"><span data-stu-id="f49cd-108">Description</span></span>

<span data-ttu-id="f49cd-109">該`dotnet tool restore`命令查找目前目錄範圍內的工具清單檔,並安裝其中列出的工具。</span><span class="sxs-lookup"><span data-stu-id="f49cd-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="f49cd-110">關於清單檔案的資訊,請參考[本地端工具與](global-tools.md#install-a-local-tool)[呼叫本地端工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="f49cd-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="f49cd-111">引數</span><span class="sxs-lookup"><span data-stu-id="f49cd-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="f49cd-112">包含要安裝的 .NET Core 工具的 NuGet 套件的名稱/ ID。</span><span class="sxs-lookup"><span data-stu-id="f49cd-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="f49cd-113">選項。</span><span class="sxs-lookup"><span data-stu-id="f49cd-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f49cd-114">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="f49cd-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="f49cd-115">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="f49cd-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="f49cd-116">清單檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="f49cd-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="f49cd-117">防止並行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="f49cd-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="f49cd-118">將包源故障視為警告。</span><span class="sxs-lookup"><span data-stu-id="f49cd-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="f49cd-119">不要緩存包和 HTTP 請求。</span><span class="sxs-lookup"><span data-stu-id="f49cd-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="f49cd-120">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="f49cd-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="f49cd-121">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f49cd-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f49cd-122">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="f49cd-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f49cd-123">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f49cd-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="f49cd-124">範例</span><span class="sxs-lookup"><span data-stu-id="f49cd-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="f49cd-125">還原當前目錄的本地工具。</span><span class="sxs-lookup"><span data-stu-id="f49cd-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f49cd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f49cd-126">See also</span></span>

- [<span data-ttu-id="f49cd-127">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="f49cd-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f49cd-128">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="f49cd-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
