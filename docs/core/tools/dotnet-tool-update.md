---
title: dotnet tool update 命令
description: dotnet tool update 命令會更新您電腦上指定的 .NET Core 通用工具。
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117534"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="47c01-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="47c01-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="47c01-104">名稱</span><span class="sxs-lookup"><span data-stu-id="47c01-104">Name</span></span>

<span data-ttu-id="47c01-105">`dotnet tool update` - 在您的電腦上更新指定的 [.NET Core 通用工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="47c01-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="47c01-106">概要</span><span class="sxs-lookup"><span data-stu-id="47c01-106">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="47c01-107">描述</span><span class="sxs-lookup"><span data-stu-id="47c01-107">Description</span></span>

<span data-ttu-id="47c01-108">`dotnet tool update` 命令可讓您將電腦上的 .NET Core 通用工具更新為套件的最新穩定版本。</span><span class="sxs-lookup"><span data-stu-id="47c01-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="47c01-109">此命令會解除安裝並重新安裝工具，並有效地更新它。</span><span class="sxs-lookup"><span data-stu-id="47c01-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="47c01-110">若要使用此命令，您必須使用 `--global` 選項指定您要更新使用者範圍安裝中的工具，或使用 `--tool-path` 選項指定安裝工具的路徑。</span><span class="sxs-lookup"><span data-stu-id="47c01-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="47c01-111">引數</span><span class="sxs-lookup"><span data-stu-id="47c01-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="47c01-112">包含要更新之 .NET Core 通用工具的 NuGet 套件的名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="47c01-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="47c01-113">您可以使用 [dotnet tool list](dotnet-tool-list.md) 命令來找到此套件名稱。</span><span class="sxs-lookup"><span data-stu-id="47c01-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="47c01-114">選項</span><span class="sxs-lookup"><span data-stu-id="47c01-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="47c01-115">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="47c01-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="47c01-116">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="47c01-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="47c01-117">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="47c01-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="47c01-118">指定更新適用於使用者範圍工具。</span><span class="sxs-lookup"><span data-stu-id="47c01-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="47c01-119">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="47c01-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="47c01-120">如果未指定此選項，您必須指定 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="47c01-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="47c01-121">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="47c01-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="47c01-122">指定安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="47c01-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="47c01-123">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="47c01-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="47c01-124">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="47c01-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="47c01-125">如果未指定此選項，您必須指定 `--global` 選項。</span><span class="sxs-lookup"><span data-stu-id="47c01-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="47c01-126">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="47c01-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="47c01-127">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="47c01-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="47c01-128">範例</span><span class="sxs-lookup"><span data-stu-id="47c01-128">Examples</span></span>

<span data-ttu-id="47c01-129">更新 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="47c01-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="47c01-130">從特定的 Windows 資料夾中更新 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="47c01-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="47c01-131">從特定的 Windows 資料夾中更新 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="47c01-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="47c01-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c01-132">See also</span></span>

- [<span data-ttu-id="47c01-133">.NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="47c01-133">.NET Core Global Tools</span></span>](global-tools.md)
