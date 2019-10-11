---
title: dotnet build 命令
description: dotnet build 命令會建置專案和其所有相依性。
ms.date: 08/08/2019
ms.openlocfilehash: 6194d70a8a14e63adbcad39c7dabbbd220ca329d
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179972"
---
# <a name="dotnet-build"></a><span data-ttu-id="e1b98-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="e1b98-103">dotnet build</span></span>

<span data-ttu-id="e1b98-104">**本文適用於：✓** .NET Core 1.x SDK 及更新版本</span><span class="sxs-lookup"><span data-stu-id="e1b98-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="e1b98-105">Name</span><span class="sxs-lookup"><span data-stu-id="e1b98-105">Name</span></span>

<span data-ttu-id="e1b98-106">`dotnet build` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="e1b98-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e1b98-107">概要</span><span class="sxs-lookup"><span data-stu-id="e1b98-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e1b98-108">描述</span><span class="sxs-lookup"><span data-stu-id="e1b98-108">Description</span></span>

<span data-ttu-id="e1b98-109">`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。</span><span class="sxs-lookup"><span data-stu-id="e1b98-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="e1b98-110">二進位檔將專案程式碼包含在副檔名為 *.dll* 的中繼語言 (IL) 檔案中，以及副檔名為 *.pdb* 且用於偵錯的符號檔。</span><span class="sxs-lookup"><span data-stu-id="e1b98-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="e1b98-111">產生相依性 JSON 檔案 ( *.deps.json*)，其中會列出應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="e1b98-111">A dependencies JSON file (*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="e1b98-112">產生 *.runtimeconfig.json* 檔案，其中會指定應用程式的共用執行階段及其版本。</span><span class="sxs-lookup"><span data-stu-id="e1b98-112">A *.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="e1b98-113">如果專案對於第三方有相依性 (例如來自 NuGet 的程式庫)，這些相依性將會從 NuGet 快取解析，而不會透過專案的建置輸出提供。</span><span class="sxs-lookup"><span data-stu-id="e1b98-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="e1b98-114">因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。</span><span class="sxs-lookup"><span data-stu-id="e1b98-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="e1b98-115">這與 .NET Framework 的行為相反。在 .NET Framework 中，建置可執行檔專案 (應用程式) 所產生的輸出，可在任何已安裝 .NET Framework 的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="e1b98-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="e1b98-116">若要在 .NET Core 中擁有類似體驗，您需要使用 [dotnet publish](dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="e1b98-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="e1b98-117">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e1b98-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="e1b98-118">建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="e1b98-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="e1b98-119">檔案會在 [`dotnet restore`](dotnet-restore.md) 執行時建立。</span><span class="sxs-lookup"><span data-stu-id="e1b98-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="e1b98-120">如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1b98-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="e1b98-121">使用 .NET Core 1.x SDK 時，您必須在執行 `dotnet build` 之前明確地執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-121">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="e1b98-122">自 .NET Core 2.0 SDK 開始，`dotnet restore` 會在您執行 `dotnet build` 時以隱含方式執行。</span><span class="sxs-lookup"><span data-stu-id="e1b98-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="e1b98-123">如果您想要在執行 build 命令時停用隱含還原，您可以跳過 `--no-restore` 選項。</span><span class="sxs-lookup"><span data-stu-id="e1b98-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="e1b98-124">專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。</span><span class="sxs-lookup"><span data-stu-id="e1b98-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="e1b98-125">下列範例顯示會產生可執行程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="e1b98-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="e1b98-126">若要產生程式庫，只要省略 `<OutputType>` 屬性即可。</span><span class="sxs-lookup"><span data-stu-id="e1b98-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="e1b98-127">建置輸出的主要差別在於，程式庫的 IL DLL 不包含進入點，而且無法執行。</span><span class="sxs-lookup"><span data-stu-id="e1b98-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="e1b98-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="e1b98-128">MSBuild</span></span>

<span data-ttu-id="e1b98-129">`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。</span><span class="sxs-lookup"><span data-stu-id="e1b98-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="e1b98-130">如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。</span><span class="sxs-lookup"><span data-stu-id="e1b98-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="e1b98-131">除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `-p`，以及用於定義記錄器的 `-l`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="e1b98-132">如需這些選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="e1b98-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="e1b98-133">或者，您也可以使用 [dotnet msbuild](dotnet-msbuild.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="e1b98-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="e1b98-134">執行 `dotnet build` 相當於 `dotnet msbuild -restore -target:Build`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="e1b98-135">引數</span><span class="sxs-lookup"><span data-stu-id="e1b98-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="e1b98-136">要建置的專案或方案檔。</span><span class="sxs-lookup"><span data-stu-id="e1b98-136">The project or solution file to build.</span></span> <span data-ttu-id="e1b98-137">若未指定專案或解決方案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 或 *sln* 的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="e1b98-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="e1b98-138">選項。</span><span class="sxs-lookup"><span data-stu-id="e1b98-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="e1b98-139">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="e1b98-139">Defines the build configuration.</span></span> <span data-ttu-id="e1b98-140">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e1b98-141">針對特定[架構](../../standard/frameworks.md)進行編譯。</span><span class="sxs-lookup"><span data-stu-id="e1b98-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e1b98-142">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="e1b98-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="e1b98-143">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="e1b98-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e1b98-144">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="e1b98-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="e1b98-145">自 .NET Core 2.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="e1b98-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="e1b98-146">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="e1b98-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="e1b98-147">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="e1b98-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e1b98-148">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="e1b98-148">For example, to complete authentication.</span></span> <span data-ttu-id="e1b98-149">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="e1b98-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="e1b98-150">忽略專案對專案 (P2P) 參考，並且只建置指定的根專案。</span><span class="sxs-lookup"><span data-stu-id="e1b98-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="e1b98-151">針對累加建置，將建置標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="e1b98-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="e1b98-152">此旗標會關閉累加編譯，並強制全新重建專案的相依性關係圖。</span><span class="sxs-lookup"><span data-stu-id="e1b98-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="e1b98-153">建置期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="e1b98-153">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="e1b98-154">自 .NET Core 2.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="e1b98-154">Available since .NET Core 2.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="e1b98-155">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="e1b98-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="e1b98-156">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="e1b98-156">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e1b98-157">在其中放置已建置的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="e1b98-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="e1b98-158">當您指定這個選項時，也需要定義 `--framework`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="e1b98-159">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e1b98-160">指定目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="e1b98-160">Specifies the target runtime.</span></span> <span data-ttu-id="e1b98-161">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="e1b98-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e1b98-162">設定 MSBuild 詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="e1b98-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="e1b98-163">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e1b98-164">預設為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="e1b98-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="e1b98-165">設定要在建置專案時使用的 `$(VersionSuffix)` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="e1b98-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="e1b98-166">這只有在沒有設定 `$(Version)` 屬性時才能運作。</span><span class="sxs-lookup"><span data-stu-id="e1b98-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="e1b98-167">接著，`$(Version)` 會設為 `$(VersionPrefix)` 加上 `$(VersionSuffix)`，並以破折號區隔。</span><span class="sxs-lookup"><span data-stu-id="e1b98-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="e1b98-168">範例</span><span class="sxs-lookup"><span data-stu-id="e1b98-168">Examples</span></span>

* <span data-ttu-id="e1b98-169">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="e1b98-169">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

* <span data-ttu-id="e1b98-170">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="e1b98-170">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

* <span data-ttu-id="e1b98-171">針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 18.04)：</span><span class="sxs-lookup"><span data-stu-id="e1b98-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="e1b98-172">建置專案，並在還原作業期間使用指定的 NuGet 套件來源 (.NET Core 2.0 SDK 和更新版本)：</span><span class="sxs-lookup"><span data-stu-id="e1b98-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="e1b98-173">建置專案並使用 `-p` [MSBuild 選項](#msbuild) 將 1.2.3.4 版設定為組建參數：</span><span class="sxs-lookup"><span data-stu-id="e1b98-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
