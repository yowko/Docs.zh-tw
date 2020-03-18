---
title: 在 Windows、Linux 和 macOS 上安裝 .NET 核心運行時 - .NET 內核
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 瞭解運行 .NET 核心應用所需的依賴項。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399011"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="eb419-104">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="eb419-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="eb419-105">在本文中，您將學習如何下載和安裝 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="eb419-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="eb419-106">.NET 核心運行時用於運行使用 .NET Core 創建的應用。</span><span class="sxs-lookup"><span data-stu-id="eb419-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="eb419-107">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-107">Install with an installer</span></span>

<span data-ttu-id="eb419-108">Windows 具有可用於安裝 .NET Core 3.1 運行時的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="eb419-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="eb419-109">x64 （64 位） CPU</span><span class="sxs-lookup"><span data-stu-id="eb419-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="eb419-110">x86 （32 位） CPU</span><span class="sxs-lookup"><span data-stu-id="eb419-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="eb419-111">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-111">Install with an installer</span></span>

<span data-ttu-id="eb419-112">macOS 具有可用於安裝 .NET Core 3.1 運行時的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="eb419-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="eb419-113">x64 （64 位） CPU</span><span class="sxs-lookup"><span data-stu-id="eb419-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="eb419-114">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-114">Download and manually install</span></span>

<span data-ttu-id="eb419-115">作為 .NET Core 的 macOS 安裝程式的替代方法，您可以下載並手動安裝運行時。</span><span class="sxs-lookup"><span data-stu-id="eb419-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="eb419-116">要安裝運行時並啟用終端上可用的 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="eb419-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="eb419-117">然後，打開一個終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="eb419-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="eb419-118">假定運行時將下載到`~/Downloads/dotnet-runtime.pkg`檔中。</span><span class="sxs-lookup"><span data-stu-id="eb419-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="eb419-119">使用包管理器安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-119">Install with a package manager</span></span>

