---
title: "Linux 上 .NET Core 的必要條件"
description: "支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.openlocfilehash: 04fdf26e150e6d489c0641588563f69f24835615
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="7e2da-104">Linux 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="7e2da-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="7e2da-105">本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="7e2da-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="7e2da-106">支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="7e2da-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="7e2da-107">使用命令列搭配您偏好的編輯器</span><span class="sxs-lookup"><span data-stu-id="7e2da-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="7e2da-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7e2da-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="7e2da-109">支援的 Linux 版本</span><span class="sxs-lookup"><span data-stu-id="7e2da-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e2da-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7e2da-111">.NET Core 2.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="7e2da-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="7e2da-112">針對每個支援的 Linux 發行版本與每種晶片架構，會有單一的 Linux 組建。</span><span class="sxs-lookup"><span data-stu-id="7e2da-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="7e2da-113">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="7e2da-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="7e2da-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7e2da-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="7e2da-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7e2da-115">CentOS 7</span></span>
 * <span data-ttu-id="7e2da-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7e2da-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="7e2da-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="7e2da-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="7e2da-118">Debian 8.7 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7e2da-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="7e2da-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7e2da-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="7e2da-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="7e2da-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="7e2da-121">openSUSE 42.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7e2da-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="7e2da-122">SUSE Enterprise Linux (SLES) 12 SP2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7e2da-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="7e2da-123">如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e2da-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7e2da-125">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="7e2da-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="7e2da-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7e2da-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="7e2da-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7e2da-127">CentOS 7</span></span>
* <span data-ttu-id="7e2da-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7e2da-128">Oracle Linux 7</span></span>
* <span data-ttu-id="7e2da-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="7e2da-129">Fedora 24</span></span>
* <span data-ttu-id="7e2da-130">Debian 8.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="7e2da-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="7e2da-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="7e2da-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="7e2da-132">最新的 .NET Core 1.1 修補程式版本支援 Ubuntu 16.10</span><span class="sxs-lookup"><span data-stu-id="7e2da-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="7e2da-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="7e2da-133">Linux Mint 17</span></span>
* <span data-ttu-id="7e2da-134">openSUSE 42.1 或更新的版本 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="7e2da-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="7e2da-135">如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="7e2da-136">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="7e2da-136">Linux distribution dependencies</span></span>

<span data-ttu-id="7e2da-137">下列被要作為範例。</span><span class="sxs-lookup"><span data-stu-id="7e2da-137">The following are intended to be examples.</span></span> <span data-ttu-id="7e2da-138">確切的版本和名稱會有些許上您所選擇的 Linux 散發。</span><span class="sxs-lookup"><span data-stu-id="7e2da-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="7e2da-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7e2da-139">Ubuntu</span></span>

<span data-ttu-id="7e2da-140">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="7e2da-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7e2da-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="7e2da-141">libunwind8</span></span>
* <span data-ttu-id="7e2da-142">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="7e2da-142">liblttng-ust0</span></span>
* <span data-ttu-id="7e2da-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="7e2da-143">libcurl3</span></span>
* <span data-ttu-id="7e2da-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="7e2da-144">libssl1.0.0</span></span>
* <span data-ttu-id="7e2da-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="7e2da-145">libuuid1</span></span>
* <span data-ttu-id="7e2da-146">libkrb5</span><span class="sxs-lookup"><span data-stu-id="7e2da-146">libkrb5</span></span>
* <span data-ttu-id="7e2da-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="7e2da-147">zlib1g</span></span>
* <span data-ttu-id="7e2da-148">libicu52 （適用於 14.X)</span><span class="sxs-lookup"><span data-stu-id="7e2da-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="7e2da-149">libicu55 （適用於 16.X)</span><span class="sxs-lookup"><span data-stu-id="7e2da-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="7e2da-150">libicu57 （適用於 17.X)</span><span class="sxs-lookup"><span data-stu-id="7e2da-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="7e2da-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="7e2da-151">CentOS</span></span>

<span data-ttu-id="7e2da-152">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="7e2da-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7e2da-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="7e2da-153">libunwind</span></span>
* <span data-ttu-id="7e2da-154">lttng ust</span><span class="sxs-lookup"><span data-stu-id="7e2da-154">lttng-ust</span></span>
* <span data-ttu-id="7e2da-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="7e2da-155">libcurl</span></span>
* <span data-ttu-id="7e2da-156">openssl 程式庫</span><span class="sxs-lookup"><span data-stu-id="7e2da-156">openssl-libs</span></span>
* <span data-ttu-id="7e2da-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="7e2da-157">libuuid</span></span>
* <span data-ttu-id="7e2da-158">krb5 程式庫</span><span class="sxs-lookup"><span data-stu-id="7e2da-158">krb5-libs</span></span>
* <span data-ttu-id="7e2da-159">libicu</span><span class="sxs-lookup"><span data-stu-id="7e2da-159">libicu</span></span>
* <span data-ttu-id="7e2da-160">zlib</span><span class="sxs-lookup"><span data-stu-id="7e2da-160">zlib</span></span>

