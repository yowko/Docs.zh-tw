---
title: 在 Windows 上安裝 .NET Core
description: 瞭解您可以在哪些版本的 Windows 上安裝 .NET Core。
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: 12cffb78de803845a4b18adc70289993e67f64f1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538285"
---
# <a name="install-net-core-on-windows"></a><span data-ttu-id="7c5c4-103">在 Windows 上安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="7c5c4-103">Install .NET Core on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [安裝在 Windows 上](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [安裝在 Linux 上](linux.md)

<span data-ttu-id="7c5c4-107">在本文中，您將瞭解如何在 Windows 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-107">In this article, you'll learn how to install .NET Core on Windows.</span></span> <span data-ttu-id="7c5c4-108">.NET Core 是由執行時間和 SDK 所組成。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="7c5c4-109">執行時間是用來執行 .NET Core 應用程式，而且不一定會包含在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="7c5c4-110">SDK 是用來建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="7c5c4-111">.NET Core 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="7c5c4-112">.NET Core 的最新版本為3.1。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7c5c4-113">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="7c5c4-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="7c5c4-114">支援的版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-114">Supported releases</span></span>

<span data-ttu-id="7c5c4-115">下表列出目前支援的 .NET Core 版本，以及支援的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-115">The following table is a list of currently supported .NET Core releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="7c5c4-116">在 [.Net Core 的版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Windows 版本達到 [生命週期結束](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)後，才會持續支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-116">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="7c5c4-117">Windows 10 版本的服務結束日期會依版本分割。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="7c5c4-118">下表只考慮 **家用**版、 **專業**版、 **專業教育**版和 **工作站版專業** 版。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="7c5c4-119">查看 [Windows 生命週期的工作表](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) 以取得特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

- <span data-ttu-id="7c5c4-120">✔️表示仍然支援 Windows 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-120">A ✔️ indicates that the version of Windows or .NET Core is still supported.</span></span>
- <span data-ttu-id="7c5c4-121">❌表示該 windows 版本不支援 windows 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-121">A ❌ indicates that the version of Windows or .NET Core isn't supported on that Windows release.</span></span>
- <span data-ttu-id="7c5c4-122">當 Windows 版本和 .NET Core 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-122">When both a version of Windows and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="7c5c4-123">作業系統</span><span class="sxs-lookup"><span data-stu-id="7c5c4-123">Operating System</span></span>                      | <span data-ttu-id="7c5c4-124">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-124">.NET Core 2.1</span></span> | <span data-ttu-id="7c5c4-125">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-125">.NET Core 3.1</span></span> | <span data-ttu-id="7c5c4-126">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="7c5c4-126">.NET 5 Preview</span></span> |
|-----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="7c5c4-127">✔️ Windows 10，版本2004</span><span class="sxs-lookup"><span data-stu-id="7c5c4-127">✔️ Windows 10, Version 2004</span></span> | <span data-ttu-id="7c5c4-128">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-128">✔️ 2.1</span></span>        | <span data-ttu-id="7c5c4-129">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-129">✔️ 3.1</span></span>        | <span data-ttu-id="7c5c4-130">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-131">✔️ Windows 10，版本1909</span><span class="sxs-lookup"><span data-stu-id="7c5c4-131">✔️ Windows 10, Version 1909</span></span> | <span data-ttu-id="7c5c4-132">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-132">✔️ 2.1</span></span>        | <span data-ttu-id="7c5c4-133">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-133">✔️ 3.1</span></span>        | <span data-ttu-id="7c5c4-134">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-135">✔️ Windows 10，版本1903</span><span class="sxs-lookup"><span data-stu-id="7c5c4-135">✔️ Windows 10, Version 1903</span></span> | <span data-ttu-id="7c5c4-136">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-136">✔️ 2.1</span></span>        | <span data-ttu-id="7c5c4-137">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-137">✔️ 3.1</span></span>        | <span data-ttu-id="7c5c4-138">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-138">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-139">✔️ Windows 10，版本1809</span><span class="sxs-lookup"><span data-stu-id="7c5c4-139">✔️ Windows 10, Version 1809</span></span> | <span data-ttu-id="7c5c4-140">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-140">✔️ 2.1</span></span>        | <span data-ttu-id="7c5c4-141">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-141">✔️ 3.1</span></span>        | <span data-ttu-id="7c5c4-142">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-142">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-143">❌ Windows 10，版本1803</span><span class="sxs-lookup"><span data-stu-id="7c5c4-143">❌ Windows 10, Version 1803</span></span> | <span data-ttu-id="7c5c4-144">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-144">✔️ 2.1</span></span>        | <span data-ttu-id="7c5c4-145">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-145">❌ 3.1</span></span>        | <span data-ttu-id="7c5c4-146">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-146">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-147">❌ Windows 10，版本1709</span><span class="sxs-lookup"><span data-stu-id="7c5c4-147">❌ Windows 10, Version 1709</span></span> | <span data-ttu-id="7c5c4-148">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-148">❌ 2.1</span></span>        | <span data-ttu-id="7c5c4-149">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-149">❌ 3.1</span></span>        | <span data-ttu-id="7c5c4-150">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-150">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-151">❌ Windows 10，版本1703</span><span class="sxs-lookup"><span data-stu-id="7c5c4-151">❌ Windows 10, Version 1703</span></span> | <span data-ttu-id="7c5c4-152">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-152">❌ 2.1</span></span>        | <span data-ttu-id="7c5c4-153">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-153">❌ 3.1</span></span>        | <span data-ttu-id="7c5c4-154">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-154">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-155">❌ Windows 10，版本1607</span><span class="sxs-lookup"><span data-stu-id="7c5c4-155">❌ Windows 10, Version 1607</span></span> | <span data-ttu-id="7c5c4-156">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-156">❌ 2.1</span></span>        | <span data-ttu-id="7c5c4-157">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-157">❌ 3.1</span></span>        | <span data-ttu-id="7c5c4-158">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-158">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-159">❌ Windows 10，版本1511</span><span class="sxs-lookup"><span data-stu-id="7c5c4-159">❌ Windows 10, Version 1511</span></span> | <span data-ttu-id="7c5c4-160">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-160">❌ 2.1</span></span>        | <span data-ttu-id="7c5c4-161">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-161">❌ 3.1</span></span>        | <span data-ttu-id="7c5c4-162">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-162">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7c5c4-163">❌ Windows 10，版本1507</span><span class="sxs-lookup"><span data-stu-id="7c5c4-163">❌ Windows 10, Version 1507</span></span> | <span data-ttu-id="7c5c4-164">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-164">❌ 2.1</span></span>        | <span data-ttu-id="7c5c4-165">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-165">❌ 3.1</span></span>        | <span data-ttu-id="7c5c4-166">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7c5c4-166">❌ 5.0 Preview</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="7c5c4-167">不支援的版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-167">Unsupported releases</span></span>

