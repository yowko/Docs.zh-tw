---
title: dotnet 命令 - .NET Core CLI
description: 了解 dotnet 命令 (.NET Core CLI 工具的通用驅動器) 和其用法。
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 53e8f8bab1cbaabaa7926aa68197c18843b0b637
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45615569"
---
# <a name="dotnet-command"></a><span data-ttu-id="445d0-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="445d0-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="445d0-104">名稱</span><span class="sxs-lookup"><span data-stu-id="445d0-104">Name</span></span>

<span data-ttu-id="445d0-105">`dotnet` - 管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="445d0-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="445d0-106">概要</span><span class="sxs-lookup"><span data-stu-id="445d0-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="445d0-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="445d0-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="445d0-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="445d0-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="445d0-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="445d0-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="445d0-110">描述</span><span class="sxs-lookup"><span data-stu-id="445d0-110">Description</span></span>

<span data-ttu-id="445d0-111">`dotnet` 是管理 .NET 原始程式碼和二進位檔的工具。</span><span class="sxs-lookup"><span data-stu-id="445d0-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="445d0-112">會公開執行特定工作的命令，例如 [`dotnet build`](dotnet-build.md) 和 [`dotnet run`](dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="445d0-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="445d0-113">每個命令會定義自己的引數。</span><span class="sxs-lookup"><span data-stu-id="445d0-113">Each command defines its own arguments.</span></span> <span data-ttu-id="445d0-114">每個命令後方鍵入 `--help` 以存取簡短說明文件。</span><span class="sxs-lookup"><span data-stu-id="445d0-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="445d0-115">可藉由指定應用程式 DLL (例如 `dotnet myapp.dll`)，使用 `dotnet` 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="445d0-116">請參閱 [.NET Core 應用程式部署](../deploying/index.md) 來了解部署選項。</span><span class="sxs-lookup"><span data-stu-id="445d0-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="445d0-117">選項</span><span class="sxs-lookup"><span data-stu-id="445d0-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="445d0-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="445d0-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="445d0-119">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="445d0-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="445d0-120">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="445d0-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="445d0-121">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="445d0-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="445d0-122">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="445d0-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="445d0-123">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="445d0-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="445d0-124">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="445d0-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="445d0-125">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="445d0-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="445d0-126">顯示已安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="445d0-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="445d0-127">顯示已安裝的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="445d0-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="445d0-128">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="445d0-128">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="445d0-129">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="445d0-129">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="445d0-130">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="445d0-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="445d0-131">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="445d0-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="445d0-132">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="445d0-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="445d0-133">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="445d0-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="445d0-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="445d0-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="445d0-135">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="445d0-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="445d0-136">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="445d0-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="445d0-137">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="445d0-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="445d0-138">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="445d0-138">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="445d0-139">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="445d0-139">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="445d0-140">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="445d0-140">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="445d0-141">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="445d0-141">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="445d0-142">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="445d0-142">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="445d0-143">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="445d0-143">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="445d0-144">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="445d0-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="445d0-145">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="445d0-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="445d0-146">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="445d0-146">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="445d0-147">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="445d0-147">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="445d0-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="445d0-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="445d0-149">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="445d0-149">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="445d0-150">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="445d0-150">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="445d0-151">用來執行應用程式的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="445d0-151">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="445d0-152">印出指定命令的文件，例如`dotnet build --help`。</span><span class="sxs-lookup"><span data-stu-id="445d0-152">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="445d0-153">`dotnet --help` 會印出可用命令的清單。</span><span class="sxs-lookup"><span data-stu-id="445d0-153">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="445d0-154">會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。</span><span class="sxs-lookup"><span data-stu-id="445d0-154">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="445d0-155">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="445d0-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="445d0-156">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="445d0-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="445d0-157">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="445d0-157">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="445d0-158">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="445d0-158">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="445d0-159">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="445d0-159">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="445d0-160">一般</span><span class="sxs-lookup"><span data-stu-id="445d0-160">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="445d0-161">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="445d0-161">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="445d0-162">命令</span><span class="sxs-lookup"><span data-stu-id="445d0-162">Command</span></span>                                       | <span data-ttu-id="445d0-163">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-163">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="445d0-164">dotnet build</span><span class="sxs-lookup"><span data-stu-id="445d0-164">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="445d0-165">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-165">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="445d0-166">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="445d0-166">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="445d0-167">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="445d0-167">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="445d0-168">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="445d0-168">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="445d0-169">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="445d0-169">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="445d0-170">dotnet help</span><span class="sxs-lookup"><span data-stu-id="445d0-170">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="445d0-171">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="445d0-171">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="445d0-172">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="445d0-172">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="445d0-173">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="445d0-173">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="445d0-174">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="445d0-174">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="445d0-175">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="445d0-175">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="445d0-176">dotnet new</span><span class="sxs-lookup"><span data-stu-id="445d0-176">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="445d0-177">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="445d0-177">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="445d0-178">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="445d0-178">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="445d0-179">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="445d0-179">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="445d0-180">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="445d0-180">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="445d0-181">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-181">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="445d0-182">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="445d0-182">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="445d0-183">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="445d0-183">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="445d0-184">dotnet run</span><span class="sxs-lookup"><span data-stu-id="445d0-184">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="445d0-185">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-185">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="445d0-186">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="445d0-186">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="445d0-187">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="445d0-187">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="445d0-188">dotnet store</span><span class="sxs-lookup"><span data-stu-id="445d0-188">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="445d0-189">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="445d0-189">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="445d0-190">dotnet test</span><span class="sxs-lookup"><span data-stu-id="445d0-190">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="445d0-191">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="445d0-191">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="445d0-192">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="445d0-192">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="445d0-193">命令</span><span class="sxs-lookup"><span data-stu-id="445d0-193">Command</span></span>                             | <span data-ttu-id="445d0-194">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-194">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="445d0-195">dotnet build</span><span class="sxs-lookup"><span data-stu-id="445d0-195">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="445d0-196">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-196">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="445d0-197">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="445d0-197">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="445d0-198">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="445d0-198">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="445d0-199">dotnet help</span><span class="sxs-lookup"><span data-stu-id="445d0-199">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="445d0-200">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="445d0-200">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="445d0-201">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="445d0-201">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="445d0-202">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="445d0-202">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="445d0-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="445d0-203">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="445d0-204">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="445d0-204">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="445d0-205">dotnet new</span><span class="sxs-lookup"><span data-stu-id="445d0-205">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="445d0-206">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="445d0-206">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="445d0-207">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="445d0-207">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="445d0-208">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="445d0-208">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="445d0-209">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="445d0-209">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="445d0-210">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-210">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="445d0-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="445d0-211">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="445d0-212">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="445d0-212">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="445d0-213">dotnet run</span><span class="sxs-lookup"><span data-stu-id="445d0-213">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="445d0-214">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-214">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="445d0-215">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="445d0-215">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="445d0-216">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="445d0-216">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="445d0-217">dotnet store</span><span class="sxs-lookup"><span data-stu-id="445d0-217">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="445d0-218">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="445d0-218">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="445d0-219">dotnet test</span><span class="sxs-lookup"><span data-stu-id="445d0-219">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="445d0-220">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="445d0-220">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="445d0-221">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="445d0-221">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="445d0-222">命令</span><span class="sxs-lookup"><span data-stu-id="445d0-222">Command</span></span>                             | <span data-ttu-id="445d0-223">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-223">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="445d0-224">dotnet build</span><span class="sxs-lookup"><span data-stu-id="445d0-224">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="445d0-225">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-225">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="445d0-226">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="445d0-226">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="445d0-227">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="445d0-227">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="445d0-228">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="445d0-228">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="445d0-229">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="445d0-229">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="445d0-230">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="445d0-230">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="445d0-231">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="445d0-231">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="445d0-232">dotnet new</span><span class="sxs-lookup"><span data-stu-id="445d0-232">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="445d0-233">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="445d0-233">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="445d0-234">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="445d0-234">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="445d0-235">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="445d0-235">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="445d0-236">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="445d0-236">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="445d0-237">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-237">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="445d0-238">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="445d0-238">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="445d0-239">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="445d0-239">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="445d0-240">dotnet run</span><span class="sxs-lookup"><span data-stu-id="445d0-240">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="445d0-241">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="445d0-241">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="445d0-242">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="445d0-242">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="445d0-243">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="445d0-243">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="445d0-244">dotnet test</span><span class="sxs-lookup"><span data-stu-id="445d0-244">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="445d0-245">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="445d0-245">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="445d0-246">專案參考</span><span class="sxs-lookup"><span data-stu-id="445d0-246">Project references</span></span>

