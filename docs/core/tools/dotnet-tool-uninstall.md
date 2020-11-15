---
title: dotnet tool uninstall 命令
description: Dotnet tool uninstall 命令會從您的電腦卸載指定的 .NET 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 34dffde8f9c930327c6b42d1d89bb4f511959fb2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634086"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="cd9da-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="cd9da-103">dotnet tool uninstall</span></span>

<span data-ttu-id="cd9da-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="cd9da-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cd9da-105">名稱</span><span class="sxs-lookup"><span data-stu-id="cd9da-105">Name</span></span>

<span data-ttu-id="cd9da-106">`dotnet tool uninstall` -從您的電腦卸載指定的 [.net 工具](global-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="cd9da-106">`dotnet tool uninstall` - Uninstalls the specified [.NET tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cd9da-107">概要</span><span class="sxs-lookup"><span data-stu-id="cd9da-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="cd9da-108">描述</span><span class="sxs-lookup"><span data-stu-id="cd9da-108">Description</span></span>

<span data-ttu-id="cd9da-109">此 `dotnet tool uninstall` 命令會提供一種方法，讓您從電腦卸載 .net 工具。</span><span class="sxs-lookup"><span data-stu-id="cd9da-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET tools from your machine.</span></span> <span data-ttu-id="cd9da-110">若要使用命令，您可以指定下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="cd9da-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="cd9da-111">若要卸載安裝在預設位置的通用工具，請使用 `--global` 選項。</span><span class="sxs-lookup"><span data-stu-id="cd9da-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="cd9da-112">若要卸載在自訂位置安裝的通用工具，請使用 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="cd9da-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="cd9da-113">若要卸載本機工具，請省略 `--global` 和 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="cd9da-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="cd9da-114">**從 .NET Core SDK 3.0 開始，可以使用本機工具。**</span><span class="sxs-lookup"><span data-stu-id="cd9da-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="cd9da-115">引數</span><span class="sxs-lookup"><span data-stu-id="cd9da-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="cd9da-116">包含要卸載之 .NET 工具的 NuGet 套件名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="cd9da-116">Name/ID of the NuGet package that contains the .NET tool to uninstall.</span></span> <span data-ttu-id="cd9da-117">您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。</span><span class="sxs-lookup"><span data-stu-id="cd9da-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="cd9da-118">選項</span><span class="sxs-lookup"><span data-stu-id="cd9da-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="cd9da-119">指定要從使用者範圍安裝中移除此工具。</span><span class="sxs-lookup"><span data-stu-id="cd9da-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="cd9da-120">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="cd9da-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="cd9da-121">省略兩者 `--global` 並 `--tool-path` 指定要移除的工具是本機工具。</span><span class="sxs-lookup"><span data-stu-id="cd9da-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cd9da-122">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="cd9da-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="cd9da-123">指定要卸載工具的位置。</span><span class="sxs-lookup"><span data-stu-id="cd9da-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="cd9da-124">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="cd9da-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="cd9da-125">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="cd9da-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="cd9da-126">省略兩者 `--global` 並 `--tool-path` 指定要移除的工具是本機工具。</span><span class="sxs-lookup"><span data-stu-id="cd9da-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="cd9da-127">範例</span><span class="sxs-lookup"><span data-stu-id="cd9da-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="cd9da-128">卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool。</span><span class="sxs-lookup"><span data-stu-id="cd9da-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="cd9da-129">從特定的 Windows 目錄卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool。</span><span class="sxs-lookup"><span data-stu-id="cd9da-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="cd9da-130">從特定的 Linux/macOS 目錄中卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool。</span><span class="sxs-lookup"><span data-stu-id="cd9da-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="cd9da-131">從目前目錄卸載 [>dotnetsay](https://www.nuget.org/packages/dotnetsay/) 本機工具。</span><span class="sxs-lookup"><span data-stu-id="cd9da-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd9da-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd9da-132">See also</span></span>

- [<span data-ttu-id="cd9da-133">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="cd9da-133">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="cd9da-134">教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具</span><span class="sxs-lookup"><span data-stu-id="cd9da-134">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="cd9da-135">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="cd9da-135">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
