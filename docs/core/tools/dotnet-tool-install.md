---
title: dotnet tool install 命令
description: Dotnet tool install 命令會在您的電腦上安裝指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 837d12bc807ad95ccdbd9c0e087c7d45418c6e74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626030"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="bbdd9-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="bbdd9-103">dotnet tool install</span></span>

<span data-ttu-id="bbdd9-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="bbdd9-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bbdd9-105">名稱</span><span class="sxs-lookup"><span data-stu-id="bbdd9-105">Name</span></span>

<span data-ttu-id="bbdd9-106">`dotnet tool install`-在您的電腦上安裝指定的[.Net Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bbdd9-107">概要</span><span class="sxs-lookup"><span data-stu-id="bbdd9-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="bbdd9-108">描述</span><span class="sxs-lookup"><span data-stu-id="bbdd9-108">Description</span></span>

<span data-ttu-id="bbdd9-109">`dotnet tool install` 命令提供一種方式，讓您在電腦上安裝 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="bbdd9-110">若要使用命令，您可以指定下列其中一個安裝選項：</span><span class="sxs-lookup"><span data-stu-id="bbdd9-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="bbdd9-111">若要在預設位置安裝全域工具，請使用 [`--global`] 選項。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="bbdd9-112">若要在自訂位置安裝全域工具，請使用 [`--tool-path`] 選項。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="bbdd9-113">若要安裝本機工具，請省略 `--global` 並 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="bbdd9-114">**從 .NET Core SDK 3.0 開始提供本機工具。**</span><span class="sxs-lookup"><span data-stu-id="bbdd9-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="bbdd9-115">當您指定 [`-g`] 或 [`--global`] 選項時，通用工具預設會安裝在下列目錄中：</span><span class="sxs-lookup"><span data-stu-id="bbdd9-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="bbdd9-116">OS</span><span class="sxs-lookup"><span data-stu-id="bbdd9-116">OS</span></span>          | <span data-ttu-id="bbdd9-117">Path</span><span class="sxs-lookup"><span data-stu-id="bbdd9-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="bbdd9-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="bbdd9-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="bbdd9-119">Windows</span><span class="sxs-lookup"><span data-stu-id="bbdd9-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="bbdd9-120">本機工具會新增至目前目錄下 *.config*目錄中的*工具資訊清單. json*檔案。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="bbdd9-121">如果資訊清單檔案尚不存在，請執行下列命令來建立檔案：</span><span class="sxs-lookup"><span data-stu-id="bbdd9-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="bbdd9-122">如需詳細資訊，請參閱[安裝本機工具](global-tools.md#install-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="bbdd9-123">引數</span><span class="sxs-lookup"><span data-stu-id="bbdd9-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="bbdd9-124">包含要安裝之 .NET Core 工具的 NuGet 套件的名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="bbdd9-125">選項。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="bbdd9-126">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="bbdd9-127">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="bbdd9-128">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="bbdd9-129">根據預設，.NET Core SDK 會嘗試選擇最適當的目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="bbdd9-130">指定安裝為使用者範圍。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="bbdd9-131">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="bbdd9-132">省略 `--global` 和 `--tool-path` 指定本機工具安裝。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="bbdd9-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="bbdd9-134">指定要安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="bbdd9-135">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="bbdd9-136">如果 PATH 不存在，命令會嘗試建立它。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="bbdd9-137">省略 `--global` 和 `--tool-path` 指定本機工具安裝。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bbdd9-138">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bbdd9-139">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="bbdd9-140">要安裝的工具版本。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-140">The version of the tool to install.</span></span> <span data-ttu-id="bbdd9-141">根據預設，會安裝最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="bbdd9-142">請使用此選項來安裝預覽版本或較舊版本的工具。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="bbdd9-143">範例</span><span class="sxs-lookup"><span data-stu-id="bbdd9-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="bbdd9-144">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為預設位置中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="bbdd9-145">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為特定 Windows 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="bbdd9-146">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為特定 Linux/macOS 目錄中的通用工具。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="bbdd9-147">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)的版本2.0.0 安裝為通用工具。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="bbdd9-148">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為目前目錄的本機工具。</span><span class="sxs-lookup"><span data-stu-id="bbdd9-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbdd9-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbdd9-149">See also</span></span>

- [<span data-ttu-id="bbdd9-150">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="bbdd9-150">.NET Core tools</span></span>](global-tools.md)
