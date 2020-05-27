---
title: dotnet restore 命令
description: 了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。
ms.date: 02/27/2020
ms.openlocfilehash: 29f81b09a01e689d3f6d86c16b1f134c9fe6b6a0
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840932"
---
# <a name="dotnet-restore"></a><span data-ttu-id="42d48-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="42d48-103">dotnet restore</span></span>

<span data-ttu-id="42d48-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="42d48-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="42d48-105">名稱</span><span class="sxs-lookup"><span data-stu-id="42d48-105">Name</span></span>

<span data-ttu-id="42d48-106">`dotnet restore` - 還原專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="42d48-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="42d48-107">概要</span><span class="sxs-lookup"><span data-stu-id="42d48-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="42d48-108">描述</span><span class="sxs-lookup"><span data-stu-id="42d48-108">Description</span></span>

<span data-ttu-id="42d48-109">`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。</span><span class="sxs-lookup"><span data-stu-id="42d48-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="42d48-110">在大部分情況下，您不需要明確地使用 `dotnet restore` 命令，因為當您執行下列命令時，會隱含地執行 NuGet 還原：</span><span class="sxs-lookup"><span data-stu-id="42d48-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="42d48-111">有時候，使用這些命令來執行隱含的 NuGet 還原可能不太方便。</span><span class="sxs-lookup"><span data-stu-id="42d48-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="42d48-112">例如，某些自動化系統，像是建置系統，必須明確呼叫 `dotnet restore` 以控制還原發生的時間，進而控制網路使用量。</span><span class="sxs-lookup"><span data-stu-id="42d48-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="42d48-113">若要防止隱含的 NuGet 還原，您可以使用 `--no-restore` 旗標搭配任何這些命令來停用隱含還原。</span><span class="sxs-lookup"><span data-stu-id="42d48-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="42d48-114">指定摘要</span><span class="sxs-lookup"><span data-stu-id="42d48-114">Specify feeds</span></span>

<span data-ttu-id="42d48-115">若要還原相依性，NuGet 需要套件所在的摘要。</span><span class="sxs-lookup"><span data-stu-id="42d48-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="42d48-116">摘要通常透過 *nuget.config* 組態檔提供。</span><span class="sxs-lookup"><span data-stu-id="42d48-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="42d48-117">安裝 .NET Core SDK 時，會提供預設的設定檔案。</span><span class="sxs-lookup"><span data-stu-id="42d48-117">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="42d48-118">若要指定其他摘要，請執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="42d48-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="42d48-119">在專案目錄中建立您自己的*nuget .config*檔案。</span><span class="sxs-lookup"><span data-stu-id="42d48-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="42d48-120">如需詳細資訊，請參閱本文稍後的[一般 nuget](/nuget/consume-packages/configuring-nuget-behavior)設定和[nuget .config 差異](#nugetconfig-differences)。</span><span class="sxs-lookup"><span data-stu-id="42d48-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="42d48-121">使用 `dotnet nuget` 之類的命令 [`dotnet nuget add source`](dotnet-nuget-add-source.md) 。</span><span class="sxs-lookup"><span data-stu-id="42d48-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="42d48-122">您可以使用選項覆寫*nuget .config*摘要。 `-s`</span><span class="sxs-lookup"><span data-stu-id="42d48-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="42d48-123">如需如何使用已驗證摘要的相關資訊，請參閱[從已驗證](/nuget/consume-packages/consuming-packages-authenticated-feeds)的摘要取用套件。</span><span class="sxs-lookup"><span data-stu-id="42d48-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="42d48-124">全域封裝資料夾</span><span class="sxs-lookup"><span data-stu-id="42d48-124">Global packages folder</span></span>

<span data-ttu-id="42d48-125">針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。</span><span class="sxs-lookup"><span data-stu-id="42d48-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="42d48-126">如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="42d48-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="42d48-127">例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*。</span><span class="sxs-lookup"><span data-stu-id="42d48-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="42d48-128">專案特定工具</span><span class="sxs-lookup"><span data-stu-id="42d48-128">Project-specific tooling</span></span>

<span data-ttu-id="42d48-129">針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。</span><span class="sxs-lookup"><span data-stu-id="42d48-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="42d48-130">nuget.config 差異</span><span class="sxs-lookup"><span data-stu-id="42d48-130">nuget.config differences</span></span>

<span data-ttu-id="42d48-131">*nuget.config* 檔案中設定 (如果有的話) 會影響 `dotnet restore` 命令的行為。</span><span class="sxs-lookup"><span data-stu-id="42d48-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="42d48-132">例如，在 *nuget.config* 中設定 `globalPackagesFolder` 會將還原的 NuGet 套件置於所指定資料夾。</span><span class="sxs-lookup"><span data-stu-id="42d48-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="42d48-133">這是在 `dotnet restore` 命令上指定 `--packages` 選項的替代方式。</span><span class="sxs-lookup"><span data-stu-id="42d48-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="42d48-134">如需詳細資訊，請參閱 [nuget.config 參考](/nuget/schema/nuget-config-file)。</span><span class="sxs-lookup"><span data-stu-id="42d48-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="42d48-135">`dotnet restore` 會忽略三個特定設定：</span><span class="sxs-lookup"><span data-stu-id="42d48-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="42d48-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="42d48-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="42d48-137">繫結重新導向不適用於 `<PackageReference>` 元素，且 .NET Core 針對 NuGet 套件僅支援 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="42d48-137">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="42d48-138">解</span><span class="sxs-lookup"><span data-stu-id="42d48-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="42d48-139">這是 Visual Studio 特定設定，不適用於 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="42d48-139">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="42d48-140">.Net Core 不會使用 `packages.config` 檔案，而是針對 NuGet 套件使用 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="42d48-140">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="42d48-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="42d48-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="42d48-142">此設定不適用，因為 [NuGet 尚未支援信任套件的跨平臺驗證](https://github.com/NuGet/Home/issues/7939)。</span><span class="sxs-lookup"><span data-stu-id="42d48-142">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="arguments"></a><span data-ttu-id="42d48-143">引數</span><span class="sxs-lookup"><span data-stu-id="42d48-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="42d48-144">要還原之專案檔的選用路徑。</span><span class="sxs-lookup"><span data-stu-id="42d48-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="42d48-145">選項</span><span class="sxs-lookup"><span data-stu-id="42d48-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="42d48-146">要用於還原作業的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="42d48-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="42d48-147">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="42d48-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="42d48-148">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="42d48-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="42d48-149">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="42d48-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="42d48-150">強制還原以重新評估所有相依性，即使鎖定檔案已經存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="42d48-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="42d48-151">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="42d48-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="42d48-152">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="42d48-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="42d48-153">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="42d48-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="42d48-154">自 .NET Core 2.1.400 起。</span><span class="sxs-lookup"><span data-stu-id="42d48-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="42d48-155">寫入專案鎖定檔案的輸出位置。</span><span class="sxs-lookup"><span data-stu-id="42d48-155">Output location where project lock file is written.</span></span> <span data-ttu-id="42d48-156">根據預設，這會是*PROJECT_ROOT \packages.lock.json*。</span><span class="sxs-lookup"><span data-stu-id="42d48-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="42d48-157">不允許更新專案鎖定檔案。</span><span class="sxs-lookup"><span data-stu-id="42d48-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="42d48-158">指定不快取 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="42d48-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="42d48-159">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="42d48-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="42d48-160">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="42d48-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="42d48-161">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="42d48-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="42d48-162">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="42d48-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="42d48-163">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="42d48-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="42d48-164">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="42d48-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="42d48-165">指定要在還原作業期間使用的 NuGet 套件來源 URI。</span><span class="sxs-lookup"><span data-stu-id="42d48-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="42d48-166">此設定會覆寫*nuget.exe*檔案中指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="42d48-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="42d48-167">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="42d48-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="42d48-168">讓專案鎖定檔案能夠產生並搭配 restore 使用。</span><span class="sxs-lookup"><span data-stu-id="42d48-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="42d48-169">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="42d48-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="42d48-170">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="42d48-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="42d48-171">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="42d48-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="42d48-172">範例</span><span class="sxs-lookup"><span data-stu-id="42d48-172">Examples</span></span>

- <span data-ttu-id="42d48-173">還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="42d48-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="42d48-174">還原在 `app1` 指定路徑中找到之專案的相依性和工具：</span><span class="sxs-lookup"><span data-stu-id="42d48-174">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="42d48-175">使用提供作為來源的檔案路徑，還原目前目錄中專案的相依性和工具：</span><span class="sxs-lookup"><span data-stu-id="42d48-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="42d48-176">使用提供做為來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具：</span><span class="sxs-lookup"><span data-stu-id="42d48-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="42d48-177">還原目前目錄中專案的相依性和工具，顯示詳細輸出：</span><span class="sxs-lookup"><span data-stu-id="42d48-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
