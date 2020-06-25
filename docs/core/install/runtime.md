---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core 執行時間-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索執行 .NET Core 應用程式所需的相依性。
author: adegeo
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 6a0390ff1db900815628e4c7eb69e7a6c5f148a8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324590"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="bfe8e-104">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="bfe8e-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="bfe8e-105">在本文中，您將瞭解如何下載並安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="bfe8e-106">.NET Core 執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="bfe8e-107">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="bfe8e-107">Install with an installer</span></span>

<span data-ttu-id="bfe8e-108">Windows 有獨立的安裝程式，可用於安裝 .NET Core 3.1 執行時間：</span><span class="sxs-lookup"><span data-stu-id="bfe8e-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="bfe8e-109">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="bfe8e-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="bfe8e-110">x86 （32位） Cpu</span><span class="sxs-lookup"><span data-stu-id="bfe8e-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="bfe8e-111">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="bfe8e-111">Install with an installer</span></span>

<span data-ttu-id="bfe8e-112">macOS 具有可用於安裝 .NET Core 3.1 執行時間的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="bfe8e-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="bfe8e-113">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="bfe8e-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="bfe8e-114">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="bfe8e-114">Download and manually install</span></span>

<span data-ttu-id="bfe8e-115">除了適用于 .NET Core 的 macOS 安裝程式之外，您還可以下載並手動安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="bfe8e-116">若要安裝執行時間並啟用終端機可用的 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="bfe8e-117">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="bfe8e-118">假設執行時間已下載至檔案 `~/Downloads/dotnet-runtime.pkg` 。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="bfe8e-119">在 Linux 上安裝</span><span class="sxs-lookup"><span data-stu-id="bfe8e-119">Install on Linux</span></span>

<span data-ttu-id="bfe8e-120">這篇文章很快就會移除。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-120">This article will be removed soon.</span></span> <span data-ttu-id="bfe8e-121">目前已藉由[在 Linux 上安裝 .Net Core](linux.md)來取代。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-121">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="bfe8e-122">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="bfe8e-122">Install with PowerShell automation</span></span>

<span data-ttu-id="bfe8e-123">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-123">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="bfe8e-124">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-124">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="bfe8e-125">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-125">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="bfe8e-126">您可以藉由指定參數來選擇特定版本 `Channel` 。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-126">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="bfe8e-127">包含用 `Runtime` 來安裝執行時間的參數。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-127">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="bfe8e-128">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-128">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="bfe8e-129">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-129">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="bfe8e-130">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-130">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="bfe8e-131">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="bfe8e-131">Download and manually install</span></span>

<span data-ttu-id="bfe8e-132">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-132">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="bfe8e-133">然後，建立要安裝的目錄，例如 `%USERPROFILE%\dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-133">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="bfe8e-134">最後，將下載的 zip 檔案解壓縮至該目錄。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-134">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="bfe8e-135">根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core，因此您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-135">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="bfe8e-136">若要這麼做，請變更應用程式啟動時所使用的環境變數：</span><span class="sxs-lookup"><span data-stu-id="bfe8e-136">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="bfe8e-137">這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-137">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="bfe8e-138">即使已設定這些環境變數，在選取最佳架構來執行應用程式時，.NET Core 仍然會考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-138">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="bfe8e-139">預設值通常是 `C:\Program Files\dotnet` 安裝程式所使用的。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-139">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="bfe8e-140">您也可以藉由設定此環境變數，指示執行時間只使用自訂安裝位置：</span><span class="sxs-lookup"><span data-stu-id="bfe8e-140">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="bfe8e-141">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="bfe8e-141">Install with bash automation</span></span>

<span data-ttu-id="bfe8e-142">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-142">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="bfe8e-143">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-143">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="bfe8e-144">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-144">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="bfe8e-145">您可以藉由指定參數來選擇特定版本 `current` 。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-145">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="bfe8e-146">包含用 `runtime` 來安裝執行時間的參數。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-146">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="bfe8e-147">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-147">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="bfe8e-148">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-148">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="bfe8e-149">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-149">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="bfe8e-150">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="bfe8e-150">All .NET Core downloads</span></span>

<span data-ttu-id="bfe8e-151">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="bfe8e-151">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="bfe8e-152">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="bfe8e-152">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="bfe8e-153">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="bfe8e-153">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="bfe8e-154">Docker</span><span class="sxs-lookup"><span data-stu-id="bfe8e-154">Docker</span></span>

<span data-ttu-id="bfe8e-155">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-155">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="bfe8e-156">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-156">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="bfe8e-157">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-157">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="bfe8e-158">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-158">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="bfe8e-159">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-159">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="bfe8e-160">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-160">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="bfe8e-161">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-161">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="bfe8e-162">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-162">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bfe8e-163">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bfe8e-163">Next steps</span></span>

- <span data-ttu-id="bfe8e-164">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-164">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
