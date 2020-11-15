---
title: 針對 .NET 工具使用問題進行疑難排解
description: 探索執行 .NET 工具和可能的解決方案時遇到的常見問題。
author: kdollard
ms.topic: troubleshooting
ms.date: 02/14/2020
ms.openlocfilehash: c5bac4c273cdddae609657c65448e3cc4bd3579d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633904"
---
# <a name="troubleshoot-net-tool-usage-issues"></a><span data-ttu-id="7f549-103">針對 .NET 工具使用問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7f549-103">Troubleshoot .NET tool usage issues</span></span>

<span data-ttu-id="7f549-104">您可能會在嘗試安裝或執行 .NET 工具時遇到問題，這可能是通用工具或本機工具。</span><span class="sxs-lookup"><span data-stu-id="7f549-104">You might come across issues when trying to install or run a .NET tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="7f549-105">本文說明常見的根本原因和一些可能的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7f549-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-tool-fails-to-run"></a><span data-ttu-id="7f549-106">安裝的 .NET 工具無法執行</span><span class="sxs-lookup"><span data-stu-id="7f549-106">Installed .NET tool fails to run</span></span>

<span data-ttu-id="7f549-107">當 .NET 工具無法執行時，您很可能會遇到下列其中一個問題：</span><span class="sxs-lookup"><span data-stu-id="7f549-107">When a .NET tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="7f549-108">找不到工具的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7f549-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="7f549-109">找不到正確版本的 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="7f549-109">The correct version of the .NET runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="7f549-110">找不到可執行檔</span><span class="sxs-lookup"><span data-stu-id="7f549-110">Executable file not found</span></span>

<span data-ttu-id="7f549-111">如果找不到可執行檔，您會看到類似下面的訊息：</span><span class="sxs-lookup"><span data-stu-id="7f549-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="7f549-112">可執行檔的名稱會決定您叫用工具的方式。</span><span class="sxs-lookup"><span data-stu-id="7f549-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="7f549-113">下表描述格式：</span><span class="sxs-lookup"><span data-stu-id="7f549-113">The following table describes the format:</span></span>

