---
title: dotnet tool install 命令
description: Dotnet tool install 命令會在您的電腦上安裝指定的 .NET 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 1dd870a8f91e557a2f59919682616aa8817fc070
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634320"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="c8969-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="c8969-103">dotnet tool install</span></span>

<span data-ttu-id="c8969-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="c8969-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c8969-105">名稱</span><span class="sxs-lookup"><span data-stu-id="c8969-105">Name</span></span>

<span data-ttu-id="c8969-106">`dotnet tool install` -在您的電腦上安裝指定的 [.net 工具](global-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="c8969-106">`dotnet tool install` - Installs the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8969-107">概要</span><span class="sxs-lookup"><span data-stu-id="c8969-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="c8969-108">描述</span><span class="sxs-lookup"><span data-stu-id="c8969-108">Description</span></span>

<span data-ttu-id="c8969-109">`dotnet tool install`命令提供可讓您在電腦上安裝 .net 工具的方法。</span><span class="sxs-lookup"><span data-stu-id="c8969-109">The `dotnet tool install` command provides a way for you to install .NET tools on your machine.</span></span> <span data-ttu-id="c8969-110">若要使用命令，您可以指定下列其中一個安裝選項：</span><span class="sxs-lookup"><span data-stu-id="c8969-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="c8969-111">若要在預設位置安裝全域工具，請使用 `--global` 選項。</span><span class="sxs-lookup"><span data-stu-id="c8969-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="c8969-112">若要在自訂位置安裝通用工具，請使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="c8969-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="c8969-113">若要安裝本機工具，請省略 `--global` 和 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="c8969-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="c8969-114">**從 .NET Core SDK 3.0 開始，可以使用本機工具。**</span><span class="sxs-lookup"><span data-stu-id="c8969-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="c8969-115">當您指定或選項時，通用工具預設會安裝在下列目錄中 `-g` `--global` ：</span><span class="sxs-lookup"><span data-stu-id="c8969-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="c8969-116">OS</span><span class="sxs-lookup"><span data-stu-id="c8969-116">OS</span></span>          | <span data-ttu-id="c8969-117">路徑</span><span class="sxs-lookup"><span data-stu-id="c8969-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="c8969-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="c8969-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="c8969-119">Windows</span><span class="sxs-lookup"><span data-stu-id="c8969-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="c8969-120">本機工具會新增至目前目錄下 .config 目錄中的檔案 *dotnet-tools.js* *。*</span><span class="sxs-lookup"><span data-stu-id="c8969-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="c8969-121">如果資訊清單檔案尚未存在，請執行下列命令來建立它：</span><span class="sxs-lookup"><span data-stu-id="c8969-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="c8969-122">如需詳細資訊，請參閱 [安裝本機工具](global-tools.md#install-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="c8969-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="c8969-123">引數</span><span class="sxs-lookup"><span data-stu-id="c8969-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="c8969-124">包含要安裝之 .NET 工具的 NuGet 套件名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="c8969-124">Name/ID of the NuGet package that contains the .NET tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="c8969-125">選項</span><span class="sxs-lookup"><span data-stu-id="c8969-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="c8969-126">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="c8969-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="c8969-127">要使用的 NuGet 組態檔 ( *nuget.config* )。</span><span class="sxs-lookup"><span data-stu-id="c8969-127">The NuGet configuration ( *nuget.config* ) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="c8969-128">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c8969-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="c8969-129">根據預設，.NET SDK 會嘗試選擇最適當的目標架構。</span><span class="sxs-lookup"><span data-stu-id="c8969-129">By default, the .NET SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="c8969-130">指定安裝為使用者範圍。</span><span class="sxs-lookup"><span data-stu-id="c8969-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="c8969-131">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="c8969-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c8969-132">省略兩者 `--global` 並 `--tool-path` 指定本機工具安裝。</span><span class="sxs-lookup"><span data-stu-id="c8969-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c8969-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c8969-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="c8969-134">指定要安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="c8969-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="c8969-135">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c8969-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="c8969-136">如果 PATH 不存在，命令會嘗試建立它。</span><span class="sxs-lookup"><span data-stu-id="c8969-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="c8969-137">省略兩者 `--global` 並 `--tool-path` 指定本機工具安裝。</span><span class="sxs-lookup"><span data-stu-id="c8969-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c8969-138">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="c8969-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c8969-139">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="c8969-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="c8969-140">要安裝的工具版本。</span><span class="sxs-lookup"><span data-stu-id="c8969-140">The version of the tool to install.</span></span> <span data-ttu-id="c8969-141">根據預設，會安裝最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="c8969-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="c8969-142">請使用此選項來安裝預覽版本或較舊版本的工具。</span><span class="sxs-lookup"><span data-stu-id="c8969-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="c8969-143">範例</span><span class="sxs-lookup"><span data-stu-id="c8969-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="c8969-144">將 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 安裝為預設位置中的全域工具。</span><span class="sxs-lookup"><span data-stu-id="c8969-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="c8969-145">將 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 安裝為特定 Windows 目錄中的全域工具。</span><span class="sxs-lookup"><span data-stu-id="c8969-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="c8969-146">將 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 安裝為特定 Linux/macOS 目錄中的全域工具。</span><span class="sxs-lookup"><span data-stu-id="c8969-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="c8969-147">將 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 的版本2.0.0 安裝為全域工具。</span><span class="sxs-lookup"><span data-stu-id="c8969-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="c8969-148">將 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 安裝為目前目錄的本機工具。</span><span class="sxs-lookup"><span data-stu-id="c8969-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8969-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8969-149">See also</span></span>

- [<span data-ttu-id="c8969-150">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="c8969-150">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="c8969-151">教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具</span><span class="sxs-lookup"><span data-stu-id="c8969-151">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="c8969-152">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="c8969-152">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
