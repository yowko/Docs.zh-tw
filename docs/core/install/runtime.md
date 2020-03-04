---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core 執行時間-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索執行 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a41bbdf5419585f06773583dbe82ab0d84ebaa4c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157632"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="53de4-104">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="53de4-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="53de4-105">在本文中，您將瞭解如何下載並安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="53de4-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="53de4-106">.NET Core 執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="53de4-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="53de4-107">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-107">Install with an installer</span></span>

<span data-ttu-id="53de4-108">Windows 有獨立的安裝程式，可用於安裝 .NET Core 3.1 執行時間：</span><span class="sxs-lookup"><span data-stu-id="53de4-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="53de4-109">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="53de4-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="53de4-110">x86 （32位） Cpu</span><span class="sxs-lookup"><span data-stu-id="53de4-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="53de4-111">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-111">Install with an installer</span></span>

<span data-ttu-id="53de4-112">macOS 具有可用於安裝 .NET Core 3.1 執行時間的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="53de4-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="53de4-113">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="53de4-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="53de4-114">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-114">Download and manually install</span></span>

<span data-ttu-id="53de4-115">除了適用于 .NET Core 的 macOS 安裝程式之外，您還可以下載並手動安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="53de4-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="53de4-116">若要安裝執行時間並啟用終端機可用的 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="53de4-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="53de4-117">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="53de4-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="53de4-118">假設執行時間已下載至 `~/Downloads/dotnet-runtime.pkg` 檔案。</span><span class="sxs-lookup"><span data-stu-id="53de4-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="53de4-119">使用套件管理員進行安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-119">Install with a package manager</span></span>

<span data-ttu-id="53de4-120">您可以使用許多常見的 Linux 封裝管理員來安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="53de4-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="53de4-121">如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="53de4-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="53de4-122">只有在 x64 架構上才支援使用套件管理員進行安裝。</span><span class="sxs-lookup"><span data-stu-id="53de4-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="53de4-123">如果您要使用不同的架構（例如 ARM）來安裝 .NET Core 執行時間，請遵循[下載並手動安裝](#download-and-manually-install)一節中的指示。</span><span class="sxs-lookup"><span data-stu-id="53de4-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="53de4-124">如需有關支援哪些架構的詳細資訊，請參閱[.Net Core 相依性和需求](dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="53de4-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="53de4-125">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-125">Download and manually install</span></span>

<span data-ttu-id="53de4-126">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="53de4-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="53de4-127">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="53de4-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="53de4-128">上述 `export` 命令只會將 .NET Core CLI 命令提供給執行它的終端機會話。</span><span class="sxs-lookup"><span data-stu-id="53de4-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="53de4-129">您可以編輯您的 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="53de4-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="53de4-130">有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="53de4-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="53de4-131">例如：</span><span class="sxs-lookup"><span data-stu-id="53de4-131">For example:</span></span>
>
> - <span data-ttu-id="53de4-132">**Bash Shell**： *~/. bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="53de4-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="53de4-133">**Korn Shell**： *~/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="53de4-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="53de4-134">**Z Shell**： *~/.zshrc*或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="53de4-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="53de4-135">為您的 shell 編輯適當的原始程式檔，並將 `:$HOME/dotnet` 新增至現有 `PATH` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="53de4-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="53de4-136">如果未包含任何 `PATH` 語句，請加入具有 `export PATH=$PATH:$HOME/dotnet`的新行。</span><span class="sxs-lookup"><span data-stu-id="53de4-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="53de4-137">此外，將 `export DOTNET_ROOT=$HOME/dotnet` 新增至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="53de4-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="53de4-138">這種方法可讓您將不同的版本安裝到不同的位置，並明確選擇哪一個應用程式要使用哪一個。</span><span class="sxs-lookup"><span data-stu-id="53de4-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="53de4-139">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-139">Install with PowerShell automation</span></span>

<span data-ttu-id="53de4-140">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="53de4-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="53de4-141">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="53de4-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="53de4-142">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="53de4-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="53de4-143">您可以藉由指定 `Channel` 參數來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="53de4-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="53de4-144">包含 `Runtime` 參數，以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="53de4-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="53de4-145">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="53de4-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="53de4-146">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="53de4-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="53de4-147">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="53de4-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="53de4-148">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-148">Download and manually install</span></span>

<span data-ttu-id="53de4-149">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="53de4-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="53de4-150">然後，建立要安裝的目錄，例如 `%USERPROFILE%\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="53de4-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="53de4-151">最後，將下載的 zip 檔案解壓縮至該目錄。</span><span class="sxs-lookup"><span data-stu-id="53de4-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="53de4-152">根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="53de4-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="53de4-153">您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="53de4-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="53de4-154">若要這麼做，請變更應用程式啟動時所使用的環境變數：</span><span class="sxs-lookup"><span data-stu-id="53de4-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="53de4-155">這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="53de4-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="53de4-156">即使已設定這些環境變數，在選取最佳架構來執行應用程式時，.NET Core 仍然會考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="53de4-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="53de4-157">預設值通常是 `C:\Program Files\dotnet`，這是安裝程式所使用的。</span><span class="sxs-lookup"><span data-stu-id="53de4-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="53de4-158">您也可以藉由設定此環境變數，指示執行時間只使用自訂安裝位置：</span><span class="sxs-lookup"><span data-stu-id="53de4-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="53de4-159">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="53de4-159">Install with bash automation</span></span>

<span data-ttu-id="53de4-160">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="53de4-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="53de4-161">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="53de4-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="53de4-162">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="53de4-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="53de4-163">您可以藉由指定 `current` 參數來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="53de4-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="53de4-164">包含 `runtime` 參數，以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="53de4-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="53de4-165">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="53de4-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="53de4-166">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="53de4-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="53de4-167">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="53de4-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="53de4-168">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="53de4-168">All .NET Core downloads</span></span>

<span data-ttu-id="53de4-169">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="53de4-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="53de4-170">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="53de4-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="53de4-171">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="53de4-171">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="53de4-172">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="53de4-172">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="53de4-173">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="53de4-173">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="53de4-174">Docker</span><span class="sxs-lookup"><span data-stu-id="53de4-174">Docker</span></span>

<span data-ttu-id="53de4-175">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="53de4-175">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="53de4-176">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="53de4-176">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="53de4-177">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="53de4-177">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="53de4-178">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="53de4-178">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="53de4-179">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="53de4-179">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="53de4-180">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="53de4-180">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="53de4-181">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="53de4-181">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="53de4-182">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="53de4-182">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="53de4-183">後續步驟</span><span class="sxs-lookup"><span data-stu-id="53de4-183">Next steps</span></span>

- <span data-ttu-id="53de4-184">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="53de4-184">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
