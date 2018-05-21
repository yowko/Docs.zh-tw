---
title: dotnet 命令 - .NET Core CLI
description: 了解 dotnet 命令 (.NET Core CLI 工具的通用驅動器) 和其用法。
author: mairaw
ms.author: mairaw
ms.date: 03/20/2018
ms.openlocfilehash: c56ed032ccef6c6fd19a13214b04b384ffff28d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="eb180-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="eb180-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="eb180-104">名稱</span><span class="sxs-lookup"><span data-stu-id="eb180-104">Name</span></span>

<span data-ttu-id="eb180-105">`dotnet` - 用於執行命令列命令的一般驅動器。</span><span class="sxs-lookup"><span data-stu-id="eb180-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="eb180-106">概要</span><span class="sxs-lookup"><span data-stu-id="eb180-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="eb180-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="eb180-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="eb180-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="eb180-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="eb180-109">描述</span><span class="sxs-lookup"><span data-stu-id="eb180-109">Description</span></span>

<span data-ttu-id="eb180-110">`dotnet` 是命令列介面 (CLI) 工具鏈的通用驅動器。</span><span class="sxs-lookup"><span data-stu-id="eb180-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="eb180-111">它會自行叫用，提供簡短的使用方式指示。</span><span class="sxs-lookup"><span data-stu-id="eb180-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="eb180-112">每個特定功能都是當成命令來實作。</span><span class="sxs-lookup"><span data-stu-id="eb180-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="eb180-113">若要使用這個功能，請在 `dotnet` 之後指定這個命令 (例如 [`dotnet build`](dotnet-build.md))。</span><span class="sxs-lookup"><span data-stu-id="eb180-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="eb180-114">這個命令後面的所有引數都是它自己的引數。</span><span class="sxs-lookup"><span data-stu-id="eb180-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="eb180-115">`dotnet` 唯一自行作為命令使用的時機是執行[與 Framework 相依的應用程式](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="eb180-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="eb180-116">在 `dotnet` 動詞之後指定應用程式 DLL，以執行應用程式 (例如，`dotnet myapp.dll`)。</span><span class="sxs-lookup"><span data-stu-id="eb180-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="eb180-117">選項</span><span class="sxs-lookup"><span data-stu-id="eb180-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="eb180-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="eb180-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="eb180-119">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="eb180-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="eb180-120">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="eb180-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="eb180-121">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="eb180-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="eb180-122">用來執行應用程式的已安裝 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="eb180-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="eb180-123">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="eb180-123">Prints out a short help for the command.</span></span> <span data-ttu-id="eb180-124">如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。</span><span class="sxs-lookup"><span data-stu-id="eb180-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="eb180-125">印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="eb180-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="eb180-126">無任何候選共用架構上的向前復原。</span><span class="sxs-lookup"><span data-stu-id="eb180-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="eb180-127">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="eb180-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="eb180-128">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="eb180-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="eb180-129">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="eb180-129">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="eb180-130">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="eb180-130">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="eb180-131">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="eb180-131">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="eb180-132">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="eb180-132">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="eb180-133">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="eb180-133">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="eb180-134">用來執行應用程式的已安裝 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="eb180-134">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="eb180-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="eb180-135">Prints out a short help for the command.</span></span> <span data-ttu-id="eb180-136">如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。</span><span class="sxs-lookup"><span data-stu-id="eb180-136">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="eb180-137">印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="eb180-137">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="eb180-138">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="eb180-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="eb180-139">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="eb180-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="eb180-140">不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="eb180-140">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="eb180-141">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="eb180-141">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="eb180-142">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="eb180-142">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="eb180-143">一般</span><span class="sxs-lookup"><span data-stu-id="eb180-143">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="eb180-144">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="eb180-144">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="eb180-145">命令</span><span class="sxs-lookup"><span data-stu-id="eb180-145">Command</span></span>                             | <span data-ttu-id="eb180-146">功能</span><span class="sxs-lookup"><span data-stu-id="eb180-146">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="eb180-147">dotnet build</span><span class="sxs-lookup"><span data-stu-id="eb180-147">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="eb180-148">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="eb180-148">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="eb180-149">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="eb180-149">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="eb180-150">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="eb180-150">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="eb180-151">dotnet help</span><span class="sxs-lookup"><span data-stu-id="eb180-151">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="eb180-152">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="eb180-152">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="eb180-153">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="eb180-153">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="eb180-154">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="eb180-154">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="eb180-155">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="eb180-155">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="eb180-156">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="eb180-156">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="eb180-157">dotnet new</span><span class="sxs-lookup"><span data-stu-id="eb180-157">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="eb180-158">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="eb180-158">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="eb180-159">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="eb180-159">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="eb180-160">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="eb180-160">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="eb180-161">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="eb180-161">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="eb180-162">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="eb180-162">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="eb180-163">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="eb180-163">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="eb180-164">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="eb180-164">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="eb180-165">dotnet run</span><span class="sxs-lookup"><span data-stu-id="eb180-165">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="eb180-166">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="eb180-166">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="eb180-167">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="eb180-167">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="eb180-168">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="eb180-168">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="eb180-169">dotnet store</span><span class="sxs-lookup"><span data-stu-id="eb180-169">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="eb180-170">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="eb180-170">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="eb180-171">dotnet test</span><span class="sxs-lookup"><span data-stu-id="eb180-171">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="eb180-172">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="eb180-172">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="eb180-173">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="eb180-173">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="eb180-174">命令</span><span class="sxs-lookup"><span data-stu-id="eb180-174">Command</span></span>                             | <span data-ttu-id="eb180-175">功能</span><span class="sxs-lookup"><span data-stu-id="eb180-175">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="eb180-176">dotnet build</span><span class="sxs-lookup"><span data-stu-id="eb180-176">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="eb180-177">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="eb180-177">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="eb180-178">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="eb180-178">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="eb180-179">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="eb180-179">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="eb180-180">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="eb180-180">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="eb180-181">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="eb180-181">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="eb180-182">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="eb180-182">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="eb180-183">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="eb180-183">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="eb180-184">dotnet new</span><span class="sxs-lookup"><span data-stu-id="eb180-184">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="eb180-185">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="eb180-185">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="eb180-186">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="eb180-186">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="eb180-187">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="eb180-187">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="eb180-188">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="eb180-188">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="eb180-189">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="eb180-189">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="eb180-190">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="eb180-190">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="eb180-191">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="eb180-191">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="eb180-192">dotnet run</span><span class="sxs-lookup"><span data-stu-id="eb180-192">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="eb180-193">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="eb180-193">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="eb180-194">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="eb180-194">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="eb180-195">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="eb180-195">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="eb180-196">dotnet test</span><span class="sxs-lookup"><span data-stu-id="eb180-196">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="eb180-197">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="eb180-197">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="eb180-198">專案參考</span><span class="sxs-lookup"><span data-stu-id="eb180-198">Project references</span></span>

