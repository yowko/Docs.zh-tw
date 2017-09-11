---
title: "Linux 上 .NET Core 的必要條件"
description: "支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 7bbb8405f39a52d2798fd1dbc78f3116cb3bedbb
ms.openlocfilehash: 9864ffa31caa007cb649a9e6e8913863d9cb2c35
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="7502a-104">Linux 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="7502a-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="7502a-105">本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="7502a-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="7502a-106">支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="7502a-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="7502a-107">使用命令列搭配您偏好的編輯器</span><span class="sxs-lookup"><span data-stu-id="7502a-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="7502a-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7502a-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="7502a-109">支援的 Linux 版本</span><span class="sxs-lookup"><span data-stu-id="7502a-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7502a-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7502a-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7502a-111">.NET Core 2.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="7502a-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="7502a-112">針對每個支援的 Linux 發行版本與每種晶片架構，會有單一的 Linux 組建。</span><span class="sxs-lookup"><span data-stu-id="7502a-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="7502a-113">在下列 Linux x64 發行版本/版本上可支援 NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="7502a-113">NET Core 2.x is supported on the following Linux x64 distributions/versions:</span></span>

 * <span data-ttu-id="7502a-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7502a-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="7502a-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7502a-115">CentOS 7</span></span>
 * <span data-ttu-id="7502a-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7502a-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="7502a-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="7502a-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="7502a-118">Debian 8.7 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7502a-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="7502a-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7502a-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="7502a-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="7502a-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="7502a-121">openSUSE 42.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7502a-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="7502a-122">SUSE Enterprise Linux (SLES) 12 SP2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7502a-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="7502a-123">如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7502a-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7502a-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7502a-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7502a-125">在下列 Linux x64 發行版本/版本上可支援 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="7502a-125">.NET Core 1.x is supported on the following Linux x64 distributions/versions:</span></span>

* <span data-ttu-id="7502a-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7502a-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="7502a-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7502a-127">CentOS 7</span></span>
* <span data-ttu-id="7502a-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7502a-128">Oracle Linux 7</span></span>
* <span data-ttu-id="7502a-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="7502a-129">Fedora 24</span></span>
* <span data-ttu-id="7502a-130">Debian 8.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7502a-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="7502a-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="7502a-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="7502a-132">最新的 .NET Core 1.1 修補程式版本支援 Ubuntu 16.10</span><span class="sxs-lookup"><span data-stu-id="7502a-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="7502a-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="7502a-133">Linux Mint 17</span></span>
* <span data-ttu-id="7502a-134">openSUSE 42.1 或更新的版本 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="7502a-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="7502a-135">如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7502a-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="7502a-136">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="7502a-136">Linux distribution dependencies</span></span>

### <a name="ubuntu"></a><span data-ttu-id="7502a-137">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7502a-137">Ubuntu</span></span>

<span data-ttu-id="7502a-138">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="7502a-138">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7502a-139">libunwind8</span><span class="sxs-lookup"><span data-stu-id="7502a-139">libunwind8</span></span>
* <span data-ttu-id="7502a-140">libunwind8-dev</span><span class="sxs-lookup"><span data-stu-id="7502a-140">libunwind8-dev</span></span>
* <span data-ttu-id="7502a-141">gettext</span><span class="sxs-lookup"><span data-stu-id="7502a-141">gettext</span></span>
* <span data-ttu-id="7502a-142">libicu-dev</span><span class="sxs-lookup"><span data-stu-id="7502a-142">libicu-dev</span></span>
* <span data-ttu-id="7502a-143">liblttng-ust-dev</span><span class="sxs-lookup"><span data-stu-id="7502a-143">liblttng-ust-dev</span></span>
* <span data-ttu-id="7502a-144">libcurl4-openssl-dev</span><span class="sxs-lookup"><span data-stu-id="7502a-144">libcurl4-openssl-dev</span></span>
* <span data-ttu-id="7502a-145">libssl-dev</span><span class="sxs-lookup"><span data-stu-id="7502a-145">libssl-dev</span></span>
* <span data-ttu-id="7502a-146">uuid-dev</span><span class="sxs-lookup"><span data-stu-id="7502a-146">uuid-dev</span></span>
* <span data-ttu-id="7502a-147">unzip</span><span class="sxs-lookup"><span data-stu-id="7502a-147">unzip</span></span>

### <a name="centos"></a><span data-ttu-id="7502a-148">CentOS</span><span class="sxs-lookup"><span data-stu-id="7502a-148">CentOS</span></span>