<span data-ttu-id="445d0-247">命令</span><span class="sxs-lookup"><span data-stu-id="445d0-247">Command</span></span> | <span data-ttu-id="445d0-248">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-248">Function</span></span>
--- | ---
[<span data-ttu-id="445d0-249">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="445d0-249">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="445d0-250">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="445d0-250">Adds a project reference.</span></span>
[<span data-ttu-id="445d0-251">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="445d0-251">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="445d0-252">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="445d0-252">Lists project references.</span></span>
[<span data-ttu-id="445d0-253">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="445d0-253">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="445d0-254">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="445d0-254">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="445d0-255">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="445d0-255">NuGet packages</span></span>

<span data-ttu-id="445d0-256">命令</span><span class="sxs-lookup"><span data-stu-id="445d0-256">Command</span></span> | <span data-ttu-id="445d0-257">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-257">Function</span></span>
--- | ---
[<span data-ttu-id="445d0-258">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="445d0-258">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="445d0-259">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="445d0-259">Adds a NuGet package.</span></span>
[<span data-ttu-id="445d0-260">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="445d0-260">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="445d0-261">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="445d0-261">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="445d0-262">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="445d0-262">NuGet commands</span></span>

<span data-ttu-id="445d0-263">命令</span><span class="sxs-lookup"><span data-stu-id="445d0-263">Command</span></span> | <span data-ttu-id="445d0-264">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-264">Function</span></span>
--- | ---
[<span data-ttu-id="445d0-265">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="445d0-265">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="445d0-266">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="445d0-266">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="445d0-267">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="445d0-267">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="445d0-268">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="445d0-268">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="445d0-269">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="445d0-269">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="445d0-270">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="445d0-270">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="445d0-271">通用工具命令</span><span class="sxs-lookup"><span data-stu-id="445d0-271">Global Tools commands</span></span>

<span data-ttu-id="445d0-272">[.NET Core 通用工具](global-tools.md)將從 .NET Core SDK 2.1.300 開始提供使用：</span><span class="sxs-lookup"><span data-stu-id="445d0-272">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="445d0-273">命令</span><span class="sxs-lookup"><span data-stu-id="445d0-273">Command</span></span> | <span data-ttu-id="445d0-274">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-274">Function</span></span>
--- | ---
[<span data-ttu-id="445d0-275">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="445d0-275">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="445d0-276">在您的電腦上安裝通用工具。</span><span class="sxs-lookup"><span data-stu-id="445d0-276">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="445d0-277">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="445d0-277">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="445d0-278">列出在您電腦上的預設目錄或在指定路徑中目前已安裝的所有通用工具。</span><span class="sxs-lookup"><span data-stu-id="445d0-278">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="445d0-279">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="445d0-279">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="445d0-280">將通用工具從您的電腦解除安裝。</span><span class="sxs-lookup"><span data-stu-id="445d0-280">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="445d0-281">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="445d0-281">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="445d0-282">更新您電腦上的通用工具。</span><span class="sxs-lookup"><span data-stu-id="445d0-282">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="445d0-283">其他工具</span><span class="sxs-lookup"><span data-stu-id="445d0-283">Additional tools</span></span>

<span data-ttu-id="445d0-284">從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="445d0-284">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="445d0-285">這些工具列於下列資料表中：</span><span class="sxs-lookup"><span data-stu-id="445d0-285">These tools are listed in the following table:</span></span>

| <span data-ttu-id="445d0-286">工具</span><span class="sxs-lookup"><span data-stu-id="445d0-286">Tool</span></span>                                              | <span data-ttu-id="445d0-287">功能</span><span class="sxs-lookup"><span data-stu-id="445d0-287">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="445d0-288">dev-certs</span><span class="sxs-lookup"><span data-stu-id="445d0-288">dev-certs</span></span>                                         | <span data-ttu-id="445d0-289">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="445d0-289">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="445d0-290">ef</span><span class="sxs-lookup"><span data-stu-id="445d0-290">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="445d0-291">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="445d0-291">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="445d0-292">sql-cache</span><span class="sxs-lookup"><span data-stu-id="445d0-292">sql-cache</span></span>                                         | <span data-ttu-id="445d0-293">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="445d0-293">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="445d0-294">user-secrets</span><span class="sxs-lookup"><span data-stu-id="445d0-294">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="445d0-295">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="445d0-295">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="445d0-296">watch</span><span class="sxs-lookup"><span data-stu-id="445d0-296">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="445d0-297">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="445d0-297">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="445d0-298">如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="445d0-298">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="445d0-299">範例</span><span class="sxs-lookup"><span data-stu-id="445d0-299">Examples</span></span>

<span data-ttu-id="445d0-300">建立新的 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="445d0-300">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="445d0-301">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="445d0-301">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="445d0-302">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="445d0-302">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="445d0-303">執行應用程式 DLL，例如 `myapp.dll`：</span><span class="sxs-lookup"><span data-stu-id="445d0-303">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="445d0-304">環境變數</span><span class="sxs-lookup"><span data-stu-id="445d0-304">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="445d0-305">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="445d0-305">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="445d0-306">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="445d0-306">The primary package cache.</span></span> <span data-ttu-id="445d0-307">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="445d0-307">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="445d0-308">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="445d0-308">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="445d0-309">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="445d0-309">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="445d0-310">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="445d0-310">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="445d0-311">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="445d0-311">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="445d0-312">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="445d0-312">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="445d0-313">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="445d0-313">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="445d0-314">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="445d0-314">If not set, it defaults to `true`.</span></span> <span data-ttu-id="445d0-315">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="445d0-315">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="445d0-316">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="445d0-316">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="445d0-317">如果設定為 `0`，將停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="445d0-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="445d0-318">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="445d0-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="445d0-319">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="445d0-319">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="445d0-320">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="445d0-320">The primary package cache.</span></span> <span data-ttu-id="445d0-321">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="445d0-321">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="445d0-322">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="445d0-322">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="445d0-323">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="445d0-323">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="445d0-324">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="445d0-324">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="445d0-325">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="445d0-325">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="445d0-326">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="445d0-326">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="445d0-327">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="445d0-327">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="445d0-328">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="445d0-328">If not set, it defaults to `true`.</span></span> <span data-ttu-id="445d0-329">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="445d0-329">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="445d0-330">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="445d0-330">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="445d0-331">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="445d0-331">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="445d0-332">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="445d0-332">The primary package cache.</span></span> <span data-ttu-id="445d0-333">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="445d0-333">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="445d0-334">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="445d0-334">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="445d0-335">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="445d0-335">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="445d0-336">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="445d0-336">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="445d0-337">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="445d0-337">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="445d0-338">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="445d0-338">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
