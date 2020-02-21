---
title: dotnet 工具還原命令
description: Dotnet 工具 restore 命令會在您的電腦上安裝目前目錄範圍內的 .NET Core 本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543905"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="81934-103">dotnet 工具還原</span><span class="sxs-lookup"><span data-stu-id="81934-103">dotnet tool restore</span></span>

<span data-ttu-id="81934-104">**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="81934-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="81934-105">名稱</span><span class="sxs-lookup"><span data-stu-id="81934-105">Name</span></span>

<span data-ttu-id="81934-106">`dotnet tool restore`-在您的電腦上安裝目前目錄範圍內的 .NET Core 本機工具。</span><span class="sxs-lookup"><span data-stu-id="81934-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="81934-107">概要</span><span class="sxs-lookup"><span data-stu-id="81934-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="81934-108">描述</span><span class="sxs-lookup"><span data-stu-id="81934-108">Description</span></span>

<span data-ttu-id="81934-109">`dotnet tool restore` 命令會尋找位於目前目錄範圍內的工具資訊清單檔，並安裝其中列出的工具。</span><span class="sxs-lookup"><span data-stu-id="81934-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="81934-110">如需資訊清單檔的相關資訊，請參閱[安裝本機工具](global-tools.md#install-a-local-tool)和叫[用本機工具](global-tools.md#invoke-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="81934-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="81934-111">引數</span><span class="sxs-lookup"><span data-stu-id="81934-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="81934-112">包含要安裝之 .NET Core 工具的 NuGet 套件的名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="81934-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="81934-113">選項。</span><span class="sxs-lookup"><span data-stu-id="81934-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="81934-114">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="81934-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="81934-115">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="81934-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="81934-116">資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="81934-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="81934-117">防止平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="81934-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="81934-118">將套件來源失敗視為警告。</span><span class="sxs-lookup"><span data-stu-id="81934-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="81934-119">不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="81934-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="81934-120">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="81934-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="81934-121">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="81934-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="81934-122">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="81934-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="81934-123">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="81934-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="81934-124">範例</span><span class="sxs-lookup"><span data-stu-id="81934-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="81934-125">還原目前目錄的本機工具。</span><span class="sxs-lookup"><span data-stu-id="81934-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="81934-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81934-126">See also</span></span>

- [<span data-ttu-id="81934-127">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="81934-127">.NET Core tools</span></span>](global-tools.md)
