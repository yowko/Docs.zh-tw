---
title: 在 Windows 上安裝 .NET
description: 瞭解您可以在哪些版本的 Windows 上安裝 .NET。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 786814549724948fa69b18a05cee966e0940aaf4
ms.sourcegitcommit: c6de55556add9f92af17e0f8d1da8f356a19a03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96549341"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="7da42-103">在 Windows 上安裝 .NET</span><span class="sxs-lookup"><span data-stu-id="7da42-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [在 Linux 上安裝](linux.md)

<span data-ttu-id="7da42-107">在本文中，您將瞭解如何在 Windows 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="7da42-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="7da42-108">.NET 是由執行時間和 SDK 所組成。</span><span class="sxs-lookup"><span data-stu-id="7da42-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="7da42-109">執行時間是用來執行 .NET 應用程式，且不一定會包含在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7da42-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="7da42-110">SDK 是用來建立 .NET 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="7da42-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="7da42-111">.NET 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="7da42-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="7da42-112">.NET 的最新版本為5.0。</span><span class="sxs-lookup"><span data-stu-id="7da42-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7da42-113">下載 .NET</span><span class="sxs-lookup"><span data-stu-id="7da42-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="7da42-114">支援的版本</span><span class="sxs-lookup"><span data-stu-id="7da42-114">Supported releases</span></span>

