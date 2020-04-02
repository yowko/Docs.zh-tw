---
title: dotnet publish 命令
description: dotnet 發佈命令將 .NET Core 專案或解決方案發佈到目錄。
ms.date: 02/24/2020
ms.openlocfilehash: 0e18220443f3713c86c257fcf401b98ddd716ebc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588273"
---
# <a name="dotnet-publish"></a><span data-ttu-id="c54e3-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="c54e3-103">dotnet publish</span></span>

<span data-ttu-id="c54e3-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="c54e3-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c54e3-105">名稱</span><span class="sxs-lookup"><span data-stu-id="c54e3-105">Name</span></span>

<span data-ttu-id="c54e3-106">`dotnet publish`- 將應用程式及其依賴項發佈到資料夾以部署到託管系統。</span><span class="sxs-lookup"><span data-stu-id="c54e3-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c54e3-107">概要</span><span class="sxs-lookup"><span data-stu-id="c54e3-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c54e3-108">描述</span><span class="sxs-lookup"><span data-stu-id="c54e3-108">Description</span></span>

<span data-ttu-id="c54e3-109">`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。</span><span class="sxs-lookup"><span data-stu-id="c54e3-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="c54e3-110">此輸出包含下列資產：</span><span class="sxs-lookup"><span data-stu-id="c54e3-110">The output includes the following assets:</span></span>

- <span data-ttu-id="c54e3-111">組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。</span><span class="sxs-lookup"><span data-stu-id="c54e3-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="c54e3-112">包含專案的所有依賴項的 *.deps.json*檔。</span><span class="sxs-lookup"><span data-stu-id="c54e3-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="c54e3-113">一個 *.runtimeconfig.json*檔,用於指定應用程式期望的共用運行時以及運行時的其他配置選項(例如,垃圾回收類型)。</span><span class="sxs-lookup"><span data-stu-id="c54e3-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="c54e3-114">應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="c54e3-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="c54e3-115">`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。</span><span class="sxs-lookup"><span data-stu-id="c54e3-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="c54e3-116">這是準備應用程式以供部署的唯一正式支援的方法。</span><span class="sxs-lookup"><span data-stu-id="c54e3-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="c54e3-117">根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="c54e3-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="c54e3-118">有關詳細資訊,請參閱發佈[.NET 核心應用 ,以及 .NET 核心 CLI](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="c54e3-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="msbuild"></a><span data-ttu-id="c54e3-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="c54e3-119">MSBuild</span></span>

<span data-ttu-id="c54e3-120">`dotnet publish` 命令會呼叫 MSBuild，這會叫用 `Publish` 目標。</span><span class="sxs-lookup"><span data-stu-id="c54e3-120">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="c54e3-121">所有傳遞給 `dotnet publish` 的參數都會傳遞給 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="c54e3-121">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="c54e3-122">`-c` 和 `-o` 參數會分別對應至 MSBuild 的 `Configuration` 和 `OutputPath` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c54e3-122">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="c54e3-123">該`dotnet publish`指令接受 MSBuild`-p`選項,`-l`例如用於設定屬性 和定義記錄器。</span><span class="sxs-lookup"><span data-stu-id="c54e3-123">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="c54e3-124">例如,可以使用: 設定 MSBuild 屬性`-p:<NAME>=<VALUE>`。</span><span class="sxs-lookup"><span data-stu-id="c54e3-124">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="c54e3-125">還可以透過參考 *.pubxml*檔來設定與發佈相關的屬性,例如:</span><span class="sxs-lookup"><span data-stu-id="c54e3-125">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="c54e3-126">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="c54e3-126">For more information, see the following resources:</span></span>

