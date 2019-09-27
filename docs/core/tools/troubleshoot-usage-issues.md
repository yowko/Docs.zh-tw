---
title: 針對 .NET Core 工具使用問題進行疑難排解
description: 探索執行 .NET Core 工具和可能的解決方案時常見的問題。
author: kdollard
ms.date: 09/23/2019
ms.openlocfilehash: eb769550493e5a25d4380cd543a3bbec880b38e9
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332974"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="21a7b-103">針對 .NET Core 工具使用問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="21a7b-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="21a7b-104">當您嘗試安裝或執行 .NET Core 工具時，可能會遇到問題，這可以是全域工具或本機工具。</span><span class="sxs-lookup"><span data-stu-id="21a7b-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="21a7b-105">本文說明常見的根本原因和一些可能的解決方案。</span><span class="sxs-lookup"><span data-stu-id="21a7b-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="21a7b-106">安裝的 .NET Core 工具無法執行</span><span class="sxs-lookup"><span data-stu-id="21a7b-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="21a7b-107">當 .NET Core 工具無法執行時，您很可能會遇到下列其中一個問題：</span><span class="sxs-lookup"><span data-stu-id="21a7b-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="21a7b-108">找不到工具的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="21a7b-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="21a7b-109">找不到正確的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="21a7b-109">The correct version of the .NET Core runtime wasn't found.</span></span> 

### <a name="executable-file-not-found"></a><span data-ttu-id="21a7b-110">找不到可執行檔</span><span class="sxs-lookup"><span data-stu-id="21a7b-110">Executable file not found</span></span>

<span data-ttu-id="21a7b-111">如果找不到可執行檔，您會看到類似下面的訊息：</span><span class="sxs-lookup"><span data-stu-id="21a7b-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="21a7b-112">可執行檔的名稱會決定您叫用此工具的方式。</span><span class="sxs-lookup"><span data-stu-id="21a7b-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="21a7b-113">下表描述格式：</span><span class="sxs-lookup"><span data-stu-id="21a7b-113">The following table describes the format:</span></span>

