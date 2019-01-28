---
title: dotnet tool uninstall 命令
description: dotnet tool uninstall 命令會從您的電腦中解除安裝指定的 .NET Core 通用工具。
ms.date: 05/29/2018
ms.openlocfilehash: 4d53d305131e3399ab5d9c19f9319f3ba3544c19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680919"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="9f131-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="9f131-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="9f131-104">名稱</span><span class="sxs-lookup"><span data-stu-id="9f131-104">Name</span></span>

<span data-ttu-id="9f131-105">`dotnet tool uninstall` - 從您的電腦中解除安裝指定的 [.NET Core 通用工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="9f131-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9f131-106">概要</span><span class="sxs-lookup"><span data-stu-id="9f131-106">Synopsis</span></span>

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="9f131-107">說明</span><span class="sxs-lookup"><span data-stu-id="9f131-107">Description</span></span>

<span data-ttu-id="9f131-108">`dotnet tool uninstall` 命令可讓您從電腦中解除安裝 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="9f131-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="9f131-109">若要使用此命令，您必須使用 `--global` 選項指定您要移除使用者範圍工具，或使用 `--tool-path` 選項指定安裝工具的路徑。</span><span class="sxs-lookup"><span data-stu-id="9f131-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="9f131-110">引數</span><span class="sxs-lookup"><span data-stu-id="9f131-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="9f131-111">包含要解除安裝的 .NET Core 通用工具之 NuGet 套件的名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="9f131-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="9f131-112">您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。</span><span class="sxs-lookup"><span data-stu-id="9f131-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="9f131-113">選項</span><span class="sxs-lookup"><span data-stu-id="9f131-113">Options</span></span>

`-g|--global`

<span data-ttu-id="9f131-114">指定要從使用者範圍安裝中移除此工具。</span><span class="sxs-lookup"><span data-stu-id="9f131-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="9f131-115">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="9f131-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="9f131-116">如果未指定此選項，您必須指定 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="9f131-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="9f131-117">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="9f131-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="9f131-118">指定要解除安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="9f131-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="9f131-119">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="9f131-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="9f131-120">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="9f131-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="9f131-121">如果未指定此選項，您必須指定 `--global` 選項。</span><span class="sxs-lookup"><span data-stu-id="9f131-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="9f131-122">範例</span><span class="sxs-lookup"><span data-stu-id="9f131-122">Examples</span></span>

<span data-ttu-id="9f131-123">解除安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="9f131-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="9f131-124">從特定的 Windows 資料夾中解除安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="9f131-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="9f131-125">從特定的 Linux/macOS 資料夾中解除安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="9f131-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="9f131-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f131-126">See also</span></span>

- [<span data-ttu-id="9f131-127">.NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="9f131-127">.NET Core Global Tools</span></span>](global-tools.md)
