---
title: dotnet restore 命令
description: 了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。
ms.date: 02/27/2020
ms.openlocfilehash: e74027ba70ddf6905a12f9691caeb0a406428ad6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157020"
---
# <a name="dotnet-restore"></a><span data-ttu-id="370d0-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="370d0-103">dotnet restore</span></span>

<span data-ttu-id="370d0-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="370d0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="370d0-105">名稱</span><span class="sxs-lookup"><span data-stu-id="370d0-105">Name</span></span>

<span data-ttu-id="370d0-106">`dotnet restore` - 還原專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="370d0-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="370d0-107">概要</span><span class="sxs-lookup"><span data-stu-id="370d0-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a><span data-ttu-id="370d0-108">描述</span><span class="sxs-lookup"><span data-stu-id="370d0-108">Description</span></span>

<span data-ttu-id="370d0-109">`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。</span><span class="sxs-lookup"><span data-stu-id="370d0-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="370d0-110">預設會平行執行相依性和工具的還原。</span><span class="sxs-lookup"><span data-stu-id="370d0-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="370d0-111">若要還原相依性，NuGet 需要套件所在的摘要。</span><span class="sxs-lookup"><span data-stu-id="370d0-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="370d0-112">摘要通常透過 *nuget.config* 組態檔提供。</span><span class="sxs-lookup"><span data-stu-id="370d0-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="370d0-113">安裝 .NET Core SDK 時，會提供預設的設定檔案。</span><span class="sxs-lookup"><span data-stu-id="370d0-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="370d0-114">您可以在專案目錄中建立自己的 *nuget.config* 檔案，以指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="370d0-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="370d0-115">您可以使用-`-s` 選項來覆寫*nuget.exe*摘要。</span><span class="sxs-lookup"><span data-stu-id="370d0-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="370d0-116">針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。</span><span class="sxs-lookup"><span data-stu-id="370d0-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="370d0-117">如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="370d0-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="370d0-118">例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*。</span><span class="sxs-lookup"><span data-stu-id="370d0-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="370d0-119">針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。</span><span class="sxs-lookup"><span data-stu-id="370d0-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="370d0-120">nuget.config 差異</span><span class="sxs-lookup"><span data-stu-id="370d0-120">nuget.config differences</span></span>

<span data-ttu-id="370d0-121">`dotnet restore`nuget.config*檔案中設定 (如果有的話) 會影響* 命令的行為。</span><span class="sxs-lookup"><span data-stu-id="370d0-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="370d0-122">例如，在 `globalPackagesFolder`nuget.config*中設定* 會將還原的 NuGet 套件置於所指定資料夾。</span><span class="sxs-lookup"><span data-stu-id="370d0-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="370d0-123">這是在 `--packages` 命令上指定 `dotnet restore` 選項的替代方式。</span><span class="sxs-lookup"><span data-stu-id="370d0-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="370d0-124">如需詳細資訊，請參閱 [nuget.config 參考](/nuget/schema/nuget-config-file)。</span><span class="sxs-lookup"><span data-stu-id="370d0-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="370d0-125">`dotnet restore` 會忽略三個特定設定：</span><span class="sxs-lookup"><span data-stu-id="370d0-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="370d0-126">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="370d0-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="370d0-127">繫結重新導向不適用於 `<PackageReference>` 元素，且 .NET Core 針對 NuGet 套件僅支援 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="370d0-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="370d0-128">solution</span><span class="sxs-lookup"><span data-stu-id="370d0-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="370d0-129">這是 Visual Studio 特定設定，不適用於 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="370d0-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="370d0-130">.Net Core 不會使用 `packages.config` 檔案，而是針對 NuGet 套件使用 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="370d0-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="370d0-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="370d0-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="370d0-132">此設定不適用，因為 [NuGet 尚未支援信任套件的跨平臺驗證](https://github.com/NuGet/Home/issues/7939)。</span><span class="sxs-lookup"><span data-stu-id="370d0-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="370d0-133">隱含還原</span><span class="sxs-lookup"><span data-stu-id="370d0-133">Implicit restore</span></span>

<span data-ttu-id="370d0-134">當您執行下列命令時，會視需要隱含地執行 `dotnet restore` 命令：</span><span class="sxs-lookup"><span data-stu-id="370d0-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="370d0-135">在大部分的情況下，您不需要明確地使用 `dotnet restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="370d0-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="370d0-136">有時候，可能不適合隱含執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="370d0-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="370d0-137">例如，某些自動化系統，像是建置系統，必須明確呼叫 `dotnet restore` 以控制還原發生的時間，進而控制網路使用量。</span><span class="sxs-lookup"><span data-stu-id="370d0-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="370d0-138">為避免隱含執行 `dotnet restore`，在使用任一這些命令時，可使用 `--no-restore` 旗標來停用隱含還原。</span><span class="sxs-lookup"><span data-stu-id="370d0-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="370d0-139">引數</span><span class="sxs-lookup"><span data-stu-id="370d0-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="370d0-140">要還原之專案檔的選用路徑。</span><span class="sxs-lookup"><span data-stu-id="370d0-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="370d0-141">選項。</span><span class="sxs-lookup"><span data-stu-id="370d0-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="370d0-142">要用於還原作業的 NuGet 組態檔 (*nuget.config*)。</span><span class="sxs-lookup"><span data-stu-id="370d0-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="370d0-143">停用平行還原多個專案。</span><span class="sxs-lookup"><span data-stu-id="370d0-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="370d0-144">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="370d0-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="370d0-145">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="370d0-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="370d0-146">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="370d0-146">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="370d0-147">如果有套件符合版本需求，則只會警告有關失敗的來源。</span><span class="sxs-lookup"><span data-stu-id="370d0-147">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--no-cache`**

  <span data-ttu-id="370d0-148">指定不要快取套件和 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="370d0-148">Specifies to not cache packages and HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="370d0-149">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="370d0-149">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="370d0-150">指定已還原套件的目錄。</span><span class="sxs-lookup"><span data-stu-id="370d0-150">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="370d0-151">指定套件還原的執行階段。</span><span class="sxs-lookup"><span data-stu-id="370d0-151">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="370d0-152">這用來針對 `<RuntimeIdentifiers>`.csproj*檔案內* 標記中未明確列出的執行階段還原套件。</span><span class="sxs-lookup"><span data-stu-id="370d0-152">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="370d0-153">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="370d0-153">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="370d0-154">多次指定這個選項來提供多個 RID。</span><span class="sxs-lookup"><span data-stu-id="370d0-154">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="370d0-155">指定要在還原作業期間使用的 NuGet 套件來源。</span><span class="sxs-lookup"><span data-stu-id="370d0-155">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="370d0-156">此設定會覆寫 *nuget.config* 檔案中指定的所有來源。</span><span class="sxs-lookup"><span data-stu-id="370d0-156">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="370d0-157">多次指定這個選項，即可提供多個來源。</span><span class="sxs-lookup"><span data-stu-id="370d0-157">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--verbosity <LEVEL>`**

  <span data-ttu-id="370d0-158">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="370d0-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="370d0-159">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="370d0-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="370d0-160">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="370d0-160">Default value is `minimal`.</span></span>

- **`--interactive`**

  <span data-ttu-id="370d0-161">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="370d0-161">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="370d0-162">自 .NET Core 2.1.400 起。</span><span class="sxs-lookup"><span data-stu-id="370d0-162">Since .NET Core 2.1.400.</span></span>

## <a name="examples"></a><span data-ttu-id="370d0-163">範例</span><span class="sxs-lookup"><span data-stu-id="370d0-163">Examples</span></span>

- <span data-ttu-id="370d0-164">還原目前目錄中專案的相依性和工具︰</span><span class="sxs-lookup"><span data-stu-id="370d0-164">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="370d0-165">還原在指定路徑中找到之 `app1` 專案的相依性和工具：</span><span class="sxs-lookup"><span data-stu-id="370d0-165">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="370d0-166">使用提供作為來源的檔案路徑，還原目前目錄中專案的相依性和工具：</span><span class="sxs-lookup"><span data-stu-id="370d0-166">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="370d0-167">使用提供做為來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具：</span><span class="sxs-lookup"><span data-stu-id="370d0-167">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="370d0-168">還原目前目錄中專案的相依性和工具，顯示詳細輸出：</span><span class="sxs-lookup"><span data-stu-id="370d0-168">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
