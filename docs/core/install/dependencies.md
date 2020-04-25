---
title: .NET Core SDK 和執行時間相依性-.NET Core
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET Core SDK 和執行時間的作業系統和 CPU 架構必要條件。
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 42765d4402dfa17d4e962b2ecaf7a83e91853c76
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140984"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="86100-103">.NET Core 相依性和需求</span><span class="sxs-lookup"><span data-stu-id="86100-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="86100-104">本文詳細說明 .NET Core 支援哪些作業系統和 CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="86100-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="86100-105">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="86100-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="86100-106">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="86100-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="86100-107">.NET Core 3.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="86100-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-108">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-109">OS</span><span class="sxs-lookup"><span data-stu-id="86100-109">OS</span></span>                            | <span data-ttu-id="86100-110">版本</span><span class="sxs-lookup"><span data-stu-id="86100-110">Version</span></span>                        | <span data-ttu-id="86100-111">架構</span><span class="sxs-lookup"><span data-stu-id="86100-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="86100-112">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-112">Windows Client</span></span>                | <span data-ttu-id="86100-113">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="86100-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="86100-114">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-114">x64, x86</span></span>        |
| <span data-ttu-id="86100-115">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-115">Windows 10 Client</span></span>             | <span data-ttu-id="86100-116">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="86100-116">Version 1607+</span></span>                  | <span data-ttu-id="86100-117">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-117">x64, x86</span></span>        |
| <span data-ttu-id="86100-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="86100-118">Windows Server</span></span>                | <span data-ttu-id="86100-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="86100-119">2012 R2+</span></span>                       | <span data-ttu-id="86100-120">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-120">x64, x86</span></span>        |
| <span data-ttu-id="86100-121">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="86100-121">Nano Server</span></span>                   | <span data-ttu-id="86100-122">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="86100-122">Version 1803+</span></span>                  | <span data-ttu-id="86100-123">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="86100-123">x64, ARM32</span></span>      |

<span data-ttu-id="86100-124">如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="86100-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="86100-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="86100-126">*.NET Core 3.0 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="86100-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="86100-127">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="86100-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-128">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-129">OS</span><span class="sxs-lookup"><span data-stu-id="86100-129">OS</span></span>                            | <span data-ttu-id="86100-130">版本</span><span class="sxs-lookup"><span data-stu-id="86100-130">Version</span></span>                        | <span data-ttu-id="86100-131">架構</span><span class="sxs-lookup"><span data-stu-id="86100-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="86100-132">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-132">Windows Client</span></span>                | <span data-ttu-id="86100-133">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="86100-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="86100-134">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-134">x64, x86</span></span>        |
| <span data-ttu-id="86100-135">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-135">Windows 10 Client</span></span>             | <span data-ttu-id="86100-136">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="86100-136">Version 1607+</span></span>                  | <span data-ttu-id="86100-137">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-137">x64, x86</span></span>        |
| <span data-ttu-id="86100-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="86100-138">Windows Server</span></span>                | <span data-ttu-id="86100-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="86100-139">2012 R2+</span></span>                       | <span data-ttu-id="86100-140">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-140">x64, x86</span></span>        |
| <span data-ttu-id="86100-141">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="86100-141">Nano Server</span></span>                   | <span data-ttu-id="86100-142">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="86100-142">Version 1803+</span></span>                  | <span data-ttu-id="86100-143">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="86100-143">x64, ARM32</span></span>      |

<span data-ttu-id="86100-144">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="86100-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="86100-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="86100-146">*.NET Core 2.2 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="86100-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="86100-147">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="86100-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-148">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-149">OS</span><span class="sxs-lookup"><span data-stu-id="86100-149">OS</span></span>                            | <span data-ttu-id="86100-150">版本</span><span class="sxs-lookup"><span data-stu-id="86100-150">Version</span></span>                        | <span data-ttu-id="86100-151">架構</span><span class="sxs-lookup"><span data-stu-id="86100-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="86100-152">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-152">Windows Client</span></span>                | <span data-ttu-id="86100-153">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="86100-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="86100-154">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-154">x64, x86</span></span>        |
| <span data-ttu-id="86100-155">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-155">Windows 10 Client</span></span>             | <span data-ttu-id="86100-156">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="86100-156">Version 1607+</span></span>                  | <span data-ttu-id="86100-157">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-157">x64, x86</span></span>        |
| <span data-ttu-id="86100-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="86100-158">Windows Server</span></span>                | <span data-ttu-id="86100-159">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="86100-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="86100-160">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-160">x64, x86</span></span>        |
| <span data-ttu-id="86100-161">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="86100-161">Nano Server</span></span>                   | <span data-ttu-id="86100-162">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="86100-162">Version 1803+</span></span>                   | <span data-ttu-id="86100-163">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="86100-163">x64, ARM32</span></span>      |

