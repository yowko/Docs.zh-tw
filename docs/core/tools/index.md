---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI 及其功能的總覽。
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920487"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="142b7-103">.NET Core CLI 總覽</span><span class="sxs-lookup"><span data-stu-id="142b7-103">.NET Core CLI overview</span></span>

<span data-ttu-id="142b7-104">.NET Core 命令列介面（CLI）是用於開發、建立、執行和發佈 .NET Core 應用程式的跨平臺工具鏈。</span><span class="sxs-lookup"><span data-stu-id="142b7-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="142b7-105">.NET Core CLI 包含在[.NET Core SDK](../sdk.md)中。</span><span class="sxs-lookup"><span data-stu-id="142b7-105">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="142b7-106">若要瞭解如何安裝 .NET Core SDK，請參閱[安裝 .NET Core SDK](../install/sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="142b7-106">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="142b7-107">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="142b7-107">CLI commands</span></span>

<span data-ttu-id="142b7-108">預設會安裝下列命令：</span><span class="sxs-lookup"><span data-stu-id="142b7-108">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="142b7-109">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="142b7-109">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="142b7-110">**基本命令**</span><span class="sxs-lookup"><span data-stu-id="142b7-110">**Basic commands**</span></span>

- [<span data-ttu-id="142b7-111">new</span><span class="sxs-lookup"><span data-stu-id="142b7-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="142b7-112">restore</span><span class="sxs-lookup"><span data-stu-id="142b7-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="142b7-113">build</span><span class="sxs-lookup"><span data-stu-id="142b7-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="142b7-114">publish</span><span class="sxs-lookup"><span data-stu-id="142b7-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="142b7-115">run</span><span class="sxs-lookup"><span data-stu-id="142b7-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="142b7-116">test</span><span class="sxs-lookup"><span data-stu-id="142b7-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="142b7-117">vstest</span><span class="sxs-lookup"><span data-stu-id="142b7-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="142b7-118">pack</span><span class="sxs-lookup"><span data-stu-id="142b7-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="142b7-119">migrate</span><span class="sxs-lookup"><span data-stu-id="142b7-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="142b7-120">clean</span><span class="sxs-lookup"><span data-stu-id="142b7-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="142b7-121">sln</span><span class="sxs-lookup"><span data-stu-id="142b7-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="142b7-122">help</span><span class="sxs-lookup"><span data-stu-id="142b7-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="142b7-123">store</span><span class="sxs-lookup"><span data-stu-id="142b7-123">store</span></span>](dotnet-store.md)

<span data-ttu-id="142b7-124">**專案修改命令**</span><span class="sxs-lookup"><span data-stu-id="142b7-124">**Project modification commands**</span></span>