| <span data-ttu-id="21a7b-114">可執行檔名稱格式</span><span class="sxs-lookup"><span data-stu-id="21a7b-114">Executable name format</span></span>  | <span data-ttu-id="21a7b-115">調用格式</span><span class="sxs-lookup"><span data-stu-id="21a7b-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="21a7b-116">通用工具</span><span class="sxs-lookup"><span data-stu-id="21a7b-116">Global tools</span></span>

    <span data-ttu-id="21a7b-117">通用工具可以安裝在預設目錄或特定位置。</span><span class="sxs-lookup"><span data-stu-id="21a7b-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="21a7b-118">預設目錄如下：</span><span class="sxs-lookup"><span data-stu-id="21a7b-118">The default directories are:</span></span>

    | <span data-ttu-id="21a7b-119">OS</span><span class="sxs-lookup"><span data-stu-id="21a7b-119">OS</span></span>          | <span data-ttu-id="21a7b-120">`Path`</span><span class="sxs-lookup"><span data-stu-id="21a7b-120">Path</span></span>                          |
    |-------------|-------------------------------|
    | <span data-ttu-id="21a7b-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="21a7b-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
    | <span data-ttu-id="21a7b-122">Windows</span><span class="sxs-lookup"><span data-stu-id="21a7b-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

    <span data-ttu-id="21a7b-123">如果您嘗試執行全域工具，請檢查您電腦上的 `PATH` 環境變數是否包含安裝通用工具的路徑，以及可執行檔是否在該路徑中。</span><span class="sxs-lookup"><span data-stu-id="21a7b-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

    <span data-ttu-id="21a7b-124">.NET Core CLI 會在第一次使用時，嘗試將預設位置新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="21a7b-124">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="21a7b-125">不過，有幾個位置可能不會自動新增至路徑，因此您必須在下列情況中編輯路徑來設定它：</span><span class="sxs-lookup"><span data-stu-id="21a7b-125">However, there are a couple of scenarios where the location might not be added to PATH automatically, so you'll have to edit PATH to configure it for the following cases:</span></span>

  * <span data-ttu-id="21a7b-126">如果您使用的是 Linux，而且您已使用*gz*檔案安裝 .NET Core SDK，而不是 apt-get 或 rpm。</span><span class="sxs-lookup"><span data-stu-id="21a7b-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="21a7b-127">如果您使用的是 macOS 10.15 "Catalina" 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="21a7b-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="21a7b-128">如果您使用 macOS 10.14 "Mojave" 或更早版本，且已使用*gz*檔案安裝 .NET Core SDK，而不是 *.pkg*。</span><span class="sxs-lookup"><span data-stu-id="21a7b-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="21a7b-129">如果您已安裝 .NET Core 3.0 SDK，而且已將 `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` 環境變數設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="21a7b-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="21a7b-130">如果您已安裝 .NET Core 2.2 SDK 或更早版本，而且已將 `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 環境變數設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="21a7b-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>
  
  <span data-ttu-id="21a7b-131">如需通用工具的詳細資訊，請參閱[.Net Core 通用工具總覽](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="21a7b-131">For more information about global tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

* <span data-ttu-id="21a7b-132">本機工具</span><span class="sxs-lookup"><span data-stu-id="21a7b-132">Local tools</span></span>

  <span data-ttu-id="21a7b-133">如果您嘗試執行本機工具，請確認目前目錄或其任何父目錄中有一個稱為*dotnet*的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="21a7b-133">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="21a7b-134">這個檔案也可以存留在專案資料夾階層中名為 *.config*的資料夾底下，而不是根資料夾。</span><span class="sxs-lookup"><span data-stu-id="21a7b-134">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="21a7b-135">如果*dotnet*存在，請將它開啟，並檢查您嘗試執行的工具。</span><span class="sxs-lookup"><span data-stu-id="21a7b-135">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="21a7b-136">如果檔案未包含 `"isRoot": true` 的專案，則也請進一步檢查檔案階層，以取得其他工具資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="21a7b-136">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

    <span data-ttu-id="21a7b-137">如果您嘗試執行以指定路徑安裝的 .NET Core 工具，則需要在使用此工具時包含該路徑。</span><span class="sxs-lookup"><span data-stu-id="21a7b-137">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="21a7b-138">使用工具路徑安裝工具的範例如下：</span><span class="sxs-lookup"><span data-stu-id="21a7b-138">An example of using a tool-path installed tool is:</span></span>

   ```console
   ..\<toolDirectory>\dotnet-<toolName>
    ```

### <a name="runtime-not-found"></a><span data-ttu-id="21a7b-139">找不到執行時間</span><span class="sxs-lookup"><span data-stu-id="21a7b-139">Runtime not found</span></span>

<span data-ttu-id="21a7b-140">.NET Core 工具是與[架構相依的應用程式](../deploying/index.md#framework-dependent-deployments-fdd)，這表示它們會依賴安裝在您電腦上的 .net core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="21a7b-140">.NET Core tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="21a7b-141">如果找不到預期的執行時間，它們會遵循一般的 .NET Core 執行時間向前復原規則，例如：</span><span class="sxs-lookup"><span data-stu-id="21a7b-141">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="21a7b-142">應用程式會向前復原到指定的主要和次要版本的最高修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="21a7b-142">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="21a7b-143">如果沒有符合的主要和次要版本號碼相符的執行時間，則會使用下一個較高的次要版本。</span><span class="sxs-lookup"><span data-stu-id="21a7b-143">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="21a7b-144">預覽版本的執行階段之間或預覽版本和發行版本之間，不會進行向前復原。</span><span class="sxs-lookup"><span data-stu-id="21a7b-144">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="21a7b-145">因此，使用預覽版本所建立的 .NET Core 工具必須由作者重建並重新發行，並重新安裝。</span><span class="sxs-lookup"><span data-stu-id="21a7b-145">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="21a7b-146">在兩個常見的案例中，預設不會進行向前復原：</span><span class="sxs-lookup"><span data-stu-id="21a7b-146">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="21a7b-147">只有較低版本的執行時間可供使用。</span><span class="sxs-lookup"><span data-stu-id="21a7b-147">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="21a7b-148">向前復原只會選取較新版本的執行時間。</span><span class="sxs-lookup"><span data-stu-id="21a7b-148">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="21a7b-149">只有較高的執行時間主要版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="21a7b-149">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="21a7b-150">向前復原不會跨越主要版本界限。</span><span class="sxs-lookup"><span data-stu-id="21a7b-150">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="21a7b-151">如果應用程式找不到適當的執行時間，它就無法執行並報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="21a7b-151">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="21a7b-152">您可以使用下列其中一個命令，找出您的電腦上已安裝的 .NET Core 執行時間：</span><span class="sxs-lookup"><span data-stu-id="21a7b-152">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="21a7b-153">如果您認為此工具應該支援您目前已安裝的執行階段版本，您可以洽詢工具作者，並查看他們是否可以更新版本號碼或多目標。</span><span class="sxs-lookup"><span data-stu-id="21a7b-153">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="21a7b-154">一旦使用更新的版本號碼將其工具套件重新編譯並重新發佈至 NuGet 之後，您就可以更新您的複本。</span><span class="sxs-lookup"><span data-stu-id="21a7b-154">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="21a7b-155">雖然不會發生這種情況，最快的解決方案是安裝可與您嘗試執行的工具搭配運作的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="21a7b-155">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="21a7b-156">若要下載特定的 .NET Core 執行階段版本，請造訪[.Net core 下載頁面](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="21a7b-156">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="21a7b-157">如果您將 .NET Core SDK 安裝到非預設位置，則必須將環境變數 `DOTNET_ROOT` 設定為包含 @no__t 1 可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="21a7b-157">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="21a7b-158">.NET Core 工具安裝失敗</span><span class="sxs-lookup"><span data-stu-id="21a7b-158">.NET Core tool installation fails</span></span>

<span data-ttu-id="21a7b-159">安裝 .NET Core 的全域或本機工具可能會失敗的原因有很多。</span><span class="sxs-lookup"><span data-stu-id="21a7b-159">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="21a7b-160">當工具安裝失敗時，您會看到類似下面的訊息：</span><span class="sxs-lookup"><span data-stu-id="21a7b-160">When the tool installation fails, you'll see a message similar to following one:</span></span>

```
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="21a7b-161">為了協助診斷這些失敗，NuGet 訊息會直接向使用者顯示，以及先前的訊息。</span><span class="sxs-lookup"><span data-stu-id="21a7b-161">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="21a7b-162">NuGet 訊息可協助您找出問題。</span><span class="sxs-lookup"><span data-stu-id="21a7b-162">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="21a7b-163">封裝命名強制執行</span><span class="sxs-lookup"><span data-stu-id="21a7b-163">Package naming enforcement</span></span>