<span data-ttu-id="7e2da-161">如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="7e2da-162">使用原生安裝程式來安裝 .NET Core 相依性</span><span class="sxs-lookup"><span data-stu-id="7e2da-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="7e2da-163">受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="7e2da-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="7e2da-164">原生安裝程式需要伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="7e2da-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="7e2da-165">使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。</span><span class="sxs-lookup"><span data-stu-id="7e2da-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="7e2da-166">原生安裝程式也會安裝 .NET Core SDK 全系統。</span><span class="sxs-lookup"><span data-stu-id="7e2da-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="7e2da-167">Linux 上有兩個安裝程式套件選擇：</span><span class="sxs-lookup"><span data-stu-id="7e2da-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="7e2da-168">使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。</span><span class="sxs-lookup"><span data-stu-id="7e2da-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="7e2da-169">使用套件本身，DEB 或 RPM。</span><span class="sxs-lookup"><span data-stu-id="7e2da-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="7e2da-170">使用 .NET Core 安裝程式指令碼以指令碼進行安裝</span><span class="sxs-lookup"><span data-stu-id="7e2da-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="7e2da-171">`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。</span><span class="sxs-lookup"><span data-stu-id="7e2da-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="7e2da-172">您可以下載從指令碼： https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="7e2da-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="7e2da-173">安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="7e2da-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="7e2da-174">此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="7e2da-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e2da-175">執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7e2da-176">安裝 Red Hat Enterprise Linux (RHEL) 7 的 .NET Core</span><span class="sxs-lookup"><span data-stu-id="7e2da-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7e2da-177">若要在 RHEL 7 上安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="7e2da-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="7e2da-178">啟用 Red Hat .NET 通道，位於 RHEL 7 訂閱底下。</span><span class="sxs-lookup"><span data-stu-id="7e2da-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="7e2da-179">Red Hat Enterprise 7 伺服器請使用：</span><span class="sxs-lookup"><span data-stu-id="7e2da-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="7e2da-180">Red Hat Enterprise 7 工作站請使用：</span><span class="sxs-lookup"><span data-stu-id="7e2da-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="7e2da-181">Red Hat Enterprise 7 HPC 計算節點請使用：</span><span class="sxs-lookup"><span data-stu-id="7e2da-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="7e2da-182">安裝 scl 工具。</span><span class="sxs-lookup"><span data-stu-id="7e2da-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="7e2da-183">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="7e2da-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e2da-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7e2da-185">安裝 .NET Core 2.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7e2da-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="7e2da-186">為環境啟用 .NET Core 2.0 SDK/執行階段：</span><span class="sxs-lookup"><span data-stu-id="7e2da-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e2da-187">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7e2da-188">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="7e2da-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="7e2da-189">安裝 .NET Core 1.1 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7e2da-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="7e2da-190">為環境啟用 .NET Core 1.1 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7e2da-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="7e2da-191">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="7e2da-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="7e2da-192">安裝 .NET Core 1.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7e2da-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="7e2da-193">為環境啟用 .NET Core 1.0 SDK 及執行階段：</span><span class="sxs-lookup"><span data-stu-id="7e2da-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="7e2da-194">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="7e2da-195">如需 Red Hat .NET 通道存取登錄說明，請參閱 Red Hat 的 [.NET Core 1.1 入門指南的第 1 章](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="7e2da-196">安裝適用於 Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 與 Linux Mint 17, Linux Mint 18 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7e2da-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="7e2da-197">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7e2da-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e2da-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7e2da-199">註冊受信任的 Microsoft 產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="7e2da-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="7e2da-200">設定所需的裝載套件摘要版本。</span><span class="sxs-lookup"><span data-stu-id="7e2da-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="7e2da-201">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="7e2da-201">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="7e2da-202">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="7e2da-202">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="7e2da-203">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="7e2da-203">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="7e2da-204">安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7e2da-204">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="7e2da-205">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-205">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e2da-206">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-206">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7e2da-207">設定所需的裝載套件摘要版本。</span><span class="sxs-lookup"><span data-stu-id="7e2da-207">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="7e2da-208">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="7e2da-208">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="7e2da-209">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="7e2da-209">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="7e2da-210">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="7e2da-210">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="7e2da-211">在 Ubuntu 或 Linux Mint 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="7e2da-211">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="7e2da-212">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-212">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="7e2da-213">安裝適用於 Debian 8 或 Debian 9 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7e2da-213">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="7e2da-214">若要在 Debian 8 或 Debian 9 上安裝 .NET Core (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="7e2da-214">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="7e2da-215">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7e2da-215">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2da-216">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7e2da-216">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e2da-217">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-217">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7e2da-218">安裝系統元件。</span><span class="sxs-lookup"><span data-stu-id="7e2da-218">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="7e2da-219">註冊受信任的 Microsoft 產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="7e2da-219">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="7e2da-220">註冊 Microsoft 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7e2da-220">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="7e2da-221">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="7e2da-221">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="7e2da-222">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="7e2da-222">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="7e2da-223">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7e2da-223">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="7e2da-224">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-224">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="7e2da-225">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-225">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e2da-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-226">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7e2da-227">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7e2da-227">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="7e2da-228">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-228">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="7e2da-229">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7e2da-229">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7e2da-230">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-230">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="7e2da-231">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-231">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="7e2da-232">安裝適用於 Fedora 24, Fedora 25 或 Fedora 26 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7e2da-232">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="7e2da-233">在 Fedora 26 或 Fedora 25 上安裝 .NET Core 2.x，或在 Fedora 24 上安裝 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="7e2da-233">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="7e2da-234">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7e2da-234">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2da-235">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7e2da-235">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e2da-236">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-236">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7e2da-237">**Fedora 26 或 Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="7e2da-237">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="7e2da-238">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="7e2da-238">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="7e2da-239">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7e2da-239">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="7e2da-240">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7e2da-240">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="7e2da-241">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-241">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e2da-242">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-242">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7e2da-243">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="7e2da-243">**Fedora 24**</span></span>

