---
title: "dotnet 命令 - .NET Core CLI"
description: "了解 dotnet 命令 (.NET Core CLI 工具的通用驅動器) 和其用法。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: fa2e5ecbf41dc2a8cd90aabc6f7291db597e657e
ms.openlocfilehash: 4c1c0e4ed1b1222abbcd104b2c10a44b1b99be8d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/17/2017

---
# <a name="dotnet-command"></a><span data-ttu-id="c60be-103">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="c60be-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c60be-104">名稱</span><span class="sxs-lookup"><span data-stu-id="c60be-104">Name</span></span>

<span data-ttu-id="c60be-105">`dotnet` - 用於執行命令列命令的一般驅動器。</span><span class="sxs-lookup"><span data-stu-id="c60be-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c60be-106">概要</span><span class="sxs-lookup"><span data-stu-id="c60be-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c60be-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c60be-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c60be-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c60be-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="c60be-109">說明</span><span class="sxs-lookup"><span data-stu-id="c60be-109">Description</span></span>

<span data-ttu-id="c60be-110">`dotnet` 是命令列介面 (CLI) 工具鏈的通用驅動器。</span><span class="sxs-lookup"><span data-stu-id="c60be-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="c60be-111">它會自行叫用，提供簡短的使用方式指示。</span><span class="sxs-lookup"><span data-stu-id="c60be-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="c60be-112">每個特定功能都是當成命令來實作。</span><span class="sxs-lookup"><span data-stu-id="c60be-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="c60be-113">若要使用這個功能，請在 `dotnet` 之後指定這個命令 (例如 [`dotnet build`](dotnet-build.md))。</span><span class="sxs-lookup"><span data-stu-id="c60be-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="c60be-114">這個命令後面的所有引數都是它自己的引數。</span><span class="sxs-lookup"><span data-stu-id="c60be-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="c60be-115">`dotnet` 唯一自行作為命令使用的時機是執行[與 Framework 相依的應用程式](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c60be-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="c60be-116">在 `dotnet` 動詞之後指定應用程式 DLL，以執行應用程式 (例如，`dotnet myapp.dll`)。</span><span class="sxs-lookup"><span data-stu-id="c60be-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="c60be-117">選項</span><span class="sxs-lookup"><span data-stu-id="c60be-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c60be-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c60be-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additionaldeps <PATH>`

<span data-ttu-id="c60be-119">其他 *deps.json* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c60be-119">Path to additonal *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="c60be-120">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="c60be-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="c60be-121">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="c60be-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="c60be-122">用來執行應用程式的已安裝 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="c60be-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="c60be-123">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c60be-123">Prints out a short help for the command.</span></span> <span data-ttu-id="c60be-124">如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。</span><span class="sxs-lookup"><span data-stu-id="c60be-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="c60be-125">印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="c60be-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="c60be-126">無任何候選共用架構上的向前復原。</span><span class="sxs-lookup"><span data-stu-id="c60be-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="c60be-127">啟用詳細資訊輸出。</span><span class="sxs-lookup"><span data-stu-id="c60be-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="c60be-128">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c60be-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c60be-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c60be-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="c60be-130">包含探查原則和要探查之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="c60be-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="c60be-131">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="c60be-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="c60be-132">用來執行應用程式的已安裝 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="c60be-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="c60be-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c60be-133">Prints out a short help for the command.</span></span> <span data-ttu-id="c60be-134">如果與 `dotnet` 搭配使用，則也會列印一份可用的命令清單。</span><span class="sxs-lookup"><span data-stu-id="c60be-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="c60be-135">印出有關 CLI 工具和環境的詳細資訊，例如目前的作業系統、版本的認可 SHA，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="c60be-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="c60be-136">啟用詳細資訊輸出。</span><span class="sxs-lookup"><span data-stu-id="c60be-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="c60be-137">印出使用中的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c60be-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="c60be-138">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="c60be-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="c60be-139">一般</span><span class="sxs-lookup"><span data-stu-id="c60be-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c60be-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c60be-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="c60be-141">命令</span><span class="sxs-lookup"><span data-stu-id="c60be-141">Command</span></span>                             | <span data-ttu-id="c60be-142">函式</span><span class="sxs-lookup"><span data-stu-id="c60be-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="c60be-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c60be-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="c60be-144">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c60be-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="c60be-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="c60be-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="c60be-146">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="c60be-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="c60be-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="c60be-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="c60be-148">顯示命令更詳細的線上文件。</span><span class="sxs-lookup"><span data-stu-id="c60be-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="c60be-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="c60be-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="c60be-150">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="c60be-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="c60be-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="c60be-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="c60be-152">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="c60be-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="c60be-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c60be-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="c60be-154">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="c60be-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="c60be-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="c60be-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="c60be-156">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c60be-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="c60be-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="c60be-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="c60be-158">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="c60be-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="c60be-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="c60be-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="c60be-160">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="c60be-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="c60be-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="c60be-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="c60be-162">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c60be-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="c60be-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="c60be-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="c60be-164">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="c60be-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="c60be-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="c60be-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="c60be-166">在執行階段套件存放區中儲存組件。</span><span class="sxs-lookup"><span data-stu-id="c60be-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="c60be-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="c60be-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="c60be-168">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="c60be-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c60be-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c60be-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="c60be-170">命令</span><span class="sxs-lookup"><span data-stu-id="c60be-170">Command</span></span>                             | <span data-ttu-id="c60be-171">函式</span><span class="sxs-lookup"><span data-stu-id="c60be-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="c60be-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c60be-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="c60be-173">建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c60be-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="c60be-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="c60be-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="c60be-175">清除組建輸出。</span><span class="sxs-lookup"><span data-stu-id="c60be-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="c60be-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="c60be-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="c60be-177">將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。</span><span class="sxs-lookup"><span data-stu-id="c60be-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="c60be-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="c60be-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="c60be-179">提供對 MSBuild 命令列的存取。</span><span class="sxs-lookup"><span data-stu-id="c60be-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="c60be-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c60be-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="c60be-181">初始化指定範本的 C# 或 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="c60be-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="c60be-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="c60be-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="c60be-183">建立您程式碼的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c60be-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="c60be-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="c60be-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="c60be-185">發行 .NET 與 Framework 相依的應用程式或獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="c60be-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="c60be-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="c60be-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="c60be-187">還原所指定應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="c60be-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="c60be-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="c60be-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="c60be-189">從原始檔執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c60be-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="c60be-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="c60be-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="c60be-191">要在方案檔中新增、移除及列出專案的選項。</span><span class="sxs-lookup"><span data-stu-id="c60be-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="c60be-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="c60be-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="c60be-193">使用測試執行器執行測試。</span><span class="sxs-lookup"><span data-stu-id="c60be-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="c60be-194">專案參考</span><span class="sxs-lookup"><span data-stu-id="c60be-194">Project references</span></span>

