---
title: .NET 架構元件
description: 描述 .NET 架構元件，例如 .NET Standard、.NET 實作、.NET 執行階段和工具。
author: cartermp
ms.date: 10/05/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 0cdd2485e81626ffc9d17380427c29fee0f82083
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050249"
---
# <a name="net-architectural-components"></a><span data-ttu-id="62b89-103">.NET 架構元件</span><span class="sxs-lookup"><span data-stu-id="62b89-103">.NET architectural components</span></span>

<span data-ttu-id="62b89-104">.NET 應用程式是針對一或多個「.NET 實作」\*\* 所開發並在其中執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-104">A .NET app is developed for and runs in one or more *implementations of .NET*.</span></span> <span data-ttu-id="62b89-105">.NET 的執行包含 .NET Framework、.NET 5 (和 .NET Core) 以及 Mono。</span><span class="sxs-lookup"><span data-stu-id="62b89-105">Implementations of .NET include the .NET Framework, .NET 5 (and .NET Core), and Mono.</span></span> <span data-ttu-id="62b89-106">有多個 .NET 的程式開發人員（稱為 .NET Standard）通用的 API 規格。</span><span class="sxs-lookup"><span data-stu-id="62b89-106">There is an API specification common to multiple implementations of .NET that's called .NET Standard.</span></span> <span data-ttu-id="62b89-107">本文提供上述每個概念的簡介。</span><span class="sxs-lookup"><span data-stu-id="62b89-107">This article gives a brief introduction to each of these concepts.</span></span>

## <a name="net-standard"></a><span data-ttu-id="62b89-108">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="62b89-108">.NET Standard</span></span>

<span data-ttu-id="62b89-109">.NET Standard 是由 .NET 實作為基類庫所執行的一組 Api。</span><span class="sxs-lookup"><span data-stu-id="62b89-109">.NET Standard is a set of APIs that are implemented by the Base Class Library of a .NET implementation.</span></span> <span data-ttu-id="62b89-110">正式地說，它是構成制式協定的 .NET API 規格，讓您據以編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="62b89-110">More formally, it's a specification of .NET APIs that make up a uniform set of contracts that you compile your code against.</span></span> <span data-ttu-id="62b89-111">這些合約會實作為多個 .NET 執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-111">These contracts are implemented in multiple .NET implementations.</span></span>