<span data-ttu-id="7c5c4-168">不再支援下列 .NET Core 版本 ❌ 。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-168">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="7c5c4-169">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-169">The downloads for these still remain published:</span></span>

- <span data-ttu-id="7c5c4-170">3.0</span><span class="sxs-lookup"><span data-stu-id="7c5c4-170">3.0</span></span>
- <span data-ttu-id="7c5c4-171">2.2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-171">2.2</span></span>
- <span data-ttu-id="7c5c4-172">2.0</span><span class="sxs-lookup"><span data-stu-id="7c5c4-172">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="7c5c4-173">執行時間資訊</span><span class="sxs-lookup"><span data-stu-id="7c5c4-173">Runtime information</span></span>

<span data-ttu-id="7c5c4-174">執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-174">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="7c5c4-175">當應用程式作者發佈應用程式時，他們可以在其應用程式中包含執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-175">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="7c5c4-176">如果未包含執行時間，則會由使用者自行安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-176">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="7c5c4-177">您可以在 Windows 上安裝三個不同的執行時間：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-177">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="7c5c4-178">*ASP.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="7c5c4-178">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="7c5c4-179">執行 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-179">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="7c5c4-180">包含 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-180">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="7c5c4-181">*桌面執行時間*</span><span class="sxs-lookup"><span data-stu-id="7c5c4-181">*Desktop runtime*</span></span>\
<span data-ttu-id="7c5c4-182">執行適用于 Windows 的 .NET Core WPF 和 .NET Core Windows Forms 桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-182">Runs .NET Core WPF and .NET Core Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="7c5c4-183">包含 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-183">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="7c5c4-184">*.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="7c5c4-184">*.NET Core runtime*</span></span>\
<span data-ttu-id="7c5c4-185">此執行時間是最簡單的執行時間，不包含任何其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-185">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="7c5c4-186">強烈建議您安裝 *ASP.NET Core 運行* 時間和 *桌面運行* 時間，以獲得與 .net Core 應用程式的最佳相容性。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-186">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7c5c4-187">下載 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="7c5c4-187">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="7c5c4-188">SDK 資訊</span><span class="sxs-lookup"><span data-stu-id="7c5c4-188">SDK information</span></span>

