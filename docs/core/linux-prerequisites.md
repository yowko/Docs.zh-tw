---
title: Linux 上 .NET Core 的必要條件
description: 支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。
author: jralexander
ms.author: johalex
ms.date: 04/19/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 9d986ed56bbc6f803988fde4b5500cd5d5364050
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="48a91-103">Linux 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="48a91-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="48a91-104">本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="48a91-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="48a91-105">支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="48a91-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="48a91-106">使用命令列搭配您偏好的編輯器</span><span class="sxs-lookup"><span data-stu-id="48a91-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="48a91-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="48a91-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="48a91-108">實際執行伺服器/生產環境不需要 .NET Core SDK 套件。</span><span class="sxs-lookup"><span data-stu-id="48a91-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="48a91-109">僅需要.NET Core 執行階段套件，即可將應用程式部署到生產環境。</span><span class="sxs-lookup"><span data-stu-id="48a91-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="48a91-110">.NET Core 執行階段將應用程式作為獨立部署的一部分進行部署，不過，針對架構相依的部署應用程式必須單獨加以部署。</span><span class="sxs-lookup"><span data-stu-id="48a91-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="48a91-111">如需架構相依部署類型和獨立部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](./deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="48a91-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="48a91-112">另請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)以了解特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="48a91-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="48a91-113">支援的 Linux 版本</span><span class="sxs-lookup"><span data-stu-id="48a91-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="48a91-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="48a91-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="48a91-115">.NET Core 2.x 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="48a91-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="48a91-116">針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。</span><span class="sxs-lookup"><span data-stu-id="48a91-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="48a91-117">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-117">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="48a91-118">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="48a91-118">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="48a91-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="48a91-119">CentOS 7</span></span>
* <span data-ttu-id="48a91-120">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="48a91-120">Oracle Linux 7</span></span>
* <span data-ttu-id="48a91-121">Fedora 27、26</span><span class="sxs-lookup"><span data-stu-id="48a91-121">Fedora 27, 26</span></span>
* <span data-ttu-id="48a91-122">Debian 9、8.7 或更新版本</span><span class="sxs-lookup"><span data-stu-id="48a91-122">Debian 9, 8.7 or later versions</span></span>
* <span data-ttu-id="48a91-123">Ubuntu 17.10、16.04、14.04</span><span class="sxs-lookup"><span data-stu-id="48a91-123">Ubuntu 17.10, 16.04, 14.04</span></span>
* <span data-ttu-id="48a91-124">Linux Mint 18、17</span><span class="sxs-lookup"><span data-stu-id="48a91-124">Linux Mint 18, 17</span></span>
* <span data-ttu-id="48a91-125">openSUSE 42.3 或更新版本</span><span class="sxs-lookup"><span data-stu-id="48a91-125">openSUSE 42.3 or later versions</span></span>
* <span data-ttu-id="48a91-126">SUSE Enterprise Linux (SLES) 12 Service Pack 2 或更新版本</span><span class="sxs-lookup"><span data-stu-id="48a91-126">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later</span></span>

<span data-ttu-id="48a91-127">如需 .NET Core 2.x 支援的作業系統完整清單、發行版本、版本、不支援的作業系統版本，以及生命週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="48a91-127">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="48a91-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-128">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="48a91-129">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-129">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="48a91-130">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="48a91-130">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="48a91-131">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="48a91-131">CentOS 7</span></span>
* <span data-ttu-id="48a91-132">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="48a91-132">Oracle Linux 7</span></span>
* <span data-ttu-id="48a91-133">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="48a91-133">Fedora 26</span></span>
* <span data-ttu-id="48a91-134">Debian 8.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="48a91-134">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="48a91-135">Ubuntu 16.04、14.04</span><span class="sxs-lookup"><span data-stu-id="48a91-135">Ubuntu 16.04, 14.04</span></span>
* <span data-ttu-id="48a91-136">Linux Mint 18、17</span><span class="sxs-lookup"><span data-stu-id="48a91-136">Linux Mint 18, 17</span></span>
* <span data-ttu-id="48a91-137">openSUSE 42.3 或更新版本 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="48a91-137">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="48a91-138">如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="48a91-138">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="48a91-139">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="48a91-139">Linux distribution dependencies</span></span>

