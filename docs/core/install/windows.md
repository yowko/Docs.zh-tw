---
title: 在 Windows 上安裝 .NET
description: 瞭解您可以在哪些版本的 Windows 上安裝 .NET。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 57cebc562949627be70aabe24e75ad4567d072fd
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536121"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="057c1-103">在 Windows 上安裝 .NET</span><span class="sxs-lookup"><span data-stu-id="057c1-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [在 Linux 上安裝](linux.md)

<span data-ttu-id="057c1-107">在本文中，您將瞭解如何在 Windows 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="057c1-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="057c1-108">.NET 是由執行時間和 SDK 所組成。</span><span class="sxs-lookup"><span data-stu-id="057c1-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="057c1-109">執行時間是用來執行 .NET 應用程式，且不一定會包含在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="057c1-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="057c1-110">SDK 是用來建立 .NET 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="057c1-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="057c1-111">.NET 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="057c1-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="057c1-112">.NET 的最新版本為5.0。</span><span class="sxs-lookup"><span data-stu-id="057c1-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="057c1-113">下載 .NET</span><span class="sxs-lookup"><span data-stu-id="057c1-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="057c1-114">支援的版本</span><span class="sxs-lookup"><span data-stu-id="057c1-114">Supported releases</span></span>

<span data-ttu-id="057c1-115">下表列出目前支援的 .NET 版本，以及支援的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="057c1-116">這些版本一直受支援，直到 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Windows 版本的 [生命週期結束](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)為止。</span><span class="sxs-lookup"><span data-stu-id="057c1-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="057c1-117">Windows 10 版本的服務結束日期會依版本分割。</span><span class="sxs-lookup"><span data-stu-id="057c1-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="057c1-118">下表只考慮 **家用** 版、 **專業** 版、 **專業教育** 版和 **工作站版專業** 版。</span><span class="sxs-lookup"><span data-stu-id="057c1-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="057c1-119">查看 [Windows 生命週期的工作表](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) 以取得特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="057c1-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="057c1-120">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="057c1-121">作業系統</span><span class="sxs-lookup"><span data-stu-id="057c1-121">Operating System</span></span>            | <span data-ttu-id="057c1-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="057c1-122">.NET Core 2.1</span></span> | <span data-ttu-id="057c1-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="057c1-123">.NET Core 3.1</span></span> | <span data-ttu-id="057c1-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="057c1-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="057c1-125">Windows 10，版本20H2</span><span class="sxs-lookup"><span data-stu-id="057c1-125">Windows 10, Version 20H2</span></span>    | <span data-ttu-id="057c1-126">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-126">✔️</span></span>           | <span data-ttu-id="057c1-127">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-127">✔️</span></span>            | <span data-ttu-id="057c1-128">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-128">✔️</span></span>    |
| <span data-ttu-id="057c1-129">Windows 10，版本2004</span><span class="sxs-lookup"><span data-stu-id="057c1-129">Windows 10, Version 2004</span></span>    | <span data-ttu-id="057c1-130">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-130">✔️</span></span>           | <span data-ttu-id="057c1-131">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-131">✔️</span></span>            | <span data-ttu-id="057c1-132">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-132">✔️</span></span>    |
| <span data-ttu-id="057c1-133">Windows 10，版本1909</span><span class="sxs-lookup"><span data-stu-id="057c1-133">Windows 10, Version 1909</span></span>    | <span data-ttu-id="057c1-134">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-134">✔️</span></span>           | <span data-ttu-id="057c1-135">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-135">✔️</span></span>            | <span data-ttu-id="057c1-136">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-136">✔️</span></span>    |
| <span data-ttu-id="057c1-137">Windows 10，版本1903</span><span class="sxs-lookup"><span data-stu-id="057c1-137">Windows 10, Version 1903</span></span>    | <span data-ttu-id="057c1-138">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-138">✔️</span></span>           | <span data-ttu-id="057c1-139">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-139">✔️</span></span>            | <span data-ttu-id="057c1-140">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-140">✔️</span></span>    |
| <span data-ttu-id="057c1-141">Windows 10，版本1809</span><span class="sxs-lookup"><span data-stu-id="057c1-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="057c1-142">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-142">✔️</span></span>           | <span data-ttu-id="057c1-143">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-143">✔️</span></span>            | <span data-ttu-id="057c1-144">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-144">✔️</span></span>    |
| <span data-ttu-id="057c1-145">Windows 10，版本1803</span><span class="sxs-lookup"><span data-stu-id="057c1-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="057c1-146">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-146">✔️</span></span>           | <span data-ttu-id="057c1-147">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-147">✔️</span></span>            | <span data-ttu-id="057c1-148">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-148">✔️</span></span>    |
| <span data-ttu-id="057c1-149">Windows 10，版本1709</span><span class="sxs-lookup"><span data-stu-id="057c1-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="057c1-150">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-150">✔️</span></span>           | <span data-ttu-id="057c1-151">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-151">✔️</span></span>            | <span data-ttu-id="057c1-152">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-152">✔️</span></span>    |
| <span data-ttu-id="057c1-153">Windows 10，版本 1607</span><span class="sxs-lookup"><span data-stu-id="057c1-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="057c1-154">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-154">✔️</span></span>           | <span data-ttu-id="057c1-155">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-155">✔️</span></span>            | <span data-ttu-id="057c1-156">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-156">✔️</span></span>    |
| <span data-ttu-id="057c1-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="057c1-157">Windows 8.1</span></span>                 | <span data-ttu-id="057c1-158">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-158">✔️</span></span>           | <span data-ttu-id="057c1-159">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-159">✔️</span></span>            | <span data-ttu-id="057c1-160">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-160">✔️</span></span>    |
| <span data-ttu-id="057c1-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="057c1-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="057c1-162">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-162">✔️</span></span>           | <span data-ttu-id="057c1-163">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-163">✔️</span></span>            | <span data-ttu-id="057c1-164">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-164">✔️</span></span>    |
| <span data-ttu-id="057c1-165">Windows 10，版本 1607</span><span class="sxs-lookup"><span data-stu-id="057c1-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="057c1-166">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-166">✔️</span></span>           | <span data-ttu-id="057c1-167">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-167">✔️</span></span>            | <span data-ttu-id="057c1-168">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-168">✔️</span></span>    |
| <span data-ttu-id="057c1-169">Windows 10，版本 1607</span><span class="sxs-lookup"><span data-stu-id="057c1-169">Windows 10, Version 1607</span></span>    | <span data-ttu-id="057c1-170">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-170">✔️</span></span>           | <span data-ttu-id="057c1-171">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-171">✔️</span></span>            | <span data-ttu-id="057c1-172">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-172">✔️</span></span>    |
| <span data-ttu-id="057c1-173">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="057c1-173">Windows Server 2012 R2</span></span>      | <span data-ttu-id="057c1-174">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-174">✔️</span></span>           | <span data-ttu-id="057c1-175">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-175">✔️</span></span>            | <span data-ttu-id="057c1-176">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-176">✔️</span></span>    |
| <span data-ttu-id="057c1-177">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="057c1-177">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="057c1-178">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-178">✔️</span></span>           | <span data-ttu-id="057c1-179">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-179">✔️</span></span>            | <span data-ttu-id="057c1-180">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-180">✔️</span></span>    |
| <span data-ttu-id="057c1-181">Nano Server、Version 1809 +</span><span class="sxs-lookup"><span data-stu-id="057c1-181">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="057c1-182">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-182">✔️</span></span>           | <span data-ttu-id="057c1-183">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-183">✔️</span></span>            | <span data-ttu-id="057c1-184">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-184">✔️</span></span>    |
| <span data-ttu-id="057c1-185">Nano Server，版本1803</span><span class="sxs-lookup"><span data-stu-id="057c1-185">Nano Server, Version 1803</span></span>   | <span data-ttu-id="057c1-186">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-186">✔️</span></span>           | <span data-ttu-id="057c1-187">✔️</span><span class="sxs-lookup"><span data-stu-id="057c1-187">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="057c1-188">不支援的版本</span><span class="sxs-lookup"><span data-stu-id="057c1-188">Unsupported releases</span></span>

