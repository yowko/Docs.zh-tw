---
title: dotnet 工具還原命令
description: Dotnet 工具 restore 命令會在您的電腦上安裝目前目錄範圍內的 .NET Core 本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: ceef3274ec9d337f8c51009d5a8c27e808b14035
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302668"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="7909a-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="7909a-103">dotnet tool restore</span></span>

<span data-ttu-id="7909a-104">**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="7909a-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7909a-105">名稱</span><span class="sxs-lookup"><span data-stu-id="7909a-105">Name</span></span>

<span data-ttu-id="7909a-106">`dotnet tool restore`-在您的電腦上安裝目前目錄範圍內的 .NET Core 本機工具。</span><span class="sxs-lookup"><span data-stu-id="7909a-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7909a-107">概要</span><span class="sxs-lookup"><span data-stu-id="7909a-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="7909a-108">描述</span><span class="sxs-lookup"><span data-stu-id="7909a-108">Description</span></span>

<span data-ttu-id="7909a-109">`dotnet tool restore`命令會尋找位於目前目錄範圍內的工具資訊清單檔，並安裝其中列出的工具。</span><span class="sxs-lookup"><span data-stu-id="7909a-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="7909a-110">如需資訊清單檔的相關資訊，請參閱[安裝本機工具](global-tools.md#install-a-local-tool)和叫[用本機工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="7909a-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="7909a-111">選項。</span><span class="sxs-lookup"><span data-stu-id="7909a-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="7909a-112">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="7909a-112">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="7909a-113">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="7909a-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="7909a-114">資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="7909a-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="7909a-115">防止平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="7909a-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="7909a-116">將套件來源失敗視為警告。</span><span class="sxs-lookup"><span data-stu-id="7909a-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="7909a-117">不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="7909a-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="7909a-118">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="7909a-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="7909a-119">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7909a-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7909a-120">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="7909a-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7909a-121">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="7909a-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="7909a-122">範例</span><span class="sxs-lookup"><span data-stu-id="7909a-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="7909a-123">還原目前目錄的本機工具。</span><span class="sxs-lookup"><span data-stu-id="7909a-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="7909a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7909a-124">See also</span></span>

- [<span data-ttu-id="7909a-125">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="7909a-125">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="7909a-126">教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具</span><span class="sxs-lookup"><span data-stu-id="7909a-126">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