<span data-ttu-id="7da42-115">下表列出目前支援的 .NET 版本，以及支援的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="7da42-116">這些版本一直受支援，直到 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Windows 版本的 [生命週期結束](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)為止。</span><span class="sxs-lookup"><span data-stu-id="7da42-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="7da42-117">Windows 10 版本的服務結束日期會依版本分割。</span><span class="sxs-lookup"><span data-stu-id="7da42-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="7da42-118">下表只考慮 **家用** 版、 **專業** 版、 **專業教育** 版和 **工作站版專業** 版。</span><span class="sxs-lookup"><span data-stu-id="7da42-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="7da42-119">查看 [Windows 生命週期的工作表](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) 以取得特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7da42-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="7da42-120">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7da42-121">作業系統</span><span class="sxs-lookup"><span data-stu-id="7da42-121">Operating System</span></span>            | <span data-ttu-id="7da42-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7da42-122">.NET Core 2.1</span></span> | <span data-ttu-id="7da42-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7da42-123">.NET Core 3.1</span></span> | <span data-ttu-id="7da42-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="7da42-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="7da42-125">Windows 10，版本2004</span><span class="sxs-lookup"><span data-stu-id="7da42-125">Windows 10, Version 2004</span></span>    | <span data-ttu-id="7da42-126">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-126">✔️</span></span>           | <span data-ttu-id="7da42-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-127">✔️</span></span>            | <span data-ttu-id="7da42-128">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-128">✔️</span></span>    |
| <span data-ttu-id="7da42-129">Windows 10，版本1909</span><span class="sxs-lookup"><span data-stu-id="7da42-129">Windows 10, Version 1909</span></span>    | <span data-ttu-id="7da42-130">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-130">✔️</span></span>           | <span data-ttu-id="7da42-131">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-131">✔️</span></span>            | <span data-ttu-id="7da42-132">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-132">✔️</span></span>    |
| <span data-ttu-id="7da42-133">Windows 10，版本1903</span><span class="sxs-lookup"><span data-stu-id="7da42-133">Windows 10, Version 1903</span></span>    | <span data-ttu-id="7da42-134">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-134">✔️</span></span>           | <span data-ttu-id="7da42-135">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-135">✔️</span></span>            | <span data-ttu-id="7da42-136">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-136">✔️</span></span>    |
| <span data-ttu-id="7da42-137">Windows 10，版本1809</span><span class="sxs-lookup"><span data-stu-id="7da42-137">Windows 10, Version 1809</span></span>    | <span data-ttu-id="7da42-138">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-138">✔️</span></span>           | <span data-ttu-id="7da42-139">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-139">✔️</span></span>            | <span data-ttu-id="7da42-140">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-140">✔️</span></span>    |
| <span data-ttu-id="7da42-141">Windows 10，版本1803</span><span class="sxs-lookup"><span data-stu-id="7da42-141">Windows 10, Version 1803</span></span>    | <span data-ttu-id="7da42-142">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-142">✔️</span></span>           | <span data-ttu-id="7da42-143">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-143">✔️</span></span>            | <span data-ttu-id="7da42-144">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-144">✔️</span></span>    |
| <span data-ttu-id="7da42-145">Windows 10，版本1709</span><span class="sxs-lookup"><span data-stu-id="7da42-145">Windows 10, Version 1709</span></span>    | <span data-ttu-id="7da42-146">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-146">✔️</span></span>           | <span data-ttu-id="7da42-147">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-147">✔️</span></span>            | <span data-ttu-id="7da42-148">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-148">✔️</span></span>    |
| <span data-ttu-id="7da42-149">Windows 10，版本 1607</span><span class="sxs-lookup"><span data-stu-id="7da42-149">Windows 10, Version 1607</span></span>    | <span data-ttu-id="7da42-150">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-150">✔️</span></span>           | <span data-ttu-id="7da42-151">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-151">✔️</span></span>            | <span data-ttu-id="7da42-152">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-152">✔️</span></span>    |
| <span data-ttu-id="7da42-153">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7da42-153">Windows 8.1</span></span>                 | <span data-ttu-id="7da42-154">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-154">✔️</span></span>           | <span data-ttu-id="7da42-155">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-155">✔️</span></span>            | <span data-ttu-id="7da42-156">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-156">✔️</span></span>    |
| <span data-ttu-id="7da42-157">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="7da42-157">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="7da42-158">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-158">✔️</span></span>           | <span data-ttu-id="7da42-159">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-159">✔️</span></span>            | <span data-ttu-id="7da42-160">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-160">✔️</span></span>    |
| <span data-ttu-id="7da42-161">Windows 10，版本 1607</span><span class="sxs-lookup"><span data-stu-id="7da42-161">Windows 10, Version 1607</span></span>    | <span data-ttu-id="7da42-162">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-162">✔️</span></span>           | <span data-ttu-id="7da42-163">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-163">✔️</span></span>            | <span data-ttu-id="7da42-164">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-164">✔️</span></span>    |
| <span data-ttu-id="7da42-165">Windows 10，版本 1607</span><span class="sxs-lookup"><span data-stu-id="7da42-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="7da42-166">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-166">✔️</span></span>           | <span data-ttu-id="7da42-167">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-167">✔️</span></span>            | <span data-ttu-id="7da42-168">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-168">✔️</span></span>    |
| <span data-ttu-id="7da42-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7da42-169">Windows Server 2012 R2</span></span>      | <span data-ttu-id="7da42-170">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-170">✔️</span></span>           | <span data-ttu-id="7da42-171">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-171">✔️</span></span>            | <span data-ttu-id="7da42-172">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-172">✔️</span></span>    |
| <span data-ttu-id="7da42-173">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7da42-173">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="7da42-174">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-174">✔️</span></span>           | <span data-ttu-id="7da42-175">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-175">✔️</span></span>            | <span data-ttu-id="7da42-176">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-176">✔️</span></span>    |
| <span data-ttu-id="7da42-177">Nano Server、Version 1809 +</span><span class="sxs-lookup"><span data-stu-id="7da42-177">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="7da42-178">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-178">✔️</span></span>           | <span data-ttu-id="7da42-179">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-179">✔️</span></span>            | <span data-ttu-id="7da42-180">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-180">✔️</span></span>    |
| <span data-ttu-id="7da42-181">Nano Server，版本1803</span><span class="sxs-lookup"><span data-stu-id="7da42-181">Nano Server, Version 1803</span></span>   | <span data-ttu-id="7da42-182">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-182">✔️</span></span>           | <span data-ttu-id="7da42-183">✔️</span><span class="sxs-lookup"><span data-stu-id="7da42-183">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="7da42-184">不支援的版本</span><span class="sxs-lookup"><span data-stu-id="7da42-184">Unsupported releases</span></span>

<span data-ttu-id="7da42-185">不再支援下列 .NET 版本 ❌ 。</span><span class="sxs-lookup"><span data-stu-id="7da42-185">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="7da42-186">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="7da42-186">The downloads for these still remain published:</span></span>

