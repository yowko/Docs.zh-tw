---
title: 在 macOS 上安裝 .NET Core
description: 瞭解您可以在哪些版本的 macOS 上安裝 .NET Core。
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: 2900d98dbd30c51f689cdce37ea273ccc4f598b5
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308919"
---
# <a name="install-net-core-on-macos"></a><span data-ttu-id="33643-103">在 macOS 上安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="33643-103">Install .NET Core on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [安裝在 Windows 上](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [安裝在 Linux 上](linux.md)

<span data-ttu-id="33643-107">在本文中，您將瞭解如何在 macOS 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="33643-107">In this article, you'll learn how to install .NET Core on macOS.</span></span> <span data-ttu-id="33643-108">.NET Core 是由執行時間和 SDK 所組成。</span><span class="sxs-lookup"><span data-stu-id="33643-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="33643-109">執行時間是用來執行 .NET Core 應用程式，且不一定會包含在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="33643-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="33643-110">SDK 可用來建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="33643-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="33643-111">.NET Core 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="33643-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="33643-112">.NET Core 的最新版本為3.1。</span><span class="sxs-lookup"><span data-stu-id="33643-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="33643-113">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="33643-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="33643-114">支援的版本</span><span class="sxs-lookup"><span data-stu-id="33643-114">Supported releases</span></span>

