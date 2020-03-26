---
title: .NET 核心 SDK 和運行時依賴項 - .NET 核心
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET 核心 SDK 的作業系統和 CPU 體系結構先決條件。
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 023b8fdf029dd6b17fe2186296d87dd7507c60b5
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546558"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="a40f4-103">.NET 核心依賴關係和要求</span><span class="sxs-lookup"><span data-stu-id="a40f4-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="a40f4-104">本文詳細介紹了 .NET Core 支援哪些作業系統和 CPU 體系結構。</span><span class="sxs-lookup"><span data-stu-id="a40f4-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="a40f4-105">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="a40f4-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="a40f4-106">.NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="a40f4-107">.NET Core 3.1 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-108">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-109">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-109">OS</span></span>                            | <span data-ttu-id="a40f4-110">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-110">Version</span></span>                        | <span data-ttu-id="a40f4-111">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a40f4-112">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-112">Windows Client</span></span>                | <span data-ttu-id="a40f4-113">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a40f4-114">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-114">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-115">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-115">Windows 10 Client</span></span>             | <span data-ttu-id="a40f4-116">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-116">Version 1607+</span></span>                  | <span data-ttu-id="a40f4-117">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-117">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-118">Windows Server</span></span>                | <span data-ttu-id="a40f4-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="a40f4-119">2012 R2+</span></span>                       | <span data-ttu-id="a40f4-120">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-120">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-121">Nano Server</span></span>                   | <span data-ttu-id="a40f4-122">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-122">Version 1803+</span></span>                  | <span data-ttu-id="a40f4-123">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="a40f4-123">x64, ARM32</span></span>      |

<span data-ttu-id="a40f4-124">有關 .NET Core 3.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="a40f4-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a40f4-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="a40f4-126">*.NET 核心 3.0 當前已無支援。有關詳細資訊，請參閱[.NET 核心支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="a40f4-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="a40f4-127">.NET Core 3.0 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-128">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-129">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-129">OS</span></span>                            | <span data-ttu-id="a40f4-130">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-130">Version</span></span>                        | <span data-ttu-id="a40f4-131">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a40f4-132">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-132">Windows Client</span></span>                | <span data-ttu-id="a40f4-133">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a40f4-134">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-134">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-135">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-135">Windows 10 Client</span></span>             | <span data-ttu-id="a40f4-136">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-136">Version 1607+</span></span>                  | <span data-ttu-id="a40f4-137">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-137">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-138">Windows Server</span></span>                | <span data-ttu-id="a40f4-139">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="a40f4-139">2012 R2+</span></span>                       | <span data-ttu-id="a40f4-140">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-140">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-141">Nano Server</span></span>                   | <span data-ttu-id="a40f4-142">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-142">Version 1803+</span></span>                  | <span data-ttu-id="a40f4-143">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="a40f4-143">x64, ARM32</span></span>      |

