---
title: 在 Windows 上安裝 .NET Core
description: 瞭解您可以在上安裝 .NET Core 的 Windows 版本。
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: e26494de7e9246b241cb965d8d735a781aab5478
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85804482"
---
# <a name="install-net-core-on-windows"></a><span data-ttu-id="4cb0c-103">在 Windows 上安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cb0c-103">Install .NET Core on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [在 Linux 上安裝](linux.md)

<span data-ttu-id="4cb0c-107">在本文中，您將瞭解如何在 Windows 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-107">In this article, you'll learn how to install .NET Core on Windows.</span></span> <span data-ttu-id="4cb0c-108">.NET Core 是由執行時間和 SDK 所組成。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="4cb0c-109">執行時間是用來執行 .NET Core 應用程式，且不一定會包含在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="4cb0c-110">SDK 可用來建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="4cb0c-111">.NET Core 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="4cb0c-112">.NET Core 的最新版本為3.1。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-112">The latest version of .NET Core is 3.1.</span></span>

[<span data-ttu-id="4cb0c-113">下載 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-113">Download .NET Core.</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="4cb0c-114">支援的版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-114">Supported releases</span></span>

<span data-ttu-id="4cb0c-115">下表列出目前支援的 .NET Core 版本，以及支援的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-115">The following table is a list of currently supported .NET Core releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="4cb0c-116">這些版本持續支援，直到[.Net Core 版本達到支援的終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或[Windows 版本達到生命週期的結束](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)為止。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-116">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="4cb0c-117">Windows 10 版本的服務結束日期是依版本分割。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="4cb0c-118">下表只會考慮**Home**、 **Pro**、 **Pro 教育**和**適用于工作站**版本的 pro。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="4cb0c-119">如需特定詳細資料，請參閱[Windows 生命週期事實表](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

- <span data-ttu-id="4cb0c-120">✔️表示仍然支援 Windows 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-120">A ✔️ indicates that the version of Windows or .NET Core is still supported.</span></span>
- <span data-ttu-id="4cb0c-121">A ❌ 表示該 windows 版本不支援 windows 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-121">A ❌ indicates that the version of Windows or .NET Core isn't supported on that Windows release.</span></span>
- <span data-ttu-id="4cb0c-122">當 Windows 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-122">When both a version of Windows and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="4cb0c-123">作業系統</span><span class="sxs-lookup"><span data-stu-id="4cb0c-123">Operating System</span></span>                      | <span data-ttu-id="4cb0c-124">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-124">.NET Core 2.1</span></span> | <span data-ttu-id="4cb0c-125">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-125">.NET Core 3.1</span></span> | <span data-ttu-id="4cb0c-126">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="4cb0c-126">.NET 5 Preview</span></span> |
|-----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="4cb0c-127">✔️ Windows 10，版本2004</span><span class="sxs-lookup"><span data-stu-id="4cb0c-127">✔️ Windows 10, Version 2004</span></span> | <span data-ttu-id="4cb0c-128">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-128">✔️ 2.1</span></span>        | <span data-ttu-id="4cb0c-129">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-129">✔️ 3.1</span></span>        | <span data-ttu-id="4cb0c-130">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="4cb0c-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-131">✔️ Windows 10，版本1909</span><span class="sxs-lookup"><span data-stu-id="4cb0c-131">✔️ Windows 10, Version 1909</span></span> | <span data-ttu-id="4cb0c-132">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-132">✔️ 2.1</span></span>        | <span data-ttu-id="4cb0c-133">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-133">✔️ 3.1</span></span>        | <span data-ttu-id="4cb0c-134">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="4cb0c-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-135">✔️ Windows 10，版本1903</span><span class="sxs-lookup"><span data-stu-id="4cb0c-135">✔️ Windows 10, Version 1903</span></span> | <span data-ttu-id="4cb0c-136">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-136">✔️ 2.1</span></span>        | <span data-ttu-id="4cb0c-137">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-137">✔️ 3.1</span></span>        | <span data-ttu-id="4cb0c-138">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="4cb0c-138">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-139">✔️ Windows 10，版本1809</span><span class="sxs-lookup"><span data-stu-id="4cb0c-139">✔️ Windows 10, Version 1809</span></span> | <span data-ttu-id="4cb0c-140">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-140">✔️ 2.1</span></span>        | <span data-ttu-id="4cb0c-141">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-141">✔️ 3.1</span></span>        | <span data-ttu-id="4cb0c-142">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="4cb0c-142">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-143">❌Windows 10 版本1803</span><span class="sxs-lookup"><span data-stu-id="4cb0c-143">❌ Windows 10, Version 1803</span></span> | <span data-ttu-id="4cb0c-144">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-144">✔️ 2.1</span></span>        | <span data-ttu-id="4cb0c-145">❌3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-145">❌ 3.1</span></span>        | <span data-ttu-id="4cb0c-146">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="4cb0c-146">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-147">❌Windows 10 版本1709</span><span class="sxs-lookup"><span data-stu-id="4cb0c-147">❌ Windows 10, Version 1709</span></span> | <span data-ttu-id="4cb0c-148">❌2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-148">❌ 2.1</span></span>        | <span data-ttu-id="4cb0c-149">❌3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-149">❌ 3.1</span></span>        | <span data-ttu-id="4cb0c-150">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="4cb0c-150">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-151">❌Windows 10 版本1703</span><span class="sxs-lookup"><span data-stu-id="4cb0c-151">❌ Windows 10, Version 1703</span></span> | <span data-ttu-id="4cb0c-152">❌2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-152">❌ 2.1</span></span>        | <span data-ttu-id="4cb0c-153">❌3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-153">❌ 3.1</span></span>        | <span data-ttu-id="4cb0c-154">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="4cb0c-154">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-155">❌Windows 10 版本1607</span><span class="sxs-lookup"><span data-stu-id="4cb0c-155">❌ Windows 10, Version 1607</span></span> | <span data-ttu-id="4cb0c-156">❌2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-156">❌ 2.1</span></span>        | <span data-ttu-id="4cb0c-157">❌3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-157">❌ 3.1</span></span>        | <span data-ttu-id="4cb0c-158">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="4cb0c-158">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-159">❌Windows 10 版本1511</span><span class="sxs-lookup"><span data-stu-id="4cb0c-159">❌ Windows 10, Version 1511</span></span> | <span data-ttu-id="4cb0c-160">❌2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-160">❌ 2.1</span></span>        | <span data-ttu-id="4cb0c-161">❌3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-161">❌ 3.1</span></span>        | <span data-ttu-id="4cb0c-162">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="4cb0c-162">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="4cb0c-163">❌Windows 10 版本1507</span><span class="sxs-lookup"><span data-stu-id="4cb0c-163">❌ Windows 10, Version 1507</span></span> | <span data-ttu-id="4cb0c-164">❌2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-164">❌ 2.1</span></span>        | <span data-ttu-id="4cb0c-165">❌3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-165">❌ 3.1</span></span>        | <span data-ttu-id="4cb0c-166">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="4cb0c-166">❌ 5.0 Preview</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="4cb0c-167">不支援的版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-167">Unsupported releases</span></span>

<span data-ttu-id="4cb0c-168">已不再支援下列 .NET Core 版本 ❌ 。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-168">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="4cb0c-169">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-169">The downloads for these still remain published:</span></span>

- <span data-ttu-id="4cb0c-170">3.0</span><span class="sxs-lookup"><span data-stu-id="4cb0c-170">3.0</span></span>
- <span data-ttu-id="4cb0c-171">2.2</span><span class="sxs-lookup"><span data-stu-id="4cb0c-171">2.2</span></span>
- <span data-ttu-id="4cb0c-172">2.0</span><span class="sxs-lookup"><span data-stu-id="4cb0c-172">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="4cb0c-173">執行時間資訊</span><span class="sxs-lookup"><span data-stu-id="4cb0c-173">Runtime information</span></span>

<span data-ttu-id="4cb0c-174">執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-174">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="4cb0c-175">當應用程式作者發行應用程式時，他們可以將執行時間包含在其應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-175">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="4cb0c-176">如果它們不包含執行時間，則會由使用者自行安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-176">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="4cb0c-177">您可以在 Windows 上安裝三種不同的執行時間：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-177">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="4cb0c-178">*ASP.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="4cb0c-178">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="4cb0c-179">執行 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-179">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="4cb0c-180">包含 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-180">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="4cb0c-181">*桌面執行時間*</span><span class="sxs-lookup"><span data-stu-id="4cb0c-181">*Desktop runtime*</span></span>\
<span data-ttu-id="4cb0c-182">執行適用于 Windows 的 .NET Core WPF 和 .NET Core Windows Forms 桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-182">Runs .NET Core WPF and .NET Core Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="4cb0c-183">包含 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-183">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="4cb0c-184">*.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="4cb0c-184">*.NET Core runtime*</span></span>\
<span data-ttu-id="4cb0c-185">此執行時間是最簡單的執行時間，不包含任何其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-185">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="4cb0c-186">強烈建議您同時安裝*ASP.NET Core 運行*時間和*桌面運行*時間，以獲得與 .net Core 應用程式的最佳相容性。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-186">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET Core apps.</span></span>

[<span data-ttu-id="4cb0c-187">下載 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-187">Download .NET Core Runtime.</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="4cb0c-188">SDK 資訊</span><span class="sxs-lookup"><span data-stu-id="4cb0c-188">SDK information</span></span>

<span data-ttu-id="4cb0c-189">SDK 可用來建立及發佈 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-189">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="4cb0c-190">安裝 SDK 包括三個[運行](#runtime-information)時間： ASP.NET Core、桌面和 .net Core。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-190">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET Core.</span></span>

[<span data-ttu-id="4cb0c-191">下載 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-191">Download .NET Core SDK.</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="4cb0c-192">相依性</span><span class="sxs-lookup"><span data-stu-id="4cb0c-192">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="4cb0c-193">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-193">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="4cb0c-194">.NET Core 3.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-194">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="4cb0c-195">`+`代表最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-195">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="4cb0c-196">OS</span><span class="sxs-lookup"><span data-stu-id="4cb0c-196">OS</span></span>                            | <span data-ttu-id="4cb0c-197">版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-197">Version</span></span>                        | <span data-ttu-id="4cb0c-198">架構</span><span class="sxs-lookup"><span data-stu-id="4cb0c-198">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="4cb0c-199">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-199">Windows Client</span></span>                | <span data-ttu-id="4cb0c-200">8.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-200">8.1</span></span>                            | <span data-ttu-id="4cb0c-201">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-201">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-202">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-202">Windows 10 Client</span></span>             | <span data-ttu-id="4cb0c-203">版本 1609 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-203">Version 1609+</span></span>                  | <span data-ttu-id="4cb0c-204">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-204">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-205">Windows Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-205">Windows Server</span></span>                | <span data-ttu-id="4cb0c-206">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-206">2012 R2+</span></span>                       | <span data-ttu-id="4cb0c-207">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-207">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-208">Nano Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-208">Nano Server</span></span>                   | <span data-ttu-id="4cb0c-209">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-209">Version 1803+</span></span>                  | <span data-ttu-id="4cb0c-210">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="4cb0c-210">x64, ARM32</span></span>      |

<span data-ttu-id="4cb0c-211">如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-211">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="4cb0c-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4cb0c-212">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="4cb0c-213">*.NET Core 3.0 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="4cb0c-213">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="4cb0c-214">.NET Core 3.0 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-214">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="4cb0c-215">`+`代表最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="4cb0c-216">OS</span><span class="sxs-lookup"><span data-stu-id="4cb0c-216">OS</span></span>                            | <span data-ttu-id="4cb0c-217">版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-217">Version</span></span>                        | <span data-ttu-id="4cb0c-218">架構</span><span class="sxs-lookup"><span data-stu-id="4cb0c-218">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="4cb0c-219">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-219">Windows Client</span></span>                | <span data-ttu-id="4cb0c-220">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-220">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="4cb0c-221">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-221">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-222">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-222">Windows 10 Client</span></span>             | <span data-ttu-id="4cb0c-223">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-223">Version 1607+</span></span>                  | <span data-ttu-id="4cb0c-224">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-224">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-225">Windows Server</span></span>                | <span data-ttu-id="4cb0c-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-226">2012 R2+</span></span>                       | <span data-ttu-id="4cb0c-227">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-227">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-228">Nano Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-228">Nano Server</span></span>                   | <span data-ttu-id="4cb0c-229">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-229">Version 1803+</span></span>                  | <span data-ttu-id="4cb0c-230">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="4cb0c-230">x64, ARM32</span></span>      |

<span data-ttu-id="4cb0c-231">如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-231">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="4cb0c-232">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="4cb0c-232">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="4cb0c-233">*.NET Core 2.2 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*</span><span class="sxs-lookup"><span data-stu-id="4cb0c-233">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="4cb0c-234">.NET Core 2.2 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-234">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="4cb0c-235">`+`代表最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-235">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="4cb0c-236">OS</span><span class="sxs-lookup"><span data-stu-id="4cb0c-236">OS</span></span>                            | <span data-ttu-id="4cb0c-237">版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-237">Version</span></span>                        | <span data-ttu-id="4cb0c-238">架構</span><span class="sxs-lookup"><span data-stu-id="4cb0c-238">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="4cb0c-239">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-239">Windows Client</span></span>                | <span data-ttu-id="4cb0c-240">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-240">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="4cb0c-241">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-241">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-242">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-242">Windows 10 Client</span></span>             | <span data-ttu-id="4cb0c-243">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-243">Version 1607+</span></span>                  | <span data-ttu-id="4cb0c-244">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-244">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-245">Windows Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-245">Windows Server</span></span>                | <span data-ttu-id="4cb0c-246">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-246">2008 R2 SP1+</span></span>                   | <span data-ttu-id="4cb0c-247">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-247">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-248">Nano Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-248">Nano Server</span></span>                   | <span data-ttu-id="4cb0c-249">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-249">Version 1803+</span></span>                   | <span data-ttu-id="4cb0c-250">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="4cb0c-250">x64, ARM32</span></span>      |

<span data-ttu-id="4cb0c-251">如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-251">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="4cb0c-252">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-252">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="4cb0c-253">.NET Core 2.1 支援下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-253">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="4cb0c-254">`+`代表最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-254">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="4cb0c-255">OS</span><span class="sxs-lookup"><span data-stu-id="4cb0c-255">OS</span></span>                            | <span data-ttu-id="4cb0c-256">版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-256">Version</span></span>                        | <span data-ttu-id="4cb0c-257">架構</span><span class="sxs-lookup"><span data-stu-id="4cb0c-257">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="4cb0c-258">Windows 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-258">Windows Client</span></span>                | <span data-ttu-id="4cb0c-259">7 SP1 +、8。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-259">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="4cb0c-260">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-260">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-261">Windows 10 用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb0c-261">Windows 10 Client</span></span>             | <span data-ttu-id="4cb0c-262">版本 1607 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-262">Version 1607+</span></span>                  | <span data-ttu-id="4cb0c-263">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-263">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-264">Windows Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-264">Windows Server</span></span>                | <span data-ttu-id="4cb0c-265">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-265">2008 R2 SP1+</span></span>                   | <span data-ttu-id="4cb0c-266">x64、x86</span><span class="sxs-lookup"><span data-stu-id="4cb0c-266">x64, x86</span></span>        |
| <span data-ttu-id="4cb0c-267">Nano Server</span><span class="sxs-lookup"><span data-stu-id="4cb0c-267">Nano Server</span></span>                   | <span data-ttu-id="4cb0c-268">版本 1803 +</span><span class="sxs-lookup"><span data-stu-id="4cb0c-268">Version 1803+</span></span>                  | <span data-ttu-id="4cb0c-269">x64</span><span class="sxs-lookup"><span data-stu-id="4cb0c-269">x64,</span></span>            |

<span data-ttu-id="4cb0c-270">如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-270">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="4cb0c-271">Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4cb0c-271">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="4cb0c-272">如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-272">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="4cb0c-273">❌Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-273">❌ Windows 7 SP1</span></span>
- <span data-ttu-id="4cb0c-274">❌Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="4cb0c-274">❌ Windows Vista SP 2</span></span>
- <span data-ttu-id="4cb0c-275">✔️ Windows 8。1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-275">✔️ Windows 8.1</span></span>
- <span data-ttu-id="4cb0c-276">✔️ Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4cb0c-276">✔️ Windows Server 2008 R2</span></span>
- <span data-ttu-id="4cb0c-277">✔️ Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4cb0c-277">✔️ Windows Server 2012 R2</span></span>

<span data-ttu-id="4cb0c-278">安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-278">Install the following:</span></span>

- <span data-ttu-id="4cb0c-279">[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件 Update 3。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-279">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="4cb0c-280">KB2533623</span><span class="sxs-lookup"><span data-stu-id="4cb0c-280">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="4cb0c-281">如果您遇到下列其中一個錯誤，也需要上述需求：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-281">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="4cb0c-282">程式無法啟動，因為電腦中遺失*api-ms-win-crt-runtime-l1-1-0.dll* 。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-282">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="4cb0c-283">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-283">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="4cb0c-284">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="4cb0c-284">\- or -</span></span>
>
> <span data-ttu-id="4cb0c-285">程式無法啟動，因為電腦中遺失*api-ms-win-cor-timezone-l1-1-0.dll* 。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-285">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="4cb0c-286">請嘗試重新安裝程式以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-286">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="4cb0c-287">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="4cb0c-287">\- or -</span></span>
>
> <span data-ttu-id="4cb0c-288">找到程式庫*hostfxr.dll* ，但從*C： \\ \<path_to_app> \\hostfxr.dll*載入它失敗。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-288">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="4cb0c-289">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="4cb0c-289">Install with PowerShell automation</span></span>

<span data-ttu-id="4cb0c-290">[Dotnet-install 腳本](../tools/dotnet-install-script.md)會用於 CI 自動化，以及非系統管理員的執行時間安裝。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-290">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="4cb0c-291">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-291">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="4cb0c-292">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-292">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="4cb0c-293">您可以藉由指定參數來選擇特定版本 `Channel` 。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-293">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="4cb0c-294">包含用 `Runtime` 來安裝執行時間的參數。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-294">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="4cb0c-295">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-295">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

<span data-ttu-id="4cb0c-296">省略參數以安裝 SDK `-Runtime` 。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-296">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="4cb0c-297">`-Channel`此範例中的參數設定為 `Current` ，它會安裝最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-297">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="4cb0c-298">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="4cb0c-298">Install with Visual Studio</span></span>

<span data-ttu-id="4cb0c-299">如果您使用 Visual Studio 開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最低必要版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-299">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="4cb0c-300">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-300">.NET Core SDK version</span></span> | <span data-ttu-id="4cb0c-301">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="4cb0c-301">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="4cb0c-302">3.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-302">3.1</span></span>                   | <span data-ttu-id="4cb0c-303">Visual Studio 2019 16.4 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-303">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="4cb0c-304">3.0</span><span class="sxs-lookup"><span data-stu-id="4cb0c-304">3.0</span></span>                   | <span data-ttu-id="4cb0c-305">Visual Studio 2019 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-305">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="4cb0c-306">2.2</span><span class="sxs-lookup"><span data-stu-id="4cb0c-306">2.2</span></span>                   | <span data-ttu-id="4cb0c-307">Visual Studio 2017 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-307">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="4cb0c-308">2.1</span><span class="sxs-lookup"><span data-stu-id="4cb0c-308">2.1</span></span>                   | <span data-ttu-id="4cb0c-309">Visual Studio 2017 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-309">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="4cb0c-310">如果您已安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-310">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="4cb0c-311">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-311">Open Visual Studio.</span></span>
01. <span data-ttu-id="4cb0c-312">選取 **[**  >  **關於 Microsoft Visual Studio**的說明]。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-312">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="4cb0c-313">閱讀 [**關於**] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-313">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="4cb0c-314">Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-314">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="4cb0c-315">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-315">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="4cb0c-316">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="4cb0c-316">Select a workload</span></span>

<span data-ttu-id="4cb0c-317">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列其中一個或多個工作負載：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-317">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="4cb0c-318">[**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-318">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="4cb0c-319">**Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-319">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="4cb0c-320">**Web & 雲端**一節中的**Azure 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-320">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="4cb0c-321">**桌上型電腦 & Mobile**一節中的 **.net 桌面開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-321">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="4cb0c-322">[![Windows Visual Studio 2019 與 .NET Core 工作負載](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="4cb0c-322">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="4cb0c-323">與 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="4cb0c-323">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="4cb0c-324">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-324">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="4cb0c-325">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-325">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="4cb0c-326">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援十分簡單。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-326">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="4cb0c-327">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-327">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="4cb0c-328">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-328">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="4cb0c-329">[從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-329">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="4cb0c-330">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="4cb0c-330">Download and manually install</span></span>

<span data-ttu-id="4cb0c-331">除了適用于 .NET Core 的 Windows 安裝程式之外，您還可以下載並手動安裝 SDK 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-331">As an alternative to the Windows installers for .NET Core, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="4cb0c-332">手動安裝通常是做為持續整合測試的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-332">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="4cb0c-333">對於開發人員或使用者，通常最好是使用[安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-333">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="4cb0c-334">.NET Core SDK 和 .NET Core 執行時間都可以在下載之後手動安裝。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-334">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="4cb0c-335">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-335">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="4cb0c-336">首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-336">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="4cb0c-337">✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="4cb0c-337">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="4cb0c-338">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="4cb0c-338">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="4cb0c-339">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="4cb0c-339">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="4cb0c-340">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="4cb0c-340">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="4cb0c-341">建立可將 .NET 解壓縮至的目錄，例如 `%USERPROFILE%\dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-341">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="4cb0c-342">然後，將下載的 zip 檔案解壓縮至該目錄。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-342">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="4cb0c-343">根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core，因此您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-343">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="4cb0c-344">若要這麼做，請變更應用程式啟動時所使用的環境變數：</span><span class="sxs-lookup"><span data-stu-id="4cb0c-344">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="4cb0c-345">這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-345">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="4cb0c-346">當 `DOTNET_MULTILEVEL_LOOKUP` 設定為時 `0` ，.net core 會忽略任何全域安裝的 .net core 版本。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-346">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET Core ignores any globally installed .NET Core version.</span></span> <span data-ttu-id="4cb0c-347">移除該環境設定，讓 .NET Core 在選取最適合執行應用程式的架構時，考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-347">Remove that environment setting to let .NET Core consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="4cb0c-348">預設值通常是 `C:\Program Files\dotnet` ，安裝程式會在此安裝 .Net Core。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-348">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET Core.</span></span>

## <a name="docker"></a><span data-ttu-id="4cb0c-349">Docker</span><span class="sxs-lookup"><span data-stu-id="4cb0c-349">Docker</span></span>

<span data-ttu-id="4cb0c-350">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-350">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="4cb0c-351">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-351">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="4cb0c-352">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-352">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="4cb0c-353">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-353">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="4cb0c-354">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-354">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="4cb0c-355">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-355">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="4cb0c-356">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-356">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="4cb0c-357">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-357">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4cb0c-358">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4cb0c-358">Next steps</span></span>

- <span data-ttu-id="4cb0c-359">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-359">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="4cb0c-360">[教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-360">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="4cb0c-361">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-361">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="4cb0c-362">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb0c-362">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>
