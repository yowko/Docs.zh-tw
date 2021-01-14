---
title: dotnet pack 命令
description: Dotnet pack 命令會建立 .NET 專案的 NuGet 套件。
ms.date: 04/28/2020
ms.openlocfilehash: a9a634c358f5de4f28c3de06edc9a2b4d2eb8d57
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190074"
---
# <a name="dotnet-pack"></a><span data-ttu-id="2a8e4-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="2a8e4-103">dotnet pack</span></span>

<span data-ttu-id="2a8e4-104">本文 **適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2a8e4-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2a8e4-105">名稱</span><span class="sxs-lookup"><span data-stu-id="2a8e4-105">Name</span></span>

<span data-ttu-id="2a8e4-106">`dotnet pack` - 將程式碼封裝到 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2a8e4-107">概要</span><span class="sxs-lookup"><span data-stu-id="2a8e4-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="2a8e4-108">Description</span><span class="sxs-lookup"><span data-stu-id="2a8e4-108">Description</span></span>

<span data-ttu-id="2a8e4-109">`dotnet pack` 命令會建置專案，並建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="2a8e4-110">此命令的結果是 NuGet 套件 (也就是 *nupkg* 檔案) 。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="2a8e4-111">如果您想要產生包含 debug 符號的封裝，您有兩個可用的選項：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="2a8e4-112">`--include-symbols` -它會建立符號套件。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="2a8e4-113">`--include-source` -它會在包含來源檔案的 `src` 資料夾內建立符號套件。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="2a8e4-114">封裝專案的 NuGet 相依性會新增至 *.nuspec* 檔案，因此在安裝套件時可以正確地解析它們。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="2a8e4-115">專案對專案參考不會封裝到專案內。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="2a8e4-116">目前，如果您有專案對專案相依性，則必須一個專案各一個套件。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="2a8e4-117">`dotnet pack` 預設會先建置專案。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="2a8e4-118">如果您想要避免這種行為，請傳遞 `--no-build` 選項。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="2a8e4-119">這個選項通常適用於您知道先前剛建立程式碼的持續整合 (CI) 組建案例。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="2a8e4-120">在某些情況下，無法執行隱含組建。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="2a8e4-121">當設定時，就會發生這種情況 `GeneratePackageOnBuild` ，以避免組建和套件目標之間有迴圈相依性。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="2a8e4-122">如果有鎖定的檔案或其他問題，組建也會失敗。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="2a8e4-123">您可以提供 MSBuild 屬性給 `dotnet pack` 命令來壓縮程序。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="2a8e4-124">如需詳細資訊，請參閱 [NuGet 套件目標屬性](/nuget/reference/msbuild-targets#pack-target) 和 [MSBuild Command-Line 參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-124">For more information, see [NuGet pack target properties](/nuget/reference/msbuild-targets#pack-target) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="2a8e4-125">[範例](#examples)一節會示範如何在 `-p` 幾個不同的案例中使用 MSBuild 參數。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-125">The [Examples](#examples) section shows how to use the MSBuild `-p` switch for a couple of different scenarios.</span></span>

<span data-ttu-id="2a8e4-126">Web 專案預設無法封裝。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="2a8e4-127">若要覆寫預設行為，請將下列屬性新增至您的 .csproj 檔案：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="2a8e4-128">隱含還原</span><span class="sxs-lookup"><span data-stu-id="2a8e4-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="2a8e4-129">引數</span><span class="sxs-lookup"><span data-stu-id="2a8e4-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="2a8e4-130">要封裝的專案或方案。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-130">The project or solution to pack.</span></span> <span data-ttu-id="2a8e4-131">它可以是 .csproj、vbproj 或 >.fsproj 檔案的路徑，也可以是方案檔或目錄。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-131">It's either a path to a csproj, vbproj, or fsproj file, or to a solution file or directory.</span></span> <span data-ttu-id="2a8e4-132">如果未指定，命令會在目前的目錄中搜尋專案或方案檔。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="2a8e4-133">選項</span><span class="sxs-lookup"><span data-stu-id="2a8e4-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="2a8e4-134">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-134">Defines the build configuration.</span></span> <span data-ttu-id="2a8e4-135">大部分專案的預設值為 `Debug` ，但您可以覆寫專案中的組建設定。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="2a8e4-136">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2a8e4-137">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2a8e4-138">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="2a8e4-139">除了輸出目錄中的一般 NuGet 套件之外，還包括 NuGet 套件的 debug 符號。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="2a8e4-140">來源檔案會包含在 `src` 符號套件內的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="2a8e4-141">除了輸出目錄中的一般 NuGet 套件之外，還包括 NuGet 套件的 debug 符號。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="2a8e4-142">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="2a8e4-143">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="2a8e4-144">不會在封裝前建置專案。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="2a8e4-145">選項也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="2a8e4-146">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2a8e4-147">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="2a8e4-148">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="2a8e4-149">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="2a8e4-150">將已建置的套件放置在指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="2a8e4-151">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="2a8e4-152">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="2a8e4-153">在套件中設定可提供服務的旗標。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="2a8e4-154">如需詳細資訊，請參閱 [.Net Blog： .NET Framework 4.5.1 支援適用于 .Net NuGet 程式庫的 Microsoft 安全性更新](https://aka.ms/nupkgservicing)。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-154">For more information, see [.NET Blog: .NET Framework 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="2a8e4-155">在專案中定義 `$(VersionSuffix)` MSBuild 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2a8e4-156">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2a8e4-157">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="2a8e4-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="2a8e4-158">範例</span><span class="sxs-lookup"><span data-stu-id="2a8e4-158">Examples</span></span>

- <span data-ttu-id="2a8e4-159">封裝目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="2a8e4-160">封裝 `app1` 專案：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="2a8e4-161">封裝目前目錄中的專案，並將產生的套件放置到 `nupkgs` 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="2a8e4-162">將目前目錄中的專案封裝到 `nupkgs` 資料夾，並略過建置步驟︰</span><span class="sxs-lookup"><span data-stu-id="2a8e4-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="2a8e4-163">在 *.csproj* 檔案中將專案的版本尾碼設定為 `<VersionSuffix>$(VersionSuffix)</VersionSuffix>`，封裝目前的專案並使用指定尾碼更新產生的套件版本︰</span><span class="sxs-lookup"><span data-stu-id="2a8e4-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="2a8e4-164">使用 `PackageVersion` MSBuild 屬性將封裝版本設定為 `2.1.0`：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="2a8e4-165">將專案針對特定[目標 Framework](../../standard/frameworks.md) 進行封裝：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="2a8e4-166">封裝專案，並使用特定執行時間 (Windows 10) 進行還原作業：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="2a8e4-167">使用 *nuspec* 檔案套件專案：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-167">Pack the project using a *.nuspec* file:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```

  <span data-ttu-id="2a8e4-168">如需如何使用、和的詳細資訊 `NuspecFile` `NuspecBasePath` `NuspecProperties` ，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="2a8e4-168">For information about how to use `NuspecFile`, `NuspecBasePath`, and `NuspecProperties`, see the following resources:</span></span>

  - [<span data-ttu-id="2a8e4-169">使用 .nuspec 封裝</span><span class="sxs-lookup"><span data-stu-id="2a8e4-169">Packing using a .nuspec</span></span>](/nuget/reference/msbuild-targets#packing-using-a-nuspec)
  - [<span data-ttu-id="2a8e4-170">用來建立自訂套件的 Advanced 擴充點</span><span class="sxs-lookup"><span data-stu-id="2a8e4-170">Advanced extension points to create customized package</span></span>](/nuget/reference/msbuild-targets#advanced-extension-points-to-create-customized-package)
  - [<span data-ttu-id="2a8e4-171">全域屬性</span><span class="sxs-lookup"><span data-stu-id="2a8e4-171">Global properties</span></span>](/visualstudio/msbuild/msbuild-properties#global-properties)
