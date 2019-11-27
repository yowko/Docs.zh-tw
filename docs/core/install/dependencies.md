---
title: .NET Core SDK 和執行時間相依性-.NET Core
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET Core SDK 和執行時間的作業系統和 CPU 架構必要條件。
author: leecow
ms.author: leecow
ms.date: 11/06/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: b79ec6a9723cbd44717d5f187213278556c0b6ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451098"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="e69e4-103">.NET Core 相依性和需求</span><span class="sxs-lookup"><span data-stu-id="e69e4-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="e69e4-104">本文詳細說明 .NET Core 支援哪些作業系統和 CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="e69e4-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="e69e4-105">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="e69e4-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="e69e4-106">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e69e4-106">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="e69e4-107">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="e69e4-107">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="e69e4-108">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e69e4-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e69e4-109">OS</span><span class="sxs-lookup"><span data-stu-id="e69e4-109">OS</span></span>                            | <span data-ttu-id="e69e4-110">版本</span><span class="sxs-lookup"><span data-stu-id="e69e4-110">Version</span></span>                        | <span data-ttu-id="e69e4-111">架構</span><span class="sxs-lookup"><span data-stu-id="e69e4-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="e69e4-112">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="e69e4-112">Windows Client</span></span>                | <span data-ttu-id="e69e4-113">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="e69e4-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="e69e4-114">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-114">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-115">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="e69e4-115">Windows 10 Client</span></span>             | <span data-ttu-id="e69e4-116">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-116">Version 1607+</span></span>                  | <span data-ttu-id="e69e4-117">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-117">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="e69e4-118">Windows Server</span></span>                | <span data-ttu-id="e69e4-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-119">2012 R2+</span></span>                       | <span data-ttu-id="e69e4-120">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-120">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-121">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="e69e4-121">Nano Server</span></span>                   | <span data-ttu-id="e69e4-122">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-122">Version 1803+</span></span>                  | <span data-ttu-id="e69e4-123">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e69e4-123">x64, ARM32</span></span>      |

<span data-ttu-id="e69e4-124">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-124">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="e69e4-125">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="e69e4-125">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="e69e4-126">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="e69e4-126">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="e69e4-127">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e69e4-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e69e4-128">OS</span><span class="sxs-lookup"><span data-stu-id="e69e4-128">OS</span></span>                            | <span data-ttu-id="e69e4-129">版本</span><span class="sxs-lookup"><span data-stu-id="e69e4-129">Version</span></span>                        | <span data-ttu-id="e69e4-130">架構</span><span class="sxs-lookup"><span data-stu-id="e69e4-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="e69e4-131">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="e69e4-131">Windows Client</span></span>                | <span data-ttu-id="e69e4-132">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="e69e4-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="e69e4-133">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-133">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-134">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="e69e4-134">Windows 10 Client</span></span>             | <span data-ttu-id="e69e4-135">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-135">Version 1607+</span></span>                  | <span data-ttu-id="e69e4-136">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-136">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="e69e4-137">Windows Server</span></span>                | <span data-ttu-id="e69e4-138">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-138">2008 R2 SP1+</span></span>                   | <span data-ttu-id="e69e4-139">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-139">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-140">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="e69e4-140">Nano Server</span></span>                   | <span data-ttu-id="e69e4-141">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-141">Version 1803+</span></span>                   | <span data-ttu-id="e69e4-142">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e69e4-142">x64, ARM32</span></span>      |

