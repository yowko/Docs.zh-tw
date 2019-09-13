---
title: dotnet restore 命令
description: 了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。
ms.date: 05/29/2018
ms.openlocfilehash: 567316e98e161a7645db6bf55a03c3c006999fa9
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893279"
---
# <a name="dotnet-restore"></a><span data-ttu-id="4232e-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4232e-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4232e-104">name</span><span class="sxs-lookup"><span data-stu-id="4232e-104">Name</span></span>

<span data-ttu-id="4232e-105">`dotnet restore` - 還原專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="4232e-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4232e-106">概要</span><span class="sxs-lookup"><span data-stu-id="4232e-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4232e-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4232e-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4232e-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4232e-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4232e-109">說明</span><span class="sxs-lookup"><span data-stu-id="4232e-109">Description</span></span>

<span data-ttu-id="4232e-110">`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。</span><span class="sxs-lookup"><span data-stu-id="4232e-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="4232e-111">預設會平行執行相依性和工具的還原。</span><span class="sxs-lookup"><span data-stu-id="4232e-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4232e-112">若要還原相依性，NuGet 需要套件所在的摘要。</span><span class="sxs-lookup"><span data-stu-id="4232e-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="4232e-113">摘要通常透過 *nuget.config* 組態檔提供。</span><span class="sxs-lookup"><span data-stu-id="4232e-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="4232e-114">安裝 CLI 工具時，會提供預設組態檔。</span><span class="sxs-lookup"><span data-stu-id="4232e-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="4232e-115">您可以在專案目錄中建立自己的 *nuget.config* 檔案，以指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="4232e-115">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="4232e-116">您也可以在命令提示字元中針對每個引動過程指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="4232e-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="4232e-117">針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。</span><span class="sxs-lookup"><span data-stu-id="4232e-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="4232e-118">如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="4232e-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="4232e-119">例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*。</span><span class="sxs-lookup"><span data-stu-id="4232e-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="4232e-120">針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。</span><span class="sxs-lookup"><span data-stu-id="4232e-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="4232e-121">nuget.config 差異</span><span class="sxs-lookup"><span data-stu-id="4232e-121">nuget.config differences</span></span>

<span data-ttu-id="4232e-122">*nuget.config* 檔案中設定 (如果有的話) 會影響 `dotnet restore` 命令的行為。</span><span class="sxs-lookup"><span data-stu-id="4232e-122">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="4232e-123">例如，在 *nuget.config* 中設定 `globalPackagesFolder` 會將還原的 NuGet 套件置於所指定資料夾。</span><span class="sxs-lookup"><span data-stu-id="4232e-123">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="4232e-124">這是在 `dotnet restore` 命令上指定 `--packages` 選項的替代方式。</span><span class="sxs-lookup"><span data-stu-id="4232e-124">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="4232e-125">如需詳細資訊，請參閱 [nuget.config 參考](/nuget/schema/nuget-config-file)。</span><span class="sxs-lookup"><span data-stu-id="4232e-125">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="4232e-126">`dotnet restore` 會忽略三個特定設定：</span><span class="sxs-lookup"><span data-stu-id="4232e-126">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="4232e-127">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="4232e-127">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="4232e-128">繫結重新導向不適用於 `<PackageReference>` 元素，且 .NET Core 針對 NuGet 套件僅支援 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="4232e-128">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="4232e-129">solution</span><span class="sxs-lookup"><span data-stu-id="4232e-129">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="4232e-130">這是 Visual Studio 特定設定，不適用於 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="4232e-130">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="4232e-131">.Net Core 不會使用 `packages.config` 檔案，而是針對 NuGet 套件使用 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="4232e-131">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="4232e-132">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="4232e-132">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="4232e-133">此設定不適用，因為 [NuGet 尚未支援信任套件的跨平臺驗證](https://github.com/NuGet/Home/issues/7939)。</span><span class="sxs-lookup"><span data-stu-id="4232e-133">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="4232e-134">隱含 `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="4232e-134">Implicit `dotnet restore`</span></span>

