---
title: 排除 .NET 核心工具使用問題
description: 在運行 .NET 核心工具和可能的解決方案時發現常見問題。
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146446"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="5a00d-103">排除 .NET 核心工具使用問題</span><span class="sxs-lookup"><span data-stu-id="5a00d-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="5a00d-104">在嘗試安裝或運行 .NET Core 工具時可能會遇到問題，該工具可以是全域工具或本地工具。</span><span class="sxs-lookup"><span data-stu-id="5a00d-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="5a00d-105">本文介紹了常見根本原因和一些可能的解決方案。</span><span class="sxs-lookup"><span data-stu-id="5a00d-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="5a00d-106">已安裝 .NET 核心工具無法運行</span><span class="sxs-lookup"><span data-stu-id="5a00d-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="5a00d-107">當 .NET Core 工具無法運行時，您最有可能遇到以下問題之一：</span><span class="sxs-lookup"><span data-stu-id="5a00d-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="5a00d-108">找不到該工具的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="5a00d-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="5a00d-109">找不到 .NET 核心運行時的正確版本。</span><span class="sxs-lookup"><span data-stu-id="5a00d-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="5a00d-110">找不到可執行檔</span><span class="sxs-lookup"><span data-stu-id="5a00d-110">Executable file not found</span></span>

<span data-ttu-id="5a00d-111">如果未找到可執行檔，您將看到類似于以下內容的消息：</span><span class="sxs-lookup"><span data-stu-id="5a00d-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="5a00d-112">可執行檔的名稱決定了如何調用該工具。</span><span class="sxs-lookup"><span data-stu-id="5a00d-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="5a00d-113">下表描述了格式：</span><span class="sxs-lookup"><span data-stu-id="5a00d-113">The following table describes the format:</span></span>