<span data-ttu-id="057c1-189">不再支援下列 .NET 版本 ❌ 。</span><span class="sxs-lookup"><span data-stu-id="057c1-189">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="057c1-190">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="057c1-190">The downloads for these still remain published:</span></span>

- <span data-ttu-id="057c1-191">3.0</span><span class="sxs-lookup"><span data-stu-id="057c1-191">3.0</span></span>
- <span data-ttu-id="057c1-192">2.2</span><span class="sxs-lookup"><span data-stu-id="057c1-192">2.2</span></span>
- <span data-ttu-id="057c1-193">2.0</span><span class="sxs-lookup"><span data-stu-id="057c1-193">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="057c1-194">執行時間資訊</span><span class="sxs-lookup"><span data-stu-id="057c1-194">Runtime information</span></span>

<span data-ttu-id="057c1-195">執行時間是用來執行以 .NET 建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="057c1-195">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="057c1-196">當應用程式作者發佈應用程式時，他們可以在其應用程式中包含執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-196">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="057c1-197">如果未包含執行時間，則會由使用者自行安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-197">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="057c1-198">您可以在 Windows 上安裝三個不同的執行時間：</span><span class="sxs-lookup"><span data-stu-id="057c1-198">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="057c1-199">*ASP.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="057c1-199">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="057c1-200">執行 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="057c1-200">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="057c1-201">包含 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-201">Includes the .NET runtime.</span></span>