<span data-ttu-id="c60be-195">命令</span><span class="sxs-lookup"><span data-stu-id="c60be-195">Command</span></span> | <span data-ttu-id="c60be-196">函式</span><span class="sxs-lookup"><span data-stu-id="c60be-196">Function</span></span>
--- | ---
[<span data-ttu-id="c60be-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="c60be-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="c60be-198">新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="c60be-198">Add a project reference.</span></span>
[<span data-ttu-id="c60be-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="c60be-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="c60be-200">列出專案參考。</span><span class="sxs-lookup"><span data-stu-id="c60be-200">List project references.</span></span>
[<span data-ttu-id="c60be-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="c60be-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="c60be-202">移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="c60be-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="c60be-203">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="c60be-203">NuGet packages</span></span>

<span data-ttu-id="c60be-204">命令</span><span class="sxs-lookup"><span data-stu-id="c60be-204">Command</span></span> | <span data-ttu-id="c60be-205">函式</span><span class="sxs-lookup"><span data-stu-id="c60be-205">Function</span></span>
--- | ---
[<span data-ttu-id="c60be-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="c60be-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="c60be-207">新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c60be-207">Add a NuGet package.</span></span>
[<span data-ttu-id="c60be-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="c60be-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="c60be-209">移除 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c60be-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="c60be-210">NuGet 命令</span><span class="sxs-lookup"><span data-stu-id="c60be-210">NuGet commands</span></span>

<span data-ttu-id="c60be-211">命令</span><span class="sxs-lookup"><span data-stu-id="c60be-211">Command</span></span> | <span data-ttu-id="c60be-212">函式</span><span class="sxs-lookup"><span data-stu-id="c60be-212">Function</span></span>
--- | ---
[<span data-ttu-id="c60be-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="c60be-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="c60be-214">從伺服器刪除或取消列出套件。</span><span class="sxs-lookup"><span data-stu-id="c60be-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="c60be-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="c60be-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="c60be-216">清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。</span><span class="sxs-lookup"><span data-stu-id="c60be-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="c60be-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="c60be-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="c60be-218">將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="c60be-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="c60be-219">範例</span><span class="sxs-lookup"><span data-stu-id="c60be-219">Examples</span></span>

<span data-ttu-id="c60be-220">初始化可編譯和執行的範例 .NET Core 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="c60be-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="c60be-221">還原所指定應用程式的相依性：</span><span class="sxs-lookup"><span data-stu-id="c60be-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

<span data-ttu-id="c60be-222">建置所指定目錄中的專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="c60be-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="c60be-223">執行名稱為 `myapp.dll` 的與 Framework 相依的應用程式：</span><span class="sxs-lookup"><span data-stu-id="c60be-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="c60be-224">環境變數</span><span class="sxs-lookup"><span data-stu-id="c60be-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="c60be-225">主要套件快取。</span><span class="sxs-lookup"><span data-stu-id="c60be-225">The primary package cache.</span></span> <span data-ttu-id="c60be-226">如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。</span><span class="sxs-lookup"><span data-stu-id="c60be-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="c60be-227">指定載入執行階段時，共用主機所使用的服務索引位置。</span><span class="sxs-lookup"><span data-stu-id="c60be-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="c60be-228">指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="c60be-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="c60be-229">設定為 `true` 取消遙測功能 (可接受的值為 `true`、`1` 或 `yes`)；否則，設定為 `false` 加入遙測功能 (可接受的值為 `false`、`0` 或 `no`)。</span><span class="sxs-lookup"><span data-stu-id="c60be-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="c60be-230">如果未設定，預設值為 `false`，且遙測功能為使用中。</span><span class="sxs-lookup"><span data-stu-id="c60be-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

