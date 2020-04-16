---
title: dotnet tool install 命令
description: dotnet 工具安裝命令在您的電腦上安裝指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 723d25caa6009288dbb55d55f173b04d7b983450
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463369"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="6ad3e-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="6ad3e-103">dotnet tool install</span></span>

<span data-ttu-id="6ad3e-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="6ad3e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6ad3e-105">名稱</span><span class="sxs-lookup"><span data-stu-id="6ad3e-105">Name</span></span>

<span data-ttu-id="6ad3e-106">`dotnet tool install`- 在機器上安裝指定的[.NET 核心工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6ad3e-107">概要</span><span class="sxs-lookup"><span data-stu-id="6ad3e-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="6ad3e-108">描述</span><span class="sxs-lookup"><span data-stu-id="6ad3e-108">Description</span></span>

<span data-ttu-id="6ad3e-109">這個`dotnet tool install`指令為您提供了在電腦上安裝 .NET Core 工具的方法。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="6ad3e-110">要使用 此指令,請指定以下安裝選項之一:</span><span class="sxs-lookup"><span data-stu-id="6ad3e-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="6ad3e-111">在預設位置安裝全域工具,請使用選項`--global`。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="6ad3e-112">您可以在自訂位置安裝全域工具,請使用選項`--tool-path`。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="6ad3e-113">要安裝本地工具,請省略和`--global``--tool-path`選項。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="6ad3e-114">**本地工具可從 .NET 核心 SDK 3.0 開始。**</span><span class="sxs-lookup"><span data-stu-id="6ad3e-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="6ad3e-115">預設情況下,當您指定`-g``--global`或選項時,全域工具將安裝在以下目錄中:</span><span class="sxs-lookup"><span data-stu-id="6ad3e-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="6ad3e-116">OS</span><span class="sxs-lookup"><span data-stu-id="6ad3e-116">OS</span></span>          | <span data-ttu-id="6ad3e-117">Path</span><span class="sxs-lookup"><span data-stu-id="6ad3e-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="6ad3e-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="6ad3e-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="6ad3e-119">Windows</span><span class="sxs-lookup"><span data-stu-id="6ad3e-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="6ad3e-120">本地工具將添加到當前目錄下的 *.config*目錄中*的工具清單.json*檔中。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="6ad3e-121">如果清單檔案不存在,請執行以下指令建立它:</span><span class="sxs-lookup"><span data-stu-id="6ad3e-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="6ad3e-122">有關詳細資訊,請參閱[安裝本地端工具](global-tools.md#install-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="6ad3e-123">引數</span><span class="sxs-lookup"><span data-stu-id="6ad3e-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="6ad3e-124">包含要安裝的 .NET Core 工具的 NuGet 套件的名稱/ ID。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="6ad3e-125">選項。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="6ad3e-126">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="6ad3e-127">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="6ad3e-128">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="6ad3e-129">根據預設，.NET Core SDK 會嘗試選擇最適當的目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="6ad3e-130">指定安裝為使用者範圍。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="6ad3e-131">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="6ad3e-132">省略兩者`--global``--tool-path`並指定本地工具安裝。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6ad3e-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="6ad3e-134">指定要安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="6ad3e-135">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="6ad3e-136">如果 PATH 不存在，命令會嘗試建立它。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="6ad3e-137">省略兩者`--global``--tool-path`並指定本地工具安裝。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6ad3e-138">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6ad3e-139">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="6ad3e-140">要安裝的工具版本。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-140">The version of the tool to install.</span></span> <span data-ttu-id="6ad3e-141">根據預設，會安裝最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="6ad3e-142">請使用此選項來安裝預覽版本或較舊版本的工具。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="6ad3e-143">範例</span><span class="sxs-lookup"><span data-stu-id="6ad3e-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="6ad3e-144">在預設位置將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="6ad3e-145">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝到特定的 Windows 目錄中。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="6ad3e-146">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)作為全域工具安裝到特定的 Linux/macOS 目錄中。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="6ad3e-147">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)的版本 2.0.0 安裝為全域工具。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="6ad3e-148">將[dotnetsay](https://www.nuget.org/packages/dotnetsay/)安裝為目前目錄的本地工具。</span><span class="sxs-lookup"><span data-stu-id="6ad3e-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ad3e-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ad3e-149">See also</span></span>

- [<span data-ttu-id="6ad3e-150">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="6ad3e-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="6ad3e-151">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="6ad3e-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="6ad3e-152">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="6ad3e-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
