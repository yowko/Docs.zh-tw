---
title: dotnet restore 命令
description: 了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。
ms.date: 02/27/2020
ms.openlocfilehash: 3deef68a9bcee389a52291c72e7e1a1019a739fd
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102784"
---
# <a name="dotnet-restore"></a><span data-ttu-id="1172a-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="1172a-103">dotnet restore</span></span>

<span data-ttu-id="1172a-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="1172a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1172a-105">名稱</span><span class="sxs-lookup"><span data-stu-id="1172a-105">Name</span></span>

<span data-ttu-id="1172a-106">`dotnet restore` - 還原專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="1172a-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1172a-107">概要</span><span class="sxs-lookup"><span data-stu-id="1172a-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="1172a-108">描述</span><span class="sxs-lookup"><span data-stu-id="1172a-108">Description</span></span>

<span data-ttu-id="1172a-109">`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。</span><span class="sxs-lookup"><span data-stu-id="1172a-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="1172a-110">預設會平行執行相依性和工具的還原。</span><span class="sxs-lookup"><span data-stu-id="1172a-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="1172a-111">指定來源</span><span class="sxs-lookup"><span data-stu-id="1172a-111">Specify feeds</span></span>

<span data-ttu-id="1172a-112">若要還原相依性，NuGet 需要套件所在的摘要。</span><span class="sxs-lookup"><span data-stu-id="1172a-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="1172a-113">摘要通常透過 *nuget.config* 組態檔提供。</span><span class="sxs-lookup"><span data-stu-id="1172a-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="1172a-114">安裝 .NET 核心 SDK 時提供預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="1172a-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="1172a-115">要指定其他來源,請執行以下操作之一:</span><span class="sxs-lookup"><span data-stu-id="1172a-115">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="1172a-116">在項目目錄中建立自己的*nuget.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="1172a-116">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="1172a-117">有關詳細資訊,請參閱本文後面的[常見 NuGet 設定](/nuget/consume-packages/configuring-nuget-behavior)和[nuget.config 差異](#nugetconfig-differences)。</span><span class="sxs-lookup"><span data-stu-id="1172a-117">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="1172a-118">使用`dotnet nuget`指令[`dotnet nuget add source`](dotnet-nuget-add-source.md)( 如 )</span><span class="sxs-lookup"><span data-stu-id="1172a-118">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="1172a-119">您可以使用`-s`選項覆蓋*nuget.config*源。</span><span class="sxs-lookup"><span data-stu-id="1172a-119">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="1172a-120">有關如何使用經過身份驗證的源的資訊,請參閱[使用來自經過身份驗證的來源的套件](/nuget/consume-packages/consuming-packages-authenticated-feeds)。</span><span class="sxs-lookup"><span data-stu-id="1172a-120">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="package-cache"></a><span data-ttu-id="1172a-121">包快取</span><span class="sxs-lookup"><span data-stu-id="1172a-121">Package cache</span></span>

<span data-ttu-id="1172a-122">針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。</span><span class="sxs-lookup"><span data-stu-id="1172a-122">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="1172a-123">如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="1172a-123">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="1172a-124">例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*。</span><span class="sxs-lookup"><span data-stu-id="1172a-124">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="1172a-125">特定於項目的工具</span><span class="sxs-lookup"><span data-stu-id="1172a-125">Project-specific tooling</span></span>

<span data-ttu-id="1172a-126">針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。</span><span class="sxs-lookup"><span data-stu-id="1172a-126">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="1172a-127">nuget.config 差異</span><span class="sxs-lookup"><span data-stu-id="1172a-127">nuget.config differences</span></span>

<span data-ttu-id="1172a-128">*nuget.config* 檔案中設定 (如果有的話) 會影響 `dotnet restore` 命令的行為。</span><span class="sxs-lookup"><span data-stu-id="1172a-128">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="1172a-129">例如，在 *nuget.config* 中設定 `globalPackagesFolder` 會將還原的 NuGet 套件置於所指定資料夾。</span><span class="sxs-lookup"><span data-stu-id="1172a-129">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="1172a-130">這是在 `dotnet restore` 命令上指定 `--packages` 選項的替代方式。</span><span class="sxs-lookup"><span data-stu-id="1172a-130">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="1172a-131">如需詳細資訊，請參閱 [nuget.config 參考](/nuget/schema/nuget-config-file)。</span><span class="sxs-lookup"><span data-stu-id="1172a-131">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="1172a-132">`dotnet restore` 會忽略三個特定設定：</span><span class="sxs-lookup"><span data-stu-id="1172a-132">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="1172a-133">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="1172a-133">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="1172a-134">繫結重新導向不適用於 `<PackageReference>` 元素，且 .NET Core 針對 NuGet 套件僅支援 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="1172a-134">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="1172a-135">解決機制</span><span class="sxs-lookup"><span data-stu-id="1172a-135">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="1172a-136">這是 Visual Studio 特定設定，不適用於 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="1172a-136">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="1172a-137">.Net Core 不會使用 `packages.config` 檔案，而是針對 NuGet 套件使用 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="1172a-137">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="1172a-138">受信任的簽名者</span><span class="sxs-lookup"><span data-stu-id="1172a-138">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="1172a-139">此設定不適用，因為 [NuGet 尚未支援信任套件的跨平臺驗證](https://github.com/NuGet/Home/issues/7939)。</span><span class="sxs-lookup"><span data-stu-id="1172a-139">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="1172a-140">隱式還原</span><span class="sxs-lookup"><span data-stu-id="1172a-140">Implicit restore</span></span>

<span data-ttu-id="1172a-141">如有必要`dotnet restore`,在運行以下命令時,該命令將隱式運行:</span><span class="sxs-lookup"><span data-stu-id="1172a-141">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="1172a-142">在大多數情況下,不需要顯式使用`dotnet restore`該命令。</span><span class="sxs-lookup"><span data-stu-id="1172a-142">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="1172a-143">有時候，可能不適合隱含執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="1172a-143">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="1172a-144">例如，某些自動化系統，像是建置系統，必須明確呼叫 `dotnet restore` 以控制還原發生的時間，進而控制網路使用量。</span><span class="sxs-lookup"><span data-stu-id="1172a-144">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="1172a-145">為避免隱含執行 `dotnet restore`，在使用任一這些命令時，可使用 `--no-restore` 旗標來停用隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1172a-145">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="1172a-146">引數</span><span class="sxs-lookup"><span data-stu-id="1172a-146">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="1172a-147">要還原之專案檔的選用路徑。</span><span class="sxs-lookup"><span data-stu-id="1172a-147">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="1172a-148">選項。</span><span class="sxs-lookup"><span data-stu-id="1172a-148">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="1172a-149">要用於還原作業的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="1172a-149">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="1172a-150">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="1172a-150">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="1172a-151">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="1172a-151">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="1172a-152">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="1172a-152">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="1172a-153">強制還原以重新評估所有依賴項,即使鎖檔已存在也是如此。</span><span class="sxs-lookup"><span data-stu-id="1172a-153">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1172a-154">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="1172a-154">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="1172a-155">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="1172a-155">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="1172a-156">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="1172a-156">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="1172a-157">自 .NET Core 2.1.400 起。</span><span class="sxs-lookup"><span data-stu-id="1172a-157">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="1172a-158">寫入項目鎖定檔的輸出位置。</span><span class="sxs-lookup"><span data-stu-id="1172a-158">Output location where project lock file is written.</span></span> <span data-ttu-id="1172a-159">預設情況下,這是*PROJECT_ROOT\包.lock.json*。</span><span class="sxs-lookup"><span data-stu-id="1172a-159">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="1172a-160">不允許更新項目鎖定檔。</span><span class="sxs-lookup"><span data-stu-id="1172a-160">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="1172a-161">指定不快取 HTTP 請求。</span><span class="sxs-lookup"><span data-stu-id="1172a-161">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="1172a-162">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="1172a-162">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="1172a-163">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="1172a-163">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="1172a-164">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="1172a-164">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="1172a-165">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="1172a-165">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="1172a-166">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="1172a-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="1172a-167">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="1172a-167">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="1172a-168">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="1172a-168">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="1172a-169">此設定將覆蓋*nuget.config*檔中指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="1172a-169">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="1172a-170">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="1172a-170">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="1172a-171">使項目鎖定檔能夠生成並與還原一起使用。</span><span class="sxs-lookup"><span data-stu-id="1172a-171">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1172a-172">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="1172a-172">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1172a-173">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="1172a-173">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1172a-174">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="1172a-174">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="1172a-175">範例</span><span class="sxs-lookup"><span data-stu-id="1172a-175">Examples</span></span>

- <span data-ttu-id="1172a-176">還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="1172a-176">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="1172a-177">回復指定路徑中找到`app1`的項目的相依項與工具:</span><span class="sxs-lookup"><span data-stu-id="1172a-177">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="1172a-178">使用此檔案路徑回復目前的目錄中項目的相依項與工具:</span><span class="sxs-lookup"><span data-stu-id="1172a-178">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="1172a-179">使用為來源的兩個檔案路徑還原目前的目錄中項目的相依項與工具:</span><span class="sxs-lookup"><span data-stu-id="1172a-179">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="1172a-180">還原目前的目錄中項目的相依項與工具,顯示詳細輸出:</span><span class="sxs-lookup"><span data-stu-id="1172a-180">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
