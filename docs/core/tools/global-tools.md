---
title: .NET Core 通用工具
description: 說明何為 .NET Core 通用工具以及它們可用之 .NET Core CLI 命令的概觀。
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 665cee64cb92efd16f5528feb656b377f9f3283c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714164"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="c821e-103">.NET Core 通用工具概觀</span><span class="sxs-lookup"><span data-stu-id="c821e-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="c821e-104">.NET Core 通用工具是包含主控台應用程式的特殊 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c821e-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="c821e-105">通用工具可以安裝在您電腦上的預設位置 (其包含在 PATH 環境變數中) 或自訂位置。</span><span class="sxs-lookup"><span data-stu-id="c821e-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="c821e-106">如果您想要使用 .NET Core 通用工具：</span><span class="sxs-lookup"><span data-stu-id="c821e-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="c821e-107">尋找工具的相關資訊 (通常是網站或 GitHub 網頁)。</span><span class="sxs-lookup"><span data-stu-id="c821e-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="c821e-108">檢查首頁中作者和統計資料的摘要 (通常是 NuGet.org)。</span><span class="sxs-lookup"><span data-stu-id="c821e-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="c821e-109">安裝工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-109">Install the tool.</span></span>
* <span data-ttu-id="c821e-110">呼叫工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-110">Call the tool.</span></span>
* <span data-ttu-id="c821e-111">更新工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-111">Update the tool.</span></span>
* <span data-ttu-id="c821e-112">解除安裝工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c821e-113">.NET Core 通用工具會顯示在您的路徑中，並且在完全信任環境下執行。</span><span class="sxs-lookup"><span data-stu-id="c821e-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="c821e-114">除非您信任作者，否則請勿安裝 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="c821e-115">尋找 .NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="c821e-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="c821e-116">目前，.NET Core 命令列介面 (CLI) 中沒有通用工具搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="c821e-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span> <span data-ttu-id="c821e-117">以下是如何尋找工具的一些建議：</span><span class="sxs-lookup"><span data-stu-id="c821e-117">The following are some recommendations on how to find tools:</span></span>

