---
title: .NET Core SDK 和執行時間相依性-.NET Core
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET Core SDK 和執行時間的作業系統和 CPU 架構必要條件。
author: leecow
ms.author: leecow
ms.date: 04/30/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 280aa1431686ff99257580bb024a84b1e57f85c0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895481"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="845b3-103">.NET Core 相依性和需求</span><span class="sxs-lookup"><span data-stu-id="845b3-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="845b3-104">本文詳細說明 .NET Core 支援哪些作業系統和 CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="845b3-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="845b3-105">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="845b3-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="845b3-106">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="845b3-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="845b3-107">.NET Core 3.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="845b3-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-108">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-109">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-109">OS</span></span>                            | <span data-ttu-id="845b3-110">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-110">Version</span></span>                        | <span data-ttu-id="845b3-111">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="845b3-112">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-112">Windows Client</span></span>                | <span data-ttu-id="845b3-113">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="845b3-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="845b3-114">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-114">x64, x86</span></span>        |
| <span data-ttu-id="845b3-115">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-115">Windows 10 Client</span></span>             | <span data-ttu-id="845b3-116">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="845b3-116">Version 1607+</span></span>                  | <span data-ttu-id="845b3-117">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-117">x64, x86</span></span>        |
| <span data-ttu-id="845b3-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="845b3-118">Windows Server</span></span>                | <span data-ttu-id="845b3-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="845b3-119">2012 R2+</span></span>                       | <span data-ttu-id="845b3-120">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-120">x64, x86</span></span>        |
| <span data-ttu-id="845b3-121">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="845b3-121">Nano Server</span></span>                   | <span data-ttu-id="845b3-122">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="845b3-122">Version 1803+</span></span>                  | <span data-ttu-id="845b3-123">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="845b3-123">x64, ARM32</span></span>      |

<span data-ttu-id="845b3-124">如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="845b3-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="845b3-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="845b3-126">*.NET Core 3.0 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="845b3-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="845b3-127">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="845b3-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-128">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-129">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-129">OS</span></span>                            | <span data-ttu-id="845b3-130">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-130">Version</span></span>                        | <span data-ttu-id="845b3-131">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="845b3-132">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-132">Windows Client</span></span>                | <span data-ttu-id="845b3-133">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="845b3-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="845b3-134">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-134">x64, x86</span></span>        |
| <span data-ttu-id="845b3-135">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-135">Windows 10 Client</span></span>             | <span data-ttu-id="845b3-136">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="845b3-136">Version 1607+</span></span>                  | <span data-ttu-id="845b3-137">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-137">x64, x86</span></span>        |
| <span data-ttu-id="845b3-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="845b3-138">Windows Server</span></span>                | <span data-ttu-id="845b3-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="845b3-139">2012 R2+</span></span>                       | <span data-ttu-id="845b3-140">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-140">x64, x86</span></span>        |
| <span data-ttu-id="845b3-141">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="845b3-141">Nano Server</span></span>                   | <span data-ttu-id="845b3-142">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="845b3-142">Version 1803+</span></span>                  | <span data-ttu-id="845b3-143">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="845b3-143">x64, ARM32</span></span>      |

<span data-ttu-id="845b3-144">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="845b3-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="845b3-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="845b3-146">*.NET Core 2.2 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="845b3-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="845b3-147">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="845b3-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-148">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-149">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-149">OS</span></span>                            | <span data-ttu-id="845b3-150">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-150">Version</span></span>                        | <span data-ttu-id="845b3-151">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="845b3-152">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-152">Windows Client</span></span>                | <span data-ttu-id="845b3-153">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="845b3-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="845b3-154">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-154">x64, x86</span></span>        |
| <span data-ttu-id="845b3-155">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-155">Windows 10 Client</span></span>             | <span data-ttu-id="845b3-156">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="845b3-156">Version 1607+</span></span>                  | <span data-ttu-id="845b3-157">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-157">x64, x86</span></span>        |
| <span data-ttu-id="845b3-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="845b3-158">Windows Server</span></span>                | <span data-ttu-id="845b3-159">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="845b3-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="845b3-160">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-160">x64, x86</span></span>        |
| <span data-ttu-id="845b3-161">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="845b3-161">Nano Server</span></span>                   | <span data-ttu-id="845b3-162">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="845b3-162">Version 1803+</span></span>                   | <span data-ttu-id="845b3-163">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="845b3-163">x64, ARM32</span></span>      |

