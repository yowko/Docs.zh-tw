---
title: dotnet run 命令
description: dotnet run 命令提供方便的選項，以透過原始程式碼來執行應用程式。
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734111"
---
# <a name="dotnet-run"></a><span data-ttu-id="5fb62-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5fb62-103">dotnet run</span></span>

<span data-ttu-id="5fb62-104">**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="5fb62-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5fb62-105">Name</span><span class="sxs-lookup"><span data-stu-id="5fb62-105">Name</span></span>

<span data-ttu-id="5fb62-106">`dotnet run` - 執行原始程式碼，而不需要有任何明確的編譯或啟動命令。</span><span class="sxs-lookup"><span data-stu-id="5fb62-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5fb62-107">概要</span><span class="sxs-lookup"><span data-stu-id="5fb62-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="5fb62-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5fb62-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5fb62-109">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5fb62-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5fb62-110">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5fb62-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5fb62-111">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5fb62-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="5fb62-112">描述</span><span class="sxs-lookup"><span data-stu-id="5fb62-112">Description</span></span>

<span data-ttu-id="5fb62-113">`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="5fb62-114">可用於在命令列中快速進行反覆開發。</span><span class="sxs-lookup"><span data-stu-id="5fb62-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="5fb62-115">此命令仰賴 [`dotnet build`](dotnet-build.md) 命令來建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="5fb62-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="5fb62-116">建置的任何需求 (例如必須先還原專案) 也同樣適用於 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="5fb62-117">輸出檔會寫入至預設位置，也就是 `bin/<configuration>/<target>`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="5fb62-118">例如，如果您有 `netcoreapp2.1` 應用程式並執行 `dotnet run`，輸出將會放置在 `bin/Debug/netcoreapp2.1` 中。</span><span class="sxs-lookup"><span data-stu-id="5fb62-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="5fb62-119">而且會視需要覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="5fb62-119">Files are overwritten as needed.</span></span> <span data-ttu-id="5fb62-120">暫存檔案會放置在 `obj` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="5fb62-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="5fb62-121">如果專案指定多個架構，執行 `dotnet run` 會導致錯誤，除非使用 `-f|--framework <FRAMEWORK>` 選項來指定架構。</span><span class="sxs-lookup"><span data-stu-id="5fb62-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="5fb62-122">`dotnet run` 命令用於專案內容中，而非已建置的組件。</span><span class="sxs-lookup"><span data-stu-id="5fb62-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="5fb62-123">如果您改為嘗試執行與 Framework 相依的應用程式 DLL，您必須不透過命令使用 [dotnet](dotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="5fb62-124">例如，若要執行 `myapp.dll`，使用︰</span><span class="sxs-lookup"><span data-stu-id="5fb62-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="5fb62-125">如需 `dotnet` 驅動程式的詳細資訊，請參閱 [.NET Core 命令列工具 (CLI)](index.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="5fb62-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="5fb62-126">為了執行應用程式，`dotnet run` 命令會從 NuGet 快取解析共用執行階段之外的應用程式相依性。</span><span class="sxs-lookup"><span data-stu-id="5fb62-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="5fb62-127">因為它會使用快取相依性，不建議您在生產環境中使用 `dotnet run` 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="5fb62-128">相反地，使用 [`dotnet publish`](dotnet-publish.md) 命令[建立部署](../deploying/index.md)，並部署已發佈的輸出。</span><span class="sxs-lookup"><span data-stu-id="5fb62-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="5fb62-129">選項</span><span class="sxs-lookup"><span data-stu-id="5fb62-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="5fb62-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5fb62-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="5fb62-131">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="5fb62-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="5fb62-132">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5fb62-133">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="5fb62-133">Defines the build configuration.</span></span> <span data-ttu-id="5fb62-134">大部分專案的預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5fb62-135">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5fb62-136">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="5fb62-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="5fb62-137">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5fb62-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5fb62-138">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fb62-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="5fb62-139">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5fb62-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="5fb62-140">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="5fb62-141">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="5fb62-142">啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="5fb62-143">如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="5fb62-144">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="5fb62-144">Doesn't build the project before running.</span></span> <span data-ttu-id="5fb62-145">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="5fb62-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="5fb62-146">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="5fb62-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="5fb62-147">不會嘗試使用 *launchSettings.json* 來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="5fb62-148">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="5fb62-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="5fb62-149">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="5fb62-150">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="5fb62-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="5fb62-151">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="5fb62-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="5fb62-152">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5fb62-153">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="5fb62-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5fb62-154">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5fb62-155">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5fb62-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="5fb62-156">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="5fb62-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="5fb62-157">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5fb62-158">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="5fb62-158">Defines the build configuration.</span></span> <span data-ttu-id="5fb62-159">大部分專案的預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5fb62-160">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5fb62-161">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="5fb62-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="5fb62-162">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5fb62-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5fb62-163">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fb62-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="5fb62-164">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5fb62-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="5fb62-165">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="5fb62-166">啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="5fb62-167">如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="5fb62-168">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="5fb62-168">Doesn't build the project before running.</span></span> <span data-ttu-id="5fb62-169">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="5fb62-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="5fb62-170">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="5fb62-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="5fb62-171">不會嘗試使用 *launchSettings.json* 來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="5fb62-172">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="5fb62-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="5fb62-173">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="5fb62-174">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="5fb62-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="5fb62-175">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="5fb62-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="5fb62-176">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5fb62-177">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="5fb62-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5fb62-178">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5fb62-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5fb62-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="5fb62-180">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="5fb62-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="5fb62-181">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5fb62-182">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="5fb62-182">Defines the build configuration.</span></span> <span data-ttu-id="5fb62-183">大部分專案的預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5fb62-184">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5fb62-185">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="5fb62-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="5fb62-186">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5fb62-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5fb62-187">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fb62-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="5fb62-188">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5fb62-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="5fb62-189">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="5fb62-190">啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="5fb62-191">如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="5fb62-192">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="5fb62-192">Doesn't build the project before running.</span></span> <span data-ttu-id="5fb62-193">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="5fb62-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="5fb62-194">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="5fb62-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="5fb62-195">不會嘗試使用 *launchSettings.json* 來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="5fb62-196">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="5fb62-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="5fb62-197">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="5fb62-198">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="5fb62-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="5fb62-199">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="5fb62-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="5fb62-200">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5fb62-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5fb62-201">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5fb62-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="5fb62-202">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="5fb62-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="5fb62-203">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5fb62-204">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="5fb62-204">Defines the build configuration.</span></span> <span data-ttu-id="5fb62-205">大部分專案的預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="5fb62-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5fb62-206">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fb62-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5fb62-207">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="5fb62-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="5fb62-208">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5fb62-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="5fb62-209">指定專案檔的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="5fb62-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="5fb62-210">（請參閱附注）。如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="5fb62-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb62-211">透過 `-p|--project` 選項使用專案檔的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="5fb62-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="5fb62-212">CLI 中出現迴歸會無法提供具有 NET Core SDK 1.x 的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="5fb62-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="5fb62-213">如需此問題的詳細資訊，請參閱 [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992) (dotnet run -p，無法啟動專案 (dotnet/cli #5992))。</span><span class="sxs-lookup"><span data-stu-id="5fb62-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="5fb62-214">範例</span><span class="sxs-lookup"><span data-stu-id="5fb62-214">Examples</span></span>

<span data-ttu-id="5fb62-215">執行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="5fb62-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="5fb62-216">執行指定的專案：</span><span class="sxs-lookup"><span data-stu-id="5fb62-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="5fb62-217">執行目前目錄中的專案 (因為已使用空白的 `--` 選項，所以這個範例中的 `--help` 引數會傳遞給應用程式)：</span><span class="sxs-lookup"><span data-stu-id="5fb62-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="5fb62-218">還原相依性及目前目錄中專案的工具，只會顯示最基本的輸出，然後執行專案：(.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="5fb62-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
