---
title: dotnet tool install 命令 - .NET Core CLI
description: dotnet tool install 命令會在您的電腦上安裝指定的 .NET Core 通用工具。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: aad5a3e815936749d90f40975a8b13d34e89386c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512191"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="84f01-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="84f01-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="84f01-104">名稱</span><span class="sxs-lookup"><span data-stu-id="84f01-104">Name</span></span>

<span data-ttu-id="84f01-105">`dotnet tool install` - 在您的電腦上安裝指定的 [.NET Core 通用工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="84f01-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="84f01-106">概要</span><span class="sxs-lookup"><span data-stu-id="84f01-106">Synopsis</span></span>

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="84f01-107">描述</span><span class="sxs-lookup"><span data-stu-id="84f01-107">Description</span></span>

<span data-ttu-id="84f01-108">`dotnet tool install` 命令可讓您在電腦上安裝 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="84f01-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="84f01-109">若要使用此命令，您必須使用 `--global` 選項指定您要使用者範圍安裝，或使用 `--tool-path` 選項指定安裝工具的路徑。</span><span class="sxs-lookup"><span data-stu-id="84f01-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="84f01-110">當您指定 `-g` (或 `--global`) 選項時，通用工具預設會安裝在下列目錄中：</span><span class="sxs-lookup"><span data-stu-id="84f01-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="84f01-111">作業系統</span><span class="sxs-lookup"><span data-stu-id="84f01-111">OS</span></span>          | <span data-ttu-id="84f01-112">路徑</span><span class="sxs-lookup"><span data-stu-id="84f01-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="84f01-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="84f01-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="84f01-114">Windows</span><span class="sxs-lookup"><span data-stu-id="84f01-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="84f01-115">引數</span><span class="sxs-lookup"><span data-stu-id="84f01-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="84f01-116">包含要安裝的 .NET Core 通用工具之 NuGet 套件的名稱/識別碼。</span><span class="sxs-lookup"><span data-stu-id="84f01-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="84f01-117">選項</span><span class="sxs-lookup"><span data-stu-id="84f01-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="84f01-118">新增其他 NuGet 套件來源以在安裝期間使用。</span><span class="sxs-lookup"><span data-stu-id="84f01-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="84f01-119">要使用的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="84f01-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="84f01-120">指定要更新其工具的[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="84f01-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="84f01-121">根據預設，.NET Core SDK 會嘗試選擇最適當的目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="84f01-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="84f01-122">指定安裝為使用者範圍。</span><span class="sxs-lookup"><span data-stu-id="84f01-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="84f01-123">無法與 `--tool-path` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="84f01-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="84f01-124">如果未指定此選項，您必須指定 `--tool-path` 選項。</span><span class="sxs-lookup"><span data-stu-id="84f01-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="84f01-125">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="84f01-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="84f01-126">指定要安裝通用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="84f01-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="84f01-127">PATH 可為絕對路徑或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="84f01-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="84f01-128">如果 PATH 不存在，命令會嘗試建立它。</span><span class="sxs-lookup"><span data-stu-id="84f01-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="84f01-129">無法與 `--global` 選項合併使用。</span><span class="sxs-lookup"><span data-stu-id="84f01-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="84f01-130">如果未指定此選項，您必須指定 `--global` 選項。</span><span class="sxs-lookup"><span data-stu-id="84f01-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="84f01-131">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="84f01-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="84f01-132">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="84f01-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="84f01-133">要安裝的工具版本。</span><span class="sxs-lookup"><span data-stu-id="84f01-133">The version of the tool to install.</span></span> <span data-ttu-id="84f01-134">根據預設，會安裝最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="84f01-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="84f01-135">請使用此選項來安裝預覽版本或較舊版本的工具。</span><span class="sxs-lookup"><span data-stu-id="84f01-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="84f01-136">範例</span><span class="sxs-lookup"><span data-stu-id="84f01-136">Examples</span></span>

<span data-ttu-id="84f01-137">在預設位置中安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="84f01-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="84f01-138">在特定的 Windows 資料夾中安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="84f01-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="84f01-139">在特定的 Linux/macOS 資料夾中安裝 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="84f01-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="84f01-140">安裝 2.0.0 版的 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 通用工具：</span><span class="sxs-lookup"><span data-stu-id="84f01-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="84f01-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84f01-141">See also</span></span>

* [<span data-ttu-id="84f01-142">.NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="84f01-142">.NET Core Global Tools</span></span>](global-tools.md)