---
title: ".NET 架構元件"
description: "描述 .NET 架構元件，例如 .NET Standard、.NET 實作、.NET 執行階段和工具。"
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a17d4c36d9c1942166b9ad889103a7942f1813d
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="net-architectural-components"></a><span data-ttu-id="9c0ac-103">.NET 架構元件</span><span class="sxs-lookup"><span data-stu-id="9c0ac-103">.NET architectural components</span></span>

<span data-ttu-id="9c0ac-104">.NET 應用程式是針對一或多個「.NET 實作」所開發並在其中執行。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-104">A .NET app is developed for and runs in one or more *implementations of .NET*.</span></span>  <span data-ttu-id="9c0ac-105">.NET 實作包括 .NET Framework、.NET Core 和 Mono。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-105">Implementations of .NET include the .NET Framework, .NET Core, and Mono.</span></span> <span data-ttu-id="9c0ac-106">所有 .NET 實作有一個通用的 API 規格，稱為 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-106">There is an API specification common to all implementations of .NET that's called the .NET Standard.</span></span> <span data-ttu-id="9c0ac-107">本文提供上述每個概念的簡介。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-107">This article gives a brief introduction to each of these concepts.</span></span>

## <a name="net-standard"></a><span data-ttu-id="9c0ac-108">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="9c0ac-108">.NET Standard</span></span>

<span data-ttu-id="9c0ac-109">.NET Standard 是由 .NET 實作的基底類別庫所實作的一組 API。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-109">The .NET Standard is a set of APIs that are implemented by the Base Class Library of a .NET implementation.</span></span> <span data-ttu-id="9c0ac-110">更正式的說法是，它是一個 .NET API 的規格，其構成了一組您據以編譯程式碼的制式協定。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-110">More formally, it's a specification of .NET APIs that make up a uniform set of contracts that you compile your code against.</span></span> <span data-ttu-id="9c0ac-111">每個 .NET 實作中都會實作這些協定。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-111">These contracts are implemented in each .NET implementation.</span></span> <span data-ttu-id="9c0ac-112">這會跨不同的 .NET 實作啟用可攜性，以有效地讓您的程式碼在任何地方執行。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-112">This enables portability across different .NET implementations, effectively allowing your code to run everywhere.</span></span>