<span data-ttu-id="48a91-140">下列要作為範例。</span><span class="sxs-lookup"><span data-stu-id="48a91-140">The following are intended to be examples.</span></span> <span data-ttu-id="48a91-141">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="48a91-141">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="48a91-142">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="48a91-142">Ubuntu</span></span>

<span data-ttu-id="48a91-143">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="48a91-143">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="48a91-144">libunwind8</span><span class="sxs-lookup"><span data-stu-id="48a91-144">libunwind8</span></span>
* <span data-ttu-id="48a91-145">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="48a91-145">liblttng-ust0</span></span>
* <span data-ttu-id="48a91-146">libcurl3</span><span class="sxs-lookup"><span data-stu-id="48a91-146">libcurl3</span></span>
* <span data-ttu-id="48a91-147">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="48a91-147">libssl1.0.0</span></span>
* <span data-ttu-id="48a91-148">libuuid1</span><span class="sxs-lookup"><span data-stu-id="48a91-148">libuuid1</span></span>
* <span data-ttu-id="48a91-149">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="48a91-149">libkrb5-3</span></span>
* <span data-ttu-id="48a91-150">zlib1g</span><span class="sxs-lookup"><span data-stu-id="48a91-150">zlib1g</span></span>
* <span data-ttu-id="48a91-151">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="48a91-151">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="48a91-152">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="48a91-152">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="48a91-153">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="48a91-153">libicu57 (for 17.x)</span></span>

### <a name="centos"></a><span data-ttu-id="48a91-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="48a91-154">CentOS</span></span>

<span data-ttu-id="48a91-155">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="48a91-155">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="48a91-156">libunwind</span><span class="sxs-lookup"><span data-stu-id="48a91-156">libunwind</span></span>
* <span data-ttu-id="48a91-157">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="48a91-157">lttng-ust</span></span>
* <span data-ttu-id="48a91-158">libcurl</span><span class="sxs-lookup"><span data-stu-id="48a91-158">libcurl</span></span>
* <span data-ttu-id="48a91-159">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="48a91-159">openssl-libs</span></span>
* <span data-ttu-id="48a91-160">libuuid</span><span class="sxs-lookup"><span data-stu-id="48a91-160">libuuid</span></span>
* <span data-ttu-id="48a91-161">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="48a91-161">krb5-libs</span></span>
* <span data-ttu-id="48a91-162">libicu</span><span class="sxs-lookup"><span data-stu-id="48a91-162">libicu</span></span>
* <span data-ttu-id="48a91-163">zlib</span><span class="sxs-lookup"><span data-stu-id="48a91-163">zlib</span></span>

<span data-ttu-id="48a91-164">如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="48a91-164">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="48a91-165">使用原生安裝程式來安裝 .NET Core 相依性</span><span class="sxs-lookup"><span data-stu-id="48a91-165">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="48a91-166">受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="48a91-166">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="48a91-167">原生安裝程式需要伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="48a91-167">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="48a91-168">使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。</span><span class="sxs-lookup"><span data-stu-id="48a91-168">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="48a91-169">原生安裝程式也會安裝 .NET Core SDK 全系統。</span><span class="sxs-lookup"><span data-stu-id="48a91-169">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="48a91-170">Linux 上有兩個安裝程式套件選擇：</span><span class="sxs-lookup"><span data-stu-id="48a91-170">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="48a91-171">使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。</span><span class="sxs-lookup"><span data-stu-id="48a91-171">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="48a91-172">使用套件本身，DEB 或 RPM。</span><span class="sxs-lookup"><span data-stu-id="48a91-172">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="48a91-173">使用 .NET Core 安裝程式指令碼以指令碼進行安裝</span><span class="sxs-lookup"><span data-stu-id="48a91-173">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="48a91-174">[dotnet-install 指令碼](./tools/dotnet-install-script.md)用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。</span><span class="sxs-lookup"><span data-stu-id="48a91-174">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="48a91-175">您可以從 [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh) 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="48a91-175">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="48a91-176">安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="48a91-176">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="48a91-177">此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="48a91-177">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a><span data-ttu-id="48a91-178">安裝適用於支援之 Red Hat Enterprise Linux (RHEL) 版本的 .NET Core</span><span class="sxs-lookup"><span data-stu-id="48a91-178">Install .NET Core for supported Red Hat Enterprise Linux (RHEL) versions</span></span>