- [<span data-ttu-id="142b7-125">add package</span><span class="sxs-lookup"><span data-stu-id="142b7-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="142b7-126">add reference</span><span class="sxs-lookup"><span data-stu-id="142b7-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="142b7-127">remove package</span><span class="sxs-lookup"><span data-stu-id="142b7-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="142b7-128">remove reference</span><span class="sxs-lookup"><span data-stu-id="142b7-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="142b7-129">list reference</span><span class="sxs-lookup"><span data-stu-id="142b7-129">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="142b7-130">**進階命令**</span><span class="sxs-lookup"><span data-stu-id="142b7-130">**Advanced commands**</span></span>

- [<span data-ttu-id="142b7-131">nuget delete</span><span class="sxs-lookup"><span data-stu-id="142b7-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="142b7-132">nuget locals</span><span class="sxs-lookup"><span data-stu-id="142b7-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="142b7-133">nuget push</span><span class="sxs-lookup"><span data-stu-id="142b7-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="142b7-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="142b7-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="142b7-135">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="142b7-135">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="142b7-136">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="142b7-136">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="142b7-137">**基本命令**</span><span class="sxs-lookup"><span data-stu-id="142b7-137">**Basic commands**</span></span>

- [<span data-ttu-id="142b7-138">new</span><span class="sxs-lookup"><span data-stu-id="142b7-138">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="142b7-139">restore</span><span class="sxs-lookup"><span data-stu-id="142b7-139">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="142b7-140">build</span><span class="sxs-lookup"><span data-stu-id="142b7-140">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="142b7-141">publish</span><span class="sxs-lookup"><span data-stu-id="142b7-141">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="142b7-142">run</span><span class="sxs-lookup"><span data-stu-id="142b7-142">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="142b7-143">test</span><span class="sxs-lookup"><span data-stu-id="142b7-143">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="142b7-144">vstest</span><span class="sxs-lookup"><span data-stu-id="142b7-144">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="142b7-145">pack</span><span class="sxs-lookup"><span data-stu-id="142b7-145">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="142b7-146">migrate</span><span class="sxs-lookup"><span data-stu-id="142b7-146">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="142b7-147">clean</span><span class="sxs-lookup"><span data-stu-id="142b7-147">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="142b7-148">sln</span><span class="sxs-lookup"><span data-stu-id="142b7-148">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="142b7-149">**專案修改命令**</span><span class="sxs-lookup"><span data-stu-id="142b7-149">**Project modification commands**</span></span>

- [<span data-ttu-id="142b7-150">add package</span><span class="sxs-lookup"><span data-stu-id="142b7-150">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="142b7-151">add reference</span><span class="sxs-lookup"><span data-stu-id="142b7-151">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="142b7-152">remove package</span><span class="sxs-lookup"><span data-stu-id="142b7-152">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="142b7-153">remove reference</span><span class="sxs-lookup"><span data-stu-id="142b7-153">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="142b7-154">list reference</span><span class="sxs-lookup"><span data-stu-id="142b7-154">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="142b7-155">**進階命令**</span><span class="sxs-lookup"><span data-stu-id="142b7-155">**Advanced commands**</span></span>

- [<span data-ttu-id="142b7-156">nuget delete</span><span class="sxs-lookup"><span data-stu-id="142b7-156">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="142b7-157">nuget locals</span><span class="sxs-lookup"><span data-stu-id="142b7-157">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="142b7-158">nuget push</span><span class="sxs-lookup"><span data-stu-id="142b7-158">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="142b7-159">msbuild</span><span class="sxs-lookup"><span data-stu-id="142b7-159">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="142b7-160">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="142b7-160">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="142b7-161">CLI 採用擴充性模型，可讓您為專案指定額外工具。</span><span class="sxs-lookup"><span data-stu-id="142b7-161">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="142b7-162">如需詳細資訊，請參閱 [.NET Core CLI 擴充性模型](extensibility.md)主題。</span><span class="sxs-lookup"><span data-stu-id="142b7-162">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="142b7-163">命令結構</span><span class="sxs-lookup"><span data-stu-id="142b7-163">Command structure</span></span>

<span data-ttu-id="142b7-164">CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令](#command)，以及可能的命令[引數](#arguments)及[選項](#options)。</span><span class="sxs-lookup"><span data-stu-id="142b7-164">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="142b7-165">您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：</span><span class="sxs-lookup"><span data-stu-id="142b7-165">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="142b7-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="142b7-166">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="142b7-167">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="142b7-167">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="142b7-168">驅動器</span><span class="sxs-lookup"><span data-stu-id="142b7-168">Driver</span></span>

<span data-ttu-id="142b7-169">驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。</span><span class="sxs-lookup"><span data-stu-id="142b7-169">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="142b7-170">若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。</span><span class="sxs-lookup"><span data-stu-id="142b7-170">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="142b7-171">從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。</span><span class="sxs-lookup"><span data-stu-id="142b7-171">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="142b7-172">若要使用特定版本的 .NET Core 執行階段，請使用 `--fx-version <VERSION>` 選項 (請參閱 [dotnet 命令](dotnet.md) 參考)。</span><span class="sxs-lookup"><span data-stu-id="142b7-172">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="142b7-173">當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。</span><span class="sxs-lookup"><span data-stu-id="142b7-173">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="142b7-174">例如：</span><span class="sxs-lookup"><span data-stu-id="142b7-174">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="142b7-175">首先，驅動器會決定要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="142b7-175">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="142b7-176">若沒有 ['global.json'](global-json.md)，將會使用最新可用版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="142b7-176">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="142b7-177">這可能是預覽版或穩定的版本，視兩者中何者版本最新。</span><span class="sxs-lookup"><span data-stu-id="142b7-177">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="142b7-178">確定 SDK 版本之後，就會開始執行命令。</span><span class="sxs-lookup"><span data-stu-id="142b7-178">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="142b7-179">命令</span><span class="sxs-lookup"><span data-stu-id="142b7-179">Command</span></span>

<span data-ttu-id="142b7-180">此命令會執行動作。</span><span class="sxs-lookup"><span data-stu-id="142b7-180">The command performs an action.</span></span> <span data-ttu-id="142b7-181">例如，`dotnet build` 會建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="142b7-181">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="142b7-182">`dotnet publish` 會發佈程式碼。</span><span class="sxs-lookup"><span data-stu-id="142b7-182">`dotnet publish` publishes code.</span></span> <span data-ttu-id="142b7-183">命令是使用 `dotnet {command}` 慣例實作為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="142b7-183">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="142b7-184">Arguments</span><span class="sxs-lookup"><span data-stu-id="142b7-184">Arguments</span></span>

<span data-ttu-id="142b7-185">您在命令列上傳遞的引數即為叫用命令的引數。</span><span class="sxs-lookup"><span data-stu-id="142b7-185">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="142b7-186">例如當您執行 `dotnet publish my_app.csproj` 時，`my_app.csproj` 引數表示要發佈的專案，並且會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="142b7-186">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="142b7-187">選項</span><span class="sxs-lookup"><span data-stu-id="142b7-187">Options</span></span>

<span data-ttu-id="142b7-188">您在命令列上傳遞的選項即為叫用命令的選項。</span><span class="sxs-lookup"><span data-stu-id="142b7-188">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="142b7-189">例如當您執行 `dotnet publish --output /build_output`，`--output` 選項及其值會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="142b7-189">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="142b7-190">從 project.json 移轉</span><span class="sxs-lookup"><span data-stu-id="142b7-190">Migration from project.json</span></span>

<span data-ttu-id="142b7-191">如果您使用 Preview 2 工具來產生 *project.json* 型專案，請參閱 [dotnet migrate](dotnet-migrate.md) 主題，來取得移轉專案至 MSBuild/ *.csproj* 以搭配發行工具使用的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="142b7-191">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="142b7-192">對於在 Preview 2 工具發行之前建立的 .NET Core 專案，請依照[從 DNX 移轉到 .NET Core CLI (project.json)](../migration/from-dnx.md) 中的指導，手動更新專案，然後再使用 `dotnet migrate` 或直接升級您的專案。</span><span class="sxs-lookup"><span data-stu-id="142b7-192">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="142b7-193">請參閱</span><span class="sxs-lookup"><span data-stu-id="142b7-193">See also</span></span>

- [<span data-ttu-id="142b7-194">dotnet/sdk GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="142b7-194">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="142b7-195">.NET core 安裝指南 (英文)</span><span class="sxs-lookup"><span data-stu-id="142b7-195">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