<span data-ttu-id="7c5c4-189">SDK 可用來建立及發佈 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-189">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="7c5c4-190">安裝 SDK 包含三個 [運行](#runtime-information)時間： ASP.NET Core、Desktop 和 .net Core。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-190">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7c5c4-191">下載 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7c5c4-191">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="7c5c4-192">相依性</span><span class="sxs-lookup"><span data-stu-id="7c5c4-192">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="7c5c4-193">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-193">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="7c5c4-194">.NET Core 3.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-194">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7c5c4-195">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-195">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7c5c4-196">OS</span><span class="sxs-lookup"><span data-stu-id="7c5c4-196">OS</span></span>                            | <span data-ttu-id="7c5c4-197">版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-197">Version</span></span>                        | <span data-ttu-id="7c5c4-198">架構</span><span class="sxs-lookup"><span data-stu-id="7c5c4-198">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7c5c4-199">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-199">Windows Client</span></span>                | <span data-ttu-id="7c5c4-200">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-200">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7c5c4-201">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-201">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-202">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-202">Windows 10 Client</span></span>             | <span data-ttu-id="7c5c4-203">版本 1609 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-203">Version 1609+</span></span>                  | <span data-ttu-id="7c5c4-204">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-204">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-205">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-205">Windows Server</span></span>                | <span data-ttu-id="7c5c4-206">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-206">2012 R2+</span></span>                       | <span data-ttu-id="7c5c4-207">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-207">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-208">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-208">Nano Server</span></span>                   | <span data-ttu-id="7c5c4-209">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-209">Version 1803+</span></span>                  | <span data-ttu-id="7c5c4-210">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7c5c4-210">x64, ARM32</span></span>      |

<span data-ttu-id="7c5c4-211">如需 .NET Core 3.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-211">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="7c5c4-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7c5c4-212">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="7c5c4-213">*.NET Core 3.0 目前不支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="7c5c4-213">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7c5c4-214">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-214">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="7c5c4-215">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7c5c4-216">OS</span><span class="sxs-lookup"><span data-stu-id="7c5c4-216">OS</span></span>                            | <span data-ttu-id="7c5c4-217">版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-217">Version</span></span>                        | <span data-ttu-id="7c5c4-218">架構</span><span class="sxs-lookup"><span data-stu-id="7c5c4-218">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7c5c4-219">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-219">Windows Client</span></span>                | <span data-ttu-id="7c5c4-220">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-220">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7c5c4-221">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-221">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-222">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-222">Windows 10 Client</span></span>             | <span data-ttu-id="7c5c4-223">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-223">Version 1607+</span></span>                  | <span data-ttu-id="7c5c4-224">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-224">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-225">Windows Server</span></span>                | <span data-ttu-id="7c5c4-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-226">2012 R2+</span></span>                       | <span data-ttu-id="7c5c4-227">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-227">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-228">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-228">Nano Server</span></span>                   | <span data-ttu-id="7c5c4-229">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-229">Version 1803+</span></span>                  | <span data-ttu-id="7c5c4-230">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7c5c4-230">x64, ARM32</span></span>      |

<span data-ttu-id="7c5c4-231">如需 .NET Core 3.0 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-231">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="7c5c4-232">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-232">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="7c5c4-233">*.NET Core 2.2 目前不支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="7c5c4-233">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7c5c4-234">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-234">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="7c5c4-235">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-235">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7c5c4-236">OS</span><span class="sxs-lookup"><span data-stu-id="7c5c4-236">OS</span></span>                            | <span data-ttu-id="7c5c4-237">版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-237">Version</span></span>                        | <span data-ttu-id="7c5c4-238">架構</span><span class="sxs-lookup"><span data-stu-id="7c5c4-238">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7c5c4-239">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-239">Windows Client</span></span>                | <span data-ttu-id="7c5c4-240">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-240">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7c5c4-241">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-241">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-242">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-242">Windows 10 Client</span></span>             | <span data-ttu-id="7c5c4-243">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-243">Version 1607+</span></span>                  | <span data-ttu-id="7c5c4-244">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-244">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-245">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-245">Windows Server</span></span>                | <span data-ttu-id="7c5c4-246">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-246">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7c5c4-247">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-247">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-248">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-248">Nano Server</span></span>                   | <span data-ttu-id="7c5c4-249">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-249">Version 1803+</span></span>                   | <span data-ttu-id="7c5c4-250">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7c5c4-250">x64, ARM32</span></span>      |

