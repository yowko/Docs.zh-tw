---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core 執行時間-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索執行 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a45cb570ccf572a699359598319fd3867fb5e5dd
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340964"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="39607-104">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="39607-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="39607-105">在本文中，您將瞭解如何下載並安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="39607-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="39607-106">.NET Core 執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="39607-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="39607-107">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="39607-107">Install with an installer</span></span>

<span data-ttu-id="39607-108">Windows 有獨立的安裝程式，可用於安裝 .NET Core 3.1 執行時間：</span><span class="sxs-lookup"><span data-stu-id="39607-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="39607-109">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="39607-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="39607-110">x86 （32位） Cpu</span><span class="sxs-lookup"><span data-stu-id="39607-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="39607-111">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="39607-111">Install with an installer</span></span>

<span data-ttu-id="39607-112">macOS 具有可用於安裝 .NET Core 3.1 執行時間的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="39607-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="39607-113">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="39607-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="39607-114">使用套件管理員進行安裝</span><span class="sxs-lookup"><span data-stu-id="39607-114">Install with a package manager</span></span>

<span data-ttu-id="39607-115">您可以使用許多常見的 Linux 封裝管理員來安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="39607-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="39607-116">如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="39607-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="39607-117">只有在 x64 架構上才支援使用套件管理員進行安裝。</span><span class="sxs-lookup"><span data-stu-id="39607-117">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="39607-118">如果您要使用不同的架構（例如 ARM）來安裝 .NET Core 執行時間，請遵循[下載並手動安裝](#download-and-manually-install)一節中的指示。</span><span class="sxs-lookup"><span data-stu-id="39607-118">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="39607-119">如需有關支援哪些架構的詳細資訊，請參閱[.Net Core 相依性和需求](dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="39607-119">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="39607-120">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="39607-120">Download and manually install</span></span>

<span data-ttu-id="39607-121">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="39607-121">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="39607-122">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="39607-122">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="39607-123">上述 `export` 命令只會將 .NET Core CLI 命令提供給執行它的終端機會話。</span><span class="sxs-lookup"><span data-stu-id="39607-123">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="39607-124">您可以編輯您的 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="39607-124">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="39607-125">有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="39607-125">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="39607-126">例如：</span><span class="sxs-lookup"><span data-stu-id="39607-126">For example:</span></span>
>
> - <span data-ttu-id="39607-127">**Bash Shell**： *~/. bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="39607-127">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="39607-128">**Korn Shell**： *~/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="39607-128">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="39607-129">**Z Shell**： *~/.zshrc*或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="39607-129">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="39607-130">為您的 shell 編輯適當的原始程式檔，並將 `:$HOME/dotnet` 新增至現有 `PATH` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="39607-130">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="39607-131">如果未包含任何 `PATH` 語句，請加入具有 `export PATH=$PATH:$HOME/dotnet`的新行。</span><span class="sxs-lookup"><span data-stu-id="39607-131">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="39607-132">此外，將 `export DOTNET_ROOT=$HOME/dotnet` 新增至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="39607-132">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="39607-133">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="39607-133">Install with PowerShell automation</span></span>

<span data-ttu-id="39607-134">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="39607-134">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="39607-135">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="39607-135">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="39607-136">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="39607-136">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="39607-137">您可以藉由指定 `Channel` 參數來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="39607-137">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="39607-138">包含 `Runtime` 參數，以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="39607-138">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="39607-139">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="39607-139">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="39607-140">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="39607-140">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="39607-141">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="39607-141">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="39607-142">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="39607-142">Install with bash automation</span></span>

<span data-ttu-id="39607-143">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="39607-143">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="39607-144">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="39607-144">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="39607-145">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="39607-145">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="39607-146">您可以藉由指定 `current` 參數來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="39607-146">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="39607-147">包含 `runtime` 參數，以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="39607-147">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="39607-148">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="39607-148">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="39607-149">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="39607-149">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="39607-150">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="39607-150">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="39607-151">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="39607-151">All .NET Core downloads</span></span>

<span data-ttu-id="39607-152">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="39607-152">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="39607-153">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="39607-153">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="39607-154">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="39607-154">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="39607-155">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="39607-155">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="39607-156">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="39607-156">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="39607-157">Docker</span><span class="sxs-lookup"><span data-stu-id="39607-157">Docker</span></span>

<span data-ttu-id="39607-158">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="39607-158">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="39607-159">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="39607-159">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="39607-160">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="39607-160">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="39607-161">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="39607-161">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="39607-162">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="39607-162">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="39607-163">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="39607-163">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="39607-164">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="39607-164">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="39607-165">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="39607-165">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="39607-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="39607-166">Next steps</span></span>

- <span data-ttu-id="39607-167">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="39607-167">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