<span data-ttu-id="057c1-202">*桌面執行時間*</span><span class="sxs-lookup"><span data-stu-id="057c1-202">*Desktop runtime*</span></span>\
<span data-ttu-id="057c1-203">執行適用于 Windows 的 .NET WPF 和 Windows Forms 桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="057c1-203">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="057c1-204">包含 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-204">Includes the .NET runtime.</span></span>

<span data-ttu-id="057c1-205">*.NET 執行時間*</span><span class="sxs-lookup"><span data-stu-id="057c1-205">*.NET runtime*</span></span>\
<span data-ttu-id="057c1-206">此執行時間是最簡單的執行時間，不包含任何其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-206">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="057c1-207">強烈建議您安裝 *ASP.NET Core 運行* 時間和 *桌面運行* 時間，以獲得與 .net 應用程式的最佳相容性。</span><span class="sxs-lookup"><span data-stu-id="057c1-207">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="057c1-208">下載 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="057c1-208">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="057c1-209">SDK 資訊</span><span class="sxs-lookup"><span data-stu-id="057c1-209">SDK information</span></span>

<span data-ttu-id="057c1-210">SDK 可用來建立及發佈 .NET 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="057c1-210">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="057c1-211">安裝 SDK 包含三個 [運行](#runtime-information)時間： ASP.NET Core、Desktop 和 .net。</span><span class="sxs-lookup"><span data-stu-id="057c1-211">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="057c1-212">相依性</span><span class="sxs-lookup"><span data-stu-id="057c1-212">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="057c1-213">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="057c1-213">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="057c1-214">.NET 5.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="057c1-214">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="057c1-215">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="057c1-216">OS</span><span class="sxs-lookup"><span data-stu-id="057c1-216">OS</span></span>                  | <span data-ttu-id="057c1-217">版本</span><span class="sxs-lookup"><span data-stu-id="057c1-217">Version</span></span>       | <span data-ttu-id="057c1-218">架構</span><span class="sxs-lookup"><span data-stu-id="057c1-218">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="057c1-219">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-219">Windows 10 Client</span></span>   | <span data-ttu-id="057c1-220">1607+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-220">Version 1607+</span></span> | <span data-ttu-id="057c1-221">x64、x86、ARM64</span><span class="sxs-lookup"><span data-stu-id="057c1-221">x64, x86, ARM64</span></span> |
| <span data-ttu-id="057c1-222">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-222">Windows Client</span></span>      | <span data-ttu-id="057c1-223">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="057c1-223">7 SP1+, 8.1</span></span>   | <span data-ttu-id="057c1-224">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-224">x64, x86</span></span>        |
| <span data-ttu-id="057c1-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="057c1-225">Windows Server</span></span>      | <span data-ttu-id="057c1-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="057c1-226">2012 R2+</span></span>      | <span data-ttu-id="057c1-227">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-227">x64, x86</span></span>        |
| <span data-ttu-id="057c1-228">Windows 伺服器核心</span><span class="sxs-lookup"><span data-stu-id="057c1-228">Windows Server Core</span></span> | <span data-ttu-id="057c1-229">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="057c1-229">2012 R2+</span></span>      | <span data-ttu-id="057c1-230">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-230">x64, x86</span></span>        |
| <span data-ttu-id="057c1-231">Nano Server</span><span class="sxs-lookup"><span data-stu-id="057c1-231">Nano Server</span></span>         | <span data-ttu-id="057c1-232">版本 1809 +</span><span class="sxs-lookup"><span data-stu-id="057c1-232">Version 1809+</span></span> | <span data-ttu-id="057c1-233">x64</span><span class="sxs-lookup"><span data-stu-id="057c1-233">x64</span></span>             |

<span data-ttu-id="057c1-234">如需 .NET 5.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱 [.net 5.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-234">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="057c1-235">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="057c1-235">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="057c1-236">.NET Core 3.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="057c1-236">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="057c1-237">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-237">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="057c1-238">OS</span><span class="sxs-lookup"><span data-stu-id="057c1-238">OS</span></span>                            | <span data-ttu-id="057c1-239">版本</span><span class="sxs-lookup"><span data-stu-id="057c1-239">Version</span></span>                        | <span data-ttu-id="057c1-240">架構</span><span class="sxs-lookup"><span data-stu-id="057c1-240">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="057c1-241">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-241">Windows Client</span></span>                | <span data-ttu-id="057c1-242">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="057c1-242">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="057c1-243">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-243">x64, x86</span></span>        |
| <span data-ttu-id="057c1-244">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-244">Windows 10 Client</span></span>             | <span data-ttu-id="057c1-245">1607+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-245">Version 1607+</span></span>                  | <span data-ttu-id="057c1-246">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-246">x64, x86</span></span>        |
| <span data-ttu-id="057c1-247">Windows Server</span><span class="sxs-lookup"><span data-stu-id="057c1-247">Windows Server</span></span>                | <span data-ttu-id="057c1-248">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="057c1-248">2012 R2+</span></span>                       | <span data-ttu-id="057c1-249">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-249">x64, x86</span></span>        |
| <span data-ttu-id="057c1-250">Nano Server</span><span class="sxs-lookup"><span data-stu-id="057c1-250">Nano Server</span></span>                   | <span data-ttu-id="057c1-251">1803+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-251">Version 1803+</span></span>                  | <span data-ttu-id="057c1-252">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="057c1-252">x64, ARM32</span></span>      |

<span data-ttu-id="057c1-253">如需 .NET Core 3.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-253">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="057c1-254">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="057c1-254">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="057c1-255">*.NET Core 3.0 目前不 ❌ 支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="057c1-255">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="057c1-256">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="057c1-256">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="057c1-257">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-257">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="057c1-258">OS</span><span class="sxs-lookup"><span data-stu-id="057c1-258">OS</span></span>                            | <span data-ttu-id="057c1-259">版本</span><span class="sxs-lookup"><span data-stu-id="057c1-259">Version</span></span>                        | <span data-ttu-id="057c1-260">架構</span><span class="sxs-lookup"><span data-stu-id="057c1-260">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="057c1-261">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-261">Windows Client</span></span>                | <span data-ttu-id="057c1-262">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="057c1-262">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="057c1-263">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-263">x64, x86</span></span>        |
| <span data-ttu-id="057c1-264">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-264">Windows 10 Client</span></span>             | <span data-ttu-id="057c1-265">1607+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-265">Version 1607+</span></span>                  | <span data-ttu-id="057c1-266">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-266">x64, x86</span></span>        |
| <span data-ttu-id="057c1-267">Windows Server</span><span class="sxs-lookup"><span data-stu-id="057c1-267">Windows Server</span></span>                | <span data-ttu-id="057c1-268">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="057c1-268">2012 R2+</span></span>                       | <span data-ttu-id="057c1-269">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-269">x64, x86</span></span>        |
| <span data-ttu-id="057c1-270">Nano Server</span><span class="sxs-lookup"><span data-stu-id="057c1-270">Nano Server</span></span>                   | <span data-ttu-id="057c1-271">1803+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-271">Version 1803+</span></span>                  | <span data-ttu-id="057c1-272">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="057c1-272">x64, ARM32</span></span>      |

<span data-ttu-id="057c1-273">如需 .NET Core 3.0 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-273">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="057c1-274">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="057c1-274">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="057c1-275">*.NET Core 2.2 目前不 ❌ 支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="057c1-275">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="057c1-276">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="057c1-276">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="057c1-277">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-277">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="057c1-278">OS</span><span class="sxs-lookup"><span data-stu-id="057c1-278">OS</span></span>                            | <span data-ttu-id="057c1-279">版本</span><span class="sxs-lookup"><span data-stu-id="057c1-279">Version</span></span>                        | <span data-ttu-id="057c1-280">架構</span><span class="sxs-lookup"><span data-stu-id="057c1-280">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="057c1-281">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-281">Windows Client</span></span>                | <span data-ttu-id="057c1-282">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="057c1-282">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="057c1-283">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-283">x64, x86</span></span>        |
| <span data-ttu-id="057c1-284">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-284">Windows 10 Client</span></span>             | <span data-ttu-id="057c1-285">1607+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-285">Version 1607+</span></span>                  | <span data-ttu-id="057c1-286">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-286">x64, x86</span></span>        |
| <span data-ttu-id="057c1-287">Windows Server</span><span class="sxs-lookup"><span data-stu-id="057c1-287">Windows Server</span></span>                | <span data-ttu-id="057c1-288">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="057c1-288">2008 R2 SP1+</span></span>                   | <span data-ttu-id="057c1-289">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-289">x64, x86</span></span>        |
| <span data-ttu-id="057c1-290">Nano Server</span><span class="sxs-lookup"><span data-stu-id="057c1-290">Nano Server</span></span>                   | <span data-ttu-id="057c1-291">1803+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-291">Version 1803+</span></span>                   | <span data-ttu-id="057c1-292">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="057c1-292">x64, ARM32</span></span>      |

<span data-ttu-id="057c1-293">如需 .NET Core 2.2 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-293">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="057c1-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="057c1-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="057c1-295">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="057c1-295">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="057c1-296">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-296">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="057c1-297">OS</span><span class="sxs-lookup"><span data-stu-id="057c1-297">OS</span></span>                            | <span data-ttu-id="057c1-298">版本</span><span class="sxs-lookup"><span data-stu-id="057c1-298">Version</span></span>                        | <span data-ttu-id="057c1-299">架構</span><span class="sxs-lookup"><span data-stu-id="057c1-299">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="057c1-300">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-300">Windows Client</span></span>                | <span data-ttu-id="057c1-301">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="057c1-301">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="057c1-302">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-302">x64, x86</span></span>        |
| <span data-ttu-id="057c1-303">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="057c1-303">Windows 10 Client</span></span>             | <span data-ttu-id="057c1-304">1607+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-304">Version 1607+</span></span>                  | <span data-ttu-id="057c1-305">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-305">x64, x86</span></span>        |
| <span data-ttu-id="057c1-306">Windows Server</span><span class="sxs-lookup"><span data-stu-id="057c1-306">Windows Server</span></span>                | <span data-ttu-id="057c1-307">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="057c1-307">2008 R2 SP1+</span></span>                   | <span data-ttu-id="057c1-308">x64、x86</span><span class="sxs-lookup"><span data-stu-id="057c1-308">x64, x86</span></span>        |
| <span data-ttu-id="057c1-309">Nano Server</span><span class="sxs-lookup"><span data-stu-id="057c1-309">Nano Server</span></span>                   | <span data-ttu-id="057c1-310">1803+ 版</span><span class="sxs-lookup"><span data-stu-id="057c1-310">Version 1803+</span></span>                  | <span data-ttu-id="057c1-311">64</span><span class="sxs-lookup"><span data-stu-id="057c1-311">x64,</span></span>            |

<span data-ttu-id="057c1-312">如需 .NET Core 2.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-312">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="057c1-313">Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="057c1-313">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="057c1-314">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要更多相依性：</span><span class="sxs-lookup"><span data-stu-id="057c1-314">More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

| <span data-ttu-id="057c1-315">作業系統</span><span class="sxs-lookup"><span data-stu-id="057c1-315">Operating System</span></span>         | <span data-ttu-id="057c1-316">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="057c1-316">Prerequisites</span></span>                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| <span data-ttu-id="057c1-317">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="057c1-317">Windows 7 SP1 [ESU][esu]</span></span> | <span data-ttu-id="057c1-318">-Microsoft Visual C++ 2015-2019 可轉散發套件[64][vcc64]位  /  [32][vcc32]位</span><span class="sxs-lookup"><span data-stu-id="057c1-318">- Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> <br> <span data-ttu-id="057c1-319">-KB3063858 [64-位][kb64]  /  [32][kb32]位</span><span class="sxs-lookup"><span data-stu-id="057c1-319">- KB3063858 [64-bit][kb64] / [32-bit][kb32]</span></span> <br> <span data-ttu-id="057c1-320">- [MicrosoftRootCertificateAuthority2011 .cer](https://go.microsoft.com/fwlink/?linkid=747875&clcid=0x409) ( 僅限 .net Core 2.1) </span><span class="sxs-lookup"><span data-stu-id="057c1-320">- [MicrosoftRootCertificateAuthority2011.cer](https://go.microsoft.com/fwlink/?linkid=747875&clcid=0x409) (.NET Core 2.1 only)</span></span> |
| <span data-ttu-id="057c1-321">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="057c1-321">Windows Vista SP 2</span></span>       | <span data-ttu-id="057c1-322">Microsoft Visual C++ 2015-2019 可轉散發套件[64][vcc64]位  /  [32][vcc32]位</span><span class="sxs-lookup"><span data-stu-id="057c1-322">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="057c1-323">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="057c1-323">Windows 8.1</span></span>              | <span data-ttu-id="057c1-324">Microsoft Visual C++ 2015-2019 可轉散發套件[64][vcc64]位  /  [32][vcc32]位</span><span class="sxs-lookup"><span data-stu-id="057c1-324">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="057c1-325">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="057c1-325">Windows Server 2008 R2</span></span>   | <span data-ttu-id="057c1-326">Microsoft Visual C++ 2015-2019 可轉散發套件[64][vcc64]位  /  [32][vcc32]位</span><span class="sxs-lookup"><span data-stu-id="057c1-326">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="057c1-327">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="057c1-327">Windows Server 2012 R2</span></span>   | <span data-ttu-id="057c1-328">Microsoft Visual C++ 2015-2019 可轉散發套件[64][vcc64]位  /  [32][vcc32]位</span><span class="sxs-lookup"><span data-stu-id="057c1-328">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |

<span data-ttu-id="057c1-329">如果您收到下列任一 dll 的相關錯誤，也需要先前的需求：</span><span class="sxs-lookup"><span data-stu-id="057c1-329">The previous requirements are also required if you receive an error related to either of the following dlls:</span></span>

- <span data-ttu-id="057c1-330">*api-ms-win-crt-runtime-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="057c1-330">*api-ms-win-crt-runtime-l1-1-0.dll*</span></span>
- <span data-ttu-id="057c1-331">*api-ms-win-cor-timezone-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="057c1-331">*api-ms-win-cor-timezone-l1-1-0.dll*</span></span>
- <span data-ttu-id="057c1-332">*hostfxr.dll*</span><span class="sxs-lookup"><span data-stu-id="057c1-332">*hostfxr.dll*</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="057c1-333">使用 PowerShell 自動化安裝</span><span class="sxs-lookup"><span data-stu-id="057c1-333">Install with PowerShell automation</span></span>

<span data-ttu-id="057c1-334">[Dotnet 安裝腳本](../tools/dotnet-install-script.md)適用于執行時間的 CI 自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="057c1-334">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="057c1-335">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="057c1-335">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="057c1-336">腳本預設會安裝最新 [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="057c1-336">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="057c1-337">您可以藉由指定參數來選擇特定版本 `Channel` 。</span><span class="sxs-lookup"><span data-stu-id="057c1-337">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="057c1-338">包含 `Runtime` 參數以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-338">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="057c1-339">否則，腳本會安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="057c1-339">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="057c1-340">藉由省略參數來安裝 SDK `-Runtime` 。</span><span class="sxs-lookup"><span data-stu-id="057c1-340">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="057c1-341">`-Channel`此範例會將此參數設定為 `Current` ，以安裝最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-341">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="057c1-342">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="057c1-342">Install with Visual Studio</span></span>

<span data-ttu-id="057c1-343">如果您使用 Visual Studio 開發 .NET 應用程式，下表將根據目標 .NET SDK 版本描述 Visual Studio 所需的最低版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-343">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="057c1-344">.NET SDK 版本</span><span class="sxs-lookup"><span data-stu-id="057c1-344">.NET SDK version</span></span>      | <span data-ttu-id="057c1-345">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="057c1-345">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="057c1-346">5.0</span><span class="sxs-lookup"><span data-stu-id="057c1-346">5.0</span></span>                   | <span data-ttu-id="057c1-347">Visual Studio 2019 16.8 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-347">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="057c1-348">3.1</span><span class="sxs-lookup"><span data-stu-id="057c1-348">3.1</span></span>                   | <span data-ttu-id="057c1-349">Visual Studio 2019 16.4 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-349">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="057c1-350">3.0</span><span class="sxs-lookup"><span data-stu-id="057c1-350">3.0</span></span>                   | <span data-ttu-id="057c1-351">Visual Studio 2019 16.3 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-351">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="057c1-352">2.2</span><span class="sxs-lookup"><span data-stu-id="057c1-352">2.2</span></span>                   | <span data-ttu-id="057c1-353">Visual Studio 2017 15.9 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-353">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="057c1-354">2.1</span><span class="sxs-lookup"><span data-stu-id="057c1-354">2.1</span></span>                   | <span data-ttu-id="057c1-355">Visual Studio 2017 15.7 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-355">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="057c1-356">如果您已經安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-356">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="057c1-357">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="057c1-357">Open Visual Studio.</span></span>
01. <span data-ttu-id="057c1-358">選取  >  **Microsoft Visual Studio** 的 [說明]。</span><span class="sxs-lookup"><span data-stu-id="057c1-358">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="057c1-359">閱讀 [ **關於** ] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="057c1-359">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="057c1-360">Visual Studio 可以安裝最新的 .NET SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-360">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="057c1-361">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="057c1-361">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="057c1-362">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="057c1-362">Select a workload</span></span>

<span data-ttu-id="057c1-363">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列一或多個工作負載：</span><span class="sxs-lookup"><span data-stu-id="057c1-363">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="057c1-364">[**其他工具** 組] 區段中的 **.net Core 跨平臺開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="057c1-364">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="057c1-365">**Web & Cloud** 區段中的 **ASP.NET 和 網頁程式開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="057c1-365">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="057c1-366">**Web & Cloud** 區段中的 **Azure 開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="057c1-366">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="057c1-367">Desktop 中的 **.net 桌面開發** 工作負載 **& Mobile** 區段。</span><span class="sxs-lookup"><span data-stu-id="057c1-367">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="057c1-368">[![使用 .NET Core 工作負載的 Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="057c1-368">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="057c1-369">隨 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="057c1-369">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="057c1-370">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="057c1-370">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="057c1-371">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="057c1-371">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="057c1-372">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援很簡單。</span><span class="sxs-lookup"><span data-stu-id="057c1-372">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="057c1-373">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="057c1-373">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="057c1-374">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="057c1-374">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="057c1-375">[從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。</span><span class="sxs-lookup"><span data-stu-id="057c1-375">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="057c1-376">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="057c1-376">Windows Installer</span></span>

<span data-ttu-id="057c1-377">.NET 的 [下載頁面](https://dotnet.microsoft.com/download/dotnet-core) 提供 Windows Installer 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="057c1-377">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="057c1-378">當您使用 Windows 安裝程式安裝 .NET 時，您可以藉由設定和參數來自訂安裝路徑 `DOTNETHOME_X64` `DOTNETHOME_X86` ：</span><span class="sxs-lookup"><span data-stu-id="057c1-378">When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

<span data-ttu-id="057c1-379">如果您想要以無訊息方式安裝 .NET，例如在生產環境中或為了支援持續整合，請使用下列參數：</span><span class="sxs-lookup"><span data-stu-id="057c1-379">If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:</span></span>

- `/install`\
<span data-ttu-id="057c1-380">安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="057c1-380">Installs .NET.</span></span>

- `/quiet`\
<span data-ttu-id="057c1-381">防止顯示任何 UI 和提示。</span><span class="sxs-lookup"><span data-stu-id="057c1-381">Prevents any UI and prompts from displaying.</span></span>

- `norestart`\
<span data-ttu-id="057c1-382">抑制任何重新啟動嘗試。</span><span class="sxs-lookup"><span data-stu-id="057c1-382">Suppresses any attempts to restart.</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

<span data-ttu-id="057c1-383">如需詳細資訊，請參閱 [標準安裝程式 Command-Line 選項](/windows/win32/msi/standard-installer-command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="057c1-383">For more information, see [Standard Installer Command-Line Options](/windows/win32/msi/standard-installer-command-line-options).</span></span>

> [!TIP]
> <span data-ttu-id="057c1-384">安裝程式會傳回結束代碼0表示成功，結束代碼為3010表示需要重新開機。</span><span class="sxs-lookup"><span data-stu-id="057c1-384">The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required.</span></span> <span data-ttu-id="057c1-385">任何其他值通常都是錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="057c1-385">Any other value is generally an error code.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="057c1-386">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="057c1-386">Download and manually install</span></span>

<span data-ttu-id="057c1-387">您也可以下載並手動安裝 SDK 或執行時間，以替代適用于 .NET 的 Windows 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="057c1-387">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="057c1-388">手動安裝通常會做為持續整合測試的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="057c1-388">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="057c1-389">針對開發人員或使用者，通常最好是使用 [安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="057c1-389">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="057c1-390">.NET SDK 和 .NET 執行時間都可以在下載之後手動安裝。</span><span class="sxs-lookup"><span data-stu-id="057c1-390">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="057c1-391">如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="057c1-391">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="057c1-392">首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：</span><span class="sxs-lookup"><span data-stu-id="057c1-392">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="057c1-393">.NET 5.0 下載</span><span class="sxs-lookup"><span data-stu-id="057c1-393">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="057c1-394">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="057c1-394">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="057c1-395">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="057c1-395">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="057c1-396">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="057c1-396">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="057c1-397">例如，建立用來將 .NET 解壓縮至的目錄 `%USERPROFILE%\dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="057c1-397">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="057c1-398">然後，將下載的 zip 檔案解壓縮到該目錄中。</span><span class="sxs-lookup"><span data-stu-id="057c1-398">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="057c1-399">根據預設，.NET CLI 命令和應用程式不會使用以這種方式安裝的 .NET，因此您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="057c1-399">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="057c1-400">若要這樣做，請變更應用程式啟動所在的環境變數：</span><span class="sxs-lookup"><span data-stu-id="057c1-400">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="057c1-401">這種方法可讓您將多個版本安裝到不同的位置，然後使用指向該位置的環境變數來執行應用程式，以明確選擇應用程式應使用的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="057c1-401">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="057c1-402">當 `DOTNET_MULTILEVEL_LOOKUP` 設定為時 `0` ，.net 會忽略任何全域安裝的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="057c1-402">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="057c1-403">移除該環境設定，讓 .NET 在選取最適合用來執行應用程式的架構時，考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="057c1-403">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="057c1-404">預設值通常是 `C:\Program Files\dotnet` 安裝程式安裝 .net 的位置。</span><span class="sxs-lookup"><span data-stu-id="057c1-404">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="057c1-405">Docker</span><span class="sxs-lookup"><span data-stu-id="057c1-405">Docker</span></span>

<span data-ttu-id="057c1-406">容器可提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="057c1-406">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="057c1-407">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="057c1-407">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="057c1-408">.NET 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="057c1-408">.NET can run in a Docker container.</span></span> <span data-ttu-id="057c1-409">官方 .NET Docker 映射會發佈至 Microsoft Container Registry (MCR) 並可在 [microsoft .net Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet)中找到。</span><span class="sxs-lookup"><span data-stu-id="057c1-409">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="057c1-410">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="057c1-410">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="057c1-411">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="057c1-411">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="057c1-412">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-aspnet) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="057c1-412">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="057c1-413">如需在 Docker 容器中使用 .NET 的詳細資訊，請參閱 [.net 和 Docker 簡介](../docker/introduction.md) 和 [範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-413">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="057c1-414">後續步驟</span><span class="sxs-lookup"><span data-stu-id="057c1-414">Next steps</span></span>

- <span data-ttu-id="057c1-415">[如何檢查是否已安裝 .net](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="057c1-415">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="057c1-416">[教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="057c1-416">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="057c1-417">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-417">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="057c1-418">[教學課程：將 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="057c1-418">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/en-us/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/en-us/download/details.aspx?id=47409
