---
title: dotnet 命令
description: 了解 dotnet 命令 (.NET Core CLI 工具的通用驅動器) 和其用法。
ms.date: 06/04/2018
ms.openlocfilehash: 2134bf8ed66157619499b027f01d39e03e84411f
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859544"
---
# <a name="dotnet-command"></a><span data-ttu-id="a4737-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="a4737-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a4737-104">名稱</span><span class="sxs-lookup"><span data-stu-id="a4737-104">Name</span></span>

<span data-ttu-id="a4737-105">`dotnet` - 管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="a4737-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a4737-106">概要</span><span class="sxs-lookup"><span data-stu-id="a4737-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a4737-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a4737-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a4737-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a4737-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4737-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4737-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="a4737-110">說明</span><span class="sxs-lookup"><span data-stu-id="a4737-110">Description</span></span>

<span data-ttu-id="a4737-111">`dotnet` 是管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="a4737-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="a4737-112">會公開執行特定工作的命令，例如 [`dotnet build`](dotnet-build.md) 和 [`dotnet run`](dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="a4737-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="a4737-113">每個命令會定義自己的引數。</span><span class="sxs-lookup"><span data-stu-id="a4737-113">Each command defines its own arguments.</span></span> <span data-ttu-id="a4737-114">每個命令後方鍵入 `--help` 以存取簡短說明文件。</span><span class="sxs-lookup"><span data-stu-id="a4737-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="a4737-115">可藉由指定應用程式 DLL (例如 `dotnet myapp.dll`)，使用 `dotnet` 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="a4737-116">請參閱 [.NET Core 應用程式部署](../deploying/index.md) 來了解部署選項。</span><span class="sxs-lookup"><span data-stu-id="a4737-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="a4737-117">選項</span><span class="sxs-lookup"><span data-stu-id="a4737-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a4737-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a4737-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="a4737-119">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4737-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a4737-120">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4737-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a4737-121">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="a4737-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a4737-122">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a4737-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a4737-123">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a4737-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a4737-124">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="a4737-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a4737-125">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="a4737-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="a4737-126">顯示已安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="a4737-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="a4737-127">顯示已安裝的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a4737-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="a4737-128">在必要的共用架構無法使用時定義行為。</span><span class="sxs-lookup"><span data-stu-id="a4737-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="a4737-129">`N` 可以是：</span><span class="sxs-lookup"><span data-stu-id="a4737-129">`N` can be:</span></span>
* <span data-ttu-id="a4737-130">`0` - 對次要版本也停用向前復原。</span><span class="sxs-lookup"><span data-stu-id="a4737-130">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="a4737-131">`1` - 對次要版本向前復原，主要版本則不。</span><span class="sxs-lookup"><span data-stu-id="a4737-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="a4737-132">這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="a4737-132">This is the default behavior.</span></span>
* <span data-ttu-id="a4737-133">`2` - 對次要及主要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a4737-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="a4737-134">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a4737-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a4737-135">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a4737-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4737-136">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a4737-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a4737-137">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="a4737-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a4737-138">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a4737-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a4737-139">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a4737-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="a4737-140">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4737-140">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a4737-141">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4737-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a4737-142">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="a4737-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a4737-143">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a4737-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a4737-144">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a4737-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a4737-145">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="a4737-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a4737-146">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="a4737-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="a4737-147">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a4737-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a4737-148">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a4737-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a4737-149">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a4737-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4737-150">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a4737-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a4737-151">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="a4737-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a4737-152">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a4737-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4737-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4737-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="a4737-154">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4737-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a4737-155">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="a4737-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a4737-156">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a4737-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a4737-157">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="a4737-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a4737-158">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="a4737-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a4737-159">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="a4737-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a4737-160">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a4737-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4737-161">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a4737-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a4737-162">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="a4737-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a4737-163">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a4737-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="a4737-164">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="a4737-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="a4737-165">一般</span><span class="sxs-lookup"><span data-stu-id="a4737-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a4737-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a4737-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="a4737-167">命令</span><span class="sxs-lookup"><span data-stu-id="a4737-167">Command</span></span>                                       | <span data-ttu-id="a4737-168">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a4737-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a4737-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="a4737-170">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a4737-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="a4737-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="a4737-172">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="a4737-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="a4737-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a4737-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="a4737-174">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="a4737-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="a4737-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a4737-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="a4737-176">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="a4737-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a4737-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a4737-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="a4737-178">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="a4737-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a4737-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a4737-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="a4737-180">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="a4737-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a4737-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a4737-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="a4737-182">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="a4737-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a4737-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a4737-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="a4737-184">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a4737-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a4737-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a4737-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="a4737-186">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a4737-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a4737-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="a4737-188">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a4737-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a4737-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a4737-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="a4737-190">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a4737-191">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a4737-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="a4737-192">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="a4737-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a4737-193">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a4737-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="a4737-194">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="a4737-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a4737-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a4737-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="a4737-196">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="a4737-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a4737-197">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a4737-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="a4737-198">命令</span><span class="sxs-lookup"><span data-stu-id="a4737-198">Command</span></span>                             | <span data-ttu-id="a4737-199">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a4737-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a4737-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a4737-201">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a4737-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a4737-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a4737-203">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="a4737-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a4737-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a4737-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="a4737-205">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="a4737-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a4737-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a4737-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a4737-207">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="a4737-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a4737-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a4737-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a4737-209">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="a4737-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a4737-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a4737-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a4737-211">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="a4737-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a4737-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a4737-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a4737-213">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a4737-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a4737-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a4737-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a4737-215">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a4737-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a4737-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a4737-217">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a4737-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a4737-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a4737-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a4737-219">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a4737-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a4737-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a4737-221">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="a4737-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a4737-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a4737-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="a4737-223">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="a4737-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a4737-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a4737-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a4737-225">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="a4737-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4737-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4737-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="a4737-227">命令</span><span class="sxs-lookup"><span data-stu-id="a4737-227">Command</span></span>                             | <span data-ttu-id="a4737-228">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a4737-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a4737-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a4737-230">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a4737-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a4737-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a4737-232">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="a4737-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a4737-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a4737-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a4737-234">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="a4737-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a4737-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a4737-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a4737-236">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="a4737-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a4737-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a4737-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a4737-238">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="a4737-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a4737-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a4737-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a4737-240">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a4737-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a4737-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a4737-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a4737-242">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a4737-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a4737-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a4737-244">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a4737-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a4737-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a4737-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a4737-246">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4737-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a4737-247">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a4737-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a4737-248">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="a4737-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a4737-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a4737-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a4737-250">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="a4737-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="a4737-251">專案參考</span><span class="sxs-lookup"><span data-stu-id="a4737-251">Project references</span></span>