<span data-ttu-id="86100-164">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="86100-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="86100-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="86100-166">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="86100-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-167">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-168">OS</span><span class="sxs-lookup"><span data-stu-id="86100-168">OS</span></span>                            | <span data-ttu-id="86100-169">版本</span><span class="sxs-lookup"><span data-stu-id="86100-169">Version</span></span>                        | <span data-ttu-id="86100-170">架構</span><span class="sxs-lookup"><span data-stu-id="86100-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="86100-171">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-171">Windows Client</span></span>                | <span data-ttu-id="86100-172">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="86100-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="86100-173">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-173">x64, x86</span></span>        |
| <span data-ttu-id="86100-174">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="86100-174">Windows 10 Client</span></span>             | <span data-ttu-id="86100-175">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="86100-175">Version 1607+</span></span>                  | <span data-ttu-id="86100-176">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-176">x64, x86</span></span>        |
| <span data-ttu-id="86100-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="86100-177">Windows Server</span></span>                | <span data-ttu-id="86100-178">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="86100-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="86100-179">x64、x86</span><span class="sxs-lookup"><span data-stu-id="86100-179">x64, x86</span></span>        |
| <span data-ttu-id="86100-180">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="86100-180">Nano Server</span></span>                   | <span data-ttu-id="86100-181">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="86100-181">Version 1803+</span></span>                  | <span data-ttu-id="86100-182">x64</span><span class="sxs-lookup"><span data-stu-id="86100-182">x64,</span></span>            |

<span data-ttu-id="86100-183">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="86100-184">Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="86100-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="86100-185">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：</span><span class="sxs-lookup"><span data-stu-id="86100-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="86100-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="86100-186">Windows 7 SP1</span></span>
- <span data-ttu-id="86100-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="86100-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="86100-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="86100-188">Windows 8.1</span></span>
- <span data-ttu-id="86100-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="86100-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="86100-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="86100-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="86100-191">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="86100-191">Install the following:</span></span>