<span data-ttu-id="eb419-120">您可以使用許多常見的 Linux 套裝程式管理器安裝 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="eb419-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="eb419-121">有關詳細資訊，請參閱[Linux 套裝軟體管理器 - 安裝 .NET 核心](linux-package-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="eb419-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="eb419-122">僅在 x64 體系結構上支援使用包管理器安裝它。</span><span class="sxs-lookup"><span data-stu-id="eb419-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="eb419-123">如果要使用其他體系結構（如 ARM）安裝 .NET 核心運行時，請按照["下載"部分的說明進行手動安裝](#download-and-manually-install)。</span><span class="sxs-lookup"><span data-stu-id="eb419-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="eb419-124">有關支援哪些體系結構的詳細資訊，請參閱[.NET Core 依賴項和要求](dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="eb419-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="eb419-125">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-125">Download and manually install</span></span>

<span data-ttu-id="eb419-126">要提取運行時並使 .NET Core CLI 命令在終端上可用，請首先[下載](#all-net-core-downloads).NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="eb419-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="eb419-127">然後，打開一個終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="eb419-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="eb419-128">前面的`export`命令僅使 .NET Core CLI 命令可用於運行它的終端會話。</span><span class="sxs-lookup"><span data-stu-id="eb419-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="eb419-129">您可以編輯 shell 設定檔以永久添加命令。</span><span class="sxs-lookup"><span data-stu-id="eb419-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="eb419-130">Linux 有許多不同的外殼，每個外殼都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="eb419-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="eb419-131">例如：</span><span class="sxs-lookup"><span data-stu-id="eb419-131">For example:</span></span>
>
> - <span data-ttu-id="eb419-132">**巴什外殼**： **/.bash_profile* *，*/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="eb419-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="eb419-133">**科恩殼牌**： \**/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="eb419-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="eb419-134">**Z 外殼**： \**/.zshrc*或 *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="eb419-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="eb419-135">編輯 shell 的相應原始檔案，並`:$HOME/dotnet`添加到現有`PATH`語句的末尾。</span><span class="sxs-lookup"><span data-stu-id="eb419-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="eb419-136">如果未`PATH`包含語句，則使用`export PATH=$PATH:$HOME/dotnet`添加新行。</span><span class="sxs-lookup"><span data-stu-id="eb419-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="eb419-137">此外，添加到`export DOTNET_ROOT=$HOME/dotnet`檔的末尾。</span><span class="sxs-lookup"><span data-stu-id="eb419-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="eb419-138">此方法允許您將不同版本安裝到不同的位置，並明確選取要使用哪個應用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="eb419-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="eb419-139">使用 PowerShell 自動化安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-139">Install with PowerShell automation</span></span>

<span data-ttu-id="eb419-140">[dotnet 安裝腳本](../tools/dotnet-install-script.md)用於運行時的自動化和非管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="eb419-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="eb419-141">可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="eb419-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="eb419-142">該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="eb419-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="eb419-143">您可以通過指定`Channel`交換器來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="eb419-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="eb419-144">包括`Runtime`用於安裝運行時的交換器。</span><span class="sxs-lookup"><span data-stu-id="eb419-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="eb419-145">否則，腳本將安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="eb419-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="eb419-146">上述命令安裝ASP.NET核心運行時以實現最大的相容性。</span><span class="sxs-lookup"><span data-stu-id="eb419-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="eb419-147">ASP.NET核心運行時還包括標準的 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="eb419-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="eb419-148">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-148">Download and manually install</span></span>

<span data-ttu-id="eb419-149">要提取運行時並使 .NET Core CLI 命令在終端上可用，請首先[下載](#all-net-core-downloads).NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="eb419-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="eb419-150">然後，創建要安裝到的目錄，例如`%USERPROFILE%\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="eb419-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="eb419-151">最後，將下載的 ZIP 檔案提取到該目錄中。</span><span class="sxs-lookup"><span data-stu-id="eb419-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="eb419-152">預設情況下，.NET 核心 CLI 命令和應用不會以這種方式使用 .NET Core 安裝。</span><span class="sxs-lookup"><span data-stu-id="eb419-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="eb419-153">您必須明確選取使用它。</span><span class="sxs-lookup"><span data-stu-id="eb419-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="eb419-154">為此，請更改啟動應用程式的環境變數：</span><span class="sxs-lookup"><span data-stu-id="eb419-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="eb419-155">此方法允許您將多個版本安裝到單獨的位置，然後通過運行應用程式的環境變數指向該位置來明確選取應用程式應使用哪個安裝位置。</span><span class="sxs-lookup"><span data-stu-id="eb419-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="eb419-156">即使設置了這些環境變數，.NET Core 在選擇運行應用程式的最佳框架時仍會考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="eb419-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="eb419-157">預設值通常是`C:\Program Files\dotnet`安裝程式使用的 。</span><span class="sxs-lookup"><span data-stu-id="eb419-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="eb419-158">也可以通過設置此環境變數來指示運行時僅使用自訂安裝位置：</span><span class="sxs-lookup"><span data-stu-id="eb419-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="eb419-159">使用 bash 自動化安裝</span><span class="sxs-lookup"><span data-stu-id="eb419-159">Install with bash automation</span></span>

<span data-ttu-id="eb419-160">[dotnet 安裝腳本](../tools/dotnet-install-script.md)用於運行時的自動化和非管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="eb419-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="eb419-161">可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="eb419-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="eb419-162">該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="eb419-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="eb419-163">您可以通過指定`current`交換器來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="eb419-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="eb419-164">包括`runtime`用於安裝運行時的交換器。</span><span class="sxs-lookup"><span data-stu-id="eb419-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="eb419-165">否則，腳本將安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="eb419-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="eb419-166">上述命令安裝ASP.NET核心運行時以實現最大的相容性。</span><span class="sxs-lookup"><span data-stu-id="eb419-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="eb419-167">ASP.NET核心運行時還包括標準的 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="eb419-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="eb419-168">所有 .NET 核心下載</span><span class="sxs-lookup"><span data-stu-id="eb419-168">All .NET Core downloads</span></span>

<span data-ttu-id="eb419-169">您可以使用以下連結之一直接下載和安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="eb419-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="eb419-170">.NET 核心 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="eb419-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="eb419-171">.NET 核心 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="eb419-171">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="eb419-172">Docker</span><span class="sxs-lookup"><span data-stu-id="eb419-172">Docker</span></span>

<span data-ttu-id="eb419-173">容器提供了將應用程式與主機系統的其餘部分隔離的羽量級方法。</span><span class="sxs-lookup"><span data-stu-id="eb419-173">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="eb419-174">同一台電腦上的容器僅共用內核並使用提供給應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="eb419-174">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="eb419-175">.NET Core 可以在 Docker 容器中運行。</span><span class="sxs-lookup"><span data-stu-id="eb419-175">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="eb419-176">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="eb419-176">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="eb419-177">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="eb419-177">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="eb419-178">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="eb419-178">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="eb419-179">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="eb419-179">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="eb419-180">有關在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.NET 和 Docker 和](../docker/introduction.md)[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)簡介。</span><span class="sxs-lookup"><span data-stu-id="eb419-180">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="eb419-181">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eb419-181">Next steps</span></span>

- <span data-ttu-id="eb419-182">[如何檢查是否已安裝 .NET Core。](how-to-detect-installed-versions.md)</span><span class="sxs-lookup"><span data-stu-id="eb419-182">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