| <span data-ttu-id="7f549-114">可執行檔名稱格式</span><span class="sxs-lookup"><span data-stu-id="7f549-114">Executable name format</span></span>  | <span data-ttu-id="7f549-115">調用格式</span><span class="sxs-lookup"><span data-stu-id="7f549-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="7f549-116">全域工具</span><span class="sxs-lookup"><span data-stu-id="7f549-116">Global tools</span></span>

  <span data-ttu-id="7f549-117">全域工具可以安裝在預設目錄或特定位置。</span><span class="sxs-lookup"><span data-stu-id="7f549-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="7f549-118">預設目錄如下：</span><span class="sxs-lookup"><span data-stu-id="7f549-118">The default directories are:</span></span>

  | <span data-ttu-id="7f549-119">OS</span><span class="sxs-lookup"><span data-stu-id="7f549-119">OS</span></span>          | <span data-ttu-id="7f549-120">路徑</span><span class="sxs-lookup"><span data-stu-id="7f549-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="7f549-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="7f549-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="7f549-122">Windows</span><span class="sxs-lookup"><span data-stu-id="7f549-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="7f549-123">如果您嘗試執行通用工具，請檢查 `PATH` 您電腦上的環境變數是否包含安裝全域工具的路徑，以及該可執行檔是否在該路徑中。</span><span class="sxs-lookup"><span data-stu-id="7f549-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="7f549-124">.NET CLI 會在第一次使用時，嘗試將預設位置新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="7f549-124">The .NET CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="7f549-125">不過，在某些情況下，位置可能不會自動新增至路徑：</span><span class="sxs-lookup"><span data-stu-id="7f549-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="7f549-126">如果您使用的是 Linux，且您已使用 *gz* 檔案安裝 .net SDK，而不是 apt 取得或 rpm。</span><span class="sxs-lookup"><span data-stu-id="7f549-126">If you're using Linux and you've installed the .NET SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="7f549-127">如果您使用的是 macOS 10.15 "Catalina" 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7f549-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="7f549-128">如果您使用 macOS 10.14 "Mojave" 或更早的版本，而您已使用 *gz* 檔案（而不是 *pkg* ）安裝 .net SDK。</span><span class="sxs-lookup"><span data-stu-id="7f549-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="7f549-129">如果您已安裝 .NET Core 3.0 SDK，而且已將 `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` 環境變數設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7f549-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="7f549-130">如果您已安裝 .NET Core 2.2 SDK 或更早版本，而且您已將 `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 環境變數設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="7f549-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="7f549-131">在這些情況下，或如果您 `--tool-path` 已指定選項，則 `PATH` 電腦上的環境變數不會自動包含您安裝全域工具的路徑。</span><span class="sxs-lookup"><span data-stu-id="7f549-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="7f549-132">在這種情況下，請將工具位置附加 (例如， `$HOME/.dotnet/tools` `PATH` 使用您的 shell 針對更新環境變數所提供的任何方法，) 至環境變數。</span><span class="sxs-lookup"><span data-stu-id="7f549-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="7f549-133">如需詳細資訊，請參閱 [.net 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="7f549-133">For more information, see [.NET tools](global-tools.md).</span></span>

* <span data-ttu-id="7f549-134">本機工具</span><span class="sxs-lookup"><span data-stu-id="7f549-134">Local tools</span></span>

  <span data-ttu-id="7f549-135">如果您嘗試執行本機工具，請確認目前目錄或其任何父目錄中有一個稱為 *dotnet-tools.js* 的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="7f549-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="7f549-136">這個檔案也可以存留在專案資料夾階層中名為 *.config* 的資料夾下，而不是根資料夾。</span><span class="sxs-lookup"><span data-stu-id="7f549-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="7f549-137">如果 *dotnet-tools.js* 存在，請開啟它，並檢查您嘗試執行的工具。</span><span class="sxs-lookup"><span data-stu-id="7f549-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="7f549-138">如果檔案未包含的專案 `"isRoot": true` ，則也請進一步檢查檔案階層中的其他工具資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="7f549-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="7f549-139">如果您嘗試執行以指定路徑安裝的 .NET 工具，則在使用此工具時必須包含該路徑。</span><span class="sxs-lookup"><span data-stu-id="7f549-139">If you're trying to run a .NET tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="7f549-140">使用工具路徑安裝的工具範例如下：</span><span class="sxs-lookup"><span data-stu-id="7f549-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="7f549-141">找不到執行時間</span><span class="sxs-lookup"><span data-stu-id="7f549-141">Runtime not found</span></span>

<span data-ttu-id="7f549-142">.NET 工具是與 [framework 相依的應用程式](../deploying/index.md#publish-framework-dependent)，這表示它們依賴電腦上所安裝的 .net 執行時間。</span><span class="sxs-lookup"><span data-stu-id="7f549-142">.NET tools are [framework-dependent applications](../deploying/index.md#publish-framework-dependent), which means they rely on a .NET runtime installed on your machine.</span></span> <span data-ttu-id="7f549-143">如果找不到預期的執行時間，則會遵循一般的 .NET 執行時間向前復原規則，例如：</span><span class="sxs-lookup"><span data-stu-id="7f549-143">If the expected runtime isn't found, they follow normal .NET runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="7f549-144">應用程式會向前復原到指定的主要和次要版本的最高修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="7f549-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="7f549-145">如果沒有符合的執行時間與主要和次要版本號碼相符，則會使用下一個較高的次要版本。</span><span class="sxs-lookup"><span data-stu-id="7f549-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="7f549-146">預覽版本的執行階段之間或預覽版本和發行版本之間，不會進行向前復原。</span><span class="sxs-lookup"><span data-stu-id="7f549-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="7f549-147">因此，使用預覽版本所建立的 .NET 工具必須由作者重建並重新發行，然後再重新安裝。</span><span class="sxs-lookup"><span data-stu-id="7f549-147">So, .NET tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="7f549-148">在兩個常見的案例中，預設不會進行向前復原：</span><span class="sxs-lookup"><span data-stu-id="7f549-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="7f549-149">只有較低的執行階段版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="7f549-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="7f549-150">向前復原只會選取較新版本的執行時間。</span><span class="sxs-lookup"><span data-stu-id="7f549-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="7f549-151">只有較高的執行時間主要版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="7f549-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="7f549-152">向前復原不會跨主要版本界限。</span><span class="sxs-lookup"><span data-stu-id="7f549-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="7f549-153">如果應用程式找不到適當的執行時間，它就無法執行，而且會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f549-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="7f549-154">您可以使用下列其中一個命令找出安裝在電腦上的 .NET 執行時間：</span><span class="sxs-lookup"><span data-stu-id="7f549-154">You can find out which .NET runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="7f549-155">如果您認為工具應該支援您目前已安裝的執行階段版本，您可以與工具作者聯繫，看看他們是否可以更新版本號碼或多目標。</span><span class="sxs-lookup"><span data-stu-id="7f549-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="7f549-156">一旦使用更新的版本號碼重新編譯並將其工具套件重新發行至 NuGet 之後，您就可以更新您的複本。</span><span class="sxs-lookup"><span data-stu-id="7f549-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="7f549-157">雖然這不會發生，但是最快的解決方案就是安裝可使用您嘗試執行之工具的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7f549-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="7f549-158">若要下載特定的 .NET 執行階段版本，請造訪 [.net 下載頁面](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7f549-158">To download a specific .NET runtime version, visit the [.NET download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="7f549-159">如果您將 .NET SDK 安裝至非預設位置，則必須將環境變數設定 `DOTNET_ROOT` 為包含 `dotnet` 可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="7f549-159">If you install the .NET SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-tool-installation-fails"></a><span data-ttu-id="7f549-160">.NET 工具安裝失敗</span><span class="sxs-lookup"><span data-stu-id="7f549-160">.NET tool installation fails</span></span>

<span data-ttu-id="7f549-161">.NET 全域或本機工具安裝可能會失敗的原因有很多。</span><span class="sxs-lookup"><span data-stu-id="7f549-161">There are a number of reasons the installation of a .NET global or local tool may fail.</span></span> <span data-ttu-id="7f549-162">當工具安裝失敗時，您會看到類似下面的訊息：</span><span class="sxs-lookup"><span data-stu-id="7f549-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="7f549-163">為了協助診斷這些失敗，NuGet 訊息會直接向使用者顯示，以及先前的訊息。</span><span class="sxs-lookup"><span data-stu-id="7f549-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="7f549-164">NuGet 訊息可協助您找出問題。</span><span class="sxs-lookup"><span data-stu-id="7f549-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="7f549-165">強制執行套件命名</span><span class="sxs-lookup"><span data-stu-id="7f549-165">Package naming enforcement</span></span>

<span data-ttu-id="7f549-166">Microsoft 已針對工具的套件識別碼變更其指導方針，導致找不到具有預測名稱的一些工具。</span><span class="sxs-lookup"><span data-stu-id="7f549-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="7f549-167">新的指引是所有的 Microsoft 工具前面都會加上「Microsoft」。</span><span class="sxs-lookup"><span data-stu-id="7f549-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="7f549-168">這個前置詞是保留的，而且只能用於使用 Microsoft 授權憑證簽署的套件。</span><span class="sxs-lookup"><span data-stu-id="7f549-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="7f549-169">在轉換期間，有些 Microsoft 工具會有舊版的套件識別碼，有些則會有新的表單：</span><span class="sxs-lookup"><span data-stu-id="7f549-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="7f549-170">更新套件識別碼時，您必須變更為新的套件識別碼，才能取得最新的更新。</span><span class="sxs-lookup"><span data-stu-id="7f549-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="7f549-171">具有簡化工具名稱的封裝將會被取代。</span><span class="sxs-lookup"><span data-stu-id="7f549-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="7f549-172">預覽版本</span><span class="sxs-lookup"><span data-stu-id="7f549-172">Preview releases</span></span>

* <span data-ttu-id="7f549-173">您正在嘗試安裝預覽版本，但未使用此 `--version` 選項來指定版本。</span><span class="sxs-lookup"><span data-stu-id="7f549-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="7f549-174">處於預覽狀態的 .NET 工具必須以部分名稱指定，以表示它們處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="7f549-174">.NET tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="7f549-175">您不需要包含整個預覽。</span><span class="sxs-lookup"><span data-stu-id="7f549-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="7f549-176">假設版本號碼採用預期的格式，您可以使用如下列範例所示的內容：</span><span class="sxs-lookup"><span data-stu-id="7f549-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-tool"></a><span data-ttu-id="7f549-177">套件不是 .NET 工具</span><span class="sxs-lookup"><span data-stu-id="7f549-177">Package isn't a .NET tool</span></span>

* <span data-ttu-id="7f549-178">找到此名稱的 NuGet 套件，但它不是 .NET 工具。</span><span class="sxs-lookup"><span data-stu-id="7f549-178">A NuGet package by this name was found, but it wasn't a .NET tool.</span></span>

<span data-ttu-id="7f549-179">如果您嘗試安裝的 NuGet 套件是一般 NuGet 套件，而不是 .NET 工具，您將會看到類似下面的錯誤：</span><span class="sxs-lookup"><span data-stu-id="7f549-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="7f549-180">NU1212：的專案套件組合無效 `<ToolName>` 。</span><span class="sxs-lookup"><span data-stu-id="7f549-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="7f549-181">DotnetToolReference 專案樣式只能包含 DotnetTool 類型的參考。</span><span class="sxs-lookup"><span data-stu-id="7f549-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="7f549-182">無法存取 NuGet 摘要</span><span class="sxs-lookup"><span data-stu-id="7f549-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="7f549-183">無法存取必要的 NuGet 摘要，可能是因為網際網路連線問題。</span><span class="sxs-lookup"><span data-stu-id="7f549-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="7f549-184">工具安裝需要存取包含工具套件的 NuGet 摘要。</span><span class="sxs-lookup"><span data-stu-id="7f549-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="7f549-185">如果無法使用摘要，它就會失敗。</span><span class="sxs-lookup"><span data-stu-id="7f549-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="7f549-186">您可以使用切換來改變摘要 `nuget.config` 、要求特定檔案 `nuget.config` ，或使用參數指定其他摘要 `--add-source` 。</span><span class="sxs-lookup"><span data-stu-id="7f549-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="7f549-187">根據預設，NuGet 會針對無法連接的任何摘要擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f549-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="7f549-188">旗標 `--ignore-failed-sources` 可以略過這些不可連線的來源。</span><span class="sxs-lookup"><span data-stu-id="7f549-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="7f549-189">套件識別碼不正確</span><span class="sxs-lookup"><span data-stu-id="7f549-189">Package ID incorrect</span></span>

* <span data-ttu-id="7f549-190">您的工具名稱輸入錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f549-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="7f549-191">失敗的常見原因是工具名稱不正確。</span><span class="sxs-lookup"><span data-stu-id="7f549-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="7f549-192">這可能是因為不正確，或是工具已移動或已淘汰。</span><span class="sxs-lookup"><span data-stu-id="7f549-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="7f549-193">針對 NuGet.org 上的工具，確保您的名稱正確的其中一種方式是在 NuGet.org 搜尋工具，然後複製安裝命令。</span><span class="sxs-lookup"><span data-stu-id="7f549-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f549-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f549-194">See also</span></span>

* [<span data-ttu-id="7f549-195">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="7f549-195">.NET tools</span></span>](global-tools.md)