<span data-ttu-id="a4737-252">命令</span><span class="sxs-lookup"><span data-stu-id="a4737-252">Command</span></span> | <span data-ttu-id="a4737-253">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-253">Function</span></span>
--- | ---
[<span data-ttu-id="a4737-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a4737-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="a4737-255">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="a4737-255">Adds a project reference.</span></span>
[<span data-ttu-id="a4737-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a4737-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="a4737-257">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="a4737-257">Lists project references.</span></span>
[<span data-ttu-id="a4737-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="a4737-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="a4737-259">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="a4737-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="a4737-260">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="a4737-260">NuGet packages</span></span>

<span data-ttu-id="a4737-261">命令</span><span class="sxs-lookup"><span data-stu-id="a4737-261">Command</span></span> | <span data-ttu-id="a4737-262">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-262">Function</span></span>
--- | ---
[<span data-ttu-id="a4737-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="a4737-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="a4737-264">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a4737-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="a4737-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="a4737-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="a4737-266">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a4737-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="a4737-267">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="a4737-267">NuGet commands</span></span>

<span data-ttu-id="a4737-268">命令</span><span class="sxs-lookup"><span data-stu-id="a4737-268">Command</span></span> | <span data-ttu-id="a4737-269">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-269">Function</span></span>
--- | ---
[<span data-ttu-id="a4737-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="a4737-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="a4737-271">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="a4737-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="a4737-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="a4737-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="a4737-273">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="a4737-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="a4737-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a4737-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="a4737-275">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="a4737-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="a4737-276">通用工具命令</span><span class="sxs-lookup"><span data-stu-id="a4737-276">Global Tools commands</span></span>

<span data-ttu-id="a4737-277">[.NET Core 通用工具](global-tools.md)將從 .NET Core SDK 2.1.300 開始提供使用：</span><span class="sxs-lookup"><span data-stu-id="a4737-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="a4737-278">命令</span><span class="sxs-lookup"><span data-stu-id="a4737-278">Command</span></span> | <span data-ttu-id="a4737-279">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-279">Function</span></span>
--- | ---
[<span data-ttu-id="a4737-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="a4737-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="a4737-281">在您的電腦上安裝通用工具。</span><span class="sxs-lookup"><span data-stu-id="a4737-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="a4737-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a4737-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="a4737-283">列出在您電腦上的預設目錄或在指定路徑中目前已安裝的所有通用工具。</span><span class="sxs-lookup"><span data-stu-id="a4737-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="a4737-284">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="a4737-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="a4737-285">將通用工具從您的電腦解除安裝。</span><span class="sxs-lookup"><span data-stu-id="a4737-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="a4737-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="a4737-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="a4737-287">更新您電腦上的通用工具。</span><span class="sxs-lookup"><span data-stu-id="a4737-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="a4737-288">其他工具</span><span class="sxs-lookup"><span data-stu-id="a4737-288">Additional tools</span></span>

<span data-ttu-id="a4737-289">從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="a4737-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="a4737-290">這些工具列於下列資料表中：</span><span class="sxs-lookup"><span data-stu-id="a4737-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="a4737-291">工具</span><span class="sxs-lookup"><span data-stu-id="a4737-291">Tool</span></span>                                              | <span data-ttu-id="a4737-292">功能</span><span class="sxs-lookup"><span data-stu-id="a4737-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="a4737-293">dev-certs</span><span class="sxs-lookup"><span data-stu-id="a4737-293">dev-certs</span></span>                                         | <span data-ttu-id="a4737-294">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="a4737-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="a4737-295">ef</span><span class="sxs-lookup"><span data-stu-id="a4737-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="a4737-296">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a4737-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="a4737-297">sql-cache</span><span class="sxs-lookup"><span data-stu-id="a4737-297">sql-cache</span></span>                                         | <span data-ttu-id="a4737-298">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a4737-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="a4737-299">user-secrets</span><span class="sxs-lookup"><span data-stu-id="a4737-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="a4737-300">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="a4737-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="a4737-301">watch</span><span class="sxs-lookup"><span data-stu-id="a4737-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="a4737-302">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="a4737-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="a4737-303">如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="a4737-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="a4737-304">範例</span><span class="sxs-lookup"><span data-stu-id="a4737-304">Examples</span></span>

<span data-ttu-id="a4737-305">建立新的 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="a4737-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="a4737-306">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="a4737-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a4737-307">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="a4737-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="a4737-308">執行應用程式 DLL，例如 `myapp.dll`：</span><span class="sxs-lookup"><span data-stu-id="a4737-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="a4737-309">環境變數</span><span class="sxs-lookup"><span data-stu-id="a4737-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a4737-310">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a4737-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="a4737-311">全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="a4737-311">The global packages folder.</span></span> <span data-ttu-id="a4737-312">如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="a4737-312">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a4737-313">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="a4737-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a4737-314">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a4737-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a4737-315">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="a4737-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a4737-316">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="a4737-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a4737-317">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="a4737-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a4737-318">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="a4737-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a4737-319">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a4737-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a4737-320">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="a4737-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a4737-321">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="a4737-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="a4737-322">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="a4737-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a4737-323">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="a4737-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a4737-324">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a4737-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="a4737-325">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="a4737-325">The primary package cache.</span></span> <span data-ttu-id="a4737-326">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="a4737-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a4737-327">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="a4737-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a4737-328">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a4737-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a4737-329">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="a4737-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a4737-330">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="a4737-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a4737-331">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="a4737-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a4737-332">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="a4737-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a4737-333">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a4737-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a4737-334">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="a4737-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a4737-335">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="a4737-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4737-336">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4737-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="a4737-337">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="a4737-337">The primary package cache.</span></span> <span data-ttu-id="a4737-338">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="a4737-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a4737-339">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="a4737-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a4737-340">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a4737-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a4737-341">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="a4737-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a4737-342">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="a4737-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a4737-343">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="a4737-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
