---
title: dotnet tool uninstall 命令
description: dotnet 工具卸載命令從電腦卸載指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463317"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="00a66-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="00a66-103">dotnet tool uninstall</span></span>

<span data-ttu-id="00a66-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="00a66-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="00a66-105">名稱</span><span class="sxs-lookup"><span data-stu-id="00a66-105">Name</span></span>

<span data-ttu-id="00a66-106">`dotnet tool uninstall`- 從電腦卸載指定的[.NET 核心工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="00a66-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="00a66-107">概要</span><span class="sxs-lookup"><span data-stu-id="00a66-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="00a66-108">描述</span><span class="sxs-lookup"><span data-stu-id="00a66-108">Description</span></span>

<span data-ttu-id="00a66-109">該`dotnet tool uninstall`命令提供了一種從電腦卸載 .NET Core 工具的方法。</span><span class="sxs-lookup"><span data-stu-id="00a66-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="00a66-110">要使用 此指令,請指定以下選項之一:</span><span class="sxs-lookup"><span data-stu-id="00a66-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="00a66-111">要卸載安裝在預設位置的全域工具,請使用 選項`--global`。</span><span class="sxs-lookup"><span data-stu-id="00a66-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="00a66-112">要卸載安裝在自訂位置的全域工具,請使用 選項`--tool-path`。</span><span class="sxs-lookup"><span data-stu-id="00a66-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="00a66-113">要卸載本地工具,請省略和`--global``--tool-path`選項。</span><span class="sxs-lookup"><span data-stu-id="00a66-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="00a66-114">**本地工具可從 .NET 核心 SDK 3.0 開始。**</span><span class="sxs-lookup"><span data-stu-id="00a66-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="00a66-115">引數</span><span class="sxs-lookup"><span data-stu-id="00a66-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="00a66-116">包含要卸載的 .NET Core 工具的 NuGet 套件的名稱/ID。</span><span class="sxs-lookup"><span data-stu-id="00a66-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="00a66-117">您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。</span><span class="sxs-lookup"><span data-stu-id="00a66-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="00a66-118">選項。</span><span class="sxs-lookup"><span data-stu-id="00a66-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="00a66-119">指定要從使用者範圍安裝中移除此工具。</span><span class="sxs-lookup"><span data-stu-id="00a66-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="00a66-120">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="00a66-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="00a66-121">省略兩者`--global``--tool-path`並 指定要刪除的工具是本地工具。</span><span class="sxs-lookup"><span data-stu-id="00a66-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="00a66-122">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="00a66-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="00a66-123">指定卸載工具的位置。</span><span class="sxs-lookup"><span data-stu-id="00a66-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="00a66-124">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="00a66-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="00a66-125">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="00a66-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="00a66-126">省略兩者`--global``--tool-path`並 指定要刪除的工具是本地工具。</span><span class="sxs-lookup"><span data-stu-id="00a66-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="00a66-127">範例</span><span class="sxs-lookup"><span data-stu-id="00a66-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="00a66-128">卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)全域工具。</span><span class="sxs-lookup"><span data-stu-id="00a66-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="00a66-129">從特定的 Windows 目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)全域工具。</span><span class="sxs-lookup"><span data-stu-id="00a66-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="00a66-130">從特定的 Linux/macOS 目錄中卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)全域工具。</span><span class="sxs-lookup"><span data-stu-id="00a66-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="00a66-131">從目前目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)本地工具。</span><span class="sxs-lookup"><span data-stu-id="00a66-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="00a66-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a66-132">See also</span></span>

- [<span data-ttu-id="00a66-133">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="00a66-133">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="00a66-134">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="00a66-134">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="00a66-135">教學:使用 .NET 核心 CLI 安裝與使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="00a66-135">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