<span data-ttu-id="e69e4-143">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-143">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e69e4-144">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e69e4-144">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="e69e4-145">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="e69e4-145">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="e69e4-146">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e69e4-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e69e4-147">OS</span><span class="sxs-lookup"><span data-stu-id="e69e4-147">OS</span></span>                            | <span data-ttu-id="e69e4-148">版本</span><span class="sxs-lookup"><span data-stu-id="e69e4-148">Version</span></span>                        | <span data-ttu-id="e69e4-149">架構</span><span class="sxs-lookup"><span data-stu-id="e69e4-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="e69e4-150">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="e69e4-150">Windows Client</span></span>                | <span data-ttu-id="e69e4-151">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="e69e4-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="e69e4-152">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-152">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-153">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="e69e4-153">Windows 10 Client</span></span>             | <span data-ttu-id="e69e4-154">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-154">Version 1607+</span></span>                  | <span data-ttu-id="e69e4-155">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-155">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="e69e4-156">Windows Server</span></span>                | <span data-ttu-id="e69e4-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="e69e4-158">x64、x86</span><span class="sxs-lookup"><span data-stu-id="e69e4-158">x64, x86</span></span>        |
| <span data-ttu-id="e69e4-159">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="e69e4-159">Nano Server</span></span>                   | <span data-ttu-id="e69e4-160">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-160">Version 1803+</span></span>                  | <span data-ttu-id="e69e4-161">x64</span><span class="sxs-lookup"><span data-stu-id="e69e4-161">x64,</span></span>            |

<span data-ttu-id="e69e4-162">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-162">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="e69e4-163">Windows 7/Vista/8.1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="e69e4-163">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="e69e4-164">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：</span><span class="sxs-lookup"><span data-stu-id="e69e4-164">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="e69e4-165">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="e69e4-165">Windows 7 SP1</span></span>
- <span data-ttu-id="e69e4-166">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="e69e4-166">Windows Vista SP 2</span></span>
- <span data-ttu-id="e69e4-167">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e69e4-167">Windows 8.1</span></span>
- <span data-ttu-id="e69e4-168">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="e69e4-168">Windows Server 2008 R2</span></span>
- <span data-ttu-id="e69e4-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e69e4-169">Windows Server 2012 R2</span></span>

<span data-ttu-id="e69e4-170">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="e69e4-170">Install the following:</span></span>