- <span data-ttu-id="7da42-187">3.0</span><span class="sxs-lookup"><span data-stu-id="7da42-187">3.0</span></span>
- <span data-ttu-id="7da42-188">2.2</span><span class="sxs-lookup"><span data-stu-id="7da42-188">2.2</span></span>
- <span data-ttu-id="7da42-189">2.0</span><span class="sxs-lookup"><span data-stu-id="7da42-189">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="7da42-190">執行時間資訊</span><span class="sxs-lookup"><span data-stu-id="7da42-190">Runtime information</span></span>

<span data-ttu-id="7da42-191">執行時間是用來執行以 .NET 建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7da42-191">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="7da42-192">當應用程式作者發佈應用程式時，他們可以在其應用程式中包含執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-192">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="7da42-193">如果未包含執行時間，則會由使用者自行安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-193">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="7da42-194">您可以在 Windows 上安裝三個不同的執行時間：</span><span class="sxs-lookup"><span data-stu-id="7da42-194">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="7da42-195">*ASP.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="7da42-195">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="7da42-196">執行 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7da42-196">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="7da42-197">包含 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-197">Includes the .NET runtime.</span></span>

<span data-ttu-id="7da42-198">*桌面執行時間*</span><span class="sxs-lookup"><span data-stu-id="7da42-198">*Desktop runtime*</span></span>\
<span data-ttu-id="7da42-199">執行適用于 Windows 的 .NET WPF 和 Windows Forms 桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="7da42-199">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="7da42-200">包含 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-200">Includes the .NET runtime.</span></span>

<span data-ttu-id="7da42-201">*.NET 執行時間*</span><span class="sxs-lookup"><span data-stu-id="7da42-201">*.NET runtime*</span></span>\
<span data-ttu-id="7da42-202">此執行時間是最簡單的執行時間，不包含任何其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-202">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="7da42-203">強烈建議您安裝 *ASP.NET Core 運行* 時間和 *桌面運行* 時間，以獲得與 .net 應用程式的最佳相容性。</span><span class="sxs-lookup"><span data-stu-id="7da42-203">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7da42-204">下載 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="7da42-204">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="7da42-205">SDK 資訊</span><span class="sxs-lookup"><span data-stu-id="7da42-205">SDK information</span></span>

