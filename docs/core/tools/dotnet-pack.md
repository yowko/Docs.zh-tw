---
title: dotnet pack 命令
description: dotnet pack 命令會建立 .NET Core 專案的 NuGet 套件。
ms.date: 12/04/2018
ms.openlocfilehash: 4b665140f7c660c5851fb68b07ecec2d9391b925
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464472"
---
# <a name="dotnet-pack"></a><span data-ttu-id="0af41-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0af41-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0af41-104">名稱</span><span class="sxs-lookup"><span data-stu-id="0af41-104">Name</span></span>

<span data-ttu-id="0af41-105">`dotnet pack` - 將程式碼封裝到 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="0af41-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0af41-106">概要</span><span class="sxs-lookup"><span data-stu-id="0af41-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0af41-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0af41-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0af41-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0af41-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="0af41-109">說明</span><span class="sxs-lookup"><span data-stu-id="0af41-109">Description</span></span>

<span data-ttu-id="0af41-110">`dotnet pack` 命令會建置專案，並建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="0af41-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="0af41-111">此命令的結果是 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="0af41-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="0af41-112">如果有 `--include-symbols` 選項，會建立另一個包含偵錯符號的套件。</span><span class="sxs-lookup"><span data-stu-id="0af41-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="0af41-113">封裝專案的 NuGet 相依性會新增至 *.nuspec* 檔案，因此在安裝套件時可以正確地解析它們。</span><span class="sxs-lookup"><span data-stu-id="0af41-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="0af41-114">專案對專案參考不會封裝到專案內。</span><span class="sxs-lookup"><span data-stu-id="0af41-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="0af41-115">目前，如果您有專案對專案相依性，則必須一個專案各一個套件。</span><span class="sxs-lookup"><span data-stu-id="0af41-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="0af41-116">`dotnet pack` 預設會先建置專案。</span><span class="sxs-lookup"><span data-stu-id="0af41-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="0af41-117">如果您想要避免這種行為，請傳遞 `--no-build` 選項。</span><span class="sxs-lookup"><span data-stu-id="0af41-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="0af41-118">這個選項通常適用於您知道先前剛建立程式碼的持續整合 (CI) 組建案例。</span><span class="sxs-lookup"><span data-stu-id="0af41-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="0af41-119">您可以提供 MSBuild 屬性給 `dotnet pack` 命令來壓縮程序。</span><span class="sxs-lookup"><span data-stu-id="0af41-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="0af41-120">如需詳細資訊，請參閱 [NuGet 中繼資料屬性](csproj.md#nuget-metadata-properties)和 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="0af41-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="0af41-121">[範例](#examples)一節示範針對數個不同案例使用 MSBuild -p 參數的方法。</span><span class="sxs-lookup"><span data-stu-id="0af41-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="0af41-122">引數</span><span class="sxs-lookup"><span data-stu-id="0af41-122">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="0af41-123">要封裝的專案。</span><span class="sxs-lookup"><span data-stu-id="0af41-123">The project to pack.</span></span> <span data-ttu-id="0af41-124">它可以是 [csproj 檔案](csproj.md)或目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="0af41-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="0af41-125">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="0af41-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="0af41-126">選項</span><span class="sxs-lookup"><span data-stu-id="0af41-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0af41-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0af41-127">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="0af41-128">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="0af41-128">Defines the build configuration.</span></span> <span data-ttu-id="0af41-129">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="0af41-129">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="0af41-130">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="0af41-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="0af41-131">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="0af41-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0af41-132">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="0af41-132">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="0af41-133">將原始程式檔納入 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="0af41-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="0af41-134">原始程式檔包含在 `nupkg` 中的 `src` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0af41-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="0af41-135">產生符號 `nupkg`。</span><span class="sxs-lookup"><span data-stu-id="0af41-135">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="0af41-136">不會在封裝前建置專案。</span><span class="sxs-lookup"><span data-stu-id="0af41-136">Doesn't build the project before packing.</span></span> <span data-ttu-id="0af41-137">選項也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="0af41-137">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="0af41-138">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="0af41-138">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="0af41-139">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="0af41-139">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="0af41-140">將已建置的套件放置在指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0af41-140">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="0af41-141">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="0af41-141">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="0af41-142">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="0af41-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="0af41-143">在套件中設定可提供服務的旗標。</span><span class="sxs-lookup"><span data-stu-id="0af41-143">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="0af41-144">如需詳細資訊，請參閱 [.NET 部落格︰.NET 4.5.1 支援適用於 .NET NuGet 程式庫的 Microsoft 安全性更新 (英文)](https://aka.ms/nupkgservicing)。</span><span class="sxs-lookup"><span data-stu-id="0af41-144">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="0af41-145">在專案中定義 `$(VersionSuffix)` MSBuild 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0af41-145">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0af41-146">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="0af41-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0af41-147">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0af41-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

> [!NOTE]
> <span data-ttu-id="0af41-148">Web 專案預設無法封裝。</span><span class="sxs-lookup"><span data-stu-id="0af41-148">Web projects aren't packable by default.</span></span> <span data-ttu-id="0af41-149">若要覆寫預設行為，請將下列屬性新增至您的 .csproj 檔案：</span><span class="sxs-lookup"><span data-stu-id="0af41-149">To override the default behavior, add the following property to your *.csproj* file:</span></span>
> ```xml
> <PropertyGroup>
>    <IsPackable>true</IsPackable>
> </PropertyGroup>
> ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0af41-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0af41-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="0af41-151">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="0af41-151">Defines the build configuration.</span></span> <span data-ttu-id="0af41-152">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="0af41-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0af41-153">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="0af41-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="0af41-154">將原始程式檔納入 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="0af41-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="0af41-155">原始程式檔包含在 `nupkg` 中的 `src` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0af41-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="0af41-156">產生符號 `nupkg`。</span><span class="sxs-lookup"><span data-stu-id="0af41-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="0af41-157">不會在封裝前建置專案。</span><span class="sxs-lookup"><span data-stu-id="0af41-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="0af41-158">將已建置的套件放置在指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0af41-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="0af41-159">在套件中設定可提供服務的旗標。</span><span class="sxs-lookup"><span data-stu-id="0af41-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="0af41-160">如需詳細資訊，請參閱 [.NET 部落格︰.NET 4.5.1 支援適用於 .NET NuGet 程式庫的 Microsoft 安全性更新 (英文)](https://aka.ms/nupkgservicing)。</span><span class="sxs-lookup"><span data-stu-id="0af41-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="0af41-161">在專案中定義 `$(VersionSuffix)` MSBuild 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0af41-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0af41-162">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="0af41-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0af41-163">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="0af41-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="0af41-164">範例</span><span class="sxs-lookup"><span data-stu-id="0af41-164">Examples</span></span>

* <span data-ttu-id="0af41-165">封裝目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="0af41-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="0af41-166">封裝 `app1` 專案：</span><span class="sxs-lookup"><span data-stu-id="0af41-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="0af41-167">封裝目前目錄中的專案，並將產生的套件放置到 `nupkgs` 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="0af41-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="0af41-168">將目前目錄中的專案封裝到 `nupkgs` 資料夾，並略過建置步驟︰</span><span class="sxs-lookup"><span data-stu-id="0af41-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="0af41-169">在 *.csproj* 檔案中將專案的版本尾碼設定為 `<VersionSuffix>$(VersionSuffix)</VersionSuffix>`，封裝目前的專案並使用指定尾碼更新產生的套件版本︰</span><span class="sxs-lookup"><span data-stu-id="0af41-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="0af41-170">使用 `PackageVersion` MSBuild 屬性將封裝版本設定為 `2.1.0`：</span><span class="sxs-lookup"><span data-stu-id="0af41-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="0af41-171">將專案針對特定[目標 Framework](../../standard/frameworks.md) 進行封裝：</span><span class="sxs-lookup"><span data-stu-id="0af41-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="0af41-172">封裝專案，並使用特定的執行階段 (Windows 10) 進行還原作業 (.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="0af41-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="0af41-173">使用 [.nuspec 檔案](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)來封裝專案：</span><span class="sxs-lookup"><span data-stu-id="0af41-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack  ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
