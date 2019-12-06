---
title: .NET Core SDK 和執行時間相依性-.NET Core
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET Core SDK 和執行時間的作業系統和 CPU 架構必要條件。
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a535048fc8756b55068098ad61fdc37fc8c1f04e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837000"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="26156-103">.NET Core 相依性和需求</span><span class="sxs-lookup"><span data-stu-id="26156-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="26156-104">本文詳細說明 .NET Core 支援哪些作業系統和 CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="26156-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="26156-105">Supported operating systems</span><span class="sxs-lookup"><span data-stu-id="26156-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31tabnetcore31"></a>[<span data-ttu-id="26156-106">.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="26156-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="26156-107">.NET Core 3.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="26156-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-108">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-109">OS</span><span class="sxs-lookup"><span data-stu-id="26156-109">OS</span></span>                            | <span data-ttu-id="26156-110">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-110">Version</span></span>                        | <span data-ttu-id="26156-111">架構</span><span class="sxs-lookup"><span data-stu-id="26156-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="26156-112">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-112">Windows Client</span></span>                | <span data-ttu-id="26156-113">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="26156-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="26156-114">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-114">x64, x86</span></span>        |
| <span data-ttu-id="26156-115">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-115">Windows 10 Client</span></span>             | <span data-ttu-id="26156-116">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="26156-116">Version 1607+</span></span>                  | <span data-ttu-id="26156-117">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-117">x64, x86</span></span>        |
| <span data-ttu-id="26156-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="26156-118">Windows Server</span></span>                | <span data-ttu-id="26156-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="26156-119">2012 R2+</span></span>                       | <span data-ttu-id="26156-120">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-120">x64, x86</span></span>        |
| <span data-ttu-id="26156-121">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="26156-121">Nano Server</span></span>                   | <span data-ttu-id="26156-122">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="26156-122">Version 1803+</span></span>                  | <span data-ttu-id="26156-123">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="26156-123">x64, ARM32</span></span>      |

<span data-ttu-id="26156-124">如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="26156-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="26156-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="26156-126">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="26156-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-127">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-128">OS</span><span class="sxs-lookup"><span data-stu-id="26156-128">OS</span></span>                            | <span data-ttu-id="26156-129">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-129">Version</span></span>                        | <span data-ttu-id="26156-130">架構</span><span class="sxs-lookup"><span data-stu-id="26156-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="26156-131">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-131">Windows Client</span></span>                | <span data-ttu-id="26156-132">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="26156-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="26156-133">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-133">x64, x86</span></span>        |
| <span data-ttu-id="26156-134">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-134">Windows 10 Client</span></span>             | <span data-ttu-id="26156-135">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="26156-135">Version 1607+</span></span>                  | <span data-ttu-id="26156-136">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-136">x64, x86</span></span>        |
| <span data-ttu-id="26156-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="26156-137">Windows Server</span></span>                | <span data-ttu-id="26156-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="26156-138">2012 R2+</span></span>                       | <span data-ttu-id="26156-139">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-139">x64, x86</span></span>        |
| <span data-ttu-id="26156-140">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="26156-140">Nano Server</span></span>                   | <span data-ttu-id="26156-141">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="26156-141">Version 1803+</span></span>                  | <span data-ttu-id="26156-142">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="26156-142">x64, ARM32</span></span>      |

<span data-ttu-id="26156-143">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="26156-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="26156-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="26156-145">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="26156-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-146">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-147">OS</span><span class="sxs-lookup"><span data-stu-id="26156-147">OS</span></span>                            | <span data-ttu-id="26156-148">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-148">Version</span></span>                        | <span data-ttu-id="26156-149">架構</span><span class="sxs-lookup"><span data-stu-id="26156-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="26156-150">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-150">Windows Client</span></span>                | <span data-ttu-id="26156-151">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="26156-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="26156-152">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-152">x64, x86</span></span>        |
| <span data-ttu-id="26156-153">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-153">Windows 10 Client</span></span>             | <span data-ttu-id="26156-154">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="26156-154">Version 1607+</span></span>                  | <span data-ttu-id="26156-155">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-155">x64, x86</span></span>        |
| <span data-ttu-id="26156-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="26156-156">Windows Server</span></span>                | <span data-ttu-id="26156-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="26156-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="26156-158">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-158">x64, x86</span></span>        |
| <span data-ttu-id="26156-159">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="26156-159">Nano Server</span></span>                   | <span data-ttu-id="26156-160">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="26156-160">Version 1803+</span></span>                   | <span data-ttu-id="26156-161">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="26156-161">x64, ARM32</span></span>      |

