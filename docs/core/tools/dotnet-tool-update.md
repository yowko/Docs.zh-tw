---
title: dotnet tool update 命令
description: Dotnet tool update 命令會更新您電腦上指定的 .NET 工具。
ms.date: 07/08/2020
ms.openlocfilehash: 18b153e53a6dbcb32e50ae4a7d06a1c2f53d1eb5
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634073"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="f1f1f-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="f1f1f-103">dotnet tool update</span></span>

<span data-ttu-id="f1f1f-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f1f1f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f1f1f-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f1f1f-105">Name</span></span>

<span data-ttu-id="f1f1f-106">`dotnet tool update` -在您的電腦上更新指定的 [.net 工具](global-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-106">`dotnet tool update` - Updates the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1f1f-107">概要</span><span class="sxs-lookup"><span data-stu-id="f1f1f-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="f1f1f-108">描述</span><span class="sxs-lookup"><span data-stu-id="f1f1f-108">Description</span></span>

<span data-ttu-id="f1f1f-109">此 `dotnet tool update` 命令可讓您將電腦上的 .net 工具更新為最新穩定版本的套件。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-109">The `dotnet tool update` command provides a way for you to update .NET tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="f1f1f-110">此命令會解除安裝並重新安裝工具，並有效地更新它。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="f1f1f-111">若要使用命令，您可以指定下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="f1f1f-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="f1f1f-112">若要更新在預設位置安裝的通用工具，請使用 `--global` 選項</span><span class="sxs-lookup"><span data-stu-id="f1f1f-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="f1f1f-113">若要更新在自訂位置安裝的通用工具，請使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="f1f1f-114">若要更新本機工具，請使用 `--local` 選項。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-114">To update a local tool, use the `--local` option.</span></span>

<span data-ttu-id="f1f1f-115">**從 .NET Core SDK 3.0 開始，可以使用本機工具。**</span><span class="sxs-lookup"><span data-stu-id="f1f1f-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="f1f1f-116">引數</span><span class="sxs-lookup"><span data-stu-id="f1f1f-116">Arguments</span></span>

- **`PACKAGE_ID`**

  <span data-ttu-id="f1f1f-117">包含要更新之 .NET 通用工具的 NuGet 套件名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-117">Name/ID of the NuGet package that contains the .NET global tool to update.</span></span> <span data-ttu-id="f1f1f-118">您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="f1f1f-119">選項</span><span class="sxs-lookup"><span data-stu-id="f1f1f-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="f1f1f-120">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f1f1f-121">要使用的 NuGet 組態檔 ( *nuget.config* )。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-121">The NuGet configuration ( *nuget.config* ) file to use.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="f1f1f-122">防止平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-122">Prevent restoring multiple projects in parallel.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="f1f1f-123">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-123">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="f1f1f-124">將封裝來源失敗視為警告。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-124">Treat package source failures as warnings.</span></span>

- **`--interactive`**

  <span data-ttu-id="f1f1f-125">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-125">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`--local`**

  <span data-ttu-id="f1f1f-126">更新工具和本機工具資訊清單。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-126">Update the tool and the local tool manifest.</span></span> <span data-ttu-id="f1f1f-127">無法與 `--global` 選項或 `--tool-path` 選項結合。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-127">Can't be combined with the `--global` option or the `--tool-path` option.</span></span>

- **`--no-cache`**

  <span data-ttu-id="f1f1f-128">請勿快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-128">Do not cache packages and HTTP requests.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="f1f1f-129">資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-129">Path to the manifest file.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="f1f1f-130">指定安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-130">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="f1f1f-131">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-131">PATH can be absolute or relative.</span></span> <span data-ttu-id="f1f1f-132">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-132">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="f1f1f-133">省略兩者 `--global` 並 `--tool-path` 指定要更新的工具是本機工具。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-133">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`--version <VERSION>`**

  <span data-ttu-id="f1f1f-134">要更新之工具套件的版本範圍。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-134">The version range of the tool package to update to.</span></span> <span data-ttu-id="f1f1f-135">這無法用來降級版本，您必須 `uninstall` 先使用較新的版本。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-135">This cannot be used to downgrade versions, you must `uninstall` newer versions first.</span></span>

- **`-g|--global`**

  <span data-ttu-id="f1f1f-136">指定更新適用於使用者範圍工具。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-136">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="f1f1f-137">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-137">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f1f1f-138">省略兩者 `--global` 並 `--tool-path` 指定要更新的工具是本機工具。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-138">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f1f1f-139">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-139">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f1f1f-140">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f1f1f-141">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="f1f1f-142">範例</span><span class="sxs-lookup"><span data-stu-id="f1f1f-142">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="f1f1f-143">更新 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-143">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="f1f1f-144">更新位於特定 Windows 目錄中的 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-144">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="f1f1f-145">更新位於特定 Linux/macOS 目錄中的 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-145">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="f1f1f-146">更新針對目前的目錄安裝的 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 本機工具。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-146">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  <span data-ttu-id="f1f1f-147">將 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全域工具更新為最新的修補程式版本、主要版本的 `2` ，以及的次要版本 `0` 。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-147">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the latest patch version, with a major version of `2`, and a minor version of `0`.</span></span>

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  <span data-ttu-id="f1f1f-148">將 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全域工具更新為指定範圍內的最低版本，將會 `(> 2.0.0 && < 2.1.4)` `2.1.0` 安裝版本。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-148">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the lowest version within the specified range `(> 2.0.0 && < 2.1.4)`, version `2.1.0` would be installed.</span></span> <span data-ttu-id="f1f1f-149">如需有關語義版本控制範圍的詳細資訊，請參閱 [NuGet 封裝版本範圍](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="f1f1f-149">For more information on semantic versioning ranges, see [NuGet packaging version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1f1f-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1f1f-150">See also</span></span>

- [<span data-ttu-id="f1f1f-151">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="f1f1f-151">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="f1f1f-152">語意化版本控制系統</span><span class="sxs-lookup"><span data-stu-id="f1f1f-152">Semantic versioning</span></span>](https://semver.org)
- [<span data-ttu-id="f1f1f-153">教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具</span><span class="sxs-lookup"><span data-stu-id="f1f1f-153">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="f1f1f-154">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="f1f1f-154">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
