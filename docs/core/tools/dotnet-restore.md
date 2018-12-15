---
title: dotnet restore 命令 - .NET Core CLI
description: 了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 504a0621beb8aea961133d2cc6d287ce17051c1c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127325"
---
# <a name="dotnet-restore"></a><span data-ttu-id="e8da2-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="e8da2-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e8da2-104">name</span><span class="sxs-lookup"><span data-stu-id="e8da2-104">Name</span></span>

<span data-ttu-id="e8da2-105">`dotnet restore` - 還原專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="e8da2-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e8da2-106">概要</span><span class="sxs-lookup"><span data-stu-id="e8da2-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="e8da2-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="e8da2-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e8da2-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e8da2-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="e8da2-109">說明</span><span class="sxs-lookup"><span data-stu-id="e8da2-109">Description</span></span>

<span data-ttu-id="e8da2-110">`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。</span><span class="sxs-lookup"><span data-stu-id="e8da2-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="e8da2-111">預設會平行執行相依性和工具的還原。</span><span class="sxs-lookup"><span data-stu-id="e8da2-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="e8da2-112">若要還原相依性，NuGet 需要套件所在的摘要。</span><span class="sxs-lookup"><span data-stu-id="e8da2-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="e8da2-113">摘要通常透過 *NuGet.config* 組態檔提供。</span><span class="sxs-lookup"><span data-stu-id="e8da2-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="e8da2-114">安裝 CLI 工具時，會提供預設組態檔。</span><span class="sxs-lookup"><span data-stu-id="e8da2-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="e8da2-115">您可以在專案目錄中建立自己的 *NuGet.config* 檔案，以指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="e8da2-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="e8da2-116">您也可以在命令提示字元中針對每個引動過程指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="e8da2-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="e8da2-117">針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。</span><span class="sxs-lookup"><span data-stu-id="e8da2-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="e8da2-118">如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="e8da2-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="e8da2-119">例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*。</span><span class="sxs-lookup"><span data-stu-id="e8da2-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="e8da2-120">針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。</span><span class="sxs-lookup"><span data-stu-id="e8da2-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="e8da2-121">*Nuget.Config* 檔案中的一些設定 (如果有的話) 會影響 `dotnet restore` 命令的行為。</span><span class="sxs-lookup"><span data-stu-id="e8da2-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="e8da2-122">例如，在 *NuGet.Config* 中設定 `globalPackagesFolder` 會將還原的 NuGet 套件置於指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e8da2-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="e8da2-123">這是在 `dotnet restore` 命令上指定 `--packages` 選項的替代方式。</span><span class="sxs-lookup"><span data-stu-id="e8da2-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="e8da2-124">如需詳細資訊，請參閱 [NuGet.Config 參考](/nuget/schema/nuget-config-file)。</span><span class="sxs-lookup"><span data-stu-id="e8da2-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="e8da2-125">隱含 `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="e8da2-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="e8da2-126">從 .NET Core 2.0 開始，當您發出下列命令時，`dotnet restore` 會於必要時隱含地執行：</span><span class="sxs-lookup"><span data-stu-id="e8da2-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="e8da2-127">多數情況下，您不再需要明確地使用 `dotnet restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="e8da2-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="e8da2-128">有時候，可能不適合隱含執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="e8da2-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="e8da2-129">例如，某些自動化系統，像是建置系統，必須明確呼叫 `dotnet restore` 以控制還原發生的時間，進而控制網路使用量。</span><span class="sxs-lookup"><span data-stu-id="e8da2-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="e8da2-130">為避免隱含執行 `dotnet restore`，在使用任一這些命令時，可使用 `--no-restore` 旗標來停用隱含還原。</span><span class="sxs-lookup"><span data-stu-id="e8da2-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="e8da2-131">引數</span><span class="sxs-lookup"><span data-stu-id="e8da2-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="e8da2-132">要還原之專案檔的選用路徑。</span><span class="sxs-lookup"><span data-stu-id="e8da2-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="e8da2-133">選項</span><span class="sxs-lookup"><span data-stu-id="e8da2-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="e8da2-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="e8da2-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="e8da2-135">要用於還原作業的 NuGet 組態檔 (*NuGet.config*)。</span><span class="sxs-lookup"><span data-stu-id="e8da2-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="e8da2-136">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="e8da2-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="e8da2-137">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="e8da2-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e8da2-138">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8da2-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="e8da2-139">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="e8da2-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="e8da2-140">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="e8da2-141">指定不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="e8da2-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="e8da2-142">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="e8da2-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="e8da2-143">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="e8da2-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e8da2-144">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="e8da2-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="e8da2-145">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="e8da2-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="e8da2-146">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="e8da2-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="e8da2-147">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="e8da2-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="e8da2-148">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="e8da2-149">此設定會覆寫 *NuGet.config* 檔案中所指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="e8da2-150">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="e8da2-151">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="e8da2-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e8da2-152">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="e8da2-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--interactive`

<span data-ttu-id="e8da2-153">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="e8da2-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="e8da2-154">自 .NET Core 2.1.400 起。</span><span class="sxs-lookup"><span data-stu-id="e8da2-154">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e8da2-155">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e8da2-155">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="e8da2-156">要用於還原作業的 NuGet 組態檔 (*NuGet.config*)。</span><span class="sxs-lookup"><span data-stu-id="e8da2-156">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="e8da2-157">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="e8da2-157">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="e8da2-158">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="e8da2-158">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="e8da2-159">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-159">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="e8da2-160">指定不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="e8da2-160">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="e8da2-161">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="e8da2-161">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="e8da2-162">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="e8da2-162">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e8da2-163">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="e8da2-163">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="e8da2-164">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="e8da2-164">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="e8da2-165">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="e8da2-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="e8da2-166">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="e8da2-166">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="e8da2-167">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-167">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="e8da2-168">如此會覆寫 *NuGet.config* 檔案中所指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-168">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="e8da2-169">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="e8da2-169">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="e8da2-170">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="e8da2-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e8da2-171">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="e8da2-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="e8da2-172">範例</span><span class="sxs-lookup"><span data-stu-id="e8da2-172">Examples</span></span>

<span data-ttu-id="e8da2-173">還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="e8da2-173">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="e8da2-174">還原在指定路徑中找到之 `app1` 專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="e8da2-174">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="e8da2-175">使用提供為來源的檔案路徑，還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="e8da2-175">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="e8da2-176">使用提供為來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="e8da2-176">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="e8da2-177">還原目前目錄中專案的相依性和工具，並且只顯示最小輸出：</span><span class="sxs-lookup"><span data-stu-id="e8da2-177">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