<span data-ttu-id="7c5c4-251">如需 .NET Core 2.2 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-251">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="7c5c4-252">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-252">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="7c5c4-253">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-253">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7c5c4-254">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-254">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7c5c4-255">OS</span><span class="sxs-lookup"><span data-stu-id="7c5c4-255">OS</span></span>                            | <span data-ttu-id="7c5c4-256">版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-256">Version</span></span>                        | <span data-ttu-id="7c5c4-257">架構</span><span class="sxs-lookup"><span data-stu-id="7c5c4-257">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7c5c4-258">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-258">Windows Client</span></span>                | <span data-ttu-id="7c5c4-259">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-259">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7c5c4-260">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-260">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-261">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c5c4-261">Windows 10 Client</span></span>             | <span data-ttu-id="7c5c4-262">1607版 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-262">Version 1607+</span></span>                  | <span data-ttu-id="7c5c4-263">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-263">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-264">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-264">Windows Server</span></span>                | <span data-ttu-id="7c5c4-265">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-265">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7c5c4-266">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7c5c4-266">x64, x86</span></span>        |
| <span data-ttu-id="7c5c4-267">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7c5c4-267">Nano Server</span></span>                   | <span data-ttu-id="7c5c4-268">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="7c5c4-268">Version 1803+</span></span>                  | <span data-ttu-id="7c5c4-269">64</span><span class="sxs-lookup"><span data-stu-id="7c5c4-269">x64,</span></span>            |

<span data-ttu-id="7c5c4-270">如需 .NET Core 2.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-270">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="7c5c4-271">Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-271">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="7c5c4-272">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-272">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="7c5c4-273">❌ Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-273">❌ Windows 7 SP1</span></span>
- <span data-ttu-id="7c5c4-274">❌ Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-274">❌ Windows Vista SP 2</span></span>
- <span data-ttu-id="7c5c4-275">✔️ Windows 8。1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-275">✔️ Windows 8.1</span></span>
- <span data-ttu-id="7c5c4-276">✔️ Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-276">✔️ Windows Server 2008 R2</span></span>
- <span data-ttu-id="7c5c4-277">✔️ Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-277">✔️ Windows Server 2012 R2</span></span>

<span data-ttu-id="7c5c4-278">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-278">Install the following:</span></span>

