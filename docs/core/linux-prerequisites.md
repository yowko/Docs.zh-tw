---
title: "Linux 上 .NET Core 的必要條件"
description: "支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 12/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload:
- dotnetcore
ms.openlocfilehash: 913d3869559b10af508e695a06d06021f8f90175
ms.sourcegitcommit: adcf9bdafeaa6bc243af7bf70b45f3df954f256a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="af5ee-104">Linux 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="af5ee-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="af5ee-105">本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="af5ee-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="af5ee-106">支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="af5ee-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="af5ee-107">使用命令列搭配您偏好的編輯器</span><span class="sxs-lookup"><span data-stu-id="af5ee-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="af5ee-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="af5ee-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="af5ee-109">支援的 Linux 版本</span><span class="sxs-lookup"><span data-stu-id="af5ee-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af5ee-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="af5ee-111">.NET Core 2.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="af5ee-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="af5ee-112">針對每個支援的 Linux 發行版本與每種晶片架構，會有單一的 Linux 組建。</span><span class="sxs-lookup"><span data-stu-id="af5ee-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="af5ee-113">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="af5ee-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="af5ee-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="af5ee-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="af5ee-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="af5ee-115">CentOS 7</span></span>
 * <span data-ttu-id="af5ee-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="af5ee-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="af5ee-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="af5ee-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="af5ee-118">Debian 8.7 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="af5ee-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="af5ee-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="af5ee-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="af5ee-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="af5ee-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="af5ee-121">openSUSE 42.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="af5ee-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="af5ee-122">SUSE Enterprise Linux (SLES) 12 SP2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="af5ee-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="af5ee-123">如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af5ee-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="af5ee-125">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="af5ee-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="af5ee-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="af5ee-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="af5ee-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="af5ee-127">CentOS 7</span></span>
* <span data-ttu-id="af5ee-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="af5ee-128">Oracle Linux 7</span></span>
* <span data-ttu-id="af5ee-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="af5ee-129">Fedora 24</span></span>
* <span data-ttu-id="af5ee-130">Debian 8.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="af5ee-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="af5ee-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="af5ee-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="af5ee-132">最新的 .NET Core 1.1 修補程式版本支援 Ubuntu 16.10</span><span class="sxs-lookup"><span data-stu-id="af5ee-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="af5ee-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="af5ee-133">Linux Mint 17</span></span>
* <span data-ttu-id="af5ee-134">openSUSE 42.1 或更新的版本 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="af5ee-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="af5ee-135">如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="af5ee-136">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="af5ee-136">Linux distribution dependencies</span></span>

<span data-ttu-id="af5ee-137">下列要作為範例。</span><span class="sxs-lookup"><span data-stu-id="af5ee-137">The following are intended to be examples.</span></span> <span data-ttu-id="af5ee-138">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="af5ee-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="af5ee-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="af5ee-139">Ubuntu</span></span>

<span data-ttu-id="af5ee-140">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="af5ee-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="af5ee-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="af5ee-141">libunwind8</span></span>
* <span data-ttu-id="af5ee-142">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="af5ee-142">liblttng-ust0</span></span>
* <span data-ttu-id="af5ee-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="af5ee-143">libcurl3</span></span>
* <span data-ttu-id="af5ee-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="af5ee-144">libssl1.0.0</span></span>
* <span data-ttu-id="af5ee-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="af5ee-145">libuuid1</span></span>
* <span data-ttu-id="af5ee-146">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="af5ee-146">libkrb5-3</span></span>
* <span data-ttu-id="af5ee-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="af5ee-147">zlib1g</span></span>
* <span data-ttu-id="af5ee-148">libicu52 (適用於 14.X)</span><span class="sxs-lookup"><span data-stu-id="af5ee-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="af5ee-149">libicu55 (適用於 16.X)</span><span class="sxs-lookup"><span data-stu-id="af5ee-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="af5ee-150">libicu57 (適用於 17.X)</span><span class="sxs-lookup"><span data-stu-id="af5ee-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="af5ee-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="af5ee-151">CentOS</span></span>

<span data-ttu-id="af5ee-152">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="af5ee-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="af5ee-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="af5ee-153">libunwind</span></span>
* <span data-ttu-id="af5ee-154">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="af5ee-154">lttng-ust</span></span>
* <span data-ttu-id="af5ee-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="af5ee-155">libcurl</span></span>
* <span data-ttu-id="af5ee-156">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="af5ee-156">openssl-libs</span></span>
* <span data-ttu-id="af5ee-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="af5ee-157">libuuid</span></span>
* <span data-ttu-id="af5ee-158">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="af5ee-158">krb5-libs</span></span>
* <span data-ttu-id="af5ee-159">libicu</span><span class="sxs-lookup"><span data-stu-id="af5ee-159">libicu</span></span>
* <span data-ttu-id="af5ee-160">zlib</span><span class="sxs-lookup"><span data-stu-id="af5ee-160">zlib</span></span>