- <span data-ttu-id="e69e4-171">[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件 Update 3。</span><span class="sxs-lookup"><span data-stu-id="e69e4-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="e69e4-172">KB2533623</span><span class="sxs-lookup"><span data-stu-id="e69e4-172">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="e69e4-173">如果您遇到下列其中一個錯誤，也需要上述需求：</span><span class="sxs-lookup"><span data-stu-id="e69e4-173">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="e69e4-174">程式無法啟動，因為您的電腦遺失了*4.9.0-api* --win---------l1-1。</span><span class="sxs-lookup"><span data-stu-id="e69e4-174">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="e69e4-175">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="e69e4-175">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="e69e4-176">\-或-</span><span class="sxs-lookup"><span data-stu-id="e69e4-176">\- or -</span></span>
>
> <span data-ttu-id="e69e4-177">找到*程式庫用 hostfxr* ，但從*C：\\\<path_to_app >\\用 hostfxr*載入它失敗。</span><span class="sxs-lookup"><span data-stu-id="e69e4-177">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="e69e4-178">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e69e4-178">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="e69e4-179">.NET Core 3.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="e69e4-179">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="e69e4-180">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="e69e4-180">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e69e4-181">下列 Linux 發行版本/版本支援 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="e69e4-181">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e69e4-182">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e69e4-182">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e69e4-183">OS</span><span class="sxs-lookup"><span data-stu-id="e69e4-183">OS</span></span>                             | <span data-ttu-id="e69e4-184">版本</span><span class="sxs-lookup"><span data-stu-id="e69e4-184">Version</span></span>               | <span data-ttu-id="e69e4-185">架構</span><span class="sxs-lookup"><span data-stu-id="e69e4-185">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="e69e4-186">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-186">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="e69e4-187">6、7、8</span><span class="sxs-lookup"><span data-stu-id="e69e4-187">6, 7, 8</span></span>               | <span data-ttu-id="e69e4-188">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-188">x64</span></span> |
| <span data-ttu-id="e69e4-189">CentOS</span><span class="sxs-lookup"><span data-stu-id="e69e4-189">CentOS</span></span>                         | <span data-ttu-id="e69e4-190">7 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-190">7+</span></span>                    | <span data-ttu-id="e69e4-191">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-191">x64</span></span> |
| <span data-ttu-id="e69e4-192">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-192">Oracle Linux</span></span>                   | <span data-ttu-id="e69e4-193">7 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-193">7+</span></span>                    | <span data-ttu-id="e69e4-194">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-194">x64</span></span> |
| <span data-ttu-id="e69e4-195">Fedora</span><span class="sxs-lookup"><span data-stu-id="e69e4-195">Fedora</span></span>                         | <span data-ttu-id="e69e4-196">29 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-196">29+</span></span>                   | <span data-ttu-id="e69e4-197">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-197">x64</span></span> |
| <span data-ttu-id="e69e4-198">Debian</span><span class="sxs-lookup"><span data-stu-id="e69e4-198">Debian</span></span>                         | <span data-ttu-id="e69e4-199">9+</span><span class="sxs-lookup"><span data-stu-id="e69e4-199">9+</span></span>                    | <span data-ttu-id="e69e4-200">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="e69e4-200">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e69e4-201">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e69e4-201">Ubuntu</span></span>                         | <span data-ttu-id="e69e4-202">16.04+</span><span class="sxs-lookup"><span data-stu-id="e69e4-202">16.04+</span></span>                | <span data-ttu-id="e69e4-203">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="e69e4-203">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e69e4-204">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e69e4-204">Linux Mint</span></span>                     | <span data-ttu-id="e69e4-205">18 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-205">18+</span></span>                   | <span data-ttu-id="e69e4-206">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-206">x64</span></span> |
| <span data-ttu-id="e69e4-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e69e4-207">openSUSE</span></span>                       | <span data-ttu-id="e69e4-208">15 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-208">15+</span></span>                   | <span data-ttu-id="e69e4-209">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-209">x64</span></span> |
| <span data-ttu-id="e69e4-210">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e69e4-210">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="e69e4-211">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e69e4-211">12 SP2+</span></span>               | <span data-ttu-id="e69e4-212">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-212">x64</span></span> |
| <span data-ttu-id="e69e4-213">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-213">Alpine Linux</span></span>                   | <span data-ttu-id="e69e4-214">3.8+</span><span class="sxs-lookup"><span data-stu-id="e69e4-214">3.8+</span></span>                  | <span data-ttu-id="e69e4-215">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="e69e4-215">x64, ARM64</span></span> |

<span data-ttu-id="e69e4-216">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-216">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="e69e4-217">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-217">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="e69e4-218">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="e69e4-218">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="e69e4-219">.NET Core 2.2 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="e69e4-219">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="e69e4-220">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="e69e4-220">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e69e4-221">下列 Linux 發行版本/版本支援 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="e69e4-221">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e69e4-222">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e69e4-222">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e69e4-223">OS</span><span class="sxs-lookup"><span data-stu-id="e69e4-223">OS</span></span>                             |  <span data-ttu-id="e69e4-224">版本</span><span class="sxs-lookup"><span data-stu-id="e69e4-224">Version</span></span>                |  <span data-ttu-id="e69e4-225">架構</span><span class="sxs-lookup"><span data-stu-id="e69e4-225">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="e69e4-226">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-226">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="e69e4-227">6、7</span><span class="sxs-lookup"><span data-stu-id="e69e4-227">6, 7</span></span>                   | <span data-ttu-id="e69e4-228">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-228">x64</span></span> |
| <span data-ttu-id="e69e4-229">CentOS</span><span class="sxs-lookup"><span data-stu-id="e69e4-229">CentOS</span></span>                         |  <span data-ttu-id="e69e4-230">7</span><span class="sxs-lookup"><span data-stu-id="e69e4-230">7</span></span>                      | <span data-ttu-id="e69e4-231">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-231">x64</span></span> |
| <span data-ttu-id="e69e4-232">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-232">Oracle Linux</span></span>                   |  <span data-ttu-id="e69e4-233">7</span><span class="sxs-lookup"><span data-stu-id="e69e4-233">7</span></span>                      | <span data-ttu-id="e69e4-234">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-234">x64</span></span> |
| <span data-ttu-id="e69e4-235">Fedora</span><span class="sxs-lookup"><span data-stu-id="e69e4-235">Fedora</span></span>                         |  <span data-ttu-id="e69e4-236">29、30</span><span class="sxs-lookup"><span data-stu-id="e69e4-236">29, 30</span></span>                 | <span data-ttu-id="e69e4-237">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-237">x64</span></span> |
| <span data-ttu-id="e69e4-238">Debian</span><span class="sxs-lookup"><span data-stu-id="e69e4-238">Debian</span></span>                         |  <span data-ttu-id="e69e4-239">9</span><span class="sxs-lookup"><span data-stu-id="e69e4-239">9</span></span>                      | <span data-ttu-id="e69e4-240">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e69e4-240">x64, ARM32</span></span> |
| <span data-ttu-id="e69e4-241">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e69e4-241">Ubuntu</span></span>                         |  <span data-ttu-id="e69e4-242">16.04、18.04、18.10、19.04</span><span class="sxs-lookup"><span data-stu-id="e69e4-242">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="e69e4-243">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e69e4-243">x64, ARM32</span></span> |
| <span data-ttu-id="e69e4-244">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e69e4-244">Linux Mint</span></span>                     |  <span data-ttu-id="e69e4-245">17、18</span><span class="sxs-lookup"><span data-stu-id="e69e4-245">17, 18</span></span>                 | <span data-ttu-id="e69e4-246">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-246">x64</span></span> |
| <span data-ttu-id="e69e4-247">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e69e4-247">openSUSE</span></span>                       |  <span data-ttu-id="e69e4-248">15 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-248">15+</span></span>                    | <span data-ttu-id="e69e4-249">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-249">x64</span></span> |
| <span data-ttu-id="e69e4-250">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e69e4-250">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="e69e4-251">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e69e4-251">12 SP2+</span></span>                | <span data-ttu-id="e69e4-252">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-252">x64</span></span> |
| <span data-ttu-id="e69e4-253">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-253">Alpine Linux</span></span>                   |  <span data-ttu-id="e69e4-254">3.8+</span><span class="sxs-lookup"><span data-stu-id="e69e4-254">3.8+</span></span>                   | <span data-ttu-id="e69e4-255">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-255">x64</span></span> |

<span data-ttu-id="e69e4-256">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-256">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e69e4-257">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e69e4-257">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="e69e4-258">.NET Core 2.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="e69e4-258">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="e69e4-259">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="e69e4-259">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e69e4-260">下列 Linux 發行版本/版本支援 .NET Core 2.1：</span><span class="sxs-lookup"><span data-stu-id="e69e4-260">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e69e4-261">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e69e4-261">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e69e4-262">OS</span><span class="sxs-lookup"><span data-stu-id="e69e4-262">OS</span></span>                             |  <span data-ttu-id="e69e4-263">版本</span><span class="sxs-lookup"><span data-stu-id="e69e4-263">Version</span></span>                |  <span data-ttu-id="e69e4-264">架構</span><span class="sxs-lookup"><span data-stu-id="e69e4-264">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="e69e4-265">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-265">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="e69e4-266">6、7、8</span><span class="sxs-lookup"><span data-stu-id="e69e4-266">6, 7, 8</span></span>                | <span data-ttu-id="e69e4-267">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-267">x64</span></span> |
| <span data-ttu-id="e69e4-268">CentOS</span><span class="sxs-lookup"><span data-stu-id="e69e4-268">CentOS</span></span>                         |  <span data-ttu-id="e69e4-269">7 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-269">7+</span></span>                     | <span data-ttu-id="e69e4-270">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-270">x64</span></span> |
| <span data-ttu-id="e69e4-271">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-271">Oracle Linux</span></span>                   |  <span data-ttu-id="e69e4-272">7 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-272">7+</span></span>                     | <span data-ttu-id="e69e4-273">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-273">x64</span></span> |
| <span data-ttu-id="e69e4-274">Fedora</span><span class="sxs-lookup"><span data-stu-id="e69e4-274">Fedora</span></span>                         |  <span data-ttu-id="e69e4-275">29 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-275">29+</span></span>                    | <span data-ttu-id="e69e4-276">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-276">x64</span></span> |
| <span data-ttu-id="e69e4-277">Debian</span><span class="sxs-lookup"><span data-stu-id="e69e4-277">Debian</span></span>                         |  <span data-ttu-id="e69e4-278">9</span><span class="sxs-lookup"><span data-stu-id="e69e4-278">9</span></span>                      | <span data-ttu-id="e69e4-279">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e69e4-279">x64, ARM32</span></span> |
| <span data-ttu-id="e69e4-280">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e69e4-280">Ubuntu</span></span>                         |  <span data-ttu-id="e69e4-281">16.04、18.04、19.04、19.10</span><span class="sxs-lookup"><span data-stu-id="e69e4-281">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="e69e4-282">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="e69e4-282">x64, ARM32</span></span> |
| <span data-ttu-id="e69e4-283">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e69e4-283">Linux Mint</span></span>                     |  <span data-ttu-id="e69e4-284">17 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-284">17+</span></span>                    | <span data-ttu-id="e69e4-285">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-285">x64</span></span> |
| <span data-ttu-id="e69e4-286">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e69e4-286">openSUSE</span></span>                       |  <span data-ttu-id="e69e4-287">15 +</span><span class="sxs-lookup"><span data-stu-id="e69e4-287">15+</span></span>                    | <span data-ttu-id="e69e4-288">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-288">x64</span></span> |
| <span data-ttu-id="e69e4-289">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e69e4-289">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="e69e4-290">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e69e4-290">12 SP2+</span></span>                | <span data-ttu-id="e69e4-291">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-291">x64</span></span> |
| <span data-ttu-id="e69e4-292">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e69e4-292">Alpine Linux</span></span>                   |  <span data-ttu-id="e69e4-293">3.8+</span><span class="sxs-lookup"><span data-stu-id="e69e4-293">3.8+</span></span>                   | <span data-ttu-id="e69e4-294">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-294">x64</span></span> |

<span data-ttu-id="e69e4-295">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-295">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="e69e4-296">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="e69e4-296">Linux distribution dependencies</span></span>

<span data-ttu-id="e69e4-297">根據您的 linux 散發套件，您可能需要安裝其他相依性。</span><span class="sxs-lookup"><span data-stu-id="e69e4-297">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e69e4-298">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="e69e4-298">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="e69e4-299">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e69e4-299">Ubuntu</span></span>

<span data-ttu-id="e69e4-300">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="e69e4-300">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="e69e4-301">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="e69e4-301">liblttng-ust0</span></span>
- <span data-ttu-id="e69e4-302">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="e69e4-302">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="e69e4-303">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="e69e4-303">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="e69e4-304">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="e69e4-304">libssl1.0.0</span></span>
- <span data-ttu-id="e69e4-305">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="e69e4-305">libkrb5-3</span></span>
- <span data-ttu-id="e69e4-306">zlib1g</span><span class="sxs-lookup"><span data-stu-id="e69e4-306">zlib1g</span></span>
- <span data-ttu-id="e69e4-307">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="e69e4-307">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="e69e4-308">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="e69e4-308">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="e69e4-309">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="e69e4-309">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="e69e4-310">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="e69e4-310">libicu60 (for 18.x)</span></span>

<span data-ttu-id="e69e4-311">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="e69e4-311">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="e69e4-312">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="e69e4-312">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="e69e4-313">最新版的 Ubuntu 包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e69e4-313">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="e69e4-314">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e69e4-314">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="e69e4-315">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="e69e4-315">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="e69e4-316">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="e69e4-316">CentOS and Fedora</span></span>

<span data-ttu-id="e69e4-317">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="e69e4-317">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="e69e4-318">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="e69e4-318">lttng-ust</span></span>
- <span data-ttu-id="e69e4-319">libcurl</span><span class="sxs-lookup"><span data-stu-id="e69e4-319">libcurl</span></span>
- <span data-ttu-id="e69e4-320">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="e69e4-320">openssl-libs</span></span>
- <span data-ttu-id="e69e4-321">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="e69e4-321">krb5-libs</span></span>
- <span data-ttu-id="e69e4-322">libicu</span><span class="sxs-lookup"><span data-stu-id="e69e4-322">libicu</span></span>
- <span data-ttu-id="e69e4-323">zlib</span><span class="sxs-lookup"><span data-stu-id="e69e4-323">zlib</span></span>

<span data-ttu-id="e69e4-324">Fedora 使用者：如果您的 OpenSSL 版本 > = 1.1，您必須安裝相容性 **-compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="e69e4-324">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="e69e4-325">針對 .NET Core 2.0，也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="e69e4-325">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="e69e4-326">libunwind</span><span class="sxs-lookup"><span data-stu-id="e69e4-326">libunwind</span></span>
- <span data-ttu-id="e69e4-327">libuuid</span><span class="sxs-lookup"><span data-stu-id="e69e4-327">libuuid</span></span>

<span data-ttu-id="e69e4-328">如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="e69e4-328">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="e69e4-329">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="e69e4-329">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="e69e4-330">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="e69e4-330">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="e69e4-331">大部分的 CentOS 和 Fedora 版本都包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e69e4-331">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="e69e4-332">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e69e4-332">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="e69e4-333">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="e69e4-333">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="e69e4-334">下列 macOS 版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="e69e4-334">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="e69e4-335">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="e69e4-335">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e69e4-336">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="e69e4-336">.NET Core Version</span></span> | <span data-ttu-id="e69e4-337">macOS</span><span class="sxs-lookup"><span data-stu-id="e69e4-337">macOS</span></span>                 | <span data-ttu-id="e69e4-338">架構</span><span class="sxs-lookup"><span data-stu-id="e69e4-338">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="e69e4-339">3.0</span><span class="sxs-lookup"><span data-stu-id="e69e4-339">3.0</span></span>               | <span data-ttu-id="e69e4-340">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="e69e4-340">High Sierra (10.13+)</span></span>  | <span data-ttu-id="e69e4-341">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-341">x64</span></span> | [<span data-ttu-id="e69e4-342">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="e69e4-342">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="e69e4-343">2.2</span><span class="sxs-lookup"><span data-stu-id="e69e4-343">2.2</span></span>               | <span data-ttu-id="e69e4-344">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="e69e4-344">Sierra (10.12+)</span></span>       | <span data-ttu-id="e69e4-345">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-345">x64</span></span> | [<span data-ttu-id="e69e4-346">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="e69e4-346">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="e69e4-347">2.1</span><span class="sxs-lookup"><span data-stu-id="e69e4-347">2.1</span></span>               | <span data-ttu-id="e69e4-348">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="e69e4-348">Sierra (10.12+)</span></span>       | <span data-ttu-id="e69e4-349">X64</span><span class="sxs-lookup"><span data-stu-id="e69e4-349">x64</span></span> | [<span data-ttu-id="e69e4-350">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="e69e4-350">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="e69e4-351">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="e69e4-351">libgdiplus</span></span>

<span data-ttu-id="e69e4-352">使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="e69e4-352">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="e69e4-353">取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。</span><span class="sxs-lookup"><span data-stu-id="e69e4-353">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="e69e4-354">安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="e69e4-354">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="e69e4-355">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e69e4-355">Next steps</span></span>

- <span data-ttu-id="e69e4-356">若要開發及執行應用程式，請安裝[.NET Core SDK](sdk.md) （包括執行時間）。</span><span class="sxs-lookup"><span data-stu-id="e69e4-356">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="e69e4-357">若要執行其他人已建立的應用程式，請安裝[.Net Core 運行](runtime.md)時間。</span><span class="sxs-lookup"><span data-stu-id="e69e4-357">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