* <span data-ttu-id="c821e-118">您可以在 [NuGet](https://www.nuget.org) 上找到 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-118">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="c821e-119">不過，NuGet 尚未允許您專門搜尋 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-119">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>
* <span data-ttu-id="c821e-120">您可以在 blog 文章或[natemcmaster/dotnet 工具](https://github.com/natemcmaster/dotnet-tools)GitHub 存放庫中找到工具建議。</span><span class="sxs-lookup"><span data-stu-id="c821e-120">You may find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="c821e-121">您可以在[aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub 存放庫中查看 ASP.NET 小組所建立之通用工具的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="c821e-121">You can see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>
* <span data-ttu-id="c821e-122">您可以在[.Net Core dotnet 診斷通用工具](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)瞭解診斷工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-122">You can learn about diagnostic tools at [.NET Core dotnet diagnostic Global Tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="c821e-123">檢查作者和統計資料</span><span class="sxs-lookup"><span data-stu-id="c821e-123">Check the author and statistics</span></span>

<span data-ttu-id="c821e-124">由於 .NET Core 通用工具在完全信任環境下執行，而且通常是安裝在您的路徑上，它們可以發揮極為強大的功能。</span><span class="sxs-lookup"><span data-stu-id="c821e-124">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="c821e-125">請不要下載來自不信任人員的工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-125">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="c821e-126">如果此工具裝載在 NuGet 上，您可以搜尋工具來檢查作者和統計資料。</span><span class="sxs-lookup"><span data-stu-id="c821e-126">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="c821e-127">安裝通用工具</span><span class="sxs-lookup"><span data-stu-id="c821e-127">Install a Global Tool</span></span>

<span data-ttu-id="c821e-128">若要安裝通用工具，您可以使用 [dotnet tool install](dotnet-tool-install.md) .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="c821e-128">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="c821e-129">下列範例會示範如何在預設位置安裝通用工具：</span><span class="sxs-lookup"><span data-stu-id="c821e-129">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="c821e-130">如果無法安裝此工具，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c821e-130">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="c821e-131">請確認正在檢查您所預期的摘要。</span><span class="sxs-lookup"><span data-stu-id="c821e-131">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="c821e-132">如果您要嘗試安裝發行前版本或特定版本的工具，可以使用下列格式指定版本號碼：</span><span class="sxs-lookup"><span data-stu-id="c821e-132">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="c821e-133">如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：</span><span class="sxs-lookup"><span data-stu-id="c821e-133">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="c821e-134">通用工具可以安裝在預設目錄或特定位置中。</span><span class="sxs-lookup"><span data-stu-id="c821e-134">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="c821e-135">預設目錄如下：</span><span class="sxs-lookup"><span data-stu-id="c821e-135">The default directories are:</span></span>

| <span data-ttu-id="c821e-136">作業系統</span><span class="sxs-lookup"><span data-stu-id="c821e-136">OS</span></span>          | <span data-ttu-id="c821e-137">{2&gt;路徑&lt;2}</span><span class="sxs-lookup"><span data-stu-id="c821e-137">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="c821e-138">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="c821e-138">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="c821e-139">Windows</span><span class="sxs-lookup"><span data-stu-id="c821e-139">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="c821e-140">第一次執行 SDK　時，這些位置會新增至使用者的路徑，因此可以直接呼叫安裝在該處的通用工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-140">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="c821e-141">請注意，通用工具是使用者特定工具，而不是電腦全域工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-141">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="c821e-142">使用者特定表示您無法安裝可供電腦上所有使用者使用的通用工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-142">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="c821e-143">此工具只適用於已安裝工具的每個使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="c821e-143">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="c821e-144">通用工具也可以安裝在特定目錄中。</span><span class="sxs-lookup"><span data-stu-id="c821e-144">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="c821e-145">安裝在特定目錄時，使用者必須確保命令可用，方法是在路徑中包含該目錄、使用指定的目錄呼叫命令，或從指定的目錄中呼叫工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-145">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="c821e-146">在此情況下，.NET Core CLI 不會將這個位置自動新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="c821e-146">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="c821e-147">使用工具</span><span class="sxs-lookup"><span data-stu-id="c821e-147">Use the tool</span></span>

<span data-ttu-id="c821e-148">安裝此工具之後，您可以使用其命令進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="c821e-148">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="c821e-149">請注意，命令可能無法與套件名稱相同。</span><span class="sxs-lookup"><span data-stu-id="c821e-149">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="c821e-150">如果命令是 `dotnetsay`，呼叫時請使用：</span><span class="sxs-lookup"><span data-stu-id="c821e-150">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="c821e-151">如果工具作者想要工具顯示在 `dotnet` 提示的內容中，他們可能會以稱為 `dotnet <command>` 的方式進行撰寫，例如：</span><span class="sxs-lookup"><span data-stu-id="c821e-151">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="c821e-152">您可以藉由使用 [dotnet tool list](dotnet-tool-list.md) 命令列出已安裝的套件，了解已安裝的通用工具套件中包含哪些工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-152">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="c821e-153">您也可以在工具的網站中，或鍵入下列其中一個命令來尋找使用方式指示：</span><span class="sxs-lookup"><span data-stu-id="c821e-153">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a><span data-ttu-id="c821e-154">其他 CLI 命令</span><span class="sxs-lookup"><span data-stu-id="c821e-154">Other CLI commands</span></span>

<span data-ttu-id="c821e-155">.NET Core SDK 包含其他支援 .NET Core 通用工具的命令。</span><span class="sxs-lookup"><span data-stu-id="c821e-155">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="c821e-156">請使用任何 `dotnet tool` 命令搭配下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="c821e-156">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="c821e-157">`--global` 或 `-g` 指定命令適用於使用者範圍通用工具。</span><span class="sxs-lookup"><span data-stu-id="c821e-157">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="c821e-158">`--tool-path` 指定通用工具的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="c821e-158">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="c821e-159">若要查看哪些命令適用於通用工具：</span><span class="sxs-lookup"><span data-stu-id="c821e-159">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="c821e-160">更新通用工具需要解除安裝再使用最新的穩定版本重新安裝。</span><span class="sxs-lookup"><span data-stu-id="c821e-160">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="c821e-161">若要更新通用工具，請使用 [dotnet tool update](dotnet-tool-update.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="c821e-161">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="c821e-162">使用 [dotnet tool uninstall](dotnet-tool-uninstall.md) 移除通用工具：</span><span class="sxs-lookup"><span data-stu-id="c821e-162">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="c821e-163">若要顯示電腦上目前已安裝的所有通用工具，以及它們的版本和命令，請使用 [dotnet tool list](dotnet-tool-list.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="c821e-163">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a><span data-ttu-id="c821e-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="c821e-164">See also</span></span>

* [<span data-ttu-id="c821e-165">針對 .NET Core 工具使用問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c821e-165">Troubleshoot .NET Core tool usage issues</span></span>](troubleshoot-usage-issues.md)