<span data-ttu-id="48a91-179">若要在支援的 RHEL 版本上安裝.NET Core：</span><span class="sxs-lookup"><span data-stu-id="48a91-179">To install .NET Core on supported RHEL versions:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="48a91-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="48a91-180">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="48a91-181">為了確保您能夠擁有最新安裝資訊，請遵循適用於支援之的 RHEL 版本non-admin [.NET Core 2.x SDK 和執行階段安裝程式指示](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current)。</span><span class="sxs-lookup"><span data-stu-id="48a91-181">To ensure you have the latest installation information, follow the [.NET Core 2.x SDK and Runtime Installer instructions](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) for supported RHEL versions.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="48a91-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-182">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="48a91-183">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="48a91-183">**.NET Core 1.1**</span></span>

1. <span data-ttu-id="48a91-184">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-184">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="48a91-185">如需在 Red Hat Enterprise Linux 上安裝 .NET Core 1.1 的最新資訊，請參閱 [.NET Core 1.1 入門指南](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)</span><span class="sxs-lookup"><span data-stu-id="48a91-185">For the latest .NET Core 1.1 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)</span></span>
     
<span data-ttu-id="48a91-186">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="48a91-186">**.NET Core 1.0**</span></span>

1. <span data-ttu-id="48a91-187">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-187">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="48a91-188">如需在 Red Hat Enterprise Linux 上安裝 .NET Core 1.0 的最新資訊，請參閱 [.NET Core 1.0 入門指南](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)</span><span class="sxs-lookup"><span data-stu-id="48a91-188">For the latest .NET Core 1.0 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.0 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)</span></span>

<span data-ttu-id="48a91-189">如需 Red Hat .NET 通道存取登錄說明，請參閱 Red Hat 的 [.NET Core 1.1 入門指南的第 1 章](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)。</span><span class="sxs-lookup"><span data-stu-id="48a91-189">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a><span data-ttu-id="48a91-190">為支援的 Ubuntu 和 Linux Mint 發行版本/版本 (64 位元) 安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="48a91-190">Install .NET Core for supported Ubuntu and Linux Mint distributions/versions (64 bit)</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="48a91-191">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="48a91-191">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="48a91-192">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-192">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-193">在支援的 Ubuntu 和 Linux Mint 發行版本/版本 (64 位元) 上安裝 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-193">Install .NET Core 2.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

<span data-ttu-id="48a91-194">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="48a91-194">**.NET Core 2.0**</span></span>