- <span data-ttu-id="7c5c4-279">[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件更新3。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-279">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="7c5c4-280">KB2533623</span><span class="sxs-lookup"><span data-stu-id="7c5c4-280">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="7c5c4-281">如果您遇到下列其中一個錯誤，也需要上述需求：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-281">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="7c5c4-282">程式無法啟動，因為您的電腦遺漏 *api-ms-win-crt-runtime-l1-1-0.dll* 。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-282">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7c5c4-283">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-283">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7c5c4-284">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7c5c4-284">\- or -</span></span>
>
> <span data-ttu-id="7c5c4-285">程式無法啟動，因為您的電腦遺漏 *api-ms-win-cor-timezone-l1-1-0.dll* 。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-285">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7c5c4-286">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-286">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7c5c4-287">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7c5c4-287">\- or -</span></span>
>
> <span data-ttu-id="7c5c4-288">找到程式庫*hostfxr.dll* ，但從*C： \\ \<path_to_app> \\hostfxr.dll*載入該程式庫失敗。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-288">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="7c5c4-289">使用 PowerShell 自動化安裝</span><span class="sxs-lookup"><span data-stu-id="7c5c4-289">Install with PowerShell automation</span></span>

<span data-ttu-id="7c5c4-290">[Dotnet 安裝腳本](../tools/dotnet-install-script.md)適用于執行時間的 CI 自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-290">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="7c5c4-291">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-291">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="7c5c4-292">腳本預設會安裝最新 [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-292">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7c5c4-293">您可以藉由指定參數來選擇特定版本 `Channel` 。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-293">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="7c5c4-294">包含 `Runtime` 參數以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-294">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="7c5c4-295">否則，腳本會安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-295">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

<span data-ttu-id="7c5c4-296">藉由省略參數來安裝 SDK `-Runtime` 。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-296">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="7c5c4-297">`-Channel`此範例會將此參數設定為 `Current` ，以安裝最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-297">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="7c5c4-298">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="7c5c4-298">Install with Visual Studio</span></span>

<span data-ttu-id="7c5c4-299">如果您使用 Visual Studio 來開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最小必要版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-299">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="7c5c4-300">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-300">.NET Core SDK version</span></span> | <span data-ttu-id="7c5c4-301">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="7c5c4-301">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="7c5c4-302">3.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-302">3.1</span></span>                   | <span data-ttu-id="7c5c4-303">Visual Studio 2019 16.4 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-303">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="7c5c4-304">3.0</span><span class="sxs-lookup"><span data-stu-id="7c5c4-304">3.0</span></span>                   | <span data-ttu-id="7c5c4-305">Visual Studio 2019 16.3 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-305">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="7c5c4-306">2.2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-306">2.2</span></span>                   | <span data-ttu-id="7c5c4-307">Visual Studio 2017 15.9 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-307">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="7c5c4-308">2.1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-308">2.1</span></span>                   | <span data-ttu-id="7c5c4-309">Visual Studio 2017 15.7 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-309">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="7c5c4-310">如果您已經安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-310">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="7c5c4-311">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-311">Open Visual Studio.</span></span>
01. <span data-ttu-id="7c5c4-312">選取**Help**  >  **Microsoft Visual Studio**的 [說明]。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-312">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="7c5c4-313">閱讀 [ **關於** ] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-313">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="7c5c4-314">Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-314">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="7c5c4-315">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-315">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="7c5c4-316">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="7c5c4-316">Select a workload</span></span>

<span data-ttu-id="7c5c4-317">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列一或多個工作負載：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-317">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="7c5c4-318">[**其他工具**組] 區段中的 **.net Core 跨平臺開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-318">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="7c5c4-319">**Web & Cloud**區段中的**ASP.NET 和 網頁程式開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-319">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7c5c4-320">**Web & Cloud**區段中的**Azure 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-320">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7c5c4-321">Desktop 中的 **.net 桌面開發** 工作負載 **& Mobile** 區段。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-321">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="7c5c4-322">[![使用 .NET Core 工作負載的 Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="7c5c4-322">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="7c5c4-323">隨 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="7c5c4-323">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="7c5c4-324">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-324">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="7c5c4-325">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-325">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="7c5c4-326">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援很簡單。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-326">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="7c5c4-327">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-327">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="7c5c4-328">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-328">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="7c5c4-329">[從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-329">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="7c5c4-330">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="7c5c4-330">Download and manually install</span></span>

<span data-ttu-id="7c5c4-331">除了 .NET Core 的 Windows 安裝程式，您也可以下載並手動安裝 SDK 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-331">As an alternative to the Windows installers for .NET Core, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="7c5c4-332">手動安裝通常會做為持續整合測試的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-332">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="7c5c4-333">針對開發人員或使用者，通常最好是使用 [安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-333">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="7c5c4-334">.NET Core SDK 和 .NET Core 執行時間都可以在下載後以手動方式安裝。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-334">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="7c5c4-335">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-335">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="7c5c4-336">首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-336">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="7c5c4-337">✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="7c5c4-337">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="7c5c4-338">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="7c5c4-338">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="7c5c4-339">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="7c5c4-339">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="7c5c4-340">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="7c5c4-340">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="7c5c4-341">例如，建立用來將 .NET 解壓縮至的目錄 `%USERPROFILE%\dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-341">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="7c5c4-342">然後，將下載的 zip 檔案解壓縮到該目錄中。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-342">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="7c5c4-343">根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core，您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-343">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="7c5c4-344">若要這樣做，請變更應用程式啟動所在的環境變數：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-344">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="7c5c4-345">這種方法可讓您將多個版本安裝到不同的位置，然後使用指向該位置的環境變數來執行應用程式，以明確選擇應用程式應使用的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-345">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="7c5c4-346">當 `DOTNET_MULTILEVEL_LOOKUP` 設定為時 `0` ，.net core 會忽略任何全域安裝的 .net core 版本。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-346">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET Core ignores any globally installed .NET Core version.</span></span> <span data-ttu-id="7c5c4-347">移除該環境設定，讓 .NET Core 在選取最適合用來執行應用程式的架構時，考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-347">Remove that environment setting to let .NET Core consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="7c5c4-348">預設值通常是 `C:\Program Files\dotnet` 安裝程式安裝 .Net Core 的位置。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-348">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET Core.</span></span>

## <a name="docker"></a><span data-ttu-id="7c5c4-349">Docker</span><span class="sxs-lookup"><span data-stu-id="7c5c4-349">Docker</span></span>

<span data-ttu-id="7c5c4-350">容器可提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-350">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="7c5c4-351">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-351">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="7c5c4-352">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-352">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="7c5c4-353">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-353">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="7c5c4-354">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-354">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="7c5c4-355">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-355">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="7c5c4-356">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-356">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="7c5c4-357">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱 [.net 和 Docker 簡介](../docker/introduction.md) 和 [範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-357">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c5c4-358">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7c5c4-358">Next steps</span></span>

- <span data-ttu-id="7c5c4-359">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-359">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="7c5c4-360">[教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-360">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="7c5c4-361">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-361">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="7c5c4-362">[教學課程：將 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-362">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>
