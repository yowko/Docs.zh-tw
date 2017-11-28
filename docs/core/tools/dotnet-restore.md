---
title: "dotnet restore 命令 - .NET Core CLI"
description: "了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。"
keywords: "dotnet-restore, CLI, CLI 命令, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 82a78dcb0cc85e2ba087b6df5ee029cbfb687358
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-restore"></a><span data-ttu-id="b35b8-104">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b35b8-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b35b8-105">name</span><span class="sxs-lookup"><span data-stu-id="b35b8-105">Name</span></span>

<span data-ttu-id="b35b8-106">`dotnet restore` - 還原專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="b35b8-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b35b8-107">概要</span><span class="sxs-lookup"><span data-stu-id="b35b8-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b35b8-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b35b8-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b35b8-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b35b8-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="b35b8-110">說明</span><span class="sxs-lookup"><span data-stu-id="b35b8-110">Description</span></span>

<span data-ttu-id="b35b8-111">`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。</span><span class="sxs-lookup"><span data-stu-id="b35b8-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="b35b8-112">預設會平行執行相依性和工具的還原。</span><span class="sxs-lookup"><span data-stu-id="b35b8-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b35b8-113">若要還原相依性，NuGet 需要套件所在的摘要。</span><span class="sxs-lookup"><span data-stu-id="b35b8-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="b35b8-114">摘要通常透過 *NuGet.config* 組態檔提供。</span><span class="sxs-lookup"><span data-stu-id="b35b8-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="b35b8-115">安裝 CLI 工具時，會提供預設組態檔。</span><span class="sxs-lookup"><span data-stu-id="b35b8-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="b35b8-116">您可以在專案目錄中建立自己的 *NuGet.config* 檔案，以指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="b35b8-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="b35b8-117">您也可以在命令提示字元中針對每個引動過程指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="b35b8-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="b35b8-118">針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。</span><span class="sxs-lookup"><span data-stu-id="b35b8-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="b35b8-119">如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中 (例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*)。</span><span class="sxs-lookup"><span data-stu-id="b35b8-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="b35b8-120">針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。</span><span class="sxs-lookup"><span data-stu-id="b35b8-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="b35b8-121">*Nuget.Config* 檔案中的一些設定 (如果有的話) 會影響 `dotnet restore` 命令的行為。</span><span class="sxs-lookup"><span data-stu-id="b35b8-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="b35b8-122">例如，在 *NuGet.Config* 中設定 `globalPackagesFolder` 會將還原的 NuGet 套件置於指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b35b8-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="b35b8-123">這是在 `dotnet restore` 命令上指定 `--packages` 選項的替代方式。</span><span class="sxs-lookup"><span data-stu-id="b35b8-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="b35b8-124">如需詳細資訊，請參閱 [NuGet.Config 參考](/nuget/schema/nuget-config-file)。</span><span class="sxs-lookup"><span data-stu-id="b35b8-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="arguments"></a><span data-ttu-id="b35b8-125">引數</span><span class="sxs-lookup"><span data-stu-id="b35b8-125">Arguments</span></span>

`ROOT`

<span data-ttu-id="b35b8-126">要還原之專案檔的選用路徑。</span><span class="sxs-lookup"><span data-stu-id="b35b8-126">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="b35b8-127">選項</span><span class="sxs-lookup"><span data-stu-id="b35b8-127">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b35b8-128">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b35b8-128">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="b35b8-129">要用於還原作業的 NuGet 組態檔 (*NuGet.config*)。</span><span class="sxs-lookup"><span data-stu-id="b35b8-129">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="b35b8-130">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="b35b8-130">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="b35b8-131">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="b35b8-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b35b8-132">這相當於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b35b8-132">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="b35b8-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b35b8-133">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="b35b8-134">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-134">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="b35b8-135">指定不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="b35b8-135">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="b35b8-136">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="b35b8-136">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="b35b8-137">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="b35b8-137">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b35b8-138">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="b35b8-138">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b35b8-139">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="b35b8-139">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b35b8-140">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b35b8-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b35b8-141">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="b35b8-141">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="b35b8-142">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-142">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b35b8-143">這會覆寫 *NuGet.config* 檔案中指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-143">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="b35b8-144">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-144">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="b35b8-145">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="b35b8-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b35b8-146">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b35b8-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b35b8-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b35b8-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="b35b8-148">要用於還原作業的 NuGet 組態檔 (*NuGet.config*)。</span><span class="sxs-lookup"><span data-stu-id="b35b8-148">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="b35b8-149">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="b35b8-149">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="b35b8-150">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b35b8-150">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="b35b8-151">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-151">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="b35b8-152">指定不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="b35b8-152">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="b35b8-153">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="b35b8-153">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="b35b8-154">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="b35b8-154">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b35b8-155">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="b35b8-155">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b35b8-156">這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="b35b8-156">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b35b8-157">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b35b8-157">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b35b8-158">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="b35b8-158">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="b35b8-159">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-159">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b35b8-160">這會覆寫 *NuGet.config* 檔案中指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-160">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="b35b8-161">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="b35b8-161">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="b35b8-162">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="b35b8-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b35b8-163">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b35b8-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="b35b8-164">範例</span><span class="sxs-lookup"><span data-stu-id="b35b8-164">Examples</span></span>

<span data-ttu-id="b35b8-165">還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="b35b8-165">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="b35b8-166">還原在指定路徑中找到之 `app1` 專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="b35b8-166">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="b35b8-167">使用提供為來源的檔案路徑，還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="b35b8-167">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="b35b8-168">使用提供為來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="b35b8-168">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="b35b8-169">還原目前目錄中專案的相依性和工具，並且只顯示最小輸出：</span><span class="sxs-lookup"><span data-stu-id="b35b8-169">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