<span data-ttu-id="af5ee-161">如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="af5ee-162">使用原生安裝程式來安裝 .NET Core 相依性</span><span class="sxs-lookup"><span data-stu-id="af5ee-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="af5ee-163">受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="af5ee-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="af5ee-164">原生安裝程式需要伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="af5ee-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="af5ee-165">使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。</span><span class="sxs-lookup"><span data-stu-id="af5ee-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="af5ee-166">原生安裝程式也會安裝 .NET Core SDK 全系統。</span><span class="sxs-lookup"><span data-stu-id="af5ee-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="af5ee-167">Linux 上有兩個安裝程式套件選擇：</span><span class="sxs-lookup"><span data-stu-id="af5ee-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="af5ee-168">使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。</span><span class="sxs-lookup"><span data-stu-id="af5ee-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="af5ee-169">使用套件本身，DEB 或 RPM。</span><span class="sxs-lookup"><span data-stu-id="af5ee-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="af5ee-170">使用 .NET Core 安裝程式指令碼以指令碼進行安裝</span><span class="sxs-lookup"><span data-stu-id="af5ee-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="af5ee-171">`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。</span><span class="sxs-lookup"><span data-stu-id="af5ee-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="af5ee-172">指令碼下載位置：https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="af5ee-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="af5ee-173">安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="af5ee-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="af5ee-174">此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="af5ee-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af5ee-175">執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="af5ee-176">安裝 Red Hat Enterprise Linux (RHEL) 7 的 .NET Core</span><span class="sxs-lookup"><span data-stu-id="af5ee-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="af5ee-177">若要在 RHEL 7 上安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="af5ee-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="af5ee-178">啟用 Red Hat .NET 通道，位於 RHEL 7 訂閱底下。</span><span class="sxs-lookup"><span data-stu-id="af5ee-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="af5ee-179">Red Hat Enterprise 7 伺服器請使用：</span><span class="sxs-lookup"><span data-stu-id="af5ee-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="af5ee-180">Red Hat Enterprise 7 工作站請使用：</span><span class="sxs-lookup"><span data-stu-id="af5ee-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="af5ee-181">Red Hat Enterprise 7 HPC 計算節點請使用：</span><span class="sxs-lookup"><span data-stu-id="af5ee-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="af5ee-182">安裝 scl 工具。</span><span class="sxs-lookup"><span data-stu-id="af5ee-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="af5ee-183">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="af5ee-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af5ee-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="af5ee-185">安裝 .NET Core 2.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="af5ee-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="af5ee-186">為環境啟用 .NET Core 2.0 SDK/執行階段：</span><span class="sxs-lookup"><span data-stu-id="af5ee-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af5ee-187">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="af5ee-188">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="af5ee-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="af5ee-189">安裝 .NET Core 1.1 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="af5ee-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="af5ee-190">為環境啟用 .NET Core 1.1 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="af5ee-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="af5ee-191">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="af5ee-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="af5ee-192">安裝 .NET Core 1.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="af5ee-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="af5ee-193">為環境啟用 .NET Core 1.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="af5ee-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="af5ee-194">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="af5ee-195">如需 Red Hat .NET 通道存取登錄說明，請參閱 Red Hat 的 [.NET Core 1.1 入門指南的第 1 章](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="af5ee-196">安裝適用於 Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 與 Linux Mint 17, Linux Mint 18 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="af5ee-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="af5ee-197">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="af5ee-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af5ee-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="af5ee-199">註冊受信任的 Microsoft 產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="af5ee-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="af5ee-200">設定所需的裝載套件摘要版本。</span><span class="sxs-lookup"><span data-stu-id="af5ee-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="af5ee-201">**Ubuntu 17.10**</span><span class="sxs-lookup"><span data-stu-id="af5ee-201">**Ubuntu 17.10**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   <span data-ttu-id="af5ee-202">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="af5ee-202">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="af5ee-203">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="af5ee-203">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="af5ee-204">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="af5ee-204">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="af5ee-205">安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="af5ee-205">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.1.4
   ```

4. <span data-ttu-id="af5ee-206">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-206">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af5ee-207">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-207">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="af5ee-208">設定所需的裝載套件摘要版本。</span><span class="sxs-lookup"><span data-stu-id="af5ee-208">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="af5ee-209">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="af5ee-209">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="af5ee-210">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="af5ee-210">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="af5ee-211">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="af5ee-211">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="af5ee-212">在 Ubuntu 或 Linux Mint 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="af5ee-212">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="af5ee-213">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-213">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="af5ee-214">安裝適用於 Debian 8 或 Debian 9 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="af5ee-214">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="af5ee-215">若要在 Debian 8 或 Debian 9 上安裝 .NET Core (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="af5ee-215">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="af5ee-216">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="af5ee-216">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="af5ee-217">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="af5ee-217">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af5ee-218">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-218">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="af5ee-219">安裝系統元件。</span><span class="sxs-lookup"><span data-stu-id="af5ee-219">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="af5ee-220">註冊受信任的 Microsoft 產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="af5ee-220">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="af5ee-221">註冊 Microsoft 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="af5ee-221">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="af5ee-222">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="af5ee-222">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="af5ee-223">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="af5ee-223">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="af5ee-224">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="af5ee-224">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="af5ee-225">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-225">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="af5ee-226">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-226">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af5ee-227">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-227">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="af5ee-228">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="af5ee-228">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="af5ee-229">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-229">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="af5ee-230">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="af5ee-230">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="af5ee-231">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-231">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="af5ee-232">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-232">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="af5ee-233">安裝適用於 Fedora 24, Fedora 25 或 Fedora 26 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="af5ee-233">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="af5ee-234">在 Fedora 26 或 Fedora 25 上安裝 .NET Core 2.x，或在 Fedora 24 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="af5ee-234">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="af5ee-235">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="af5ee-235">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="af5ee-236">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="af5ee-236">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af5ee-237">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-237">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="af5ee-238">**Fedora 26 或 Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="af5ee-238">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="af5ee-239">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="af5ee-239">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="af5ee-240">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="af5ee-240">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="af5ee-241">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="af5ee-241">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="af5ee-242">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-242">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af5ee-243">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-243">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="af5ee-244">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="af5ee-244">**Fedora 24**</span></span>

2. <span data-ttu-id="af5ee-245">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="af5ee-245">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="af5ee-246">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-246">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="af5ee-247">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="af5ee-247">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="af5ee-248">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-248">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="af5ee-249">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-249">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="af5ee-250">安裝 .NET Core for CentOS 7.1 (64 位元) 以及 Oracle Linux 7.1 (64 位元)</span><span class="sxs-lookup"><span data-stu-id="af5ee-250">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="af5ee-251">安裝 .NET Core for CentOS 7.1 (64 位元) 與 Oracle Linux 7.1 (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="af5ee-251">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="af5ee-252">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="af5ee-252">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="af5ee-253">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="af5ee-253">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af5ee-254">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-254">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="af5ee-255">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="af5ee-255">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="af5ee-256">新增 Microsoft 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="af5ee-256">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="af5ee-257">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="af5ee-257">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="af5ee-258">將 dotnet 新增至 PATH</span><span class="sxs-lookup"><span data-stu-id="af5ee-258">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af5ee-259">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-259">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="af5ee-260">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="af5ee-260">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="af5ee-261">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-261">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="af5ee-262">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="af5ee-262">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="af5ee-263">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-263">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="af5ee-264">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-264">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="af5ee-265">安裝適用於 SUSE Linux Enterprise Server 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="af5ee-265">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="af5ee-266">安裝適用於 SUSE Linux Enterprise Server (SLES) 12 SP2 (64 位元) 的 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="af5ee-266">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="af5ee-267">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="af5ee-267">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="af5ee-268">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="af5ee-268">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="af5ee-269">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="af5ee-269">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="af5ee-270">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-270">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="af5ee-271">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-271">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="af5ee-272">安裝適用於 openSUSE 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="af5ee-272">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="af5ee-273">安裝適用於 openSUSE 的 .NET Core 2.x 或適用於 openSUSE (64 位元) 的 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="af5ee-273">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="af5ee-274">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="af5ee-274">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="af5ee-275">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="af5ee-275">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af5ee-276">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-276">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="af5ee-277">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="af5ee-277">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="af5ee-278">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="af5ee-278">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="af5ee-279">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="af5ee-279">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="af5ee-280">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-280">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af5ee-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af5ee-281">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="af5ee-282">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="af5ee-282">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="af5ee-283">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="af5ee-283">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="af5ee-284">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="af5ee-284">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="af5ee-285">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="af5ee-285">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="af5ee-286">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="af5ee-286">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="af5ee-287">如果支援的 Linux 發行版本/版本遇到 .NET Core 2.x 安裝問題，請參閱已安裝的發行版本/版本的 [2.0 已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。</span><span class="sxs-lookup"><span data-stu-id="af5ee-287">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="af5ee-288">如果支援的 Linux 發行版本/版本遇到 .NET Core 1.x 安裝問題，請參閱已安裝的發行版本/版本的 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。</span><span class="sxs-lookup"><span data-stu-id="af5ee-288">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