- <span data-ttu-id="86100-192">[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件 Update 3。</span><span class="sxs-lookup"><span data-stu-id="86100-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="86100-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="86100-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="86100-194">如果您遇到下列其中一個錯誤，也需要上述需求：</span><span class="sxs-lookup"><span data-stu-id="86100-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="86100-195">程式無法啟動，因為您的電腦遺失了*4.9.0-api* --win---------l1-1。</span><span class="sxs-lookup"><span data-stu-id="86100-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="86100-196">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="86100-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="86100-197">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="86100-197">\- or -</span></span>
>
> <span data-ttu-id="86100-198">程式無法啟動，因為您的電腦缺少 cor--------------- *1 4.9.0-.dll。*</span><span class="sxs-lookup"><span data-stu-id="86100-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="86100-199">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="86100-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="86100-200">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="86100-200">\- or -</span></span>
>
> <span data-ttu-id="86100-201">找到*程式庫用 hostfxr* ，但從*C\\\<： path_to_app>\\用 hostfxr*載入失敗。</span><span class="sxs-lookup"><span data-stu-id="86100-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="86100-202">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="86100-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="86100-203">.NET Core 3.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="86100-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="86100-204">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="86100-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="86100-205">下列 Linux 發行版本/版本支援 .NET Core 3.1：</span><span class="sxs-lookup"><span data-stu-id="86100-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-206">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-207">OS</span><span class="sxs-lookup"><span data-stu-id="86100-207">OS</span></span>                             | <span data-ttu-id="86100-208">版本</span><span class="sxs-lookup"><span data-stu-id="86100-208">Version</span></span>               | <span data-ttu-id="86100-209">架構</span><span class="sxs-lookup"><span data-stu-id="86100-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="86100-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="86100-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="86100-211">6、7、8</span><span class="sxs-lookup"><span data-stu-id="86100-211">6, 7, 8</span></span>               | <span data-ttu-id="86100-212">x64</span><span class="sxs-lookup"><span data-stu-id="86100-212">x64</span></span> |
| <span data-ttu-id="86100-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="86100-213">CentOS</span></span>                         | <span data-ttu-id="86100-214">7+</span><span class="sxs-lookup"><span data-stu-id="86100-214">7+</span></span>                    | <span data-ttu-id="86100-215">x64</span><span class="sxs-lookup"><span data-stu-id="86100-215">x64</span></span> |
| <span data-ttu-id="86100-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="86100-216">Oracle Linux</span></span>                   | <span data-ttu-id="86100-217">7+</span><span class="sxs-lookup"><span data-stu-id="86100-217">7+</span></span>                    | <span data-ttu-id="86100-218">x64</span><span class="sxs-lookup"><span data-stu-id="86100-218">x64</span></span> |
| <span data-ttu-id="86100-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="86100-219">Fedora</span></span>                         | <span data-ttu-id="86100-220">30 +</span><span class="sxs-lookup"><span data-stu-id="86100-220">30+</span></span>                   | <span data-ttu-id="86100-221">x64</span><span class="sxs-lookup"><span data-stu-id="86100-221">x64</span></span> |
| <span data-ttu-id="86100-222">Debian</span><span class="sxs-lookup"><span data-stu-id="86100-222">Debian</span></span>                         | <span data-ttu-id="86100-223">9+</span><span class="sxs-lookup"><span data-stu-id="86100-223">9+</span></span>                    | <span data-ttu-id="86100-224">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="86100-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="86100-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86100-225">Ubuntu</span></span>                         | <span data-ttu-id="86100-226">16.04+</span><span class="sxs-lookup"><span data-stu-id="86100-226">16.04+</span></span>                | <span data-ttu-id="86100-227">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="86100-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="86100-228">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="86100-228">Linux Mint</span></span>                     | <span data-ttu-id="86100-229">18 +</span><span class="sxs-lookup"><span data-stu-id="86100-229">18+</span></span>                   | <span data-ttu-id="86100-230">x64</span><span class="sxs-lookup"><span data-stu-id="86100-230">x64</span></span> |
| <span data-ttu-id="86100-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="86100-231">openSUSE</span></span>                       | <span data-ttu-id="86100-232">15 +</span><span class="sxs-lookup"><span data-stu-id="86100-232">15+</span></span>                   | <span data-ttu-id="86100-233">x64</span><span class="sxs-lookup"><span data-stu-id="86100-233">x64</span></span> |
| <span data-ttu-id="86100-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="86100-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="86100-235">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="86100-235">12 SP2+</span></span>               | <span data-ttu-id="86100-236">x64</span><span class="sxs-lookup"><span data-stu-id="86100-236">x64</span></span> |
| <span data-ttu-id="86100-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="86100-237">Alpine Linux</span></span>                   | <span data-ttu-id="86100-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="86100-238">3.10+</span></span>                 | <span data-ttu-id="86100-239">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="86100-239">x64, ARM64</span></span> |

<span data-ttu-id="86100-240">如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="86100-241">如需有關如何在 ARM64 上安裝 .NET Core 3.1 （核心 4.14 +）的詳細資訊，請參閱[在 Linux 上安裝 .Net core 3.0 ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。</span><span class="sxs-lookup"><span data-stu-id="86100-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86100-242">ARM64 支援需要 Linux 核心4.14 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="86100-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="86100-243">有些 linux 散發套件符合此需求，而有些則不需要。</span><span class="sxs-lookup"><span data-stu-id="86100-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="86100-244">例如，支援 Ubuntu 18.04，但 Ubuntu 16.04 則否。</span><span class="sxs-lookup"><span data-stu-id="86100-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="86100-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="86100-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="86100-246">*.NET Core 3.0 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="86100-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="86100-247">.NET Core 3.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="86100-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="86100-248">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="86100-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="86100-249">下列 Linux 發行版本/版本支援 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="86100-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-250">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-251">OS</span><span class="sxs-lookup"><span data-stu-id="86100-251">OS</span></span>                             | <span data-ttu-id="86100-252">版本</span><span class="sxs-lookup"><span data-stu-id="86100-252">Version</span></span>               | <span data-ttu-id="86100-253">架構</span><span class="sxs-lookup"><span data-stu-id="86100-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="86100-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="86100-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="86100-255">6、7、8</span><span class="sxs-lookup"><span data-stu-id="86100-255">6, 7, 8</span></span>               | <span data-ttu-id="86100-256">x64</span><span class="sxs-lookup"><span data-stu-id="86100-256">x64</span></span> |
| <span data-ttu-id="86100-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="86100-257">CentOS</span></span>                         | <span data-ttu-id="86100-258">7+</span><span class="sxs-lookup"><span data-stu-id="86100-258">7+</span></span>                    | <span data-ttu-id="86100-259">x64</span><span class="sxs-lookup"><span data-stu-id="86100-259">x64</span></span> |
| <span data-ttu-id="86100-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="86100-260">Oracle Linux</span></span>                   | <span data-ttu-id="86100-261">7+</span><span class="sxs-lookup"><span data-stu-id="86100-261">7+</span></span>                    | <span data-ttu-id="86100-262">x64</span><span class="sxs-lookup"><span data-stu-id="86100-262">x64</span></span> |
| <span data-ttu-id="86100-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="86100-263">Fedora</span></span>                         | <span data-ttu-id="86100-264">29 +</span><span class="sxs-lookup"><span data-stu-id="86100-264">29+</span></span>                   | <span data-ttu-id="86100-265">x64</span><span class="sxs-lookup"><span data-stu-id="86100-265">x64</span></span> |
| <span data-ttu-id="86100-266">Debian</span><span class="sxs-lookup"><span data-stu-id="86100-266">Debian</span></span>                         | <span data-ttu-id="86100-267">9+</span><span class="sxs-lookup"><span data-stu-id="86100-267">9+</span></span>                    | <span data-ttu-id="86100-268">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="86100-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="86100-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86100-269">Ubuntu</span></span>                         | <span data-ttu-id="86100-270">16.04+</span><span class="sxs-lookup"><span data-stu-id="86100-270">16.04+</span></span>                | <span data-ttu-id="86100-271">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="86100-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="86100-272">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="86100-272">Linux Mint</span></span>                     | <span data-ttu-id="86100-273">18 +</span><span class="sxs-lookup"><span data-stu-id="86100-273">18+</span></span>                   | <span data-ttu-id="86100-274">x64</span><span class="sxs-lookup"><span data-stu-id="86100-274">x64</span></span> |
| <span data-ttu-id="86100-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="86100-275">openSUSE</span></span>                       | <span data-ttu-id="86100-276">15 +</span><span class="sxs-lookup"><span data-stu-id="86100-276">15+</span></span>                   | <span data-ttu-id="86100-277">x64</span><span class="sxs-lookup"><span data-stu-id="86100-277">x64</span></span> |
| <span data-ttu-id="86100-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="86100-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="86100-279">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="86100-279">12 SP2+</span></span>               | <span data-ttu-id="86100-280">x64</span><span class="sxs-lookup"><span data-stu-id="86100-280">x64</span></span> |
| <span data-ttu-id="86100-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="86100-281">Alpine Linux</span></span>                   | <span data-ttu-id="86100-282">3.8+</span><span class="sxs-lookup"><span data-stu-id="86100-282">3.8+</span></span>                  | <span data-ttu-id="86100-283">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="86100-283">x64, ARM64</span></span> |

<span data-ttu-id="86100-284">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="86100-285">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="86100-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="86100-286">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="86100-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="86100-287">*.NET Core 2.2 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="86100-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="86100-288">.NET Core 2.2 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="86100-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="86100-289">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="86100-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="86100-290">下列 Linux 發行版本/版本支援 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="86100-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-291">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-292">OS</span><span class="sxs-lookup"><span data-stu-id="86100-292">OS</span></span>                             |  <span data-ttu-id="86100-293">版本</span><span class="sxs-lookup"><span data-stu-id="86100-293">Version</span></span>                |  <span data-ttu-id="86100-294">架構</span><span class="sxs-lookup"><span data-stu-id="86100-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="86100-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="86100-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="86100-296">6、7</span><span class="sxs-lookup"><span data-stu-id="86100-296">6, 7</span></span>                   | <span data-ttu-id="86100-297">x64</span><span class="sxs-lookup"><span data-stu-id="86100-297">x64</span></span> |
| <span data-ttu-id="86100-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="86100-298">CentOS</span></span>                         |  <span data-ttu-id="86100-299">7</span><span class="sxs-lookup"><span data-stu-id="86100-299">7</span></span>                      | <span data-ttu-id="86100-300">x64</span><span class="sxs-lookup"><span data-stu-id="86100-300">x64</span></span> |
| <span data-ttu-id="86100-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="86100-301">Oracle Linux</span></span>                   |  <span data-ttu-id="86100-302">7</span><span class="sxs-lookup"><span data-stu-id="86100-302">7</span></span>                      | <span data-ttu-id="86100-303">x64</span><span class="sxs-lookup"><span data-stu-id="86100-303">x64</span></span> |
| <span data-ttu-id="86100-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="86100-304">Fedora</span></span>                         |  <span data-ttu-id="86100-305">29、30</span><span class="sxs-lookup"><span data-stu-id="86100-305">29, 30</span></span>                 | <span data-ttu-id="86100-306">x64</span><span class="sxs-lookup"><span data-stu-id="86100-306">x64</span></span> |
| <span data-ttu-id="86100-307">Debian</span><span class="sxs-lookup"><span data-stu-id="86100-307">Debian</span></span>                         |  <span data-ttu-id="86100-308">9</span><span class="sxs-lookup"><span data-stu-id="86100-308">9</span></span>                      | <span data-ttu-id="86100-309">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="86100-309">x64, ARM32</span></span> |
| <span data-ttu-id="86100-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86100-310">Ubuntu</span></span>                         |  <span data-ttu-id="86100-311">16.04、18.04、18.10</span><span class="sxs-lookup"><span data-stu-id="86100-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="86100-312">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="86100-312">x64, ARM32</span></span> |
| <span data-ttu-id="86100-313">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="86100-313">Linux Mint</span></span>                     |  <span data-ttu-id="86100-314">17、18</span><span class="sxs-lookup"><span data-stu-id="86100-314">17, 18</span></span>                 | <span data-ttu-id="86100-315">x64</span><span class="sxs-lookup"><span data-stu-id="86100-315">x64</span></span> |
| <span data-ttu-id="86100-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="86100-316">openSUSE</span></span>                       |  <span data-ttu-id="86100-317">15 +</span><span class="sxs-lookup"><span data-stu-id="86100-317">15+</span></span>                    | <span data-ttu-id="86100-318">x64</span><span class="sxs-lookup"><span data-stu-id="86100-318">x64</span></span> |
| <span data-ttu-id="86100-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="86100-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="86100-320">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="86100-320">12 SP2+</span></span>                | <span data-ttu-id="86100-321">x64</span><span class="sxs-lookup"><span data-stu-id="86100-321">x64</span></span> |
| <span data-ttu-id="86100-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="86100-322">Alpine Linux</span></span>                   |  <span data-ttu-id="86100-323">3.8+</span><span class="sxs-lookup"><span data-stu-id="86100-323">3.8+</span></span>                   | <span data-ttu-id="86100-324">x64</span><span class="sxs-lookup"><span data-stu-id="86100-324">x64</span></span> |

<span data-ttu-id="86100-325">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="86100-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="86100-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="86100-327">.NET Core 2.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="86100-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="86100-328">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="86100-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="86100-329">下列 Linux 發行版本/版本支援 .NET Core 2.1：</span><span class="sxs-lookup"><span data-stu-id="86100-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-330">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-331">OS</span><span class="sxs-lookup"><span data-stu-id="86100-331">OS</span></span>                             |  <span data-ttu-id="86100-332">版本</span><span class="sxs-lookup"><span data-stu-id="86100-332">Version</span></span>                |  <span data-ttu-id="86100-333">架構</span><span class="sxs-lookup"><span data-stu-id="86100-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="86100-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="86100-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="86100-335">6、7、8</span><span class="sxs-lookup"><span data-stu-id="86100-335">6, 7, 8</span></span>                | <span data-ttu-id="86100-336">x64</span><span class="sxs-lookup"><span data-stu-id="86100-336">x64</span></span> |
| <span data-ttu-id="86100-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="86100-337">CentOS</span></span>                         |  <span data-ttu-id="86100-338">7+</span><span class="sxs-lookup"><span data-stu-id="86100-338">7+</span></span>                     | <span data-ttu-id="86100-339">x64</span><span class="sxs-lookup"><span data-stu-id="86100-339">x64</span></span> |
| <span data-ttu-id="86100-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="86100-340">Oracle Linux</span></span>                   |  <span data-ttu-id="86100-341">7+</span><span class="sxs-lookup"><span data-stu-id="86100-341">7+</span></span>                     | <span data-ttu-id="86100-342">x64</span><span class="sxs-lookup"><span data-stu-id="86100-342">x64</span></span> |
| <span data-ttu-id="86100-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="86100-343">Fedora</span></span>                         |  <span data-ttu-id="86100-344">30 +</span><span class="sxs-lookup"><span data-stu-id="86100-344">30+</span></span>                    | <span data-ttu-id="86100-345">x64</span><span class="sxs-lookup"><span data-stu-id="86100-345">x64</span></span> |
| <span data-ttu-id="86100-346">Debian</span><span class="sxs-lookup"><span data-stu-id="86100-346">Debian</span></span>                         |  <span data-ttu-id="86100-347">9</span><span class="sxs-lookup"><span data-stu-id="86100-347">9</span></span>                      | <span data-ttu-id="86100-348">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="86100-348">x64, ARM32</span></span> |
| <span data-ttu-id="86100-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86100-349">Ubuntu</span></span>                         |  <span data-ttu-id="86100-350">16.04、18.04、19.04、19.10</span><span class="sxs-lookup"><span data-stu-id="86100-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="86100-351">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="86100-351">x64, ARM32</span></span> |
| <span data-ttu-id="86100-352">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="86100-352">Linux Mint</span></span>                     |  <span data-ttu-id="86100-353">17+</span><span class="sxs-lookup"><span data-stu-id="86100-353">17+</span></span>                    | <span data-ttu-id="86100-354">x64</span><span class="sxs-lookup"><span data-stu-id="86100-354">x64</span></span> |
| <span data-ttu-id="86100-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="86100-355">openSUSE</span></span>                       |  <span data-ttu-id="86100-356">15 +</span><span class="sxs-lookup"><span data-stu-id="86100-356">15+</span></span>                    | <span data-ttu-id="86100-357">x64</span><span class="sxs-lookup"><span data-stu-id="86100-357">x64</span></span> |
| <span data-ttu-id="86100-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="86100-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="86100-359">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="86100-359">12 SP2+</span></span>                | <span data-ttu-id="86100-360">x64</span><span class="sxs-lookup"><span data-stu-id="86100-360">x64</span></span> |
| <span data-ttu-id="86100-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="86100-361">Alpine Linux</span></span>                   |  <span data-ttu-id="86100-362">3.8+</span><span class="sxs-lookup"><span data-stu-id="86100-362">3.8+</span></span>                   | <span data-ttu-id="86100-363">x64</span><span class="sxs-lookup"><span data-stu-id="86100-363">x64</span></span> |

<span data-ttu-id="86100-364">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="86100-365">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="86100-365">Linux distribution dependencies</span></span>

<span data-ttu-id="86100-366">根據您的 linux 散發套件，您可能需要安裝其他相依性。</span><span class="sxs-lookup"><span data-stu-id="86100-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86100-367">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="86100-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="86100-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86100-368">Ubuntu</span></span>

<span data-ttu-id="86100-369">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="86100-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="86100-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="86100-370">liblttng-ust0</span></span>
- <span data-ttu-id="86100-371">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="86100-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="86100-372">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="86100-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="86100-373">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="86100-373">libssl1.0.0</span></span>
- <span data-ttu-id="86100-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="86100-374">libkrb5-3</span></span>
- <span data-ttu-id="86100-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="86100-375">zlib1g</span></span>
- <span data-ttu-id="86100-376">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="86100-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="86100-377">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="86100-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="86100-378">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="86100-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="86100-379">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="86100-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="86100-380">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="86100-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="86100-381">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="86100-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="86100-382">最新版的 Ubuntu 包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="86100-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="86100-383">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="86100-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="86100-384">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="86100-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="86100-385">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="86100-385">CentOS and Fedora</span></span>

<span data-ttu-id="86100-386">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="86100-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="86100-387">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="86100-387">lttng-ust</span></span>
- <span data-ttu-id="86100-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="86100-388">libcurl</span></span>
- <span data-ttu-id="86100-389">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="86100-389">openssl-libs</span></span>
- <span data-ttu-id="86100-390">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="86100-390">krb5-libs</span></span>
- <span data-ttu-id="86100-391">libicu</span><span class="sxs-lookup"><span data-stu-id="86100-391">libicu</span></span>
- <span data-ttu-id="86100-392">zlib</span><span class="sxs-lookup"><span data-stu-id="86100-392">zlib</span></span>

<span data-ttu-id="86100-393">Fedora 使用者：如果您的 OpenSSL 版本 >= 1.1，您必須安裝相容性 **-compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="86100-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="86100-394">針對 .NET Core 2.0，也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="86100-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="86100-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="86100-395">libunwind</span></span>
- <span data-ttu-id="86100-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="86100-396">libuuid</span></span>

<span data-ttu-id="86100-397">如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="86100-398">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="86100-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="86100-399">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="86100-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="86100-400">大部分的 CentOS 和 Fedora 版本都包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="86100-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="86100-401">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="86100-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="86100-402">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="86100-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="86100-403">下列 macOS 版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="86100-403">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="86100-404">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="86100-404">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="86100-405">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="86100-405">.NET Core Version</span></span> | <span data-ttu-id="86100-406">macOS</span><span class="sxs-lookup"><span data-stu-id="86100-406">macOS</span></span>                 | <span data-ttu-id="86100-407">架構</span><span class="sxs-lookup"><span data-stu-id="86100-407">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="86100-408">3.1</span><span class="sxs-lookup"><span data-stu-id="86100-408">3.1</span></span>               | <span data-ttu-id="86100-409">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="86100-409">High Sierra (10.13+)</span></span>  | <span data-ttu-id="86100-410">x64</span><span class="sxs-lookup"><span data-stu-id="86100-410">x64</span></span> | [<span data-ttu-id="86100-411">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="86100-411">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="86100-412">3.0</span><span class="sxs-lookup"><span data-stu-id="86100-412">3.0</span></span>               | <span data-ttu-id="86100-413">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="86100-413">High Sierra (10.13+)</span></span>  | <span data-ttu-id="86100-414">x64</span><span class="sxs-lookup"><span data-stu-id="86100-414">x64</span></span> | [<span data-ttu-id="86100-415">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="86100-415">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="86100-416">2.2</span><span class="sxs-lookup"><span data-stu-id="86100-416">2.2</span></span>               | <span data-ttu-id="86100-417">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="86100-417">Sierra (10.12+)</span></span>       | <span data-ttu-id="86100-418">x64</span><span class="sxs-lookup"><span data-stu-id="86100-418">x64</span></span> | [<span data-ttu-id="86100-419">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="86100-419">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="86100-420">2.1</span><span class="sxs-lookup"><span data-stu-id="86100-420">2.1</span></span>               | <span data-ttu-id="86100-421">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="86100-421">Sierra (10.12+)</span></span>       | <span data-ttu-id="86100-422">x64</span><span class="sxs-lookup"><span data-stu-id="86100-422">x64</span></span> | [<span data-ttu-id="86100-423">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="86100-423">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="86100-424">從 macOS Catalina （版本10.15）開始，在2019年6月1日之後以開發人員識別碼散發的所有軟體都必須是公證。</span><span class="sxs-lookup"><span data-stu-id="86100-424">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="86100-425">這項需求適用于 .NET core 執行時間、.NET Core SDK 和使用 .NET Core 所建立的軟體。</span><span class="sxs-lookup"><span data-stu-id="86100-425">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="86100-426">從2020年2月18日起，已公證 .NET Core （執行時間和 SDK）版本3.1、3.0 和2.1 的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="86100-426">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="86100-427">先前發行的版本不會公證。</span><span class="sxs-lookup"><span data-stu-id="86100-427">Prior released versions aren't notarized.</span></span> <span data-ttu-id="86100-428">如果您執行非公證應用程式，您會看到類似下圖的錯誤：</span><span class="sxs-lookup"><span data-stu-id="86100-428">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notarization 警示](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="86100-430">如需強制執行 notarization 如何影響 .NET Core （和您的 .NET Core 應用程式）的詳細資訊，請參閱[使用 MacOS Catalina notarization](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="86100-430">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="86100-431">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="86100-431">libgdiplus</span></span>

<span data-ttu-id="86100-432">使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="86100-432">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="86100-433">取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。</span><span class="sxs-lookup"><span data-stu-id="86100-433">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="86100-434">安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="86100-434">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="86100-435">後續步驟</span><span class="sxs-lookup"><span data-stu-id="86100-435">Next steps</span></span>

- <span data-ttu-id="86100-436">若要開發及執行應用程式，請安裝[.NET Core SDK](sdk.md) （包括執行時間）。</span><span class="sxs-lookup"><span data-stu-id="86100-436">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="86100-437">若要執行其他人已建立的應用程式，請安裝[.Net Core 運行](runtime.md)時間。</span><span class="sxs-lookup"><span data-stu-id="86100-437">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
