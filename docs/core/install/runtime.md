---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core 執行時間-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索執行 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 8f4a895ad66dea3063a32f785e4c521196266978
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835725"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="cef24-104">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="cef24-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="cef24-105">在本文中，您將瞭解如何下載並安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="cef24-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="cef24-106">.NET Core 執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cef24-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="cef24-107">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="cef24-107">Install with an installer</span></span>

<span data-ttu-id="cef24-108">Windows 有獨立的安裝程式，可用於安裝 .NET Core 3.1 執行時間：</span><span class="sxs-lookup"><span data-stu-id="cef24-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="cef24-109">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="cef24-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="cef24-110">x86 （32位） Cpu</span><span class="sxs-lookup"><span data-stu-id="cef24-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="cef24-111">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="cef24-111">Install with an installer</span></span>

<span data-ttu-id="cef24-112">macOS 具有可用於安裝 .NET Core 3.1 執行時間的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="cef24-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="cef24-113">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="cef24-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="cef24-114">使用套件管理員進行安裝</span><span class="sxs-lookup"><span data-stu-id="cef24-114">Install with a package manager</span></span>

<span data-ttu-id="cef24-115">您可以使用許多常見的 Linux 封裝管理員來安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="cef24-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="cef24-116">如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-manager-rhel7.md)。</span><span class="sxs-lookup"><span data-stu-id="cef24-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="cef24-117">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="cef24-117">Install with PowerShell automation</span></span>

<span data-ttu-id="cef24-118">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="cef24-118">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="cef24-119">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="cef24-119">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cef24-120">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="cef24-120">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="cef24-121">您可以藉由指定 `Channel` 參數來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="cef24-121">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="cef24-122">包含 `Runtime` 參數，以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="cef24-122">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="cef24-123">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="cef24-123">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="cef24-124">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="cef24-124">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="cef24-125">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="cef24-125">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="cef24-126">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="cef24-126">Install with bash automation</span></span>

<span data-ttu-id="cef24-127">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="cef24-127">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="cef24-128">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="cef24-128">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cef24-129">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="cef24-129">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="cef24-130">您可以藉由指定 `current` 參數來選擇特定版本。</span><span class="sxs-lookup"><span data-stu-id="cef24-130">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="cef24-131">包含 `runtime` 參數，以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="cef24-131">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="cef24-132">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="cef24-132">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="cef24-133">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="cef24-133">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="cef24-134">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="cef24-134">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="cef24-135">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="cef24-135">All .NET Core downloads</span></span>

<span data-ttu-id="cef24-136">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="cef24-136">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="cef24-137">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="cef24-137">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="cef24-138">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="cef24-138">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="cef24-139">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="cef24-139">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="cef24-140">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="cef24-140">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="cef24-141">Docker</span><span class="sxs-lookup"><span data-stu-id="cef24-141">Docker</span></span>

<span data-ttu-id="cef24-142">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="cef24-142">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="cef24-143">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="cef24-143">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="cef24-144">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="cef24-144">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="cef24-145">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="cef24-145">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="cef24-146">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="cef24-146">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="cef24-147">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="cef24-147">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="cef24-148">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="cef24-148">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="cef24-149">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="cef24-149">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cef24-150">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cef24-150">Next steps</span></span>

- <span data-ttu-id="cef24-151">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="cef24-151">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
