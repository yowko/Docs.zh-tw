---
title: dotnet tool restore 命令
description: Dotnet tool restore 命令會在您的電腦上安裝目前目錄範圍內的 .NET 本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 1b7fd10102f2c957b3eb235f6897b60bc8ca9c07
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634268"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="7cdae-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="7cdae-103">dotnet tool restore</span></span>

<span data-ttu-id="7cdae-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="7cdae-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7cdae-105">名稱</span><span class="sxs-lookup"><span data-stu-id="7cdae-105">Name</span></span>

<span data-ttu-id="7cdae-106">`dotnet tool restore` -在您的電腦上安裝目前目錄範圍內的 .NET 本機工具。</span><span class="sxs-lookup"><span data-stu-id="7cdae-106">`dotnet tool restore` - Installs on your machine the .NET local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7cdae-107">概要</span><span class="sxs-lookup"><span data-stu-id="7cdae-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="7cdae-108">描述</span><span class="sxs-lookup"><span data-stu-id="7cdae-108">Description</span></span>

<span data-ttu-id="7cdae-109">此 `dotnet tool restore` 命令會尋找目前目錄範圍內的工具資訊清單檔，並安裝其中所列的工具。</span><span class="sxs-lookup"><span data-stu-id="7cdae-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="7cdae-110">如需資訊清單檔案的相關資訊，請參閱 [安裝本機工具](global-tools.md#install-a-local-tool) 和叫 [用本機工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="7cdae-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="7cdae-111">選項</span><span class="sxs-lookup"><span data-stu-id="7cdae-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="7cdae-112">要使用的 NuGet 組態檔 ( *nuget.config* )。</span><span class="sxs-lookup"><span data-stu-id="7cdae-112">The NuGet configuration ( *nuget.config* ) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="7cdae-113">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="7cdae-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="7cdae-114">資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="7cdae-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="7cdae-115">防止平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="7cdae-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="7cdae-116">將封裝來源失敗視為警告。</span><span class="sxs-lookup"><span data-stu-id="7cdae-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="7cdae-117">請勿快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="7cdae-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="7cdae-118">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="7cdae-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="7cdae-119">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7cdae-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7cdae-120">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="7cdae-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7cdae-121">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="7cdae-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="7cdae-122">範例</span><span class="sxs-lookup"><span data-stu-id="7cdae-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="7cdae-123">還原目前目錄的本機工具。</span><span class="sxs-lookup"><span data-stu-id="7cdae-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cdae-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cdae-124">See also</span></span>

- [<span data-ttu-id="7cdae-125">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="7cdae-125">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="7cdae-126">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="7cdae-126">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
