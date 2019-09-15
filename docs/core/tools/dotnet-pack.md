---
title: dotnet pack 命令
description: dotnet pack 命令會建立 .NET Core 專案的 NuGet 套件。
ms.date: 08/08/2019
ms.openlocfilehash: ba5a438d58963222c3fa55d2c585ef503dcd49db
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990415"
---
# <a name="dotnet-pack"></a><span data-ttu-id="18596-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="18596-103">dotnet pack</span></span>

<span data-ttu-id="18596-104">**本主題適用於：✓** .NET Core 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="18596-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="18596-105">名稱</span><span class="sxs-lookup"><span data-stu-id="18596-105">Name</span></span>

<span data-ttu-id="18596-106">`dotnet pack` - 將程式碼封裝到 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="18596-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="18596-107">概要</span><span class="sxs-lookup"><span data-stu-id="18596-107">Synopsis</span></span>

```console
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive] 
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable] 
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="18596-108">描述</span><span class="sxs-lookup"><span data-stu-id="18596-108">Description</span></span>

<span data-ttu-id="18596-109">`dotnet pack` 命令會建置專案，並建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="18596-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="18596-110">此命令的結果是 NuGet 套件（也就是*nupkg*檔案）。</span><span class="sxs-lookup"><span data-stu-id="18596-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span> 

<span data-ttu-id="18596-111">如果您想要產生包含 debug 符號的封裝，您有兩個可用的選項：</span><span class="sxs-lookup"><span data-stu-id="18596-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="18596-112">`--include-symbols`-它會建立符號套件。</span><span class="sxs-lookup"><span data-stu-id="18596-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="18596-113">`--include-source`-它會建立符號套件，並`src`在其中包含來源檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="18596-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="18596-114">封裝專案的 NuGet 相依性會新增至 *.nuspec* 檔案，因此在安裝套件時可以正確地解析它們。</span><span class="sxs-lookup"><span data-stu-id="18596-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="18596-115">專案對專案參考不會封裝到專案內。</span><span class="sxs-lookup"><span data-stu-id="18596-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="18596-116">目前，如果您有專案對專案相依性，則必須一個專案各一個套件。</span><span class="sxs-lookup"><span data-stu-id="18596-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="18596-117">`dotnet pack` 預設會先建置專案。</span><span class="sxs-lookup"><span data-stu-id="18596-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="18596-118">如果您想要避免這種行為，請傳遞 `--no-build` 選項。</span><span class="sxs-lookup"><span data-stu-id="18596-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="18596-119">這個選項通常適用於您知道先前剛建立程式碼的持續整合 (CI) 組建案例。</span><span class="sxs-lookup"><span data-stu-id="18596-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="18596-120">您可以提供 MSBuild 屬性給 `dotnet pack` 命令來壓縮程序。</span><span class="sxs-lookup"><span data-stu-id="18596-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="18596-121">如需詳細資訊，請參閱 [NuGet 中繼資料屬性](csproj.md#nuget-metadata-properties)和 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="18596-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="18596-122">[範例](#examples)一節示範針對數個不同案例使用 MSBuild -p 參數的方法。</span><span class="sxs-lookup"><span data-stu-id="18596-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="18596-123">Web 專案預設無法封裝。</span><span class="sxs-lookup"><span data-stu-id="18596-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="18596-124">若要覆寫預設行為，請將下列屬性新增至您的 .csproj 檔案：</span><span class="sxs-lookup"><span data-stu-id="18596-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="18596-125">引數</span><span class="sxs-lookup"><span data-stu-id="18596-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="18596-126">要包裝的專案或方案。</span><span class="sxs-lookup"><span data-stu-id="18596-126">The project or solution to pack.</span></span> <span data-ttu-id="18596-127">它是[.csproj](csproj.md)檔案、方案檔或目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="18596-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="18596-128">如果未指定，命令會在目前的目錄中搜尋專案或方案檔。</span><span class="sxs-lookup"><span data-stu-id="18596-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="18596-129">選項</span><span class="sxs-lookup"><span data-stu-id="18596-129">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="18596-130">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="18596-130">Defines the build configuration.</span></span> <span data-ttu-id="18596-131">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="18596-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="18596-132">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="18596-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="18596-133">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="18596-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="18596-134">自 .NET Core 2.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="18596-134">Option available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="18596-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="18596-135">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="18596-136">除了輸出目錄中的一般 NuGet 套件外，還包含 debug 符號 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="18596-136">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="18596-137">來源檔案會包含在符號封裝`src`內的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="18596-137">The sources files are included in the `src` folder within the symbols package.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="18596-138">除了輸出目錄中的一般 NuGet 套件外，還包含 debug 符號 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="18596-138">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

* **`--interactive`**

  <span data-ttu-id="18596-139">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="18596-139">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="18596-140">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="18596-140">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-build`**

  <span data-ttu-id="18596-141">不會在封裝前建置專案。</span><span class="sxs-lookup"><span data-stu-id="18596-141">Doesn't build the project before packing.</span></span> <span data-ttu-id="18596-142">選項也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="18596-142">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="18596-143">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="18596-143">Ignores project-to-project references and only restores the root project.</span></span> <span data-ttu-id="18596-144">自 .NET Core 2.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="18596-144">Option available since .NET Core 2.0 SDK.</span></span>

