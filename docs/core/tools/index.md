---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI 及其功能的總覽。
ms.date: 02/13/2020
ms.openlocfilehash: c491088f26a9aa1c065414e76fb0b80d554380b4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625978"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="c7081-103">.NET Core CLI 總覽</span><span class="sxs-lookup"><span data-stu-id="c7081-103">.NET Core CLI overview</span></span>

<span data-ttu-id="c7081-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="c7081-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="c7081-105">.NET Core 命令列介面（CLI）是用於開發、建立、執行和發佈 .NET Core 應用程式的跨平臺工具鏈。</span><span class="sxs-lookup"><span data-stu-id="c7081-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="c7081-106">.NET Core CLI 包含在[.NET Core SDK](../sdk.md)中。</span><span class="sxs-lookup"><span data-stu-id="c7081-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="c7081-107">若要瞭解如何安裝 .NET Core SDK，請參閱[安裝 .NET Core SDK](../install/sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="c7081-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="c7081-108">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="c7081-108">CLI commands</span></span>

<span data-ttu-id="c7081-109">預設會安裝下列命令：</span><span class="sxs-lookup"><span data-stu-id="c7081-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="c7081-110">基本命令</span><span class="sxs-lookup"><span data-stu-id="c7081-110">Basic commands</span></span>

- [<span data-ttu-id="c7081-111">new</span><span class="sxs-lookup"><span data-stu-id="c7081-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="c7081-112">還原</span><span class="sxs-lookup"><span data-stu-id="c7081-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="c7081-113">build</span><span class="sxs-lookup"><span data-stu-id="c7081-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="c7081-114">publish</span><span class="sxs-lookup"><span data-stu-id="c7081-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="c7081-115">run</span><span class="sxs-lookup"><span data-stu-id="c7081-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="c7081-116">test</span><span class="sxs-lookup"><span data-stu-id="c7081-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="c7081-117">vstest</span><span class="sxs-lookup"><span data-stu-id="c7081-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="c7081-118">pack</span><span class="sxs-lookup"><span data-stu-id="c7081-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="c7081-119">移轉</span><span class="sxs-lookup"><span data-stu-id="c7081-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="c7081-120">clean</span><span class="sxs-lookup"><span data-stu-id="c7081-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="c7081-121">sln</span><span class="sxs-lookup"><span data-stu-id="c7081-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="c7081-122">help</span><span class="sxs-lookup"><span data-stu-id="c7081-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="c7081-123">store</span><span class="sxs-lookup"><span data-stu-id="c7081-123">store</span></span>](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="c7081-124">專案修改命令</span><span class="sxs-lookup"><span data-stu-id="c7081-124">Project modification commands</span></span>

- [<span data-ttu-id="c7081-125">add package</span><span class="sxs-lookup"><span data-stu-id="c7081-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="c7081-126">add reference</span><span class="sxs-lookup"><span data-stu-id="c7081-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="c7081-127">remove package</span><span class="sxs-lookup"><span data-stu-id="c7081-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="c7081-128">remove reference</span><span class="sxs-lookup"><span data-stu-id="c7081-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="c7081-129">list reference</span><span class="sxs-lookup"><span data-stu-id="c7081-129">list reference</span></span>](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="c7081-130">進階命令</span><span class="sxs-lookup"><span data-stu-id="c7081-130">Advanced commands</span></span>

- [<span data-ttu-id="c7081-131">nuget delete</span><span class="sxs-lookup"><span data-stu-id="c7081-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="c7081-132">nuget locals</span><span class="sxs-lookup"><span data-stu-id="c7081-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="c7081-133">nuget push</span><span class="sxs-lookup"><span data-stu-id="c7081-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="c7081-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="c7081-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="c7081-135">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="c7081-135">dotnet install script</span></span>](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="c7081-136">工具管理命令</span><span class="sxs-lookup"><span data-stu-id="c7081-136">Tool management commands</span></span>

- [<span data-ttu-id="c7081-137">工具安裝</span><span class="sxs-lookup"><span data-stu-id="c7081-137">tool install</span></span>](dotnet-tool-install.md)
- [<span data-ttu-id="c7081-138">工具清單</span><span class="sxs-lookup"><span data-stu-id="c7081-138">tool list</span></span>](dotnet-tool-list.md)
- [<span data-ttu-id="c7081-139">工具更新</span><span class="sxs-lookup"><span data-stu-id="c7081-139">tool update</span></span>](dotnet-tool-update.md)
- <span data-ttu-id="c7081-140">**從 .NET Core SDK 3.0 開始提供的**[工具還原](global-tools.md#install-a-local-tool)</span><span class="sxs-lookup"><span data-stu-id="c7081-140">[tool restore](global-tools.md#install-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- <span data-ttu-id="c7081-141">**從 .NET Core SDK 3.0 開始提供的**[工具執行](global-tools.md#invoke-a-local-tool)</span><span class="sxs-lookup"><span data-stu-id="c7081-141">[tool run](global-tools.md#invoke-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- [<span data-ttu-id="c7081-142">工具卸載</span><span class="sxs-lookup"><span data-stu-id="c7081-142">tool uninstall</span></span>](dotnet-tool-uninstall.md)

<span data-ttu-id="c7081-143">工具是從 NuGet 套件安裝並從命令提示字元叫用的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7081-143">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="c7081-144">您可以自行撰寫工具，或安裝由協力廠商撰寫的工具。</span><span class="sxs-lookup"><span data-stu-id="c7081-144">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="c7081-145">工具也稱為「通用工具」、「工具路徑工具」和「本機工具」。</span><span class="sxs-lookup"><span data-stu-id="c7081-145">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="c7081-146">如需詳細資訊，請參閱[.Net Core 工具總覽](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c7081-146">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="c7081-147">命令結構</span><span class="sxs-lookup"><span data-stu-id="c7081-147">Command structure</span></span>

<span data-ttu-id="c7081-148">CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令](#command)，以及可能的命令[引數](#arguments)及[選項](#options)。</span><span class="sxs-lookup"><span data-stu-id="c7081-148">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="c7081-149">您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：</span><span class="sxs-lookup"><span data-stu-id="c7081-149">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="c7081-150">驅動程式</span><span class="sxs-lookup"><span data-stu-id="c7081-150">Driver</span></span>

<span data-ttu-id="c7081-151">驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。</span><span class="sxs-lookup"><span data-stu-id="c7081-151">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="c7081-152">若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。</span><span class="sxs-lookup"><span data-stu-id="c7081-152">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="c7081-153">從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。</span><span class="sxs-lookup"><span data-stu-id="c7081-153">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="c7081-154">若要使用特定版本的 .NET Core 執行階段，請使用 `--fx-version <VERSION>` 選項 (請參閱 [dotnet 命令](dotnet.md) 參考)。</span><span class="sxs-lookup"><span data-stu-id="c7081-154">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="c7081-155">當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。</span><span class="sxs-lookup"><span data-stu-id="c7081-155">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="c7081-156">例如：</span><span class="sxs-lookup"><span data-stu-id="c7081-156">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="c7081-157">首先，驅動器會決定要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c7081-157">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="c7081-158">如果沒有[global json](global-json.md)檔案，則會使用可用的最新 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c7081-158">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="c7081-159">這可能是預覽版或穩定的版本，視兩者中何者版本最新。</span><span class="sxs-lookup"><span data-stu-id="c7081-159">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="c7081-160">確定 SDK 版本之後，就會開始執行命令。</span><span class="sxs-lookup"><span data-stu-id="c7081-160">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="c7081-161">Command</span><span class="sxs-lookup"><span data-stu-id="c7081-161">Command</span></span>

<span data-ttu-id="c7081-162">此命令會執行動作。</span><span class="sxs-lookup"><span data-stu-id="c7081-162">The command performs an action.</span></span> <span data-ttu-id="c7081-163">例如，`dotnet build` 會建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7081-163">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="c7081-164">`dotnet publish` 會發佈程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7081-164">`dotnet publish` publishes code.</span></span> <span data-ttu-id="c7081-165">命令是使用 `dotnet {command}` 慣例實作為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7081-165">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="c7081-166">引數</span><span class="sxs-lookup"><span data-stu-id="c7081-166">Arguments</span></span>

<span data-ttu-id="c7081-167">您在命令列上傳遞的引數即為叫用命令的引數。</span><span class="sxs-lookup"><span data-stu-id="c7081-167">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="c7081-168">例如當您執行 `dotnet publish my_app.csproj` 時，`my_app.csproj` 引數表示要發佈的專案，並且會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="c7081-168">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="c7081-169">選項。</span><span class="sxs-lookup"><span data-stu-id="c7081-169">Options</span></span>

<span data-ttu-id="c7081-170">您在命令列上傳遞的選項即為叫用命令的選項。</span><span class="sxs-lookup"><span data-stu-id="c7081-170">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="c7081-171">例如當您執行 `dotnet publish --output /build_output`，`--output` 選項及其值會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="c7081-171">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7081-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7081-172">See also</span></span>

- [<span data-ttu-id="c7081-173">dotnet/sdk GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="c7081-173">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="c7081-174">.NET core 安裝指南 (英文)</span><span class="sxs-lookup"><span data-stu-id="c7081-174">.NET Core installation guide</span></span>](../install/sdk.md)