<span data-ttu-id="7da42-206">SDK 可用來建立及發佈 .NET 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="7da42-206">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="7da42-207">安裝 SDK 包含三個 [運行](#runtime-information)時間： ASP.NET Core、Desktop 和 .net。</span><span class="sxs-lookup"><span data-stu-id="7da42-207">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="7da42-208">相依性</span><span class="sxs-lookup"><span data-stu-id="7da42-208">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="7da42-209">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="7da42-209">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="7da42-210">.NET 5.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7da42-210">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="7da42-211">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-211">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7da42-212">OS</span><span class="sxs-lookup"><span data-stu-id="7da42-212">OS</span></span>                  | <span data-ttu-id="7da42-213">版本</span><span class="sxs-lookup"><span data-stu-id="7da42-213">Version</span></span>       | <span data-ttu-id="7da42-214">架構</span><span class="sxs-lookup"><span data-stu-id="7da42-214">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="7da42-215">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-215">Windows 10 Client</span></span>   | <span data-ttu-id="7da42-216">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7da42-216">Version 1607+</span></span> | <span data-ttu-id="7da42-217">x64、x86、ARM64</span><span class="sxs-lookup"><span data-stu-id="7da42-217">x64, x86, ARM64</span></span> |
| <span data-ttu-id="7da42-218">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-218">Windows Client</span></span>      | <span data-ttu-id="7da42-219">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7da42-219">7 SP1+, 8.1</span></span>   | <span data-ttu-id="7da42-220">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-220">x64, x86</span></span>        |
| <span data-ttu-id="7da42-221">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7da42-221">Windows Server</span></span>      | <span data-ttu-id="7da42-222">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="7da42-222">2012 R2+</span></span>      | <span data-ttu-id="7da42-223">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-223">x64, x86</span></span>        |
| <span data-ttu-id="7da42-224">Windows 伺服器核心</span><span class="sxs-lookup"><span data-stu-id="7da42-224">Windows Server Core</span></span> | <span data-ttu-id="7da42-225">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="7da42-225">2012 R2+</span></span>      | <span data-ttu-id="7da42-226">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-226">x64, x86</span></span>        |
| <span data-ttu-id="7da42-227">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7da42-227">Nano Server</span></span>         | <span data-ttu-id="7da42-228">版本 1809 +</span><span class="sxs-lookup"><span data-stu-id="7da42-228">Version 1809+</span></span> | <span data-ttu-id="7da42-229">x64</span><span class="sxs-lookup"><span data-stu-id="7da42-229">x64</span></span>             |

<span data-ttu-id="7da42-230">如需 .NET 5.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱 [.net 5.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-230">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="7da42-231">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7da42-231">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="7da42-232">.NET Core 3.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7da42-232">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7da42-233">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-233">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7da42-234">OS</span><span class="sxs-lookup"><span data-stu-id="7da42-234">OS</span></span>                            | <span data-ttu-id="7da42-235">版本</span><span class="sxs-lookup"><span data-stu-id="7da42-235">Version</span></span>                        | <span data-ttu-id="7da42-236">架構</span><span class="sxs-lookup"><span data-stu-id="7da42-236">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7da42-237">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-237">Windows Client</span></span>                | <span data-ttu-id="7da42-238">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7da42-238">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7da42-239">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-239">x64, x86</span></span>        |
| <span data-ttu-id="7da42-240">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-240">Windows 10 Client</span></span>             | <span data-ttu-id="7da42-241">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7da42-241">Version 1607+</span></span>                  | <span data-ttu-id="7da42-242">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-242">x64, x86</span></span>        |
| <span data-ttu-id="7da42-243">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7da42-243">Windows Server</span></span>                | <span data-ttu-id="7da42-244">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="7da42-244">2012 R2+</span></span>                       | <span data-ttu-id="7da42-245">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-245">x64, x86</span></span>        |
| <span data-ttu-id="7da42-246">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7da42-246">Nano Server</span></span>                   | <span data-ttu-id="7da42-247">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7da42-247">Version 1803+</span></span>                  | <span data-ttu-id="7da42-248">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7da42-248">x64, ARM32</span></span>      |

<span data-ttu-id="7da42-249">如需 .NET Core 3.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-249">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="7da42-250">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7da42-250">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="7da42-251">*.NET Core 3.0 目前不 ❌ 支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="7da42-251">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7da42-252">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7da42-252">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="7da42-253">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-253">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7da42-254">OS</span><span class="sxs-lookup"><span data-stu-id="7da42-254">OS</span></span>                            | <span data-ttu-id="7da42-255">版本</span><span class="sxs-lookup"><span data-stu-id="7da42-255">Version</span></span>                        | <span data-ttu-id="7da42-256">架構</span><span class="sxs-lookup"><span data-stu-id="7da42-256">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7da42-257">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-257">Windows Client</span></span>                | <span data-ttu-id="7da42-258">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7da42-258">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7da42-259">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-259">x64, x86</span></span>        |
| <span data-ttu-id="7da42-260">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-260">Windows 10 Client</span></span>             | <span data-ttu-id="7da42-261">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7da42-261">Version 1607+</span></span>                  | <span data-ttu-id="7da42-262">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-262">x64, x86</span></span>        |
| <span data-ttu-id="7da42-263">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7da42-263">Windows Server</span></span>                | <span data-ttu-id="7da42-264">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="7da42-264">2012 R2+</span></span>                       | <span data-ttu-id="7da42-265">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-265">x64, x86</span></span>        |
| <span data-ttu-id="7da42-266">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7da42-266">Nano Server</span></span>                   | <span data-ttu-id="7da42-267">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7da42-267">Version 1803+</span></span>                  | <span data-ttu-id="7da42-268">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7da42-268">x64, ARM32</span></span>      |

<span data-ttu-id="7da42-269">如需 .NET Core 3.0 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-269">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="7da42-270">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7da42-270">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="7da42-271">*.NET Core 2.2 目前不 ❌ 支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="7da42-271">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7da42-272">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7da42-272">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="7da42-273">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-273">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7da42-274">OS</span><span class="sxs-lookup"><span data-stu-id="7da42-274">OS</span></span>                            | <span data-ttu-id="7da42-275">版本</span><span class="sxs-lookup"><span data-stu-id="7da42-275">Version</span></span>                        | <span data-ttu-id="7da42-276">架構</span><span class="sxs-lookup"><span data-stu-id="7da42-276">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7da42-277">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-277">Windows Client</span></span>                | <span data-ttu-id="7da42-278">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7da42-278">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7da42-279">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-279">x64, x86</span></span>        |
| <span data-ttu-id="7da42-280">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-280">Windows 10 Client</span></span>             | <span data-ttu-id="7da42-281">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7da42-281">Version 1607+</span></span>                  | <span data-ttu-id="7da42-282">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-282">x64, x86</span></span>        |
| <span data-ttu-id="7da42-283">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7da42-283">Windows Server</span></span>                | <span data-ttu-id="7da42-284">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="7da42-284">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7da42-285">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-285">x64, x86</span></span>        |
| <span data-ttu-id="7da42-286">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7da42-286">Nano Server</span></span>                   | <span data-ttu-id="7da42-287">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7da42-287">Version 1803+</span></span>                   | <span data-ttu-id="7da42-288">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7da42-288">x64, ARM32</span></span>      |

<span data-ttu-id="7da42-289">如需 .NET Core 2.2 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-289">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="7da42-290">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7da42-290">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="7da42-291">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7da42-291">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7da42-292">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-292">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7da42-293">OS</span><span class="sxs-lookup"><span data-stu-id="7da42-293">OS</span></span>                            | <span data-ttu-id="7da42-294">版本</span><span class="sxs-lookup"><span data-stu-id="7da42-294">Version</span></span>                        | <span data-ttu-id="7da42-295">架構</span><span class="sxs-lookup"><span data-stu-id="7da42-295">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7da42-296">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-296">Windows Client</span></span>                | <span data-ttu-id="7da42-297">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7da42-297">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7da42-298">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-298">x64, x86</span></span>        |
| <span data-ttu-id="7da42-299">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7da42-299">Windows 10 Client</span></span>             | <span data-ttu-id="7da42-300">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7da42-300">Version 1607+</span></span>                  | <span data-ttu-id="7da42-301">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-301">x64, x86</span></span>        |
| <span data-ttu-id="7da42-302">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7da42-302">Windows Server</span></span>                | <span data-ttu-id="7da42-303">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="7da42-303">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7da42-304">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7da42-304">x64, x86</span></span>        |
| <span data-ttu-id="7da42-305">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7da42-305">Nano Server</span></span>                   | <span data-ttu-id="7da42-306">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7da42-306">Version 1803+</span></span>                  | <span data-ttu-id="7da42-307">64</span><span class="sxs-lookup"><span data-stu-id="7da42-307">x64,</span></span>            |

<span data-ttu-id="7da42-308">如需 .NET Core 2.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-308">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="7da42-309">Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7da42-309">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="7da42-310">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：</span><span class="sxs-lookup"><span data-stu-id="7da42-310">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="7da42-311">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="7da42-311">Windows 7 SP1 [ESU][esu]</span></span>
- <span data-ttu-id="7da42-312">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="7da42-312">Windows Vista SP 2</span></span>
- <span data-ttu-id="7da42-313">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7da42-313">Windows 8.1</span></span>
- <span data-ttu-id="7da42-314">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="7da42-314">Windows Server 2008 R2</span></span>
- <span data-ttu-id="7da42-315">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7da42-315">Windows Server 2012 R2</span></span>

<span data-ttu-id="7da42-316">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="7da42-316">Install the following:</span></span>

- <span data-ttu-id="7da42-317">[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件更新3。</span><span class="sxs-lookup"><span data-stu-id="7da42-317">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="7da42-318">KB2533623</span><span class="sxs-lookup"><span data-stu-id="7da42-318">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="7da42-319">如果您遇到下列其中一個錯誤，也需要先前的需求：</span><span class="sxs-lookup"><span data-stu-id="7da42-319">The previous requirements are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="7da42-320">程式無法啟動，因為您的電腦遺漏 *api-ms-win-crt-runtime-l1-1-0.dll* 。</span><span class="sxs-lookup"><span data-stu-id="7da42-320">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7da42-321">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="7da42-321">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7da42-322">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7da42-322">\- or -</span></span>
>
> <span data-ttu-id="7da42-323">程式無法啟動，因為您的電腦遺漏 *api-ms-win-cor-timezone-l1-1-0.dll* 。</span><span class="sxs-lookup"><span data-stu-id="7da42-323">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7da42-324">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="7da42-324">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7da42-325">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7da42-325">\- or -</span></span>
>
> <span data-ttu-id="7da42-326">找到程式庫 *hostfxr.dll* ，但從 *C： \\ \<path_to_app> \\hostfxr.dll* 載入該程式庫失敗。</span><span class="sxs-lookup"><span data-stu-id="7da42-326">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="7da42-327">使用 PowerShell 自動化安裝</span><span class="sxs-lookup"><span data-stu-id="7da42-327">Install with PowerShell automation</span></span>

<span data-ttu-id="7da42-328">[Dotnet 安裝腳本](../tools/dotnet-install-script.md)適用于執行時間的 CI 自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="7da42-328">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="7da42-329">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="7da42-329">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="7da42-330">腳本預設會安裝最新 [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="7da42-330">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7da42-331">您可以藉由指定參數來選擇特定版本 `Channel` 。</span><span class="sxs-lookup"><span data-stu-id="7da42-331">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="7da42-332">包含 `Runtime` 參數以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-332">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="7da42-333">否則，腳本會安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="7da42-333">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="7da42-334">藉由省略參數來安裝 SDK `-Runtime` 。</span><span class="sxs-lookup"><span data-stu-id="7da42-334">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="7da42-335">`-Channel`此範例會將此參數設定為 `Current` ，以安裝最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-335">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="7da42-336">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="7da42-336">Install with Visual Studio</span></span>

<span data-ttu-id="7da42-337">如果您使用 Visual Studio 開發 .NET 應用程式，下表將根據目標 .NET SDK 版本描述 Visual Studio 所需的最低版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-337">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="7da42-338">.NET SDK 版本</span><span class="sxs-lookup"><span data-stu-id="7da42-338">.NET SDK version</span></span>      | <span data-ttu-id="7da42-339">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="7da42-339">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="7da42-340">5.0</span><span class="sxs-lookup"><span data-stu-id="7da42-340">5.0</span></span>                   | <span data-ttu-id="7da42-341">Visual Studio 2019 16.8 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-341">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="7da42-342">3.1</span><span class="sxs-lookup"><span data-stu-id="7da42-342">3.1</span></span>                   | <span data-ttu-id="7da42-343">Visual Studio 2019 16.4 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-343">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="7da42-344">3.0</span><span class="sxs-lookup"><span data-stu-id="7da42-344">3.0</span></span>                   | <span data-ttu-id="7da42-345">Visual Studio 2019 16.3 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-345">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="7da42-346">2.2</span><span class="sxs-lookup"><span data-stu-id="7da42-346">2.2</span></span>                   | <span data-ttu-id="7da42-347">Visual Studio 2017 15.9 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-347">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="7da42-348">2.1</span><span class="sxs-lookup"><span data-stu-id="7da42-348">2.1</span></span>                   | <span data-ttu-id="7da42-349">Visual Studio 2017 15.7 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-349">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="7da42-350">如果您已經安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-350">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="7da42-351">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7da42-351">Open Visual Studio.</span></span>
01. <span data-ttu-id="7da42-352">選取 **Help**  >  **Microsoft Visual Studio** 的 [說明]。</span><span class="sxs-lookup"><span data-stu-id="7da42-352">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="7da42-353">閱讀 [ **關於** ] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7da42-353">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="7da42-354">Visual Studio 可以安裝最新的 .NET SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-354">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="7da42-355">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="7da42-355">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="7da42-356">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="7da42-356">Select a workload</span></span>

<span data-ttu-id="7da42-357">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列一或多個工作負載：</span><span class="sxs-lookup"><span data-stu-id="7da42-357">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="7da42-358">[**其他工具** 組] 區段中的 **.net Core 跨平臺開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="7da42-358">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="7da42-359">**Web & Cloud** 區段中的 **ASP.NET 和 網頁程式開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="7da42-359">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7da42-360">**Web & Cloud** 區段中的 **Azure 開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="7da42-360">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7da42-361">Desktop 中的 **.net 桌面開發** 工作負載 **& Mobile** 區段。</span><span class="sxs-lookup"><span data-stu-id="7da42-361">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="7da42-362">[![使用 .NET Core 工作負載的 Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="7da42-362">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="7da42-363">隨 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="7da42-363">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="7da42-364">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="7da42-364">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="7da42-365">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="7da42-365">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="7da42-366">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援很簡單。</span><span class="sxs-lookup"><span data-stu-id="7da42-366">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="7da42-367">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="7da42-367">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="7da42-368">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7da42-368">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="7da42-369">[從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。</span><span class="sxs-lookup"><span data-stu-id="7da42-369">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="7da42-370">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="7da42-370">Windows Installer</span></span>

<span data-ttu-id="7da42-371">.NET 的 [下載頁面](https://dotnet.microsoft.com/download/dotnet-core) 提供 Windows Installer 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7da42-371">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="7da42-372">當您使用 MSI 檔案來安裝 .NET 時< 您可以藉由設定和參數來自訂安裝路徑 `DOTNETHOME_X64` `DOTNETHOME_X86` ：</span><span class="sxs-lookup"><span data-stu-id="7da42-372">When you use the MSI files to install .NET< you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

## <a name="download-and-manually-install"></a><span data-ttu-id="7da42-373">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="7da42-373">Download and manually install</span></span>

<span data-ttu-id="7da42-374">您也可以下載並手動安裝 SDK 或執行時間，以替代適用于 .NET 的 Windows 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="7da42-374">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="7da42-375">手動安裝通常會做為持續整合測試的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="7da42-375">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="7da42-376">針對開發人員或使用者，通常最好是使用 [安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7da42-376">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="7da42-377">.NET SDK 和 .NET 執行時間都可以在下載之後手動安裝。</span><span class="sxs-lookup"><span data-stu-id="7da42-377">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="7da42-378">如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="7da42-378">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="7da42-379">首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：</span><span class="sxs-lookup"><span data-stu-id="7da42-379">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="7da42-380">.NET 5.0 下載</span><span class="sxs-lookup"><span data-stu-id="7da42-380">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="7da42-381">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="7da42-381">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="7da42-382">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="7da42-382">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="7da42-383">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="7da42-383">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="7da42-384">例如，建立用來將 .NET 解壓縮至的目錄 `%USERPROFILE%\dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="7da42-384">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="7da42-385">然後，將下載的 zip 檔案解壓縮到該目錄中。</span><span class="sxs-lookup"><span data-stu-id="7da42-385">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="7da42-386">根據預設，.NET CLI 命令和應用程式不會使用以這種方式安裝的 .NET，因此您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="7da42-386">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="7da42-387">若要這樣做，請變更應用程式啟動所在的環境變數：</span><span class="sxs-lookup"><span data-stu-id="7da42-387">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="7da42-388">這種方法可讓您將多個版本安裝到不同的位置，然後使用指向該位置的環境變數來執行應用程式，以明確選擇應用程式應使用的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="7da42-388">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="7da42-389">當 `DOTNET_MULTILEVEL_LOOKUP` 設定為時 `0` ，.net 會忽略任何全域安裝的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="7da42-389">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="7da42-390">移除該環境設定，讓 .NET 在選取最適合用來執行應用程式的架構時，考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="7da42-390">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="7da42-391">預設值通常是 `C:\Program Files\dotnet` 安裝程式安裝 .net 的位置。</span><span class="sxs-lookup"><span data-stu-id="7da42-391">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="7da42-392">Docker</span><span class="sxs-lookup"><span data-stu-id="7da42-392">Docker</span></span>

<span data-ttu-id="7da42-393">容器可提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="7da42-393">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="7da42-394">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="7da42-394">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="7da42-395">.NET 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="7da42-395">.NET can run in a Docker container.</span></span> <span data-ttu-id="7da42-396">官方 .NET Docker 映射會發佈至 Microsoft Container Registry (MCR) 並可在 [microsoft .net Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet)中找到。</span><span class="sxs-lookup"><span data-stu-id="7da42-396">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="7da42-397">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="7da42-397">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="7da42-398">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="7da42-398">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="7da42-399">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-aspnet) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="7da42-399">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="7da42-400">如需在 Docker 容器中使用 .NET 的詳細資訊，請參閱 [.net 和 Docker 簡介](../docker/introduction.md) 和 [範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-400">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7da42-401">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7da42-401">Next steps</span></span>

- <span data-ttu-id="7da42-402">[如何檢查是否已安裝 .net](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="7da42-402">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="7da42-403">[教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="7da42-403">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="7da42-404">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-404">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="7da42-405">[教學課程：將 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7da42-405">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