<span data-ttu-id="9c0ac-113">.NET Standard 也是[目標 Framework](glossary.md#target-framework)。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-113">The .NET Standard is also a [target framework](glossary.md#target-framework).</span></span> <span data-ttu-id="9c0ac-114">如果您的程式碼以某個 .NET Standard 版本為目標，就可以在支援該版 .NET Standard 的任何 .NET 實作上執行。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-114">If your code targets a version of the .NET Standard, it can run on any .NET implementation which supports that version of the .NET Standard.</span></span>

<span data-ttu-id="9c0ac-115">若要了解 .NET Standard 及如何將其設為目標，請參閱 [.NET Standard](net-standard.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-115">To learn more about the .NET Standard and how to target it, see the [.NET Standard](net-standard.md) topic.</span></span>

## <a name="net-implementations"></a><span data-ttu-id="9c0ac-116">.NET 實作</span><span class="sxs-lookup"><span data-stu-id="9c0ac-116">.NET implementations</span></span>

<span data-ttu-id="9c0ac-117">.NET 的每項實作包括下列元件：</span><span class="sxs-lookup"><span data-stu-id="9c0ac-117">Each implementation of .NET includes the following components:</span></span>

- <span data-ttu-id="9c0ac-118">一或多個執行階段。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-118">One or more runtimes.</span></span> <span data-ttu-id="9c0ac-119">範例：適用於 .NET Framework 的 CLR、適用於 .NET Core 的 CoreCLR 和 CoreRT。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-119">Examples: CLR for .NET Framework, CoreCLR and CoreRT for .NET Core.</span></span>
- <span data-ttu-id="9c0ac-120">實作 .NET Standard 並可能實作其他 API 的類別庫。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-120">A class library that implements the .NET Standard and may implement additional APIs.</span></span> <span data-ttu-id="9c0ac-121">範例：.NET Framework 基底類別庫、.NET Core 基底類別庫。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-121">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="9c0ac-122">(選擇性) 一或多個應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-122">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="9c0ac-123">範例：[ASP.NET](https://www.asp.net/)、[Windows Forms](../framework/winforms/windows-forms-overview.md) 和 [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) 會包含在 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-123">Examples: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md), and [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) are included in the .NET Framework.</span></span>
- <span data-ttu-id="9c0ac-124">(選擇性) 開發工具。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-124">Optionally, development tools.</span></span> <span data-ttu-id="9c0ac-125">某些開發工具可在多個實作之間共用。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-125">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="9c0ac-126">Microsoft 會主動開發和維護的主要 .NET 實作有四個︰.NET Core、.NET Framework、Mono 和 UWP。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-126">There are four primary .NET implementations that Microsoft actively develops and maintains: .NET Core, .NET Framework, Mono, and UWP.</span></span>

### <a name="net-core"></a><span data-ttu-id="9c0ac-127">.NET 核心</span><span class="sxs-lookup"><span data-stu-id="9c0ac-127">.NET Core</span></span>

<span data-ttu-id="9c0ac-128">.NET Core 是 .NET 的跨平台實作，目的是處理大規模的伺服器與雲端工作負載。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-128">.NET Core is a cross-platform implementation of .NET and designed to handle server and cloud workloads at scale.</span></span> <span data-ttu-id="9c0ac-129">可在 Windows、macOS 及 Linux 執行。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-129">It runs on Windows, macOS and Linux.</span></span> <span data-ttu-id="9c0ac-130">它會實作 .NET Standard，讓以 .NET Standard 為目標的程式碼可以在 .NET Core 上執行。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-130">It implements the .NET Standard, so code that targets the .NET Standard can run on .NET Core.</span></span> <span data-ttu-id="9c0ac-131">ASP.NET Core 會在 .NET Core 上執行。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-131">ASP.NET Core runs on .NET Core.</span></span> 

<span data-ttu-id="9c0ac-132">若要深入了解 .NET Core，請參閱 [.NET Core 指南](../core/index.md)及[為伺服器應用程式選擇 .NET Core 或 .NET Framework](choosing-core-framework-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-132">To learn more about .NET Core, see the [.NET Core Guide](../core/index.md) and [Choosing between .NET Core and .NET Framework for server apps](choosing-core-framework-server.md).</span></span>

### <a name="net-framework"></a><span data-ttu-id="9c0ac-133">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c0ac-133">.NET Framework</span></span>

<span data-ttu-id="9c0ac-134">.NET Framework 是自 2002年以來已存在的原始 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-134">The.NET Framework is the original .NET implementation that has existed since 2002.</span></span> <span data-ttu-id="9c0ac-135">它就是現有 .NET 開發人員一律會使用的同一個 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-135">It's the same .NET Framework that existing .NET developers have always used.</span></span> <span data-ttu-id="9c0ac-136">4.5 和更新版本會實作 .NET Standard，讓以 .NET Standard 為目標的程式碼可以在這些 .NET Framework 版本上執行。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-136">Versions 4.5 and later implement the .NET Standard, so code that targets the .NET Standard can run on those versions of the .NET Framework.</span></span> <span data-ttu-id="9c0ac-137">它包含其他 Windows 特定的 API，例如，使用 Windows Form 和 WPF 進行適用於 Windows 桌面開發的 API。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-137">It contains additional Windows-specific APIs, such as APIs for Windows desktop development with Windows Forms and WPF.</span></span> <span data-ttu-id="9c0ac-138">.NET Framework 最適合用來建置 Windows 傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-138">The .NET Framework is optimized for building Windows desktop applications.</span></span>

<span data-ttu-id="9c0ac-139">若要深入了解 .NET Framework，請參閱 [.NET Framework 指南](../framework/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-139">To learn more about the .NET Framework, see the [.NET Framework Guide](../framework/index.md).</span></span>

### <a name="mono"></a><span data-ttu-id="9c0ac-140">Mono</span><span class="sxs-lookup"><span data-stu-id="9c0ac-140">Mono</span></span>

<span data-ttu-id="9c0ac-141">Mono 是需要小型執行階段時主要使用的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-141">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="9c0ac-142">它是支援 Android、Mac、iOS、tvOS 和 watchOS 版 Xamarin 應用程式的執行階段，主要著重於較小的使用量。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-142">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on a small footprint.</span></span> <span data-ttu-id="9c0ac-143">Mono 也支援使用 Unity 引擎所建置的遊戲。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-143">Mono also powers games built using the Unity engine.</span></span>

<span data-ttu-id="9c0ac-144">它支援目前發行的所有 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-144">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="9c0ac-145">在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-145">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="9c0ac-146">它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-146">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="9c0ac-147">Mono 通常可搭配 Just-In-Time 編譯器使用，但也提供適用於 iOS 等平台的完整靜態編譯器 (預先編譯)。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-147">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="9c0ac-148">若要深入了解 Mono，請參閱 [Mono 文件](http://www.mono-project.com/docs/)。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-148">To learn more about Mono, see the [Mono documentation](http://www.mono-project.com/docs/).</span></span>

### <a name="universal-windows-platform-uwp"></a><span data-ttu-id="9c0ac-149">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="9c0ac-149">Universal Windows Platform (UWP)</span></span>

<span data-ttu-id="9c0ac-150">UWP 是用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-150">UWP is an implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="9c0ac-151">其設計目的是為了整合您可能想要設為目標的不同裝置類型，包括電腦、平板電腦、平板手機、手機，甚至是 Xbox。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-151">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="9c0ac-152">UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-152">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="9c0ac-153">您可以使用 C++、C#、VB.NET 和 JavaScript 來撰寫應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-153">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="9c0ac-154">使用 C# 和 VB.NET 時，.NET API 是由 .NET Core 所提供。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-154">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

<span data-ttu-id="9c0ac-155">若要深入了解 UWP，請參閱[通用 Windows 平台簡介](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-155">To learn more about UWP, see [Intro to the Universal Windows Platform](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

## <a name="net-runtimes"></a><span data-ttu-id="9c0ac-156">.NET 執行階段</span><span class="sxs-lookup"><span data-stu-id="9c0ac-156">.NET runtimes</span></span>

<span data-ttu-id="9c0ac-157">執行階段是受管理程式的執行環境。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-157">A runtime is the execution environment for a managed program.</span></span> <span data-ttu-id="9c0ac-158">OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-158">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="9c0ac-159">以下是 .NET 執行階段的一些範例：</span><span class="sxs-lookup"><span data-stu-id="9c0ac-159">Here are some examples of .NET runtimes:</span></span>
 
 - <span data-ttu-id="9c0ac-160">適用於 .NET Framework 的 Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="9c0ac-160">Common Language Runtime (CLR) for the .NET Framework</span></span>
 - <span data-ttu-id="9c0ac-161">適用於 .NET Core 的 Core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="9c0ac-161">Core Common Language Runtime (CoreCLR) for .NET Core</span></span>
 - <span data-ttu-id="9c0ac-162">適用於通用 Windows 平台的 .NET Native</span><span class="sxs-lookup"><span data-stu-id="9c0ac-162">.NET Native for Universal Windows Platform</span></span> 
 - <span data-ttu-id="9c0ac-163">適用於 Xamarin.iOS、Xamarin.Android、Xamarin.Mac 和 Mono 桌面架構的 Mono 執行階段</span><span class="sxs-lookup"><span data-stu-id="9c0ac-163">The Mono runtime for Xamarin.iOS, Xamarin.Android, Xamarin.Mac, and the Mono desktop framework</span></span>

## <a name="net-tooling-and-common-infrastructure"></a><span data-ttu-id="9c0ac-164">.NET 工具和通用基礎結構</span><span class="sxs-lookup"><span data-stu-id="9c0ac-164">.NET tooling and common infrastructure</span></span>

<span data-ttu-id="9c0ac-165">您可以存取一組詳盡的工具和基礎結構元件，以搭配各種 .NET 實作使用。</span><span class="sxs-lookup"><span data-stu-id="9c0ac-165">You have access to an extensive set of tools and infrastructure components that work with every implementation of .NET.</span></span> <span data-ttu-id="9c0ac-166">這些包括 (但不限於) 下列項目：</span><span class="sxs-lookup"><span data-stu-id="9c0ac-166">These include, but are not limited to the following:</span></span>

- <span data-ttu-id="9c0ac-167">.NET 語言及其編譯器</span><span class="sxs-lookup"><span data-stu-id="9c0ac-167">The .NET languages and their compilers</span></span>
- <span data-ttu-id="9c0ac-168">.NET 專案系統 (以 *.csproj*、*.vbproj* 和 *.fsproj* 檔案為基礎)</span><span class="sxs-lookup"><span data-stu-id="9c0ac-168">The .NET project system (based on *.csproj*, *.vbproj*, and *.fsproj* files)</span></span>
- <span data-ttu-id="9c0ac-169">[MSBuild](/visualstudio/msbuild/msbuild)，用來建置專案的建置引擎</span><span class="sxs-lookup"><span data-stu-id="9c0ac-169">[MSBuild](/visualstudio/msbuild/msbuild), the build engine used to build projects</span></span>
- <span data-ttu-id="9c0ac-170">[NuGet](/nuget/)，適用於 .NET 的 Microsoft 套件管理員</span><span class="sxs-lookup"><span data-stu-id="9c0ac-170">[NuGet](/nuget/), Microsoft's package manager for .NET</span></span>
- <span data-ttu-id="9c0ac-171">開放原始碼建置協調流程工具，例如 [CAKE](http://cakebuild.net/) 和 [FAKE](https://fake.build/)</span><span class="sxs-lookup"><span data-stu-id="9c0ac-171">Open-source build orchestration tools, such as [CAKE](http://cakebuild.net/) and [FAKE](https://fake.build/)</span></span>

## <a name="see-also"></a><span data-ttu-id="9c0ac-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c0ac-172">See also</span></span>
<span data-ttu-id="9c0ac-173">[為伺服器應用程式選擇 .NET Core 或 .NET Framework](choosing-core-framework-server.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ac-173">[Choosing between .NET Core and .NET Framework for server apps](choosing-core-framework-server.md) </span></span>  
[<span data-ttu-id="9c0ac-174">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="9c0ac-174">.NET Standard</span></span>](net-standard.md)  
[<span data-ttu-id="9c0ac-175">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="9c0ac-175">.NET Core Guide</span></span>](../core/index.md)  
[<span data-ttu-id="9c0ac-176">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="9c0ac-176">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="9c0ac-177">C# 指南</span><span class="sxs-lookup"><span data-stu-id="9c0ac-177">C# Guide</span></span>](../csharp/index.md)  
[<span data-ttu-id="9c0ac-178">F# 指南</span><span class="sxs-lookup"><span data-stu-id="9c0ac-178">F# Guide</span></span>](../fsharp/index.md)  
[<span data-ttu-id="9c0ac-179">VB.NET 指南</span><span class="sxs-lookup"><span data-stu-id="9c0ac-179">VB.NET Guide</span></span>](../visual-basic/index.md)  