<span data-ttu-id="845b3-164">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="845b3-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="845b3-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="845b3-166">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="845b3-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-167">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-168">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-168">OS</span></span>                            | <span data-ttu-id="845b3-169">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-169">Version</span></span>                        | <span data-ttu-id="845b3-170">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="845b3-171">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-171">Windows Client</span></span>                | <span data-ttu-id="845b3-172">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="845b3-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="845b3-173">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-173">x64, x86</span></span>        |
| <span data-ttu-id="845b3-174">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="845b3-174">Windows 10 Client</span></span>             | <span data-ttu-id="845b3-175">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="845b3-175">Version 1607+</span></span>                  | <span data-ttu-id="845b3-176">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-176">x64, x86</span></span>        |
| <span data-ttu-id="845b3-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="845b3-177">Windows Server</span></span>                | <span data-ttu-id="845b3-178">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="845b3-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="845b3-179">x64、x86</span><span class="sxs-lookup"><span data-stu-id="845b3-179">x64, x86</span></span>        |
| <span data-ttu-id="845b3-180">Nano 伺服器</span><span class="sxs-lookup"><span data-stu-id="845b3-180">Nano Server</span></span>                   | <span data-ttu-id="845b3-181">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="845b3-181">Version 1803+</span></span>                  | <span data-ttu-id="845b3-182">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-182">x64,</span></span>            |

<span data-ttu-id="845b3-183">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="845b3-184">Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="845b3-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="845b3-185">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：</span><span class="sxs-lookup"><span data-stu-id="845b3-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="845b3-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="845b3-186">Windows 7 SP1</span></span>
- <span data-ttu-id="845b3-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="845b3-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="845b3-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="845b3-188">Windows 8.1</span></span>
- <span data-ttu-id="845b3-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="845b3-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="845b3-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="845b3-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="845b3-191">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="845b3-191">Install the following:</span></span>