<span data-ttu-id="26156-162">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="26156-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="26156-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="26156-164">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="26156-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-165">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-166">OS</span><span class="sxs-lookup"><span data-stu-id="26156-166">OS</span></span>                            | <span data-ttu-id="26156-167">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-167">Version</span></span>                        | <span data-ttu-id="26156-168">架構</span><span class="sxs-lookup"><span data-stu-id="26156-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="26156-169">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-169">Windows Client</span></span>                | <span data-ttu-id="26156-170">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="26156-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="26156-171">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-171">x64, x86</span></span>        |
| <span data-ttu-id="26156-172">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="26156-172">Windows 10 Client</span></span>             | <span data-ttu-id="26156-173">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="26156-173">Version 1607+</span></span>                  | <span data-ttu-id="26156-174">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-174">x64, x86</span></span>        |
| <span data-ttu-id="26156-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="26156-175">Windows Server</span></span>                | <span data-ttu-id="26156-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="26156-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="26156-177">x64、x86</span><span class="sxs-lookup"><span data-stu-id="26156-177">x64, x86</span></span>        |
| <span data-ttu-id="26156-178">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="26156-178">Nano Server</span></span>                   | <span data-ttu-id="26156-179">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="26156-179">Version 1803+</span></span>                  | <span data-ttu-id="26156-180">x64</span><span class="sxs-lookup"><span data-stu-id="26156-180">x64,</span></span>            |

<span data-ttu-id="26156-181">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="26156-182">Windows 7/Vista/8.1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="26156-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="26156-183">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：</span><span class="sxs-lookup"><span data-stu-id="26156-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="26156-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="26156-184">Windows 7 SP1</span></span>
- <span data-ttu-id="26156-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="26156-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="26156-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="26156-186">Windows 8.1</span></span>
- <span data-ttu-id="26156-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="26156-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="26156-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="26156-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="26156-189">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="26156-189">Install the following:</span></span>