<span data-ttu-id="4232e-135">從 .NET Core 2.0 開始，當您發出下列命令時，`dotnet restore` 會於必要時隱含地執行：</span><span class="sxs-lookup"><span data-stu-id="4232e-135">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="4232e-136">多數情況下，您不再需要明確地使用 `dotnet restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="4232e-136">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="4232e-137">有時候，可能不適合隱含執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="4232e-137">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="4232e-138">例如，某些自動化系統，像是建置系統，必須明確呼叫 `dotnet restore` 以控制還原發生的時間，進而控制網路使用量。</span><span class="sxs-lookup"><span data-stu-id="4232e-138">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="4232e-139">為避免隱含執行 `dotnet restore`，在使用任一這些命令時，可使用 `--no-restore` 旗標來停用隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4232e-139">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="4232e-140">引數</span><span class="sxs-lookup"><span data-stu-id="4232e-140">Arguments</span></span>

`ROOT`

<span data-ttu-id="4232e-141">要還原之專案檔的選用路徑。</span><span class="sxs-lookup"><span data-stu-id="4232e-141">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="4232e-142">選項</span><span class="sxs-lookup"><span data-stu-id="4232e-142">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4232e-143">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4232e-143">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="4232e-144">要用於還原作業的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="4232e-144">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="4232e-145">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="4232e-145">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="4232e-146">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="4232e-146">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="4232e-147">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4232e-147">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="4232e-148">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4232e-148">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="4232e-149">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="4232e-149">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="4232e-150">指定不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="4232e-150">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="4232e-151">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="4232e-151">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="4232e-152">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="4232e-152">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4232e-153">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="4232e-153">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="4232e-154">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="4232e-154">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="4232e-155">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="4232e-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="4232e-156">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="4232e-156">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="4232e-157">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="4232e-157">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="4232e-158">此設定會覆寫 *nuget.config* 檔案中指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="4232e-158">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="4232e-159">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="4232e-159">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="4232e-160">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4232e-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4232e-161">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4232e-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--interactive`

<span data-ttu-id="4232e-162">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="4232e-162">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="4232e-163">自 .NET Core 2.1.400 起。</span><span class="sxs-lookup"><span data-stu-id="4232e-163">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4232e-164">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4232e-164">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="4232e-165">要用於還原作業的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="4232e-165">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="4232e-166">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="4232e-166">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="4232e-167">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4232e-167">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="4232e-168">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="4232e-168">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="4232e-169">指定不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="4232e-169">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="4232e-170">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="4232e-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="4232e-171">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="4232e-171">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4232e-172">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="4232e-172">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="4232e-173">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="4232e-173">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="4232e-174">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="4232e-174">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="4232e-175">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="4232e-175">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="4232e-176">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="4232e-176">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="4232e-177">這會覆寫*nuget.exe*檔案中指定的所有來源， `<packageSource>`並有效地讀取*nuget .config*檔案，就像專案不存在一樣。</span><span class="sxs-lookup"><span data-stu-id="4232e-177">This overrides all of the sources specified in the *nuget.config* files, effectively reading the *nuget.config* file as if the `<packageSource>` element was not there.</span></span> <span data-ttu-id="4232e-178">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="4232e-178">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="4232e-179">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4232e-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4232e-180">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4232e-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4232e-181">範例</span><span class="sxs-lookup"><span data-stu-id="4232e-181">Examples</span></span>

<span data-ttu-id="4232e-182">還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="4232e-182">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="4232e-183">還原在指定路徑中找到之 `app1` 專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="4232e-183">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="4232e-184">使用提供為來源的檔案路徑，還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="4232e-184">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="4232e-185">使用提供為來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="4232e-185">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="4232e-186">還原目前目錄中專案的相依性和工具，並且只顯示最小輸出：</span><span class="sxs-lookup"><span data-stu-id="4232e-186">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
