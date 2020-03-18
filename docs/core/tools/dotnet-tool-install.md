---
title: dotnet tool install 命令
description: dotnet 工具安裝命令在您的電腦上安裝指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 1e142773d1f981a8dc3b552d5a23d2864cdd82c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146459"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="f1ecb-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="f1ecb-103">dotnet tool install</span></span>

<span data-ttu-id="f1ecb-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="f1ecb-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f1ecb-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f1ecb-105">Name</span></span>

<span data-ttu-id="f1ecb-106">`dotnet tool install`- 在機器上安裝指定的[.NET 核心工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1ecb-107">概要</span><span class="sxs-lookup"><span data-stu-id="f1ecb-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME> <--tool-path>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="f1ecb-108">描述</span><span class="sxs-lookup"><span data-stu-id="f1ecb-108">Description</span></span>

<span data-ttu-id="f1ecb-109">該`dotnet tool install`命令為您提供了在電腦上安裝 .NET Core 工具的方法。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="f1ecb-110">要使用 該命令，請指定以下安裝選項之一：</span><span class="sxs-lookup"><span data-stu-id="f1ecb-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="f1ecb-111">要在預設位置安裝全域工具，請使用 選項`--global`。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="f1ecb-112">要在自訂位置安裝全域工具，請使用 選項`--tool-path`。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="f1ecb-113">要安裝本地工具，請省略 和`--global``--tool-path`選項。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="f1ecb-114">**本地工具可從 .NET 核心 SDK 3.0 開始。**</span><span class="sxs-lookup"><span data-stu-id="f1ecb-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="f1ecb-115">預設情況下，當您指定 或`-g``--global`選項時，全域工具將安裝在以下目錄中：</span><span class="sxs-lookup"><span data-stu-id="f1ecb-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="f1ecb-116">OS</span><span class="sxs-lookup"><span data-stu-id="f1ecb-116">OS</span></span>          | <span data-ttu-id="f1ecb-117">Path</span><span class="sxs-lookup"><span data-stu-id="f1ecb-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="f1ecb-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="f1ecb-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="f1ecb-119">Windows</span><span class="sxs-lookup"><span data-stu-id="f1ecb-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="f1ecb-120">本地工具將添加到目前的目錄下的 *.config*目錄中*的工具清單.json*檔中。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="f1ecb-121">如果清單檔尚不存在，請通過運行以下命令創建它：</span><span class="sxs-lookup"><span data-stu-id="f1ecb-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="f1ecb-122">有關詳細資訊，請參閱[安裝本地工具](global-tools.md#install-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="f1ecb-123">引數</span><span class="sxs-lookup"><span data-stu-id="f1ecb-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="f1ecb-124">包含要安裝的 .NET Core 工具的 NuGet 包的名稱/ID。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="f1ecb-125">選項。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="f1ecb-126">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="f1ecb-127">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="f1ecb-128">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="f1ecb-129">根據預設，.NET Core SDK 會嘗試選擇最適當的目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="f1ecb-130">指定安裝為使用者範圍。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="f1ecb-131">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f1ecb-132">省略兩者`--global`並`--tool-path`指定本地工具安裝。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f1ecb-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="f1ecb-134">指定要安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="f1ecb-135">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="f1ecb-136">如果 PATH 不存在，命令會嘗試建立它。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="f1ecb-137">省略兩者`--global`並`--tool-path`指定本地工具安裝。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f1ecb-138">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f1ecb-139">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="f1ecb-140">要安裝的工具版本。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-140">The version of the tool to install.</span></span> <span data-ttu-id="f1ecb-141">根據預設，會安裝最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="f1ecb-142">請使用此選項來安裝預覽版本或較舊版本的工具。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="f1ecb-143">範例</span><span class="sxs-lookup"><span data-stu-id="f1ecb-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="f1ecb-144">在預設位置將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="f1ecb-145">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝到特定的 Windows 目錄中。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="f1ecb-146">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝到特定的 Linux/macOS 目錄中。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="f1ecb-147">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)的版本 2.0.0 安裝為全域工具。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="f1ecb-148">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為目前的目錄的本地工具。</span><span class="sxs-lookup"><span data-stu-id="f1ecb-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1ecb-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1ecb-149">See also</span></span>

- [<span data-ttu-id="f1ecb-150">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="f1ecb-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f1ecb-151">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="f1ecb-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="f1ecb-152">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="f1ecb-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
