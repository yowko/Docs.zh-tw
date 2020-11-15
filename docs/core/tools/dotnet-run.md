---
title: dotnet run 命令
description: dotnet run 命令提供方便的選項，以透過原始程式碼來執行應用程式。
ms.date: 02/19/2020
ms.openlocfilehash: c80f290c75e3bac65ae73fe8edada53db4ce86f8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634412"
---
# <a name="dotnet-run"></a><span data-ttu-id="cecd4-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="cecd4-103">dotnet run</span></span>

<span data-ttu-id="cecd4-104">本文 **適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="cecd4-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cecd4-105">名稱</span><span class="sxs-lookup"><span data-stu-id="cecd4-105">Name</span></span>

<span data-ttu-id="cecd4-106">`dotnet run` - 執行原始程式碼，而不需要有任何明確的編譯或啟動命令。</span><span class="sxs-lookup"><span data-stu-id="cecd4-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cecd4-107">概要</span><span class="sxs-lookup"><span data-stu-id="cecd4-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="cecd4-108">描述</span><span class="sxs-lookup"><span data-stu-id="cecd4-108">Description</span></span>

<span data-ttu-id="cecd4-109">`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cecd4-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="cecd4-110">可用於在命令列中快速進行反覆開發。</span><span class="sxs-lookup"><span data-stu-id="cecd4-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="cecd4-111">命令相依于用 [`dotnet build`](dotnet-build.md) 來建立程式碼的命令。</span><span class="sxs-lookup"><span data-stu-id="cecd4-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="cecd4-112">建置的任何需求 (例如必須先還原專案) 也同樣適用於 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="cecd4-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="cecd4-113">輸出檔會寫入至預設位置，也就是 `bin/<configuration>/<target>`。</span><span class="sxs-lookup"><span data-stu-id="cecd4-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="cecd4-114">例如，如果您有 `netcoreapp2.1` 應用程式並執行 `dotnet run`，輸出將會放置在 `bin/Debug/netcoreapp2.1` 中。</span><span class="sxs-lookup"><span data-stu-id="cecd4-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="cecd4-115">而且會視需要覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="cecd4-115">Files are overwritten as needed.</span></span> <span data-ttu-id="cecd4-116">暫存檔案會放置在 `obj` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="cecd4-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="cecd4-117">如果專案指定多個架構，執行 `dotnet run` 會導致錯誤，除非使用 `-f|--framework <FRAMEWORK>` 選項來指定架構。</span><span class="sxs-lookup"><span data-stu-id="cecd4-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="cecd4-118">`dotnet run` 命令用於專案內容中，而非已建置的組件。</span><span class="sxs-lookup"><span data-stu-id="cecd4-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="cecd4-119">如果您改為嘗試執行與 Framework 相依的應用程式 DLL，您必須不透過命令使用 [dotnet](dotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="cecd4-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="cecd4-120">例如，若要執行 `myapp.dll`，使用︰</span><span class="sxs-lookup"><span data-stu-id="cecd4-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="cecd4-121">如需驅動程式的詳細資訊 `dotnet` ，請參閱 [.Net 命令列工具 (CLI) ](index.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="cecd4-121">For more information on the `dotnet` driver, see the [.NET Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="cecd4-122">為了執行應用程式，`dotnet run` 命令會從 NuGet 快取解析共用執行階段之外的應用程式相依性。</span><span class="sxs-lookup"><span data-stu-id="cecd4-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="cecd4-123">因為它會使用快取相依性，不建議您在生產環境中使用 `dotnet run` 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cecd4-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="cecd4-124">相反地，使用 [`dotnet publish`](dotnet-publish.md) 命令[建立部署](../deploying/index.md)，並部署已發佈的輸出。</span><span class="sxs-lookup"><span data-stu-id="cecd4-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="cecd4-125">隱含還原</span><span class="sxs-lookup"><span data-stu-id="cecd4-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="cecd4-126">選項</span><span class="sxs-lookup"><span data-stu-id="cecd4-126">Options</span></span>

- **`--`**

  <span data-ttu-id="cecd4-127">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="cecd4-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="cecd4-128">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cecd4-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="cecd4-129">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="cecd4-129">Defines the build configuration.</span></span> <span data-ttu-id="cecd4-130">大部分專案的預設值為 `Debug` ，但您可以覆寫專案中的組建設定。</span><span class="sxs-lookup"><span data-stu-id="cecd4-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="cecd4-131">使用指定的 [架構](../../standard/frameworks.md)，建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cecd4-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cecd4-132">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="cecd4-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="cecd4-133">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="cecd4-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cecd4-134">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="cecd4-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cecd4-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="cecd4-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="cecd4-136">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="cecd4-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="cecd4-137">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="cecd4-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="cecd4-138">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="cecd4-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="cecd4-139">啟動設定檔是在檔案的 *launchSettings.js* 中定義，通常稱為 `Development` 、 `Staging` 和 `Production` 。</span><span class="sxs-lookup"><span data-stu-id="cecd4-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="cecd4-140">如需詳細資訊，請參閱 [使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="cecd4-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="cecd4-141">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="cecd4-141">Doesn't build the project before running.</span></span> <span data-ttu-id="cecd4-142">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="cecd4-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="cecd4-143">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="cecd4-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="cecd4-144">不會嘗試使用 *launchSettings.json* 來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="cecd4-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="cecd4-145">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="cecd4-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="cecd4-146">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="cecd4-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="cecd4-147">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="cecd4-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="cecd4-148">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="cecd4-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="cecd4-149">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="cecd4-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cecd4-150">`-r` 自 .NET Core 3.0 SDK 起提供的簡短選項。</span><span class="sxs-lookup"><span data-stu-id="cecd4-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cecd4-151">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="cecd4-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cecd4-152">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="cecd4-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="cecd4-153">預設值是 `m`。</span><span class="sxs-lookup"><span data-stu-id="cecd4-153">The default value is `m`.</span></span> <span data-ttu-id="cecd4-154">自 .NET Core 2.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="cecd4-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="cecd4-155">範例</span><span class="sxs-lookup"><span data-stu-id="cecd4-155">Examples</span></span>

- <span data-ttu-id="cecd4-156">執行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="cecd4-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="cecd4-157">執行指定的專案：</span><span class="sxs-lookup"><span data-stu-id="cecd4-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="cecd4-158">執行目前目錄中的專案 (因為已使用空白的 `--` 選項，所以這個範例中的 `--help` 引數會傳遞給應用程式)：</span><span class="sxs-lookup"><span data-stu-id="cecd4-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="cecd4-159">還原目前目錄中專案的相依性和工具，只會顯示最基本的輸出，然後執行專案：</span><span class="sxs-lookup"><span data-stu-id="cecd4-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project:</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