- <span data-ttu-id="845b3-192">[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件 Update 3。</span><span class="sxs-lookup"><span data-stu-id="845b3-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="845b3-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="845b3-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="845b3-194">如果您遇到下列其中一個錯誤，也需要上述需求：</span><span class="sxs-lookup"><span data-stu-id="845b3-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="845b3-195">程式無法啟動，因為您的電腦遺失了*4.9.0-api* --win---------l1-1。</span><span class="sxs-lookup"><span data-stu-id="845b3-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="845b3-196">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="845b3-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="845b3-197">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="845b3-197">\- or -</span></span>
>
> <span data-ttu-id="845b3-198">程式無法啟動，因為您的電腦缺少 cor--------------- *1 4.9.0-.dll。*</span><span class="sxs-lookup"><span data-stu-id="845b3-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="845b3-199">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="845b3-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="845b3-200">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="845b3-200">\- or -</span></span>
>
> <span data-ttu-id="845b3-201">找到*程式庫用 hostfxr* ，但從*C\\\<： path_to_app>\\用 hostfxr*載入失敗。</span><span class="sxs-lookup"><span data-stu-id="845b3-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="845b3-202">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="845b3-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="845b3-203">.NET Core 3.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="845b3-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="845b3-204">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="845b3-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="845b3-205">下列 Linux 發行版本/版本支援 .NET Core 3.1：</span><span class="sxs-lookup"><span data-stu-id="845b3-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-206">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-207">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-207">OS</span></span>                             | <span data-ttu-id="845b3-208">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-208">Version</span></span>               | <span data-ttu-id="845b3-209">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="845b3-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="845b3-211">6、7、8</span><span class="sxs-lookup"><span data-stu-id="845b3-211">6, 7, 8</span></span>               | <span data-ttu-id="845b3-212">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-212">x64</span></span> |
| <span data-ttu-id="845b3-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="845b3-213">CentOS</span></span>                         | <span data-ttu-id="845b3-214">7+</span><span class="sxs-lookup"><span data-stu-id="845b3-214">7+</span></span>                    | <span data-ttu-id="845b3-215">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-215">x64</span></span> |
| <span data-ttu-id="845b3-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-216">Oracle Linux</span></span>                   | <span data-ttu-id="845b3-217">7+</span><span class="sxs-lookup"><span data-stu-id="845b3-217">7+</span></span>                    | <span data-ttu-id="845b3-218">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-218">x64</span></span> |
| <span data-ttu-id="845b3-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="845b3-219">Fedora</span></span>                         | <span data-ttu-id="845b3-220">30 +</span><span class="sxs-lookup"><span data-stu-id="845b3-220">30+</span></span>                   | <span data-ttu-id="845b3-221">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-221">x64</span></span> |
| <span data-ttu-id="845b3-222">Debian</span><span class="sxs-lookup"><span data-stu-id="845b3-222">Debian</span></span>                         | <span data-ttu-id="845b3-223">9+</span><span class="sxs-lookup"><span data-stu-id="845b3-223">9+</span></span>                    | <span data-ttu-id="845b3-224">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="845b3-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="845b3-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="845b3-225">Ubuntu</span></span>                         | <span data-ttu-id="845b3-226">16.04+</span><span class="sxs-lookup"><span data-stu-id="845b3-226">16.04+</span></span>                | <span data-ttu-id="845b3-227">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="845b3-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="845b3-228">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="845b3-228">Linux Mint</span></span>                     | <span data-ttu-id="845b3-229">18 +</span><span class="sxs-lookup"><span data-stu-id="845b3-229">18+</span></span>                   | <span data-ttu-id="845b3-230">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-230">x64</span></span> |
| <span data-ttu-id="845b3-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="845b3-231">openSUSE</span></span>                       | <span data-ttu-id="845b3-232">15 +</span><span class="sxs-lookup"><span data-stu-id="845b3-232">15+</span></span>                   | <span data-ttu-id="845b3-233">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-233">x64</span></span> |
| <span data-ttu-id="845b3-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="845b3-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="845b3-235">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="845b3-235">12 SP2+</span></span>               | <span data-ttu-id="845b3-236">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-236">x64</span></span> |
| <span data-ttu-id="845b3-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-237">Alpine Linux</span></span>                   | <span data-ttu-id="845b3-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="845b3-238">3.10+</span></span>                 | <span data-ttu-id="845b3-239">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="845b3-239">x64, ARM64</span></span> |

<span data-ttu-id="845b3-240">如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="845b3-241">如需有關如何在 ARM64 上安裝 .NET Core 3.1 （核心 4.14 +）的詳細資訊，請參閱[在 Linux 上安裝 .Net core 3.0 ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。</span><span class="sxs-lookup"><span data-stu-id="845b3-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="845b3-242">ARM64 支援需要 Linux 核心4.14 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="845b3-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="845b3-243">有些 linux 散發套件符合此需求，而有些則不需要。</span><span class="sxs-lookup"><span data-stu-id="845b3-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="845b3-244">例如，支援 Ubuntu 18.04，但 Ubuntu 16.04 則否。</span><span class="sxs-lookup"><span data-stu-id="845b3-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="845b3-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="845b3-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="845b3-246">*.NET Core 3.0 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="845b3-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="845b3-247">.NET Core 3.0 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="845b3-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="845b3-248">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="845b3-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="845b3-249">下列 Linux 發行版本/版本支援 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="845b3-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-250">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-251">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-251">OS</span></span>                             | <span data-ttu-id="845b3-252">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-252">Version</span></span>               | <span data-ttu-id="845b3-253">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="845b3-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="845b3-255">6、7、8</span><span class="sxs-lookup"><span data-stu-id="845b3-255">6, 7, 8</span></span>               | <span data-ttu-id="845b3-256">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-256">x64</span></span> |
| <span data-ttu-id="845b3-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="845b3-257">CentOS</span></span>                         | <span data-ttu-id="845b3-258">7+</span><span class="sxs-lookup"><span data-stu-id="845b3-258">7+</span></span>                    | <span data-ttu-id="845b3-259">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-259">x64</span></span> |
| <span data-ttu-id="845b3-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-260">Oracle Linux</span></span>                   | <span data-ttu-id="845b3-261">7+</span><span class="sxs-lookup"><span data-stu-id="845b3-261">7+</span></span>                    | <span data-ttu-id="845b3-262">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-262">x64</span></span> |
| <span data-ttu-id="845b3-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="845b3-263">Fedora</span></span>                         | <span data-ttu-id="845b3-264">29 +</span><span class="sxs-lookup"><span data-stu-id="845b3-264">29+</span></span>                   | <span data-ttu-id="845b3-265">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-265">x64</span></span> |
| <span data-ttu-id="845b3-266">Debian</span><span class="sxs-lookup"><span data-stu-id="845b3-266">Debian</span></span>                         | <span data-ttu-id="845b3-267">9+</span><span class="sxs-lookup"><span data-stu-id="845b3-267">9+</span></span>                    | <span data-ttu-id="845b3-268">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="845b3-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="845b3-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="845b3-269">Ubuntu</span></span>                         | <span data-ttu-id="845b3-270">16.04+</span><span class="sxs-lookup"><span data-stu-id="845b3-270">16.04+</span></span>                | <span data-ttu-id="845b3-271">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="845b3-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="845b3-272">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="845b3-272">Linux Mint</span></span>                     | <span data-ttu-id="845b3-273">18 +</span><span class="sxs-lookup"><span data-stu-id="845b3-273">18+</span></span>                   | <span data-ttu-id="845b3-274">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-274">x64</span></span> |
| <span data-ttu-id="845b3-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="845b3-275">openSUSE</span></span>                       | <span data-ttu-id="845b3-276">15 +</span><span class="sxs-lookup"><span data-stu-id="845b3-276">15+</span></span>                   | <span data-ttu-id="845b3-277">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-277">x64</span></span> |
| <span data-ttu-id="845b3-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="845b3-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="845b3-279">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="845b3-279">12 SP2+</span></span>               | <span data-ttu-id="845b3-280">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-280">x64</span></span> |
| <span data-ttu-id="845b3-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-281">Alpine Linux</span></span>                   | <span data-ttu-id="845b3-282">3.8+</span><span class="sxs-lookup"><span data-stu-id="845b3-282">3.8+</span></span>                  | <span data-ttu-id="845b3-283">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="845b3-283">x64, ARM64</span></span> |

<span data-ttu-id="845b3-284">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="845b3-285">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="845b3-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="845b3-286">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="845b3-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="845b3-287">*.NET Core 2.2 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="845b3-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="845b3-288">.NET Core 2.2 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="845b3-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="845b3-289">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="845b3-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="845b3-290">下列 Linux 發行版本/版本支援 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="845b3-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-291">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-292">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-292">OS</span></span>                             |  <span data-ttu-id="845b3-293">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-293">Version</span></span>                |  <span data-ttu-id="845b3-294">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="845b3-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="845b3-296">6、7</span><span class="sxs-lookup"><span data-stu-id="845b3-296">6, 7</span></span>                   | <span data-ttu-id="845b3-297">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-297">x64</span></span> |
| <span data-ttu-id="845b3-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="845b3-298">CentOS</span></span>                         |  <span data-ttu-id="845b3-299">7</span><span class="sxs-lookup"><span data-stu-id="845b3-299">7</span></span>                      | <span data-ttu-id="845b3-300">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-300">x64</span></span> |
| <span data-ttu-id="845b3-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-301">Oracle Linux</span></span>                   |  <span data-ttu-id="845b3-302">7</span><span class="sxs-lookup"><span data-stu-id="845b3-302">7</span></span>                      | <span data-ttu-id="845b3-303">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-303">x64</span></span> |
| <span data-ttu-id="845b3-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="845b3-304">Fedora</span></span>                         |  <span data-ttu-id="845b3-305">29、30</span><span class="sxs-lookup"><span data-stu-id="845b3-305">29, 30</span></span>                 | <span data-ttu-id="845b3-306">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-306">x64</span></span> |
| <span data-ttu-id="845b3-307">Debian</span><span class="sxs-lookup"><span data-stu-id="845b3-307">Debian</span></span>                         |  <span data-ttu-id="845b3-308">9</span><span class="sxs-lookup"><span data-stu-id="845b3-308">9</span></span>                      | <span data-ttu-id="845b3-309">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="845b3-309">x64, ARM32</span></span> |
| <span data-ttu-id="845b3-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="845b3-310">Ubuntu</span></span>                         |  <span data-ttu-id="845b3-311">16.04、18.04、18.10</span><span class="sxs-lookup"><span data-stu-id="845b3-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="845b3-312">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="845b3-312">x64, ARM32</span></span> |
| <span data-ttu-id="845b3-313">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="845b3-313">Linux Mint</span></span>                     |  <span data-ttu-id="845b3-314">17、18</span><span class="sxs-lookup"><span data-stu-id="845b3-314">17, 18</span></span>                 | <span data-ttu-id="845b3-315">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-315">x64</span></span> |
| <span data-ttu-id="845b3-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="845b3-316">openSUSE</span></span>                       |  <span data-ttu-id="845b3-317">15 +</span><span class="sxs-lookup"><span data-stu-id="845b3-317">15+</span></span>                    | <span data-ttu-id="845b3-318">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-318">x64</span></span> |
| <span data-ttu-id="845b3-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="845b3-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="845b3-320">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="845b3-320">12 SP2+</span></span>                | <span data-ttu-id="845b3-321">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-321">x64</span></span> |
| <span data-ttu-id="845b3-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-322">Alpine Linux</span></span>                   |  <span data-ttu-id="845b3-323">3.8+</span><span class="sxs-lookup"><span data-stu-id="845b3-323">3.8+</span></span>                   | <span data-ttu-id="845b3-324">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-324">x64</span></span> |

<span data-ttu-id="845b3-325">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="845b3-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="845b3-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="845b3-327">.NET Core 2.1 將 Linux 視為單一作業系統。</span><span class="sxs-lookup"><span data-stu-id="845b3-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="845b3-328">針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。</span><span class="sxs-lookup"><span data-stu-id="845b3-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="845b3-329">下列 Linux 發行版本/版本支援 .NET Core 2.1：</span><span class="sxs-lookup"><span data-stu-id="845b3-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-330">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-331">OS</span><span class="sxs-lookup"><span data-stu-id="845b3-331">OS</span></span>                             |  <span data-ttu-id="845b3-332">版本</span><span class="sxs-lookup"><span data-stu-id="845b3-332">Version</span></span>                |  <span data-ttu-id="845b3-333">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="845b3-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="845b3-335">6、7、8</span><span class="sxs-lookup"><span data-stu-id="845b3-335">6, 7, 8</span></span>                | <span data-ttu-id="845b3-336">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-336">x64</span></span> |
| <span data-ttu-id="845b3-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="845b3-337">CentOS</span></span>                         |  <span data-ttu-id="845b3-338">7+</span><span class="sxs-lookup"><span data-stu-id="845b3-338">7+</span></span>                     | <span data-ttu-id="845b3-339">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-339">x64</span></span> |
| <span data-ttu-id="845b3-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-340">Oracle Linux</span></span>                   |  <span data-ttu-id="845b3-341">7+</span><span class="sxs-lookup"><span data-stu-id="845b3-341">7+</span></span>                     | <span data-ttu-id="845b3-342">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-342">x64</span></span> |
| <span data-ttu-id="845b3-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="845b3-343">Fedora</span></span>                         |  <span data-ttu-id="845b3-344">30 +</span><span class="sxs-lookup"><span data-stu-id="845b3-344">30+</span></span>                    | <span data-ttu-id="845b3-345">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-345">x64</span></span> |
| <span data-ttu-id="845b3-346">Debian</span><span class="sxs-lookup"><span data-stu-id="845b3-346">Debian</span></span>                         |  <span data-ttu-id="845b3-347">9</span><span class="sxs-lookup"><span data-stu-id="845b3-347">9</span></span>                      | <span data-ttu-id="845b3-348">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="845b3-348">x64, ARM32</span></span> |
| <span data-ttu-id="845b3-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="845b3-349">Ubuntu</span></span>                         |  <span data-ttu-id="845b3-350">16.04、18.04、19.04、19.10</span><span class="sxs-lookup"><span data-stu-id="845b3-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="845b3-351">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="845b3-351">x64, ARM32</span></span> |
| <span data-ttu-id="845b3-352">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="845b3-352">Linux Mint</span></span>                     |  <span data-ttu-id="845b3-353">17+</span><span class="sxs-lookup"><span data-stu-id="845b3-353">17+</span></span>                    | <span data-ttu-id="845b3-354">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-354">x64</span></span> |
| <span data-ttu-id="845b3-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="845b3-355">openSUSE</span></span>                       |  <span data-ttu-id="845b3-356">15 +</span><span class="sxs-lookup"><span data-stu-id="845b3-356">15+</span></span>                    | <span data-ttu-id="845b3-357">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-357">x64</span></span> |
| <span data-ttu-id="845b3-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="845b3-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="845b3-359">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="845b3-359">12 SP2+</span></span>                | <span data-ttu-id="845b3-360">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-360">x64</span></span> |
| <span data-ttu-id="845b3-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="845b3-361">Alpine Linux</span></span>                   |  <span data-ttu-id="845b3-362">3.8+</span><span class="sxs-lookup"><span data-stu-id="845b3-362">3.8+</span></span>                   | <span data-ttu-id="845b3-363">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-363">x64</span></span> |

<span data-ttu-id="845b3-364">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="845b3-365">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="845b3-365">Linux distribution dependencies</span></span>

<span data-ttu-id="845b3-366">根據您的 linux 散發套件，您可能需要安裝其他相依性。</span><span class="sxs-lookup"><span data-stu-id="845b3-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="845b3-367">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="845b3-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="845b3-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="845b3-368">Ubuntu</span></span>

<span data-ttu-id="845b3-369">Ubuntu 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="845b3-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="845b3-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="845b3-370">liblttng-ust0</span></span>
- <span data-ttu-id="845b3-371">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="845b3-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="845b3-372">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="845b3-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="845b3-373">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="845b3-373">libssl1.0.0</span></span>
- <span data-ttu-id="845b3-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="845b3-374">libkrb5-3</span></span>
- <span data-ttu-id="845b3-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="845b3-375">zlib1g</span></span>
- <span data-ttu-id="845b3-376">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="845b3-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="845b3-377">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="845b3-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="845b3-378">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="845b3-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="845b3-379">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="845b3-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="845b3-380">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="845b3-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="845b3-381">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="845b3-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="845b3-382">最新版的 Ubuntu 包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="845b3-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="845b3-383">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="845b3-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="845b3-384">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="845b3-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="845b3-385">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="845b3-385">CentOS and Fedora</span></span>

<span data-ttu-id="845b3-386">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="845b3-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="845b3-387">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="845b3-387">lttng-ust</span></span>
- <span data-ttu-id="845b3-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="845b3-388">libcurl</span></span>
- <span data-ttu-id="845b3-389">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="845b3-389">openssl-libs</span></span>
- <span data-ttu-id="845b3-390">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="845b3-390">krb5-libs</span></span>
- <span data-ttu-id="845b3-391">libicu</span><span class="sxs-lookup"><span data-stu-id="845b3-391">libicu</span></span>
- <span data-ttu-id="845b3-392">zlib</span><span class="sxs-lookup"><span data-stu-id="845b3-392">zlib</span></span>

<span data-ttu-id="845b3-393">Fedora 使用者：如果您的 OpenSSL 版本 >= 1.1，您必須安裝相容性 **-compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="845b3-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="845b3-394">針對 .NET Core 2.0，也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="845b3-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="845b3-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="845b3-395">libunwind</span></span>
- <span data-ttu-id="845b3-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="845b3-396">libuuid</span></span>

<span data-ttu-id="845b3-397">如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="845b3-398">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="845b3-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="845b3-399">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="845b3-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="845b3-400">大部分的 CentOS 和 Fedora 版本都包含舊版的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="845b3-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="845b3-401">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="845b3-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="845b3-402">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="845b3-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="alpine"></a><span data-ttu-id="845b3-403">Alpine</span><span class="sxs-lookup"><span data-stu-id="845b3-403">Alpine</span></span>

<span data-ttu-id="845b3-404">Alpine 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="845b3-404">Alpine distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="845b3-405">icu-程式庫（如果停用全球化則不需要此功能）</span><span class="sxs-lookup"><span data-stu-id="845b3-405">icu-libs (this is not needed if globalization is disabled)</span></span>
- <span data-ttu-id="845b3-406">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="845b3-406">krb5-libs</span></span>
- <span data-ttu-id="845b3-407">libcurl</span><span class="sxs-lookup"><span data-stu-id="845b3-407">libcurl</span></span>
- <span data-ttu-id="845b3-408">libintl</span><span class="sxs-lookup"><span data-stu-id="845b3-408">libintl</span></span>
- <span data-ttu-id="845b3-409">libssl1.0.0 1.1 （適用于 Alpine 3.9 或更新版本）或 libssl1.0.0 1.0 （適用于舊版）</span><span class="sxs-lookup"><span data-stu-id="845b3-409">libssl1.1 (for Alpine 3.9 or later) or libssl1.0 (for older ones)</span></span>
- <span data-ttu-id="845b3-410">libstdc++</span><span class="sxs-lookup"><span data-stu-id="845b3-410">libstdc++</span></span>
- <span data-ttu-id="845b3-411">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="845b3-411">lttng-ust</span></span>
- <span data-ttu-id="845b3-412">numactl （選擇性，僅適用于已啟用 NUMA 的裝置）</span><span class="sxs-lookup"><span data-stu-id="845b3-412">numactl (optional, useful only for devices with NUMA enabled)</span></span>
- <span data-ttu-id="845b3-413">zlib</span><span class="sxs-lookup"><span data-stu-id="845b3-413">zlib</span></span>

<span data-ttu-id="845b3-414">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="845b3-414">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="845b3-415">libgdiplus （僅適用于 edge/測試存放庫）</span><span class="sxs-lookup"><span data-stu-id="845b3-415">libgdiplus (it is available only in the edge/testing repository)</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="845b3-416">下列 macOS 版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="845b3-416">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="845b3-417">代表`+`最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="845b3-417">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="845b3-418">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="845b3-418">.NET Core Version</span></span> | <span data-ttu-id="845b3-419">macOS</span><span class="sxs-lookup"><span data-stu-id="845b3-419">macOS</span></span>                 | <span data-ttu-id="845b3-420">架構</span><span class="sxs-lookup"><span data-stu-id="845b3-420">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="845b3-421">3.1</span><span class="sxs-lookup"><span data-stu-id="845b3-421">3.1</span></span>               | <span data-ttu-id="845b3-422">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="845b3-422">High Sierra (10.13+)</span></span>  | <span data-ttu-id="845b3-423">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-423">x64</span></span> | [<span data-ttu-id="845b3-424">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="845b3-424">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="845b3-425">3.0</span><span class="sxs-lookup"><span data-stu-id="845b3-425">3.0</span></span>               | <span data-ttu-id="845b3-426">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="845b3-426">High Sierra (10.13+)</span></span>  | <span data-ttu-id="845b3-427">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-427">x64</span></span> | [<span data-ttu-id="845b3-428">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="845b3-428">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="845b3-429">2.2</span><span class="sxs-lookup"><span data-stu-id="845b3-429">2.2</span></span>               | <span data-ttu-id="845b3-430">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="845b3-430">Sierra (10.12+)</span></span>       | <span data-ttu-id="845b3-431">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-431">x64</span></span> | [<span data-ttu-id="845b3-432">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="845b3-432">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="845b3-433">2.1</span><span class="sxs-lookup"><span data-stu-id="845b3-433">2.1</span></span>               | <span data-ttu-id="845b3-434">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="845b3-434">Sierra (10.12+)</span></span>       | <span data-ttu-id="845b3-435">x64</span><span class="sxs-lookup"><span data-stu-id="845b3-435">x64</span></span> | [<span data-ttu-id="845b3-436">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="845b3-436">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="845b3-437">從 macOS Catalina （版本10.15）開始，在2019年6月1日之後以開發人員識別碼散發的所有軟體都必須是公證。</span><span class="sxs-lookup"><span data-stu-id="845b3-437">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="845b3-438">這項需求適用于 .NET core 執行時間、.NET Core SDK 和使用 .NET Core 所建立的軟體。</span><span class="sxs-lookup"><span data-stu-id="845b3-438">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="845b3-439">從2020年2月18日起，已公證 .NET Core （執行時間和 SDK）版本3.1、3.0 和2.1 的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="845b3-439">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="845b3-440">先前發行的版本不會公證。</span><span class="sxs-lookup"><span data-stu-id="845b3-440">Prior released versions aren't notarized.</span></span> <span data-ttu-id="845b3-441">如果您執行非公證應用程式，您會看到類似下圖的錯誤：</span><span class="sxs-lookup"><span data-stu-id="845b3-441">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notarization 警示](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="845b3-443">如需強制執行 notarization 如何影響 .NET Core （和您的 .NET Core 應用程式）的詳細資訊，請參閱[使用 MacOS Catalina notarization](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="845b3-443">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="845b3-444">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="845b3-444">libgdiplus</span></span>

<span data-ttu-id="845b3-445">使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="845b3-445">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="845b3-446">取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。</span><span class="sxs-lookup"><span data-stu-id="845b3-446">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="845b3-447">安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="845b3-447">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="845b3-448">後續步驟</span><span class="sxs-lookup"><span data-stu-id="845b3-448">Next steps</span></span>

- <span data-ttu-id="845b3-449">若要開發及執行應用程式，請安裝[.NET Core SDK](sdk.md) （包括執行時間）。</span><span class="sxs-lookup"><span data-stu-id="845b3-449">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="845b3-450">若要執行其他人已建立的應用程式，請安裝[.Net Core 運行](runtime.md)時間。</span><span class="sxs-lookup"><span data-stu-id="845b3-450">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