<span data-ttu-id="62b89-112">.NET Standard 是 [目標 framework](glossary.md#target-framework)。</span><span class="sxs-lookup"><span data-stu-id="62b89-112">.NET Standard is a [target framework](glossary.md#target-framework).</span></span> <span data-ttu-id="62b89-113">如果您的程式碼以某個 .NET Standard 版本為目標，則可以在任何支援該版本 .NET Standard 的 .NET 執行上執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-113">If your code targets a version of .NET Standard, it can run on any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="62b89-114">建立 .NET Standard 是為了在不同的 .NET 執行之間啟用可攜性，但是現在 .NET 5 提供更好的方式，可在多個平臺和工作負載之間共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="62b89-114">.NET Standard was created to enable portability across different .NET implementations, but now .NET 5 offers a better way to share code across multiple platforms and workloads.</span></span> <span data-ttu-id="62b89-115">如需詳細資訊，請參閱 [.net 5 及 .NET Standard](net-standard.md#net-5-and-net-standard)。</span><span class="sxs-lookup"><span data-stu-id="62b89-115">For more information, see [.NET 5 and .NET Standard](net-standard.md#net-5-and-net-standard).</span></span>

## <a name="net-implementations"></a><span data-ttu-id="62b89-116">.NET 實作</span><span class="sxs-lookup"><span data-stu-id="62b89-116">.NET implementations</span></span>

<span data-ttu-id="62b89-117">.NET 的每項實作包括下列元件：</span><span class="sxs-lookup"><span data-stu-id="62b89-117">Each implementation of .NET includes the following components:</span></span>

- <span data-ttu-id="62b89-118">一或多個執行階段。</span><span class="sxs-lookup"><span data-stu-id="62b89-118">One or more runtimes.</span></span> <span data-ttu-id="62b89-119">範例： .NET Framework CLR、.NET 5 CLR。</span><span class="sxs-lookup"><span data-stu-id="62b89-119">Examples: .NET Framework CLR, .NET 5 CLR.</span></span>
- <span data-ttu-id="62b89-120">類別庫。</span><span class="sxs-lookup"><span data-stu-id="62b89-120">A class library.</span></span> <span data-ttu-id="62b89-121">範例： .NET Framework 基礎類別庫、.NET 5 基類庫。</span><span class="sxs-lookup"><span data-stu-id="62b89-121">Examples: .NET Framework Base Class Library, .NET 5 Base Class Library.</span></span>
- <span data-ttu-id="62b89-122">(選擇性) 一或多個應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="62b89-122">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="62b89-123">範例： [ASP.NET](https://www.asp.net/)、 [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview)和 [Windows Presentation Foundation (WPF) ](/dotnet/desktop/wpf/) 包含在 .NET Framework 和 .net 5 中。</span><span class="sxs-lookup"><span data-stu-id="62b89-123">Examples: [ASP.NET](https://www.asp.net/), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview), and [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) are included in the .NET Framework and .NET 5.</span></span>
- <span data-ttu-id="62b89-124">(選擇性) 開發工具。</span><span class="sxs-lookup"><span data-stu-id="62b89-124">Optionally, development tools.</span></span> <span data-ttu-id="62b89-125">某些開發工具可在多個實作之間共用。</span><span class="sxs-lookup"><span data-stu-id="62b89-125">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="62b89-126">有四個 Microsoft 支援的 .NET 實現：</span><span class="sxs-lookup"><span data-stu-id="62b89-126">There are four .NET implementations that Microsoft supports:</span></span>

- <span data-ttu-id="62b89-127">.NET 5 (和 .NET Core) 和更新版本</span><span class="sxs-lookup"><span data-stu-id="62b89-127">.NET 5 (and .NET Core) and later versions</span></span>
- <span data-ttu-id="62b89-128">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="62b89-128">.NET Framework</span></span>
- <span data-ttu-id="62b89-129">Mono</span><span class="sxs-lookup"><span data-stu-id="62b89-129">Mono</span></span>
- <span data-ttu-id="62b89-130">UWP</span><span class="sxs-lookup"><span data-stu-id="62b89-130">UWP</span></span>

<span data-ttu-id="62b89-131">.NET 5 現在是主要的實作為進行中開發的重點。</span><span class="sxs-lookup"><span data-stu-id="62b89-131">.NET 5 is now the primary implementation, the one that is the focus of ongoing development.</span></span> <span data-ttu-id="62b89-132">.NET 5 建基於單一程式碼基底，可支援多個平臺和許多工作負載，例如 Windows 傳統型應用程式和跨平臺主控台應用程式、雲端服務和網站。</span><span class="sxs-lookup"><span data-stu-id="62b89-132">.NET 5 is built on a single code base that supports multiple platforms and many workloads, such as Windows desktop apps and cross-platform console apps, cloud services, and websites.</span></span>

### <a name="net-5"></a><span data-ttu-id="62b89-133">.NET 5</span><span class="sxs-lookup"><span data-stu-id="62b89-133">.NET 5</span></span>

<span data-ttu-id="62b89-134">.NET 5 是 .NET 的跨平臺執行，其設計目的是要大規模處理伺服器和雲端工作負載。</span><span class="sxs-lookup"><span data-stu-id="62b89-134">.NET 5 is a cross-platform implementation of .NET that is designed to handle server and cloud workloads at scale.</span></span> <span data-ttu-id="62b89-135">也支援其他工作負載，包括桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="62b89-135">It also supports other workloads, including desktop apps.</span></span> <span data-ttu-id="62b89-136">它會在 Windows、macOS 和 Linux 上執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-136">It runs on Windows, macOS, and Linux.</span></span> <span data-ttu-id="62b89-137">它會實行 .NET Standard，因此以 .NET Standard 為目標的程式碼可以在 .NET 5 上執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-137">It implements .NET Standard, so code that targets .NET Standard can run on .NET 5.</span></span> <span data-ttu-id="62b89-138">[ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)、 [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview)和 [Windows Presentation Foundation (WPF) ](/dotnet/desktop/wpf/) 全都在 .net 5 上執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-138">[ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview), and [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) all run on .NET 5.</span></span>

<span data-ttu-id="62b89-139">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="62b89-139">For more information, see the following resources:</span></span>

- [<span data-ttu-id="62b89-140">.NET 簡介</span><span class="sxs-lookup"><span data-stu-id="62b89-140">.NET introduction</span></span>](../core/introduction.md)
- [<span data-ttu-id="62b89-141">針對伺服器應用程式在 .NET 5 和 .NET Framework 之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="62b89-141">Choosing between .NET 5 and .NET Framework for server apps</span></span>](choosing-core-framework-server.md)
- [<span data-ttu-id="62b89-142">.NET 5 和 .NET Standard</span><span class="sxs-lookup"><span data-stu-id="62b89-142">.NET 5 and .NET Standard</span></span>](net-standard.md#net-5-and-net-standard)

### <a name="net-framework"></a><span data-ttu-id="62b89-143">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="62b89-143">.NET Framework</span></span>

<span data-ttu-id="62b89-144">.NET Framework 是自2002起已存在的原始 .NET 執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-144">.NET Framework is the original .NET implementation that has existed since 2002.</span></span> <span data-ttu-id="62b89-145">4.5 版和更新版本會執行 .NET Standard，因此以 .NET Standard 為目標的程式碼可以在這些 .NET Framework 版本上執行。</span><span class="sxs-lookup"><span data-stu-id="62b89-145">Versions 4.5 and later implement .NET Standard, so code that targets .NET Standard can run on those versions of .NET Framework.</span></span> <span data-ttu-id="62b89-146">它包含其他 Windows 特定的 API，例如，使用 Windows Form 和 WPF 進行適用於 Windows 桌面開發的 API。</span><span class="sxs-lookup"><span data-stu-id="62b89-146">It contains additional Windows-specific APIs, such as APIs for Windows desktop development with Windows Forms and WPF.</span></span> <span data-ttu-id="62b89-147">.NET Framework 最適合用來建置 Windows 傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="62b89-147">.NET Framework is optimized for building Windows desktop applications.</span></span>

<span data-ttu-id="62b89-148">如需詳細資訊，請參閱 [.NET Framework 指南](../framework/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="62b89-148">For more information, see the [.NET Framework guide](../framework/index.yml).</span></span>

### <a name="mono"></a><span data-ttu-id="62b89-149">Mono</span><span class="sxs-lookup"><span data-stu-id="62b89-149">Mono</span></span>

<span data-ttu-id="62b89-150">Mono 是需要小型執行階段時主要使用的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="62b89-150">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="62b89-151">它是在 Android、macOS、iOS、tvOS 和 watchOS 上提供 Xamarin 應用程式的執行時間，主要著重于較小的使用量。</span><span class="sxs-lookup"><span data-stu-id="62b89-151">It is the runtime that powers Xamarin applications on Android, macOS, iOS, tvOS, and watchOS and is focused primarily on a small footprint.</span></span> <span data-ttu-id="62b89-152">Mono 也支援使用 Unity 引擎所建置的遊戲。</span><span class="sxs-lookup"><span data-stu-id="62b89-152">Mono also powers games built using the Unity engine.</span></span>

<span data-ttu-id="62b89-153">它支援目前發行的所有 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="62b89-153">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="62b89-154">在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。</span><span class="sxs-lookup"><span data-stu-id="62b89-154">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="62b89-155">它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62b89-155">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="62b89-156">Mono 通常可搭配 Just-In-Time 編譯器使用，但也提供適用於 iOS 等平台的完整靜態編譯器 (預先編譯)。</span><span class="sxs-lookup"><span data-stu-id="62b89-156">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="62b89-157">如需詳細資訊，請參閱 [Mono 檔](https://www.mono-project.com/docs/)。</span><span class="sxs-lookup"><span data-stu-id="62b89-157">For more information, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

### <a name="universal-windows-platform-uwp"></a><span data-ttu-id="62b89-158">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="62b89-158">Universal Windows Platform (UWP)</span></span>

<span data-ttu-id="62b89-159">UWP 是用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="62b89-159">UWP is an implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="62b89-160">它是設計來統一您可能想要鎖定的不同裝置類型，包括電腦、平板電腦、手機，甚至是 Xbox。</span><span class="sxs-lookup"><span data-stu-id="62b89-160">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="62b89-161">UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。</span><span class="sxs-lookup"><span data-stu-id="62b89-161">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="62b89-162">您可以用 c + +、c #、Visual Basic 和 JavaScript 來撰寫應用程式。</span><span class="sxs-lookup"><span data-stu-id="62b89-162">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span>

<span data-ttu-id="62b89-163">如需詳細資訊，請參閱 [通用 Windows 平臺簡介](/windows/uwp/get-started/universal-application-platform-guide)。</span><span class="sxs-lookup"><span data-stu-id="62b89-163">For more information, see [Introduction to the Universal Windows Platform](/windows/uwp/get-started/universal-application-platform-guide).</span></span>

## <a name="net-runtimes"></a><span data-ttu-id="62b89-164">.NET 執行階段</span><span class="sxs-lookup"><span data-stu-id="62b89-164">.NET runtimes</span></span>

<span data-ttu-id="62b89-165">執行階段是受管理程式的執行環境。</span><span class="sxs-lookup"><span data-stu-id="62b89-165">A runtime is the execution environment for a managed program.</span></span> <span data-ttu-id="62b89-166">OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="62b89-166">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="62b89-167">以下是 .NET 執行階段的一些範例：</span><span class="sxs-lookup"><span data-stu-id="62b89-167">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="62b89-168">適用于 .NET Framework 的 Common Language Runtime (CLR) </span><span class="sxs-lookup"><span data-stu-id="62b89-168">Common Language Runtime (CLR) for .NET Framework</span></span>
- <span data-ttu-id="62b89-169">適用于 .NET 5 的 Common Language Runtime (CLR) </span><span class="sxs-lookup"><span data-stu-id="62b89-169">Common Language Runtime (CLR) for .NET 5</span></span>
- <span data-ttu-id="62b89-170">適用於通用 Windows 平台的 .NET Native</span><span class="sxs-lookup"><span data-stu-id="62b89-170">.NET Native for Universal Windows Platform</span></span>
- <span data-ttu-id="62b89-171">適用於 Xamarin.iOS、Xamarin.Android、Xamarin.Mac 和 Mono 桌面架構的 Mono 執行階段</span><span class="sxs-lookup"><span data-stu-id="62b89-171">The Mono runtime for Xamarin.iOS, Xamarin.Android, Xamarin.Mac, and the Mono desktop framework</span></span>

## <a name="net-tooling-and-common-infrastructure"></a><span data-ttu-id="62b89-172">.NET 工具和通用基礎結構</span><span class="sxs-lookup"><span data-stu-id="62b89-172">.NET tooling and common infrastructure</span></span>

<span data-ttu-id="62b89-173">您可以存取一組詳盡的工具和基礎結構元件，以搭配各種 .NET 實作使用。</span><span class="sxs-lookup"><span data-stu-id="62b89-173">You have access to an extensive set of tools and infrastructure components that work with every implementation of .NET.</span></span> <span data-ttu-id="62b89-174">這些工具和元件包括：</span><span class="sxs-lookup"><span data-stu-id="62b89-174">These tools and components include:</span></span>

- <span data-ttu-id="62b89-175">.NET 語言及其編譯器</span><span class="sxs-lookup"><span data-stu-id="62b89-175">The .NET languages and their compilers</span></span>
- <span data-ttu-id="62b89-176">.NET 專案系統 (以 *.csproj*、*.vbproj* 和 *.fsproj* 檔案為基礎)</span><span class="sxs-lookup"><span data-stu-id="62b89-176">The .NET project system (based on *.csproj*, *.vbproj*, and *.fsproj* files)</span></span>
- <span data-ttu-id="62b89-177">[MSBuild](/visualstudio/msbuild/msbuild)，用來建立專案的組建引擎</span><span class="sxs-lookup"><span data-stu-id="62b89-177">[MSBuild](/visualstudio/msbuild/msbuild), the build engine used to build projects</span></span>
- <span data-ttu-id="62b89-178">[NuGet](/nuget/)，適用于 .Net 的 Microsoft 套件管理員</span><span class="sxs-lookup"><span data-stu-id="62b89-178">[NuGet](/nuget/), Microsoft's package manager for .NET</span></span>
- <span data-ttu-id="62b89-179">開放原始碼建置協調流程工具，例如 [CAKE](https://cakebuild.net/) 和 [FAKE](https://fake.build/)</span><span class="sxs-lookup"><span data-stu-id="62b89-179">Open-source build orchestration tools, such as [CAKE](https://cakebuild.net/) and [FAKE](https://fake.build/)</span></span>

<span data-ttu-id="62b89-180">如需詳細資訊，請參閱 [工具和生產力](../core/introduction.md#tools-and-productivity)。</span><span class="sxs-lookup"><span data-stu-id="62b89-180">For more information, see [Tools and productivity](../core/introduction.md#tools-and-productivity).</span></span>

## <a name="applicable-standards"></a><span data-ttu-id="62b89-181">適用標準</span><span class="sxs-lookup"><span data-stu-id="62b89-181">Applicable standards</span></span>

<span data-ttu-id="62b89-182">C # 語言和 Common Language 基礎結構 (CLI) 規格會透過[ECMA International &reg; ](https://www.ecma-international.org/)標準化。</span><span class="sxs-lookup"><span data-stu-id="62b89-182">The C# Language and the Common Language Infrastructure (CLI) specifications are standardized through [Ecma International&reg;](https://www.ecma-international.org/).</span></span> <span data-ttu-id="62b89-183">這些標準的第一版是在2001年12月發行的 Ecma。</span><span class="sxs-lookup"><span data-stu-id="62b89-183">The first editions of these standards were published by Ecma in December 2001.</span></span>

<span data-ttu-id="62b89-184">標準的後續修訂是由 TC49-TG2 (c # ) 和 TC49-TG3 (CLI) 在程式設計語言中的工作群組 ([TC49](https://www.ecma-international.org/memento/tc49.htm)) ，然後由 Ecma 一般元件所採用，之後透過 Iso Fast-Track 程式來採用 ISO/IEC JTC 1。</span><span class="sxs-lookup"><span data-stu-id="62b89-184">Subsequent revisions to the standards have been developed by the TC49-TG2 (C#) and TC49-TG3 (CLI) task groups within the Programming Languages Technical Committee ([TC49](https://www.ecma-international.org/memento/tc49.htm)), and adopted by the Ecma General Assembly and subsequently by ISO/IEC JTC 1 via the ISO Fast-Track process.</span></span>

### <a name="latest-standards"></a><span data-ttu-id="62b89-185">最新標準</span><span class="sxs-lookup"><span data-stu-id="62b89-185">Latest standards</span></span>

<span data-ttu-id="62b89-186">下列官方 Ecma 檔適用于 [c #](http://www.ecma-international.org/publications/standards/Ecma-334.htm) 和 [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)) ：</span><span class="sxs-lookup"><span data-stu-id="62b89-186">The following official Ecma documents are available for [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) and the [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)):</span></span>

- <span data-ttu-id="62b89-187">\*\*C # 語言標準 (5.0 版) \*\*： [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)</span><span class="sxs-lookup"><span data-stu-id="62b89-187">**The C# Language Standard (version 5.0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)</span></span>
- <span data-ttu-id="62b89-188">**通用語言基礎結構**：適用于 [pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) 表單和 [zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) 格式。</span><span class="sxs-lookup"><span data-stu-id="62b89-188">**The Common Language Infrastructure**: Available in [pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) form and [zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) form.</span></span>
- <span data-ttu-id="62b89-189">**衍生自資料分割 IV XML 檔案的資訊**： [pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) 和 [zip](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip) 格式提供。</span><span class="sxs-lookup"><span data-stu-id="62b89-189">**Information Derived from the Partition IV XML File**: Available in [pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) and [zip](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip) formats.</span></span>

<span data-ttu-id="62b89-190">ISO/IEC [公開可用的標準](https://standards.iso.org/ittf/PubliclyAvailableStandards/) 頁面提供官方的 ISO/iec 檔。</span><span class="sxs-lookup"><span data-stu-id="62b89-190">The official ISO/IEC documents are available from the ISO/IEC [Publicly Available Standards](https://standards.iso.org/ittf/PubliclyAvailableStandards/) page.</span></span> <span data-ttu-id="62b89-191">這些連結會直接來自該頁面：</span><span class="sxs-lookup"><span data-stu-id="62b89-191">These links are direct from that page:</span></span>

- <span data-ttu-id="62b89-192">**資訊技術-程式設計語言-c #**： [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)</span><span class="sxs-lookup"><span data-stu-id="62b89-192">**Information technology - Programming languages - C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)</span></span>
- <span data-ttu-id="62b89-193">**資訊技術-通用語言基礎結構 (CLI) 資料分割 I 到 VI**： [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)</span><span class="sxs-lookup"><span data-stu-id="62b89-193">**Information technology — Common Language Infrastructure (CLI) Partitions I to VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)</span></span>
- <span data-ttu-id="62b89-194">**資訊技術（通用語言基礎結構 (CLI) ）從資料分割 IV XML 檔案衍生的資訊技術報告**： [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)</span><span class="sxs-lookup"><span data-stu-id="62b89-194">**Information technology — Common Language Infrastructure (CLI) — Technical Report on Information Derived from Partition IV XML File**: [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)</span></span>

## <a name="see-also"></a><span data-ttu-id="62b89-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62b89-195">See also</span></span>

- [<span data-ttu-id="62b89-196">.NET 簡介</span><span class="sxs-lookup"><span data-stu-id="62b89-196">.NET introduction</span></span>](../core/introduction.md)
- [<span data-ttu-id="62b89-197">.NET Standard 簡介</span><span class="sxs-lookup"><span data-stu-id="62b89-197">.NET Standard introduction</span></span>](net-standard.md)
- [<span data-ttu-id="62b89-198">針對伺服器應用程式在 .NET 5 和 .NET Framework 之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="62b89-198">Choosing between .NET 5 and .NET Framework for server apps</span></span>](choosing-core-framework-server.md)
- [<span data-ttu-id="62b89-199">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="62b89-199">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="62b89-200">C# 指南</span><span class="sxs-lookup"><span data-stu-id="62b89-200">C# Guide</span></span>](../csharp/index.yml)
- [<span data-ttu-id="62b89-201">F# 指南</span><span class="sxs-lookup"><span data-stu-id="62b89-201">F# Guide</span></span>](../fsharp/index.yml)
- [<span data-ttu-id="62b89-202">Visual Basic 指南</span><span class="sxs-lookup"><span data-stu-id="62b89-202">Visual Basic Guide</span></span>](../visual-basic/index.yml)