|<span data-ttu-id="48a91-195">執行階段/SDK</span><span class="sxs-lookup"><span data-stu-id="48a91-195">Runtimes / SDKs</span></span>          |<span data-ttu-id="48a91-196">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="48a91-196">Ubuntu 17.10</span></span>  |<span data-ttu-id="48a91-197">Ubuntu 16.04/Linux Mint 18</span><span class="sxs-lookup"><span data-stu-id="48a91-197">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="48a91-198">Ubuntu 14.04/Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="48a91-198">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|--------------|----------------------------|----------------------------|
|<span data-ttu-id="48a91-199">.NET Core Runtime 2.0.6</span><span class="sxs-lookup"><span data-stu-id="48a91-199">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="48a91-200">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-200">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[<span data-ttu-id="48a91-201">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-201">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[<span data-ttu-id="48a91-202">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-202">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|<span data-ttu-id="48a91-203">.NET Core Runtime 2.0.5</span><span class="sxs-lookup"><span data-stu-id="48a91-203">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="48a91-204">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-204">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[<span data-ttu-id="48a91-205">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-205">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[<span data-ttu-id="48a91-206">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-206">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|<span data-ttu-id="48a91-207">.NET Core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="48a91-207">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="48a91-208">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-208">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[<span data-ttu-id="48a91-209">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-209">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[<span data-ttu-id="48a91-210">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-210">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|<span data-ttu-id="48a91-211">.NET Core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="48a91-211">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="48a91-212">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-212">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[<span data-ttu-id="48a91-213">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-213">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[<span data-ttu-id="48a91-214">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-214">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |

<span data-ttu-id="48a91-215">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="48a91-215">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="48a91-216">若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。</span><span class="sxs-lookup"><span data-stu-id="48a91-216">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="48a91-217">執行階段/SDK</span><span class="sxs-lookup"><span data-stu-id="48a91-217">Runtimes / SDKs</span></span>                  |<span data-ttu-id="48a91-218">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="48a91-218">Ubuntu 17.10</span></span>    |<span data-ttu-id="48a91-219">Ubuntu 16.04/Linux Mint 18</span><span class="sxs-lookup"><span data-stu-id="48a91-219">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="48a91-220">Ubuntu 14.04/Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="48a91-220">Ubuntu 14.04 / Linux Mint 17</span></span>|
|---------------------------------|----------------|----------------------------|----------------------------|
|<span data-ttu-id="48a91-221">.NET Core Runtime 2.1.0-preview2</span><span class="sxs-lookup"><span data-stu-id="48a91-221">.NET Core Runtime 2.1.0-preview2</span></span> |[<span data-ttu-id="48a91-222">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-222">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview2)|[<span data-ttu-id="48a91-223">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-223">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview2)            |[<span data-ttu-id="48a91-224">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-224">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview2)            |
|<span data-ttu-id="48a91-225">.NET Core Runtime 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="48a91-225">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="48a91-226">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-226">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview1)|[<span data-ttu-id="48a91-227">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-227">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview1)            |[<span data-ttu-id="48a91-228">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-228">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview1)            |
|<span data-ttu-id="48a91-229">.NET Core SDK 2.1.300-preview2</span><span class="sxs-lookup"><span data-stu-id="48a91-229">.NET Core SDK 2.1.300-preview2</span></span>   |[<span data-ttu-id="48a91-230">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-230">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview2)|[<span data-ttu-id="48a91-231">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-231">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview2)            |[<span data-ttu-id="48a91-232">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-232">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview2)
|<span data-ttu-id="48a91-233">.NET Core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="48a91-233">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="48a91-234">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-234">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview1)|[<span data-ttu-id="48a91-235">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-235">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview1)            |[<span data-ttu-id="48a91-236">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-236">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview1)            |


# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="48a91-237">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-237">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="48a91-238">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-238">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-239">在支援的 Ubuntu 和 Linux Mint 發行版本/版本 (64 位元) 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-239">Install .NET Core 1.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

| <span data-ttu-id="48a91-240">執行階段/SDK</span><span class="sxs-lookup"><span data-stu-id="48a91-240">Runtimes / SDKs</span></span>         |<span data-ttu-id="48a91-241">Ubuntu 16.04/Linux Mint 18</span><span class="sxs-lookup"><span data-stu-id="48a91-241">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="48a91-242">Ubuntu 14.04/Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="48a91-242">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|----------------------------|----------------------------|
|<span data-ttu-id="48a91-243">.NET Core Runtime 1.1.7</span><span class="sxs-lookup"><span data-stu-id="48a91-243">.NET Core Runtime 1.1.7</span></span>  |[<span data-ttu-id="48a91-244">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-244">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-245">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-245">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="48a91-246">.NET Core Runtime 1.1.6</span><span class="sxs-lookup"><span data-stu-id="48a91-246">.NET Core Runtime 1.1.6</span></span>  |[<span data-ttu-id="48a91-247">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-247">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-248">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-248">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="48a91-249">.NET Core Runtime 1.0.10</span><span class="sxs-lookup"><span data-stu-id="48a91-249">.NET Core Runtime 1.0.10</span></span> |[<span data-ttu-id="48a91-250">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-250">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-251">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-251">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="48a91-252">.NET Core Runtime 1.0.9</span><span class="sxs-lookup"><span data-stu-id="48a91-252">.NET Core Runtime 1.0.9</span></span>  |[<span data-ttu-id="48a91-253">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-253">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-254">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-254">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="48a91-255">.NET Core SDK 1.1.8</span><span class="sxs-lookup"><span data-stu-id="48a91-255">.NET Core SDK 1.1.8</span></span>      |[<span data-ttu-id="48a91-256">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-256">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-257">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-257">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="48a91-258">.NET Core SDK 1.1.7</span><span class="sxs-lookup"><span data-stu-id="48a91-258">.NET Core SDK 1.1.7</span></span>      |[<span data-ttu-id="48a91-259">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-259">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-260">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-260">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="48a91-261">.NET Core SDK 1.0.4</span><span class="sxs-lookup"><span data-stu-id="48a91-261">.NET Core SDK 1.0.4</span></span>      |[<span data-ttu-id="48a91-262">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-262">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-263">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-263">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="48a91-264">.NET Core SDK 1.0.1</span><span class="sxs-lookup"><span data-stu-id="48a91-264">.NET Core SDK 1.0.1</span></span>      |[<span data-ttu-id="48a91-265">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-265">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="48a91-266">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-266">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a><span data-ttu-id="48a91-267">為支援的 Debian 版本 (64 位元) 安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="48a91-267">Install .NET Core for supported Debian versions (64 bit)</span></span>

<span data-ttu-id="48a91-268">在支援的 Debian 版本 (64 位元) 上安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="48a91-268">To install .NET Core on supported Debian versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="48a91-269">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="48a91-269">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="48a91-270">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="48a91-270">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="48a91-271">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-271">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-272">在支援的 Debian 版本 (64 位元) 上安裝 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-272">Install .NET Core 2.x on supported Debian versions (64 bit):</span></span>

<span data-ttu-id="48a91-273">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="48a91-273">**.NET Core 2.0**</span></span>

|<span data-ttu-id="48a91-274">執行階段/SDK</span><span class="sxs-lookup"><span data-stu-id="48a91-274">Runtimes / SDKs</span></span>          |<span data-ttu-id="48a91-275">Debian 9</span><span class="sxs-lookup"><span data-stu-id="48a91-275">Debian 9</span></span>       |<span data-ttu-id="48a91-276">Debian 8</span><span class="sxs-lookup"><span data-stu-id="48a91-276">Debian 8</span></span>       |
|-------------------------|---------------|---------------|
|<span data-ttu-id="48a91-277">.NET Core Runtime 2.0.6</span><span class="sxs-lookup"><span data-stu-id="48a91-277">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="48a91-278">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-278">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[<span data-ttu-id="48a91-279">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-279">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|<span data-ttu-id="48a91-280">.NET Core Runtime 2.0.5</span><span class="sxs-lookup"><span data-stu-id="48a91-280">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="48a91-281">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-281">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[<span data-ttu-id="48a91-282">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-282">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|<span data-ttu-id="48a91-283">.NET Core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="48a91-283">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="48a91-284">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-284">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[<span data-ttu-id="48a91-285">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-285">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|<span data-ttu-id="48a91-286">.NET Core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="48a91-286">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="48a91-287">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-287">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[<span data-ttu-id="48a91-288">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-288">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |

<span data-ttu-id="48a91-289">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="48a91-289">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="48a91-290">若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。</span><span class="sxs-lookup"><span data-stu-id="48a91-290">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="48a91-291">執行階段/SDK</span><span class="sxs-lookup"><span data-stu-id="48a91-291">Runtimes / SDKs</span></span>                  |<span data-ttu-id="48a91-292">Debian 9</span><span class="sxs-lookup"><span data-stu-id="48a91-292">Debian 9</span></span>       |<span data-ttu-id="48a91-293">Debian 8</span><span class="sxs-lookup"><span data-stu-id="48a91-293">Debian 8</span></span>       |
|---------------------------------|---------------|---------------|
|<span data-ttu-id="48a91-294">.NET Core Runtime 2.1.0-preview2</span><span class="sxs-lookup"><span data-stu-id="48a91-294">.NET Core Runtime 2.1.0-preview2</span></span> |[<span data-ttu-id="48a91-295">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-295">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview2)   |[<span data-ttu-id="48a91-296">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-296">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview2)   |
|<span data-ttu-id="48a91-297">.NET Core Runtime 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="48a91-297">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="48a91-298">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-298">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview1)   |[<span data-ttu-id="48a91-299">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-299">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview1)   |
|<span data-ttu-id="48a91-300">.NET Core SDK 2.1.300-preview2</span><span class="sxs-lookup"><span data-stu-id="48a91-300">.NET Core SDK 2.1.300-preview2</span></span>   |[<span data-ttu-id="48a91-301">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-301">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview2)   |[<span data-ttu-id="48a91-302">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-302">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview2)   |
|<span data-ttu-id="48a91-303">.NET Core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="48a91-303">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="48a91-304">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-304">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview1)   |[<span data-ttu-id="48a91-305">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-305">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview1)   |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="48a91-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-306">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="48a91-307">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-307">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-308">若要在 Debian 9 或 Debian 8 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-308">Install .NET Core 1.x on Debian 9 or Debian 8:</span></span>

* <span data-ttu-id="48a91-309">.NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-309">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="48a91-310">.NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-310">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="48a91-311">.NET Core Runtime 1.0.10 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-311">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="48a91-312">.NET Core Runtime 1.0.9 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-312">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="48a91-313">.NET Core SDK 1.1.8 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-313">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="48a91-314">.NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-314">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="48a91-315">.NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-315">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="48a91-316">.NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-316">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a><span data-ttu-id="48a91-317">為支援的 Fedora 版本 (64 位元) 安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="48a91-317">Install .NET Core for supported Fedora versions (64 bit)</span></span>

<span data-ttu-id="48a91-318">若要在支援的 Fedora 版本上安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="48a91-318">To install .NET Core on supported Fedora versions:</span></span>

> [!NOTE]
> <span data-ttu-id="48a91-319">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="48a91-319">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="48a91-320">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="48a91-320">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="48a91-321">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-321">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-322">在支援的 Fedora 版本 (64 位元) 上安裝 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-322">Install .NET Core 2.x on supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="48a91-323">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="48a91-323">**.NET Core 2.0**</span></span>

|<span data-ttu-id="48a91-324">執行階段/SDK</span><span class="sxs-lookup"><span data-stu-id="48a91-324">Runtimes / SDKs</span></span>          |<span data-ttu-id="48a91-325">Fedora 26 或更新版本</span><span class="sxs-lookup"><span data-stu-id="48a91-325">Fedora 26 or later</span></span> |<span data-ttu-id="48a91-326">Fedora 25 或更舊版本</span><span class="sxs-lookup"><span data-stu-id="48a91-326">Fedora 25 or previous</span></span> |
|-------------------------|-------------------|----------------------|
|<span data-ttu-id="48a91-327">.NET Core Runtime 2.0.6</span><span class="sxs-lookup"><span data-stu-id="48a91-327">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="48a91-328">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-328">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[<span data-ttu-id="48a91-329">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-329">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|<span data-ttu-id="48a91-330">.NET Core Runtime 2.0.5</span><span class="sxs-lookup"><span data-stu-id="48a91-330">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="48a91-331">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-331">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[<span data-ttu-id="48a91-332">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-332">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|<span data-ttu-id="48a91-333">.NET Core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="48a91-333">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="48a91-334">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-334">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[<span data-ttu-id="48a91-335">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-335">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|<span data-ttu-id="48a91-336">.NET Core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="48a91-336">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="48a91-337">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-337">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[<span data-ttu-id="48a91-338">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-338">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

<span data-ttu-id="48a91-339">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="48a91-339">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="48a91-340">若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。</span><span class="sxs-lookup"><span data-stu-id="48a91-340">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="48a91-341">執行階段/SDK</span><span class="sxs-lookup"><span data-stu-id="48a91-341">Runtimes / SDKs</span></span>                  |<span data-ttu-id="48a91-342">Fedora 26 或更新版本</span><span class="sxs-lookup"><span data-stu-id="48a91-342">Fedora 26 or later</span></span> |<span data-ttu-id="48a91-343">Fedora 25 或更舊版本</span><span class="sxs-lookup"><span data-stu-id="48a91-343">Fedora 25 or previous</span></span> |
|---------------------------------|-------------------|----------------------|
|<span data-ttu-id="48a91-344">.NET Core Runtime 2.1.0-preview2</span><span class="sxs-lookup"><span data-stu-id="48a91-344">.NET Core Runtime 2.1.0-preview2</span></span> |[<span data-ttu-id="48a91-345">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-345">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview2)       |[<span data-ttu-id="48a91-346">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-346">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview2)           |
|<span data-ttu-id="48a91-347">.NET Core Runtime 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="48a91-347">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="48a91-348">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-348">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview1)       |[<span data-ttu-id="48a91-349">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-349">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview1)           |
|<span data-ttu-id="48a91-350">.NET Core SDK 2.1.300-preview2</span><span class="sxs-lookup"><span data-stu-id="48a91-350">.NET Core SDK 2.1.300-preview2</span></span>   |[<span data-ttu-id="48a91-351">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-351">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview2)       |[<span data-ttu-id="48a91-352">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-352">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview2)           |
|<span data-ttu-id="48a91-353">.NET Core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="48a91-353">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="48a91-354">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-354">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview1)       |[<span data-ttu-id="48a91-355">安裝連結</span><span class="sxs-lookup"><span data-stu-id="48a91-355">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview1)           |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="48a91-356">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-356">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="48a91-357">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-357">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-358">在支援的 Fedora 版本 (64 位元) 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-358">Install .NET Core 1.x supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="48a91-359">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="48a91-359">**Fedora 24**</span></span>

* <span data-ttu-id="48a91-360">.NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-360">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="48a91-361">.NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-361">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="48a91-362">.NET Core SDK 1.1.8 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-362">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="48a91-363">.NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-363">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="48a91-364">.NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-364">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

<span data-ttu-id="48a91-365">**Fedora 23**</span><span class="sxs-lookup"><span data-stu-id="48a91-365">**Fedora 23**</span></span>

* <span data-ttu-id="48a91-366">.NET Core Runtime 1.0.9 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-366">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="48a91-367">.NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-367">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="48a91-368">.NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-368">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a><span data-ttu-id="48a91-369">為支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="48a91-369">Install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit)</span></span>

<span data-ttu-id="48a91-370">若要為支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="48a91-370">To install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="48a91-371">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="48a91-371">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="48a91-372">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="48a91-372">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="48a91-373">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-373">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-374">在支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 上安裝 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-374">Install .NET Core 2.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

<span data-ttu-id="48a91-375">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="48a91-375">**.NET Core 2.0**</span></span>

* <span data-ttu-id="48a91-376">.NET Core Runtime 2.0.6 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="48a91-376">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span></span>
* <span data-ttu-id="48a91-377">.NET Core Runtime 2.0.5 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="48a91-377">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span></span>
* <span data-ttu-id="48a91-378">.NET Core SDK 2.1.103 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="48a91-378">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span></span>
* <span data-ttu-id="48a91-379">.NET Core SDK 2.0.3 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="48a91-379">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span></span>
 
<span data-ttu-id="48a91-380">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="48a91-380">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="48a91-381">若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview/)。</span><span class="sxs-lookup"><span data-stu-id="48a91-381">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview/).</span></span>

* <span data-ttu-id="48a91-382">.NET Core Runtime 2.1.0-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview2)</span><span class="sxs-lookup"><span data-stu-id="48a91-382">.NET Core Runtime 2.1.0-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview2)</span></span>
* <span data-ttu-id="48a91-383">.NET Core Runtime 2.1.0-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="48a91-383">.NET Core Runtime 2.1.0-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="48a91-384">.NET Core SDK 2.1.300-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview2)</span><span class="sxs-lookup"><span data-stu-id="48a91-384">.NET Core SDK 2.1.300-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview2)</span></span>
* <span data-ttu-id="48a91-385">.NET Core SDK 2.1.300-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="48a91-385">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="48a91-386">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-386">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="48a91-387">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-387">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-388">在支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-388">Install .NET Core 1.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

* <span data-ttu-id="48a91-389">.NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-389">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="48a91-390">.NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-390">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="48a91-391">.NET Core Runtime 1.0.10 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-391">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="48a91-392">.NET Core Runtime 1.0.9 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-392">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="48a91-393">.NET Core SDK 1.1.8 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-393">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="48a91-394">.NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-394">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="48a91-395">.NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-395">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="48a91-396">.NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-396">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a><span data-ttu-id="48a91-397">為支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 安裝.NET Core</span><span class="sxs-lookup"><span data-stu-id="48a91-397">Install .NET Core for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit)</span></span>

