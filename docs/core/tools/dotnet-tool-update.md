---
title: dotnet tool update 命令
description: dotnet 工具更新指令更新您電腦上的指定的 .NET 核心工具。
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463292"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="f2f21-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="f2f21-103">dotnet tool update</span></span>

<span data-ttu-id="f2f21-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="f2f21-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f2f21-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f2f21-105">Name</span></span>

<span data-ttu-id="f2f21-106">`dotnet tool update`- 更新機器上指定的[.NET 核心工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f2f21-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f2f21-107">概要</span><span class="sxs-lookup"><span data-stu-id="f2f21-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="f2f21-108">描述</span><span class="sxs-lookup"><span data-stu-id="f2f21-108">Description</span></span>

<span data-ttu-id="f2f21-109">該`dotnet tool update`指令提供了一種將電腦上的 .NET Core 工具更新到套件的最新穩定版本的方法。</span><span class="sxs-lookup"><span data-stu-id="f2f21-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="f2f21-110">此命令會解除安裝並重新安裝工具，並有效地更新它。</span><span class="sxs-lookup"><span data-stu-id="f2f21-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="f2f21-111">要使用 此指令,請指定以下選項之一:</span><span class="sxs-lookup"><span data-stu-id="f2f21-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="f2f21-112">要更新安裝在預設位置的全域工具,請使用 選項`--global`</span><span class="sxs-lookup"><span data-stu-id="f2f21-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="f2f21-113">要更新安裝在自訂位置的全域工具,請使用 選項`--tool-path`。</span><span class="sxs-lookup"><span data-stu-id="f2f21-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="f2f21-114">要更新本地工具,請省略和`--global``--tool-path`選項。</span><span class="sxs-lookup"><span data-stu-id="f2f21-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="f2f21-115">**本地工具可從 .NET 核心 SDK 3.0 開始。**</span><span class="sxs-lookup"><span data-stu-id="f2f21-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="f2f21-116">引數</span><span class="sxs-lookup"><span data-stu-id="f2f21-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="f2f21-117">包含要更新的 .NET Core 全域工具的 NuGet 套件的名稱/ ID。</span><span class="sxs-lookup"><span data-stu-id="f2f21-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="f2f21-118">您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。</span><span class="sxs-lookup"><span data-stu-id="f2f21-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="f2f21-119">選項。</span><span class="sxs-lookup"><span data-stu-id="f2f21-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="f2f21-120">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="f2f21-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f2f21-121">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="f2f21-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="f2f21-122">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f2f21-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="f2f21-123">指定更新適用於使用者範圍工具。</span><span class="sxs-lookup"><span data-stu-id="f2f21-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="f2f21-124">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="f2f21-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f2f21-125">省略兩者`--global``--tool-path`並 指定要更新的工具是本地工具。</span><span class="sxs-lookup"><span data-stu-id="f2f21-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f2f21-126">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f2f21-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="f2f21-127">指定安裝全域工具的位置。</span><span class="sxs-lookup"><span data-stu-id="f2f21-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="f2f21-128">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="f2f21-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="f2f21-129">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="f2f21-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="f2f21-130">省略兩者`--global``--tool-path`並 指定要更新的工具是本地工具。</span><span class="sxs-lookup"><span data-stu-id="f2f21-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f2f21-131">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="f2f21-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f2f21-132">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f2f21-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="f2f21-133">範例</span><span class="sxs-lookup"><span data-stu-id="f2f21-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="f2f21-134">更新[點網路賽](https://www.nuget.org/packages/dotnetsay/)全域工具。</span><span class="sxs-lookup"><span data-stu-id="f2f21-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="f2f21-135">更新位於特定 Windows 目錄中的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)全域工具。</span><span class="sxs-lookup"><span data-stu-id="f2f21-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="f2f21-136">更新位於特定 Linux/macOS 目錄中的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)全域工具。</span><span class="sxs-lookup"><span data-stu-id="f2f21-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="f2f21-137">更新為目前目錄安裝的[dotnetsay](https://www.nuget.org/packages/dotnetsay/)本地工具。</span><span class="sxs-lookup"><span data-stu-id="f2f21-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2f21-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2f21-138">See also</span></span>

- [<span data-ttu-id="f2f21-139">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="f2f21-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f2f21-140">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="f2f21-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="f2f21-141">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="f2f21-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
