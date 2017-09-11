---
title: "dotnet build 命令 - .NET Core CLI"
description: "dotnet build 命令會建置專案和其所有相依性。"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 9a5495220a95d0e2b0018f08617bbb41485fe96f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-build"></a><span data-ttu-id="a45f9-103">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="a45f9-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a45f9-104">名稱</span><span class="sxs-lookup"><span data-stu-id="a45f9-104">Name</span></span>

<span data-ttu-id="a45f9-105">`dotnet build` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="a45f9-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a45f9-106">概要</span><span class="sxs-lookup"><span data-stu-id="a45f9-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a45f9-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a45f9-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a45f9-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a45f9-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a45f9-109">說明</span><span class="sxs-lookup"><span data-stu-id="a45f9-109">Description</span></span>

<span data-ttu-id="a45f9-110">`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。</span><span class="sxs-lookup"><span data-stu-id="a45f9-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="a45f9-111">二進位檔將專案程式碼包含在副檔名為 *.dll* 的中繼語言 (IL) 檔案中，以及副檔名為 *.pdb* 且用於偵錯的符號檔。</span><span class="sxs-lookup"><span data-stu-id="a45f9-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="a45f9-112">產生相依性的 JSON 檔案 (*\*.deps.json*)，其中列出應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a45f9-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="a45f9-113">產生 *\*.runtimeconfig.json* 檔案，其中指定應用程式的共用執行階段及其版本。</span><span class="sxs-lookup"><span data-stu-id="a45f9-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="a45f9-114">如果專案對於第三方有相依性 (例如來自 NuGet 的程式庫)，這些相依性將會從 NuGet 快取解析，而不會透過專案的建置輸出提供。</span><span class="sxs-lookup"><span data-stu-id="a45f9-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="a45f9-115">因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。</span><span class="sxs-lookup"><span data-stu-id="a45f9-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="a45f9-116">這與 .NET Framework 的行為相反。在 .NET Framework 中，建置可執行檔專案 (應用程式) 所產生的輸出，可在任何已安裝 .NET Framework 的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="a45f9-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="a45f9-117">若要在 .NET Core 中擁有類似體驗，您需要使用 [dotnet publish](dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="a45f9-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="a45f9-118">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a45f9-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="a45f9-119">建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="a45f9-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="a45f9-120">檔案會在 [`dotnet restore`](dotnet-restore.md) 執行時建立。</span><span class="sxs-lookup"><span data-stu-id="a45f9-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="a45f9-121">如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a45f9-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="a45f9-122">以前使用 .NET Core 1.x SDK，您需要先明確執行 `dotnet restore` 再執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-122">With .NET Core 1.x SDK, you needed to explicitily run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="a45f9-123">自 .NET Core 2.0 SDK 開始，`dotnet restore` 會在您執行 `dotnet build` 時以隱含方式執行。</span><span class="sxs-lookup"><span data-stu-id="a45f9-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitily when you run `dotnet build`.</span></span> <span data-ttu-id="a45f9-124">如果您想要在執行 build 命令時停用隱含還原，您可以跳過 `--no-restore` 選項。</span><span class="sxs-lookup"><span data-stu-id="a45f9-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

<span data-ttu-id="a45f9-125">`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。</span><span class="sxs-lookup"><span data-stu-id="a45f9-125">`dotnet build` uses MSBuild to build the project; thus, it supports both parallel and incremental builds.</span></span> <span data-ttu-id="a45f9-126">如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。</span><span class="sxs-lookup"><span data-stu-id="a45f9-126">Refer to [Incremental Builds](/visualstudio/msbuild/incremental-builds) for more information.</span></span>

<span data-ttu-id="a45f9-127">除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `/p`，以及用於定義記錄器的 `/l`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `/p` for setting properties or `/l` to define a logger.</span></span> <span data-ttu-id="a45f9-128">請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)，以深入了解這些選項。</span><span class="sxs-lookup"><span data-stu-id="a45f9-128">Learn more about these options in the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> 