* **`--no-restore`**

  <span data-ttu-id="18596-145">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="18596-145">Doesn't execute an implicit restore when running the command.</span></span> <span data-ttu-id="18596-146">自 .NET Core 2.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="18596-146">Option available since .NET Core 2.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="18596-147">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="18596-147">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="18596-148">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="18596-148">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="18596-149">將已建置的套件放置在指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="18596-149">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="18596-150">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="18596-150">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="18596-151">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="18596-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="18596-152">自 .NET Core 2.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="18596-152">Option available since .NET Core 2.0 SDK.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="18596-153">在套件中設定可提供服務的旗標。</span><span class="sxs-lookup"><span data-stu-id="18596-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="18596-154">如需詳細資訊，請參閱 [.NET 部落格︰.NET 4.5.1 支援適用於 .NET NuGet 程式庫的 Microsoft 安全性更新 (英文)](https://aka.ms/nupkgservicing)。</span><span class="sxs-lookup"><span data-stu-id="18596-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="18596-155">在專案中定義 `$(VersionSuffix)` MSBuild 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="18596-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="18596-156">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="18596-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="18596-157">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="18596-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="18596-158">範例</span><span class="sxs-lookup"><span data-stu-id="18596-158">Examples</span></span>

* <span data-ttu-id="18596-159">封裝目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="18596-159">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="18596-160">封裝 `app1` 專案：</span><span class="sxs-lookup"><span data-stu-id="18596-160">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="18596-161">封裝目前目錄中的專案，並將產生的套件放置到 `nupkgs` 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="18596-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="18596-162">將目前目錄中的專案封裝到 `nupkgs` 資料夾，並略過建置步驟︰</span><span class="sxs-lookup"><span data-stu-id="18596-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="18596-163">在 *.csproj* 檔案中將專案的版本尾碼設定為 `<VersionSuffix>$(VersionSuffix)</VersionSuffix>`，封裝目前的專案並使用指定尾碼更新產生的套件版本︰</span><span class="sxs-lookup"><span data-stu-id="18596-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="18596-164">使用 `PackageVersion` MSBuild 屬性將封裝版本設定為 `2.1.0`：</span><span class="sxs-lookup"><span data-stu-id="18596-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="18596-165">將專案針對特定[目標 Framework](../../standard/frameworks.md) 進行封裝：</span><span class="sxs-lookup"><span data-stu-id="18596-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="18596-166">封裝專案，並使用特定的執行階段 (Windows 10) 進行還原作業 (.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="18596-166">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="18596-167">使用 [.nuspec 檔案](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)來封裝專案：</span><span class="sxs-lookup"><span data-stu-id="18596-167">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