- [<span data-ttu-id="c54e3-127">MSBuild 指令列參考</span><span class="sxs-lookup"><span data-stu-id="c54e3-127">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="c54e3-128">視覺化工作室發佈設定檔 (.pubxml) ASP.NET核心應用部署</span><span class="sxs-lookup"><span data-stu-id="c54e3-128">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="c54e3-129">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="c54e3-129">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="c54e3-130">引數</span><span class="sxs-lookup"><span data-stu-id="c54e3-130">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="c54e3-131">要發佈的專案或解決方案。</span><span class="sxs-lookup"><span data-stu-id="c54e3-131">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="c54e3-132">`PROJECT`是[C#、F#](csproj.md)或 Visual Basic 專案檔的路徑和檔名,或包含 C#、F# 或 Visual Basic 專案檔的目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="c54e3-132">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="c54e3-133">如果未指定目錄,則預設為當前目錄。</span><span class="sxs-lookup"><span data-stu-id="c54e3-133">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="c54e3-134">`SOLUTION`是解決方案檔 *(.sln*副檔名) 的路徑和檔名,或包含解決方案檔的目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="c54e3-134">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="c54e3-135">如果未指定目錄,則預設為當前目錄。</span><span class="sxs-lookup"><span data-stu-id="c54e3-135">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="c54e3-136">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c54e3-136">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="c54e3-137">選項。</span><span class="sxs-lookup"><span data-stu-id="c54e3-137">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="c54e3-138">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="c54e3-138">Defines the build configuration.</span></span> <span data-ttu-id="c54e3-139">大多數項目的預設值為,`Debug`但您可以覆蓋專案中的生成配置設置。</span><span class="sxs-lookup"><span data-stu-id="c54e3-139">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c54e3-140">發行所指定[目標架構](../../standard/frameworks.md)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c54e3-140">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="c54e3-141">您必須在專案檔中指定此目標架構。</span><span class="sxs-lookup"><span data-stu-id="c54e3-141">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="c54e3-142">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="c54e3-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="c54e3-143">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="c54e3-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c54e3-144">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c54e3-144">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="c54e3-145">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="c54e3-145">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="c54e3-146">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="c54e3-146">For example, to complete authentication.</span></span> <span data-ttu-id="c54e3-147">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c54e3-147">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="c54e3-148">指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。</span><span class="sxs-lookup"><span data-stu-id="c54e3-148">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="c54e3-149">清單檔是[`dotnet store`命令](dotnet-store.md)的輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="c54e3-149">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="c54e3-150">若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。</span><span class="sxs-lookup"><span data-stu-id="c54e3-150">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="c54e3-151">不會在發佈前建置專案。</span><span class="sxs-lookup"><span data-stu-id="c54e3-151">Doesn't build the project before publishing.</span></span> <span data-ttu-id="c54e3-152">選項也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="c54e3-152">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="c54e3-153">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="c54e3-153">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="c54e3-154">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="c54e3-154">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="c54e3-155">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c54e3-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c54e3-156">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c54e3-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c54e3-157">指定輸出目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="c54e3-157">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="c54e3-158">如果未指定,它預設為 *[project_file_folder]/bin/[配置]/[框架]/發佈/* 對於與運行時相關的可執行檔和跨平臺二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="c54e3-158">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="c54e3-159">它預設為 *[project_file_folder]/bin/[配置]/[框架]/[運行時]/發佈/* 獨立執行檔。</span><span class="sxs-lookup"><span data-stu-id="c54e3-159">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  - <span data-ttu-id="c54e3-160">.NET 核心 3.x SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="c54e3-160">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="c54e3-161">如果在發佈專案時指定了相對路徑,則生成的輸出目錄與當前工作目錄相關,而不是與專案檔位置相關。</span><span class="sxs-lookup"><span data-stu-id="c54e3-161">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="c54e3-162">如果在發佈解決方案時指定了相對路徑,則所有專案的所有輸出都進入相對於當前工作目錄的指定資料夾。</span><span class="sxs-lookup"><span data-stu-id="c54e3-162">If a relative path is specified when publishing a solution, all output for all projects go into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="c54e3-163">要使發佈輸出轉到每個項目的單獨資料夾,請使用 msbuild`PublishDir`屬性`--output`而不是選項 指定相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c54e3-163">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="c54e3-164">例如,`dotnet publish -p:PublishDir=.\publish`將每個項目的發佈輸出發送到包含專案檔`publish`的 資料夾下的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c54e3-164">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="c54e3-165">.NET 核心 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="c54e3-165">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="c54e3-166">如果在發佈專案時指定了相對路徑,則生成的輸出目錄相對於專案檔位置,而不是當前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="c54e3-166">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="c54e3-167">如果在發佈解決方案時指定了相對路徑,則每個項目的輸出將相對於專案檔位置進入一個單獨的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c54e3-167">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="c54e3-168">如果在發佈解決方案時指定了絕對路徑,則所有專案的發佈輸出都將進入指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c54e3-168">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="c54e3-169">使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。</span><span class="sxs-lookup"><span data-stu-id="c54e3-169">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="c54e3-170">預設值是`true`指定運行時識別碼,並且專案是可執行專案(不是庫專案)。</span><span class="sxs-lookup"><span data-stu-id="c54e3-170">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="c54e3-171">有關詳細資訊,請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="c54e3-171">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="c54e3-172">如果使用這個選項不指定`true``false`或 ,則預設`true`值為 。</span><span class="sxs-lookup"><span data-stu-id="c54e3-172">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="c54e3-173">在這種情況下,不要立即將解決方案或專案參數放在`--self-contained`之後,`true`因為`false`或預期處於該位置。</span><span class="sxs-lookup"><span data-stu-id="c54e3-173">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="c54e3-174">相當於 `--self-contained false`。</span><span class="sxs-lookup"><span data-stu-id="c54e3-174">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="c54e3-175">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c54e3-175">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c54e3-176">發行所指定執行階段的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c54e3-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="c54e3-177">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="c54e3-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="c54e3-178">有關詳細資訊,請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="c54e3-178">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c54e3-179">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="c54e3-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c54e3-180">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="c54e3-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c54e3-181">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="c54e3-181">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="c54e3-182">定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="c54e3-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="c54e3-183">範例</span><span class="sxs-lookup"><span data-stu-id="c54e3-183">Examples</span></span>

- <span data-ttu-id="c54e3-184">建立目前目錄中的項目建立[與執行時相關的跨平台二進位檔案](../deploying/index.md#produce-a-cross-platform-binary):</span><span class="sxs-lookup"><span data-stu-id="c54e3-184">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="c54e3-185">從 .NET Core 3.0 SDK 開始,此範例還會為目前平台建立[與執行時相關的可執行檔](../deploying/index.md#publish-runtime-dependent)。</span><span class="sxs-lookup"><span data-stu-id="c54e3-185">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="c54e3-186">為目前的目錄中建立的項目為特定執行時建立[自包含可執行檔](../deploying/index.md#publish-self-contained):</span><span class="sxs-lookup"><span data-stu-id="c54e3-186">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="c54e3-187">RID 必須位於項目檔中。</span><span class="sxs-lookup"><span data-stu-id="c54e3-187">The RID must be in the project file.</span></span>

- <span data-ttu-id="c54e3-188">為目前目錄中的項目為特定平台建立[與執行時相關的執行檔](../deploying/index.md#publish-runtime-dependent):</span><span class="sxs-lookup"><span data-stu-id="c54e3-188">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="c54e3-189">RID 必須位於項目檔中。</span><span class="sxs-lookup"><span data-stu-id="c54e3-189">The RID must be in the project file.</span></span> <span data-ttu-id="c54e3-190">此範例適用於 .NET Core 3.0 SDK 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="c54e3-190">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="c54e3-191">在目前的目錄中發行項目,用於特定執行時和目標框架:</span><span class="sxs-lookup"><span data-stu-id="c54e3-191">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="c54e3-192">發佈指定的項目檔:</span><span class="sxs-lookup"><span data-stu-id="c54e3-192">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="c54e3-193">發佈目前的應用程式,但不還原專案到專案 (P2P) 引用,只是還原操作期間的根專案:</span><span class="sxs-lookup"><span data-stu-id="c54e3-193">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="c54e3-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c54e3-194">See also</span></span>

- [<span data-ttu-id="c54e3-195">.NET 核心應用程式發佈概述</span><span class="sxs-lookup"><span data-stu-id="c54e3-195">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="c54e3-196">使用 .NET 核心 CLI 發佈 .NET 核心應用</span><span class="sxs-lookup"><span data-stu-id="c54e3-196">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="c54e3-197">目標框架</span><span class="sxs-lookup"><span data-stu-id="c54e3-197">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="c54e3-198">執行時識別器 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="c54e3-198">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="c54e3-199">使用 macOS Catalina 公證</span><span class="sxs-lookup"><span data-stu-id="c54e3-199">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="c54e3-200">已發布應用程式的目錄結構</span><span class="sxs-lookup"><span data-stu-id="c54e3-200">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="c54e3-201">MSBuild 指令列參考</span><span class="sxs-lookup"><span data-stu-id="c54e3-201">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="c54e3-202">視覺化工作室發佈設定檔 (.pubxml) ASP.NET核心應用部署</span><span class="sxs-lookup"><span data-stu-id="c54e3-202">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="c54e3-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="c54e3-203">dotnet msbuild</span></span>](dotnet-msbuild.md)