<span data-ttu-id="a45f9-129">專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。</span><span class="sxs-lookup"><span data-stu-id="a45f9-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="a45f9-130">下列範例顯示將產生可執行程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="a45f9-130">The following example shows a project that will produce executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="a45f9-131">若要產生程式庫，只要省略 `<OutputType>` 屬性即可。</span><span class="sxs-lookup"><span data-stu-id="a45f9-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="a45f9-132">建置輸出的主要差別在於，程式庫的 IL DLL 不包含進入點，而且無法執行。</span><span class="sxs-lookup"><span data-stu-id="a45f9-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span> 

## <a name="arguments"></a><span data-ttu-id="a45f9-133">引數</span><span class="sxs-lookup"><span data-stu-id="a45f9-133">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a45f9-134">要建置的專案檔。</span><span class="sxs-lookup"><span data-stu-id="a45f9-134">The project file to build.</span></span> <span data-ttu-id="a45f9-135">如果未指定專案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="a45f9-135">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="a45f9-136">選項</span><span class="sxs-lookup"><span data-stu-id="a45f9-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a45f9-137">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a45f9-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a45f9-138">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="a45f9-138">Defines the build configuration.</span></span> <span data-ttu-id="a45f9-139">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a45f9-140">針對特定[架構](../../standard/frameworks.md)進行編譯。</span><span class="sxs-lookup"><span data-stu-id="a45f9-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a45f9-141">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="a45f9-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

 <span data-ttu-id="a45f9-142">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="a45f9-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a45f9-143">這相當於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="a45f9-143">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="a45f9-144">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a45f9-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="a45f9-145">忽略專案對專案 (P2P) 參考，並且只建置指定要建置的根專案。</span><span class="sxs-lookup"><span data-stu-id="a45f9-145">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="a45f9-146">針對累加建置，將建置標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="a45f9-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="a45f9-147">這會關閉累加編譯，並強制全新重建專案的相依性關係圖。</span><span class="sxs-lookup"><span data-stu-id="a45f9-147">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="a45f9-148">建置期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a45f9-148">Doesn't perform an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a45f9-149">在其中放置已建置的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="a45f9-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="a45f9-150">當您指定這個選項時，也需要定義 `--framework`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a45f9-151">指定目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="a45f9-151">Specifies the target runtime.</span></span> <span data-ttu-id="a45f9-152">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="a45f9-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a45f9-153">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a45f9-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a45f9-154">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a45f9-155">定義專案檔版本欄位中星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="a45f9-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="a45f9-156">格式遵循 NuGet 的版本指導方針。</span><span class="sxs-lookup"><span data-stu-id="a45f9-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a45f9-157">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a45f9-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a45f9-158">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="a45f9-158">Defines the build configuration.</span></span> <span data-ttu-id="a45f9-159">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a45f9-160">針對特定[架構](../../standard/frameworks.md)進行編譯。</span><span class="sxs-lookup"><span data-stu-id="a45f9-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a45f9-161">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="a45f9-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="a45f9-162">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a45f9-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="a45f9-163">忽略專案對專案 (P2P) 參考，並且只建置指定要建置的根專案。</span><span class="sxs-lookup"><span data-stu-id="a45f9-163">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="a45f9-164">針對累加建置，將建置標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="a45f9-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="a45f9-165">這會關閉累加編譯，並強制全新重建專案的相依性關係圖。</span><span class="sxs-lookup"><span data-stu-id="a45f9-165">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a45f9-166">在其中放置已建置的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="a45f9-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="a45f9-167">當您指定這個選項時，也需要定義 `--framework`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a45f9-168">指定目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="a45f9-168">Specifies the target runtime.</span></span> <span data-ttu-id="a45f9-169">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="a45f9-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a45f9-170">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a45f9-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a45f9-171">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a45f9-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a45f9-172">定義專案檔版本欄位中星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="a45f9-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="a45f9-173">格式遵循 NuGet 的版本指導方針。</span><span class="sxs-lookup"><span data-stu-id="a45f9-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a45f9-174">範例</span><span class="sxs-lookup"><span data-stu-id="a45f9-174">Examples</span></span>

<span data-ttu-id="a45f9-175">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="a45f9-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="a45f9-176">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="a45f9-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="a45f9-177">針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 16.04)：</span><span class="sxs-lookup"><span data-stu-id="a45f9-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`
