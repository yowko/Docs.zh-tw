---
title: Linux 上 .NET Core 的必要條件
description: 支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: ad1ab42bcf66e32a45351ae2b6156251c9d0dc1f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849053"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="56faf-103">Linux 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="56faf-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="56faf-104">本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="56faf-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="56faf-105">支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="56faf-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="56faf-106">使用命令列搭配您偏好的編輯器</span><span class="sxs-lookup"><span data-stu-id="56faf-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="56faf-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="56faf-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="56faf-108">實際執行伺服器/生產環境不需要 .NET Core SDK 套件。</span><span class="sxs-lookup"><span data-stu-id="56faf-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="56faf-109">僅需要.NET Core 執行階段套件，即可將應用程式部署到生產環境。</span><span class="sxs-lookup"><span data-stu-id="56faf-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="56faf-110">.NET Core 執行階段將應用程式作為獨立部署的一部分進行部署，不過，針對架構相依的部署應用程式必須單獨加以部署。</span><span class="sxs-lookup"><span data-stu-id="56faf-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="56faf-111">如需架構相依部署類型和獨立部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](./deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="56faf-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="56faf-112">另請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)以了解特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="56faf-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="56faf-113">支援的 Linux 版本</span><span class="sxs-lookup"><span data-stu-id="56faf-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="56faf-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="56faf-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="56faf-115">.NET Core 2.x 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="56faf-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="56faf-116">針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。</span><span class="sxs-lookup"><span data-stu-id="56faf-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="56faf-117">如需下載連結和詳細資訊，請參閱 [.NET Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)或 [.NET Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="56faf-117">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="56faf-118">下列 Linux 發行版本/版本支援 .NET core 2.x：</span><span class="sxs-lookup"><span data-stu-id="56faf-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="56faf-119">Red Hat Enterprise Linux 7、6 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="56faf-120">CentOS 7 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="56faf-121">Oracle Linux 7 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="56faf-122">Fedora 28、27 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="56faf-123">Debian 9 (64 位元，`arm32`)、8.7 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="56faf-124">Ubuntu 18.04 (64 位元 `arm32`)、16.04、14.04 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="56faf-125">Linux Mint 18、17 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="56faf-126">openSUSE 42.3 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="56faf-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="56faf-128">Alpine Linux 3.7 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)</span><span class="sxs-lookup"><span data-stu-id="56faf-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="56faf-129">如需 .NET Core 2.1 和 .NET Core 2.2 支援的作業系統完整清單、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結，請參閱 [.NET Core 2.1 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)和 [.NET Core 2.2 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="56faf-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="56faf-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="56faf-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="56faf-131">如需下載連結和詳細資訊，請參閱 [.NET Core 1.1 下載](https://dotnet.microsoft.com/download/dotnet-core/1.1)或 [.NET Core 1.0 下載](https://dotnet.microsoft.com/download/dotnet-core/1.0)。</span><span class="sxs-lookup"><span data-stu-id="56faf-131">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="56faf-132">下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：</span><span class="sxs-lookup"><span data-stu-id="56faf-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="56faf-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="56faf-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="56faf-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="56faf-134">CentOS 7</span></span>
* <span data-ttu-id="56faf-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="56faf-135">Oracle Linux 7</span></span>
* <span data-ttu-id="56faf-136">Fedora 28 (.NET Core 1.1)、27</span><span class="sxs-lookup"><span data-stu-id="56faf-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="56faf-137">Debian 8.2 或更新的版本</span><span class="sxs-lookup"><span data-stu-id="56faf-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="56faf-138">Ubuntu 18.04 (.NET Core 1.1)、16.04、14.04</span><span class="sxs-lookup"><span data-stu-id="56faf-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="56faf-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="56faf-139">Linux Mint 17</span></span>
* <span data-ttu-id="56faf-140">openSUSE 42.3 或更新版本 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="56faf-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="56faf-141">如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="56faf-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="56faf-142">.NET Core 3.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="56faf-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="56faf-143">.NET Core 3.0 Preview 1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="56faf-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="56faf-144">針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。</span><span class="sxs-lookup"><span data-stu-id="56faf-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="56faf-145">如需下載連結和詳細資訊，請參閱 [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) (.NET Core 3.0 下載)。</span><span class="sxs-lookup"><span data-stu-id="56faf-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="56faf-146">下列 Linux 發行版本/版本支援 .NET Core 3.0 Preview 1。</span><span class="sxs-lookup"><span data-stu-id="56faf-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="56faf-147">作業系統</span><span class="sxs-lookup"><span data-stu-id="56faf-147">OS</span></span>                            | <span data-ttu-id="56faf-148">Version</span><span class="sxs-lookup"><span data-stu-id="56faf-148">Version</span></span>               | <span data-ttu-id="56faf-149">架構</span><span class="sxs-lookup"><span data-stu-id="56faf-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="56faf-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="56faf-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="56faf-151">6</span><span class="sxs-lookup"><span data-stu-id="56faf-151">6</span></span>                     | <span data-ttu-id="56faf-152">X64</span><span class="sxs-lookup"><span data-stu-id="56faf-152">x64</span></span>
<span data-ttu-id="56faf-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="56faf-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="56faf-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="56faf-154">CentOS</span></span><br><span data-ttu-id="56faf-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="56faf-155">Oracle Linux</span></span>  | <span data-ttu-id="56faf-156">7</span><span class="sxs-lookup"><span data-stu-id="56faf-156">7</span></span>                     | <span data-ttu-id="56faf-157">X64</span><span class="sxs-lookup"><span data-stu-id="56faf-157">x64</span></span>
<span data-ttu-id="56faf-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="56faf-158">Fedora</span></span>                        | <span data-ttu-id="56faf-159">28</span><span class="sxs-lookup"><span data-stu-id="56faf-159">28</span></span>                    | <span data-ttu-id="56faf-160">X64</span><span class="sxs-lookup"><span data-stu-id="56faf-160">x64</span></span>
<span data-ttu-id="56faf-161">Debian</span><span class="sxs-lookup"><span data-stu-id="56faf-161">Debian</span></span>                        | <span data-ttu-id="56faf-162">9</span><span class="sxs-lookup"><span data-stu-id="56faf-162">9</span></span>                     | <span data-ttu-id="56faf-163">x64、ARM32\*、ARM64\*</span><span class="sxs-lookup"><span data-stu-id="56faf-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="56faf-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56faf-164">Ubuntu</span></span>                        | <span data-ttu-id="56faf-165">16.04+、18.04+</span><span class="sxs-lookup"><span data-stu-id="56faf-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="56faf-166">x64、ARM32\*、ARM64\*</span><span class="sxs-lookup"><span data-stu-id="56faf-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="56faf-167">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="56faf-167">Linux Mint</span></span>                    | <span data-ttu-id="56faf-168">18</span><span class="sxs-lookup"><span data-stu-id="56faf-168">18</span></span>                    | <span data-ttu-id="56faf-169">X64</span><span class="sxs-lookup"><span data-stu-id="56faf-169">x64</span></span>
<span data-ttu-id="56faf-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="56faf-170">openSUSE</span></span>                      | <span data-ttu-id="56faf-171">42.3+</span><span class="sxs-lookup"><span data-stu-id="56faf-171">42.3+</span></span>                 | <span data-ttu-id="56faf-172">X64</span><span class="sxs-lookup"><span data-stu-id="56faf-172">x64</span></span>
<span data-ttu-id="56faf-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="56faf-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="56faf-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="56faf-174">12 SP2+</span></span>               | <span data-ttu-id="56faf-175">X64</span><span class="sxs-lookup"><span data-stu-id="56faf-175">x64</span></span>
<span data-ttu-id="56faf-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="56faf-176">Alpine Linux</span></span>                  | <span data-ttu-id="56faf-177">3.8+</span><span class="sxs-lookup"><span data-stu-id="56faf-177">3.8+</span></span>                  | <span data-ttu-id="56faf-178">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="56faf-178">x64, ARM64</span></span>

<span data-ttu-id="56faf-179">\* 從 Debian 9 和 Ubuntu 16.04 開始，支援 ARM32 和 ARM64。</span><span class="sxs-lookup"><span data-stu-id="56faf-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="56faf-180">ARM 晶片不支援這些發行版本的舊版。</span><span class="sxs-lookup"><span data-stu-id="56faf-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="56faf-181">如需 .NET Core 3.0 支援的作業系統、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結完整清單，請參閱 [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) (.NET Core 3.0 支援的 OS 版本)。</span><span class="sxs-lookup"><span data-stu-id="56faf-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="56faf-182">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="56faf-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="56faf-183">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="56faf-183">Linux distribution dependencies</span></span>

<span data-ttu-id="56faf-184">下列要作為範例。</span><span class="sxs-lookup"><span data-stu-id="56faf-184">The following are intended to be examples.</span></span> <span data-ttu-id="56faf-185">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="56faf-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="56faf-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56faf-186">Ubuntu</span></span>

<span data-ttu-id="56faf-187">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="56faf-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="56faf-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="56faf-188">liblttng-ust0</span></span>
* <span data-ttu-id="56faf-189">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="56faf-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="56faf-190">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="56faf-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="56faf-191">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="56faf-191">libssl1.0.0</span></span>
* <span data-ttu-id="56faf-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="56faf-192">libkrb5-3</span></span>
* <span data-ttu-id="56faf-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="56faf-193">zlib1g</span></span>
* <span data-ttu-id="56faf-194">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="56faf-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="56faf-195">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="56faf-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="56faf-196">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="56faf-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="56faf-197">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="56faf-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="56faf-198">針對 .NET Core 2.1 之前的版本，還需要下列的相依性：</span><span class="sxs-lookup"><span data-stu-id="56faf-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="56faf-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="56faf-199">libunwind8</span></span>
* <span data-ttu-id="56faf-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="56faf-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="56faf-201">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="56faf-201">CentOS and Fedora</span></span>

<span data-ttu-id="56faf-202">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="56faf-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="56faf-203">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="56faf-203">lttng-ust</span></span>
* <span data-ttu-id="56faf-204">libcurl</span><span class="sxs-lookup"><span data-stu-id="56faf-204">libcurl</span></span>
* <span data-ttu-id="56faf-205">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="56faf-205">openssl-libs</span></span>
* <span data-ttu-id="56faf-206">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="56faf-206">krb5-libs</span></span>
* <span data-ttu-id="56faf-207">libicu</span><span class="sxs-lookup"><span data-stu-id="56faf-207">libicu</span></span>
* <span data-ttu-id="56faf-208">zlib</span><span class="sxs-lookup"><span data-stu-id="56faf-208">zlib</span></span>

<span data-ttu-id="56faf-209">Fedora 使用者：如果您的 openssl 版本 >= 1.1，則必須安裝 compat-openssl10。</span><span class="sxs-lookup"><span data-stu-id="56faf-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="56faf-210">針對 .NET Core 2.1 之前的版本，還需要下列的相依性：</span><span class="sxs-lookup"><span data-stu-id="56faf-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="56faf-211">libunwind</span><span class="sxs-lookup"><span data-stu-id="56faf-211">libunwind</span></span>
* <span data-ttu-id="56faf-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="56faf-212">libuuid</span></span>

<span data-ttu-id="56faf-213">如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="56faf-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="56faf-214">使用原生安裝程式來安裝 .NET Core 相依性</span><span class="sxs-lookup"><span data-stu-id="56faf-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="56faf-215">受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="56faf-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="56faf-216">原生安裝程式需要伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="56faf-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="56faf-217">使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。</span><span class="sxs-lookup"><span data-stu-id="56faf-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="56faf-218">原生安裝程式也會安裝 .NET Core SDK 全系統。</span><span class="sxs-lookup"><span data-stu-id="56faf-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="56faf-219">Linux 上有兩個安裝程式套件選擇：</span><span class="sxs-lookup"><span data-stu-id="56faf-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="56faf-220">使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。</span><span class="sxs-lookup"><span data-stu-id="56faf-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="56faf-221">使用套件本身，DEB 或 RPM。</span><span class="sxs-lookup"><span data-stu-id="56faf-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="56faf-222">使用 .NET Core 安裝程式指令碼以指令碼進行安裝</span><span class="sxs-lookup"><span data-stu-id="56faf-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="56faf-223">[dotnet-install 指令碼](./tools/dotnet-install-script.md)用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。</span><span class="sxs-lookup"><span data-stu-id="56faf-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="56faf-224">您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="56faf-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="56faf-225">指令碼預設為安裝最新的 "LTS" 版本，也就是目前的 .NET Core 1.1。</span><span class="sxs-lookup"><span data-stu-id="56faf-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="56faf-226">若要安裝 .NET Core 2.1，請使用下列參數執行指令碼：</span><span class="sxs-lookup"><span data-stu-id="56faf-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="56faf-227">安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="56faf-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="56faf-228">此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="56faf-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="56faf-229">疑難排解</span><span class="sxs-lookup"><span data-stu-id="56faf-229">Troubleshoot</span></span>

<span data-ttu-id="56faf-230">如果您在支援的 Linux 發行版本/版本上安裝 .NET Core 的相關問題，請參閱已安裝之發行版本/版本的下列主題：</span><span class="sxs-lookup"><span data-stu-id="56faf-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="56faf-231">.NET Core 3.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="56faf-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="56faf-232">.NET Core 2.2 的已知問題</span><span class="sxs-lookup"><span data-stu-id="56faf-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="56faf-233">.NET Core 2.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="56faf-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="56faf-234">.NET Core 1.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="56faf-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="56faf-235">.NET Core 1.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="56faf-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