<span data-ttu-id="a40f4-144">有關 .NET Core 3.0 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="a40f4-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="a40f4-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="a40f4-146">*.NET 核心 2.2 當前已無支援。有關詳細資訊，請參閱[.NET 核心支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="a40f4-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="a40f4-147">.NET Core 2.2 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-148">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-149">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-149">OS</span></span>                            | <span data-ttu-id="a40f4-150">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-150">Version</span></span>                        | <span data-ttu-id="a40f4-151">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a40f4-152">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-152">Windows Client</span></span>                | <span data-ttu-id="a40f4-153">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a40f4-154">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-154">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-155">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-155">Windows 10 Client</span></span>             | <span data-ttu-id="a40f4-156">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-156">Version 1607+</span></span>                  | <span data-ttu-id="a40f4-157">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-157">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-158">Windows Server</span></span>                | <span data-ttu-id="a40f4-159">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="a40f4-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="a40f4-160">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-160">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-161">Nano Server</span></span>                   | <span data-ttu-id="a40f4-162">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-162">Version 1803+</span></span>                   | <span data-ttu-id="a40f4-163">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="a40f4-163">x64, ARM32</span></span>      |

<span data-ttu-id="a40f4-164">有關 .NET Core 2.2 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="a40f4-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="a40f4-166">.NET Core 2.1 支援以下 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-167">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-168">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-168">OS</span></span>                            | <span data-ttu-id="a40f4-169">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-169">Version</span></span>                        | <span data-ttu-id="a40f4-170">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a40f4-171">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-171">Windows Client</span></span>                | <span data-ttu-id="a40f4-172">7 SP1+， 8.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a40f4-173">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-173">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-174">視窗 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="a40f4-174">Windows 10 Client</span></span>             | <span data-ttu-id="a40f4-175">版本 1607\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-175">Version 1607+</span></span>                  | <span data-ttu-id="a40f4-176">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-176">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-177">Windows Server</span></span>                | <span data-ttu-id="a40f4-178">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="a40f4-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="a40f4-179">x64、x86</span><span class="sxs-lookup"><span data-stu-id="a40f4-179">x64, x86</span></span>        |
| <span data-ttu-id="a40f4-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="a40f4-180">Nano Server</span></span>                   | <span data-ttu-id="a40f4-181">版本 1803\*</span><span class="sxs-lookup"><span data-stu-id="a40f4-181">Version 1803+</span></span>                  | <span data-ttu-id="a40f4-182">x64，</span><span class="sxs-lookup"><span data-stu-id="a40f4-182">x64,</span></span>            |

<span data-ttu-id="a40f4-183">有關 .NET Core 2.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="a40f4-184">視窗 7 / Vista / 8.1 / 伺服器 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a40f4-184">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="a40f4-185">如果要在以下 Windows 版本上安裝 .NET SDK 或運行時，則需要其他依賴項：</span><span class="sxs-lookup"><span data-stu-id="a40f4-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="a40f4-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a40f4-186">Windows 7 SP1</span></span>
- <span data-ttu-id="a40f4-187">視窗 Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="a40f4-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="a40f4-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-188">Windows 8.1</span></span>
- <span data-ttu-id="a40f4-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a40f4-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="a40f4-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a40f4-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="a40f4-191">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="a40f4-191">Install the following:</span></span>

- <span data-ttu-id="a40f4-192">[微軟視覺C++ 2015 可轉散布更新 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="a40f4-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="a40f4-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="a40f4-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="a40f4-194">如果您遇到以下錯誤之一，還需要上述要求：</span><span class="sxs-lookup"><span data-stu-id="a40f4-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="a40f4-195">無法啟動該程式，因為您的電腦中缺少*api-ms-win-cr-runtime-l1-1-0.dll。*</span><span class="sxs-lookup"><span data-stu-id="a40f4-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="a40f4-196">請嘗試重新安裝程式以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="a40f4-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="a40f4-197">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="a40f4-197">\- or -</span></span>
>
> <span data-ttu-id="a40f4-198">找到庫*hostfxr.dll，* 但從*C：path_to_app\\\<載入\\>主機fxr.dll*失敗。</span><span class="sxs-lookup"><span data-stu-id="a40f4-198">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="a40f4-199">.NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-199">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="a40f4-200">.NET Core 3.1 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="a40f4-200">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="a40f4-201">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="a40f4-201">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a40f4-202">.NET Core 3.1 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-202">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-203">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-203">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-204">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-204">OS</span></span>                             | <span data-ttu-id="a40f4-205">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-205">Version</span></span>               | <span data-ttu-id="a40f4-206">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-206">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="a40f4-207">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-207">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="a40f4-208">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="a40f4-208">6, 7, 8</span></span>               | <span data-ttu-id="a40f4-209">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-209">x64</span></span> |
| <span data-ttu-id="a40f4-210">CentOS</span><span class="sxs-lookup"><span data-stu-id="a40f4-210">CentOS</span></span>                         | <span data-ttu-id="a40f4-211">7+</span><span class="sxs-lookup"><span data-stu-id="a40f4-211">7+</span></span>                    | <span data-ttu-id="a40f4-212">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-212">x64</span></span> |
| <span data-ttu-id="a40f4-213">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-213">Oracle Linux</span></span>                   | <span data-ttu-id="a40f4-214">7+</span><span class="sxs-lookup"><span data-stu-id="a40f4-214">7+</span></span>                    | <span data-ttu-id="a40f4-215">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-215">x64</span></span> |
| <span data-ttu-id="a40f4-216">Fedora</span><span class="sxs-lookup"><span data-stu-id="a40f4-216">Fedora</span></span>                         | <span data-ttu-id="a40f4-217">30€</span><span class="sxs-lookup"><span data-stu-id="a40f4-217">30+</span></span>                   | <span data-ttu-id="a40f4-218">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-218">x64</span></span> |
| <span data-ttu-id="a40f4-219">Debian</span><span class="sxs-lookup"><span data-stu-id="a40f4-219">Debian</span></span>                         | <span data-ttu-id="a40f4-220">9+</span><span class="sxs-lookup"><span data-stu-id="a40f4-220">9+</span></span>                    | <span data-ttu-id="a40f4-221">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="a40f4-221">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a40f4-222">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a40f4-222">Ubuntu</span></span>                         | <span data-ttu-id="a40f4-223">16.04+</span><span class="sxs-lookup"><span data-stu-id="a40f4-223">16.04+</span></span>                | <span data-ttu-id="a40f4-224">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="a40f4-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a40f4-225">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="a40f4-225">Linux Mint</span></span>                     | <span data-ttu-id="a40f4-226">18€</span><span class="sxs-lookup"><span data-stu-id="a40f4-226">18+</span></span>                   | <span data-ttu-id="a40f4-227">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-227">x64</span></span> |
| <span data-ttu-id="a40f4-228">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a40f4-228">openSUSE</span></span>                       | <span data-ttu-id="a40f4-229">15€</span><span class="sxs-lookup"><span data-stu-id="a40f4-229">15+</span></span>                   | <span data-ttu-id="a40f4-230">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-230">x64</span></span> |
| <span data-ttu-id="a40f4-231">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a40f4-231">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="a40f4-232">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a40f4-232">12 SP2+</span></span>               | <span data-ttu-id="a40f4-233">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-233">x64</span></span> |
| <span data-ttu-id="a40f4-234">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-234">Alpine Linux</span></span>                   | <span data-ttu-id="a40f4-235">3.10°</span><span class="sxs-lookup"><span data-stu-id="a40f4-235">3.10+</span></span>                 | <span data-ttu-id="a40f4-236">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="a40f4-236">x64, ARM64</span></span> |

<span data-ttu-id="a40f4-237">有關 .NET Core 3.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-237">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="a40f4-238">有關如何在 ARM64（內核 4.14+）上安裝 .NET 酷睿 3.1 的詳細資訊，請參閱[在 Linux ARM64 上安裝 .NET 核心 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-238">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a40f4-239">ARM64 支援需要 Linux 內核 4.14 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-239">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="a40f4-240">某些 linux 發行版本滿足此要求，而其他發行版本則不滿足此要求。</span><span class="sxs-lookup"><span data-stu-id="a40f4-240">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="a40f4-241">例如，Ubuntu 18.04 受支援，但 Ubuntu 16.04 不支援。</span><span class="sxs-lookup"><span data-stu-id="a40f4-241">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="a40f4-242">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a40f4-242">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="a40f4-243">*.NET 核心 3.0 當前已無支援。有關詳細資訊，請參閱[.NET 核心支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="a40f4-243">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="a40f4-244">.NET Core 3.0 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="a40f4-244">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="a40f4-245">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="a40f4-245">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a40f4-246">.NET Core 3.0 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-246">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-247">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-247">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-248">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-248">OS</span></span>                             | <span data-ttu-id="a40f4-249">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-249">Version</span></span>               | <span data-ttu-id="a40f4-250">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-250">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="a40f4-251">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-251">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="a40f4-252">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="a40f4-252">6, 7, 8</span></span>               | <span data-ttu-id="a40f4-253">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-253">x64</span></span> |
| <span data-ttu-id="a40f4-254">CentOS</span><span class="sxs-lookup"><span data-stu-id="a40f4-254">CentOS</span></span>                         | <span data-ttu-id="a40f4-255">7+</span><span class="sxs-lookup"><span data-stu-id="a40f4-255">7+</span></span>                    | <span data-ttu-id="a40f4-256">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-256">x64</span></span> |
| <span data-ttu-id="a40f4-257">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-257">Oracle Linux</span></span>                   | <span data-ttu-id="a40f4-258">7+</span><span class="sxs-lookup"><span data-stu-id="a40f4-258">7+</span></span>                    | <span data-ttu-id="a40f4-259">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-259">x64</span></span> |
| <span data-ttu-id="a40f4-260">Fedora</span><span class="sxs-lookup"><span data-stu-id="a40f4-260">Fedora</span></span>                         | <span data-ttu-id="a40f4-261">29°</span><span class="sxs-lookup"><span data-stu-id="a40f4-261">29+</span></span>                   | <span data-ttu-id="a40f4-262">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-262">x64</span></span> |
| <span data-ttu-id="a40f4-263">Debian</span><span class="sxs-lookup"><span data-stu-id="a40f4-263">Debian</span></span>                         | <span data-ttu-id="a40f4-264">9+</span><span class="sxs-lookup"><span data-stu-id="a40f4-264">9+</span></span>                    | <span data-ttu-id="a40f4-265">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="a40f4-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a40f4-266">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a40f4-266">Ubuntu</span></span>                         | <span data-ttu-id="a40f4-267">16.04+</span><span class="sxs-lookup"><span data-stu-id="a40f4-267">16.04+</span></span>                | <span data-ttu-id="a40f4-268">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="a40f4-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a40f4-269">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="a40f4-269">Linux Mint</span></span>                     | <span data-ttu-id="a40f4-270">18€</span><span class="sxs-lookup"><span data-stu-id="a40f4-270">18+</span></span>                   | <span data-ttu-id="a40f4-271">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-271">x64</span></span> |
| <span data-ttu-id="a40f4-272">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a40f4-272">openSUSE</span></span>                       | <span data-ttu-id="a40f4-273">15€</span><span class="sxs-lookup"><span data-stu-id="a40f4-273">15+</span></span>                   | <span data-ttu-id="a40f4-274">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-274">x64</span></span> |
| <span data-ttu-id="a40f4-275">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a40f4-275">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="a40f4-276">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a40f4-276">12 SP2+</span></span>               | <span data-ttu-id="a40f4-277">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-277">x64</span></span> |
| <span data-ttu-id="a40f4-278">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-278">Alpine Linux</span></span>                   | <span data-ttu-id="a40f4-279">3.8+</span><span class="sxs-lookup"><span data-stu-id="a40f4-279">3.8+</span></span>                  | <span data-ttu-id="a40f4-280">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="a40f4-280">x64, ARM64</span></span> |

<span data-ttu-id="a40f4-281">有關 .NET Core 3.0 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-281">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="a40f4-282">如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-282">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="a40f4-283">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="a40f4-283">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="a40f4-284">*.NET 核心 2.2 當前已無支援。有關詳細資訊，請參閱[.NET 核心支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="a40f4-284">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="a40f4-285">.NET Core 2.2 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="a40f4-285">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="a40f4-286">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="a40f4-286">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a40f4-287">.NET Core 2.2 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-287">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-288">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-288">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-289">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-289">OS</span></span>                             |  <span data-ttu-id="a40f4-290">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-290">Version</span></span>                |  <span data-ttu-id="a40f4-291">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-291">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="a40f4-292">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-292">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="a40f4-293">6、7</span><span class="sxs-lookup"><span data-stu-id="a40f4-293">6, 7</span></span>                   | <span data-ttu-id="a40f4-294">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-294">x64</span></span> |
| <span data-ttu-id="a40f4-295">CentOS</span><span class="sxs-lookup"><span data-stu-id="a40f4-295">CentOS</span></span>                         |  <span data-ttu-id="a40f4-296">7</span><span class="sxs-lookup"><span data-stu-id="a40f4-296">7</span></span>                      | <span data-ttu-id="a40f4-297">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-297">x64</span></span> |
| <span data-ttu-id="a40f4-298">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-298">Oracle Linux</span></span>                   |  <span data-ttu-id="a40f4-299">7</span><span class="sxs-lookup"><span data-stu-id="a40f4-299">7</span></span>                      | <span data-ttu-id="a40f4-300">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-300">x64</span></span> |
| <span data-ttu-id="a40f4-301">Fedora</span><span class="sxs-lookup"><span data-stu-id="a40f4-301">Fedora</span></span>                         |  <span data-ttu-id="a40f4-302">29, 30</span><span class="sxs-lookup"><span data-stu-id="a40f4-302">29, 30</span></span>                 | <span data-ttu-id="a40f4-303">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-303">x64</span></span> |
| <span data-ttu-id="a40f4-304">Debian</span><span class="sxs-lookup"><span data-stu-id="a40f4-304">Debian</span></span>                         |  <span data-ttu-id="a40f4-305">9</span><span class="sxs-lookup"><span data-stu-id="a40f4-305">9</span></span>                      | <span data-ttu-id="a40f4-306">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="a40f4-306">x64, ARM32</span></span> |
| <span data-ttu-id="a40f4-307">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a40f4-307">Ubuntu</span></span>                         |  <span data-ttu-id="a40f4-308">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="a40f4-308">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="a40f4-309">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="a40f4-309">x64, ARM32</span></span> |
| <span data-ttu-id="a40f4-310">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="a40f4-310">Linux Mint</span></span>                     |  <span data-ttu-id="a40f4-311">17, 18</span><span class="sxs-lookup"><span data-stu-id="a40f4-311">17, 18</span></span>                 | <span data-ttu-id="a40f4-312">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-312">x64</span></span> |
| <span data-ttu-id="a40f4-313">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a40f4-313">openSUSE</span></span>                       |  <span data-ttu-id="a40f4-314">15€</span><span class="sxs-lookup"><span data-stu-id="a40f4-314">15+</span></span>                    | <span data-ttu-id="a40f4-315">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-315">x64</span></span> |
| <span data-ttu-id="a40f4-316">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a40f4-316">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="a40f4-317">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a40f4-317">12 SP2+</span></span>                | <span data-ttu-id="a40f4-318">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-318">x64</span></span> |
| <span data-ttu-id="a40f4-319">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-319">Alpine Linux</span></span>                   |  <span data-ttu-id="a40f4-320">3.8+</span><span class="sxs-lookup"><span data-stu-id="a40f4-320">3.8+</span></span>                   | <span data-ttu-id="a40f4-321">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-321">x64</span></span> |

<span data-ttu-id="a40f4-322">有關 .NET Core 2.2 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-322">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="a40f4-323">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-323">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="a40f4-324">.NET Core 2.1 將 Linux 視為單個作業系統。</span><span class="sxs-lookup"><span data-stu-id="a40f4-324">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="a40f4-325">支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。</span><span class="sxs-lookup"><span data-stu-id="a40f4-325">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a40f4-326">.NET Core 2.1 支援以下 Linux 發行版本/版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-326">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-327">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-327">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-328">OS</span><span class="sxs-lookup"><span data-stu-id="a40f4-328">OS</span></span>                             |  <span data-ttu-id="a40f4-329">版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-329">Version</span></span>                |  <span data-ttu-id="a40f4-330">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-330">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="a40f4-331">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-331">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="a40f4-332">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="a40f4-332">6, 7, 8</span></span>                | <span data-ttu-id="a40f4-333">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-333">x64</span></span> |
| <span data-ttu-id="a40f4-334">CentOS</span><span class="sxs-lookup"><span data-stu-id="a40f4-334">CentOS</span></span>                         |  <span data-ttu-id="a40f4-335">7+</span><span class="sxs-lookup"><span data-stu-id="a40f4-335">7+</span></span>                     | <span data-ttu-id="a40f4-336">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-336">x64</span></span> |
| <span data-ttu-id="a40f4-337">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-337">Oracle Linux</span></span>                   |  <span data-ttu-id="a40f4-338">7+</span><span class="sxs-lookup"><span data-stu-id="a40f4-338">7+</span></span>                     | <span data-ttu-id="a40f4-339">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-339">x64</span></span> |
| <span data-ttu-id="a40f4-340">Fedora</span><span class="sxs-lookup"><span data-stu-id="a40f4-340">Fedora</span></span>                         |  <span data-ttu-id="a40f4-341">30€</span><span class="sxs-lookup"><span data-stu-id="a40f4-341">30+</span></span>                    | <span data-ttu-id="a40f4-342">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-342">x64</span></span> |
| <span data-ttu-id="a40f4-343">Debian</span><span class="sxs-lookup"><span data-stu-id="a40f4-343">Debian</span></span>                         |  <span data-ttu-id="a40f4-344">9</span><span class="sxs-lookup"><span data-stu-id="a40f4-344">9</span></span>                      | <span data-ttu-id="a40f4-345">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="a40f4-345">x64, ARM32</span></span> |
| <span data-ttu-id="a40f4-346">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a40f4-346">Ubuntu</span></span>                         |  <span data-ttu-id="a40f4-347">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="a40f4-347">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="a40f4-348">x64， ARM32</span><span class="sxs-lookup"><span data-stu-id="a40f4-348">x64, ARM32</span></span> |
| <span data-ttu-id="a40f4-349">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="a40f4-349">Linux Mint</span></span>                     |  <span data-ttu-id="a40f4-350">17+</span><span class="sxs-lookup"><span data-stu-id="a40f4-350">17+</span></span>                    | <span data-ttu-id="a40f4-351">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-351">x64</span></span> |
| <span data-ttu-id="a40f4-352">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a40f4-352">openSUSE</span></span>                       |  <span data-ttu-id="a40f4-353">15€</span><span class="sxs-lookup"><span data-stu-id="a40f4-353">15+</span></span>                    | <span data-ttu-id="a40f4-354">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-354">x64</span></span> |
| <span data-ttu-id="a40f4-355">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a40f4-355">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="a40f4-356">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a40f4-356">12 SP2+</span></span>                | <span data-ttu-id="a40f4-357">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-357">x64</span></span> |
| <span data-ttu-id="a40f4-358">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="a40f4-358">Alpine Linux</span></span>                   |  <span data-ttu-id="a40f4-359">3.8+</span><span class="sxs-lookup"><span data-stu-id="a40f4-359">3.8+</span></span>                   | <span data-ttu-id="a40f4-360">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-360">x64</span></span> |

<span data-ttu-id="a40f4-361">有關 .NET Core 2.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-361">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="a40f4-362">Linux 發行版本相依性</span><span class="sxs-lookup"><span data-stu-id="a40f4-362">Linux distribution dependencies</span></span>

<span data-ttu-id="a40f4-363">根據您的 linux 發行版本，您可能需要安裝其他依賴項。</span><span class="sxs-lookup"><span data-stu-id="a40f4-363">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a40f4-364">確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。</span><span class="sxs-lookup"><span data-stu-id="a40f4-364">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="a40f4-365">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a40f4-365">Ubuntu</span></span>

<span data-ttu-id="a40f4-366">Ubuntu 分發需要安裝以下庫：</span><span class="sxs-lookup"><span data-stu-id="a40f4-366">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="a40f4-367">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="a40f4-367">liblttng-ust0</span></span>
- <span data-ttu-id="a40f4-368">libcurl3 (適用於 14.x 及 16.x)</span><span class="sxs-lookup"><span data-stu-id="a40f4-368">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="a40f4-369">libcurl4 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="a40f4-369">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="a40f4-370">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="a40f4-370">libssl1.0.0</span></span>
- <span data-ttu-id="a40f4-371">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="a40f4-371">libkrb5-3</span></span>
- <span data-ttu-id="a40f4-372">zlib1g</span><span class="sxs-lookup"><span data-stu-id="a40f4-372">zlib1g</span></span>
- <span data-ttu-id="a40f4-373">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="a40f4-373">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="a40f4-374">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="a40f4-374">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="a40f4-375">libicu57 (適用於 17.x)</span><span class="sxs-lookup"><span data-stu-id="a40f4-375">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="a40f4-376">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="a40f4-376">libicu60 (for 18.x)</span></span>

<span data-ttu-id="a40f4-377">對於使用*System.Drawing.Common*程式集的 .NET Core 應用，您還需要以下依賴項：</span><span class="sxs-lookup"><span data-stu-id="a40f4-377">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="a40f4-378">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="a40f4-378">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="a40f4-379">大多數版本的Ubuntu包括早期版本的libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="a40f4-379">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="a40f4-380">您可以通過將 Mono 存儲庫添加到系統來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="a40f4-380">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="a40f4-381">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="a40f4-381">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="a40f4-382">CentOS 與 Fedora</span><span class="sxs-lookup"><span data-stu-id="a40f4-382">CentOS and Fedora</span></span>

<span data-ttu-id="a40f4-383">CentOS 發行版本需要安裝下列程式庫：</span><span class="sxs-lookup"><span data-stu-id="a40f4-383">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="a40f4-384">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="a40f4-384">lttng-ust</span></span>
- <span data-ttu-id="a40f4-385">libcurl</span><span class="sxs-lookup"><span data-stu-id="a40f4-385">libcurl</span></span>
- <span data-ttu-id="a40f4-386">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="a40f4-386">openssl-libs</span></span>
- <span data-ttu-id="a40f4-387">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="a40f4-387">krb5-libs</span></span>
- <span data-ttu-id="a40f4-388">libicu</span><span class="sxs-lookup"><span data-stu-id="a40f4-388">libicu</span></span>
- <span data-ttu-id="a40f4-389">zlib</span><span class="sxs-lookup"><span data-stu-id="a40f4-389">zlib</span></span>

<span data-ttu-id="a40f4-390">Fedora 使用者：如果您的 OpenSSL 版本>= 1.1，則需要安裝相容**openssl10**。</span><span class="sxs-lookup"><span data-stu-id="a40f4-390">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="a40f4-391">對於 .NET Core 2.0，還需要以下依賴項：</span><span class="sxs-lookup"><span data-stu-id="a40f4-391">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="a40f4-392">libunwind</span><span class="sxs-lookup"><span data-stu-id="a40f4-392">libunwind</span></span>
- <span data-ttu-id="a40f4-393">libuuid</span><span class="sxs-lookup"><span data-stu-id="a40f4-393">libuuid</span></span>

<span data-ttu-id="a40f4-394">有關依賴項的詳細資訊，請參閱[自包含的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-394">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="a40f4-395">對於使用*System.Drawing.Common*程式集的 .NET Core 應用，您還需要以下依賴項：</span><span class="sxs-lookup"><span data-stu-id="a40f4-395">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="a40f4-396">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="a40f4-396">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="a40f4-397">CentOS 和 Fedora 的大多數版本都包括早期版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="a40f4-397">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="a40f4-398">您可以通過將 Mono 存儲庫添加到系統來安裝最新版本的 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="a40f4-398">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="a40f4-399">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="a40f4-399">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="a40f4-400">.NET 核心支援以下 macOS 版本：</span><span class="sxs-lookup"><span data-stu-id="a40f4-400">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="a40f4-401">符號`+`表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="a40f4-401">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a40f4-402">.NET 核心版本</span><span class="sxs-lookup"><span data-stu-id="a40f4-402">.NET Core Version</span></span> | <span data-ttu-id="a40f4-403">macOS</span><span class="sxs-lookup"><span data-stu-id="a40f4-403">macOS</span></span>                 | <span data-ttu-id="a40f4-404">架構</span><span class="sxs-lookup"><span data-stu-id="a40f4-404">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="a40f4-405">3.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-405">3.1</span></span>               | <span data-ttu-id="a40f4-406">高塞拉 （10.13+）</span><span class="sxs-lookup"><span data-stu-id="a40f4-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="a40f4-407">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-407">x64</span></span> | [<span data-ttu-id="a40f4-408">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a40f4-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="a40f4-409">3.0</span><span class="sxs-lookup"><span data-stu-id="a40f4-409">3.0</span></span>               | <span data-ttu-id="a40f4-410">高塞拉 （10.13+）</span><span class="sxs-lookup"><span data-stu-id="a40f4-410">High Sierra (10.13+)</span></span>  | <span data-ttu-id="a40f4-411">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-411">x64</span></span> | [<span data-ttu-id="a40f4-412">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a40f4-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="a40f4-413">2.2</span><span class="sxs-lookup"><span data-stu-id="a40f4-413">2.2</span></span>               | <span data-ttu-id="a40f4-414">塞拉 （10.12+）</span><span class="sxs-lookup"><span data-stu-id="a40f4-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="a40f4-415">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-415">x64</span></span> | [<span data-ttu-id="a40f4-416">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a40f4-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="a40f4-417">2.1</span><span class="sxs-lookup"><span data-stu-id="a40f4-417">2.1</span></span>               | <span data-ttu-id="a40f4-418">塞拉 （10.12+）</span><span class="sxs-lookup"><span data-stu-id="a40f4-418">Sierra (10.12+)</span></span>       | <span data-ttu-id="a40f4-419">x64</span><span class="sxs-lookup"><span data-stu-id="a40f4-419">x64</span></span> | [<span data-ttu-id="a40f4-420">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a40f4-420">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="a40f4-421">從 macOS Catalina（版本 10.15）開始，所有 2019 年 6 月 1 日之後構建的所有軟體都必須使用開發人員 ID 進行公證。</span><span class="sxs-lookup"><span data-stu-id="a40f4-421">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="a40f4-422">此要求適用于 .NET 核心運行時、.NET 核心 SDK 和使用 .NET Core 創建的軟體。</span><span class="sxs-lookup"><span data-stu-id="a40f4-422">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="a40f4-423">自 2020 年 2 月 18 日起，對 .NET Core（運行時和 SDK）版本 3.1、3.0 和 2.1 的安裝程式進行了公證。</span><span class="sxs-lookup"><span data-stu-id="a40f4-423">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="a40f4-424">未對以前發佈的版本進行公證。</span><span class="sxs-lookup"><span data-stu-id="a40f4-424">Prior released versions aren't notarized.</span></span> <span data-ttu-id="a40f4-425">如果運行非公證應用，您將看到類似于下圖的錯誤：</span><span class="sxs-lookup"><span data-stu-id="a40f4-425">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS 卡塔利娜公證警報](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="a40f4-427">有關強制公證如何影響 .NET Core（和 .NET 核心應用）的詳細資訊，請參閱使用[macOS Catalina 公證](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-427">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="a40f4-428">利格迪加</span><span class="sxs-lookup"><span data-stu-id="a40f4-428">libgdiplus</span></span>

<span data-ttu-id="a40f4-429">.NET 核心應用程式，使用*系統.繪圖.公共*程式集需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="a40f4-429">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="a40f4-430">獲得 libgdiplus 的一種簡單方法是使用[macOS 的自製啤酒（"釀造"）](https://brew.sh/)包管理器。</span><span class="sxs-lookup"><span data-stu-id="a40f4-430">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="a40f4-431">安裝*沖煮*後，通過在終端（命令）提示符上執行以下命令來安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="a40f4-431">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="a40f4-432">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a40f4-432">Next steps</span></span>

- <span data-ttu-id="a40f4-433">要開發和運行應用，請安裝[.NET 核心 SDK（](sdk.md)包括運行時）。</span><span class="sxs-lookup"><span data-stu-id="a40f4-433">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="a40f4-434">要運行其他人創建的應用，請安裝[.NET Core 運行時](runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="a40f4-434">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
