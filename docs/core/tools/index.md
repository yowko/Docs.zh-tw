---
title: .NET CLI
titleSuffix: ''
description: .NET CLI 和其功能的總覽。
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 6a12e2d16afe36092c10e14a7465fa3bdbb23f32
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633852"
---
# <a name="net-cli-overview"></a><span data-ttu-id="6e4c3-103">.NET CLI 總覽</span><span class="sxs-lookup"><span data-stu-id="6e4c3-103">.NET CLI overview</span></span>

<span data-ttu-id="6e4c3-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="6e4c3-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="6e4c3-105">.NET 命令列介面 (CLI) 是用於開發、建立、執行和發佈 .NET 應用程式的跨平臺工具鏈。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-105">The .NET command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span>

<span data-ttu-id="6e4c3-106">.Net CLI 隨附于 [.NET SDK](../sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-106">The .NET CLI is included with the [.NET SDK](../sdk.md).</span></span> <span data-ttu-id="6e4c3-107">若要瞭解如何安裝 .NET SDK，請參閱 [安裝 .Net Core](../install/windows.md)。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-107">To learn how to install the .NET SDK, see [Install .NET Core](../install/windows.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="6e4c3-108">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="6e4c3-108">CLI commands</span></span>

<span data-ttu-id="6e4c3-109">預設會安裝下列命令：</span><span class="sxs-lookup"><span data-stu-id="6e4c3-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="6e4c3-110">基本命令</span><span class="sxs-lookup"><span data-stu-id="6e4c3-110">Basic commands</span></span>

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

### <a name="project-modification-commands"></a><span data-ttu-id="6e4c3-111">專案修改命令</span><span class="sxs-lookup"><span data-stu-id="6e4c3-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="6e4c3-112">進階命令</span><span class="sxs-lookup"><span data-stu-id="6e4c3-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="6e4c3-113">工具管理命令</span><span class="sxs-lookup"><span data-stu-id="6e4c3-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="6e4c3-114">[`tool restore`](global-tools.md#install-a-local-tool) 自 .NET Core SDK 3.0 起提供。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="6e4c3-115">[`tool run`](global-tools.md#invoke-a-local-tool) 自 .NET Core SDK 3.0 起提供。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="6e4c3-116">工具是從 NuGet 套件安裝的主控台應用程式，會從命令提示字元叫用。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="6e4c3-117">您可以自行撰寫工具或安裝協力廠商所撰寫的工具。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="6e4c3-118">工具也稱為「通用工具」、「工具路徑工具」和「本機工具」。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="6e4c3-119">如需詳細資訊，請參閱 [.net 工具總覽](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-119">For more information, see [.NET tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="6e4c3-120">命令結構</span><span class="sxs-lookup"><span data-stu-id="6e4c3-120">Command structure</span></span>

<span data-ttu-id="6e4c3-121">CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令](#command)，以及可能的命令[引數](#arguments)及[選項](#options)。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="6e4c3-122">您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：</span><span class="sxs-lookup"><span data-stu-id="6e4c3-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app* :</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="6e4c3-123">驅動程式</span><span class="sxs-lookup"><span data-stu-id="6e4c3-123">Driver</span></span>

<span data-ttu-id="6e4c3-124">驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="6e4c3-125">若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="6e4c3-126">從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="6e4c3-127">如果您想要使用特定版本的 .NET 執行時間，請使用 `--fx-version <VERSION>` 選項 (參閱 [dotnet 命令](dotnet.md) 參考) 。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-127">If you want to use a specific version of the .NET Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="6e4c3-128">當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="6e4c3-129">例如：</span><span class="sxs-lookup"><span data-stu-id="6e4c3-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="6e4c3-130">首先，驅動器會決定要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="6e4c3-131">如果檔案沒有 [global.js](global-json.md) ，則會使用最新版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="6e4c3-132">這可能是預覽版或穩定的版本，視兩者中何者版本最新。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="6e4c3-133">確定 SDK 版本之後，就會開始執行命令。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="6e4c3-134">命令</span><span class="sxs-lookup"><span data-stu-id="6e4c3-134">Command</span></span>

<span data-ttu-id="6e4c3-135">此命令會執行動作。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-135">The command performs an action.</span></span> <span data-ttu-id="6e4c3-136">例如，`dotnet build` 會建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="6e4c3-137">`dotnet publish` 會發佈程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="6e4c3-138">命令是使用 `dotnet {command}` 慣例實作為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="6e4c3-139">引數</span><span class="sxs-lookup"><span data-stu-id="6e4c3-139">Arguments</span></span>

<span data-ttu-id="6e4c3-140">您在命令列上傳遞的引數即為叫用命令的引數。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="6e4c3-141">例如，當您執行時 `dotnet publish my_app.csproj` ， `my_app.csproj` 引數會指出要發行的專案，並傳遞至 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="6e4c3-142">選項</span><span class="sxs-lookup"><span data-stu-id="6e4c3-142">Options</span></span>

<span data-ttu-id="6e4c3-143">您在命令列上傳遞的選項即為叫用命令的選項。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="6e4c3-144">例如，當您執行時 `dotnet publish --output /build_output` ， `--output` 選項和其值會傳遞至 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="6e4c3-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e4c3-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e4c3-145">See also</span></span>

- [<span data-ttu-id="6e4c3-146">dotnet/sdk GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="6e4c3-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="6e4c3-147">.NET 安裝指南</span><span class="sxs-lookup"><span data-stu-id="6e4c3-147">.NET installation guide</span></span>](../install/windows.md)