<span data-ttu-id="7502a-149">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="7502a-149">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7502a-150">deltarpm</span><span class="sxs-lookup"><span data-stu-id="7502a-150">deltarpm</span></span>
* <span data-ttu-id="7502a-151">epel-release</span><span class="sxs-lookup"><span data-stu-id="7502a-151">epel-release</span></span>
* <span data-ttu-id="7502a-152">unzip</span><span class="sxs-lookup"><span data-stu-id="7502a-152">unzip</span></span>
* <span data-ttu-id="7502a-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="7502a-153">libunwind</span></span>
* <span data-ttu-id="7502a-154">gettext</span><span class="sxs-lookup"><span data-stu-id="7502a-154">gettext</span></span>
* <span data-ttu-id="7502a-155">libcurl-devel</span><span class="sxs-lookup"><span data-stu-id="7502a-155">libcurl-devel</span></span>
* <span data-ttu-id="7502a-156">openssl-devel</span><span class="sxs-lookup"><span data-stu-id="7502a-156">openssl-devel</span></span>
* <span data-ttu-id="7502a-157">zlib</span><span class="sxs-lookup"><span data-stu-id="7502a-157">zlib</span></span>
* <span data-ttu-id="7502a-158">libicu-devel</span><span class="sxs-lookup"><span data-stu-id="7502a-158">libicu-devel</span></span>

