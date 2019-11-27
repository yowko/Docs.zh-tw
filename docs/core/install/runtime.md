---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core 執行時間-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索執行 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 395978a2e471260254caf3da8421adf2413c132c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450853"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="c255a-104">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="c255a-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="c255a-105">在本文中，您將瞭解如何下載並安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c255a-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="c255a-106">.NET Core 執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c255a-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

<span data-ttu-id="c255a-107">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="c255a-107">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="c255a-108">.NET Core 3.1 Preview 3 下載</span><span class="sxs-lookup"><span data-stu-id="c255a-108">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="c255a-109">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="c255a-109">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="c255a-110">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="c255a-110">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="c255a-111">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="c255a-111">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="install-with-an-installer"></a><span data-ttu-id="c255a-112">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="c255a-112">Install with an installer</span></span>

<span data-ttu-id="c255a-113">Windows 和 macOS 都有獨立的安裝程式，可以用來安裝 .NET Core 3.0 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c255a-113">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 runtime.</span></span>

- <span data-ttu-id="c255a-114">Windows [X64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x64-installer) | [x32 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="c255a-114">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x86-installer)</span></span>
- <span data-ttu-id="c255a-115">macOS [X64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="c255a-115">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-macos-x64-installer)</span></span>

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="c255a-116">使用套件管理員進行安裝</span><span class="sxs-lookup"><span data-stu-id="c255a-116">Install with a package manager</span></span>

<span data-ttu-id="c255a-117">您可以使用許多常見的 Linux 封裝管理員來安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c255a-117">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="c255a-118">如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-manager-rhel7.md)。</span><span class="sxs-lookup"><span data-stu-id="c255a-118">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="c255a-119">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="c255a-119">Install with PowerShell automation</span></span>

<span data-ttu-id="c255a-120">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="c255a-120">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="c255a-121">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="c255a-121">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c255a-122">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="c255a-122">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="c255a-123">若要安裝目前版本的 .NET Core （3.0），請使用下列參數執行腳本：</span><span class="sxs-lookup"><span data-stu-id="c255a-123">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="c255a-124">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="c255a-124">Install with bash automation</span></span>

<span data-ttu-id="c255a-125">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="c255a-125">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="c255a-126">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="c255a-126">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c255a-127">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="c255a-127">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="c255a-128">若要安裝目前版本的 .NET Core （3.0），請使用下列參數執行腳本：</span><span class="sxs-lookup"><span data-stu-id="c255a-128">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="c255a-129">Docker</span><span class="sxs-lookup"><span data-stu-id="c255a-129">Docker</span></span>

<span data-ttu-id="c255a-130">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="c255a-130">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="c255a-131">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="c255a-131">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="c255a-132">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="c255a-132">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="c255a-133">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="c255a-133">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="c255a-134">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="c255a-134">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="c255a-135">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="c255a-135">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="c255a-136">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="c255a-136">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="c255a-137">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="c255a-137">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c255a-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c255a-138">Next steps</span></span>

- <span data-ttu-id="c255a-139">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="c255a-139">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