<span data-ttu-id="33643-115">下表列出目前支援的 .NET Core 版本，以及支援的 macOS 版本。</span><span class="sxs-lookup"><span data-stu-id="33643-115">The following table is a list of currently supported .NET Core releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="33643-116">這些版本仍可支援[.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="33643-116">These versions remain supported either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="33643-117">✔️表示仍然支援 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="33643-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="33643-118">❌表示不支援 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="33643-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="33643-119">作業系統</span><span class="sxs-lookup"><span data-stu-id="33643-119">Operating System</span></span>          | <span data-ttu-id="33643-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="33643-120">.NET Core 2.1</span></span> | <span data-ttu-id="33643-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="33643-121">.NET Core 3.1</span></span> | <span data-ttu-id="33643-122">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="33643-122">.NET 5 Preview</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="33643-123">macOS 10.15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="33643-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="33643-124">✔️2.1 （[版本][release-notes-21]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="33643-125">✔️3.1 （[版本][release-notes-31]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="33643-126">✔️ 5.0 Preview （[版本][release-notes-50]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-126">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="33643-127">macOS 10.14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="33643-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="33643-128">✔️2.1 （[版本][release-notes-21]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="33643-129">✔️3.1 （[版本][release-notes-31]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="33643-130">✔️ 5.0 Preview （[版本][release-notes-50]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-130">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="33643-131">macOS 10.13 「高塞拉里昂」</span><span class="sxs-lookup"><span data-stu-id="33643-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="33643-132">✔️2.1 （[版本][release-notes-21]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="33643-133">✔️3.1 （[版本][release-notes-31]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="33643-134">✔️ 5.0 Preview （[版本][release-notes-50]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-134">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="33643-135">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="33643-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="33643-136">✔️2.1 （[版本][release-notes-21]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="33643-137">❌3.1 （[版本][release-notes-31]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="33643-138">❌5.0 Preview （[版本][release-notes-50]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-138">❌ 5.0 Preview ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="33643-139">不支援的版本</span><span class="sxs-lookup"><span data-stu-id="33643-139">Unsupported releases</span></span>

<span data-ttu-id="33643-140">已不再支援下列 .NET Core 版本 ❌ 。</span><span class="sxs-lookup"><span data-stu-id="33643-140">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="33643-141">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="33643-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="33643-142">3.0 （[版本][release-notes-30]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="33643-143">2.2 （[版本][release-notes-22]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="33643-144">2.0 （[版本][release-notes-20]資訊）</span><span class="sxs-lookup"><span data-stu-id="33643-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="33643-145">執行時間資訊</span><span class="sxs-lookup"><span data-stu-id="33643-145">Runtime information</span></span>

<span data-ttu-id="33643-146">執行時間是用來執行使用 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="33643-146">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="33643-147">當應用程式作者發行應用程式時，他們可以將執行時間包含在其應用程式中。</span><span class="sxs-lookup"><span data-stu-id="33643-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="33643-148">如果它們不包含執行時間，則會由使用者自行安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="33643-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="33643-149">您可以在 macOS 上安裝三種不同的執行時間：</span><span class="sxs-lookup"><span data-stu-id="33643-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="33643-150">*ASP.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="33643-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="33643-151">執行 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="33643-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="33643-152">包含 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="33643-152">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="33643-153">*.NET Core 執行時間*</span><span class="sxs-lookup"><span data-stu-id="33643-153">*.NET Core runtime*</span></span>\
<span data-ttu-id="33643-154">此執行時間是最簡單的執行時間，不包含任何其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="33643-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="33643-155">強烈建議您安裝*ASP.NET Core 運行*時間，以與 .net Core 應用程式達到最佳的相容性。</span><span class="sxs-lookup"><span data-stu-id="33643-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="33643-156">下載 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="33643-156">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="33643-157">SDK 資訊</span><span class="sxs-lookup"><span data-stu-id="33643-157">SDK information</span></span>

<span data-ttu-id="33643-158">SDK 可用來建立及發佈 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="33643-158">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="33643-159">安裝 SDK 同時包含[運行](#runtime-information)時間： ASP.NET CORE 和 .net Core。</span><span class="sxs-lookup"><span data-stu-id="33643-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="33643-160">下載 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="33643-160">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="33643-161">相依性</span><span class="sxs-lookup"><span data-stu-id="33643-161">Dependencies</span></span>

<span data-ttu-id="33643-162">下列 macOS 版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="33643-162">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="33643-163">`+`代表最小版本的符號。</span><span class="sxs-lookup"><span data-stu-id="33643-163">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="33643-164">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="33643-164">.NET Core Version</span></span> | <span data-ttu-id="33643-165">macOS</span><span class="sxs-lookup"><span data-stu-id="33643-165">macOS</span></span>                 | <span data-ttu-id="33643-166">架構</span><span class="sxs-lookup"><span data-stu-id="33643-166">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="33643-167">3.1</span><span class="sxs-lookup"><span data-stu-id="33643-167">3.1</span></span>               | <span data-ttu-id="33643-168">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="33643-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="33643-169">x64</span><span class="sxs-lookup"><span data-stu-id="33643-169">x64</span></span> | [<span data-ttu-id="33643-170">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="33643-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="33643-171">3.0</span><span class="sxs-lookup"><span data-stu-id="33643-171">3.0</span></span>               | <span data-ttu-id="33643-172">高塞拉里昂（10.13 +）</span><span class="sxs-lookup"><span data-stu-id="33643-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="33643-173">x64</span><span class="sxs-lookup"><span data-stu-id="33643-173">x64</span></span> | [<span data-ttu-id="33643-174">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="33643-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="33643-175">2.2</span><span class="sxs-lookup"><span data-stu-id="33643-175">2.2</span></span>               | <span data-ttu-id="33643-176">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="33643-176">Sierra (10.12+)</span></span>       | <span data-ttu-id="33643-177">x64</span><span class="sxs-lookup"><span data-stu-id="33643-177">x64</span></span> | [<span data-ttu-id="33643-178">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="33643-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="33643-179">2.1</span><span class="sxs-lookup"><span data-stu-id="33643-179">2.1</span></span>               | <span data-ttu-id="33643-180">塞拉里昂（10.12 +）</span><span class="sxs-lookup"><span data-stu-id="33643-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="33643-181">x64</span><span class="sxs-lookup"><span data-stu-id="33643-181">x64</span></span> | [<span data-ttu-id="33643-182">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="33643-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="33643-183">從 macOS Catalina （版本10.15）開始，在2019年6月1日之後以開發人員識別碼散發的所有軟體都必須是公證。</span><span class="sxs-lookup"><span data-stu-id="33643-183">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="33643-184">這項需求適用于 .NET core 執行時間、.NET Core SDK 和使用 .NET Core 所建立的軟體。</span><span class="sxs-lookup"><span data-stu-id="33643-184">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="33643-185">從2020年2月18日起，已公證 .NET Core （執行時間和 SDK）版本3.1、3.0 和2.1 的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="33643-185">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="33643-186">先前發行的版本不會公證。</span><span class="sxs-lookup"><span data-stu-id="33643-186">Prior released versions aren't notarized.</span></span> <span data-ttu-id="33643-187">如果您執行非公證應用程式，您會看到類似下圖的錯誤：</span><span class="sxs-lookup"><span data-stu-id="33643-187">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notarization 警示](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="33643-189">如需強制執行 notarization 如何影響 .NET Core （和您的 .NET Core 應用程式）的詳細資訊，請參閱[使用 MacOS Catalina notarization](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="33643-189">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="33643-190">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="33643-190">libgdiplus</span></span>

<span data-ttu-id="33643-191">使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="33643-191">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="33643-192">取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。</span><span class="sxs-lookup"><span data-stu-id="33643-192">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="33643-193">安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="33643-193">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="33643-194">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="33643-194">Install with an installer</span></span>

<span data-ttu-id="33643-195">macOS 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="33643-195">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="33643-196">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="33643-196">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="33643-197">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="33643-197">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="33643-198">除了適用于 .NET Core 的 macOS 安裝程式之外，您還可以下載並手動安裝 SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="33643-198">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="33643-199">手動安裝通常是做為持續整合測試的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="33643-199">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="33643-200">對於開發人員或使用者，通常最好是使用[安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="33643-200">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="33643-201">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="33643-201">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="33643-202">首先，從下列其中一個網站下載 SDK 或執行時間的**二進位**版本：</span><span class="sxs-lookup"><span data-stu-id="33643-202">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="33643-203">✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="33643-203">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="33643-204">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="33643-204">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="33643-205">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="33643-205">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="33643-206">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="33643-206">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="33643-207">接下來，將下載的檔案解壓縮，並使用 `export` 命令來設定 .Net core 所使用的變數，然後確保 .Net core 在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="33643-207">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="33643-208">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先下載 .NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="33643-208">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="33643-209">然後，開啟終端機，並從儲存檔案的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="33643-209">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="33643-210">封存檔案名稱可能會根據您下載的內容而有所不同。</span><span class="sxs-lookup"><span data-stu-id="33643-210">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="33643-211">**使用下列命令來解壓縮運行**時間：</span><span class="sxs-lookup"><span data-stu-id="33643-211">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="33643-212">**使用下列命令來解壓縮 SDK**：</span><span class="sxs-lookup"><span data-stu-id="33643-212">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="33643-213">上述 `export` 命令只會對其執行所在的終端機會話提供 .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="33643-213">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="33643-214">您可以編輯您的 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="33643-214">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="33643-215">有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="33643-215">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="33643-216">例如：</span><span class="sxs-lookup"><span data-stu-id="33643-216">For example:</span></span>
>
> - <span data-ttu-id="33643-217">**Bash Shell**： *~/. bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="33643-217">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="33643-218">**Korn Shell**： *~/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="33643-218">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="33643-219">**Z Shell**： *~/.zshrc*或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="33643-219">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="33643-220">為您的 shell 編輯適當的原始程式檔，並將新增 `:$HOME/dotnet` 至現有 `PATH` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="33643-220">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="33643-221">如果未 `PATH` 包含任何語句，請加入具有的新行 `export PATH=$PATH:$HOME/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="33643-221">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="33643-222">此外，將新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="33643-222">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="33643-223">這種方法可讓您將不同的版本安裝到不同的位置，並明確選擇哪一個應用程式要使用哪一個。</span><span class="sxs-lookup"><span data-stu-id="33643-223">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="33643-224">使用 Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="33643-224">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="33643-225">Visual Studio for Mac 在選取 [ **.Net Core** ] 工作負載時安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="33643-225">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="33643-226">若要開始在 macOS 上使用 .NET Core 開發，請參閱[安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="33643-226">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="33643-227">針對最新版本 .NET Core 3.1，您必須使用 Visual Studio for Mac 8.4 Preview。</span><span class="sxs-lookup"><span data-stu-id="33643-227">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="33643-228">[![使用 .NET Core 工作負載功能的 macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="33643-228">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="33643-229">與 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="33643-229">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="33643-230">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="33643-230">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="33643-231">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="33643-231">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="33643-232">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援十分簡單。</span><span class="sxs-lookup"><span data-stu-id="33643-232">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="33643-233">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="33643-233">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="33643-234">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="33643-234">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="33643-235">[從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。</span><span class="sxs-lookup"><span data-stu-id="33643-235">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="33643-236">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="33643-236">Install with bash automation</span></span>

<span data-ttu-id="33643-237">[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="33643-237">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="33643-238">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="33643-238">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="33643-239">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="33643-239">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="33643-240">您可以藉由指定參數來選擇特定版本 `current` 。</span><span class="sxs-lookup"><span data-stu-id="33643-240">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="33643-241">包含用 `runtime` 來安裝執行時間的參數。</span><span class="sxs-lookup"><span data-stu-id="33643-241">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="33643-242">否則，腳本會安裝[SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="33643-242">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="33643-243">上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。</span><span class="sxs-lookup"><span data-stu-id="33643-243">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="33643-244">ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="33643-244">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="33643-245">Docker</span><span class="sxs-lookup"><span data-stu-id="33643-245">Docker</span></span>

<span data-ttu-id="33643-246">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="33643-246">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="33643-247">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="33643-247">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="33643-248">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="33643-248">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="33643-249">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="33643-249">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="33643-250">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="33643-250">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="33643-251">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="33643-251">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="33643-252">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="33643-252">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="33643-253">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="33643-253">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="33643-254">後續步驟</span><span class="sxs-lookup"><span data-stu-id="33643-254">Next steps</span></span>

- <span data-ttu-id="33643-255">[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="33643-255">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="33643-256">使用[MacOS Catalina notarization](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="33643-256">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="33643-257">[教學課程：開始使用 macOS](../tutorials/using-on-mac-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="33643-257">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="33643-258">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="33643-258">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="33643-259">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="33643-259">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