2. <span data-ttu-id="7e2da-244">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7e2da-244">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="7e2da-245">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-245">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="7e2da-246">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7e2da-246">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7e2da-247">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-247">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="7e2da-248">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-248">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="7e2da-249">安裝 .NET Core for CentOS 7.1 (64 位元) 以及 Oracle Linux 7.1 (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7e2da-249">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="7e2da-250">安裝 .NET Core for CentOS 7.1 (64 位元) 與 Oracle Linux 7.1 (64 位元)：</span><span class="sxs-lookup"><span data-stu-id="7e2da-250">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="7e2da-251">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7e2da-251">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2da-252">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7e2da-252">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e2da-253">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-253">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7e2da-254">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="7e2da-254">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="7e2da-255">新增 Microsoft 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7e2da-255">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="7e2da-256">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7e2da-256">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="7e2da-257">將 dotnet 新增至 PATH</span><span class="sxs-lookup"><span data-stu-id="7e2da-257">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e2da-258">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-258">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7e2da-259">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7e2da-259">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="7e2da-260">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-260">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="7e2da-261">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7e2da-261">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7e2da-262">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-262">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="7e2da-263">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-263">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="7e2da-264">安裝適用於 SUSE Linux Enterprise Server 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7e2da-264">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="7e2da-265">安裝適用於 SUSE Linux Enterprise Server (SLES) 12 SP2 (64 位元) 的 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="7e2da-265">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="7e2da-266">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7e2da-266">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="7e2da-267">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7e2da-267">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="7e2da-268">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7e2da-268">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="7e2da-269">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-269">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="7e2da-270">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-270">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="7e2da-271">安裝適用於 openSUSE 的 .NET Core (64 位元)</span><span class="sxs-lookup"><span data-stu-id="7e2da-271">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="7e2da-272">安裝適用於 openSUSE 的 .NET Core 2.x 或適用於 openSUSE (64 位元) 的 .NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="7e2da-272">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="7e2da-273">請移除系統中所有 .NET Core **先前的預覽版**。</span><span class="sxs-lookup"><span data-stu-id="7e2da-273">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2da-274">需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。</span><span class="sxs-lookup"><span data-stu-id="7e2da-274">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e2da-275">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-275">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="7e2da-276">註冊 Microsoft 簽章金鑰。</span><span class="sxs-lookup"><span data-stu-id="7e2da-276">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="7e2da-277">新增 dotnet 產品摘要。</span><span class="sxs-lookup"><span data-stu-id="7e2da-277">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="7e2da-278">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7e2da-278">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="7e2da-279">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-279">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e2da-280">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e2da-280">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="7e2da-281">取得必要條件。</span><span class="sxs-lookup"><span data-stu-id="7e2da-281">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="7e2da-282">下載 .NET Core SDK 二進位檔 (tarball)。</span><span class="sxs-lookup"><span data-stu-id="7e2da-282">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="7e2da-283">擷取 .NET Core SDK 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="7e2da-283">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="7e2da-284">將 dotnet 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="7e2da-284">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="7e2da-285">執行 `dotnet --version` 命令，以證明安裝成功。</span><span class="sxs-lookup"><span data-stu-id="7e2da-285">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="7e2da-286">如果支援的 Linux 發行版本/版本遇到 .NET Core 2.x 安裝問題，請參閱已安裝的發行版本/版本的 [2.0 已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。</span><span class="sxs-lookup"><span data-stu-id="7e2da-286">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="7e2da-287">如果支援的 Linux 發行版本/版本遇到 .NET Core 1.x 安裝問題，請參閱已安裝的發行版本/版本的 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。</span><span class="sxs-lookup"><span data-stu-id="7e2da-287">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