- <span data-ttu-id="26156-190">[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件 Update 3。</span><span class="sxs-lookup"><span data-stu-id="26156-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="26156-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="26156-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="26156-192">如果您遇到下列其中一個錯誤，也需要上述需求：</span><span class="sxs-lookup"><span data-stu-id="26156-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="26156-193">程式無法啟動，因為您的電腦遺失了*4.9.0-api* --win---------l1-1。</span><span class="sxs-lookup"><span data-stu-id="26156-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="26156-194">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="26156-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="26156-195">\-或-</span><span class="sxs-lookup"><span data-stu-id="26156-195">\- or -</span></span>
>
> <span data-ttu-id="26156-196">找到*程式庫用 hostfxr* ，但從*C：\\\<path_to_app >\\用 hostfxr*載入它失敗。</span><span class="sxs-lookup"><span data-stu-id="26156-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31tabnetcore31"></a>[<span data-ttu-id="26156-197">.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="26156-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="26156-198">.NET Core 3.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="26156-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="26156-199">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="26156-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="26156-200">下列 Linux 發行版本/版本支援 .NET Core 3.1：</span><span class="sxs-lookup"><span data-stu-id="26156-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-201">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-202">OS</span><span class="sxs-lookup"><span data-stu-id="26156-202">OS</span></span>                             | <span data-ttu-id="26156-203">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-203">Version</span></span>               | <span data-ttu-id="26156-204">架構</span><span class="sxs-lookup"><span data-stu-id="26156-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="26156-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="26156-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="26156-206">6、7、8</span><span class="sxs-lookup"><span data-stu-id="26156-206">6, 7, 8</span></span>               | <span data-ttu-id="26156-207">x64</span><span class="sxs-lookup"><span data-stu-id="26156-207">x64</span></span> |
| <span data-ttu-id="26156-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="26156-208">CentOS</span></span>                         | <span data-ttu-id="26156-209">7+</span><span class="sxs-lookup"><span data-stu-id="26156-209">7+</span></span>                    | <span data-ttu-id="26156-210">x64</span><span class="sxs-lookup"><span data-stu-id="26156-210">x64</span></span> |
| <span data-ttu-id="26156-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="26156-211">Oracle Linux</span></span>                   | <span data-ttu-id="26156-212">7+</span><span class="sxs-lookup"><span data-stu-id="26156-212">7+</span></span>                    | <span data-ttu-id="26156-213">x64</span><span class="sxs-lookup"><span data-stu-id="26156-213">x64</span></span> |
| <span data-ttu-id="26156-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="26156-214">Fedora</span></span>                         | <span data-ttu-id="26156-215">29 +</span><span class="sxs-lookup"><span data-stu-id="26156-215">29+</span></span>                   | <span data-ttu-id="26156-216">x64</span><span class="sxs-lookup"><span data-stu-id="26156-216">x64</span></span> |
| <span data-ttu-id="26156-217">Debian</span><span class="sxs-lookup"><span data-stu-id="26156-217">Debian</span></span>                         | <span data-ttu-id="26156-218">9+</span><span class="sxs-lookup"><span data-stu-id="26156-218">9+</span></span>                    | <span data-ttu-id="26156-219">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="26156-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="26156-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="26156-220">Ubuntu</span></span>                         | <span data-ttu-id="26156-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="26156-221">16.04+</span></span>                | <span data-ttu-id="26156-222">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="26156-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="26156-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="26156-223">Linux Mint</span></span>                     | <span data-ttu-id="26156-224">18 +</span><span class="sxs-lookup"><span data-stu-id="26156-224">18+</span></span>                   | <span data-ttu-id="26156-225">x64</span><span class="sxs-lookup"><span data-stu-id="26156-225">x64</span></span> |
| <span data-ttu-id="26156-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="26156-226">openSUSE</span></span>                       | <span data-ttu-id="26156-227">15 +</span><span class="sxs-lookup"><span data-stu-id="26156-227">15+</span></span>                   | <span data-ttu-id="26156-228">x64</span><span class="sxs-lookup"><span data-stu-id="26156-228">x64</span></span> |
| <span data-ttu-id="26156-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="26156-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="26156-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="26156-230">12 SP2+</span></span>               | <span data-ttu-id="26156-231">x64</span><span class="sxs-lookup"><span data-stu-id="26156-231">x64</span></span> |
| <span data-ttu-id="26156-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="26156-232">Alpine Linux</span></span>                   | <span data-ttu-id="26156-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="26156-233">3.10+</span></span>                 | <span data-ttu-id="26156-234">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="26156-234">x64, ARM64</span></span> |

<span data-ttu-id="26156-235">如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="26156-236">如需有關如何在 ARM64 上安裝 .NET Core 3.1 （核心 4.14 +）的詳細資訊，請參閱[在 Linux 上安裝 .Net core 3.0 ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。</span><span class="sxs-lookup"><span data-stu-id="26156-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26156-237">ARM64 支援需要 Linux 核心4.14 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="26156-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="26156-238">有些 linux 散發套件符合此需求，而有些則不需要。</span><span class="sxs-lookup"><span data-stu-id="26156-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="26156-239">例如，支援 Ubuntu 18.04，但 Ubuntu 16.04 則否。</span><span class="sxs-lookup"><span data-stu-id="26156-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="26156-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="26156-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="26156-241">.NET Core 3.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="26156-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="26156-242">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="26156-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="26156-243">下列 Linux 發行版本/版本支援 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="26156-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-244">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-245">OS</span><span class="sxs-lookup"><span data-stu-id="26156-245">OS</span></span>                             | <span data-ttu-id="26156-246">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-246">Version</span></span>               | <span data-ttu-id="26156-247">架構</span><span class="sxs-lookup"><span data-stu-id="26156-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="26156-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="26156-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="26156-249">6、7、8</span><span class="sxs-lookup"><span data-stu-id="26156-249">6, 7, 8</span></span>               | <span data-ttu-id="26156-250">x64</span><span class="sxs-lookup"><span data-stu-id="26156-250">x64</span></span> |
| <span data-ttu-id="26156-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="26156-251">CentOS</span></span>                         | <span data-ttu-id="26156-252">7+</span><span class="sxs-lookup"><span data-stu-id="26156-252">7+</span></span>                    | <span data-ttu-id="26156-253">x64</span><span class="sxs-lookup"><span data-stu-id="26156-253">x64</span></span> |
| <span data-ttu-id="26156-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="26156-254">Oracle Linux</span></span>                   | <span data-ttu-id="26156-255">7+</span><span class="sxs-lookup"><span data-stu-id="26156-255">7+</span></span>                    | <span data-ttu-id="26156-256">x64</span><span class="sxs-lookup"><span data-stu-id="26156-256">x64</span></span> |
| <span data-ttu-id="26156-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="26156-257">Fedora</span></span>                         | <span data-ttu-id="26156-258">29 +</span><span class="sxs-lookup"><span data-stu-id="26156-258">29+</span></span>                   | <span data-ttu-id="26156-259">x64</span><span class="sxs-lookup"><span data-stu-id="26156-259">x64</span></span> |
| <span data-ttu-id="26156-260">Debian</span><span class="sxs-lookup"><span data-stu-id="26156-260">Debian</span></span>                         | <span data-ttu-id="26156-261">9+</span><span class="sxs-lookup"><span data-stu-id="26156-261">9+</span></span>                    | <span data-ttu-id="26156-262">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="26156-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="26156-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="26156-263">Ubuntu</span></span>                         | <span data-ttu-id="26156-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="26156-264">16.04+</span></span>                | <span data-ttu-id="26156-265">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="26156-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="26156-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="26156-266">Linux Mint</span></span>                     | <span data-ttu-id="26156-267">18 +</span><span class="sxs-lookup"><span data-stu-id="26156-267">18+</span></span>                   | <span data-ttu-id="26156-268">x64</span><span class="sxs-lookup"><span data-stu-id="26156-268">x64</span></span> |
| <span data-ttu-id="26156-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="26156-269">openSUSE</span></span>                       | <span data-ttu-id="26156-270">15 +</span><span class="sxs-lookup"><span data-stu-id="26156-270">15+</span></span>                   | <span data-ttu-id="26156-271">x64</span><span class="sxs-lookup"><span data-stu-id="26156-271">x64</span></span> |
| <span data-ttu-id="26156-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="26156-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="26156-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="26156-273">12 SP2+</span></span>               | <span data-ttu-id="26156-274">x64</span><span class="sxs-lookup"><span data-stu-id="26156-274">x64</span></span> |
| <span data-ttu-id="26156-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="26156-275">Alpine Linux</span></span>                   | <span data-ttu-id="26156-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="26156-276">3.8+</span></span>                  | <span data-ttu-id="26156-277">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="26156-277">x64, ARM64</span></span> |

<span data-ttu-id="26156-278">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="26156-279">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="26156-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="26156-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="26156-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="26156-281">.NET Core 2.2 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="26156-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="26156-282">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="26156-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="26156-283">下列 Linux 發行版本/版本支援 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="26156-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-284">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-285">OS</span><span class="sxs-lookup"><span data-stu-id="26156-285">OS</span></span>                             |  <span data-ttu-id="26156-286">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-286">Version</span></span>                |  <span data-ttu-id="26156-287">架構</span><span class="sxs-lookup"><span data-stu-id="26156-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="26156-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="26156-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="26156-289">6、7</span><span class="sxs-lookup"><span data-stu-id="26156-289">6, 7</span></span>                   | <span data-ttu-id="26156-290">x64</span><span class="sxs-lookup"><span data-stu-id="26156-290">x64</span></span> |
| <span data-ttu-id="26156-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="26156-291">CentOS</span></span>                         |  <span data-ttu-id="26156-292">7</span><span class="sxs-lookup"><span data-stu-id="26156-292">7</span></span>                      | <span data-ttu-id="26156-293">x64</span><span class="sxs-lookup"><span data-stu-id="26156-293">x64</span></span> |
| <span data-ttu-id="26156-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="26156-294">Oracle Linux</span></span>                   |  <span data-ttu-id="26156-295">7</span><span class="sxs-lookup"><span data-stu-id="26156-295">7</span></span>                      | <span data-ttu-id="26156-296">x64</span><span class="sxs-lookup"><span data-stu-id="26156-296">x64</span></span> |
| <span data-ttu-id="26156-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="26156-297">Fedora</span></span>                         |  <span data-ttu-id="26156-298">29、30</span><span class="sxs-lookup"><span data-stu-id="26156-298">29, 30</span></span>                 | <span data-ttu-id="26156-299">x64</span><span class="sxs-lookup"><span data-stu-id="26156-299">x64</span></span> |
| <span data-ttu-id="26156-300">Debian</span><span class="sxs-lookup"><span data-stu-id="26156-300">Debian</span></span>                         |  <span data-ttu-id="26156-301">9</span><span class="sxs-lookup"><span data-stu-id="26156-301">9</span></span>                      | <span data-ttu-id="26156-302">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="26156-302">x64, ARM32</span></span> |
| <span data-ttu-id="26156-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="26156-303">Ubuntu</span></span>                         |  <span data-ttu-id="26156-304">16.04、18.04、18.10、19.04</span><span class="sxs-lookup"><span data-stu-id="26156-304">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="26156-305">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="26156-305">x64, ARM32</span></span> |
| <span data-ttu-id="26156-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="26156-306">Linux Mint</span></span>                     |  <span data-ttu-id="26156-307">17、18</span><span class="sxs-lookup"><span data-stu-id="26156-307">17, 18</span></span>                 | <span data-ttu-id="26156-308">x64</span><span class="sxs-lookup"><span data-stu-id="26156-308">x64</span></span> |
| <span data-ttu-id="26156-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="26156-309">openSUSE</span></span>                       |  <span data-ttu-id="26156-310">15 +</span><span class="sxs-lookup"><span data-stu-id="26156-310">15+</span></span>                    | <span data-ttu-id="26156-311">x64</span><span class="sxs-lookup"><span data-stu-id="26156-311">x64</span></span> |
| <span data-ttu-id="26156-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="26156-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="26156-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="26156-313">12 SP2+</span></span>                | <span data-ttu-id="26156-314">x64</span><span class="sxs-lookup"><span data-stu-id="26156-314">x64</span></span> |
| <span data-ttu-id="26156-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="26156-315">Alpine Linux</span></span>                   |  <span data-ttu-id="26156-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="26156-316">3.8+</span></span>                   | <span data-ttu-id="26156-317">x64</span><span class="sxs-lookup"><span data-stu-id="26156-317">x64</span></span> |

<span data-ttu-id="26156-318">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="26156-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="26156-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="26156-320">.NET Core 2.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="26156-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="26156-321">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="26156-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="26156-322">下列 Linux 發行版本/版本支援 .NET Core 2.1：</span><span class="sxs-lookup"><span data-stu-id="26156-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-323">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-324">OS</span><span class="sxs-lookup"><span data-stu-id="26156-324">OS</span></span>                             |  <span data-ttu-id="26156-325">{2&gt;版本&lt;2}</span><span class="sxs-lookup"><span data-stu-id="26156-325">Version</span></span>                |  <span data-ttu-id="26156-326">架構</span><span class="sxs-lookup"><span data-stu-id="26156-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="26156-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="26156-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="26156-328">6、7、8</span><span class="sxs-lookup"><span data-stu-id="26156-328">6, 7, 8</span></span>                | <span data-ttu-id="26156-329">x64</span><span class="sxs-lookup"><span data-stu-id="26156-329">x64</span></span> |
| <span data-ttu-id="26156-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="26156-330">CentOS</span></span>                         |  <span data-ttu-id="26156-331">7+</span><span class="sxs-lookup"><span data-stu-id="26156-331">7+</span></span>                     | <span data-ttu-id="26156-332">x64</span><span class="sxs-lookup"><span data-stu-id="26156-332">x64</span></span> |
| <span data-ttu-id="26156-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="26156-333">Oracle Linux</span></span>                   |  <span data-ttu-id="26156-334">7+</span><span class="sxs-lookup"><span data-stu-id="26156-334">7+</span></span>                     | <span data-ttu-id="26156-335">x64</span><span class="sxs-lookup"><span data-stu-id="26156-335">x64</span></span> |
| <span data-ttu-id="26156-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="26156-336">Fedora</span></span>                         |  <span data-ttu-id="26156-337">29 +</span><span class="sxs-lookup"><span data-stu-id="26156-337">29+</span></span>                    | <span data-ttu-id="26156-338">x64</span><span class="sxs-lookup"><span data-stu-id="26156-338">x64</span></span> |
| <span data-ttu-id="26156-339">Debian</span><span class="sxs-lookup"><span data-stu-id="26156-339">Debian</span></span>                         |  <span data-ttu-id="26156-340">9</span><span class="sxs-lookup"><span data-stu-id="26156-340">9</span></span>                      | <span data-ttu-id="26156-341">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="26156-341">x64, ARM32</span></span> |
| <span data-ttu-id="26156-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="26156-342">Ubuntu</span></span>                         |  <span data-ttu-id="26156-343">16.04、18.04、19.04、19.10</span><span class="sxs-lookup"><span data-stu-id="26156-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="26156-344">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="26156-344">x64, ARM32</span></span> |
| <span data-ttu-id="26156-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="26156-345">Linux Mint</span></span>                     |  <span data-ttu-id="26156-346">17 +</span><span class="sxs-lookup"><span data-stu-id="26156-346">17+</span></span>                    | <span data-ttu-id="26156-347">x64</span><span class="sxs-lookup"><span data-stu-id="26156-347">x64</span></span> |
| <span data-ttu-id="26156-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="26156-348">openSUSE</span></span>                       |  <span data-ttu-id="26156-349">15 +</span><span class="sxs-lookup"><span data-stu-id="26156-349">15+</span></span>                    | <span data-ttu-id="26156-350">x64</span><span class="sxs-lookup"><span data-stu-id="26156-350">x64</span></span> |
| <span data-ttu-id="26156-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="26156-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="26156-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="26156-352">12 SP2+</span></span>                | <span data-ttu-id="26156-353">x64</span><span class="sxs-lookup"><span data-stu-id="26156-353">x64</span></span> |
| <span data-ttu-id="26156-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="26156-354">Alpine Linux</span></span>                   |  <span data-ttu-id="26156-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="26156-355">3.8+</span></span>                   | <span data-ttu-id="26156-356">x64</span><span class="sxs-lookup"><span data-stu-id="26156-356">x64</span></span> |

<span data-ttu-id="26156-357">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="26156-358">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="26156-358">Linux distribution dependencies</span></span>

<span data-ttu-id="26156-359">根據您的 linux 散發套件，您可能需要安裝其他相依性。</span><span class="sxs-lookup"><span data-stu-id="26156-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26156-360">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="26156-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="26156-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="26156-361">Ubuntu</span></span>

<span data-ttu-id="26156-362">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="26156-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="26156-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="26156-363">liblttng-ust0</span></span>
- <span data-ttu-id="26156-364">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="26156-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="26156-365">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="26156-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="26156-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="26156-366">libssl1.0.0</span></span>
- <span data-ttu-id="26156-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="26156-367">libkrb5-3</span></span>
- <span data-ttu-id="26156-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="26156-368">zlib1g</span></span>
- <span data-ttu-id="26156-369">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="26156-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="26156-370">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="26156-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="26156-371">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="26156-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="26156-372">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="26156-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="26156-373">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="26156-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="26156-374">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="26156-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="26156-375">最新版的 Ubuntu 包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="26156-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="26156-376">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="26156-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="26156-377">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="26156-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="26156-378">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="26156-378">CentOS and Fedora</span></span>

<span data-ttu-id="26156-379">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="26156-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="26156-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="26156-380">lttng-ust</span></span>
- <span data-ttu-id="26156-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="26156-381">libcurl</span></span>
- <span data-ttu-id="26156-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="26156-382">openssl-libs</span></span>
- <span data-ttu-id="26156-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="26156-383">krb5-libs</span></span>
- <span data-ttu-id="26156-384">libicu</span><span class="sxs-lookup"><span data-stu-id="26156-384">libicu</span></span>
- <span data-ttu-id="26156-385">zlib</span><span class="sxs-lookup"><span data-stu-id="26156-385">zlib</span></span>

<span data-ttu-id="26156-386">Fedora 使用者：如果您的 OpenSSL 版本 > = 1.1，您必須安裝相容性 **-compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="26156-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="26156-387">針對 .NET Core 2.0，也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="26156-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="26156-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="26156-388">libunwind</span></span>
- <span data-ttu-id="26156-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="26156-389">libuuid</span></span>

<span data-ttu-id="26156-390">如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="26156-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="26156-391">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="26156-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="26156-392">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="26156-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="26156-393">大部分的 CentOS 和 Fedora 版本都包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="26156-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="26156-394">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="26156-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="26156-395">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="26156-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="26156-396">下列 macOS 版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="26156-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="26156-397">`+` 符號代表最小版本。</span><span class="sxs-lookup"><span data-stu-id="26156-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="26156-398">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="26156-398">.NET Core Version</span></span> | <span data-ttu-id="26156-399">macOS</span><span class="sxs-lookup"><span data-stu-id="26156-399">macOS</span></span>                 | <span data-ttu-id="26156-400">架構</span><span class="sxs-lookup"><span data-stu-id="26156-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="26156-401">3.1</span><span class="sxs-lookup"><span data-stu-id="26156-401">3.1</span></span>               | <span data-ttu-id="26156-402">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="26156-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="26156-403">x64</span><span class="sxs-lookup"><span data-stu-id="26156-403">x64</span></span> | [<span data-ttu-id="26156-404">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="26156-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="26156-405">3.0</span><span class="sxs-lookup"><span data-stu-id="26156-405">3.0</span></span>               | <span data-ttu-id="26156-406">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="26156-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="26156-407">x64</span><span class="sxs-lookup"><span data-stu-id="26156-407">x64</span></span> | [<span data-ttu-id="26156-408">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="26156-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="26156-409">2.2</span><span class="sxs-lookup"><span data-stu-id="26156-409">2.2</span></span>               | <span data-ttu-id="26156-410">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="26156-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="26156-411">x64</span><span class="sxs-lookup"><span data-stu-id="26156-411">x64</span></span> | [<span data-ttu-id="26156-412">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="26156-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="26156-413">2.1</span><span class="sxs-lookup"><span data-stu-id="26156-413">2.1</span></span>               | <span data-ttu-id="26156-414">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="26156-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="26156-415">x64</span><span class="sxs-lookup"><span data-stu-id="26156-415">x64</span></span> | [<span data-ttu-id="26156-416">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="26156-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="26156-417">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="26156-417">libgdiplus</span></span>

<span data-ttu-id="26156-418">使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="26156-418">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="26156-419">取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。</span><span class="sxs-lookup"><span data-stu-id="26156-419">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="26156-420">安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="26156-420">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="26156-421">後續步驟</span><span class="sxs-lookup"><span data-stu-id="26156-421">Next steps</span></span>

- <span data-ttu-id="26156-422">若要開發及執行應用程式，請安裝[.NET Core SDK](sdk.md) （包括執行時間）。</span><span class="sxs-lookup"><span data-stu-id="26156-422">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="26156-423">若要執行其他人已建立的應用程式，請安裝[.Net Core 運行](runtime.md)時間。</span><span class="sxs-lookup"><span data-stu-id="26156-423">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
