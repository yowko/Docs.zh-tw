---
title: 在 macOS 上安裝 .NET
description: 瞭解您可以在哪些版本的 macOS 上安裝 .NET。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b1434938a8e8e81da81e495a6b99e6c99467aae1
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009354"
---
# <a name="install-net-on-macos"></a><span data-ttu-id="0e011-103">在 macOS 上安裝 .NET</span><span class="sxs-lookup"><span data-stu-id="0e011-103">Install .NET on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [安裝在 Linux 上](linux.md)

<span data-ttu-id="0e011-107">在本文中，您將瞭解如何在 macOS 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="0e011-107">In this article, you'll learn how to install .NET on macOS.</span></span> <span data-ttu-id="0e011-108">.NET 是由執行時間和 SDK 所組成。</span><span class="sxs-lookup"><span data-stu-id="0e011-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="0e011-109">執行時間是用來執行 .NET 應用程式，且不一定會包含在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="0e011-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="0e011-110">SDK 是用來建立 .NET 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="0e011-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="0e011-111">.NET 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="0e011-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="0e011-112">.NET 的最新版本為5.0。</span><span class="sxs-lookup"><span data-stu-id="0e011-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="0e011-113">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="0e011-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="0e011-114">支援的版本</span><span class="sxs-lookup"><span data-stu-id="0e011-114">Supported releases</span></span>

