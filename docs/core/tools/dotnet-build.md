---
title: dotnet build 命令 - .NET Core CLI
description: dotnet build 命令會建置專案和其所有相依性。
ms.date: 12/04/2018
ms.openlocfilehash: 5d47fdfca14d20b3f2a134a8e734f76b1c86c498
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149155"
---
# <a name="dotnet-build"></a><span data-ttu-id="f1f9c-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="f1f9c-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f1f9c-104">名稱</span><span class="sxs-lookup"><span data-stu-id="f1f9c-104">Name</span></span>

<span data-ttu-id="f1f9c-105">`dotnet build` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1f9c-106">概要</span><span class="sxs-lookup"><span data-stu-id="f1f9c-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f1f9c-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f1f9c-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f1f9c-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f1f9c-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="f1f9c-109">說明</span><span class="sxs-lookup"><span data-stu-id="f1f9c-109">Description</span></span>

<span data-ttu-id="f1f9c-110">`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="f1f9c-111">二進位檔將專案程式碼包含在副檔名為 *.dll* 的中繼語言 (IL) 檔案中，以及副檔名為 *.pdb* 且用於偵錯的符號檔。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="f1f9c-112">產生相依性的 JSON 檔案 (*\*.deps.json*)，其中列出應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="f1f9c-113">產生 *\*.runtimeconfig.json* 檔案，其中指定應用程式的共用執行階段及其版本。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="f1f9c-114">如果專案對於第三方有相依性 (例如來自 NuGet 的程式庫)，這些相依性將會從 NuGet 快取解析，而不會透過專案的建置輸出提供。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="f1f9c-115">因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="f1f9c-116">這與 .NET Framework 的行為相反。在 .NET Framework 中，建置可執行檔專案 (應用程式) 所產生的輸出，可在任何已安裝 .NET Framework 的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="f1f9c-117">若要在 .NET Core 中擁有類似體驗，您需要使用 [dotnet publish](dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="f1f9c-118">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="f1f9c-119">建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="f1f9c-120">檔案會在 [`dotnet restore`](dotnet-restore.md) 執行時建立。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="f1f9c-121">如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="f1f9c-122">以前使用 .NET Core 1.x SDK 時，您需要先明確執行 `dotnet restore` 再執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="f1f9c-123">自 .NET Core 2.0 SDK 開始，`dotnet restore` 會在您執行 `dotnet build` 時以隱含方式執行。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="f1f9c-124">如果您想要在執行 build 命令時停用隱含還原，您可以跳過 `--no-restore` 選項。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="f1f9c-125">專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-125">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="f1f9c-126">下列範例顯示會產生可執行程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="f1f9c-126">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="f1f9c-127">若要產生程式庫，只要省略 `<OutputType>` 屬性即可。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-127">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="f1f9c-128">建置輸出的主要差別在於，程式庫的 IL DLL 不包含進入點，而且無法執行。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-128">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="f1f9c-129">MSBuild</span><span class="sxs-lookup"><span data-stu-id="f1f9c-129">MSBuild</span></span>

<span data-ttu-id="f1f9c-130">`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-130">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="f1f9c-131">如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-131">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="f1f9c-132">除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `-p`，以及用於定義記錄器的 `-l`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-132">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="f1f9c-133">如需這些選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-133">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="f1f9c-134">或者，您也可以使用 [dotnet msbuild](dotnet-msbuild.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-134">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="f1f9c-135">執行 `dotnet build` 相當於 `dotnet msbuild -restore -target:Build`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-135">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="f1f9c-136">引數</span><span class="sxs-lookup"><span data-stu-id="f1f9c-136">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="f1f9c-137">要建置的專案或方案檔。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-137">The project or solution file to build.</span></span> <span data-ttu-id="f1f9c-138">如果未指定專案或方案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 或 *sln* 的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-138">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="f1f9c-139">選項</span><span class="sxs-lookup"><span data-stu-id="f1f9c-139">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f1f9c-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f1f9c-140">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="f1f9c-141">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-141">Defines the build configuration.</span></span> <span data-ttu-id="f1f9c-142">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-142">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1f9c-143">針對特定[架構](../../standard/frameworks.md)進行編譯。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-143">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f1f9c-144">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-144">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="f1f9c-145">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-145">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f1f9c-146">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-146">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="f1f9c-147">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-147">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="f1f9c-148">忽略專案對專案 (P2P) 參考，並且只建置指定的根專案。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-148">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="f1f9c-149">針對累加建置，將建置標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-149">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="f1f9c-150">此旗標會關閉累加編譯，並強制全新重建專案的相依性關係圖。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-150">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="f1f9c-151">建置期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-151">Doesn't execute an implicit restore during build.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f1f9c-152">在其中放置已建置的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-152">Directory in which to place the built binaries.</span></span> <span data-ttu-id="f1f9c-153">當您指定這個選項時，也需要定義 `--framework`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-153">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="f1f9c-154">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-154">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f1f9c-155">指定目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-155">Specifies the target runtime.</span></span> <span data-ttu-id="f1f9c-156">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-156">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f1f9c-157">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f1f9c-158">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="f1f9c-159">定義專案檔版本欄位中星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-159">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="f1f9c-160">格式遵循 NuGet 的版本指導方針。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-160">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f1f9c-161">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f1f9c-161">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="f1f9c-162">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-162">Defines the build configuration.</span></span> <span data-ttu-id="f1f9c-163">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-163">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1f9c-164">針對特定[架構](../../standard/frameworks.md)進行編譯。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-164">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f1f9c-165">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-165">The framework must be defined in the [project file](csproj.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="f1f9c-166">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-166">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="f1f9c-167">忽略專案對專案 (P2P) 參考，並且只建置指定的根專案。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-167">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="f1f9c-168">針對累加建置，將建置標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-168">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="f1f9c-169">此旗標會關閉累加編譯，並強制全新重建專案的相依性關係圖。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-169">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f1f9c-170">在其中放置已建置的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-170">Directory in which to place the built binaries.</span></span> <span data-ttu-id="f1f9c-171">當您指定這個選項時，也需要定義 `--framework`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-171">You also need to define `--framework` when you specify this option.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f1f9c-172">指定目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-172">Specifies the target runtime.</span></span> <span data-ttu-id="f1f9c-173">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f1f9c-174">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f1f9c-175">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="f1f9c-176">定義專案檔版本欄位中星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-176">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="f1f9c-177">格式遵循 NuGet 的版本指導方針。</span><span class="sxs-lookup"><span data-stu-id="f1f9c-177">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f1f9c-178">範例</span><span class="sxs-lookup"><span data-stu-id="f1f9c-178">Examples</span></span>

* <span data-ttu-id="f1f9c-179">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="f1f9c-179">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="f1f9c-180">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="f1f9c-180">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="f1f9c-181">針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 16.04)：</span><span class="sxs-lookup"><span data-stu-id="f1f9c-181">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.16.04-x64
  ```

* <span data-ttu-id="f1f9c-182">建置專案，並在還原作業期間使用指定的 NuGet 套件來源 (.NET Core 2.0 SDK 和更新版本)：</span><span class="sxs-lookup"><span data-stu-id="f1f9c-182">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="f1f9c-183">建置專案並設定 1.2.3.4 版本作為建置參數：</span><span class="sxs-lookup"><span data-stu-id="f1f9c-183">Build the project and set 1.2.3.4 version as a build parameter:</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```