| <span data-ttu-id="5a00d-114">可執行名稱格式</span><span class="sxs-lookup"><span data-stu-id="5a00d-114">Executable name format</span></span>  | <span data-ttu-id="5a00d-115">調用格式</span><span class="sxs-lookup"><span data-stu-id="5a00d-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="5a00d-116">全域工具</span><span class="sxs-lookup"><span data-stu-id="5a00d-116">Global tools</span></span>

  <span data-ttu-id="5a00d-117">全域工具可以安裝在預設目錄或特定位置。</span><span class="sxs-lookup"><span data-stu-id="5a00d-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="5a00d-118">預設目錄如下：</span><span class="sxs-lookup"><span data-stu-id="5a00d-118">The default directories are:</span></span>

  | <span data-ttu-id="5a00d-119">OS</span><span class="sxs-lookup"><span data-stu-id="5a00d-119">OS</span></span>          | <span data-ttu-id="5a00d-120">Path</span><span class="sxs-lookup"><span data-stu-id="5a00d-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="5a00d-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="5a00d-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="5a00d-122">Windows</span><span class="sxs-lookup"><span data-stu-id="5a00d-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="5a00d-123">如果嘗試運行全域工具，請檢查電腦上的`PATH`環境變數是否包含安裝全域工具的路徑，以及可執行檔是否位於該路徑中。</span><span class="sxs-lookup"><span data-stu-id="5a00d-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="5a00d-124">.NET 核心 CLI 嘗試在其首次使用時將預設位置添加到 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="5a00d-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="5a00d-125">但是，在某些情況下，位置可能無法自動添加到 PATH：</span><span class="sxs-lookup"><span data-stu-id="5a00d-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="5a00d-126">如果您使用的是 Linux，並且已使用 *.tar.gz*檔安裝了 .NET Core SDK，而不是 apt-get 或 rpm。</span><span class="sxs-lookup"><span data-stu-id="5a00d-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="5a00d-127">如果您使用的是 macOS 10.15"Catalina"或更高版本。</span><span class="sxs-lookup"><span data-stu-id="5a00d-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="5a00d-128">如果您使用的是 macOS 10.14"Mojave"或早期版本，並且已安裝 .NET Core SDK 使用 *.tar.gz*檔而不是 *.pkg*。</span><span class="sxs-lookup"><span data-stu-id="5a00d-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="5a00d-129">如果您安裝了 .NET Core 3.0 SDK，並且將`DOTNET_ADD_GLOBAL_TOOLS_TO_PATH`環境變數設置為`false`。</span><span class="sxs-lookup"><span data-stu-id="5a00d-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="5a00d-130">如果您已安裝 .NET Core 2.2 SDK 或早期版本，並且將`DOTNET_SKIP_FIRST_TIME_EXPERIENCE`環境變數設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="5a00d-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="5a00d-131">在這些情況下，或者如果指定了`--tool-path`該選項，電腦上的`PATH`環境變數不會自動包含安裝全域工具的路徑。</span><span class="sxs-lookup"><span data-stu-id="5a00d-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="5a00d-132">在這種情況下，通過使用 shell 為更新`$HOME/.dotnet/tools``PATH`環境變數提供的任何方法將工具位置（例如 ，）追加到環境變數。</span><span class="sxs-lookup"><span data-stu-id="5a00d-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="5a00d-133">有關詳細資訊，請參閱[.NET 核心工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5a00d-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="5a00d-134">本機工具</span><span class="sxs-lookup"><span data-stu-id="5a00d-134">Local tools</span></span>

  <span data-ttu-id="5a00d-135">如果您嘗試運行本地工具，請驗證目前的目錄中是否有名為*dotnet-tools.json*的清單檔或其任何父目錄。</span><span class="sxs-lookup"><span data-stu-id="5a00d-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="5a00d-136">此檔還可以位於專案資料夾層次結構中任何位置的名為 *.config*的資料夾下，而不是根資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a00d-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="5a00d-137">如果*dotnet 工具.json*存在，請打開它並檢查您嘗試運行的工具。</span><span class="sxs-lookup"><span data-stu-id="5a00d-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="5a00d-138">如果檔不包含 的`"isRoot": true`條目，則還會進一步檢查檔層次結構中的其他工具清單檔。</span><span class="sxs-lookup"><span data-stu-id="5a00d-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="5a00d-139">如果嘗試運行使用指定路徑安裝的 .NET Core 工具，則需要在使用該工具時包括該路徑。</span><span class="sxs-lookup"><span data-stu-id="5a00d-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="5a00d-140">使用工具路徑安裝工具的示例包括：</span><span class="sxs-lookup"><span data-stu-id="5a00d-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="5a00d-141">未找到運行時</span><span class="sxs-lookup"><span data-stu-id="5a00d-141">Runtime not found</span></span>

<span data-ttu-id="5a00d-142">.NET Core 工具是[依賴于框架的應用程式](../deploying/index.md#publish-runtime-dependent)，這意味著它們依賴于電腦上安裝的 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="5a00d-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="5a00d-143">如果未找到預期的運行時，它們將遵循正常的 .NET Core 運行時前滾規則，例如：</span><span class="sxs-lookup"><span data-stu-id="5a00d-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="5a00d-144">應用程式會向前復原到指定的主要和次要版本的最高修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="5a00d-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="5a00d-145">如果沒有匹配的主要版本號和次要版本號的匹配運行時，則使用下一個較高的次要版本。</span><span class="sxs-lookup"><span data-stu-id="5a00d-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="5a00d-146">預覽版本的執行階段之間或預覽版本和發行版本之間，不會進行向前復原。</span><span class="sxs-lookup"><span data-stu-id="5a00d-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="5a00d-147">因此，使用預覽版本創建的 .NET Core 工具必須由作者重新生成並重新發佈並重新安裝。</span><span class="sxs-lookup"><span data-stu-id="5a00d-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="5a00d-148">預設情況下，在兩種常見方案中不會發生前滾：</span><span class="sxs-lookup"><span data-stu-id="5a00d-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="5a00d-149">只有較低版本的運行時可用。</span><span class="sxs-lookup"><span data-stu-id="5a00d-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="5a00d-150">前滾僅選擇更高版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="5a00d-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="5a00d-151">只有更高的主要執行階段版本可用。</span><span class="sxs-lookup"><span data-stu-id="5a00d-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="5a00d-152">前滾不會跨越主要版本邊界。</span><span class="sxs-lookup"><span data-stu-id="5a00d-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="5a00d-153">如果應用程式找不到適當的運行時，它將無法運行並報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a00d-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="5a00d-154">您可以使用以下命令之一瞭解電腦上安裝了哪些 .NET Core 運行時：</span><span class="sxs-lookup"><span data-stu-id="5a00d-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="5a00d-155">如果您認為該工具應支援當前安裝的執行階段版本，可以聯繫工具作者，看看他們是否可以更新版本號或多目標。</span><span class="sxs-lookup"><span data-stu-id="5a00d-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="5a00d-156">一旦他們重新編譯並重新發佈其工具組到 NuGet 與更新的版本號，您可以更新您的副本。</span><span class="sxs-lookup"><span data-stu-id="5a00d-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="5a00d-157">雖然這種情況不會發生，但最快的解決方案是安裝一個執行階段版本，該版本將與您嘗試運行的工具配合使用。</span><span class="sxs-lookup"><span data-stu-id="5a00d-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="5a00d-158">要下載特定的 .NET 酷睿執行階段版本，請訪問[.NET 核心下載頁面](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="5a00d-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="5a00d-159">如果將 .NET Core SDK 安裝到非預設位置，則需要將環境變數`DOTNET_ROOT`設置為包含`dotnet`可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="5a00d-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="5a00d-160">.NET 核心工具安裝失敗</span><span class="sxs-lookup"><span data-stu-id="5a00d-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="5a00d-161">安裝 .NET Core 全域或本地工具可能會失敗的原因有很多。</span><span class="sxs-lookup"><span data-stu-id="5a00d-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="5a00d-162">當工具安裝失敗時，您將看到類似于以下內容的消息：</span><span class="sxs-lookup"><span data-stu-id="5a00d-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="5a00d-163">為了説明診斷這些故障，NuGet 消息將直接顯示給使用者，以及上一條消息。</span><span class="sxs-lookup"><span data-stu-id="5a00d-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="5a00d-164">NuGet 消息可以説明您識別問題。</span><span class="sxs-lookup"><span data-stu-id="5a00d-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="5a00d-165">包命名強制</span><span class="sxs-lookup"><span data-stu-id="5a00d-165">Package naming enforcement</span></span>

<span data-ttu-id="5a00d-166">Microsoft 更改了對工具的包 ID 的指導，導致找不到許多具有預測名稱的工具。</span><span class="sxs-lookup"><span data-stu-id="5a00d-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="5a00d-167">新的指南是，所有 Microsoft 工具都預綴于"微軟"。</span><span class="sxs-lookup"><span data-stu-id="5a00d-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="5a00d-168">此首碼是保留的，只能用於使用 Microsoft 授權證書簽名的包。</span><span class="sxs-lookup"><span data-stu-id="5a00d-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="5a00d-169">在過渡期間，某些 Microsoft 工具將具有舊形式的包 ID，而其他工具將具有新形式：</span><span class="sxs-lookup"><span data-stu-id="5a00d-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="5a00d-170">更新包 ID 後，您需要更改為新的包 ID 以獲取最新更新。</span><span class="sxs-lookup"><span data-stu-id="5a00d-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="5a00d-171">使用簡化工具名稱的包將被棄用。</span><span class="sxs-lookup"><span data-stu-id="5a00d-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="5a00d-172">預覽版本</span><span class="sxs-lookup"><span data-stu-id="5a00d-172">Preview releases</span></span>

* <span data-ttu-id="5a00d-173">您正在嘗試安裝預覽版本，但沒有使用`--version`該選項來指定版本。</span><span class="sxs-lookup"><span data-stu-id="5a00d-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="5a00d-174">預覽中的 .NET 核心工具必須使用名稱的一部分進行指定，以指示它們處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="5a00d-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="5a00d-175">您無需包括整個預覽。</span><span class="sxs-lookup"><span data-stu-id="5a00d-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="5a00d-176">假設版本號採用預期格式，則可以使用類似下面的示例：</span><span class="sxs-lookup"><span data-stu-id="5a00d-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="5a00d-177">包不是 .NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="5a00d-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="5a00d-178">找到此名稱的 NuGet 包，但它不是 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="5a00d-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="5a00d-179">如果您嘗試安裝 NuGet 包，該包是常規 NuGet 包，而不是 .NET Core 工具，您將看到類似于以下內容的錯誤：</span><span class="sxs-lookup"><span data-stu-id="5a00d-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="5a00d-180">NU1212：不正確專案`<ToolName>`包組合。</span><span class="sxs-lookup"><span data-stu-id="5a00d-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="5a00d-181">DotnetTool 參考專案樣式只能包含 DotnetTool 類型的引用。</span><span class="sxs-lookup"><span data-stu-id="5a00d-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="5a00d-182">無法訪問 NuGet 源</span><span class="sxs-lookup"><span data-stu-id="5a00d-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="5a00d-183">無法訪問所需的 NuGet 源，可能是因為 Internet 連接問題。</span><span class="sxs-lookup"><span data-stu-id="5a00d-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="5a00d-184">工具安裝需要訪問包含工具組的 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="5a00d-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="5a00d-185">如果源不可用，它將失敗。</span><span class="sxs-lookup"><span data-stu-id="5a00d-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="5a00d-186">您可以使用 更改 源`nuget.config`，請求特定`nuget.config`檔，或使用`--add-source`交換器指定其他源。</span><span class="sxs-lookup"><span data-stu-id="5a00d-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="5a00d-187">預設情況下，NuGet 會為無法連接的任何源引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a00d-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="5a00d-188">標誌`--ignore-failed-sources`可以跳過這些無法訪問的源。</span><span class="sxs-lookup"><span data-stu-id="5a00d-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="5a00d-189">包 ID 不正確</span><span class="sxs-lookup"><span data-stu-id="5a00d-189">Package ID incorrect</span></span>

* <span data-ttu-id="5a00d-190">鍵入工具的名稱錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a00d-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="5a00d-191">失敗的一個常見原因是工具名稱不正確。</span><span class="sxs-lookup"><span data-stu-id="5a00d-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="5a00d-192">這可能是由於霧化，或者因為工具移動或被棄用。</span><span class="sxs-lookup"><span data-stu-id="5a00d-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="5a00d-193">對於NuGet.org上的工具，確保名稱正確的方法之一是在NuGet.org處搜索該工具並複製安裝命令。</span><span class="sxs-lookup"><span data-stu-id="5a00d-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a00d-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a00d-194">See also</span></span>

* [<span data-ttu-id="5a00d-195">.NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="5a00d-195">.NET Core tools</span></span>](global-tools.md)