<span data-ttu-id="0e011-115">下表列出目前支援的 .NET 版本，以及其支援的 macOS 版本。</span><span class="sxs-lookup"><span data-stu-id="0e011-115">The following table is a list of currently supported .NET releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="0e011-116">這些版本仍可支援 .Net 的版本，以 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="0e011-116">These versions remain supported either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="0e011-117">✔️表示仍支援 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="0e011-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="0e011-118">❌表示不支援 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="0e011-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="0e011-119">作業系統</span><span class="sxs-lookup"><span data-stu-id="0e011-119">Operating System</span></span>          | <span data-ttu-id="0e011-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0e011-120">.NET Core 2.1</span></span> | <span data-ttu-id="0e011-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0e011-121">.NET Core 3.1</span></span> | <span data-ttu-id="0e011-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0e011-122">.NET 5.0</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="0e011-123">macOS 11.0 "Big Sur"</span><span class="sxs-lookup"><span data-stu-id="0e011-123">macOS 11.0 "Big Sur"</span></span>        | <span data-ttu-id="0e011-124">✔️ 2.1 ([版本][release-notes-21] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="0e011-125">✔️ 3.1 ([版本][release-notes-31] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="0e011-126">✔️ 5.0 ([版本][release-notes-50] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-126">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="0e011-127">macOS 10.15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="0e011-127">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="0e011-128">✔️ 2.1 ([版本][release-notes-21] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="0e011-129">✔️ 3.1 ([版本][release-notes-31] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="0e011-130">✔️ 5.0 ([版本][release-notes-50] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-130">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="0e011-131">macOS 10.14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="0e011-131">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="0e011-132">✔️ 2.1 ([版本][release-notes-21] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="0e011-133">✔️ 3.1 ([版本][release-notes-31] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="0e011-134">✔️ 5.0 ([版本][release-notes-50] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-134">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="0e011-135">macOS 10.13 "High Sierra"</span><span class="sxs-lookup"><span data-stu-id="0e011-135">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="0e011-136">✔️ 2.1 ([版本][release-notes-21] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="0e011-137">✔️ 3.1 ([版本][release-notes-31] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-137">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="0e011-138">✔️ 5.0 ([版本][release-notes-50] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-138">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="0e011-139">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="0e011-139">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="0e011-140">✔️ 2.1 ([版本][release-notes-21] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-140">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="0e011-141">❌ 3.1 ([版本][release-notes-31] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-141">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="0e011-142">❌ 5.0 ([版本][release-notes-50] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-142">❌ 5.0 ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="0e011-143">不支援的版本</span><span class="sxs-lookup"><span data-stu-id="0e011-143">Unsupported releases</span></span>

<span data-ttu-id="0e011-144">不再支援下列 .NET 版本 ❌ 。</span><span class="sxs-lookup"><span data-stu-id="0e011-144">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="0e011-145">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="0e011-145">The downloads for these still remain published:</span></span>

- <span data-ttu-id="0e011-146">3.0 ([版本][release-notes-30] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-146">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="0e011-147">2.2 ([版本][release-notes-22] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-147">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="0e011-148">2.0 ([版本][release-notes-20] 資訊) </span><span class="sxs-lookup"><span data-stu-id="0e011-148">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="0e011-149">執行時間資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-149">Runtime information</span></span>

<span data-ttu-id="0e011-150">執行時間是用來執行以 .NET 建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e011-150">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="0e011-151">當應用程式作者發佈應用程式時，他們可以在其應用程式中包含執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-151">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="0e011-152">如果未包含執行時間，則會由使用者自行安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-152">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="0e011-153">您可以在 macOS 上安裝三個不同的執行時間：</span><span class="sxs-lookup"><span data-stu-id="0e011-153">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="0e011-154">*ASP.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="0e011-154">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="0e011-155">執行 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e011-155">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="0e011-156">包含 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-156">Includes the .NET runtime.</span></span>

<span data-ttu-id="0e011-157">*.NET 執行時間*</span><span class="sxs-lookup"><span data-stu-id="0e011-157">*.NET runtime*</span></span>\
<span data-ttu-id="0e011-158">此執行時間是最簡單的執行時間，不包含任何其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-158">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="0e011-159">強烈建議您安裝 *ASP.NET Core 運行* 時間，以獲得與 .net 應用程式的最佳相容性。</span><span class="sxs-lookup"><span data-stu-id="0e011-159">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="0e011-160">下載 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="0e011-160">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="0e011-161">SDK 資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-161">SDK information</span></span>

<span data-ttu-id="0e011-162">SDK 可用來建立及發佈 .NET 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="0e011-162">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="0e011-163">安裝 SDK 同時包含 [運行](#runtime-information)時間： ASP.NET CORE 和 .net。</span><span class="sxs-lookup"><span data-stu-id="0e011-163">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="0e011-164">相依性</span><span class="sxs-lookup"><span data-stu-id="0e011-164">Dependencies</span></span>

<span data-ttu-id="0e011-165">下列 macOS 版本支援 .NET：</span><span class="sxs-lookup"><span data-stu-id="0e011-165">.NET is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="0e011-166">`+`符號表示最小版本。</span><span class="sxs-lookup"><span data-stu-id="0e011-166">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e011-167">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="0e011-167">.NET Core Version</span></span> | <span data-ttu-id="0e011-168">macOS</span><span class="sxs-lookup"><span data-stu-id="0e011-168">macOS</span></span>                 | <span data-ttu-id="0e011-169">架構</span><span class="sxs-lookup"><span data-stu-id="0e011-169">Architectures</span></span> | <span data-ttu-id="0e011-170">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-170">More information</span></span>    |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="0e011-171">5.0</span><span class="sxs-lookup"><span data-stu-id="0e011-171">5.0</span></span>               | <span data-ttu-id="0e011-172">高塞拉里昂 (10.13 +) </span><span class="sxs-lookup"><span data-stu-id="0e011-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="0e011-173">x64</span><span class="sxs-lookup"><span data-stu-id="0e011-173">x64</span></span> | [<span data-ttu-id="0e011-174">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| <span data-ttu-id="0e011-175">3.1</span><span class="sxs-lookup"><span data-stu-id="0e011-175">3.1</span></span>               | <span data-ttu-id="0e011-176">高塞拉里昂 (10.13 +) </span><span class="sxs-lookup"><span data-stu-id="0e011-176">High Sierra (10.13+)</span></span>  | <span data-ttu-id="0e011-177">x64</span><span class="sxs-lookup"><span data-stu-id="0e011-177">x64</span></span> | [<span data-ttu-id="0e011-178">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="0e011-179">3.0</span><span class="sxs-lookup"><span data-stu-id="0e011-179">3.0</span></span>               | <span data-ttu-id="0e011-180">高塞拉里昂 (10.13 +) </span><span class="sxs-lookup"><span data-stu-id="0e011-180">High Sierra (10.13+)</span></span>  | <span data-ttu-id="0e011-181">x64</span><span class="sxs-lookup"><span data-stu-id="0e011-181">x64</span></span> | [<span data-ttu-id="0e011-182">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="0e011-183">2.2</span><span class="sxs-lookup"><span data-stu-id="0e011-183">2.2</span></span>               | <span data-ttu-id="0e011-184">10.12 +) 的塞拉里昂 (</span><span class="sxs-lookup"><span data-stu-id="0e011-184">Sierra (10.12+)</span></span>       | <span data-ttu-id="0e011-185">x64</span><span class="sxs-lookup"><span data-stu-id="0e011-185">x64</span></span> | [<span data-ttu-id="0e011-186">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-186">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="0e011-187">2.1</span><span class="sxs-lookup"><span data-stu-id="0e011-187">2.1</span></span>               | <span data-ttu-id="0e011-188">10.12 +) 的塞拉里昂 (</span><span class="sxs-lookup"><span data-stu-id="0e011-188">Sierra (10.12+)</span></span>       | <span data-ttu-id="0e011-189">x64</span><span class="sxs-lookup"><span data-stu-id="0e011-189">x64</span></span> | [<span data-ttu-id="0e011-190">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e011-190">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="0e011-191">從 macOS Catalina () 10.15 版開始，在2019年6月1日之後，以開發人員識別碼散發的所有軟體都必須公證。</span><span class="sxs-lookup"><span data-stu-id="0e011-191">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="0e011-192">這項需求適用于 .NET 執行時間、.NET SDK 和使用 .NET 建立的軟體。</span><span class="sxs-lookup"><span data-stu-id="0e011-192">This requirement applies to the .NET runtime, .NET SDK, and software created with .NET.</span></span>

<span data-ttu-id="0e011-193">.NET 5.0 和 .NET Core 3.1、3.0 和2.1 的執行時間和 SDK 安裝程式，自2020年2月18日起已公證。</span><span class="sxs-lookup"><span data-stu-id="0e011-193">The runtime and SDK installers for .NET 5.0 and .NET Core 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="0e011-194">先前發行的版本不會公證。</span><span class="sxs-lookup"><span data-stu-id="0e011-194">Prior released versions aren't notarized.</span></span> <span data-ttu-id="0e011-195">如果您執行非公證應用程式，您會看到類似下圖的錯誤：</span><span class="sxs-lookup"><span data-stu-id="0e011-195">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina 公證警示](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="0e011-197">如需強制執行公證如何影響 .NET (和您的 .NET 應用程式) 的詳細資訊，請參閱 [使用 MacOS Catalina 公證](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="0e011-197">For more information about how enforced-notarization affects .NET (and your .NET apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="0e011-198">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="0e011-198">libgdiplus</span></span>

<span data-ttu-id="0e011-199">使用 *system.object* 的 .net 應用程式需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="0e011-199">.NET applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="0e011-200">取得 libgdiplus 的簡單方法是使用 macOS 的 [Homebrew ( "brew" ) ](https://brew.sh/) 套件管理員。</span><span class="sxs-lookup"><span data-stu-id="0e011-200">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="0e011-201">安裝 *brew* 之後，請在終端機 (命令) 提示字元中執行下列命令，以安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="0e011-201">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="0e011-202">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="0e011-202">Install with an installer</span></span>

<span data-ttu-id="0e011-203">macOS 具有可用於安裝 .NET 5.0 SDK 的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="0e011-203">macOS has standalone installers that can be used to install the .NET 5.0 SDK:</span></span>

- [<span data-ttu-id="0e011-204">x64 (64 位) Cpu</span><span class="sxs-lookup"><span data-stu-id="0e011-204">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a><span data-ttu-id="0e011-205">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="0e011-205">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="0e011-206">除了 .NET 的 macOS 安裝程式之外，您還可以下載並手動安裝 SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-206">As an alternative to the macOS installers for .NET, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="0e011-207">手動安裝通常會做為持續整合測試的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="0e011-207">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="0e011-208">針對開發人員或使用者，通常最好是使用 [安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="0e011-208">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="0e011-209">如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-209">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="0e011-210">首先，從下列其中一個網站下載 SDK 或執行時間的 **二進位** 版本：</span><span class="sxs-lookup"><span data-stu-id="0e011-210">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="0e011-211">✔️ [.net 5.0 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="0e011-211">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="0e011-212">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="0e011-212">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="0e011-213">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="0e011-213">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="0e011-214">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="0e011-214">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="0e011-215">接下來，將下載的檔案解壓縮，並使用 `export` 命令設定 .net 所使用的變數，然後確定 .net 是在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="0e011-215">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="0e011-216">若要將執行時間解壓縮，並讓 .NET CLI 命令可在終端機上使用，請先下載 .NET 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="0e011-216">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="0e011-217">然後，開啟終端機，並從儲存檔案的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0e011-217">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="0e011-218">保存檔案名稱可能會因您所下載的內容而有所不同。</span><span class="sxs-lookup"><span data-stu-id="0e011-218">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="0e011-219">**使用下列命令，將執行時間解壓縮**：</span><span class="sxs-lookup"><span data-stu-id="0e011-219">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="0e011-220">**使用下列命令將 SDK 解壓縮**：</span><span class="sxs-lookup"><span data-stu-id="0e011-220">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="0e011-221">上述 `export` 命令只會讓執行的終端機會話提供 .NET CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="0e011-221">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="0e011-222">您可以編輯 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="0e011-222">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="0e011-223">Linux 有一些不同的 shell 可用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="0e011-223">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="0e011-224">例如：</span><span class="sxs-lookup"><span data-stu-id="0e011-224">For example:</span></span>
>
> - <span data-ttu-id="0e011-225">**Bash Shell**： *~/.bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="0e011-225">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="0e011-226">**Korn Shell**： *~/.kshrc* 或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="0e011-226">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="0e011-227">**Z Shell**： *~/.zshrc* 或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="0e011-227">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="0e011-228">編輯您 shell 的適當原始程式檔，並新增 `:$HOME/dotnet` 至現有語句的結尾 `PATH` 。</span><span class="sxs-lookup"><span data-stu-id="0e011-228">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="0e011-229">如果未 `PATH` 包含任何語句，請使用加入新的一行 `export PATH=$PATH:$HOME/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="0e011-229">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="0e011-230">此外，新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="0e011-230">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="0e011-231">這種方法可讓您將不同的版本安裝到不同的位置，並明確地選擇哪個應用程式要使用哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="0e011-231">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="0e011-232">使用 Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="0e011-232">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="0e011-233">Visual Studio for Mac 在選取 **.net** 工作負載時安裝 .net SDK。</span><span class="sxs-lookup"><span data-stu-id="0e011-233">Visual Studio for Mac installs the .NET SDK when the **.NET** workload is selected.</span></span> <span data-ttu-id="0e011-234">若要開始在 macOS 上進行 .NET 程式開發，請參閱 [安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="0e011-234">To get started with .NET development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

| <span data-ttu-id="0e011-235">.NET SDK 版本</span><span class="sxs-lookup"><span data-stu-id="0e011-235">.NET SDK version</span></span>      | <span data-ttu-id="0e011-236">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="0e011-236">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="0e011-237">5.0</span><span class="sxs-lookup"><span data-stu-id="0e011-237">5.0</span></span>                   | <span data-ttu-id="0e011-238">適用于 Mac 8.8 版或更高版本的 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="0e011-238">Visual Studio 2019 for Mac version 8.8 or higher.</span></span> |
| <span data-ttu-id="0e011-239">3.1</span><span class="sxs-lookup"><span data-stu-id="0e011-239">3.1</span></span>                   | <span data-ttu-id="0e011-240">適用于 Mac 8.4 版或更高版本的 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="0e011-240">Visual Studio 2019 for Mac version 8.4 or higher.</span></span> |
| <span data-ttu-id="0e011-241">2.1</span><span class="sxs-lookup"><span data-stu-id="0e011-241">2.1</span></span>                   | <span data-ttu-id="0e011-242">適用于 Mac 8.0 版或更高版本的 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="0e011-242">Visual Studio 2019 for Mac version 8.0 or higher.</span></span> |

<span data-ttu-id="0e011-243">[![macOS Visual Studio 2019 for Mac with .NET 工作負載功能](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="0e011-243">[![macOS Visual Studio 2019 for Mac with .NET workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="0e011-244">隨 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="0e011-244">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="0e011-245">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="0e011-245">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="0e011-246">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="0e011-246">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="0e011-247">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET 安裝程式，但新增 .NET 支援很簡單。</span><span class="sxs-lookup"><span data-stu-id="0e011-247">While Visual Studio Code doesn't come with an automated .NET installer like Visual Studio does, adding .NET support is simple.</span></span>

01. <span data-ttu-id="0e011-248">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="0e011-248">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="0e011-249">[下載並安裝 .NET SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="0e011-249">[Download and install the .NET SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="0e011-250">[從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。</span><span class="sxs-lookup"><span data-stu-id="0e011-250">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="0e011-251">使用 bash automation 安裝</span><span class="sxs-lookup"><span data-stu-id="0e011-251">Install with bash automation</span></span>

<span data-ttu-id="0e011-252">[Dotnet 安裝腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="0e011-252">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="0e011-253">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="0e011-253">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="0e011-254">腳本預設會安裝最新 [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="0e011-254">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="0e011-255">您可以藉由指定參數來選擇特定版本 `current` 。</span><span class="sxs-lookup"><span data-stu-id="0e011-255">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="0e011-256">包含 `runtime` 參數以安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-256">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="0e011-257">否則，腳本會安裝 [SDK](./windows.md)。</span><span class="sxs-lookup"><span data-stu-id="0e011-257">Otherwise, the script installs the [SDK](./windows.md).</span></span>

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="0e011-258">上一個命令會安裝 ASP.NET Core 執行時間，以取得最大相容性。</span><span class="sxs-lookup"><span data-stu-id="0e011-258">The previous command installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="0e011-259">ASP.NET Core 執行時間也包含標準的 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e011-259">The ASP.NET Core runtime also includes the standard .NET runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="0e011-260">Docker</span><span class="sxs-lookup"><span data-stu-id="0e011-260">Docker</span></span>

<span data-ttu-id="0e011-261">容器可提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="0e011-261">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="0e011-262">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="0e011-262">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="0e011-263">.NET 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="0e011-263">.NET can run in a Docker container.</span></span> <span data-ttu-id="0e011-264">官方 .NET Docker 映射會發佈至 Microsoft Container Registry (MCR) 並可在 [microsoft .Net Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet/)中找到。</span><span class="sxs-lookup"><span data-stu-id="0e011-264">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet/).</span></span> <span data-ttu-id="0e011-265">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="0e011-265">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="0e011-266">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="0e011-266">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="0e011-267">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-aspnet) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="0e011-267">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="0e011-268">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱 [.net 和 Docker 簡介](../docker/introduction.md) 和 [範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="0e011-268">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0e011-269">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0e011-269">Next steps</span></span>

- <span data-ttu-id="0e011-270">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="0e011-270">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="0e011-271">使用[MacOS Catalina 公證](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="0e011-271">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="0e011-272">[教學課程：開始使用 macOS](../tutorials/with-visual-studio-mac.md)。</span><span class="sxs-lookup"><span data-stu-id="0e011-272">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="0e011-273">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="0e011-273">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="0e011-274">[教學課程：將 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="0e011-274">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