<span data-ttu-id="eb180-199">命令</span><span class="sxs-lookup"><span data-stu-id="eb180-199">Command</span></span> | <span data-ttu-id="eb180-200">功能</span><span class="sxs-lookup"><span data-stu-id="eb180-200">Function</span></span>
--- | ---
[<span data-ttu-id="eb180-201">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="eb180-201">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="eb180-202">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="eb180-202">Add a project reference.</span></span>
[<span data-ttu-id="eb180-203">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="eb180-203">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="eb180-204">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="eb180-204">List project references.</span></span>
[<span data-ttu-id="eb180-205">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="eb180-205">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="eb180-206">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="eb180-206">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="eb180-207">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="eb180-207">NuGet packages</span></span>

<span data-ttu-id="eb180-208">命令</span><span class="sxs-lookup"><span data-stu-id="eb180-208">Command</span></span> | <span data-ttu-id="eb180-209">功能</span><span class="sxs-lookup"><span data-stu-id="eb180-209">Function</span></span>
--- | ---
[<span data-ttu-id="eb180-210">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="eb180-210">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="eb180-211">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="eb180-211">Add a NuGet package.</span></span>
[<span data-ttu-id="eb180-212">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="eb180-212">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="eb180-213">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="eb180-213">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="eb180-214">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="eb180-214">NuGet commands</span></span>

<span data-ttu-id="eb180-215">命令</span><span class="sxs-lookup"><span data-stu-id="eb180-215">Command</span></span> | <span data-ttu-id="eb180-216">功能</span><span class="sxs-lookup"><span data-stu-id="eb180-216">Function</span></span>
--- | ---
[<span data-ttu-id="eb180-217">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="eb180-217">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="eb180-218">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="eb180-218">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="eb180-219">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="eb180-219">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="eb180-220">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="eb180-220">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="eb180-221">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="eb180-221">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="eb180-222">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="eb180-222">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="eb180-223">範例</span><span class="sxs-lookup"><span data-stu-id="eb180-223">Examples</span></span>

<span data-ttu-id="eb180-224">初始化可編譯和執行的範例 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="eb180-224">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="eb180-225">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="eb180-225">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="eb180-226">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="eb180-226">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="eb180-227">執行名稱為 `myapp.dll` 的與 Framework 相依的應用程式：</span><span class="sxs-lookup"><span data-stu-id="eb180-227">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="eb180-228">環境變數</span><span class="sxs-lookup"><span data-stu-id="eb180-228">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="eb180-229">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="eb180-229">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="eb180-230">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="eb180-230">The primary package cache.</span></span> <span data-ttu-id="eb180-231">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="eb180-231">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="eb180-232">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="eb180-232">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="eb180-233">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="eb180-233">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="eb180-234">設定為 `true` 取消遙測功能 (可接受的值為 `true`、`1` 或 `yes`)；否則，設定為 `false` 加入遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="eb180-234">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="eb180-235">如果未設定，預設值為 `false`，且遙測功能為使用中。</span><span class="sxs-lookup"><span data-stu-id="eb180-235">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="eb180-236">指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。</span><span class="sxs-lookup"><span data-stu-id="eb180-236">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="eb180-237">如果未設定，則預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="eb180-237">If not set, it defaults to `true`.</span></span> <span data-ttu-id="eb180-238">設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。</span><span class="sxs-lookup"><span data-stu-id="eb180-238">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="eb180-239">如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。</span><span class="sxs-lookup"><span data-stu-id="eb180-239">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="eb180-240">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="eb180-240">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="eb180-241">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="eb180-241">The primary package cache.</span></span> <span data-ttu-id="eb180-242">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="eb180-242">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="eb180-243">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="eb180-243">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="eb180-244">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="eb180-244">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="eb180-245">設定為 `true` 取消遙測功能 (可接受的值為 `true`、`1` 或 `yes`)；否則，設定為 `false` 加入遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="eb180-245">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="eb180-246">如果未設定，預設值為 `false`，且遙測功能為使用中。</span><span class="sxs-lookup"><span data-stu-id="eb180-246">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