<span data-ttu-id="7502a-159">如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="7502a-159">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="7502a-160">使用原生安裝程式來安裝 .NET Core 相依性</span><span class="sxs-lookup"><span data-stu-id="7502a-160">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="7502a-161">受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="7502a-161">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="7502a-162">原生安裝程式需要伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="7502a-162">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="7502a-163">使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。</span><span class="sxs-lookup"><span data-stu-id="7502a-163">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="7502a-164">原生安裝程式也會安裝 .NET Core SDK 全系統。</span><span class="sxs-lookup"><span data-stu-id="7502a-164">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="7502a-165">Linux 上有兩個安裝程式套件選擇：</span><span class="sxs-lookup"><span data-stu-id="7502a-165">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="7502a-166">使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。</span><span class="sxs-lookup"><span data-stu-id="7502a-166">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="7502a-167">使用套件本身，DEB 或 RPM。</span><span class="sxs-lookup"><span data-stu-id="7502a-167">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="7502a-168">使用 .NET Core 安裝程式指令碼以指令碼進行安裝</span><span class="sxs-lookup"><span data-stu-id="7502a-168">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="7502a-169">`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。</span><span class="sxs-lookup"><span data-stu-id="7502a-169">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="7502a-170">您可以從 [CLI GitHub 存放庫 (英文)](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain) 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="7502a-170">You can download the scripts from the [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span></span>

<span data-ttu-id="7502a-171">安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="7502a-171">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="7502a-172">此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="7502a-172">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7502a-173">執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。</span><span class="sxs-lookup"><span data-stu-id="7502a-173">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7502a-174">安裝 Red Hat Enterprise Linux (RHEL) 7 的 .NET Core</span><span class="sxs-lookup"><span data-stu-id="7502a-174">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7502a-175">若要在 RHEL 7 上安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="7502a-175">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="7502a-176">啟用 Red Hat .NET 通道，位於 RHEL 7 訂閱底下。</span><span class="sxs-lookup"><span data-stu-id="7502a-176">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="7502a-177">Red Hat Enterprise 7 伺服器請使用：</span><span class="sxs-lookup"><span data-stu-id="7502a-177">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="7502a-178">Red Hat Enterprise 7 工作站請使用：</span><span class="sxs-lookup"><span data-stu-id="7502a-178">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="7502a-179">Red Hat Enterprise 7 HPC 計算節點請使用：</span><span class="sxs-lookup"><span data-stu-id="7502a-179">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="7502a-180">安裝 scl 工具。</span><span class="sxs-lookup"><span data-stu-id="7502a-180">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="7502a-181">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="7502a-181">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7502a-182">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7502a-182">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7502a-183">安裝 .NET Core 2.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7502a-183">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="7502a-184">為環境啟用 .NET Core 2.0 SDK/執行階段：</span><span class="sxs-lookup"><span data-stu-id="7502a-184">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7502a-185">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7502a-185">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7502a-186">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="7502a-186">**.NET Core 1.1**</span></span>

<span data-ttu-id="7502a-187">安裝 .NET Core 1.1 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7502a-187">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="7502a-188">為環境啟用 .NET Core 1.1 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7502a-188">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="7502a-189">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="7502a-189">**.NET Core 1.0**</span></span>

<span data-ttu-id="7502a-190">安裝 .NET Core 1.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7502a-190">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="7502a-191">為環境啟用 .NET Core 1.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7502a-191">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="7502a-192">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-192">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="7502a-193">如需 Red Hat .NET 通道存取登錄說明，請參閱 Red Hat 的 [.NET Core 1.1 入門指南的第 1 章](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)。</span><span class="sxs-lookup"><span data-stu-id="7502a-193">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="7502a-194">安裝適用於 Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 與 Linux Mint 17, Linux Mint 18 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7502a-194">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="7502a-195">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7502a-195">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7502a-196">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7502a-196">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7502a-197">註冊受信任的 Microsoft 產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="7502a-197">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="7502a-198">設定所需的裝載套件摘要版本。</span><span class="sxs-lookup"><span data-stu-id="7502a-198">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="7502a-199">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="7502a-199">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="7502a-200">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="7502a-200">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="7502a-201">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="7502a-201">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="7502a-202">安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7502a-202">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="7502a-203">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-203">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7502a-204">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7502a-204">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7502a-205">設定所需的裝載套件摘要版本。</span><span class="sxs-lookup"><span data-stu-id="7502a-205">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="7502a-206">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="7502a-206">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="7502a-207">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="7502a-207">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="7502a-208">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="7502a-208">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="7502a-209">在 Ubuntu 或 Linux Mint 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="7502a-209">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="7502a-210">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-210">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="7502a-211">安裝適用於 Debian 8 或 Debian 9 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7502a-211">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="7502a-212">若要在 Debian 8 或 Debian 9 上安裝 .NET Core (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="7502a-212">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="7502a-213">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7502a-213">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7502a-214">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7502a-214">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7502a-215">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7502a-215">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7502a-216">安裝系統元件。</span><span class="sxs-lookup"><span data-stu-id="7502a-216">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="7502a-217">註冊受信任的 Microsoft 產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="7502a-217">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="7502a-218">註冊 Microsoft 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7502a-218">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="7502a-219">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="7502a-219">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="7502a-220">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="7502a-220">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="7502a-221">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7502a-221">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="7502a-222">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-222">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7502a-223">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7502a-223">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7502a-224">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7502a-224">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="7502a-225">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7502a-225">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="7502a-226">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7502a-226">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7502a-227">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-227">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="7502a-228">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-228">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="7502a-229">安裝適用於 Fedora 24, Fedora 25 或 Fedora 26 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7502a-229">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="7502a-230">若要安裝適用於 Fedora 26, Fedora 25 (.NET Core 2.x) 或 Fedora 24 (.NET Core 1.x) 的 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="7502a-230">To Install .NET Core for Fedora 26, Fedora 25 (.NET Core 2.x) or Fedora 24 (.NET Core 1.x):</span></span>

1. <span data-ttu-id="7502a-231">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7502a-231">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7502a-232">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7502a-232">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7502a-233">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7502a-233">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7502a-234">**Fedora 26 或 Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="7502a-234">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="7502a-235">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="7502a-235">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="7502a-236">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7502a-236">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="7502a-237">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7502a-237">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="7502a-238">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-238">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7502a-239">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7502a-239">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7502a-240">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="7502a-240">**Fedora 24**</span></span>

2. <span data-ttu-id="7502a-241">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7502a-241">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="7502a-242">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7502a-242">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="7502a-243">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7502a-243">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7502a-244">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-244">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="7502a-245">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-245">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="7502a-246">安裝 .NET Core for CentOS 7.1 (64 位元) 以及 Oracle Linux 7.1 (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7502a-246">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="7502a-247">安裝 .NET Core for CentOS 7.1 (64 位元) 以及 Oracle Linux 7.1 (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="7502a-247">To Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="7502a-248">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7502a-248">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7502a-249">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7502a-249">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7502a-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7502a-250">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7502a-251">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="7502a-251">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="7502a-252">新增 Microsoft 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7502a-252">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="7502a-253">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7502a-253">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="7502a-254">將 dotnet 新增至 PATH</span><span class="sxs-lookup"><span data-stu-id="7502a-254">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7502a-255">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7502a-255">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7502a-256">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7502a-256">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="7502a-257">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7502a-257">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="7502a-258">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7502a-258">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7502a-259">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-259">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="7502a-260">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-260">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="7502a-261">安裝適用於 SUSE Linux Enterprise Server 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7502a-261">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="7502a-262">若要安裝適用於 SUSE Linux Enterprise Server (SLES) 12 SP2 的 .NET Core 2.x (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="7502a-262">To Install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="7502a-263">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7502a-263">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="7502a-264">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7502a-264">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="7502a-265">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7502a-265">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="7502a-266">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-266">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="7502a-267">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-267">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="7502a-268">安裝適用於 openSUSE 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7502a-268">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="7502a-269">若要安裝適用於 openSUSE 的 .NET Core 2.x 或適用於 openSUSE 的 .NET Core 1.x (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="7502a-269">To Install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="7502a-270">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7502a-270">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7502a-271">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7502a-271">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7502a-272">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7502a-272">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7502a-273">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="7502a-273">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="7502a-274">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7502a-274">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="7502a-275">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7502a-275">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="7502a-276">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-276">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7502a-277">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7502a-277">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7502a-278">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7502a-278">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="7502a-279">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7502a-279">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="7502a-280">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7502a-280">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7502a-281">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7502a-281">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="7502a-282">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7502a-282">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="7502a-283">如果支援的 Linux 發行版本/版本遇到 .NET Core 2.x 安裝問題，請參閱已安裝的發行版本/版本的 [2.0 已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。</span><span class="sxs-lookup"><span data-stu-id="7502a-283">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="7502a-284">如果支援的 Linux 發行版本/版本遇到 .NET Core 1.x 安裝問題，請參閱已安裝的發行版本/版本的 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。</span><span class="sxs-lookup"><span data-stu-id="7502a-284">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>