<span data-ttu-id="21a7b-164">Microsoft 已變更工具的套件識別碼指引，導致找不到具有預測名稱的一些工具。</span><span class="sxs-lookup"><span data-stu-id="21a7b-164">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="21a7b-165">新的指引是所有的 Microsoft 工具前面都會加上 "Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="21a7b-165">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="21a7b-166">這個前置詞是保留的，只能用於以 Microsoft 授權憑證簽署的封裝。</span><span class="sxs-lookup"><span data-stu-id="21a7b-166">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="21a7b-167">在轉換期間，有些 Microsoft 工具會有舊版的套件識別碼，有些則會有新的表單：</span><span class="sxs-lookup"><span data-stu-id="21a7b-167">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="21a7b-168">更新套件識別碼時，您必須變更為新的套件識別碼，才能取得最新的更新。</span><span class="sxs-lookup"><span data-stu-id="21a7b-168">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="21a7b-169">具有簡化工具名稱的套件將會被取代。</span><span class="sxs-lookup"><span data-stu-id="21a7b-169">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="21a7b-170">預覽版本</span><span class="sxs-lookup"><span data-stu-id="21a7b-170">Preview releases</span></span>

* <span data-ttu-id="21a7b-171">您正嘗試安裝預覽版本，但未使用 `--version` 選項來指定版本。</span><span class="sxs-lookup"><span data-stu-id="21a7b-171">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="21a7b-172">處於預覽狀態的 .NET Core 工具必須以部分名稱指定，以表示其為預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="21a7b-172">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="21a7b-173">您不需要包含整個預覽。</span><span class="sxs-lookup"><span data-stu-id="21a7b-173">You don't need to include the entire preview.</span></span> <span data-ttu-id="21a7b-174">假設版本號碼採用預期的格式，您可以使用類似下列的範例：</span><span class="sxs-lookup"><span data-stu-id="21a7b-174">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

