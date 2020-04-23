---
title: dotnet build 命令
description: dotnet build 命令會建置專案和其所有相依性。
ms.date: 02/14/2020
ms.openlocfilehash: 1022df059493c7e045f81d4be93dff2fdab77eb1
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102836"
---
# <a name="dotnet-build"></a><span data-ttu-id="17272-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="17272-103">dotnet build</span></span>

<span data-ttu-id="17272-104">**本文適用於:✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="17272-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="17272-105">名稱</span><span class="sxs-lookup"><span data-stu-id="17272-105">Name</span></span>

<span data-ttu-id="17272-106">`dotnet build` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="17272-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="17272-107">概要</span><span class="sxs-lookup"><span data-stu-id="17272-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="17272-108">描述</span><span class="sxs-lookup"><span data-stu-id="17272-108">Description</span></span>

<span data-ttu-id="17272-109">`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。</span><span class="sxs-lookup"><span data-stu-id="17272-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="17272-110">二進位檔包括專案代碼的中間語言 (IL) 檔案與 *.dll*副檔名。</span><span class="sxs-lookup"><span data-stu-id="17272-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="17272-111">根據項目類型和設定,可能會包括其他檔,例如:</span><span class="sxs-lookup"><span data-stu-id="17272-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="17272-112">如果項目類型是目標 .NET Core 3.0 或更高版本的可執行檔,則可用於運行應用程式的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="17272-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="17272-113">用於使用 *.pdb*擴展名進行除錯的符號檔。</span><span class="sxs-lookup"><span data-stu-id="17272-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="17272-114">*.deps.json*檔,其中列出了應用程式或庫的依賴項。</span><span class="sxs-lookup"><span data-stu-id="17272-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="17272-115">*.運行時config.json*檔,該檔指定應用程式的共用運行時及其版本。</span><span class="sxs-lookup"><span data-stu-id="17272-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="17272-116">項目所依賴的其他庫(通過專案引用或 NuGet 包引用)。</span><span class="sxs-lookup"><span data-stu-id="17272-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="17272-117">對於面向早於 .NET Core 3.0 版本的可執行專案,NuGet 的庫依賴項通常不會複製到輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="17272-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="17272-118">它們在運行時從 NuGet 全域包資料夾中解析。</span><span class="sxs-lookup"><span data-stu-id="17272-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="17272-119">因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。</span><span class="sxs-lookup"><span data-stu-id="17272-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="17272-120">要建立可部署的應用程式的版本,需要發佈它(例如,使用[dotnet發佈](dotnet-publish.md)命令)。</span><span class="sxs-lookup"><span data-stu-id="17272-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="17272-121">有關詳細資訊,請參閱[.NET 核心應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="17272-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="17272-122">對於針對 .NET Core 3.0 及更高版本的可執行專案,庫依賴項將複製到輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="17272-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="17272-123">這意味著,如果沒有任何其他特定於發佈的邏輯(如 Web 專案),則生成輸出應該是可部署的。</span><span class="sxs-lookup"><span data-stu-id="17272-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="17272-124">隱式還原</span><span class="sxs-lookup"><span data-stu-id="17272-124">Implicit restore</span></span>

<span data-ttu-id="17272-125">建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="17272-125">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="17272-126">執行時[`dotnet restore`](dotnet-restore.md)將創建該檔。</span><span class="sxs-lookup"><span data-stu-id="17272-126">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="17272-127">如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="17272-127">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a><span data-ttu-id="17272-128">執行或函式庫輸出</span><span class="sxs-lookup"><span data-stu-id="17272-128">Executable or library output</span></span>

<span data-ttu-id="17272-129">專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。</span><span class="sxs-lookup"><span data-stu-id="17272-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="17272-130">下列範例顯示會產生可執行程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="17272-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="17272-131">要產生函式庫,`<OutputType>`省略屬性或將其值`Library`變更為 。</span><span class="sxs-lookup"><span data-stu-id="17272-131">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="17272-132">庫的 IL DLL 不包含入口點,無法執行。</span><span class="sxs-lookup"><span data-stu-id="17272-132">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="17272-133">MSBuild</span><span class="sxs-lookup"><span data-stu-id="17272-133">MSBuild</span></span>

<span data-ttu-id="17272-134">`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。</span><span class="sxs-lookup"><span data-stu-id="17272-134">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="17272-135">如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。</span><span class="sxs-lookup"><span data-stu-id="17272-135">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="17272-136">除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `-p`，以及用於定義記錄器的 `-l`。</span><span class="sxs-lookup"><span data-stu-id="17272-136">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="17272-137">如需這些選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="17272-137">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="17272-138">或者，您也可以使用 [dotnet msbuild](dotnet-msbuild.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="17272-138">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="17272-139">執行`dotnet build`等效於`dotnet msbuild -restore`運行 ;但是,輸出的默認詳細程度是不同的。</span><span class="sxs-lookup"><span data-stu-id="17272-139">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="17272-140">引數</span><span class="sxs-lookup"><span data-stu-id="17272-140">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="17272-141">要建置的專案或方案檔。</span><span class="sxs-lookup"><span data-stu-id="17272-141">The project or solution file to build.</span></span> <span data-ttu-id="17272-142">若未指定專案或解決方案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 或 *sln* 的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="17272-142">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="17272-143">選項。</span><span class="sxs-lookup"><span data-stu-id="17272-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="17272-144">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="17272-144">Defines the build configuration.</span></span> <span data-ttu-id="17272-145">大多數項目的預設值為,`Debug`但您可以覆蓋專案中的生成配置設置。</span><span class="sxs-lookup"><span data-stu-id="17272-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="17272-146">針對特定[架構](../../standard/frameworks.md)進行編譯。</span><span class="sxs-lookup"><span data-stu-id="17272-146">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="17272-147">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="17272-147">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="17272-148">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="17272-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="17272-149">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="17272-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="17272-150">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="17272-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="17272-151">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="17272-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="17272-152">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="17272-152">For example, to complete authentication.</span></span> <span data-ttu-id="17272-153">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="17272-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="17272-154">忽略專案對專案 (P2P) 參考，並且只建置指定的根專案。</span><span class="sxs-lookup"><span data-stu-id="17272-154">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="17272-155">針對累加建置，將建置標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="17272-155">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="17272-156">此旗標會關閉累加編譯，並強制全新重建專案的相依性關係圖。</span><span class="sxs-lookup"><span data-stu-id="17272-156">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="17272-157">建置期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="17272-157">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="17272-158">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="17272-158">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="17272-159">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="17272-159">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="17272-160">在其中放置已建置的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="17272-160">Directory in which to place the built binaries.</span></span> <span data-ttu-id="17272-161">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="17272-161">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="17272-162">對於具有多個目標框架的專案(通過`TargetFrameworks`屬性),還需要在指定此選項`--framework`時 定義。</span><span class="sxs-lookup"><span data-stu-id="17272-162">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="17272-163">指定目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="17272-163">Specifies the target runtime.</span></span> <span data-ttu-id="17272-164">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="17272-164">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="17272-165">設定 MSBuild 詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="17272-165">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="17272-166">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="17272-166">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="17272-167">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="17272-167">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="17272-168">設定要在建置專案時使用的 `$(VersionSuffix)` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="17272-168">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="17272-169">這只有在沒有設定 `$(Version)` 屬性時才能運作。</span><span class="sxs-lookup"><span data-stu-id="17272-169">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="17272-170">接著，`$(Version)` 會設為 `$(VersionPrefix)` 加上 `$(VersionSuffix)`，並以破折號區隔。</span><span class="sxs-lookup"><span data-stu-id="17272-170">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="17272-171">範例</span><span class="sxs-lookup"><span data-stu-id="17272-171">Examples</span></span>

- <span data-ttu-id="17272-172">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="17272-172">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="17272-173">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="17272-173">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="17272-174">針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 18.04)：</span><span class="sxs-lookup"><span data-stu-id="17272-174">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="17272-175">建置專案，並在還原作業期間使用指定的 NuGet 套件來源 (.NET Core 2.0 SDK 和更新版本)：</span><span class="sxs-lookup"><span data-stu-id="17272-175">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="17272-176">建置專案並使用 `-p` [MSBuild 選項](#msbuild) 將 1.2.3.4 版設定為組建參數：</span><span class="sxs-lookup"><span data-stu-id="17272-176">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
