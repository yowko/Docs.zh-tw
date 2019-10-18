---
title: Linux 上 .NET Core 的必要條件
description: 支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。
author: leecow
ms.author: leecow
ms.date: 10/11/2019
ms.openlocfilehash: 0e798e86fcf88a1b7a67f50c2301e10ad725fad8
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521483"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="e9f0f-103">Linux 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="e9f0f-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="e9f0f-104">本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="e9f0f-105">支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

- [<span data-ttu-id="e9f0f-106">使用命令列搭配您偏好的編輯器</span><span class="sxs-lookup"><span data-stu-id="e9f0f-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
- [<span data-ttu-id="e9f0f-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e9f0f-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="e9f0f-108">實際執行伺服器/生產環境不需要 .NET Core SDK 套件。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="e9f0f-109">僅需要.NET Core 執行階段套件，即可將應用程式部署到生產環境。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="e9f0f-110">.NET Core 執行階段將應用程式作為獨立部署的一部分進行部署，不過，針對架構相依的部署應用程式必須單獨加以部署。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="e9f0f-111">如需架構相依部署類型和獨立部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](./deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="e9f0f-112">另請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)以了解特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="e9f0f-113">支援的 Linux 版本</span><span class="sxs-lookup"><span data-stu-id="e9f0f-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="e9f0f-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e9f0f-114">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="e9f0f-115">.NET Core 3.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-115">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="e9f0f-116">針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="e9f0f-117">如需下載連結和詳細資訊，請參閱 [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) (.NET Core 3.0 下載)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-117">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="e9f0f-118">下列 Linux 發行版本/版本支援 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-118">.NET Core 3.0 is supported on the following Linux distributions/versions):</span></span>

> [!NOTE]
> <span data-ttu-id="e9f0f-119">@No__t_0 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-119">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e9f0f-120">OS</span><span class="sxs-lookup"><span data-stu-id="e9f0f-120">OS</span></span>                             | <span data-ttu-id="e9f0f-121">版本</span><span class="sxs-lookup"><span data-stu-id="e9f0f-121">Version</span></span>               | <span data-ttu-id="e9f0f-122">架構</span><span class="sxs-lookup"><span data-stu-id="e9f0f-122">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="e9f0f-123">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-123">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="e9f0f-124">6 +、7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-124">6+, 7</span></span>                 | <span data-ttu-id="e9f0f-125">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-125">x64</span></span> |
| <span data-ttu-id="e9f0f-126">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-126">Oracle Linux</span></span>                   | <span data-ttu-id="e9f0f-127">7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-127">7</span></span>                     | <span data-ttu-id="e9f0f-128">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-128">x64</span></span> |
| <span data-ttu-id="e9f0f-129">CentOS</span><span class="sxs-lookup"><span data-stu-id="e9f0f-129">CentOS</span></span>                         | <span data-ttu-id="e9f0f-130">7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-130">7</span></span>                     | <span data-ttu-id="e9f0f-131">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-131">x64</span></span> |
| <span data-ttu-id="e9f0f-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="e9f0f-132">Fedora</span></span>                         | <span data-ttu-id="e9f0f-133">29 +</span><span class="sxs-lookup"><span data-stu-id="e9f0f-133">29+</span></span>                   | <span data-ttu-id="e9f0f-134">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-134">x64</span></span> |
| <span data-ttu-id="e9f0f-135">Debian</span><span class="sxs-lookup"><span data-stu-id="e9f0f-135">Debian</span></span>                         | <span data-ttu-id="e9f0f-136">9+</span><span class="sxs-lookup"><span data-stu-id="e9f0f-136">9+</span></span>                    | <span data-ttu-id="e9f0f-137">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-137">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e9f0f-138">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e9f0f-138">Ubuntu</span></span>                         | <span data-ttu-id="e9f0f-139">16.04+</span><span class="sxs-lookup"><span data-stu-id="e9f0f-139">16.04+</span></span>                | <span data-ttu-id="e9f0f-140">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-140">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e9f0f-141">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e9f0f-141">Linux Mint</span></span>                     | <span data-ttu-id="e9f0f-142">18 +</span><span class="sxs-lookup"><span data-stu-id="e9f0f-142">18+</span></span>                   | <span data-ttu-id="e9f0f-143">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-143">x64</span></span> |
| <span data-ttu-id="e9f0f-144">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e9f0f-144">openSUSE</span></span>                       | <span data-ttu-id="e9f0f-145">15 +</span><span class="sxs-lookup"><span data-stu-id="e9f0f-145">15+</span></span>                   | <span data-ttu-id="e9f0f-146">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-146">x64</span></span> |
| <span data-ttu-id="e9f0f-147">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-147">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="e9f0f-148">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e9f0f-148">12 SP2+</span></span>               | <span data-ttu-id="e9f0f-149">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-149">x64</span></span> |
| <span data-ttu-id="e9f0f-150">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-150">Alpine Linux</span></span>                   | <span data-ttu-id="e9f0f-151">3.8+</span><span class="sxs-lookup"><span data-stu-id="e9f0f-151">3.8+</span></span>                  | <span data-ttu-id="e9f0f-152">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-152">x64, ARM64</span></span> |

<span data-ttu-id="e9f0f-153">如需 .NET Core 3.0 支援的作業系統、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結完整清單，請參閱 [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) (.NET Core 3.0 支援的 OS 版本)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-153">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="e9f0f-154">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-154">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="e9f0f-155">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="e9f0f-155">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="e9f0f-156">.NET Core 2.2 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-156">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="e9f0f-157">針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-157">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e9f0f-158">如需下載連結和詳細資訊，請參閱[.Net Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-158">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2).</span></span>

<span data-ttu-id="e9f0f-159">下列 Linux 發行版本/版本支援 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-159">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e9f0f-160">@No__t_0 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-160">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e9f0f-161">OS</span><span class="sxs-lookup"><span data-stu-id="e9f0f-161">OS</span></span>                             |  <span data-ttu-id="e9f0f-162">版本</span><span class="sxs-lookup"><span data-stu-id="e9f0f-162">Version</span></span>                |  <span data-ttu-id="e9f0f-163">架構</span><span class="sxs-lookup"><span data-stu-id="e9f0f-163">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="e9f0f-164">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-164">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="e9f0f-165">6、7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-165">6, 7</span></span>                   | <span data-ttu-id="e9f0f-166">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-166">x64</span></span> |
| <span data-ttu-id="e9f0f-167">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-167">Oracle Linux</span></span>                   |  <span data-ttu-id="e9f0f-168">7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-168">7</span></span>                      | <span data-ttu-id="e9f0f-169">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-169">x64</span></span> |
| <span data-ttu-id="e9f0f-170">CentOS</span><span class="sxs-lookup"><span data-stu-id="e9f0f-170">CentOS</span></span>                         |  <span data-ttu-id="e9f0f-171">7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-171">7</span></span>                      | <span data-ttu-id="e9f0f-172">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-172">x64</span></span> |
| <span data-ttu-id="e9f0f-173">Fedora</span><span class="sxs-lookup"><span data-stu-id="e9f0f-173">Fedora</span></span>                         |  <span data-ttu-id="e9f0f-174">29、30</span><span class="sxs-lookup"><span data-stu-id="e9f0f-174">29, 30</span></span>                 | <span data-ttu-id="e9f0f-175">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-175">x64</span></span> |
| <span data-ttu-id="e9f0f-176">Debian</span><span class="sxs-lookup"><span data-stu-id="e9f0f-176">Debian</span></span>                         |  <span data-ttu-id="e9f0f-177">9</span><span class="sxs-lookup"><span data-stu-id="e9f0f-177">9</span></span>                      | <span data-ttu-id="e9f0f-178">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e9f0f-178">x64, ARM32</span></span> |
| <span data-ttu-id="e9f0f-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e9f0f-179">Ubuntu</span></span>                         |  <span data-ttu-id="e9f0f-180">16.04、18.04、18.10</span><span class="sxs-lookup"><span data-stu-id="e9f0f-180">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="e9f0f-181">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e9f0f-181">x64, ARM32</span></span> |
| <span data-ttu-id="e9f0f-182">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e9f0f-182">Linux Mint</span></span>                     |  <span data-ttu-id="e9f0f-183">17、18</span><span class="sxs-lookup"><span data-stu-id="e9f0f-183">17, 18</span></span>                 | <span data-ttu-id="e9f0f-184">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-184">x64</span></span> |
| <span data-ttu-id="e9f0f-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e9f0f-185">openSUSE</span></span>                       |  <span data-ttu-id="e9f0f-186">15 +</span><span class="sxs-lookup"><span data-stu-id="e9f0f-186">15+</span></span>                    | <span data-ttu-id="e9f0f-187">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-187">x64</span></span> |
| <span data-ttu-id="e9f0f-188">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-188">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="e9f0f-189">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e9f0f-189">12 SP2+</span></span>                | <span data-ttu-id="e9f0f-190">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-190">x64</span></span> |
| <span data-ttu-id="e9f0f-191">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-191">Alpine Linux</span></span>                   |  <span data-ttu-id="e9f0f-192">3.7 +</span><span class="sxs-lookup"><span data-stu-id="e9f0f-192">3.7+</span></span>                   | <span data-ttu-id="e9f0f-193">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-193">x64</span></span> |

<span data-ttu-id="e9f0f-194">如需 .NET Core 2.2 支援的作業系統完整清單、發行版本與版本、不支援的作業系統版本，以及生命週期原則連結，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-194">See [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e9f0f-195">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e9f0f-195">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="e9f0f-196">.NET Core 2.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-196">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="e9f0f-197">針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-197">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e9f0f-198">如需下載連結和詳細資訊，請參閱[.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-198">For download links and more information, see [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="e9f0f-199">下列 Linux 發行版本/版本支援 .NET Core 2.1：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-199">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

| <span data-ttu-id="e9f0f-200">OS</span><span class="sxs-lookup"><span data-stu-id="e9f0f-200">OS</span></span>                             |  <span data-ttu-id="e9f0f-201">版本</span><span class="sxs-lookup"><span data-stu-id="e9f0f-201">Version</span></span>                |  <span data-ttu-id="e9f0f-202">架構</span><span class="sxs-lookup"><span data-stu-id="e9f0f-202">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="e9f0f-203">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-203">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="e9f0f-204">6、7、8</span><span class="sxs-lookup"><span data-stu-id="e9f0f-204">6, 7, 8</span></span>                | <span data-ttu-id="e9f0f-205">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-205">x64</span></span> |
| <span data-ttu-id="e9f0f-206">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-206">Oracle Linux</span></span>                   |  <span data-ttu-id="e9f0f-207">7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-207">7</span></span>                      | <span data-ttu-id="e9f0f-208">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-208">x64</span></span> |
| <span data-ttu-id="e9f0f-209">CentOS</span><span class="sxs-lookup"><span data-stu-id="e9f0f-209">CentOS</span></span>                         |  <span data-ttu-id="e9f0f-210">7</span><span class="sxs-lookup"><span data-stu-id="e9f0f-210">7</span></span>                      | <span data-ttu-id="e9f0f-211">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-211">x64</span></span> |
| <span data-ttu-id="e9f0f-212">Fedora</span><span class="sxs-lookup"><span data-stu-id="e9f0f-212">Fedora</span></span>                         |  <span data-ttu-id="e9f0f-213">29、30</span><span class="sxs-lookup"><span data-stu-id="e9f0f-213">29, 30</span></span>                 | <span data-ttu-id="e9f0f-214">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-214">x64</span></span> |
| <span data-ttu-id="e9f0f-215">Debian</span><span class="sxs-lookup"><span data-stu-id="e9f0f-215">Debian</span></span>                         |  <span data-ttu-id="e9f0f-216">9</span><span class="sxs-lookup"><span data-stu-id="e9f0f-216">9</span></span>                      | <span data-ttu-id="e9f0f-217">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e9f0f-217">x64, ARM32</span></span> |
| <span data-ttu-id="e9f0f-218">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e9f0f-218">Ubuntu</span></span>                         |  <span data-ttu-id="e9f0f-219">16.04、18.04、19.04</span><span class="sxs-lookup"><span data-stu-id="e9f0f-219">16.04, 18.04, 19.04</span></span>    | <span data-ttu-id="e9f0f-220">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e9f0f-220">x64, ARM32</span></span> |
| <span data-ttu-id="e9f0f-221">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e9f0f-221">Linux Mint</span></span>                     |  <span data-ttu-id="e9f0f-222">17、18</span><span class="sxs-lookup"><span data-stu-id="e9f0f-222">17, 18</span></span>                 | <span data-ttu-id="e9f0f-223">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-223">x64</span></span> |
| <span data-ttu-id="e9f0f-224">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e9f0f-224">openSUSE</span></span>                       |  <span data-ttu-id="e9f0f-225">42.3+</span><span class="sxs-lookup"><span data-stu-id="e9f0f-225">42.3+</span></span>                  | <span data-ttu-id="e9f0f-226">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-226">x64</span></span> |
| <span data-ttu-id="e9f0f-227">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-227">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="e9f0f-228">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e9f0f-228">12 SP2+</span></span>                | <span data-ttu-id="e9f0f-229">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-229">x64</span></span> |
| <span data-ttu-id="e9f0f-230">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e9f0f-230">Alpine Linux</span></span>                   |  <span data-ttu-id="e9f0f-231">3.7 +</span><span class="sxs-lookup"><span data-stu-id="e9f0f-231">3.7+</span></span>                   | <span data-ttu-id="e9f0f-232">X64</span><span class="sxs-lookup"><span data-stu-id="e9f0f-232">x64</span></span> |

<span data-ttu-id="e9f0f-233">如需 .NET Core 2.1 支援的作業系統完整清單、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結，請參閱 [.NET Core 2.1 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-233">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="e9f0f-234">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="e9f0f-234">Linux distribution dependencies</span></span>

<span data-ttu-id="e9f0f-235">下列要作為範例。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-235">The following are intended to be examples.</span></span> <span data-ttu-id="e9f0f-236">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-236">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="e9f0f-237">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e9f0f-237">Ubuntu</span></span>

<span data-ttu-id="e9f0f-238">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-238">Ubuntu distributions require the following libraries installed:</span></span>

- <span data-ttu-id="e9f0f-239">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="e9f0f-239">liblttng-ust0</span></span>
- <span data-ttu-id="e9f0f-240">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-240">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="e9f0f-241">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-241">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="e9f0f-242">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="e9f0f-242">libssl1.0.0</span></span>
- <span data-ttu-id="e9f0f-243">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="e9f0f-243">libkrb5-3</span></span>
- <span data-ttu-id="e9f0f-244">zlib1g</span><span class="sxs-lookup"><span data-stu-id="e9f0f-244">zlib1g</span></span>
- <span data-ttu-id="e9f0f-245">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-245">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="e9f0f-246">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-246">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="e9f0f-247">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-247">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="e9f0f-248">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="e9f0f-248">libicu60 (for 18.x)</span></span>

<span data-ttu-id="e9f0f-249">針對 .NET Core 2.1 之前的版本，還需要下列的相依性：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-249">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

- <span data-ttu-id="e9f0f-250">libunwind8</span><span class="sxs-lookup"><span data-stu-id="e9f0f-250">libunwind8</span></span>
- <span data-ttu-id="e9f0f-251">libuuid1</span><span class="sxs-lookup"><span data-stu-id="e9f0f-251">libuuid1</span></span>

<span data-ttu-id="e9f0f-252">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-252">For .NET Core applications that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

* <span data-ttu-id="e9f0f-253">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="e9f0f-253">libgdiplus (version 6.0.1 or later)</span></span>

> [!NOTE]
> <span data-ttu-id="e9f0f-254">最新版的 Ubuntu 包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-254">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="e9f0f-255">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-255">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="e9f0f-256">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-256">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="e9f0f-257">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="e9f0f-257">CentOS and Fedora</span></span>

<span data-ttu-id="e9f0f-258">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-258">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="e9f0f-259">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="e9f0f-259">lttng-ust</span></span>
- <span data-ttu-id="e9f0f-260">libcurl</span><span class="sxs-lookup"><span data-stu-id="e9f0f-260">libcurl</span></span>
- <span data-ttu-id="e9f0f-261">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="e9f0f-261">openssl-libs</span></span>
- <span data-ttu-id="e9f0f-262">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="e9f0f-262">krb5-libs</span></span>
- <span data-ttu-id="e9f0f-263">libicu</span><span class="sxs-lookup"><span data-stu-id="e9f0f-263">libicu</span></span>
- <span data-ttu-id="e9f0f-264">zlib</span><span class="sxs-lookup"><span data-stu-id="e9f0f-264">zlib</span></span>

<span data-ttu-id="e9f0f-265">Fedora 使用者：如果您的 openssl 版本 >= 1.1，則必須安裝 compat-openssl10。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-265">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="e9f0f-266">針對 .NET Core 2.1 之前的版本，還需要下列的相依性：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-266">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

- <span data-ttu-id="e9f0f-267">libunwind</span><span class="sxs-lookup"><span data-stu-id="e9f0f-267">libunwind</span></span>
- <span data-ttu-id="e9f0f-268">libuuid</span><span class="sxs-lookup"><span data-stu-id="e9f0f-268">libuuid</span></span>

<span data-ttu-id="e9f0f-269">如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-269">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="e9f0f-270">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-270">For .NET Core applications that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

* <span data-ttu-id="e9f0f-271">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="e9f0f-271">libgdiplus (version 6.0.1 or later)</span></span>

> [!NOTE]
> <span data-ttu-id="e9f0f-272">大部分的 CentOS 和 Fedora 版本都包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-272">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="e9f0f-273">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-273">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="e9f0f-274">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-274">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="e9f0f-275">使用原生安裝程式來安裝 .NET Core 相依性</span><span class="sxs-lookup"><span data-stu-id="e9f0f-275">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="e9f0f-276">受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-276">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="e9f0f-277">原生安裝程式需要伺服器的管理員 (sudo) 存取權。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-277">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="e9f0f-278">使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-278">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="e9f0f-279">原生安裝程式也會安裝 .NET Core SDK 全系統。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-279">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="e9f0f-280">Linux 上有兩個安裝程式套件選擇：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-280">On Linux, there are two installer package choices:</span></span>

- <span data-ttu-id="e9f0f-281">使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-281">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
- <span data-ttu-id="e9f0f-282">使用套件本身，DEB 或 RPM。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-282">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="e9f0f-283">使用 .NET Core 安裝程式指令碼以指令碼進行安裝</span><span class="sxs-lookup"><span data-stu-id="e9f0f-283">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="e9f0f-284">[dotnet-install 指令碼](./tools/dotnet-install-script.md)用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-284">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="e9f0f-285">您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-285">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="e9f0f-286">指令碼預設為安裝最新的 "LTS" 版本，也就是目前的 .NET Core 1.1。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-286">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="e9f0f-287">若要安裝 .NET Core 2.1，請使用下列參數執行指令碼：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-287">To install .NET Core 2.1, run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="e9f0f-288">安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-288">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="e9f0f-289">此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="e9f0f-289">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="e9f0f-290">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e9f0f-290">Troubleshoot</span></span>

<span data-ttu-id="e9f0f-291">如果您在支援的 Linux 發行版本/版本上安裝 .NET Core 的相關問題，請參閱已安裝之發行版本/版本的下列主題：</span><span class="sxs-lookup"><span data-stu-id="e9f0f-291">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

- [<span data-ttu-id="e9f0f-292">.NET Core 3.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="e9f0f-292">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
- [<span data-ttu-id="e9f0f-293">.NET Core 2.2 的已知問題</span><span class="sxs-lookup"><span data-stu-id="e9f0f-293">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
- [<span data-ttu-id="e9f0f-294">.NET Core 2.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="e9f0f-294">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
- [<span data-ttu-id="e9f0f-295">.NET Core 1.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="e9f0f-295">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
- [<span data-ttu-id="e9f0f-296">.NET Core 1.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="e9f0f-296">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
