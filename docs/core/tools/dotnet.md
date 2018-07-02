---
title: dotnet 命令 - .NET Core CLI
description: 了解 dotnet 命令 (.NET Core CLI 工具的通用驅動器) 和其用法。
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 788dc746705f9328683019ab3ad9836204a1ea63
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805655"
---
# <a name="dotnet-command"></a><span data-ttu-id="d2249-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="d2249-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d2249-104">名稱</span><span class="sxs-lookup"><span data-stu-id="d2249-104">Name</span></span>

<span data-ttu-id="d2249-105">`dotnet` - 用於執行命令列命令的一般驅動器。</span><span class="sxs-lookup"><span data-stu-id="d2249-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2249-106">概要</span><span class="sxs-lookup"><span data-stu-id="d2249-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d2249-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d2249-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d2249-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d2249-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2249-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d2249-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="d2249-110">描述</span><span class="sxs-lookup"><span data-stu-id="d2249-110">Description</span></span>

<span data-ttu-id="d2249-111">`dotnet` 是命令列介面 (CLI) 工具鏈的通用驅動器。</span><span class="sxs-lookup"><span data-stu-id="d2249-111">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="d2249-112">它會自行叫用，提供簡短的使用方式指示。</span><span class="sxs-lookup"><span data-stu-id="d2249-112">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="d2249-113">每個特定功能都是當成命令來實作。</span><span class="sxs-lookup"><span data-stu-id="d2249-113">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="d2249-114">若要使用這個功能，請在 `dotnet` 之後指定命令 (例如 [`dotnet build`](dotnet-build.md))。</span><span class="sxs-lookup"><span data-stu-id="d2249-114">To use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="d2249-115">這個命令後面的所有引數都是它自己的引數。</span><span class="sxs-lookup"><span data-stu-id="d2249-115">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="d2249-116">`dotnet` 唯一自行作為命令使用的時機是執行[與 Framework 相依的應用程式](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d2249-116">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="d2249-117">在 `dotnet` 動詞之後指定應用程式 DLL，以執行應用程式 (例如，`dotnet myapp.dll`)。</span><span class="sxs-lookup"><span data-stu-id="d2249-117">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="d2249-118">選項</span><span class="sxs-lookup"><span data-stu-id="d2249-118">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d2249-119">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d2249-119">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="d2249-120">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="d2249-120">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="d2249-121">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="d2249-121">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d2249-122">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="d2249-122">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d2249-123">用來執行應用程式的已安裝 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="d2249-123">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d2249-124">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="d2249-124">Prints out a short help for the command.</span></span> <span data-ttu-id="d2249-125">如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。</span><span class="sxs-lookup"><span data-stu-id="d2249-125">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="d2249-126">印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d2249-126">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--list-runtimes`

<span data-ttu-id="d2249-127">顯示已安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="d2249-127">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="d2249-128">顯示已安裝的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="d2249-128">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="d2249-129">無任何候選共用架構上的向前復原。</span><span class="sxs-lookup"><span data-stu-id="d2249-129">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d2249-130">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="d2249-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2249-131">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="d2249-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d2249-132">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="d2249-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d2249-133">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="d2249-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d2249-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d2249-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="d2249-135">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="d2249-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="d2249-136">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="d2249-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d2249-137">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="d2249-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d2249-138">用來執行應用程式的已安裝 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="d2249-138">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d2249-139">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="d2249-139">Prints out a short help for the command.</span></span> <span data-ttu-id="d2249-140">如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。</span><span class="sxs-lookup"><span data-stu-id="d2249-140">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="d2249-141">印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d2249-141">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="d2249-142">無任何候選共用架構上的向前復原。</span><span class="sxs-lookup"><span data-stu-id="d2249-142">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d2249-143">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="d2249-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2249-144">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="d2249-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d2249-145">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="d2249-145">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d2249-146">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="d2249-146">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2249-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d2249-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="d2249-148">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="d2249-148">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d2249-149">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="d2249-149">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d2249-150">用來執行應用程式的已安裝 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="d2249-150">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d2249-151">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="d2249-151">Prints out a short help for the command.</span></span> <span data-ttu-id="d2249-152">如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。</span><span class="sxs-lookup"><span data-stu-id="d2249-152">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="d2249-153">印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d2249-153">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d2249-154">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="d2249-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2249-155">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="d2249-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d2249-156">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="d2249-156">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d2249-157">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="d2249-157">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="d2249-158">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="d2249-158">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="d2249-159">一般</span><span class="sxs-lookup"><span data-stu-id="d2249-159">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d2249-160">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d2249-160">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="d2249-161">命令</span><span class="sxs-lookup"><span data-stu-id="d2249-161">Command</span></span>                                       | <span data-ttu-id="d2249-162">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-162">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d2249-163">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d2249-163">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="d2249-164">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-164">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d2249-165">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="d2249-165">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="d2249-166">與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="d2249-166">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="d2249-167">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d2249-167">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="d2249-168">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="d2249-168">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="d2249-169">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d2249-169">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="d2249-170">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="d2249-170">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d2249-171">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d2249-171">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="d2249-172">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="d2249-172">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d2249-173">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d2249-173">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="d2249-174">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="d2249-174">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d2249-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2249-175">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="d2249-176">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="d2249-176">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d2249-177">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d2249-177">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="d2249-178">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d2249-178">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d2249-179">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d2249-179">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="d2249-180">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-180">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d2249-181">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d2249-181">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="d2249-182">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="d2249-182">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d2249-183">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d2249-183">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="d2249-184">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-184">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d2249-185">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d2249-185">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="d2249-186">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="d2249-186">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d2249-187">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d2249-187">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="d2249-188">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="d2249-188">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d2249-189">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d2249-189">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="d2249-190">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="d2249-190">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d2249-191">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d2249-191">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="d2249-192">命令</span><span class="sxs-lookup"><span data-stu-id="d2249-192">Command</span></span>                             | <span data-ttu-id="d2249-193">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-193">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d2249-194">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d2249-194">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d2249-195">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-195">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d2249-196">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d2249-196">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d2249-197">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="d2249-197">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d2249-198">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d2249-198">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="d2249-199">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="d2249-199">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d2249-200">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d2249-200">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d2249-201">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="d2249-201">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d2249-202">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d2249-202">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d2249-203">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="d2249-203">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d2249-204">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2249-204">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d2249-205">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="d2249-205">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d2249-206">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d2249-206">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d2249-207">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d2249-207">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d2249-208">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d2249-208">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d2249-209">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-209">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d2249-210">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d2249-210">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d2249-211">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="d2249-211">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d2249-212">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d2249-212">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d2249-213">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-213">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d2249-214">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d2249-214">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d2249-215">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="d2249-215">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d2249-216">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d2249-216">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="d2249-217">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="d2249-217">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d2249-218">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d2249-218">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d2249-219">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="d2249-219">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2249-220">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d2249-220">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="d2249-221">命令</span><span class="sxs-lookup"><span data-stu-id="d2249-221">Command</span></span>                             | <span data-ttu-id="d2249-222">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-222">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d2249-223">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d2249-223">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d2249-224">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-224">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d2249-225">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d2249-225">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d2249-226">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="d2249-226">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d2249-227">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d2249-227">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d2249-228">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="d2249-228">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d2249-229">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d2249-229">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d2249-230">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="d2249-230">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d2249-231">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2249-231">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d2249-232">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="d2249-232">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d2249-233">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d2249-233">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d2249-234">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d2249-234">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d2249-235">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d2249-235">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d2249-236">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-236">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d2249-237">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d2249-237">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d2249-238">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="d2249-238">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d2249-239">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d2249-239">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d2249-240">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2249-240">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d2249-241">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d2249-241">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d2249-242">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="d2249-242">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d2249-243">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d2249-243">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d2249-244">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="d2249-244">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="d2249-245">專案參考</span><span class="sxs-lookup"><span data-stu-id="d2249-245">Project references</span></span>

<span data-ttu-id="d2249-246">命令</span><span class="sxs-lookup"><span data-stu-id="d2249-246">Command</span></span> | <span data-ttu-id="d2249-247">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-247">Function</span></span>
--- | ---
[<span data-ttu-id="d2249-248">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="d2249-248">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="d2249-249">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="d2249-249">Adds a project reference.</span></span>
[<span data-ttu-id="d2249-250">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="d2249-250">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="d2249-251">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="d2249-251">Lists project references.</span></span>
[<span data-ttu-id="d2249-252">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="d2249-252">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="d2249-253">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="d2249-253">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="d2249-254">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="d2249-254">NuGet packages</span></span>

<span data-ttu-id="d2249-255">命令</span><span class="sxs-lookup"><span data-stu-id="d2249-255">Command</span></span> | <span data-ttu-id="d2249-256">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-256">Function</span></span>
--- | ---
[<span data-ttu-id="d2249-257">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="d2249-257">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="d2249-258">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d2249-258">Adds a NuGet package.</span></span>
[<span data-ttu-id="d2249-259">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="d2249-259">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="d2249-260">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d2249-260">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="d2249-261">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="d2249-261">NuGet commands</span></span>

<span data-ttu-id="d2249-262">命令</span><span class="sxs-lookup"><span data-stu-id="d2249-262">Command</span></span> | <span data-ttu-id="d2249-263">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-263">Function</span></span>
--- | ---
[<span data-ttu-id="d2249-264">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="d2249-264">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="d2249-265">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="d2249-265">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="d2249-266">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="d2249-266">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="d2249-267">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="d2249-267">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="d2249-268">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="d2249-268">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="d2249-269">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="d2249-269">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="d2249-270">通用工具命令</span><span class="sxs-lookup"><span data-stu-id="d2249-270">Global Tools commands</span></span>

<span data-ttu-id="d2249-271">[.NET Core 通用工具](global-tools.md)將從 .NET Core SDK 2.1.300 開始提供使用：</span><span class="sxs-lookup"><span data-stu-id="d2249-271">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="d2249-272">命令</span><span class="sxs-lookup"><span data-stu-id="d2249-272">Command</span></span> | <span data-ttu-id="d2249-273">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-273">Function</span></span>
--- | ---
[<span data-ttu-id="d2249-274">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="d2249-274">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="d2249-275">在您的電腦上安裝通用工具。</span><span class="sxs-lookup"><span data-stu-id="d2249-275">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="d2249-276">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="d2249-276">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="d2249-277">列出在您電腦上的預設目錄或在指定路徑中目前已安裝的所有通用工具。</span><span class="sxs-lookup"><span data-stu-id="d2249-277">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="d2249-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="d2249-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="d2249-279">將通用工具從您的電腦解除安裝。</span><span class="sxs-lookup"><span data-stu-id="d2249-279">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="d2249-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="d2249-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="d2249-281">更新您電腦上的通用工具。</span><span class="sxs-lookup"><span data-stu-id="d2249-281">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="d2249-282">其他工具</span><span class="sxs-lookup"><span data-stu-id="d2249-282">Additional tools</span></span>

<span data-ttu-id="d2249-283">從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="d2249-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="d2249-284">這些工具包括：</span><span class="sxs-lookup"><span data-stu-id="d2249-284">These tools include:</span></span>

| <span data-ttu-id="d2249-285">工具</span><span class="sxs-lookup"><span data-stu-id="d2249-285">Tool</span></span>                                              | <span data-ttu-id="d2249-286">功能</span><span class="sxs-lookup"><span data-stu-id="d2249-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="d2249-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="d2249-287">dev-certs</span></span>                                         | <span data-ttu-id="d2249-288">建立及管理開發憑證。</span><span class="sxs-lookup"><span data-stu-id="d2249-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="d2249-289">ef</span><span class="sxs-lookup"><span data-stu-id="d2249-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="d2249-290">Entity Framework Core 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="d2249-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="d2249-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="d2249-291">sql-cache</span></span>                                         | <span data-ttu-id="d2249-292">SQL Server 快取命令列工具。</span><span class="sxs-lookup"><span data-stu-id="d2249-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="d2249-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="d2249-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="d2249-294">管理開發使用者祕密。</span><span class="sxs-lookup"><span data-stu-id="d2249-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="d2249-295">watch</span><span class="sxs-lookup"><span data-stu-id="d2249-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="d2249-296">啟動會在檔案變更時執行命令的檔案監看員。</span><span class="sxs-lookup"><span data-stu-id="d2249-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="d2249-297">如需每個工具的詳細資訊，請執行 `dotnet <tool-name> --help`。</span><span class="sxs-lookup"><span data-stu-id="d2249-297">For more information about each tool, execute `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="d2249-298">範例</span><span class="sxs-lookup"><span data-stu-id="d2249-298">Examples</span></span>

<span data-ttu-id="d2249-299">建立新的 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="d2249-299">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="d2249-300">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="d2249-300">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d2249-301">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="d2249-301">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="d2249-302">執行名稱為 `myapp.dll` 的與 Framework 相依的應用程式：</span><span class="sxs-lookup"><span data-stu-id="d2249-302">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="d2249-303">環境變數</span><span class="sxs-lookup"><span data-stu-id="d2249-303">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d2249-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d2249-304">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="d2249-305">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="d2249-305">The primary package cache.</span></span> <span data-ttu-id="d2249-306">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="d2249-306">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d2249-307">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="d2249-307">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d2249-308">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="d2249-308">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d2249-309">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="d2249-309">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d2249-310">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="d2249-310">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d2249-311">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="d2249-311">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="d2249-312">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="d2249-312">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="d2249-313">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d2249-313">If not set, it defaults to `true`.</span></span> <span data-ttu-id="d2249-314">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="d2249-314">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="d2249-315">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="d2249-315">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="d2249-316">停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="d2249-316">Disables minor version roll forward.</span></span> <span data-ttu-id="d2249-317">如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="d2249-317">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d2249-318">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d2249-318">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="d2249-319">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="d2249-319">The primary package cache.</span></span> <span data-ttu-id="d2249-320">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="d2249-320">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d2249-321">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="d2249-321">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d2249-322">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="d2249-322">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d2249-323">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="d2249-323">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d2249-324">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="d2249-324">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d2249-325">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="d2249-325">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="d2249-326">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="d2249-326">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="d2249-327">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d2249-327">If not set, it defaults to `true`.</span></span> <span data-ttu-id="d2249-328">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="d2249-328">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="d2249-329">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="d2249-329">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2249-330">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d2249-330">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="d2249-331">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="d2249-331">The primary package cache.</span></span> <span data-ttu-id="d2249-332">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="d2249-332">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d2249-333">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="d2249-333">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d2249-334">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="d2249-334">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d2249-335">設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。</span><span class="sxs-lookup"><span data-stu-id="d2249-335">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d2249-336">否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="d2249-336">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d2249-337">如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。</span><span class="sxs-lookup"><span data-stu-id="d2249-337">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
