---
title: .NET 核心 SDK 和運行時依賴項 - .NET 核心
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET 核心 SDK 的作業系統和 CPU 體系結構先決條件。
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157802"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="fa8d2-103">.NET 核心依賴關係和要求</span><span class="sxs-lookup"><span data-stu-id="fa8d2-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="fa8d2-104">本文詳細介紹了 .NET Core 支援哪些作業系統和 CPU 體系結構。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="fa8d2-105">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="fa8d2-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="fa8d2-106">.NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="fa8d2-107">.NET Core 3.1 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-108">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-109">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-109">OS</span></span>                            | <span data-ttu-id="fa8d2-110">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-110">Version</span></span>                        | <span data-ttu-id="fa8d2-111">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fa8d2-112">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-112">Windows Client</span></span>                | <span data-ttu-id="fa8d2-113">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fa8d2-114">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-114">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-115">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-115">Windows 10 Client</span></span>             | <span data-ttu-id="fa8d2-116">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-116">Version 1607+</span></span>                  | <span data-ttu-id="fa8d2-117">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-117">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-118">Windows Server</span></span>                | <span data-ttu-id="fa8d2-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-119">2012 R2+</span></span>                       | <span data-ttu-id="fa8d2-120">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-120">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-121">Nano Server</span></span>                   | <span data-ttu-id="fa8d2-122">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-122">Version 1803+</span></span>                  | <span data-ttu-id="fa8d2-123">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="fa8d2-123">x64, ARM32</span></span>      |

<span data-ttu-id="fa8d2-124">有關 .NET Core 3.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="fa8d2-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fa8d2-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="fa8d2-126">.NET Core 3.0 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-127">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-128">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-128">OS</span></span>                            | <span data-ttu-id="fa8d2-129">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-129">Version</span></span>                        | <span data-ttu-id="fa8d2-130">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fa8d2-131">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-131">Windows Client</span></span>                | <span data-ttu-id="fa8d2-132">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fa8d2-133">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-133">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-134">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-134">Windows 10 Client</span></span>             | <span data-ttu-id="fa8d2-135">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-135">Version 1607+</span></span>                  | <span data-ttu-id="fa8d2-136">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-136">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-137">Windows Server</span></span>                | <span data-ttu-id="fa8d2-138">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-138">2012 R2+</span></span>                       | <span data-ttu-id="fa8d2-139">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-139">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-140">Nano Server</span></span>                   | <span data-ttu-id="fa8d2-141">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-141">Version 1803+</span></span>                  | <span data-ttu-id="fa8d2-142">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="fa8d2-142">x64, ARM32</span></span>      |

<span data-ttu-id="fa8d2-143">有關 .NET Core 3.0 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="fa8d2-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="fa8d2-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="fa8d2-145">.NET Core 2.2 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-146">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-147">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-147">OS</span></span>                            | <span data-ttu-id="fa8d2-148">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-148">Version</span></span>                        | <span data-ttu-id="fa8d2-149">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fa8d2-150">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-150">Windows Client</span></span>                | <span data-ttu-id="fa8d2-151">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fa8d2-152">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-152">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-153">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-153">Windows 10 Client</span></span>             | <span data-ttu-id="fa8d2-154">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-154">Version 1607+</span></span>                  | <span data-ttu-id="fa8d2-155">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-155">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-156">Windows Server</span></span>                | <span data-ttu-id="fa8d2-157">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="fa8d2-158">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-158">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-159">Nano Server</span></span>                   | <span data-ttu-id="fa8d2-160">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-160">Version 1803+</span></span>                   | <span data-ttu-id="fa8d2-161">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="fa8d2-161">x64, ARM32</span></span>      |

<span data-ttu-id="fa8d2-162">有關 .NET Core 2.2 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="fa8d2-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fa8d2-164">.NET Core 2.1 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-165">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-166">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-166">OS</span></span>                            | <span data-ttu-id="fa8d2-167">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-167">Version</span></span>                        | <span data-ttu-id="fa8d2-168">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fa8d2-169">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-169">Windows Client</span></span>                | <span data-ttu-id="fa8d2-170">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fa8d2-171">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-171">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-172">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="fa8d2-172">Windows 10 Client</span></span>             | <span data-ttu-id="fa8d2-173">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-173">Version 1607+</span></span>                  | <span data-ttu-id="fa8d2-174">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-174">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-175">Windows Server</span></span>                | <span data-ttu-id="fa8d2-176">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="fa8d2-177">x64、x86</span><span class="sxs-lookup"><span data-stu-id="fa8d2-177">x64, x86</span></span>        |
| <span data-ttu-id="fa8d2-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="fa8d2-178">Nano Server</span></span>                   | <span data-ttu-id="fa8d2-179">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-179">Version 1803+</span></span>                  | <span data-ttu-id="fa8d2-180">x64，</span><span class="sxs-lookup"><span data-stu-id="fa8d2-180">x64,</span></span>            |