<span data-ttu-id="48a91-398">為支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 安裝.NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-398">To install .NET Core 2.x for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="48a91-399">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="48a91-399">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="48a91-400">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-400">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-401">在支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 上安裝.NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="48a91-401">Install .NET Core 2.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="48a91-402">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="48a91-402">**.NET Core 2.0**</span></span>

* <span data-ttu-id="48a91-403">.NET Core Runtime 2.0.6 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="48a91-403">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span></span>
* <span data-ttu-id="48a91-404">.NET Core Runtime 2.0.5 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="48a91-404">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span></span>
* <span data-ttu-id="48a91-405">.NET Core SDK 2.1.103 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="48a91-405">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span></span>
* <span data-ttu-id="48a91-406">.NET Core SDK 2.0.3 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="48a91-406">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span></span>
 
<span data-ttu-id="48a91-407">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="48a91-407">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="48a91-408">若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。</span><span class="sxs-lookup"><span data-stu-id="48a91-408">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

* <span data-ttu-id="48a91-409">.NET Core Runtime 2.1.0-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview2)</span><span class="sxs-lookup"><span data-stu-id="48a91-409">.NET Core Runtime 2.1.0-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview2)</span></span>
* <span data-ttu-id="48a91-410">.NET Core Runtime 2.1.0-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="48a91-410">.NET Core Runtime 2.1.0-preview1  [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="48a91-411">.NET Core SDK 2.1.300-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview2)</span><span class="sxs-lookup"><span data-stu-id="48a91-411">.NET Core SDK 2.1.300-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview2)</span></span>
* <span data-ttu-id="48a91-412">.NET Core SDK 2.1.300-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="48a91-412">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="48a91-413">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-413">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="48a91-414">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="48a91-414">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="48a91-415">在支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 上安裝.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="48a91-415">Install .NET Core 1.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="48a91-416">**SUSE Linux Enterprise Server 13.2**</span><span class="sxs-lookup"><span data-stu-id="48a91-416">**SUSE Linux Enterprise Server 13.2**</span></span>

* <span data-ttu-id="48a91-417">.NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-417">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="48a91-418">.NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-418">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="48a91-419">.NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-419">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>

<span data-ttu-id="48a91-420">**openSUSE 24**</span><span class="sxs-lookup"><span data-stu-id="48a91-420">**openSUSE 24**</span></span>

* <span data-ttu-id="48a91-421">.NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-421">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span></span>
* <span data-ttu-id="48a91-422">.NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="48a91-422">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span></span>

---

> [!IMPORTANT]
> <span data-ttu-id="48a91-423">如果您在支援的 Linux 發行版本/版本上安裝 .NET Core 的相關問題，請參閱已安裝之發行版本/版本的下列主題：</span><span class="sxs-lookup"><span data-stu-id="48a91-423">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>
> * [<span data-ttu-id="48a91-424">.NET Core 2.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="48a91-424">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [<span data-ttu-id="48a91-425">.NET Core 2.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="48a91-425">.NET Core 2.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [<span data-ttu-id="48a91-426">.NET Core 1.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="48a91-426">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [<span data-ttu-id="48a91-427">.NET Core 1.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="48a91-427">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)