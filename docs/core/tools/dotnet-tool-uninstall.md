---
title: dotnet tool uninstall 命令
description: Dotnet tool uninstall 命令會從您的電腦卸載指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 7a15c169c73cf5a743e0fa6f47645d6bccedbde3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157041"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="11f27-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="11f27-103">dotnet tool uninstall</span></span>

<span data-ttu-id="11f27-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="11f27-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="11f27-105">名稱</span><span class="sxs-lookup"><span data-stu-id="11f27-105">Name</span></span>

<span data-ttu-id="11f27-106">`dotnet tool uninstall`-從您的電腦卸載指定的[.Net Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="11f27-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="11f27-107">概要</span><span class="sxs-lookup"><span data-stu-id="11f27-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="11f27-108">描述</span><span class="sxs-lookup"><span data-stu-id="11f27-108">Description</span></span>

<span data-ttu-id="11f27-109">`dotnet tool uninstall` 命令提供一種方式，讓您從電腦卸載 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="11f27-110">若要使用命令，您可以指定下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="11f27-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="11f27-111">若要卸載安裝在預設位置的全域工具，請使用 [`--global`] 選項。</span><span class="sxs-lookup"><span data-stu-id="11f27-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="11f27-112">若要卸載安裝在自訂位置的全域工具，請使用 [`--tool-path`] 選項。</span><span class="sxs-lookup"><span data-stu-id="11f27-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="11f27-113">若要卸載本機工具，請省略 `--global` 並 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="11f27-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="11f27-114">**從 .NET Core SDK 3.0 開始提供本機工具。**</span><span class="sxs-lookup"><span data-stu-id="11f27-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="11f27-115">引數</span><span class="sxs-lookup"><span data-stu-id="11f27-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="11f27-116">包含要卸載之 .NET Core 工具之 NuGet 套件的名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="11f27-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="11f27-117">您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。</span><span class="sxs-lookup"><span data-stu-id="11f27-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="11f27-118">選項。</span><span class="sxs-lookup"><span data-stu-id="11f27-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="11f27-119">指定要從使用者範圍安裝中移除此工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="11f27-120">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="11f27-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="11f27-121">省略 `--global` 和 `--tool-path` 指定要移除的工具是本機工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="11f27-122">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="11f27-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="11f27-123">指定要卸載工具的位置。</span><span class="sxs-lookup"><span data-stu-id="11f27-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="11f27-124">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="11f27-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="11f27-125">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="11f27-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="11f27-126">省略 `--global` 和 `--tool-path` 指定要移除的工具是本機工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="11f27-127">範例</span><span class="sxs-lookup"><span data-stu-id="11f27-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="11f27-128">卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="11f27-129">從特定的 Windows 目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="11f27-130">從特定的 Linux/macOS 目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)通用工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="11f27-131">從目前的目錄卸載[dotnetsay](https://www.nuget.org/packages/dotnetsay/)本機工具。</span><span class="sxs-lookup"><span data-stu-id="11f27-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="11f27-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11f27-132">See also</span></span>

- [<span data-ttu-id="11f27-133">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="11f27-133">.NET Core tools</span></span>](global-tools.md)