> [!NOTE]
> <span data-ttu-id="21a7b-175">.NET Core CLI 小組計畫在未來的版本中新增 `--preview` 參數，讓這項作業變得更容易。</span><span class="sxs-lookup"><span data-stu-id="21a7b-175">The .NET Core CLI team is planning to add a `--preview` switch in a future release to make this easier.</span></span>

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="21a7b-176">套件不是 .NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="21a7b-176">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="21a7b-177">找到這個名稱的 NuGet 套件，但它不是 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="21a7b-177">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="21a7b-178">如果您嘗試安裝屬於一般 NuGet 套件而不是 .NET Core 工具的 NuGet 套件，您會看到類似下面的錯誤：</span><span class="sxs-lookup"><span data-stu-id="21a7b-178">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

`NU1212: Invalid project-package combination for `<ToolName>`. DotnetToolReference project style can only contain references of the DotnetTool type.`

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="21a7b-179">無法存取 NuGet 摘要</span><span class="sxs-lookup"><span data-stu-id="21a7b-179">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="21a7b-180">無法存取所需的 NuGet 摘要，可能是因為網際網路連線問題所致。</span><span class="sxs-lookup"><span data-stu-id="21a7b-180">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="21a7b-181">工具安裝需要存取包含工具套件的 NuGet 摘要。</span><span class="sxs-lookup"><span data-stu-id="21a7b-181">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="21a7b-182">如果饋送無法使用，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="21a7b-182">It fails if the feed isn't available.</span></span> <span data-ttu-id="21a7b-183">您可以使用 `nuget.config` 來改變摘要、要求特定的 @no__t 1 檔案，或使用 `--add-source` 參數來指定其他摘要。</span><span class="sxs-lookup"><span data-stu-id="21a7b-183">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="21a7b-184">根據預設，NuGet 會針對無法連接的任何摘要擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="21a7b-184">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="21a7b-185">旗標 `--ignore-failed-sources` 可以略過這些無法連線的來源。</span><span class="sxs-lookup"><span data-stu-id="21a7b-185">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="21a7b-186">套件識別碼不正確</span><span class="sxs-lookup"><span data-stu-id="21a7b-186">Package ID incorrect</span></span>

* <span data-ttu-id="21a7b-187">您的工具名稱輸入錯誤。</span><span class="sxs-lookup"><span data-stu-id="21a7b-187">You mistyped the name of the tool.</span></span>

<span data-ttu-id="21a7b-188">失敗的常見原因是工具名稱不正確。</span><span class="sxs-lookup"><span data-stu-id="21a7b-188">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="21a7b-189">這可能是因為錯誤錯誤而發生，或是因為工具已移動或已被取代。</span><span class="sxs-lookup"><span data-stu-id="21a7b-189">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="21a7b-190">針對 NuGet.org 上的工具，確保您的名稱正確的方法之一，就是在 NuGet.org 搜尋工具並複製安裝命令。</span><span class="sxs-lookup"><span data-stu-id="21a7b-190">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="21a7b-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21a7b-191">See also</span></span>
* [<span data-ttu-id="21a7b-192">.NET Core 全域工具概觀</span><span class="sxs-lookup"><span data-stu-id="21a7b-192">.NET Core Global Tools overview</span></span>](global-tools.md)