<span data-ttu-id="fa8d2-181">有關 .NET Core 2.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="fa8d2-182">視窗 7 / Vista / 8.1 / 伺服器 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fa8d2-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="fa8d2-183">如果要在以下 Windows 版本上安裝 .NET SDK 或運行時，則需要其他依賴項：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="fa8d2-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-184">Windows 7 SP1</span></span>
- <span data-ttu-id="fa8d2-185">視窗 Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="fa8d2-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="fa8d2-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-186">Windows 8.1</span></span>
- <span data-ttu-id="fa8d2-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fa8d2-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="fa8d2-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fa8d2-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="fa8d2-189">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-189">Install the following:</span></span>

- <span data-ttu-id="fa8d2-190">[微軟視覺C++ 2015 可轉散布更新 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="fa8d2-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="fa8d2-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="fa8d2-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="fa8d2-192">如果您遇到以下錯誤之一，還需要上述要求：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="fa8d2-193">無法啟動該程式，因為您的電腦中缺少*api-ms-win-cr-runtime-l1-1-0.dll。*</span><span class="sxs-lookup"><span data-stu-id="fa8d2-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="fa8d2-194">請嘗試重新安裝程式以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="fa8d2-195">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="fa8d2-195">\- or -</span></span>
>
> <span data-ttu-id="fa8d2-196">找到庫*hostfxr.dll，* 但從*C：path_to_app\\\<載入\\>主機fxr.dll*失敗。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="fa8d2-197">.NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="fa8d2-198">.NET Core 3.1 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="fa8d2-199">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fa8d2-200">.NET Core 3.1 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-201">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-202">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-202">OS</span></span>                             | <span data-ttu-id="fa8d2-203">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-203">Version</span></span>               | <span data-ttu-id="fa8d2-204">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="fa8d2-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="fa8d2-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="fa8d2-206">6, 7, 8</span></span>               | <span data-ttu-id="fa8d2-207">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-207">x64</span></span> |
| <span data-ttu-id="fa8d2-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-208">CentOS</span></span>                         | <span data-ttu-id="fa8d2-209">7+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-209">7+</span></span>                    | <span data-ttu-id="fa8d2-210">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-210">x64</span></span> |
| <span data-ttu-id="fa8d2-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-211">Oracle Linux</span></span>                   | <span data-ttu-id="fa8d2-212">7+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-212">7+</span></span>                    | <span data-ttu-id="fa8d2-213">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-213">x64</span></span> |
| <span data-ttu-id="fa8d2-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="fa8d2-214">Fedora</span></span>                         | <span data-ttu-id="fa8d2-215">29°</span><span class="sxs-lookup"><span data-stu-id="fa8d2-215">29+</span></span>                   | <span data-ttu-id="fa8d2-216">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-216">x64</span></span> |
| <span data-ttu-id="fa8d2-217">Debian</span><span class="sxs-lookup"><span data-stu-id="fa8d2-217">Debian</span></span>                         | <span data-ttu-id="fa8d2-218">9+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-218">9+</span></span>                    | <span data-ttu-id="fa8d2-219">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fa8d2-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fa8d2-220">Ubuntu</span></span>                         | <span data-ttu-id="fa8d2-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-221">16.04+</span></span>                | <span data-ttu-id="fa8d2-222">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fa8d2-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="fa8d2-223">Linux Mint</span></span>                     | <span data-ttu-id="fa8d2-224">18€</span><span class="sxs-lookup"><span data-stu-id="fa8d2-224">18+</span></span>                   | <span data-ttu-id="fa8d2-225">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-225">x64</span></span> |
| <span data-ttu-id="fa8d2-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fa8d2-226">openSUSE</span></span>                       | <span data-ttu-id="fa8d2-227">15€</span><span class="sxs-lookup"><span data-stu-id="fa8d2-227">15+</span></span>                   | <span data-ttu-id="fa8d2-228">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-228">x64</span></span> |
| <span data-ttu-id="fa8d2-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="fa8d2-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-230">12 SP2+</span></span>               | <span data-ttu-id="fa8d2-231">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-231">x64</span></span> |
| <span data-ttu-id="fa8d2-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-232">Alpine Linux</span></span>                   | <span data-ttu-id="fa8d2-233">3.10°</span><span class="sxs-lookup"><span data-stu-id="fa8d2-233">3.10+</span></span>                 | <span data-ttu-id="fa8d2-234">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-234">x64, ARM64</span></span> |

<span data-ttu-id="fa8d2-235">有關 .NET Core 3.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="fa8d2-236">有關如何在 ARM64（內核 4.14+）上安裝 .NET 酷睿 3.1 的詳細資訊，請參閱[在 Linux ARM64 上安裝 .NET 核心 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa8d2-237">ARM64 支援需要 Linux 內核 4.14 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="fa8d2-238">某些 linux 發行版本滿足此要求，而其他發行版本則不滿足此要求。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="fa8d2-239">例如，Ubuntu 18.04 受支援，但 Ubuntu 16.04 不支援。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="fa8d2-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fa8d2-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="fa8d2-241">.NET Core 3.0 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="fa8d2-242">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fa8d2-243">.NET Core 3.0 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-244">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-245">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-245">OS</span></span>                             | <span data-ttu-id="fa8d2-246">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-246">Version</span></span>               | <span data-ttu-id="fa8d2-247">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="fa8d2-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="fa8d2-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="fa8d2-249">6, 7, 8</span></span>               | <span data-ttu-id="fa8d2-250">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-250">x64</span></span> |
| <span data-ttu-id="fa8d2-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-251">CentOS</span></span>                         | <span data-ttu-id="fa8d2-252">7+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-252">7+</span></span>                    | <span data-ttu-id="fa8d2-253">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-253">x64</span></span> |
| <span data-ttu-id="fa8d2-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-254">Oracle Linux</span></span>                   | <span data-ttu-id="fa8d2-255">7+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-255">7+</span></span>                    | <span data-ttu-id="fa8d2-256">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-256">x64</span></span> |
| <span data-ttu-id="fa8d2-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="fa8d2-257">Fedora</span></span>                         | <span data-ttu-id="fa8d2-258">29°</span><span class="sxs-lookup"><span data-stu-id="fa8d2-258">29+</span></span>                   | <span data-ttu-id="fa8d2-259">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-259">x64</span></span> |
| <span data-ttu-id="fa8d2-260">Debian</span><span class="sxs-lookup"><span data-stu-id="fa8d2-260">Debian</span></span>                         | <span data-ttu-id="fa8d2-261">9+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-261">9+</span></span>                    | <span data-ttu-id="fa8d2-262">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fa8d2-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fa8d2-263">Ubuntu</span></span>                         | <span data-ttu-id="fa8d2-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-264">16.04+</span></span>                | <span data-ttu-id="fa8d2-265">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fa8d2-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="fa8d2-266">Linux Mint</span></span>                     | <span data-ttu-id="fa8d2-267">18€</span><span class="sxs-lookup"><span data-stu-id="fa8d2-267">18+</span></span>                   | <span data-ttu-id="fa8d2-268">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-268">x64</span></span> |
| <span data-ttu-id="fa8d2-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fa8d2-269">openSUSE</span></span>                       | <span data-ttu-id="fa8d2-270">15€</span><span class="sxs-lookup"><span data-stu-id="fa8d2-270">15+</span></span>                   | <span data-ttu-id="fa8d2-271">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-271">x64</span></span> |
| <span data-ttu-id="fa8d2-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="fa8d2-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-273">12 SP2+</span></span>               | <span data-ttu-id="fa8d2-274">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-274">x64</span></span> |
| <span data-ttu-id="fa8d2-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-275">Alpine Linux</span></span>                   | <span data-ttu-id="fa8d2-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-276">3.8+</span></span>                  | <span data-ttu-id="fa8d2-277">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-277">x64, ARM64</span></span> |

<span data-ttu-id="fa8d2-278">有關 .NET Core 3.0 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="fa8d2-279">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="fa8d2-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="fa8d2-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="fa8d2-281">.NET Core 2.2 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="fa8d2-282">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fa8d2-283">.NET Core 2.2 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-284">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-285">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-285">OS</span></span>                             |  <span data-ttu-id="fa8d2-286">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-286">Version</span></span>                |  <span data-ttu-id="fa8d2-287">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="fa8d2-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="fa8d2-289">6、7</span><span class="sxs-lookup"><span data-stu-id="fa8d2-289">6, 7</span></span>                   | <span data-ttu-id="fa8d2-290">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-290">x64</span></span> |
| <span data-ttu-id="fa8d2-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-291">CentOS</span></span>                         |  <span data-ttu-id="fa8d2-292">7</span><span class="sxs-lookup"><span data-stu-id="fa8d2-292">7</span></span>                      | <span data-ttu-id="fa8d2-293">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-293">x64</span></span> |
| <span data-ttu-id="fa8d2-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-294">Oracle Linux</span></span>                   |  <span data-ttu-id="fa8d2-295">7</span><span class="sxs-lookup"><span data-stu-id="fa8d2-295">7</span></span>                      | <span data-ttu-id="fa8d2-296">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-296">x64</span></span> |
| <span data-ttu-id="fa8d2-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="fa8d2-297">Fedora</span></span>                         |  <span data-ttu-id="fa8d2-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="fa8d2-298">29, 30</span></span>                 | <span data-ttu-id="fa8d2-299">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-299">x64</span></span> |
| <span data-ttu-id="fa8d2-300">Debian</span><span class="sxs-lookup"><span data-stu-id="fa8d2-300">Debian</span></span>                         |  <span data-ttu-id="fa8d2-301">9</span><span class="sxs-lookup"><span data-stu-id="fa8d2-301">9</span></span>                      | <span data-ttu-id="fa8d2-302">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="fa8d2-302">x64, ARM32</span></span> |
| <span data-ttu-id="fa8d2-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fa8d2-303">Ubuntu</span></span>                         |  <span data-ttu-id="fa8d2-304">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="fa8d2-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="fa8d2-305">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="fa8d2-305">x64, ARM32</span></span> |
| <span data-ttu-id="fa8d2-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="fa8d2-306">Linux Mint</span></span>                     |  <span data-ttu-id="fa8d2-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="fa8d2-307">17, 18</span></span>                 | <span data-ttu-id="fa8d2-308">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-308">x64</span></span> |
| <span data-ttu-id="fa8d2-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fa8d2-309">openSUSE</span></span>                       |  <span data-ttu-id="fa8d2-310">15€</span><span class="sxs-lookup"><span data-stu-id="fa8d2-310">15+</span></span>                    | <span data-ttu-id="fa8d2-311">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-311">x64</span></span> |
| <span data-ttu-id="fa8d2-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="fa8d2-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-313">12 SP2+</span></span>                | <span data-ttu-id="fa8d2-314">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-314">x64</span></span> |
| <span data-ttu-id="fa8d2-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-315">Alpine Linux</span></span>                   |  <span data-ttu-id="fa8d2-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-316">3.8+</span></span>                   | <span data-ttu-id="fa8d2-317">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-317">x64</span></span> |

<span data-ttu-id="fa8d2-318">有關 .NET Core 2.2 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="fa8d2-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fa8d2-320">.NET Core 2.1 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="fa8d2-321">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fa8d2-322">.NET Core 2.1 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-323">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-324">OS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-324">OS</span></span>                             |  <span data-ttu-id="fa8d2-325">版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-325">Version</span></span>                |  <span data-ttu-id="fa8d2-326">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="fa8d2-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="fa8d2-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="fa8d2-328">6, 7, 8</span></span>                | <span data-ttu-id="fa8d2-329">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-329">x64</span></span> |
| <span data-ttu-id="fa8d2-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-330">CentOS</span></span>                         |  <span data-ttu-id="fa8d2-331">7+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-331">7+</span></span>                     | <span data-ttu-id="fa8d2-332">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-332">x64</span></span> |
| <span data-ttu-id="fa8d2-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-333">Oracle Linux</span></span>                   |  <span data-ttu-id="fa8d2-334">7+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-334">7+</span></span>                     | <span data-ttu-id="fa8d2-335">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-335">x64</span></span> |
| <span data-ttu-id="fa8d2-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="fa8d2-336">Fedora</span></span>                         |  <span data-ttu-id="fa8d2-337">29°</span><span class="sxs-lookup"><span data-stu-id="fa8d2-337">29+</span></span>                    | <span data-ttu-id="fa8d2-338">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-338">x64</span></span> |
| <span data-ttu-id="fa8d2-339">Debian</span><span class="sxs-lookup"><span data-stu-id="fa8d2-339">Debian</span></span>                         |  <span data-ttu-id="fa8d2-340">9</span><span class="sxs-lookup"><span data-stu-id="fa8d2-340">9</span></span>                      | <span data-ttu-id="fa8d2-341">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="fa8d2-341">x64, ARM32</span></span> |
| <span data-ttu-id="fa8d2-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fa8d2-342">Ubuntu</span></span>                         |  <span data-ttu-id="fa8d2-343">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="fa8d2-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="fa8d2-344">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="fa8d2-344">x64, ARM32</span></span> |
| <span data-ttu-id="fa8d2-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="fa8d2-345">Linux Mint</span></span>                     |  <span data-ttu-id="fa8d2-346">17+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-346">17+</span></span>                    | <span data-ttu-id="fa8d2-347">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-347">x64</span></span> |
| <span data-ttu-id="fa8d2-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fa8d2-348">openSUSE</span></span>                       |  <span data-ttu-id="fa8d2-349">15€</span><span class="sxs-lookup"><span data-stu-id="fa8d2-349">15+</span></span>                    | <span data-ttu-id="fa8d2-350">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-350">x64</span></span> |
| <span data-ttu-id="fa8d2-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="fa8d2-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-352">12 SP2+</span></span>                | <span data-ttu-id="fa8d2-353">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-353">x64</span></span> |
| <span data-ttu-id="fa8d2-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fa8d2-354">Alpine Linux</span></span>                   |  <span data-ttu-id="fa8d2-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="fa8d2-355">3.8+</span></span>                   | <span data-ttu-id="fa8d2-356">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-356">x64</span></span> |

<span data-ttu-id="fa8d2-357">有關 .NET Core 2.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="fa8d2-358">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="fa8d2-358">Linux distribution dependencies</span></span>

<span data-ttu-id="fa8d2-359">根據您的 linux 發行版本，您可能需要安裝其他依賴項。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa8d2-360">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="fa8d2-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fa8d2-361">Ubuntu</span></span>

<span data-ttu-id="fa8d2-362">Ubuntu 分發需要安裝以下庫：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="fa8d2-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="fa8d2-363">liblttng-ust0</span></span>
- <span data-ttu-id="fa8d2-364">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="fa8d2-365">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="fa8d2-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="fa8d2-366">libssl1.0.0</span></span>
- <span data-ttu-id="fa8d2-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="fa8d2-367">libkrb5-3</span></span>
- <span data-ttu-id="fa8d2-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="fa8d2-368">zlib1g</span></span>
- <span data-ttu-id="fa8d2-369">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="fa8d2-370">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="fa8d2-371">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="fa8d2-372">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="fa8d2-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="fa8d2-373">對於使用*System.Drawing.Common*程式集的 .NET Core 應用，您還需要以下依賴項：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="fa8d2-374">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="fa8d2-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="fa8d2-375">大多數版本的Ubuntu包括早期版本的libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="fa8d2-376">您可以通過將 Mono 存儲庫添加到系統來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="fa8d2-377">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="fa8d2-378">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="fa8d2-378">CentOS and Fedora</span></span>

<span data-ttu-id="fa8d2-379">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="fa8d2-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="fa8d2-380">lttng-ust</span></span>
- <span data-ttu-id="fa8d2-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="fa8d2-381">libcurl</span></span>
- <span data-ttu-id="fa8d2-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="fa8d2-382">openssl-libs</span></span>
- <span data-ttu-id="fa8d2-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="fa8d2-383">krb5-libs</span></span>
- <span data-ttu-id="fa8d2-384">libicu</span><span class="sxs-lookup"><span data-stu-id="fa8d2-384">libicu</span></span>
- <span data-ttu-id="fa8d2-385">zlib</span><span class="sxs-lookup"><span data-stu-id="fa8d2-385">zlib</span></span>

<span data-ttu-id="fa8d2-386">Fedora 使用者：如果您的 OpenSSL 版本>= 1.1，則需要安裝相容**openssl10**。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="fa8d2-387">對於 .NET Core 2.0，還需要以下依賴項：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="fa8d2-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="fa8d2-388">libunwind</span></span>
- <span data-ttu-id="fa8d2-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="fa8d2-389">libuuid</span></span>

<span data-ttu-id="fa8d2-390">有關依賴項的詳細資訊，請參閱[自包含的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="fa8d2-391">對於使用*System.Drawing.Common*程式集的 .NET Core 應用，您還需要以下依賴項：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="fa8d2-392">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="fa8d2-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="fa8d2-393">CentOS 和 Fedora 的大多數版本都包括早期版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="fa8d2-394">您可以通過將 Mono 存儲庫添加到系統來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="fa8d2-395">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="fa8d2-396">.NET 核心支援以下 macOS 版本：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d2-397">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fa8d2-398">.NET 核心版本</span><span class="sxs-lookup"><span data-stu-id="fa8d2-398">.NET Core Version</span></span> | <span data-ttu-id="fa8d2-399">macOS</span><span class="sxs-lookup"><span data-stu-id="fa8d2-399">macOS</span></span>                 | <span data-ttu-id="fa8d2-400">架構</span><span class="sxs-lookup"><span data-stu-id="fa8d2-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="fa8d2-401">3.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-401">3.1</span></span>               | <span data-ttu-id="fa8d2-402">高塞拉 （10.13+）</span><span class="sxs-lookup"><span data-stu-id="fa8d2-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="fa8d2-403">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-403">x64</span></span> | [<span data-ttu-id="fa8d2-404">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="fa8d2-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="fa8d2-405">3.0</span><span class="sxs-lookup"><span data-stu-id="fa8d2-405">3.0</span></span>               | <span data-ttu-id="fa8d2-406">高塞拉 （10.13+）</span><span class="sxs-lookup"><span data-stu-id="fa8d2-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="fa8d2-407">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-407">x64</span></span> | [<span data-ttu-id="fa8d2-408">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="fa8d2-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="fa8d2-409">2.2</span><span class="sxs-lookup"><span data-stu-id="fa8d2-409">2.2</span></span>               | <span data-ttu-id="fa8d2-410">塞拉 （10.12+）</span><span class="sxs-lookup"><span data-stu-id="fa8d2-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="fa8d2-411">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-411">x64</span></span> | [<span data-ttu-id="fa8d2-412">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="fa8d2-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="fa8d2-413">2.1</span><span class="sxs-lookup"><span data-stu-id="fa8d2-413">2.1</span></span>               | <span data-ttu-id="fa8d2-414">塞拉 （10.12+）</span><span class="sxs-lookup"><span data-stu-id="fa8d2-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="fa8d2-415">x64</span><span class="sxs-lookup"><span data-stu-id="fa8d2-415">x64</span></span> | [<span data-ttu-id="fa8d2-416">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="fa8d2-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="fa8d2-417">從 macOS Catalina（版本 10.15）開始，所有 2019 年 6 月 1 日之後構建的所有軟體都必須使用開發人員 ID 進行公證。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="fa8d2-418">此要求適用于 .NET 核心運行時、.NET 核心 SDK 和使用 .NET Core 創建的軟體。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="fa8d2-419">自 2020 年 2 月 18 日起，對 .NET Core（運行時和 SDK）版本 3.1、3.0 和 2.1 的安裝程式進行了公證。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="fa8d2-420">未對以前發佈的版本進行公證。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="fa8d2-421">如果運行非公證應用，您將看到類似于下圖的錯誤：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS 卡塔利娜公證警報](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="fa8d2-423">有關強制公證如何影響 .NET Core（和 .NET 核心應用）的詳細資訊，請參閱使用[macOS Catalina 公證](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="fa8d2-424">利格迪加</span><span class="sxs-lookup"><span data-stu-id="fa8d2-424">libgdiplus</span></span>

<span data-ttu-id="fa8d2-425">.NET 核心應用程式，使用*系統.繪圖.公共*程式集需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="fa8d2-426">獲得 libgdiplus 的一種簡單方法是使用[macOS 的自製啤酒（"釀造"）](https://brew.sh/)包管理器。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="fa8d2-427">安裝*沖煮*後，通過在終端（命令）提示符上執行以下命令來安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="fa8d2-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="fa8d2-428">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fa8d2-428">Next steps</span></span>

- <span data-ttu-id="fa8d2-429">要開發和運行應用，請安裝[.NET 核心 SDK（](sdk.md)包括運行時）。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="fa8d2-430">要運行其他人創建的應用，請安裝[.NET Core 運行時](runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d2-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
