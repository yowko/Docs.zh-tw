---
title: dotnet run 命令 - .NET Core CLI
description: dotnet run 命令提供方便的選項，以透過原始程式碼來執行應用程式。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f560e6f795f00488818647a4b5c711dcf9d59dcd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45687643"
---
# <a name="dotnet-run"></a><span data-ttu-id="78821-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="78821-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="78821-104">名稱</span><span class="sxs-lookup"><span data-stu-id="78821-104">Name</span></span>

<span data-ttu-id="78821-105">`dotnet run` - 執行原始程式碼，而不需要有任何明確的編譯或啟動命令。</span><span class="sxs-lookup"><span data-stu-id="78821-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="78821-106">概要</span><span class="sxs-lookup"><span data-stu-id="78821-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78821-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78821-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78821-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78821-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78821-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78821-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="78821-110">描述</span><span class="sxs-lookup"><span data-stu-id="78821-110">Description</span></span>

<span data-ttu-id="78821-111">`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="78821-112">可用於在命令列中快速進行反覆開發。</span><span class="sxs-lookup"><span data-stu-id="78821-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="78821-113">此命令仰賴 [`dotnet build`](dotnet-build.md) 命令來建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="78821-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="78821-114">建置的任何需求 (例如必須先還原專案) 也同樣適用於 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="78821-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="78821-115">輸出檔會寫入至預設位置，也就是 `bin/<configuration>/<target>`。</span><span class="sxs-lookup"><span data-stu-id="78821-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="78821-116">例如，如果您有 `netcoreapp2.1` 應用程式並執行 `dotnet run`，輸出將會放置在 `bin/Debug/netcoreapp2.1` 中。</span><span class="sxs-lookup"><span data-stu-id="78821-116">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="78821-117">而且會視需要覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="78821-117">Files are overwritten as needed.</span></span> <span data-ttu-id="78821-118">暫存檔案會放置在 `obj` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="78821-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="78821-119">如果專案指定多個架構，執行 `dotnet run` 會導致錯誤，除非使用 `-f|--framework <FRAMEWORK>` 選項來指定架構。</span><span class="sxs-lookup"><span data-stu-id="78821-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="78821-120">`dotnet run` 命令用於專案內容中，而非已建置的組件。</span><span class="sxs-lookup"><span data-stu-id="78821-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="78821-121">如果您改為嘗試執行與 Framework 相依的應用程式 DLL，您必須不透過命令使用 [dotnet](dotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="78821-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="78821-122">例如，若要執行 `myapp.dll`，使用︰</span><span class="sxs-lookup"><span data-stu-id="78821-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="78821-123">如需 `dotnet` 驅動程式的詳細資訊，請參閱 [.NET Core 命令列工具 (CLI)](index.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="78821-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="78821-124">為了執行應用程式，`dotnet run` 命令會從 NuGet 快取解析共用執行階段之外的應用程式相依性。</span><span class="sxs-lookup"><span data-stu-id="78821-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="78821-125">因為它會使用快取相依性，不建議您在生產環境中使用 `dotnet run` 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="78821-126">相反地，使用 [`dotnet publish`](dotnet-publish.md) 命令[建立部署](../deploying/index.md)，並部署已發佈的輸出。</span><span class="sxs-lookup"><span data-stu-id="78821-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="78821-127">選項</span><span class="sxs-lookup"><span data-stu-id="78821-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78821-128">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78821-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="78821-129">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="78821-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="78821-130">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="78821-131">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="78821-131">Defines the build configuration.</span></span> <span data-ttu-id="78821-132">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="78821-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="78821-133">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="78821-134">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="78821-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="78821-135">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="78821-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="78821-136">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="78821-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="78821-137">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="78821-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="78821-138">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="78821-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="78821-139">啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。</span><span class="sxs-lookup"><span data-stu-id="78821-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="78821-140">如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="78821-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="78821-141">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="78821-141">Doesn't build the project before running.</span></span> <span data-ttu-id="78821-142">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="78821-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="78821-143">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="78821-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="78821-144">不會嘗試使用 *launchSettings.json* 來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="78821-145">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="78821-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="78821-146">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="78821-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="78821-147">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="78821-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="78821-148">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="78821-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="78821-149">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="78821-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="78821-150">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="78821-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="78821-151">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="78821-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78821-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78821-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="78821-153">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="78821-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="78821-154">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="78821-155">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="78821-155">Defines the build configuration.</span></span> <span data-ttu-id="78821-156">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="78821-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="78821-157">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="78821-158">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="78821-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="78821-159">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="78821-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="78821-160">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="78821-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="78821-161">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="78821-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="78821-162">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="78821-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="78821-163">啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。</span><span class="sxs-lookup"><span data-stu-id="78821-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="78821-164">如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="78821-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="78821-165">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="78821-165">Doesn't build the project before running.</span></span> <span data-ttu-id="78821-166">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="78821-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="78821-167">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="78821-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="78821-168">不會嘗試使用 *launchSettings.json* 來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="78821-169">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="78821-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="78821-170">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="78821-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="78821-171">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="78821-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="78821-172">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="78821-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="78821-173">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="78821-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78821-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78821-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="78821-175">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="78821-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="78821-176">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="78821-177">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="78821-177">Defines the build configuration.</span></span> <span data-ttu-id="78821-178">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="78821-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="78821-179">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78821-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="78821-180">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="78821-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="78821-181">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="78821-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="78821-182">指定專案檔的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="78821-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="78821-183">(請參閱附註)。如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="78821-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="78821-184">透過 `-p|--project` 選項使用專案檔的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="78821-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="78821-185">CLI 中出現迴歸會無法提供具有 NET Core SDK 1.x 的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="78821-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="78821-186">如需此問題的詳細資訊，請參閱 [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992) (dotnet run -p，無法啟動專案 (dotnet/cli #5992))。</span><span class="sxs-lookup"><span data-stu-id="78821-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="78821-187">範例</span><span class="sxs-lookup"><span data-stu-id="78821-187">Examples</span></span>

<span data-ttu-id="78821-188">執行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="78821-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="78821-189">執行指定的專案：</span><span class="sxs-lookup"><span data-stu-id="78821-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="78821-190">執行目前目錄中的專案 (因為已使用空白的 `--` 選項，所以這個範例中的 `--help` 引數會傳遞給應用程式)：</span><span class="sxs-lookup"><span data-stu-id="78821-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="78821-191">還原相依性及目前目錄中專案的工具，只會顯示最基本的輸出，然後執行專案：(.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="78821-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`