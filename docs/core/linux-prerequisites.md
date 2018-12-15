---
title: Linux 上 .NET Core 的必要條件
description: 支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.date: 12/03/2018
ms.openlocfilehash: e250158d10c6a03535f4e693e74954747f860a3c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148319"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="0d3e0-103">Linux 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="0d3e0-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="0d3e0-104">本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="0d3e0-105">支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="0d3e0-106">使用命令列搭配您偏好的編輯器</span><span class="sxs-lookup"><span data-stu-id="0d3e0-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="0d3e0-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0d3e0-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="0d3e0-108">實際執行伺服器/生產環境不需要 .NET Core SDK 套件。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="0d3e0-109">僅需要.NET Core 執行階段套件，即可將應用程式部署到生產環境。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="0d3e0-110">.NET Core 執行階段將應用程式作為獨立部署的一部分進行部署，不過，針對架構相依的部署應用程式必須單獨加以部署。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="0d3e0-111">如需架構相依部署類型和獨立部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](./deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="0d3e0-112">另請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)以了解特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="0d3e0-113">支援的 Linux 版本</span><span class="sxs-lookup"><span data-stu-id="0d3e0-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0d3e0-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0d3e0-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="0d3e0-115">.NET Core 2.x 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="0d3e0-116">針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="0d3e0-117">如需下載連結和詳細資訊，請參閱 [.NET Core 2.2 下載](https://www.microsoft.com/net/download/dotnet-core/2.2)或 [.NET Core 2.1 下載](https://www.microsoft.com/net/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="0d3e0-118">下列 Linux 發行版本/版本支援 .NET core 2.x：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="0d3e0-119">Red Hat Enterprise Linux 7、6 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="0d3e0-120">CentOS 7 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="0d3e0-121">Oracle Linux 7 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="0d3e0-122">Fedora 28、27 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="0d3e0-123">Debian 9 (64 位元，`arm32`)、8.7 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="0d3e0-124">Ubuntu 18.04 (64 位元 `arm32`)、16.04、14.04 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="0d3e0-125">Linux Mint 18、17 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="0d3e0-126">openSUSE 42.3 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="0d3e0-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="0d3e0-128">Alpine Linux 3.7 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="0d3e0-129">如需 .NET Core 2.1 和 .NET Core 2.2 支援的作業系統完整清單、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結，請參閱 [.NET Core 2.1 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)和 [.NET Core 2.2 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0d3e0-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0d3e0-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0d3e0-131">如需下載連結和詳細資訊，請參閱 [.NET Core 1.1 下載](https://www.microsoft.com/net/download/dotnet-core/1.1)或 [.NET Core 1.0 下載](https://www.microsoft.com/net/download/dotnet-core/1.0)。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="0d3e0-132">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="0d3e0-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="0d3e0-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="0d3e0-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0d3e0-134">CentOS 7</span></span>
* <span data-ttu-id="0d3e0-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="0d3e0-135">Oracle Linux 7</span></span>
* <span data-ttu-id="0d3e0-136">Fedora 28 (.NET Core 1.1)、27</span><span class="sxs-lookup"><span data-stu-id="0d3e0-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="0d3e0-137">Debian 8.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="0d3e0-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="0d3e0-138">Ubuntu 18.04 (.NET Core 1.1)、16.04、14.04</span><span class="sxs-lookup"><span data-stu-id="0d3e0-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="0d3e0-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="0d3e0-139">Linux Mint 17</span></span>
* <span data-ttu-id="0d3e0-140">openSUSE 42.3 或更新版本 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="0d3e0-141">如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="0d3e0-142">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="0d3e0-142">Linux distribution dependencies</span></span>

<span data-ttu-id="0d3e0-143">下列要作為範例。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-143">The following are intended to be examples.</span></span> <span data-ttu-id="0d3e0-144">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-144">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="0d3e0-145">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0d3e0-145">Ubuntu</span></span>

<span data-ttu-id="0d3e0-146">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-146">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="0d3e0-147">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="0d3e0-147">liblttng-ust0</span></span>
* <span data-ttu-id="0d3e0-148">libcurl3</span><span class="sxs-lookup"><span data-stu-id="0d3e0-148">libcurl3</span></span>
* <span data-ttu-id="0d3e0-149">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="0d3e0-149">libssl1.0.0</span></span>
* <span data-ttu-id="0d3e0-150">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="0d3e0-150">libkrb5-3</span></span>
* <span data-ttu-id="0d3e0-151">zlib1g</span><span class="sxs-lookup"><span data-stu-id="0d3e0-151">zlib1g</span></span>
* <span data-ttu-id="0d3e0-152">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-152">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="0d3e0-153">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-153">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="0d3e0-154">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-154">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="0d3e0-155">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="0d3e0-155">libicu60 (for 18.x)</span></span>

<span data-ttu-id="0d3e0-156">針對 .NET Core 2.1 之前的版本，還需要下列的相依性：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-156">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="0d3e0-157">libunwind8</span><span class="sxs-lookup"><span data-stu-id="0d3e0-157">libunwind8</span></span>
* <span data-ttu-id="0d3e0-158">libuuid1</span><span class="sxs-lookup"><span data-stu-id="0d3e0-158">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="0d3e0-159">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="0d3e0-159">CentOS and Fedora</span></span>

<span data-ttu-id="0d3e0-160">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-160">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="0d3e0-161">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="0d3e0-161">lttng-ust</span></span>
* <span data-ttu-id="0d3e0-162">libcurl</span><span class="sxs-lookup"><span data-stu-id="0d3e0-162">libcurl</span></span>
* <span data-ttu-id="0d3e0-163">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="0d3e0-163">openssl-libs</span></span>
* <span data-ttu-id="0d3e0-164">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="0d3e0-164">krb5-libs</span></span>
* <span data-ttu-id="0d3e0-165">libicu</span><span class="sxs-lookup"><span data-stu-id="0d3e0-165">libicu</span></span>
* <span data-ttu-id="0d3e0-166">zlib</span><span class="sxs-lookup"><span data-stu-id="0d3e0-166">zlib</span></span>

<span data-ttu-id="0d3e0-167">Fedora 使用者：如果您的 openssl 版本 >= 1.1，則必須安裝 compat-openssl10。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-167">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="0d3e0-168">針對 .NET Core 2.1 之前的版本，還需要下列的相依性：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-168">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="0d3e0-169">libunwind</span><span class="sxs-lookup"><span data-stu-id="0d3e0-169">libunwind</span></span>
* <span data-ttu-id="0d3e0-170">libuuid</span><span class="sxs-lookup"><span data-stu-id="0d3e0-170">libuuid</span></span>

<span data-ttu-id="0d3e0-171">如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-171">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="0d3e0-172">使用原生安裝程式來安裝 .NET Core 相依性</span><span class="sxs-lookup"><span data-stu-id="0d3e0-172">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="0d3e0-173">受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-173">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="0d3e0-174">原生安裝程式需要伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-174">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="0d3e0-175">使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-175">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="0d3e0-176">原生安裝程式也會安裝 .NET Core SDK 全系統。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-176">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="0d3e0-177">Linux 上有兩個安裝程式套件選擇：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-177">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="0d3e0-178">使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-178">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="0d3e0-179">使用套件本身，DEB 或 RPM。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-179">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="0d3e0-180">使用 .NET Core 安裝程式指令碼以指令碼進行安裝</span><span class="sxs-lookup"><span data-stu-id="0d3e0-180">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="0d3e0-181">[dotnet-install 指令碼](./tools/dotnet-install-script.md)用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-181">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="0d3e0-182">您可以從 [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh) 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-182">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="0d3e0-183">指令碼預設為安裝最新的 "LTS" 版本，也就是目前的 .NET Core 1.1。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-183">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="0d3e0-184">若要安裝 .NET Core 2.1，請使用下列參數執行指令碼：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-184">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="0d3e0-185">安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-185">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="0d3e0-186">此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="0d3e0-186">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="0d3e0-187">疑難排解</span><span class="sxs-lookup"><span data-stu-id="0d3e0-187">Troubleshoot</span></span>

<span data-ttu-id="0d3e0-188">如果您在支援的 Linux 發行版本/版本上安裝 .NET Core 的相關問題，請參閱已安裝之發行版本/版本的下列主題：</span><span class="sxs-lookup"><span data-stu-id="0d3e0-188">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="0d3e0-189">.NET Core 3.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="0d3e0-189">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="0d3e0-190">.NET Core 2.2 的已知問題</span><span class="sxs-lookup"><span data-stu-id="0d3e0-190">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="0d3e0-191">.NET Core 2.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="0d3e0-191">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="0d3e0-192">.NET Core 1.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="0d3e0-192">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="0d3e0-193">.NET Core 1.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="0d3e0-193">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
