---
title: .NET Core 命令列介面 (Command-Line Interface, CLI) 工具
description: .NET Core 命令列介面 (CLI) 工具與功能概觀。
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: 698e6188d2cc73c30a7003f53199065d1eff2ec0
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170183"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="dfb2a-103">.NET Core 命令列介面 (CLI) 工具</span><span class="sxs-lookup"><span data-stu-id="dfb2a-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="dfb2a-104">.NET Core 命令列介面 (CLI) 是新的跨平台工具鏈，適用於開發 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="dfb2a-105">CLI 是整合式開發環境 (IDE)、編輯器和建置 Orchestrator 等高層級工具所依靠的基礎。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="dfb2a-106">安裝</span><span class="sxs-lookup"><span data-stu-id="dfb2a-106">Installation</span></span>

<span data-ttu-id="dfb2a-107">使用原生安裝程式或使用安裝殼層指令碼：</span><span class="sxs-lookup"><span data-stu-id="dfb2a-107">Either use the native installers or use the installation shell scripts:</span></span>

* <span data-ttu-id="dfb2a-108">原生安裝程式主要用於開發人員的電腦，並且使用每個受支援平台的原生安裝機制，例如 Ubuntu 上的 DEB 套件，或 Windows 上的 MSI 套件組合。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="dfb2a-109">這些安裝程式安裝及設定的環境可供開發人員立即使用，但他們會需要電腦的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="dfb2a-110">您可以檢視 [.NET Core 安裝指南 (英文)](https://aka.ms/dotnetcoregs) 上的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
* <span data-ttu-id="dfb2a-111">殼層指令碼主要用於設定組建伺服器，或者當您想要安裝工具，但沒有系統管理權限時也可以使用。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="dfb2a-112">安裝指令碼不會在電腦上安裝必要的項目，所以您必須手動安裝這些項目。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="dfb2a-113">如需詳細資訊，請參閱[安裝指令碼參考主題](dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="dfb2a-114">如需如何在持續整合 (CI) 組建伺服器上設定 CLI 的詳細資訊，請參閱[在持續整合 (CI) 中使用 .NET Core SDK 和工具](using-ci-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="dfb2a-115">根據預設，CLI 會以並存 (Side-By-Side, SxS) 的形式安裝，因此一部電腦上可以同時存在多個版本的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="dfb2a-116">[驅動器](#driver)一節詳細說明如何在已安裝多個版本的電腦上判斷所使用的版本。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="dfb2a-117">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="dfb2a-117">CLI commands</span></span>

<span data-ttu-id="dfb2a-118">預設會安裝下列命令：</span><span class="sxs-lookup"><span data-stu-id="dfb2a-118">The following commands are installed by default:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb2a-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb2a-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="dfb2a-120">**基本命令**</span><span class="sxs-lookup"><span data-stu-id="dfb2a-120">**Basic commands**</span></span>

* [<span data-ttu-id="dfb2a-121">new</span><span class="sxs-lookup"><span data-stu-id="dfb2a-121">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="dfb2a-122">restore</span><span class="sxs-lookup"><span data-stu-id="dfb2a-122">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="dfb2a-123">build</span><span class="sxs-lookup"><span data-stu-id="dfb2a-123">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="dfb2a-124">publish</span><span class="sxs-lookup"><span data-stu-id="dfb2a-124">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="dfb2a-125">run</span><span class="sxs-lookup"><span data-stu-id="dfb2a-125">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="dfb2a-126">test</span><span class="sxs-lookup"><span data-stu-id="dfb2a-126">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="dfb2a-127">vstest</span><span class="sxs-lookup"><span data-stu-id="dfb2a-127">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="dfb2a-128">pack</span><span class="sxs-lookup"><span data-stu-id="dfb2a-128">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="dfb2a-129">migrate</span><span class="sxs-lookup"><span data-stu-id="dfb2a-129">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="dfb2a-130">clean</span><span class="sxs-lookup"><span data-stu-id="dfb2a-130">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="dfb2a-131">sln</span><span class="sxs-lookup"><span data-stu-id="dfb2a-131">sln</span></span>](dotnet-sln.md)
* [<span data-ttu-id="dfb2a-132">help</span><span class="sxs-lookup"><span data-stu-id="dfb2a-132">help</span></span>](dotnet-help.md)
* [<span data-ttu-id="dfb2a-133">store</span><span class="sxs-lookup"><span data-stu-id="dfb2a-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="dfb2a-134">**專案修改命令**</span><span class="sxs-lookup"><span data-stu-id="dfb2a-134">**Project modification commands**</span></span>

* [<span data-ttu-id="dfb2a-135">add package</span><span class="sxs-lookup"><span data-stu-id="dfb2a-135">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="dfb2a-136">add reference</span><span class="sxs-lookup"><span data-stu-id="dfb2a-136">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="dfb2a-137">remove package</span><span class="sxs-lookup"><span data-stu-id="dfb2a-137">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="dfb2a-138">remove reference</span><span class="sxs-lookup"><span data-stu-id="dfb2a-138">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="dfb2a-139">list reference</span><span class="sxs-lookup"><span data-stu-id="dfb2a-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="dfb2a-140">**進階命令**</span><span class="sxs-lookup"><span data-stu-id="dfb2a-140">**Advanced commands**</span></span>

* [<span data-ttu-id="dfb2a-141">nuget delete</span><span class="sxs-lookup"><span data-stu-id="dfb2a-141">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="dfb2a-142">nuget locals</span><span class="sxs-lookup"><span data-stu-id="dfb2a-142">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="dfb2a-143">nuget push</span><span class="sxs-lookup"><span data-stu-id="dfb2a-143">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="dfb2a-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="dfb2a-144">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="dfb2a-145">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="dfb2a-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb2a-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb2a-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="dfb2a-147">**基本命令**</span><span class="sxs-lookup"><span data-stu-id="dfb2a-147">**Basic commands**</span></span>

* [<span data-ttu-id="dfb2a-148">new</span><span class="sxs-lookup"><span data-stu-id="dfb2a-148">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="dfb2a-149">restore</span><span class="sxs-lookup"><span data-stu-id="dfb2a-149">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="dfb2a-150">build</span><span class="sxs-lookup"><span data-stu-id="dfb2a-150">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="dfb2a-151">publish</span><span class="sxs-lookup"><span data-stu-id="dfb2a-151">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="dfb2a-152">run</span><span class="sxs-lookup"><span data-stu-id="dfb2a-152">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="dfb2a-153">test</span><span class="sxs-lookup"><span data-stu-id="dfb2a-153">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="dfb2a-154">vstest</span><span class="sxs-lookup"><span data-stu-id="dfb2a-154">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="dfb2a-155">pack</span><span class="sxs-lookup"><span data-stu-id="dfb2a-155">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="dfb2a-156">migrate</span><span class="sxs-lookup"><span data-stu-id="dfb2a-156">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="dfb2a-157">clean</span><span class="sxs-lookup"><span data-stu-id="dfb2a-157">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="dfb2a-158">sln</span><span class="sxs-lookup"><span data-stu-id="dfb2a-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="dfb2a-159">**專案修改命令**</span><span class="sxs-lookup"><span data-stu-id="dfb2a-159">**Project modification commands**</span></span>

* [<span data-ttu-id="dfb2a-160">add package</span><span class="sxs-lookup"><span data-stu-id="dfb2a-160">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="dfb2a-161">add reference</span><span class="sxs-lookup"><span data-stu-id="dfb2a-161">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="dfb2a-162">remove package</span><span class="sxs-lookup"><span data-stu-id="dfb2a-162">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="dfb2a-163">remove reference</span><span class="sxs-lookup"><span data-stu-id="dfb2a-163">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="dfb2a-164">list reference</span><span class="sxs-lookup"><span data-stu-id="dfb2a-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="dfb2a-165">**進階命令**</span><span class="sxs-lookup"><span data-stu-id="dfb2a-165">**Advanced commands**</span></span>

* [<span data-ttu-id="dfb2a-166">nuget delete</span><span class="sxs-lookup"><span data-stu-id="dfb2a-166">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="dfb2a-167">nuget locals</span><span class="sxs-lookup"><span data-stu-id="dfb2a-167">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="dfb2a-168">nuget push</span><span class="sxs-lookup"><span data-stu-id="dfb2a-168">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="dfb2a-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="dfb2a-169">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="dfb2a-170">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="dfb2a-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="dfb2a-171">CLI 採用擴充性模型，可讓您為專案指定額外工具。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="dfb2a-172">如需詳細資訊，請參閱 [.NET Core CLI 擴充性模型](extensibility.md)主題。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="dfb2a-173">命令結構</span><span class="sxs-lookup"><span data-stu-id="dfb2a-173">Command structure</span></span>

<span data-ttu-id="dfb2a-174">CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令 (或「指令」)](#command-verb)，以及可能的命令[引數](#arguments)及[選項](#options)。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command (or "verb")](#command-verb), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="dfb2a-175">您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：</span><span class="sxs-lookup"><span data-stu-id="dfb2a-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb2a-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb2a-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb2a-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb2a-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="dfb2a-178">驅動器</span><span class="sxs-lookup"><span data-stu-id="dfb2a-178">Driver</span></span>

<span data-ttu-id="dfb2a-179">驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> <span data-ttu-id="dfb2a-180">唯獨啟動應用程式時會不搭配命令使用 `dotnet`。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-180">The only time `dotnet` is used without a command is when it's used to start an application.</span></span>

<span data-ttu-id="dfb2a-181">若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-181">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="dfb2a-182">從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-182">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span>

<span data-ttu-id="dfb2a-183">當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="dfb2a-184">首先，驅動器會決定要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-184">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="dfb2a-185">如果命令選項中未指定版本，則驅動器會使用可用的最新版本。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-185">If the version isn't specified in the command options, the driver uses the latest version available.</span></span> <span data-ttu-id="dfb2a-186">若要指定已安裝之最新版本以外的版本，請使用 `--fx-version <VERSION>` 選項 (請參閱 [dotnet 命令](dotnet.md)參考)。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-186">To specify a version other than the latest installed version, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span> <span data-ttu-id="dfb2a-187">決定 SDK 版本之後，驅動器會執行命令。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-187">Once the SDK version is determined, the driver executes the command.</span></span>

### <a name="command-verb"></a><span data-ttu-id="dfb2a-188">命令 (「動詞」)</span><span class="sxs-lookup"><span data-stu-id="dfb2a-188">Command ("verb")</span></span>

<span data-ttu-id="dfb2a-189">命令 (或「動詞」) 只是執行動作的命令。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-189">The command (or "verb") is simply a command that performs an action.</span></span> <span data-ttu-id="dfb2a-190">例如，`dotnet build` 會建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-190">For example, `dotnet build` builds your code.</span></span> <span data-ttu-id="dfb2a-191">`dotnet publish` 會發行程式碼。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-191">`dotnet publish` publishes your code.</span></span> <span data-ttu-id="dfb2a-192">命令是使用 `dotnet {verb}` 慣例實作為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-192">The commands are implemented as a console application using a `dotnet {verb}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="dfb2a-193">引數</span><span class="sxs-lookup"><span data-stu-id="dfb2a-193">Arguments</span></span>

<span data-ttu-id="dfb2a-194">您在命令列上傳遞的引數即為叫用命令的引數。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-194">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="dfb2a-195">例如當您執行 `dotnet publish my_app.csproj` 時，`my_app.csproj` 引數表示要發佈的專案，並且會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-195">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="dfb2a-196">選項</span><span class="sxs-lookup"><span data-stu-id="dfb2a-196">Options</span></span>

<span data-ttu-id="dfb2a-197">您在命令列上傳遞的選項即為叫用命令的選項。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-197">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="dfb2a-198">例如當您執行 `dotnet publish --output /build_output`，`--output` 選項及其值會傳遞給 `publish` 命令。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-198">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="dfb2a-199">從 project.json 移轉</span><span class="sxs-lookup"><span data-stu-id="dfb2a-199">Migration from project.json</span></span>

<span data-ttu-id="dfb2a-200">如果您使用 Preview 2 工具來產生 *project.json* 型專案，請參閱 [dotnet migrate](dotnet-migrate.md) 主題，來取得移轉專案至 MSBuild/*.csproj* 以搭配發行工具使用的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-200">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="dfb2a-201">對於在 Preview 2 工具發行之前建立的 .NET Core 專案，請依照[從 DNX 移轉到 .NET Core CLI (project.json)](../migration/from-dnx.md) 中的指導，手動更新專案，然後再使用 `dotnet migrate` 或直接升級您的專案。</span><span class="sxs-lookup"><span data-stu-id="dfb2a-201">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfb2a-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfb2a-202">See also</span></span>

* [<span data-ttu-id="dfb2a-203">dotnet/CLI GitHub 存放庫 (英文)</span><span class="sxs-lookup"><span data-stu-id="dfb2a-203">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)  
* [<span data-ttu-id="dfb2a-204">.NET core 安裝指南 (英文)</span><span class="sxs-lookup"><span data-stu-id="dfb2a-204">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)  
