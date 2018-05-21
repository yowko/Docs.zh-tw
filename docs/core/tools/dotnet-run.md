---
title: dotnet run 命令 - .NET Core CLI
description: dotnet run 命令提供方便的選項，以透過原始程式碼來執行應用程式。
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.openlocfilehash: b45d6772cabd6be90ea8e8b5da57c16692b20322
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-run"></a><span data-ttu-id="11831-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="11831-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="11831-104">名稱</span><span class="sxs-lookup"><span data-stu-id="11831-104">Name</span></span>

<span data-ttu-id="11831-105">`dotnet run` - 執行原始程式碼，而不需要有任何明確的編譯或啟動命令。</span><span class="sxs-lookup"><span data-stu-id="11831-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="11831-106">概要</span><span class="sxs-lookup"><span data-stu-id="11831-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11831-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11831-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11831-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11831-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="11831-109">描述</span><span class="sxs-lookup"><span data-stu-id="11831-109">Description</span></span>

<span data-ttu-id="11831-110">`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="11831-110">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="11831-111">可用於在命令列中快速進行反覆開發。</span><span class="sxs-lookup"><span data-stu-id="11831-111">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="11831-112">此命令仰賴 [`dotnet build`](dotnet-build.md) 命令來建置程式碼。</span><span class="sxs-lookup"><span data-stu-id="11831-112">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="11831-113">建置的任何需求 (例如必須先還原專案) 也同樣適用於 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="11831-113">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="11831-114">輸出檔會寫入至預設位置，也就是 `bin/<configuration>/<target>`。</span><span class="sxs-lookup"><span data-stu-id="11831-114">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="11831-115">例如，如果您有 `netcoreapp1.0` 應用程式並執行 `dotnet run`，輸出將會放置在 `bin/Debug/netcoreapp1.0` 中。</span><span class="sxs-lookup"><span data-stu-id="11831-115">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="11831-116">而且會視需要覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="11831-116">Files are overwritten as needed.</span></span> <span data-ttu-id="11831-117">暫存檔案會放置在 `obj` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="11831-117">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="11831-118">如果專案指定多個架構，執行 `dotnet run` 會導致錯誤，除非使用 `-f|--framework <FRAMEWORK>` 選項來指定架構。</span><span class="sxs-lookup"><span data-stu-id="11831-118">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="11831-119">`dotnet run` 命令用於專案內容中，而非已建置的組件。</span><span class="sxs-lookup"><span data-stu-id="11831-119">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="11831-120">如果您改為嘗試執行與 Framework 相依的應用程式 DLL，您必須不透過命令使用 [dotnet](dotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="11831-120">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="11831-121">例如，若要執行 `myapp.dll`，使用︰</span><span class="sxs-lookup"><span data-stu-id="11831-121">For example, to run `myapp.dll`, use:</span></span>

```
dotnet myapp.dll
```

<span data-ttu-id="11831-122">如需 `dotnet` 驅動程式的詳細資訊，請參閱 [.NET Core 命令列工具 (CLI)](index.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="11831-122">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="11831-123">為了執行應用程式，`dotnet run` 命令會從 NuGet 快取解析共用執行階段之外的應用程式相依性。</span><span class="sxs-lookup"><span data-stu-id="11831-123">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="11831-124">因為它會使用快取相依性，不建議您在生產環境中使用 `dotnet run` 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="11831-124">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="11831-125">相反地，使用 [`dotnet publish`](dotnet-publish.md) 命令[建立部署](../deploying/index.md)，並部署已發佈的輸出。</span><span class="sxs-lookup"><span data-stu-id="11831-125">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="11831-126">選項</span><span class="sxs-lookup"><span data-stu-id="11831-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11831-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11831-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`--`

<span data-ttu-id="11831-128">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="11831-128">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="11831-129">此項目之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="11831-129">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="11831-130">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="11831-130">Defines the build configuration.</span></span> <span data-ttu-id="11831-131">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="11831-131">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="11831-132">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="11831-132">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="11831-133">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="11831-133">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="11831-134">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="11831-134">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="11831-135">這相當於刪除 *project.assets.json*。</span><span class="sxs-lookup"><span data-stu-id="11831-135">This is equivalent to deleting *project.assets.json*.</span></span>

`-h|--help`

<span data-ttu-id="11831-136">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="11831-136">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="11831-137">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="11831-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="11831-138">啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。</span><span class="sxs-lookup"><span data-stu-id="11831-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging` and `Production`.</span></span> <span data-ttu-id="11831-139">如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="11831-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="11831-140">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="11831-140">Doesn't build the project before running.</span></span>

`--no-dependencies`

<span data-ttu-id="11831-141">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="11831-141">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="11831-142">不會嘗試使用 *launchSettings.json* 設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="11831-142">Doesn't attempt to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="11831-143">執行命令時，不執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="11831-143">Doesn't perform an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="11831-144">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="11831-144">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="11831-145">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="11831-145">It defaults to the current directory if not specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="11831-146">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="11831-146">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="11831-147">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="11831-147">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11831-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11831-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="11831-149">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="11831-149">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="11831-150">此項目之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="11831-150">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="11831-151">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="11831-151">Defines the build configuration.</span></span> <span data-ttu-id="11831-152">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="11831-152">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="11831-153">使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="11831-153">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="11831-154">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="11831-154">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="11831-155">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="11831-155">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="11831-156">指定專案檔的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="11831-156">Specifies the path and name of the project file.</span></span> <span data-ttu-id="11831-157">(請參閱附註)。如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="11831-157">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="11831-158">透過 `-p|--project` 選項使用專案檔的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="11831-158">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="11831-159">CLI 中出現迴歸會無法提供具有 NET Core SDK 1.x 的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="11831-159">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="11831-160">如需此問題的詳細資訊，請參閱 [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992) (dotnet run -p，無法啟動專案 (dotnet/cli #5992))。</span><span class="sxs-lookup"><span data-stu-id="11831-160">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="11831-161">範例</span><span class="sxs-lookup"><span data-stu-id="11831-161">Examples</span></span>

<span data-ttu-id="11831-162">執行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="11831-162">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="11831-163">執行指定的專案：</span><span class="sxs-lookup"><span data-stu-id="11831-163">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="11831-164">執行目前目錄中的專案 (因為已使用 `--` 引數，所以這個範例中的 `--help` 引數會傳遞給應用程式)：</span><span class="sxs-lookup"><span data-stu-id="11831-164">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="11831-165">還原相依性及目前目錄中專案的工具，只會顯示最基本的輸出，然後執行專案：(.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="11831-165">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`