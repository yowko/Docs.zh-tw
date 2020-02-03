---
title: dotnet build 命令
description: dotnet build 命令會建置專案和其所有相依性。
ms.date: 10/14/2019
ms.openlocfilehash: ec37d82c9e22a59acf7617f80a7491c0bcab89c9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734308"
---
# <a name="dotnet-build"></a><span data-ttu-id="c7b04-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c7b04-103">dotnet build</span></span>

<span data-ttu-id="c7b04-104">**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="c7b04-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="c7b04-105">名稱</span><span class="sxs-lookup"><span data-stu-id="c7b04-105">Name</span></span>

<span data-ttu-id="c7b04-106">`dotnet build` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="c7b04-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c7b04-107">概要</span><span class="sxs-lookup"><span data-stu-id="c7b04-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c7b04-108">描述</span><span class="sxs-lookup"><span data-stu-id="c7b04-108">Description</span></span>

<span data-ttu-id="c7b04-109">`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c7b04-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="c7b04-110">二進位檔會將專案的程式碼包含在副檔名為 *.dll*的中繼語言（IL）檔案中。</span><span class="sxs-lookup"><span data-stu-id="c7b04-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="c7b04-111">視專案類型和設定而定，可能會包含其他檔案，例如：</span><span class="sxs-lookup"><span data-stu-id="c7b04-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="c7b04-112">如果專案類型是以 .NET Core 3.0 或更新版本為目標的可執行檔，則可以用來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7b04-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="c7b04-113">用來以 *.pdb*副檔名進行偵錯工具的符號檔。</span><span class="sxs-lookup"><span data-stu-id="c7b04-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="c7b04-114">*.Deps.json json*檔案，其中會列出應用程式或程式庫的相依性。</span><span class="sxs-lookup"><span data-stu-id="c7b04-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="c7b04-115">*.Runtimeconfig.json json*檔案，指定應用程式的共用執行時間及其版本。</span><span class="sxs-lookup"><span data-stu-id="c7b04-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="c7b04-116">專案相依的其他程式庫（透過專案參考或 NuGet 套件參考）。</span><span class="sxs-lookup"><span data-stu-id="c7b04-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="c7b04-117">針對以 .NET Core 3.0 之前版本為目標的可執行檔專案，NuGet 的程式庫相依性通常不會複製到輸出檔案夾。</span><span class="sxs-lookup"><span data-stu-id="c7b04-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="c7b04-118">它們會在執行時間從 [NuGet 全域套件] 資料夾加以解析。</span><span class="sxs-lookup"><span data-stu-id="c7b04-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="c7b04-119">因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。</span><span class="sxs-lookup"><span data-stu-id="c7b04-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="c7b04-120">若要建立可部署的應用程式版本，您必須將它發佈（例如，使用[dotnet publish](dotnet-publish.md)命令）。</span><span class="sxs-lookup"><span data-stu-id="c7b04-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="c7b04-121">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c7b04-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="c7b04-122">針對以 .NET Core 3.0 和更新版本為目標的可執行專案，會將程式庫相依性複製到輸出檔案夾。</span><span class="sxs-lookup"><span data-stu-id="c7b04-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="c7b04-123">這表示，如果沒有任何其他發佈特定邏輯（例如 Web 專案），則組建輸出應該是可部署的。</span><span class="sxs-lookup"><span data-stu-id="c7b04-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="c7b04-124">建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="c7b04-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="c7b04-125">檔案會在 [`dotnet restore`](dotnet-restore.md) 執行時建立。</span><span class="sxs-lookup"><span data-stu-id="c7b04-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="c7b04-126">如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7b04-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="c7b04-127">使用 .NET Core 1.x SDK 時，您必須在執行 `dotnet build`之前明確地執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="c7b04-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="c7b04-128">自 .NET Core 2.0 SDK 開始，`dotnet restore` 會在您執行 `dotnet build` 時以隱含方式執行。</span><span class="sxs-lookup"><span data-stu-id="c7b04-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="c7b04-129">如果您想要在執行 build 命令時停用隱含還原，您可以跳過 `--no-restore` 選項。</span><span class="sxs-lookup"><span data-stu-id="c7b04-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="c7b04-130">專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。</span><span class="sxs-lookup"><span data-stu-id="c7b04-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="c7b04-131">下列範例顯示會產生可執行程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="c7b04-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="c7b04-132">若要產生程式庫，請省略 `<OutputType>` 屬性，或將其值變更為 `Library`。</span><span class="sxs-lookup"><span data-stu-id="c7b04-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="c7b04-133">程式庫的 IL DLL 不包含進入點，因此無法執行。</span><span class="sxs-lookup"><span data-stu-id="c7b04-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="c7b04-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="c7b04-134">MSBuild</span></span>

<span data-ttu-id="c7b04-135">`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。</span><span class="sxs-lookup"><span data-stu-id="c7b04-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="c7b04-136">如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。</span><span class="sxs-lookup"><span data-stu-id="c7b04-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="c7b04-137">除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `-p`，以及用於定義記錄器的 `-l`。</span><span class="sxs-lookup"><span data-stu-id="c7b04-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="c7b04-138">如需這些選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="c7b04-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="c7b04-139">或者，您也可以使用 [dotnet msbuild](dotnet-msbuild.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="c7b04-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="c7b04-140">執行 `dotnet build` 相當於執行 `dotnet msbuild -restore`;不過，輸出的預設詳細資訊是不同的。</span><span class="sxs-lookup"><span data-stu-id="c7b04-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="c7b04-141">引數</span><span class="sxs-lookup"><span data-stu-id="c7b04-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="c7b04-142">要建置的專案或方案檔。</span><span class="sxs-lookup"><span data-stu-id="c7b04-142">The project or solution file to build.</span></span> <span data-ttu-id="c7b04-143">若未指定專案或解決方案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 或 *sln* 的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="c7b04-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="c7b04-144">選項</span><span class="sxs-lookup"><span data-stu-id="c7b04-144">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="c7b04-145">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="c7b04-145">Defines the build configuration.</span></span> <span data-ttu-id="c7b04-146">大部分專案的預設值都是 `Debug`，但您可以覆寫專案中的組建設定。</span><span class="sxs-lookup"><span data-stu-id="c7b04-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c7b04-147">針對特定[架構](../../standard/frameworks.md)進行編譯。</span><span class="sxs-lookup"><span data-stu-id="c7b04-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="c7b04-148">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="c7b04-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="c7b04-149">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="c7b04-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="c7b04-150">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="c7b04-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="c7b04-151">自 .NET Core 2.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="c7b04-151">Available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c7b04-152">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c7b04-152">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="c7b04-153">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="c7b04-153">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="c7b04-154">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="c7b04-154">For example, to complete authentication.</span></span> <span data-ttu-id="c7b04-155">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="c7b04-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="c7b04-156">忽略專案對專案 (P2P) 參考，並且只建置指定的根專案。</span><span class="sxs-lookup"><span data-stu-id="c7b04-156">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="c7b04-157">針對累加建置，將建置標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="c7b04-157">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="c7b04-158">此旗標會關閉累加編譯，並強制全新重建專案的相依性關係圖。</span><span class="sxs-lookup"><span data-stu-id="c7b04-158">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c7b04-159">建置期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c7b04-159">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="c7b04-160">自 .NET Core 2.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="c7b04-160">Available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="c7b04-161">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="c7b04-161">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="c7b04-162">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="c7b04-162">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c7b04-163">在其中放置已建置的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="c7b04-163">Directory in which to place the built binaries.</span></span> <span data-ttu-id="c7b04-164">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="c7b04-164">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="c7b04-165">針對具有多個目標 framework 的專案（透過 `TargetFrameworks` 屬性），您也需要在指定此選項時定義 `--framework`。</span><span class="sxs-lookup"><span data-stu-id="c7b04-165">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c7b04-166">指定目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="c7b04-166">Specifies the target runtime.</span></span> <span data-ttu-id="c7b04-167">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="c7b04-167">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c7b04-168">設定 MSBuild 詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="c7b04-168">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="c7b04-169">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="c7b04-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c7b04-170">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="c7b04-170">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="c7b04-171">設定要在建置專案時使用的 `$(VersionSuffix)` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="c7b04-171">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="c7b04-172">這只有在沒有設定 `$(Version)` 屬性時才能運作。</span><span class="sxs-lookup"><span data-stu-id="c7b04-172">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="c7b04-173">接著，`$(Version)` 會設為 `$(VersionPrefix)` 加上 `$(VersionSuffix)`，並以破折號區隔。</span><span class="sxs-lookup"><span data-stu-id="c7b04-173">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="c7b04-174">範例</span><span class="sxs-lookup"><span data-stu-id="c7b04-174">Examples</span></span>

- <span data-ttu-id="c7b04-175">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="c7b04-175">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="c7b04-176">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="c7b04-176">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="c7b04-177">針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 18.04)：</span><span class="sxs-lookup"><span data-stu-id="c7b04-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="c7b04-178">建置專案，並在還原作業期間使用指定的 NuGet 套件來源 (.NET Core 2.0 SDK 和更新版本)：</span><span class="sxs-lookup"><span data-stu-id="c7b04-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="c7b04-179">使用 `-p` [MSBuild 選項](#msbuild)，建立專案並將版本1.2.3.4 設定為組建參數：</span><span class="sxs-lookup"><span data-stu-id="c7b04-179">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
