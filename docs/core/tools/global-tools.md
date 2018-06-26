---
title: .NET Core 通用工具
description: 說明何為 .NET Core 通用工具以及它們可用之 .NET Core CLI 命令的概觀。
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697088"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="94448-103">.NET Core 通用工具概觀</span><span class="sxs-lookup"><span data-stu-id="94448-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="94448-104">.NET Core 通用工具是包含主控台應用程式的特殊 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="94448-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="94448-105">通用工具可以安裝在您電腦上的預設位置 (其包含在 PATH 環境變數中) 或自訂位置。</span><span class="sxs-lookup"><span data-stu-id="94448-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="94448-106">如果您想要使用 .NET Core 通用工具：</span><span class="sxs-lookup"><span data-stu-id="94448-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="94448-107">尋找工具的相關資訊 (通常是網站或 GitHub 網頁)。</span><span class="sxs-lookup"><span data-stu-id="94448-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="94448-108">檢查首頁中作者和統計資料的摘要 (通常是 NuGet.org)。</span><span class="sxs-lookup"><span data-stu-id="94448-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="94448-109">安裝工具。</span><span class="sxs-lookup"><span data-stu-id="94448-109">Install the tool.</span></span>
* <span data-ttu-id="94448-110">呼叫工具。</span><span class="sxs-lookup"><span data-stu-id="94448-110">Call the tool.</span></span>
* <span data-ttu-id="94448-111">更新工具。</span><span class="sxs-lookup"><span data-stu-id="94448-111">Update the tool.</span></span>
* <span data-ttu-id="94448-112">解除安裝工具。</span><span class="sxs-lookup"><span data-stu-id="94448-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94448-113">.NET Core 通用工具會顯示在您的路徑中，並且在完全信任環境下執行。</span><span class="sxs-lookup"><span data-stu-id="94448-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="94448-114">除非您信任作者，否則請勿安裝 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="94448-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="94448-115">尋找 .NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="94448-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="94448-116">目前，.NET Core 命令列介面 (CLI) 中沒有通用工具搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="94448-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="94448-117">您可以在 [NuGet](https://www.nuget.org) 上找到 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="94448-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="94448-118">不過，NuGet 尚未允許您專門搜尋 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="94448-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="94448-119">您也可以在部落格文章或 [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub 存放庫中找到工具建議。</span><span class="sxs-lookup"><span data-stu-id="94448-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="94448-120">還可以在 [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub 存放庫中看到 ASP.NET 小組所建立之通用工具的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="94448-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="94448-121">檢查作者和統計資料</span><span class="sxs-lookup"><span data-stu-id="94448-121">Check the author and statistics</span></span>

<span data-ttu-id="94448-122">由於 .NET Core 通用工具在完全信任環境下執行，而且通常是安裝在您的路徑上，它們可以發揮極為強大的功能。</span><span class="sxs-lookup"><span data-stu-id="94448-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="94448-123">請不要下載來自不信任人員的工具。</span><span class="sxs-lookup"><span data-stu-id="94448-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="94448-124">如果此工具裝載在 NuGet 上，您可以搜尋工具來檢查作者和統計資料。</span><span class="sxs-lookup"><span data-stu-id="94448-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="94448-125">安裝通用工具</span><span class="sxs-lookup"><span data-stu-id="94448-125">Install a Global Tool</span></span>

<span data-ttu-id="94448-126">若要安裝通用工具，您可以使用 [dotnet tool install](dotnet-tool-install.md) .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="94448-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="94448-127">下列範例會示範如何在預設位置安裝通用工具：</span><span class="sxs-lookup"><span data-stu-id="94448-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="94448-128">如果無法安裝此工具，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="94448-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="94448-129">請確認正在檢查您所預期的摘要。</span><span class="sxs-lookup"><span data-stu-id="94448-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="94448-130">如果您要嘗試安裝發行前版本或特定版本的工具，可以使用下列格式指定版本號碼：</span><span class="sxs-lookup"><span data-stu-id="94448-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="94448-131">如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：</span><span class="sxs-lookup"><span data-stu-id="94448-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="94448-132">通用工具可以安裝在預設目錄或特定位置中。</span><span class="sxs-lookup"><span data-stu-id="94448-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="94448-133">預設目錄如下：</span><span class="sxs-lookup"><span data-stu-id="94448-133">The default directories are:</span></span>

| <span data-ttu-id="94448-134">作業系統</span><span class="sxs-lookup"><span data-stu-id="94448-134">OS</span></span>          | <span data-ttu-id="94448-135">路徑</span><span class="sxs-lookup"><span data-stu-id="94448-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="94448-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="94448-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="94448-137">Windows</span><span class="sxs-lookup"><span data-stu-id="94448-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="94448-138">第一次執行 SDK　時，這些位置會新增至使用者的路徑，因此可以直接呼叫安裝在該處的通用工具。</span><span class="sxs-lookup"><span data-stu-id="94448-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="94448-139">請注意，通用工具是使用者特定工具，而不是電腦全域工具。</span><span class="sxs-lookup"><span data-stu-id="94448-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="94448-140">使用者特定表示您無法安裝可供電腦上所有使用者使用的通用工具。</span><span class="sxs-lookup"><span data-stu-id="94448-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="94448-141">此工具只適用於已安裝工具的每個使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="94448-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="94448-142">通用工具也可以安裝在特定目錄中。</span><span class="sxs-lookup"><span data-stu-id="94448-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="94448-143">安裝在特定目錄時，使用者必須確保命令可用，方法是在路徑中包含該目錄、使用指定的目錄呼叫命令，或從指定的目錄中呼叫工具。</span><span class="sxs-lookup"><span data-stu-id="94448-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="94448-144">在此情況下，.NET Core CLI 不會將這個位置自動新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="94448-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="94448-145">使用工具</span><span class="sxs-lookup"><span data-stu-id="94448-145">Use the tool</span></span>

<span data-ttu-id="94448-146">安裝此工具之後，您可以使用其命令進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="94448-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="94448-147">請注意，命令可能無法與套件名稱相同。</span><span class="sxs-lookup"><span data-stu-id="94448-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="94448-148">如果命令是 `dotnetsay`，呼叫時請使用：</span><span class="sxs-lookup"><span data-stu-id="94448-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="94448-149">如果工具作者想要工具顯示在 `dotnet` 提示的內容中，他們可能會以稱為 `dotnet <command>` 的方式進行撰寫，例如：</span><span class="sxs-lookup"><span data-stu-id="94448-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="94448-150">您可以藉由使用 [dotnet tool list](dotnet-tool-list.md) 命令列出已安裝的套件，了解已安裝的通用工具套件中包含哪些工具。</span><span class="sxs-lookup"><span data-stu-id="94448-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="94448-151">您也可以在工具的網站中，或鍵入下列其中一個命令來尋找使用方式指示：</span><span class="sxs-lookup"><span data-stu-id="94448-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="94448-152">可能會發生什麼問題</span><span class="sxs-lookup"><span data-stu-id="94448-152">What could go wrong</span></span>

<span data-ttu-id="94448-153">通用工具是[與架構相依的應用程式](../deploying/index.md#framework-dependent-deployments-fdd)，這表示它們會依賴電腦上安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="94448-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="94448-154">如果找不到預期的執行階段，則會遵循一般的 .NET Core 執行階段向前復原規則，例如：</span><span class="sxs-lookup"><span data-stu-id="94448-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="94448-155">應用程式會向前復原到指定的主要和次要版本的最高修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="94448-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="94448-156">如果沒有與符合的主要和次要版本號碼相符的執行階段，則會使用下一個較高的次要版本。</span><span class="sxs-lookup"><span data-stu-id="94448-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="94448-157">預覽版本的執行階段之間或預覽版本和發行版本之間，不會進行向前復原。</span><span class="sxs-lookup"><span data-stu-id="94448-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="94448-158">因此，使用預覽版本所建立的通用工具必須重建、由作者重新發行，以及重新安裝。</span><span class="sxs-lookup"><span data-stu-id="94448-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="94448-159">在 .NET Core 2.1 Preview 1 中建立的通用工具可能會發生其他問題。</span><span class="sxs-lookup"><span data-stu-id="94448-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="94448-160">如需詳細資訊，請參閱 [.NET Core 2.1 Preview 2 的已知問題](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="94448-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="94448-161">如果應用程式找不到適當的執行階段，則無法執行，並且會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="94448-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="94448-162">另一個可能發生的問題是：使用目前安裝的 .NET Core 執行階段，可能無法執行較早預覽期間所建立的通用工具。</span><span class="sxs-lookup"><span data-stu-id="94448-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="94448-163">您可以使用下列命令，查看您的電腦上安裝了哪些執行階段：</span><span class="sxs-lookup"><span data-stu-id="94448-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="94448-164">請連絡通用工具的作者，確認他們是否可以重新編譯其工具套件，並以更新的版本號碼重新發行至 NuGet。</span><span class="sxs-lookup"><span data-stu-id="94448-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="94448-165">一旦他們更新 NuGet 上的套件之後，您就可以更新您的複本。</span><span class="sxs-lookup"><span data-stu-id="94448-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="94448-166">.NET Core CLI 會在第一次使用時，嘗試將預設位置新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="94448-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="94448-167">不過，有幾種情況可能不會將位置自動新增至 PATH，例如：</span><span class="sxs-lookup"><span data-stu-id="94448-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="94448-168">如果您已設定 `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="94448-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="94448-169">在 macOS 上，如果您已使用 *.tar.gz* 檔案 (而非 *.pkg*) 安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="94448-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="94448-170">在 Linux 上，您需要編輯殼層環境檔案來設定 PATH。</span><span class="sxs-lookup"><span data-stu-id="94448-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="94448-171">其他 CLI 命令</span><span class="sxs-lookup"><span data-stu-id="94448-171">Other CLI commands</span></span>

<span data-ttu-id="94448-172">.NET Core SDK 包含其他支援 .NET Core 通用工具的命令。</span><span class="sxs-lookup"><span data-stu-id="94448-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="94448-173">請使用任何 `dotnet tool` 命令搭配下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="94448-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="94448-174">`--global` 或 `-g` 指定命令適用於使用者範圍通用工具。</span><span class="sxs-lookup"><span data-stu-id="94448-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="94448-175">`--tool-path` 指定通用工具的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="94448-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="94448-176">若要查看哪些命令適用於通用工具：</span><span class="sxs-lookup"><span data-stu-id="94448-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="94448-177">更新通用工具需要解除安裝再使用最新的穩定版本重新安裝。</span><span class="sxs-lookup"><span data-stu-id="94448-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="94448-178">若要更新通用工具，請使用 [dotnet tool update](dotnet-tool-update.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="94448-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="94448-179">使用 [dotnet tool uninstall](dotnet-tool-uninstall.md) 移除通用工具：</span><span class="sxs-lookup"><span data-stu-id="94448-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="94448-180">若要顯示電腦上目前已安裝的所有通用工具，以及它們的版本和命令，請使用 [dotnet tool list](dotnet-tool-list.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="94448-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```