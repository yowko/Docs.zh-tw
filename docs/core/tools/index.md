---
title: .NET Core CLI
titleSuffix: ''
description: .NET 核心 CLI 及其功能的概述。
ms.date: 02/13/2020
ms.openlocfilehash: 45a40063f70a621e807abf5e01ceecb125aecd7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399116"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="0137b-103">.NET 核心 CLI 概述</span><span class="sxs-lookup"><span data-stu-id="0137b-103">.NET Core CLI overview</span></span>

<span data-ttu-id="0137b-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="0137b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="0137b-105">.NET Core 命令列介面 （CLI） 是一個跨平臺工具鏈，用於開發、構建、運行和發佈 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0137b-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="0137b-106">.NET 核心 CLI 包含在[.NET 核心 SDK](../sdk.md)中。</span><span class="sxs-lookup"><span data-stu-id="0137b-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="0137b-107">要瞭解如何安裝 .NET 核心 SDK，請參閱[安裝 .NET 核心 SDK](../install/sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="0137b-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="0137b-108">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="0137b-108">CLI commands</span></span>

<span data-ttu-id="0137b-109">預設會安裝下列命令：</span><span class="sxs-lookup"><span data-stu-id="0137b-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="0137b-110">基本命令</span><span class="sxs-lookup"><span data-stu-id="0137b-110">Basic commands</span></span>

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="0137b-111">專案修改命令</span><span class="sxs-lookup"><span data-stu-id="0137b-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="0137b-112">進階命令</span><span class="sxs-lookup"><span data-stu-id="0137b-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="0137b-113">工具管理命令</span><span class="sxs-lookup"><span data-stu-id="0137b-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="0137b-114">[`tool restore`](global-tools.md#install-a-local-tool)自 .NET 核心 SDK 3.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="0137b-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="0137b-115">[`tool run`](global-tools.md#invoke-a-local-tool)自 .NET 核心 SDK 3.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="0137b-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="0137b-116">工具是從 NuGet 包安裝並從命令提示符調用的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0137b-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="0137b-117">您可以自己編寫工具或安裝由協力廠商編寫的工具。</span><span class="sxs-lookup"><span data-stu-id="0137b-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="0137b-118">工具也稱為全域工具、刀具路徑工具和本地工具。</span><span class="sxs-lookup"><span data-stu-id="0137b-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="0137b-119">有關詳細資訊，請參閱[.NET 核心工具概述](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0137b-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="0137b-120">命令結構</span><span class="sxs-lookup"><span data-stu-id="0137b-120">Command structure</span></span>

<span data-ttu-id="0137b-121">CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令](#command)，以及可能的命令[引數](#arguments)及[選項](#options)。</span><span class="sxs-lookup"><span data-stu-id="0137b-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="0137b-122">您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：</span><span class="sxs-lookup"><span data-stu-id="0137b-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="0137b-123">驅動程式</span><span class="sxs-lookup"><span data-stu-id="0137b-123">Driver</span></span>

<span data-ttu-id="0137b-124">驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。</span><span class="sxs-lookup"><span data-stu-id="0137b-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="0137b-125">若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。</span><span class="sxs-lookup"><span data-stu-id="0137b-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="0137b-126">從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。</span><span class="sxs-lookup"><span data-stu-id="0137b-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="0137b-127">若要使用特定版本的 .NET Core 執行階段，請使用 `--fx-version <VERSION>` 選項 (請參閱 [dotnet 命令](dotnet.md) 參考)。</span><span class="sxs-lookup"><span data-stu-id="0137b-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="0137b-128">當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。</span><span class="sxs-lookup"><span data-stu-id="0137b-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="0137b-129">例如：</span><span class="sxs-lookup"><span data-stu-id="0137b-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="0137b-130">首先，驅動器會決定要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="0137b-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="0137b-131">如果沒有[全域.json](global-json.md)檔，則使用可用的 SDK 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="0137b-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="0137b-132">這可能是預覽版或穩定的版本，視兩者中何者版本最新。</span><span class="sxs-lookup"><span data-stu-id="0137b-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="0137b-133">確定 SDK 版本之後，就會開始執行命令。</span><span class="sxs-lookup"><span data-stu-id="0137b-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="0137b-134">Command</span><span class="sxs-lookup"><span data-stu-id="0137b-134">Command</span></span>

<span data-ttu-id="0137b-135">此命令會執行動作。</span><span class="sxs-lookup"><span data-stu-id="0137b-135">The command performs an action.</span></span> <span data-ttu-id="0137b-136">例如，`dotnet build` 會建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="0137b-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="0137b-137">`dotnet publish` 會發佈程式碼。</span><span class="sxs-lookup"><span data-stu-id="0137b-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="0137b-138">命令是使用 `dotnet {command}` 慣例實作為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0137b-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="0137b-139">引數</span><span class="sxs-lookup"><span data-stu-id="0137b-139">Arguments</span></span>

<span data-ttu-id="0137b-140">您在命令列上傳遞的引數即為叫用命令的引數。</span><span class="sxs-lookup"><span data-stu-id="0137b-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="0137b-141">例如當您執行 `dotnet publish my_app.csproj` 時，`my_app.csproj` 引數表示要發佈的專案，並且會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="0137b-141">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="0137b-142">選項。</span><span class="sxs-lookup"><span data-stu-id="0137b-142">Options</span></span>

<span data-ttu-id="0137b-143">您在命令列上傳遞的選項即為叫用命令的選項。</span><span class="sxs-lookup"><span data-stu-id="0137b-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="0137b-144">例如當您執行 `dotnet publish --output /build_output`，`--output` 選項及其值會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="0137b-144">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="0137b-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0137b-145">See also</span></span>

- [<span data-ttu-id="0137b-146">點網/sdk GitHub 存儲庫</span><span class="sxs-lookup"><span data-stu-id="0137b-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="0137b-147">.NET core 安裝指南 (英文)</span><span class="sxs-lookup"><span data-stu-id="0137b-147">.NET Core installation guide</span></span>](../install/sdk.md)
