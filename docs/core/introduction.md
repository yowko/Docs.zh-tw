---
title: .NET 簡介和總覽
description: 深入瞭解 .NET 這項免費的開放原始碼開發平臺，可用於建立許多種類的應用程式。
author: tdykstra
ms.date: 09/28/2020
ms.custom: updateeachrelease
ms.openlocfilehash: c161daed58c94940734d057bb1b42f3b87caf97c
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756060"
---
# <a name="introduction-to-net"></a><span data-ttu-id="d47e5-103">.NET 簡介</span><span class="sxs-lookup"><span data-stu-id="d47e5-103">Introduction to .NET</span></span>

<span data-ttu-id="d47e5-104">.NET 是免費的開放原始碼開發平臺，可用於建立許多種類的應用程式，例如：</span><span class="sxs-lookup"><span data-stu-id="d47e5-104">.NET is a free, open-source development platform for building many kinds of apps, such as:</span></span>

* [<span data-ttu-id="d47e5-105">Web 應用程式、web Api 和微服務</span><span class="sxs-lookup"><span data-stu-id="d47e5-105">Web apps, web APIs, and microservices</span></span>](/aspnet/core/introduction-to-aspnet-core#recommended-learning-path)
* [<span data-ttu-id="d47e5-106">雲端中的無伺服器函式</span><span class="sxs-lookup"><span data-stu-id="d47e5-106">Serverless functions in the cloud</span></span>](/azure/azure-functions/functions-create-first-function-vs-code?pivots=programming-language-csharp)
* [<span data-ttu-id="d47e5-107">雲端原生應用程式</span><span class="sxs-lookup"><span data-stu-id="d47e5-107">Cloud native apps</span></span>](/dotnet/architecture/cloud-native/)
* [<span data-ttu-id="d47e5-108">行動應用程式</span><span class="sxs-lookup"><span data-stu-id="d47e5-108">Mobile apps</span></span>](https://dotnet.microsoft.com/learn/xamarin/hello-world-tutorial/intro)
* <span data-ttu-id="d47e5-109">傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="d47e5-109">Desktop apps</span></span>
  * [<span data-ttu-id="d47e5-110">Windows WPF</span><span class="sxs-lookup"><span data-stu-id="d47e5-110">Windows WPF</span></span>](/dotnet/desktop/wpf/)
  * [<span data-ttu-id="d47e5-111">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d47e5-111">Windows Forms</span></span>](/dotnet/desktop/winforms/)
  * [<span data-ttu-id="d47e5-112">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="d47e5-112">Universal Windows Platform (UWP)</span></span>](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* [<span data-ttu-id="d47e5-113">遊戲</span><span class="sxs-lookup"><span data-stu-id="d47e5-113">Games</span></span>](https://dotnet.microsoft.com/learn/games/unity-tutorial/intro)
* [<span data-ttu-id="d47e5-114">物聯網 (IoT)</span><span class="sxs-lookup"><span data-stu-id="d47e5-114">Internet of Things (IoT)</span></span>](https://dotnet.microsoft.com/apps/iot)
* [<span data-ttu-id="d47e5-115">機器學習</span><span class="sxs-lookup"><span data-stu-id="d47e5-115">Machine learning</span></span>](../machine-learning/index.yml)
* [<span data-ttu-id="d47e5-116">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="d47e5-116">Console apps</span></span>](tutorials/with-visual-studio-code.md)
* [<span data-ttu-id="d47e5-117">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="d47e5-117">Windows services</span></span>](/aspnet/core/host-and-deploy/windows-service)

<span data-ttu-id="d47e5-118">使用 [類別庫](../standard/class-libraries.md)，在不同的應用程式和應用程式類型之間共用功能。</span><span class="sxs-lookup"><span data-stu-id="d47e5-118">Share functionality among different apps and app types by using [class libraries](../standard/class-libraries.md).</span></span>

<span data-ttu-id="d47e5-119">使用 .NET 時，無論您要建立哪種類型的應用程式，程式碼和專案檔的外觀和操作都會相同。</span><span class="sxs-lookup"><span data-stu-id="d47e5-119">With .NET, your code and project files look and feel the same no matter which type of app you're building.</span></span> <span data-ttu-id="d47e5-120">您可以使用每個應用程式存取相同的執行時間、API 和語言功能。</span><span class="sxs-lookup"><span data-stu-id="d47e5-120">You have access to the same runtime, API, and language capabilities with each app.</span></span>

## <a name="cross-platform"></a><span data-ttu-id="d47e5-121">跨平台</span><span class="sxs-lookup"><span data-stu-id="d47e5-121">Cross platform</span></span>

<span data-ttu-id="d47e5-122">您可以為許多作業系統建立 .NET 應用程式，包括：</span><span class="sxs-lookup"><span data-stu-id="d47e5-122">You can create .NET apps for many operating systems, including:</span></span>

* <span data-ttu-id="d47e5-123">Windows</span><span class="sxs-lookup"><span data-stu-id="d47e5-123">Windows</span></span>
* <span data-ttu-id="d47e5-124">macOS</span><span class="sxs-lookup"><span data-stu-id="d47e5-124">macOS</span></span>
* <span data-ttu-id="d47e5-125">Linux</span><span class="sxs-lookup"><span data-stu-id="d47e5-125">Linux</span></span>
* <span data-ttu-id="d47e5-126">Android</span><span class="sxs-lookup"><span data-stu-id="d47e5-126">Android</span></span>
* <span data-ttu-id="d47e5-127">iOS</span><span class="sxs-lookup"><span data-stu-id="d47e5-127">iOS</span></span>
* <span data-ttu-id="d47e5-128">tvOS</span><span class="sxs-lookup"><span data-stu-id="d47e5-128">tvOS</span></span>
* <span data-ttu-id="d47e5-129">watchOS</span><span class="sxs-lookup"><span data-stu-id="d47e5-129">watchOS</span></span>

<span data-ttu-id="d47e5-130">支援的處理器架構包括：</span><span class="sxs-lookup"><span data-stu-id="d47e5-130">Supported processor architectures include:</span></span>

* <span data-ttu-id="d47e5-131">x64</span><span class="sxs-lookup"><span data-stu-id="d47e5-131">x64</span></span>
* <span data-ttu-id="d47e5-132">x86</span><span class="sxs-lookup"><span data-stu-id="d47e5-132">x86</span></span>
* <span data-ttu-id="d47e5-133">ARM32</span><span class="sxs-lookup"><span data-stu-id="d47e5-133">ARM32</span></span>
* <span data-ttu-id="d47e5-134">ARM64</span><span class="sxs-lookup"><span data-stu-id="d47e5-134">ARM64</span></span>

<span data-ttu-id="d47e5-135">.NET 可讓您使用平臺特定的功能，例如作業系統 Api。</span><span class="sxs-lookup"><span data-stu-id="d47e5-135">.NET lets you use platform-specific capabilities, such as operating system APIs.</span></span> <span data-ttu-id="d47e5-136">範例包括 Windows 上的 Windows Forms 和 WPF，以及 Xamarin 的每個行動平臺的原生系結。</span><span class="sxs-lookup"><span data-stu-id="d47e5-136">Examples are Windows Forms and WPF on Windows and the native bindings to each mobile platform from Xamarin.</span></span>

<span data-ttu-id="d47e5-137">如需詳細資訊，請參閱 [支援的 OS 生命週期原則](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md) 和 [.net RID 目錄](rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-137">For more information, see [Supported OS lifecycle policy](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md) and [.NET RID Catalog](rid-catalog.md).</span></span>

## <a name="open-source"></a><span data-ttu-id="d47e5-138">開放原始碼</span><span class="sxs-lookup"><span data-stu-id="d47e5-138">Open source</span></span>

<span data-ttu-id="d47e5-139">.NET 是開放原始碼，使用 [MIT 和 Apache 2 授權](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-139">.NET is open source, using [MIT and Apache 2 licenses](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT).</span></span> <span data-ttu-id="d47e5-140">.NET 是 [.Net Foundation](https://dotnetfoundation.org/)的專案。</span><span class="sxs-lookup"><span data-stu-id="d47e5-140">.NET is a project of the [.NET Foundation](https://dotnetfoundation.org/).</span></span>

<span data-ttu-id="d47e5-141">如需詳細資訊，請參閱 [GitHub.com 上的專案存放庫清單](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-141">For more information, see the [list of project repositories on GitHub.com](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="d47e5-142">支援</span><span class="sxs-lookup"><span data-stu-id="d47e5-142">Support</span></span>

<span data-ttu-id="d47e5-143">Microsoft 在 Windows、macOS 和 Linux 上支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="d47e5-143">.NET is supported by Microsoft on Windows, macOS, and Linux.</span></span> <span data-ttu-id="d47e5-144">它會在每個月的第二個星期二定期更新安全性和品質。</span><span class="sxs-lookup"><span data-stu-id="d47e5-144">It's updated regularly for security and quality, on the second Tuesday of each month.</span></span>

<span data-ttu-id="d47e5-145">Microsoft 的 .NET 二進位散發套件是在 Azure 中 Microsoft 維護的伺服器上建立和測試，並遵循 Microsoft 工程和安全性作法。</span><span class="sxs-lookup"><span data-stu-id="d47e5-145">.NET binary distributions from Microsoft are built and tested on Microsoft-maintained servers in Azure and follow Microsoft engineering and security practices.</span></span>

<span data-ttu-id="d47e5-146">[Red Hat 支援](https://developers.redhat.com/topics/dotnet/) Red Hat Enterprise Linux 上的 .NET (RHEL) 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-146">[Red Hat supports .NET](https://developers.redhat.com/topics/dotnet/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="d47e5-147">Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。</span><span class="sxs-lookup"><span data-stu-id="d47e5-147">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

<span data-ttu-id="d47e5-148">[Tizen 支援](https://developer.tizen.org/development/training/.net-application) Tizen 平臺上的 .net。</span><span class="sxs-lookup"><span data-stu-id="d47e5-148">[Tizen supports .NET](https://developer.tizen.org/development/training/.net-application) on Tizen platforms.</span></span>

<span data-ttu-id="d47e5-149">如需詳細資訊，請參閱 [支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-149">For more information, see the [Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="tools-and-productivity"></a><span data-ttu-id="d47e5-150">工具和生產力</span><span class="sxs-lookup"><span data-stu-id="d47e5-150">Tools and productivity</span></span>

<span data-ttu-id="d47e5-151">.NET 提供您選擇的語言、整合式開發環境 (Ide) 和其他工具。</span><span class="sxs-lookup"><span data-stu-id="d47e5-151">.NET gives you a choice of languages, integrated development environments (IDEs), and other tools.</span></span>

### <a name="programming-languages"></a><span data-ttu-id="d47e5-152">程式語言</span><span class="sxs-lookup"><span data-stu-id="d47e5-152">Programming languages</span></span>

<span data-ttu-id="d47e5-153">.NET 支援三種程式設計語言：</span><span class="sxs-lookup"><span data-stu-id="d47e5-153">.NET supports three programming languages:</span></span>

* [<span data-ttu-id="d47e5-154">C#</span><span class="sxs-lookup"><span data-stu-id="d47e5-154">C#</span></span>](../csharp/index.yml)

  <span data-ttu-id="d47e5-155">C # (發音為「看清晰的」 ) 是新式、物件導向且型別安全的程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="d47e5-155">C# (pronounced "See Sharp") is a modern, object-oriented, and type-safe programming language.</span></span> <span data-ttu-id="d47e5-156">C# 源自於是 C 系列語言，使用 C、C++、Java 和 JavaScript 的程式設計人員會立即感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="d47e5-156">C# has its roots in the C family of languages and will be immediately familiar to C, C++, Java, and JavaScript programmers.</span></span>

* [<span data-ttu-id="d47e5-157">F#</span><span class="sxs-lookup"><span data-stu-id="d47e5-157">F#</span></span>](../fsharp/index.yml)

  <span data-ttu-id="d47e5-158">F # 語言支援功能性、物件導向和命令式程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="d47e5-158">The F# language supports functional, object-oriented, and imperative programming models.</span></span>

* [<span data-ttu-id="d47e5-159">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d47e5-159">Visual Basic</span></span>](../visual-basic/index.yml)

  <span data-ttu-id="d47e5-160">在 .NET 語言中，Visual Basic 的語法是最接近一般人類語言的語法，可讓您更輕鬆地學習。</span><span class="sxs-lookup"><span data-stu-id="d47e5-160">Among the .NET languages, the syntax of Visual Basic is the closest to ordinary human language, which can make it easier to learn.</span></span> <span data-ttu-id="d47e5-161">不同于 c # 和 F #，Microsoft 正積極開發新功能，Visual Basic 的語言是穩定的。</span><span class="sxs-lookup"><span data-stu-id="d47e5-161">Unlike C# and F#, for which Microsoft is actively developing new features, the Visual Basic language is stable.</span></span> <span data-ttu-id="d47e5-162">Web 應用程式不支援 Visual Basic，但 web Api 支援此功能。</span><span class="sxs-lookup"><span data-stu-id="d47e5-162">Visual Basic isn't supported for web apps, but it is supported for web APIs.</span></span>

<span data-ttu-id="d47e5-163">以下是 .NET 語言支援的一些功能：</span><span class="sxs-lookup"><span data-stu-id="d47e5-163">Here are some of the capabilities that .NET languages support:</span></span>

* [<span data-ttu-id="d47e5-164">型別安全</span><span class="sxs-lookup"><span data-stu-id="d47e5-164">Type safety</span></span>](../standard/base-types/common-type-system.md)
* <span data-ttu-id="d47e5-165">型別推斷- [c #](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations)、 [F #](../fsharp/language-reference/type-inference.md)、 [Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="d47e5-165">Type inference - [C#](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations), [F#](../fsharp/language-reference/type-inference.md), [Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>
* [<span data-ttu-id="d47e5-166">泛型類型</span><span class="sxs-lookup"><span data-stu-id="d47e5-166">Generic types</span></span>](../standard/generics.md)
* [<span data-ttu-id="d47e5-167">委派</span><span class="sxs-lookup"><span data-stu-id="d47e5-167">Delegates</span></span>](../standard/delegates-lambdas.md)
* [<span data-ttu-id="d47e5-168">Lambda</span><span class="sxs-lookup"><span data-stu-id="d47e5-168">Lambdas</span></span>](../standard/delegates-lambdas.md)
* [<span data-ttu-id="d47e5-169">事件</span><span class="sxs-lookup"><span data-stu-id="d47e5-169">Events</span></span>](../standard/events/index.md)
* [<span data-ttu-id="d47e5-170">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d47e5-170">Exceptions</span></span>](../standard/exceptions/index.md)
* [<span data-ttu-id="d47e5-171">屬性</span><span class="sxs-lookup"><span data-stu-id="d47e5-171">Attributes</span></span>](../standard/attributes/index.md)
* [<span data-ttu-id="d47e5-172">非同步程式碼</span><span class="sxs-lookup"><span data-stu-id="d47e5-172">Asynchronous code</span></span>](../standard/async.md)
* [<span data-ttu-id="d47e5-173">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="d47e5-173">Parallel programming</span></span>](../standard/parallel-programming/index.md)
* [<span data-ttu-id="d47e5-174">程式碼分析器</span><span class="sxs-lookup"><span data-stu-id="d47e5-174">Code analyzers</span></span>](../fundamentals/code-analysis/overview.md)

### <a name="ides"></a><span data-ttu-id="d47e5-175">IDE</span><span class="sxs-lookup"><span data-stu-id="d47e5-175">IDEs</span></span>

<span data-ttu-id="d47e5-176">適用于 .NET 的整合式開發環境包括：</span><span class="sxs-lookup"><span data-stu-id="d47e5-176">The integrated development environments for .NET include:</span></span>

* [<span data-ttu-id="d47e5-177">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d47e5-177">Visual Studio</span></span>](https://visualstudio.microsoft.com/vs/)

  <span data-ttu-id="d47e5-178">只能在 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="d47e5-178">Runs on Windows only.</span></span> <span data-ttu-id="d47e5-179">具有廣泛的內建功能，其設計目的是使用 .NET。</span><span class="sxs-lookup"><span data-stu-id="d47e5-179">Has extensive built-in functionality designed to work with .NET.</span></span> <span data-ttu-id="d47e5-180">所有學生、開放原始碼參與者及個人均可免費取得此社區版。</span><span class="sxs-lookup"><span data-stu-id="d47e5-180">The Community edition is free for students, open-source contributors, and individuals.</span></span>

* [<span data-ttu-id="d47e5-181">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d47e5-181">Visual Studio Code</span></span>](https://code.visualstudio.com/)

  <span data-ttu-id="d47e5-182">在 Windows、macOS 和 Linux 上執行。</span><span class="sxs-lookup"><span data-stu-id="d47e5-182">Runs on Windows, macOS, and Linux.</span></span> <span data-ttu-id="d47e5-183">免費且開放的原始碼。</span><span class="sxs-lookup"><span data-stu-id="d47e5-183">Free and open source.</span></span> <span data-ttu-id="d47e5-184">擴充功能可搭配 .NET 語言使用。</span><span class="sxs-lookup"><span data-stu-id="d47e5-184">Extensions are available for working with .NET languages.</span></span>

* [<span data-ttu-id="d47e5-185">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="d47e5-185">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/)

  <span data-ttu-id="d47e5-186">只會在 macOS 上執行。</span><span class="sxs-lookup"><span data-stu-id="d47e5-186">Runs on macOS only.</span></span> <span data-ttu-id="d47e5-187">適用于開發適用于 iOS、Android 和 web 的 .NET 應用程式和遊戲。</span><span class="sxs-lookup"><span data-stu-id="d47e5-187">For developing .NET apps and games for iOS, Android, and web.</span></span>

* [<span data-ttu-id="d47e5-188">GitHub Codespaces</span><span class="sxs-lookup"><span data-stu-id="d47e5-188">GitHub Codespaces</span></span>](https://github.com/features/codespaces)

  <span data-ttu-id="d47e5-189">線上 Visual Studio Code 環境，目前為搶鮮版（Beta）。</span><span class="sxs-lookup"><span data-stu-id="d47e5-189">An online Visual Studio Code environment, currently in beta.</span></span>

### <a name="sdk-and-runtimes"></a><span data-ttu-id="d47e5-190">SDK 和執行時間</span><span class="sxs-lookup"><span data-stu-id="d47e5-190">SDK and runtimes</span></span>

<span data-ttu-id="d47e5-191">[.NET SDK](sdk.md)是用來開發及執行 .net 應用程式的一組程式庫和工具。</span><span class="sxs-lookup"><span data-stu-id="d47e5-191">The [.NET SDK](sdk.md) is a set of libraries and tools for developing and running .NET applications.</span></span>

<span data-ttu-id="d47e5-192">當您 [下載 .net](https://dotnet.microsoft.com/download/dotnet-core/)時，您可以選擇 SDK 或 *運行*時間，例如 .net 執行時間或 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-192">When you [download .NET](https://dotnet.microsoft.com/download/dotnet-core/), you can choose the SDK or a *runtime*, such as the .NET runtime or the ASP.NET Core runtime.</span></span> <span data-ttu-id="d47e5-193">在您想要準備執行 .NET 應用程式的電腦上安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-193">Install a runtime on a machine that you want to prepare for running .NET apps.</span></span> <span data-ttu-id="d47e5-194">在您要用於開發的電腦上安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="d47e5-194">Install the SDK on a machine that you want to use for development.</span></span> <span data-ttu-id="d47e5-195">當您下載 SDK 時，您會自動取得其執行時間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-195">When you download the SDK, you automatically get the runtimes with it.</span></span>

<span data-ttu-id="d47e5-196">SDK 下載包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="d47e5-196">The SDK download includes the following components:</span></span>

* <span data-ttu-id="d47e5-197">[.NET CLI](tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-197">The [.NET CLI](tools/index.md).</span></span> <span data-ttu-id="d47e5-198">您可以用於本機開發和連續整合腳本的命令列工具。</span><span class="sxs-lookup"><span data-stu-id="d47e5-198">Command-line tools that you can use for local development and continuous integration scripts.</span></span>
* <span data-ttu-id="d47e5-199">`dotnet`[驅動程式](tools/index.md#driver)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-199">The `dotnet` [driver](tools/index.md#driver).</span></span> <span data-ttu-id="d47e5-200">執行與架構相依的應用程式的 CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="d47e5-200">A CLI command that runs framework-dependent apps.</span></span>
* <span data-ttu-id="d47e5-201">[Roslyn](https://github.com/dotnet/roslyn)和[F #](https://github.com/microsoft/visualfsharp)程式設計語言編譯器。</span><span class="sxs-lookup"><span data-stu-id="d47e5-201">The [Roslyn](https://github.com/dotnet/roslyn) and [F#](https://github.com/microsoft/visualfsharp) programming language compilers.</span></span>
* <span data-ttu-id="d47e5-202">[MSBuild](/visualstudio/msbuild/msbuild)組建引擎。</span><span class="sxs-lookup"><span data-stu-id="d47e5-202">The [MSBuild](/visualstudio/msbuild/msbuild) build engine.</span></span>
* <span data-ttu-id="d47e5-203">[.Net 運行](#clr)時間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-203">The [.NET runtime](#clr).</span></span> <span data-ttu-id="d47e5-204">提供類型系統、元件載入、垃圾收集行程、原生 interop 及其他基本服務。</span><span class="sxs-lookup"><span data-stu-id="d47e5-204">Provides a type system, assembly loading, a garbage collector, native interop, and other basic services.</span></span>
* <span data-ttu-id="d47e5-205">[執行階段程式庫](#runtime-libraries)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-205">[Runtime libraries](#runtime-libraries).</span></span> <span data-ttu-id="d47e5-206">提供基本資料類型和基本公用程式。</span><span class="sxs-lookup"><span data-stu-id="d47e5-206">Provides primitive data types and fundamental utilities.</span></span>
* <span data-ttu-id="d47e5-207">ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-207">The ASP.NET Core runtime.</span></span> <span data-ttu-id="d47e5-208">為網際網路連線的應用程式（例如 web 應用程式、IoT 應用程式和行動後端）提供基本的服務。</span><span class="sxs-lookup"><span data-stu-id="d47e5-208">Provides basic services for internet-connected apps, such as web apps, IoT apps, and mobile backends.</span></span>
* <span data-ttu-id="d47e5-209">桌面執行時間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-209">The desktop runtime.</span></span> <span data-ttu-id="d47e5-210">提供 Windows 傳統型應用程式的基本服務，包括 Windows Forms 和 WPF。</span><span class="sxs-lookup"><span data-stu-id="d47e5-210">Provides basic services for Windows desktop apps, including Windows Forms and WPF.</span></span>

<span data-ttu-id="d47e5-211">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="d47e5-211">For more information, see the following resources:</span></span>

* [<span data-ttu-id="d47e5-212">.NET SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="d47e5-212">.NET SDK overview</span></span>](sdk.md)
* [<span data-ttu-id="d47e5-213">.NET CLI 總覽</span><span class="sxs-lookup"><span data-stu-id="d47e5-213">.NET CLI overview</span></span>](tools/index.md)
* [<span data-ttu-id="d47e5-214">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="d47e5-214">dotnet command</span></span>](tools/dotnet.md)

### <a name="project-system-and-msbuild"></a><span data-ttu-id="d47e5-215">專案系統和 MSBuild</span><span class="sxs-lookup"><span data-stu-id="d47e5-215">Project system and MSBuild</span></span>

<span data-ttu-id="d47e5-216">.NET 應用程式是使用 [MSBuild](/visualstudio/msbuild/msbuild)從原始程式碼建立的。</span><span class="sxs-lookup"><span data-stu-id="d47e5-216">A .NET app is built from source code by using [MSBuild](/visualstudio/msbuild/msbuild).</span></span> <span data-ttu-id="d47e5-217">專案檔 (*.csproj*、 *>.fsproj*或 *. vbproj*) 指定負責編譯、封裝和發佈程式碼的[目標](/visualstudio/msbuild/msbuild-targets)[和相關聯](/visualstudio/msbuild/msbuild-tasks)工作。</span><span class="sxs-lookup"><span data-stu-id="d47e5-217">A project file (*.csproj*, *.fsproj*, or *.vbproj*) specifies [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="d47e5-218">有 SDK 識別碼可參考目標和工作的標準集合。</span><span class="sxs-lookup"><span data-stu-id="d47e5-218">There are SDK identifiers that refer to standard collections of targets and tasks.</span></span> <span data-ttu-id="d47e5-219">使用這些識別碼有助於讓專案檔變小且容易使用。</span><span class="sxs-lookup"><span data-stu-id="d47e5-219">The use of these identifiers helps keep project files small and easy to work with.</span></span> <span data-ttu-id="d47e5-220">例如，以下是主控台應用程式的專案檔：</span><span class="sxs-lookup"><span data-stu-id="d47e5-220">For example, here is a project file for a console app:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d47e5-221">以下是 web 應用程式的其中一個：</span><span class="sxs-lookup"><span data-stu-id="d47e5-221">And here's one for a web app:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d47e5-222">在這些範例中， `Sdk` 元素的屬性 `Project` 會指定一組 MSBuild 目標和工作，以建立專案。</span><span class="sxs-lookup"><span data-stu-id="d47e5-222">In these examples, the `Sdk` attribute of the `Project` element specifies a set of MSBuild targets and tasks that build the project.</span></span>  <span data-ttu-id="d47e5-223">`TargetFramework`元素會指定應用程式所相依的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="d47e5-223">The `TargetFramework` element specifies the .NET version that the app depends on.</span></span> <span data-ttu-id="d47e5-224">您可以編輯專案檔，以加入專案特定的其他目標和工作。</span><span class="sxs-lookup"><span data-stu-id="d47e5-224">You can edit the project file to add additional targets and tasks specific to the project.</span></span>

<span data-ttu-id="d47e5-225">如需詳細資訊，請參閱 [.net 專案 SDK 總覽](project-sdk/overview.md) 和 [目標 framework](../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-225">For more information, see [.NET project SDK overview](project-sdk/overview.md) and [Target frameworks](../standard/frameworks.md).</span></span>

### <a name="cicd"></a><span data-ttu-id="d47e5-226">CI/CD</span><span class="sxs-lookup"><span data-stu-id="d47e5-226">CI/CD</span></span>

<span data-ttu-id="d47e5-227">MSBuild 和 .NET CLI 可以搭配各種持續整合工具和環境使用，例如：</span><span class="sxs-lookup"><span data-stu-id="d47e5-227">MSBuild and the .NET CLI can be used with various continuous integration tools and environments, such as:</span></span>

* [<span data-ttu-id="d47e5-228">GitHub 動作</span><span class="sxs-lookup"><span data-stu-id="d47e5-228">GitHub Actions</span></span>](https://github.com/features/actions)
* [<span data-ttu-id="d47e5-229">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="d47e5-229">Azure DevOps</span></span>](/azure/devops/user-guide/what-is-azure-devops)
* [<span data-ttu-id="d47e5-230">蛋糕</span><span class="sxs-lookup"><span data-stu-id="d47e5-230">CAKE</span></span>](https://cakebuild.net/)
* [<span data-ttu-id="d47e5-231">假</span><span class="sxs-lookup"><span data-stu-id="d47e5-231">FAKE</span></span>](https://fake.build/)

<span data-ttu-id="d47e5-232">如需詳細資訊，請參閱 [在持續整合 (CI 中使用 .NET SDK 和工具) ](tools/using-ci-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="d47e5-232">For more information, see [Using .NET SDK and tools in Continuous Integration (CI)](tools/using-ci-with-cli.md)</span></span>

### <a name="nuget"></a><span data-ttu-id="d47e5-233">NuGet</span><span class="sxs-lookup"><span data-stu-id="d47e5-233">NuGet</span></span>

<span data-ttu-id="d47e5-234">[NuGet](/nuget/what-is-nuget) 是專為 .net 設計的開放原始碼套件管理員。</span><span class="sxs-lookup"><span data-stu-id="d47e5-234">[NuGet](/nuget/what-is-nuget) is an open-source package manager designed for .NET.</span></span> <span data-ttu-id="d47e5-235">NuGet 套件是副檔名為的 *.zip* 檔案，其中 `.nupkg` 包含已編譯的程式碼 (dll) 、與該程式碼相關的其他檔案，以及包含套件版本號碼等資訊的描述性資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d47e5-235">A NuGet package is a *.zip* file with the `.nupkg` extension that contains compiled code (DLLs), other files related to that code, and a descriptive manifest that includes information like the package's version number.</span></span> <span data-ttu-id="d47e5-236">具有程式碼的開發人員可共用建立封裝，並將其發佈至 [nuget.org](https://nuget.org) 或私用主機。</span><span class="sxs-lookup"><span data-stu-id="d47e5-236">Developers with code to share create packages and publish them to [nuget.org](https://nuget.org) or a private host.</span></span> <span data-ttu-id="d47e5-237">如果開發人員想要使用共用程式碼，請將封裝新增至其專案，然後在其專案程式碼中呼叫封裝所公開的 API。</span><span class="sxs-lookup"><span data-stu-id="d47e5-237">Developers who want to use shared code add a package to their project and can then call the API exposed by the package in their project code.</span></span>

<span data-ttu-id="d47e5-238">如需詳細資訊，請參閱 [NuGet 檔](/nuget/)集。</span><span class="sxs-lookup"><span data-stu-id="d47e5-238">For more information, see [NuGet documentation](/nuget/).</span></span>

### <a name="net-interactive"></a><span data-ttu-id="d47e5-239">.NET 互動</span><span class="sxs-lookup"><span data-stu-id="d47e5-239">.NET Interactive</span></span>

<span data-ttu-id="d47e5-240">.NET Interactive 是一組 CLI 工具和 Api，可讓使用者在 web、markdown 和筆記本之間建立互動式體驗。</span><span class="sxs-lookup"><span data-stu-id="d47e5-240">.NET Interactive is a group of CLI tools and APIs that enable users to create interactive experiences across the web, markdown, and notebooks.</span></span>

<span data-ttu-id="d47e5-241">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="d47e5-241">For more information, see the following resources:</span></span>

* [<span data-ttu-id="d47e5-242">.NET 瀏覽器中教學課程</span><span class="sxs-lookup"><span data-stu-id="d47e5-242">.NET In-Browser Tutorial</span></span>](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1)
* [<span data-ttu-id="d47e5-243">在您的電腦上搭配 Jupyter 使用 .NET 筆記本</span><span class="sxs-lookup"><span data-stu-id="d47e5-243">Using .NET notebooks with Jupyter on your machine</span></span>](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)
* [<span data-ttu-id="d47e5-244">.NET 互動式檔</span><span class="sxs-lookup"><span data-stu-id="d47e5-244">.NET Interactive documentation</span></span>](https://github.com/dotnet/interactive/blob/main/docs/README.md)

## <a name="execution-models"></a><span data-ttu-id="d47e5-245">執行模型</span><span class="sxs-lookup"><span data-stu-id="d47e5-245">Execution models</span></span>

<span data-ttu-id="d47e5-246">.NET 應用程式會在執行時間環境中執行 [managed 程式碼](../standard/managed-code.md) ，此環境稱為 Common Language RUNTIME (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-246">.NET apps run [managed code](../standard/managed-code.md) in a runtime environment known as the Common Language Runtime (CLR).</span></span>

### <a name="clr"></a><span data-ttu-id="d47e5-247">CLR</span><span class="sxs-lookup"><span data-stu-id="d47e5-247">CLR</span></span>

<span data-ttu-id="d47e5-248">.NET [CLR](../standard/clr.md) 是一種跨平臺執行時間，包含對 Windows、MacOS 和 Linux 的支援。</span><span class="sxs-lookup"><span data-stu-id="d47e5-248">The .NET [CLR](../standard/clr.md) is a cross-platform runtime that includes support for Windows, macOS, and Linux.</span></span> <span data-ttu-id="d47e5-249">CLR 會處理記憶體配置和管理。</span><span class="sxs-lookup"><span data-stu-id="d47e5-249">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="d47e5-250">CLR 也是虛擬機器，不僅會執行應用程式，也會使用及時 (JIT) 編譯器來產生和編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="d47e5-250">The CLR is also a virtual machine that not only executes apps but also generates and compiles code using a just-in-time (JIT) compiler.</span></span>

<span data-ttu-id="d47e5-251">如需詳細資訊，請參閱 [Common Language Runtime (CLR) 總覽](../standard/clr.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-251">For more information, see [Common Language Runtime (CLR) overview](../standard/clr.md).</span></span>

### <a name="jit-compiler-and-il"></a><span data-ttu-id="d47e5-252">JIT 編譯程式和 IL</span><span class="sxs-lookup"><span data-stu-id="d47e5-252">JIT compiler and IL</span></span>

<span data-ttu-id="d47e5-253">較高階的 .NET 語言 (例如 C#) 可向下編譯成硬體無從驗證的指令集，稱為中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-253">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="d47e5-254">當應用程式執行時，JIT 編譯程式會將 IL 轉譯為處理器瞭解的機器碼。</span><span class="sxs-lookup"><span data-stu-id="d47e5-254">When an app runs, the JIT compiler translates IL to machine code that the processor understands.</span></span> <span data-ttu-id="d47e5-255">JIT 編譯發生在程式碼即將執行的同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="d47e5-255">JIT compilation happens on the same machine that the code is going to run on.</span></span>

<span data-ttu-id="d47e5-256">由於 JIT 編譯是在應用程式執行期間發生，編譯時間是執行時間的一部分。</span><span class="sxs-lookup"><span data-stu-id="d47e5-256">Since JIT compilation occurs during execution of the application, the compilation time is part of the run time.</span></span> <span data-ttu-id="d47e5-257">因此，JIT 編譯程式必須將花費在優化程式碼的時間與產生的程式碼所能產生的節省時間進行平衡。</span><span class="sxs-lookup"><span data-stu-id="d47e5-257">Therefore, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="d47e5-258">但是 JIT 編譯程式知道實際的硬體，而且可以讓開發人員不需要為不同的平臺送出不同的執行方式。</span><span class="sxs-lookup"><span data-stu-id="d47e5-258">But a JIT compiler knows the actual hardware and can free developers from having to ship different implementations for different platforms.</span></span>

<span data-ttu-id="d47e5-259">.NET JIT 編譯程式可以進行階層式 *編譯*，這表示它可以在執行時間重新編譯個別方法。</span><span class="sxs-lookup"><span data-stu-id="d47e5-259">The .NET JIT compiler can do *tiered compilation*, which means it can recompile individual methods at run time.</span></span> <span data-ttu-id="d47e5-260">這項功能可讓它快速編譯，同時仍能針對常用的方法產生高度調整的程式碼版本。</span><span class="sxs-lookup"><span data-stu-id="d47e5-260">This feature lets it compile quickly while still being able to produce a highly tuned version of the code for frequently used methods.</span></span>

<span data-ttu-id="d47e5-261">如需詳細資訊，請參閱 [Managed 執行](../standard/managed-execution-process.md) 程式和階層式 [編譯](whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-261">For more information, see [Managed execution process](../standard/managed-execution-process.md) and [Tiered compilation](whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>

### <a name="aot-compiler"></a><span data-ttu-id="d47e5-262">AOT 編譯器</span><span class="sxs-lookup"><span data-stu-id="d47e5-262">AOT compiler</span></span>

<span data-ttu-id="d47e5-263">大部分 .NET 工作負載的預設體驗都是 JIT 編譯程式，但 .NET 提供兩種預先 (AOT) 編譯的形式：</span><span class="sxs-lookup"><span data-stu-id="d47e5-263">The default experience for most .NET workloads is the JIT compiler, but .NET offers two forms of ahead-of-time (AOT) compilation:</span></span>

* <span data-ttu-id="d47e5-264">某些案例需要 100% AOT 編譯。</span><span class="sxs-lookup"><span data-stu-id="d47e5-264">Some scenarios require 100% AOT compilation.</span></span> <span data-ttu-id="d47e5-265">例如 [iOS](/xamarin/ios/)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-265">An example is [iOS](/xamarin/ios/).</span></span>
* <span data-ttu-id="d47e5-266">在其他案例中，大部分的應用程式程式碼都是由 AOT 編譯，但有些則是 JIT 編譯的。</span><span class="sxs-lookup"><span data-stu-id="d47e5-266">In other scenarios, most of an app's code is AOT-compiled but some is JIT-compiled.</span></span> <span data-ttu-id="d47e5-267">某些程式碼模式不適用於 AOT (例如泛型) 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-267">Some code patterns aren't friendly to AOT (like generics).</span></span> <span data-ttu-id="d47e5-268">這種形式的 AOT 編譯範例是可 [立即執行](whats-new/dotnet-core-3-0.md#readytorun-images) 的發行選項。</span><span class="sxs-lookup"><span data-stu-id="d47e5-268">An example of this form of AOT compilation is the [ready-to-run](whats-new/dotnet-core-3-0.md#readytorun-images) publish option.</span></span> <span data-ttu-id="d47e5-269">這種形式的 AOT 可提供 AOT 的優點，而不會有其缺點。</span><span class="sxs-lookup"><span data-stu-id="d47e5-269">This form of AOT offers the benefits of AOT without its drawbacks.</span></span>

### <a name="automatic-memory-management"></a><span data-ttu-id="d47e5-270">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="d47e5-270">Automatic memory management</span></span>

<span data-ttu-id="d47e5-271">*垃圾收集*行程 (GC) 管理應用程式的記憶體配置和釋放。</span><span class="sxs-lookup"><span data-stu-id="d47e5-271">The *garbage collector* (GC) manages the allocation and release of memory for applications.</span></span> <span data-ttu-id="d47e5-272">每當您的程式碼建立新的物件時，CLR 就會從 [managed 堆積](../standard/garbage-collection/fundamentals.md#the-managed-heap)設定物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d47e5-272">Each time your code creates a new object, the CLR allocates memory for the object from the [managed heap](../standard/garbage-collection/fundamentals.md#the-managed-heap).</span></span> <span data-ttu-id="d47e5-273">只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-273">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="d47e5-274">如果沒有足夠的可用位址空間，GC 就會檢查 managed 堆積中，應用程式不再使用的物件。</span><span class="sxs-lookup"><span data-stu-id="d47e5-274">When not enough free address space remains, the GC checks for objects in the managed heap that are no longer being used by the application.</span></span> <span data-ttu-id="d47e5-275">然後回收該記憶體。</span><span class="sxs-lookup"><span data-stu-id="d47e5-275">It then reclaims that memory.</span></span>

<span data-ttu-id="d47e5-276">GC 是可協助確保 *記憶體安全*的其中一個 CLR 服務。</span><span class="sxs-lookup"><span data-stu-id="d47e5-276">The GC is one of the CLR services that help ensure *memory safety*.</span></span> <span data-ttu-id="d47e5-277">如果程式只存取已配置的記憶體，就是記憶體安全。</span><span class="sxs-lookup"><span data-stu-id="d47e5-277">A program is memory safe if it accesses only allocated memory.</span></span> <span data-ttu-id="d47e5-278">例如，執行階段可確保應用程式不會存取陣列界限外已取消配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d47e5-278">For instance, the runtime ensures that an app doesn't access unallocated memory beyond the bounds of an array.</span></span>

<span data-ttu-id="d47e5-279">如需詳細資訊，請參閱 [自動記憶體管理](../standard/automatic-memory-management.md) 和 [垃圾收集的基本](../standard/garbage-collection/fundamentals.md)概念。</span><span class="sxs-lookup"><span data-stu-id="d47e5-279">For more information, see [Automatic memory management](../standard/automatic-memory-management.md) and [Fundamentals of garbage collection](../standard/garbage-collection/fundamentals.md).</span></span>

### <a name="working-with-unmanaged-resources"></a><span data-ttu-id="d47e5-280">使用 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="d47e5-280">Working with unmanaged resources</span></span>

<span data-ttu-id="d47e5-281">有時候，程式碼需要參考 *未受管理的資源*。</span><span class="sxs-lookup"><span data-stu-id="d47e5-281">Sometimes code needs to reference *unmanaged resources*.</span></span> <span data-ttu-id="d47e5-282">Unmanaged 資源是指 .NET 執行階段不會自動維護的資源。</span><span class="sxs-lookup"><span data-stu-id="d47e5-282">Unmanaged resources are resources that aren't automatically maintained by the .NET runtime.</span></span> <span data-ttu-id="d47e5-283">例如檔案控制程式碼就是 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="d47e5-283">For example, a file handle is an unmanaged resource.</span></span> <span data-ttu-id="d47e5-284"><xref:System.IO.FileStream> 物件是Managed 物件，但會 Unmanaged 檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d47e5-284">A <xref:System.IO.FileStream> object is a managed object, but it references a file handle, which is unmanaged.</span></span> <span data-ttu-id="d47e5-285">當您使用完成時 <xref:System.IO.FileStream> ，您必須明確釋放檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d47e5-285">When you're done using the <xref:System.IO.FileStream>, you need to explicitly release the file handle.</span></span>

<span data-ttu-id="d47e5-286">在.NET 中，參考 Unmanaged 資源的物件會實作 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="d47e5-286">In .NET, objects that reference unmanaged resources implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="d47e5-287">當您完成使用此物件時，您可以呼叫物件的 <xref:System.IDisposable.Dispose> 方法來釋放任何 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="d47e5-287">When you're done using the object, you call the object's <xref:System.IDisposable.Dispose> method, which is responsible for releasing any unmanaged resources.</span></span> <span data-ttu-id="d47e5-288">.Net 語言提供了一個方便的 `using` 語句， ([c #](../csharp/language-reference/keywords/using.md)、 [F #](../fsharp/language-reference/resource-management-the-use-keyword.md)、 [VB](../visual-basic/language-reference/statements/using-statement.md)) ，可確保 `Dispose` 呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="d47e5-288">The .NET languages provide a convenient `using` statement ([C#](../csharp/language-reference/keywords/using.md), [F#](../fsharp/language-reference/resource-management-the-use-keyword.md), [VB](../visual-basic/language-reference/statements/using-statement.md)) that ensures the `Dispose` method is called.</span></span>

<span data-ttu-id="d47e5-289">如需詳細資訊，請參閱 [清除非受控資源](../standard/garbage-collection/unmanaged.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-289">For more information, see [Cleaning up unmanaged resources](../standard/garbage-collection/unmanaged.md).</span></span>

## <a name="deployment-models"></a><span data-ttu-id="d47e5-290">部署模型</span><span class="sxs-lookup"><span data-stu-id="d47e5-290">Deployment models</span></span>

<span data-ttu-id="d47e5-291">.NET 應用程式可在兩種不同的模式下發行：</span><span class="sxs-lookup"><span data-stu-id="d47e5-291">.NET apps can be published in two different modes:</span></span>

* <span data-ttu-id="d47e5-292">將應用程式發佈為 *獨立* 應用程式會產生可執行檔，其中包含 .net [運行](#sdk-and-runtimes) 時間和連結 [庫](#runtime-libraries)，以及應用程式及其相依性。</span><span class="sxs-lookup"><span data-stu-id="d47e5-292">Publishing an app as *self-contained* produces an executable file that includes the .NET [runtime](#sdk-and-runtimes) and [libraries](#runtime-libraries), and the application and its dependencies.</span></span> <span data-ttu-id="d47e5-293">應用程式的使用者可以在未安裝 .NET 執行時間的電腦上執行它。</span><span class="sxs-lookup"><span data-stu-id="d47e5-293">Users of the application can run it on a machine that doesn't have the .NET runtime installed.</span></span> <span data-ttu-id="d47e5-294">獨立應用程式是平臺專屬的應用程式，而且可以選擇性地使用 [AOT 編譯](#aot-compiler)形式來發佈。</span><span class="sxs-lookup"><span data-stu-id="d47e5-294">Self-contained apps are platform-specific, and they can optionally be published using a form of [AOT compilation](#aot-compiler).</span></span>

* <span data-ttu-id="d47e5-295">將應用程式發行為與 *framework 相依* 的應用程式，會產生可執行檔和二進位檔案 (*.dll* 檔案，) 只包含應用程式本身及其相依性。</span><span class="sxs-lookup"><span data-stu-id="d47e5-295">Publishing an app as *framework-dependent* produces an executable file and binary files (*.dll* files) that include only the application itself and its dependencies.</span></span> <span data-ttu-id="d47e5-296">應用程式的使用者必須分別安裝 .NET [運行](#sdk-and-runtimes)時間。</span><span class="sxs-lookup"><span data-stu-id="d47e5-296">Users of the application have to separately install the .NET [runtime](#sdk-and-runtimes).</span></span> <span data-ttu-id="d47e5-297">可執行檔是平臺專屬的，但架構相依應用程式的 *.dll* 檔案是跨平臺。</span><span class="sxs-lookup"><span data-stu-id="d47e5-297">The executable file is platform-specific, but The *.dll* files of framework-dependent applications are cross-platform.</span></span>

  <span data-ttu-id="d47e5-298">您可以並存安裝多個版本的執行時間，以執行以不同執行階段版本為目標的架構相依應用程式。</span><span class="sxs-lookup"><span data-stu-id="d47e5-298">You can install multiple versions of the runtime side by side to run framework-dependent apps that target different versions of the runtime.</span></span> <span data-ttu-id="d47e5-299">如需詳細資訊，請參閱 [目標 framework](../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-299">For more information, see [Target frameworks](../standard/frameworks.md).</span></span>

<span data-ttu-id="d47e5-300">系統會針對特定的目標平臺產生可執行檔，您可以使用執行時間識別碼來指定 [ (RID) ](rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-300">Executables are produced for specific target platforms, which you specify with a [runtime identifier (RID)](rid-catalog.md).</span></span>

<span data-ttu-id="d47e5-301">如需詳細資訊，請參閱 [.net 應用程式發行總覽](deploying/index.md) 和 [.Net 和 Docker 簡介](docker/introduction.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-301">For more information, see [.NET application publishing overview](deploying/index.md) and [Introduction to .NET and Docker](docker/introduction.md).</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="d47e5-302">執行時間程式庫</span><span class="sxs-lookup"><span data-stu-id="d47e5-302">Runtime libraries</span></span>

<span data-ttu-id="d47e5-303">.NET 有一組廣泛的標準類別庫。</span><span class="sxs-lookup"><span data-stu-id="d47e5-303">.NET has an expansive standard set of class libraries.</span></span> <span data-ttu-id="d47e5-304">核心集稱為「基類庫」（base class library）， (BCL) 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-304">The core set is referred to as the base class library (BCL).</span></span> <span data-ttu-id="d47e5-305">完整的集合稱為執行時間程式庫或 framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="d47e5-305">The complete set is referred to as the runtime libraries or framework libraries.</span></span> <span data-ttu-id="d47e5-306">這些程式庫提供許多一般用途和工作負載特定類型和公用程式功能的實作為。</span><span class="sxs-lookup"><span data-stu-id="d47e5-306">These libraries provide implementations for many general-purpose and workload-specific types and utility functionality.</span></span>

<span data-ttu-id="d47e5-307">以下是執行時間程式庫中定義的一些類型範例：</span><span class="sxs-lookup"><span data-stu-id="d47e5-307">Here are some examples of types defined in the runtime libraries:</span></span>

* <span data-ttu-id="d47e5-308">基本類型，例如 <xref:System.Boolean?displayProperty=nameWithType> 和 <xref:System.Int32?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-308">Primitive types, such as <xref:System.Boolean?displayProperty=nameWithType> and <xref:System.Int32?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="d47e5-309">集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d47e5-309">Collections, such as <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> and <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="d47e5-310">資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 和 <xref:System.Data.DataTable?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-310">Data types, such as <xref:System.Data.DataSet?displayProperty=nameWithType> and <xref:System.Data.DataTable?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="d47e5-311">網路公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-311">Network utility types, such as <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="d47e5-312">檔案[和資料流程 i/o](../standard/io/index.md)公用程式類型，例如 <xref:System.IO.FileStream?displayProperty=nameWithType> 和 <xref:System.IO.TextWriter?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-312">[File and stream I/O](../standard/io/index.md) utility types, such as <xref:System.IO.FileStream?displayProperty=nameWithType> and <xref:System.IO.TextWriter?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="d47e5-313">[序列化](../standard/serialization/index.md) 公用程式類型，例如 <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 和 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-313">[Serialization](../standard/serialization/index.md) utility types, such as <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> and <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="d47e5-314">高效能類型，例如 <xref:System.Span%601?displayProperty=nameWithType> 、 <xref:System.Numerics.Vector?displayProperty=nameWithType> 和 [管線](../standard/io/pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-314">High-performance types, such as <xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Numerics.Vector?displayProperty=nameWithType>, and [Pipelines](../standard/io/pipelines.md).</span></span>

<span data-ttu-id="d47e5-315">如需詳細資訊，請參閱 [架構](../standard/framework-libraries.md) 程式庫和連結 [庫的原始程式碼](https://github.com/dotnet/runtime/tree/master/src/libraries)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-315">For more information, see [Framework libraries](../standard/framework-libraries.md) and [the source code for the libraries](https://github.com/dotnet/runtime/tree/master/src/libraries).</span></span>

## <a name="microsoftextensions-libraries"></a><span data-ttu-id="d47e5-316">Microsoft Extensions 程式庫</span><span class="sxs-lookup"><span data-stu-id="d47e5-316">Microsoft.Extensions libraries</span></span>

<span data-ttu-id="d47e5-317">某些常用應用程式功能的程式庫不包含在執行時間程式庫中，但可在 NuGet 套件中使用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d47e5-317">Libraries for some commonly used application functionality aren't included in the runtime libraries but are made available in NuGet packages, such as the following:</span></span>

| <span data-ttu-id="d47e5-318">Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="d47e5-318">NuGet package</span></span> | <span data-ttu-id="d47e5-319">文件</span><span class="sxs-lookup"><span data-stu-id="d47e5-319">Documentation</span></span> |
|---------|---------|
| [<span data-ttu-id="d47e5-320">Microsoft.Extensions.Hosting</span><span class="sxs-lookup"><span data-stu-id="d47e5-320">Microsoft.Extensions.Hosting</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) | [<span data-ttu-id="d47e5-321">應用程式存留期管理 (一般主機) </span><span class="sxs-lookup"><span data-stu-id="d47e5-321">Application lifetime management (Generic Host)</span></span>](extensions/generic-host.md) |
| [<span data-ttu-id="d47e5-322">DependencyInjection</span><span class="sxs-lookup"><span data-stu-id="d47e5-322">Microsoft.Extensions.DependencyInjection</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection) | [<span data-ttu-id="d47e5-323">相依性插入 (DI)</span><span class="sxs-lookup"><span data-stu-id="d47e5-323">Dependency injection (DI)</span></span>](extensions/dependency-injection.md)
| [<span data-ttu-id="d47e5-324">Microsoft.Extensions.Configuration</span><span class="sxs-lookup"><span data-stu-id="d47e5-324">Microsoft.Extensions.Configuration</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Configuration) | [<span data-ttu-id="d47e5-325">設定</span><span class="sxs-lookup"><span data-stu-id="d47e5-325">Configuration</span></span>](extensions/configuration.md) |
| [<span data-ttu-id="d47e5-326">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="d47e5-326">Microsoft.Extensions.Logging</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Logging) | [<span data-ttu-id="d47e5-327">Logging</span><span class="sxs-lookup"><span data-stu-id="d47e5-327">Logging</span></span>](extensions/logging.md) |
| [<span data-ttu-id="d47e5-328">Microsoft. Extensions. 選項</span><span class="sxs-lookup"><span data-stu-id="d47e5-328">Microsoft.Extensions.Options</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Options) | [<span data-ttu-id="d47e5-329">選項模式</span><span class="sxs-lookup"><span data-stu-id="d47e5-329">Options pattern</span></span>](extensions/options.md) |

<span data-ttu-id="d47e5-330">如需詳細資訊，請參閱 [GitHub 上的 dotnet/extensions 存放庫](https://github.com/dotnet/extensions)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-330">For more information, see the [dotnet/extensions repository on GitHub](https://github.com/dotnet/extensions).</span></span>

## <a name="data-access"></a><span data-ttu-id="d47e5-331">資料存取</span><span class="sxs-lookup"><span data-stu-id="d47e5-331">Data access</span></span>

<span data-ttu-id="d47e5-332">.NET 提供物件/關聯式對應程式 (ORM) 以及在程式碼中撰寫 SQL 查詢的方式。</span><span class="sxs-lookup"><span data-stu-id="d47e5-332">.NET provides an Object/Relational Mapper (ORM) and a way to write SQL queries in code.</span></span>

### <a name="entity-framework-core"></a><span data-ttu-id="d47e5-333">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="d47e5-333">Entity Framework Core</span></span>

<span data-ttu-id="d47e5-334">Entity Framework (EF) Core 是一個 [開放原始](https://github.com/aspnet/EntityFrameworkCore) 碼和跨平臺的資料存取技術，可作為 ORM。</span><span class="sxs-lookup"><span data-stu-id="d47e5-334">Entity Framework (EF) Core is an [open source](https://github.com/aspnet/EntityFrameworkCore) and cross-platform data-access technology that can serve as an ORM.</span></span> <span data-ttu-id="d47e5-335">EF Core 可讓您在程式碼中參考 .NET 物件來處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="d47e5-335">EF Core lets you work with a database by referring to .NET objects in code.</span></span> <span data-ttu-id="d47e5-336">它可減少您需要撰寫和測試的資料存取程式碼數量。</span><span class="sxs-lookup"><span data-stu-id="d47e5-336">It reduces the amount of data-access code you would otherwise need to write and test.</span></span> <span data-ttu-id="d47e5-337">EF Core 支援許多資料庫引擎。</span><span class="sxs-lookup"><span data-stu-id="d47e5-337">EF Core supports many database engines.</span></span>

<span data-ttu-id="d47e5-338">如需詳細資訊，請參閱 [Entity Framework Core](/ef/core/) 和 [資料庫提供者](/ef/core/providers/)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-338">For more information, see [Entity Framework Core](/ef/core/) and [Database Providers](/ef/core/providers/).</span></span>

### <a name="linq"></a><span data-ttu-id="d47e5-339">LINQ</span><span class="sxs-lookup"><span data-stu-id="d47e5-339">LINQ</span></span>

<span data-ttu-id="d47e5-340">語言整合式查詢 (LINQ) 可讓您撰寫用來運算元據的宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="d47e5-340">Language-integrated query (LINQ) lets you write declarative code for operating on data.</span></span> <span data-ttu-id="d47e5-341">資料可以是許多形式 (例如記憶體內部物件、SQL 資料庫或 XML 文件)，但您撰寫的 LINQ 程式碼在資料來源方面通常大同小異。</span><span class="sxs-lookup"><span data-stu-id="d47e5-341">The data can be in many forms (such as in-memory objects, a SQL database, or an XML document), but the LINQ code you write typically doesn't differ by data source.</span></span>

<span data-ttu-id="d47e5-342">如需詳細資訊，請參閱 [LINQ (語言整合式查詢) 總覽](../standard/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-342">For more information, see [LINQ (Language Integrated Query) overview](../standard/linq/index.md).</span></span>

## <a name="net-terminology"></a><span data-ttu-id="d47e5-343">.NET 術語</span><span class="sxs-lookup"><span data-stu-id="d47e5-343">.NET terminology</span></span>

<span data-ttu-id="d47e5-344">若要瞭解 .NET 檔，可協助您瞭解某些詞彙的使用方式如何隨時間而改變。</span><span class="sxs-lookup"><span data-stu-id="d47e5-344">To understand .NET documentation, it can help to know how the usage of some terms has changed over time.</span></span>

### <a name="net-core-and-net-5"></a><span data-ttu-id="d47e5-345">.NET Core 和 .NET 5</span><span class="sxs-lookup"><span data-stu-id="d47e5-345">.NET Core and .NET 5</span></span>

<span data-ttu-id="d47e5-346">在2002中，Microsoft 發行了 [.NET Framework](../framework/get-started/overview.md)，這是用來建立 Windows 應用程式的開發平臺。</span><span class="sxs-lookup"><span data-stu-id="d47e5-346">In 2002, Microsoft released [.NET Framework](../framework/get-started/overview.md), a development platform for creating Windows apps.</span></span> <span data-ttu-id="d47e5-347">今天 .NET Framework 是4.8 版，而且 Microsoft 仍 [支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)此版本。</span><span class="sxs-lookup"><span data-stu-id="d47e5-347">Today .NET Framework is at version 4.8 and is still [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework).</span></span>

<span data-ttu-id="d47e5-348">在2014中，Microsoft 開始撰寫 .NET Framework 的跨平臺開放原始碼後續工作。</span><span class="sxs-lookup"><span data-stu-id="d47e5-348">In 2014, Microsoft began writing a cross-platform, open-source successor to .NET Framework.</span></span> <span data-ttu-id="d47e5-349">這項新的 .NET 實名為 .NET Core，直到它到達3.1 版為止。</span><span class="sxs-lookup"><span data-stu-id="d47e5-349">This new implementation of .NET was named .NET Core until it reached version 3.1.</span></span> <span data-ttu-id="d47e5-350">.NET Core 3.1 之後的下一個版本是 .NET 5.0，目前為預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="d47e5-350">The next version after .NET Core 3.1 is .NET 5.0, which is currently in preview.</span></span> <span data-ttu-id="d47e5-351">已略過第4版，以避免這種 .NET 的執行與 .NET Framework 4.8 的混淆。</span><span class="sxs-lookup"><span data-stu-id="d47e5-351">Version number 4 was skipped to avoid confusion between this implementation of .NET and .NET Framework 4.8.</span></span> <span data-ttu-id="d47e5-352">已捨棄名稱 "Core"，以確定這現在是 .NET 的主要執行。</span><span class="sxs-lookup"><span data-stu-id="d47e5-352">The name "Core" was dropped to make clear that this is now the main implementation of .NET.</span></span>

<span data-ttu-id="d47e5-353">這篇文章是關於 .NET 5，但 .NET 5 的大部分檔仍有 ".NET Core" 或 ".NET Framework" 的參考。</span><span class="sxs-lookup"><span data-stu-id="d47e5-353">This article is about .NET 5, but much of the documentation for .NET 5 still has references to ".NET Core" or ".NET Framework".</span></span> <span data-ttu-id="d47e5-354">此外，"Core" 會保留在名稱 [ASP.NET Core](/aspnet/core/) 和 [Entity Framework Core](/ef/core/)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-354">In addition, "Core" remains in the names [ASP.NET Core](/aspnet/core/) and [Entity Framework Core](/ef/core/).</span></span>

<span data-ttu-id="d47e5-355">檔也會參考 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="d47e5-355">The documentation also refers to .NET Standard.</span></span> <span data-ttu-id="d47e5-356">[.NET Standard](../standard/net-standard.md)是一種 API 規格，可讓您開發適用于多個 .net 的類別庫。</span><span class="sxs-lookup"><span data-stu-id="d47e5-356">The [.NET Standard](../standard/net-standard.md) is an API specification that lets you develop class libraries for multiple implementations of .NET.</span></span>

<span data-ttu-id="d47e5-357">如需詳細資訊，請參閱 [.net 架構元件](../standard/components.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-357">For more information, see [.NET architectural components](../standard/components.md).</span></span>

### <a name="overloaded-terms"></a><span data-ttu-id="d47e5-358">多載詞彙</span><span class="sxs-lookup"><span data-stu-id="d47e5-358">Overloaded terms</span></span>

<span data-ttu-id="d47e5-359">適用于 .NET 的部分術語可能會造成混淆，因為相同的單字在不同的內容中使用不同的方式。</span><span class="sxs-lookup"><span data-stu-id="d47e5-359">Some of the terminology for .NET can be confusing because the same word is used in different ways in different contexts.</span></span> <span data-ttu-id="d47e5-360">以下是一些比較顯著的實例：</span><span class="sxs-lookup"><span data-stu-id="d47e5-360">Here are a few of the more prominent instances:</span></span>

* <span data-ttu-id="d47e5-361">**執行階段**</span><span class="sxs-lookup"><span data-stu-id="d47e5-361">**runtime**</span></span>

  |<span data-ttu-id="d47e5-362">Context</span><span class="sxs-lookup"><span data-stu-id="d47e5-362">Context</span></span>  |<span data-ttu-id="d47e5-363">「執行時間」表示</span><span class="sxs-lookup"><span data-stu-id="d47e5-363">"runtime" meaning</span></span> |
  |---------|---------|
  | [<span data-ttu-id="d47e5-364">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="d47e5-364">Common Language Runtime (CLR)</span></span>](#clr)| <span data-ttu-id="d47e5-365">受管理程式的執行環境。</span><span class="sxs-lookup"><span data-stu-id="d47e5-365">The execution environment for a managed program.</span></span> <span data-ttu-id="d47e5-366">作業系統是執行時間環境的一部分，但不是 .NET 執行時間的一部分。</span><span class="sxs-lookup"><span data-stu-id="d47e5-366">The OS is part of the runtime environment but isn't part of the .NET runtime.</span></span> |
  | [<span data-ttu-id="d47e5-367">.NET 下載頁面上的 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="d47e5-367">.NET runtime on the .NET download page</span></span>](https://dotnet.microsoft.com/download/dotnet-core) | <span data-ttu-id="d47e5-368">[CLR](#clr)與執行時間連結[庫](#runtime-libraries)，兩者共同提供執行[架構相依](#deployment-models)應用程式的支援。</span><span class="sxs-lookup"><span data-stu-id="d47e5-368">The [CLR](#clr) and [runtime libraries](#runtime-libraries), which together provide support for running [framework-dependent](#deployment-models) apps.</span></span> <span data-ttu-id="d47e5-369">此頁面也提供 ASP.NET Core server 應用程式和 Windows 桌面應用程式的執行時間選項。</span><span class="sxs-lookup"><span data-stu-id="d47e5-369">The page also offers runtime choices for ASP.NET Core server apps and Windows desktop apps.</span></span> |
  | [<span data-ttu-id="d47e5-370"> (RID) 的執行時間識別碼 </span><span class="sxs-lookup"><span data-stu-id="d47e5-370">Runtime Identifier (RID)</span></span>](rid-catalog.md) | <span data-ttu-id="d47e5-371">.NET 應用程式執行所在的 OS 平臺和 CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="d47e5-371">The OS platform and CPU architecture that a .NET app runs on.</span></span> <span data-ttu-id="d47e5-372">例如： Windows x64、Linux x64。</span><span class="sxs-lookup"><span data-stu-id="d47e5-372">For example: Windows x64, Linux x64.</span></span> |

* <span data-ttu-id="d47e5-373">**框架**</span><span class="sxs-lookup"><span data-stu-id="d47e5-373">**framework**</span></span>

  |<span data-ttu-id="d47e5-374">Context</span><span class="sxs-lookup"><span data-stu-id="d47e5-374">Context</span></span>  | <span data-ttu-id="d47e5-375">"framework" 意義</span><span class="sxs-lookup"><span data-stu-id="d47e5-375">"framework" meaning</span></span> |
  |---------|---------------------|
  | <span data-ttu-id="d47e5-376">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d47e5-376">.NET Framework</span></span> | <span data-ttu-id="d47e5-377">.NET 的原始、僅限 Windows 的實作為。</span><span class="sxs-lookup"><span data-stu-id="d47e5-377">The original, Windows-only implementation of .NET.</span></span> <span data-ttu-id="d47e5-378">"Framework" 為大寫。</span><span class="sxs-lookup"><span data-stu-id="d47e5-378">"Framework" is capitalized.</span></span> |
  | <span data-ttu-id="d47e5-379">Target Framework - 目標 Framework</span><span class="sxs-lookup"><span data-stu-id="d47e5-379">target framework</span></span> | <span data-ttu-id="d47e5-380">.NET 應用程式或程式庫依賴的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="d47e5-380">The collection of APIs that a .NET app or library relies on.</span></span> <span data-ttu-id="d47e5-381">範例： .NET Core 3.1、.NET Standard 2。0</span><span class="sxs-lookup"><span data-stu-id="d47e5-381">Examples: .NET Core 3.1, .NET Standard 2.0</span></span> |
  | <span data-ttu-id="d47e5-382">Target Framework Moniker (TFM)</span><span class="sxs-lookup"><span data-stu-id="d47e5-382">Target Framework Moniker (TFM)</span></span>  | <span data-ttu-id="d47e5-383">TFM 是標準化的權杖格式，用於指定 .NET 應用程式或程式庫的目標 framework。</span><span class="sxs-lookup"><span data-stu-id="d47e5-383">A TFM is a standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="d47e5-384">範例： `net462` 適用于 .NET Framework 4.6.2。</span><span class="sxs-lookup"><span data-stu-id="d47e5-384">Example: `net462` for .NET Framework 4.6.2.</span></span> |
  | <span data-ttu-id="d47e5-385">與 framework 相依的應用程式</span><span class="sxs-lookup"><span data-stu-id="d47e5-385">framework-dependent app</span></span> | <span data-ttu-id="d47e5-386">只能在您從 [.net 下載頁面](https://dotnet.microsoft.com/download/dotnet-core)安裝執行時間的電腦上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d47e5-386">An app that can only run on a machine where you've installed the runtime from the [.NET download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span> <span data-ttu-id="d47e5-387">此使用方式中的「架構」與您從 .NET 下載頁面下載的「執行時間」相同。</span><span class="sxs-lookup"><span data-stu-id="d47e5-387">"Framework" in this usage is the same thing as the "runtime" that you download from the .NET download page.</span></span> |
  
* <span data-ttu-id="d47e5-388">**SDK**</span><span class="sxs-lookup"><span data-stu-id="d47e5-388">**SDK**</span></span>

  |<span data-ttu-id="d47e5-389">Context</span><span class="sxs-lookup"><span data-stu-id="d47e5-389">Context</span></span>  | <span data-ttu-id="d47e5-390">"SDK" 意義</span><span class="sxs-lookup"><span data-stu-id="d47e5-390">"SDK" meaning</span></span> |
  |---------|---------------|
  | [<span data-ttu-id="d47e5-391">.NET 下載頁面上的 SDK</span><span class="sxs-lookup"><span data-stu-id="d47e5-391">SDK on the .NET download page</span></span>](#sdk-and-runtimes)  | <span data-ttu-id="d47e5-392">您下載並安裝以開發和執行 .NET 應用程式的工具和程式庫集合。</span><span class="sxs-lookup"><span data-stu-id="d47e5-392">A collection of tools and libraries that you download and install to develop and run .NET apps.</span></span> <span data-ttu-id="d47e5-393">包括 CLI、MSBuild、.NET 執行時間和其他元件。</span><span class="sxs-lookup"><span data-stu-id="d47e5-393">Includes the CLI, MSBuild, the .NET runtime, and other components.</span></span>|
  | [<span data-ttu-id="d47e5-394">SDK 樣式專案</span><span class="sxs-lookup"><span data-stu-id="d47e5-394">SDK-style project</span></span>](#project-system-and-msbuild) | <span data-ttu-id="d47e5-395">一組 MSBuild 目標和工作，可指定如何建立特定應用程式類型的專案。</span><span class="sxs-lookup"><span data-stu-id="d47e5-395">A set of MSBuild targets and tasks that specifies how to build a project for a particular app type.</span></span> <span data-ttu-id="d47e5-396">此概念中的 SDK 是使用 `Sdk` 專案檔中專案的屬性所指定 `Project` 。</span><span class="sxs-lookup"><span data-stu-id="d47e5-396">The SDK in this sense is specified by using the `Sdk` attribute of the `Project` element in a project file.</span></span> |

* <span data-ttu-id="d47e5-397">**平台**</span><span class="sxs-lookup"><span data-stu-id="d47e5-397">**platform**</span></span>

  |<span data-ttu-id="d47e5-398">Context</span><span class="sxs-lookup"><span data-stu-id="d47e5-398">Context</span></span>  | <span data-ttu-id="d47e5-399">「平臺」意義</span><span class="sxs-lookup"><span data-stu-id="d47e5-399">"platform" meaning</span></span> |
  |---------|--------------------|
  | <span data-ttu-id="d47e5-400">跨平臺</span><span class="sxs-lookup"><span data-stu-id="d47e5-400">cross platform</span></span> | <span data-ttu-id="d47e5-401">在此詞彙中，「平臺」表示作業系統和其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。</span><span class="sxs-lookup"><span data-stu-id="d47e5-401">In this term, "platform" means an operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span> |
  | <span data-ttu-id="d47e5-402">.NET 平臺</span><span class="sxs-lookup"><span data-stu-id="d47e5-402">.NET platform</span></span> | <span data-ttu-id="d47e5-403">使用方式會有所不同。</span><span class="sxs-lookup"><span data-stu-id="d47e5-403">Usage varies.</span></span> <span data-ttu-id="d47e5-404">參考可能是一種 .NET (的執行，例如 .NET Framework 或 .NET 5) 或 .NET 的整體概念，包括所有的實作為。</span><span class="sxs-lookup"><span data-stu-id="d47e5-404">The reference may be to one implementation of .NET (such as .NET Framework or .NET 5) or to an overarching concept of .NET including all implementations.</span></span> |

<span data-ttu-id="d47e5-405">如需 .NET 術語的詳細資訊，請參閱 [.net 詞彙](../standard/glossary.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-405">For more information about .NET terminology, see the [.NET glossary](../standard/glossary.md).</span></span>

## <a name="advanced-scenarios"></a><span data-ttu-id="d47e5-406">進階案例</span><span class="sxs-lookup"><span data-stu-id="d47e5-406">Advanced scenarios</span></span>

<span data-ttu-id="d47e5-407">下列各節說明一些適用于先進案例的 .NET 功能。</span><span class="sxs-lookup"><span data-stu-id="d47e5-407">The following sections explain some capabilities of .NET that are useful in advanced scenarios.</span></span>

### <a name="native-interop"></a><span data-ttu-id="d47e5-408">原生 interop</span><span class="sxs-lookup"><span data-stu-id="d47e5-408">Native interop</span></span>

<span data-ttu-id="d47e5-409">每個作業系統都包含提供系統服務的應用程式開發介面 (API)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-409">Every operating system includes an application programming interface (API) that provides system services.</span></span> <span data-ttu-id="d47e5-410">.NET 提供幾種方式來呼叫這些 API。</span><span class="sxs-lookup"><span data-stu-id="d47e5-410">.NET provides several ways to call those APIs.</span></span>

<span data-ttu-id="d47e5-411">與原生 Api 交互操作的主要方式是透過「平台叫用」或 P/Invoke （短）。</span><span class="sxs-lookup"><span data-stu-id="d47e5-411">The main way to interoperate with native APIs is via "platform invoke" or P/Invoke for short.</span></span> <span data-ttu-id="d47e5-412">Linux 和 Windows 平臺之間支援 P/Invoke。</span><span class="sxs-lookup"><span data-stu-id="d47e5-412">P/Invoke is supported across Linux and Windows platforms.</span></span> <span data-ttu-id="d47e5-413">僅限 Windows 的交互操作方法稱為「COM interop」，可搭配 managed 程式碼中的 [COM 元件](/cpp/atl/introduction-to-com) 使用。</span><span class="sxs-lookup"><span data-stu-id="d47e5-413">A Windows-only way of interoperating is known as "COM interop," which works with [COM components](/cpp/atl/introduction-to-com) in managed code.</span></span> <span data-ttu-id="d47e5-414">它是以 P/Invoke 基礎結構為建置基礎，但運作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="d47e5-414">It's built on top of the P/Invoke infrastructure, but it works in subtly different ways.</span></span>

<span data-ttu-id="d47e5-415">如需詳細資訊，請參閱 [原生互通性](../standard/native-interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-415">For more information, see [Native interoperability](../standard/native-interop/index.md).</span></span>

### <a name="unsafe-code"></a><span data-ttu-id="d47e5-416">Unsafe 程式碼</span><span class="sxs-lookup"><span data-stu-id="d47e5-416">Unsafe code</span></span>

<span data-ttu-id="d47e5-417">CLR 可讓您根據語言支援透過 `unsafe` 程式碼存取原生記憶體及執行指標算術。</span><span class="sxs-lookup"><span data-stu-id="d47e5-417">Depending on language support, the CLR lets you access native memory and do pointer arithmetic via `unsafe` code.</span></span> <span data-ttu-id="d47e5-418">特定演算法和系統互通性需要這些作業。</span><span class="sxs-lookup"><span data-stu-id="d47e5-418">These operations are needed for certain algorithms and system interoperability.</span></span> <span data-ttu-id="d47e5-419">雖然功能強大，但不建議使用 unsafe 程式碼，除非它必須與系統 Api 互通，或執行最有效率的演算法。</span><span class="sxs-lookup"><span data-stu-id="d47e5-419">Although powerful, use of unsafe code is discouraged unless it's necessary to interoperate with system APIs or implement the most efficient algorithm.</span></span> <span data-ttu-id="d47e5-420">Unsafe 程式碼在不同的環境中執行時可能不盡相同，而且也會失去記憶體回收行程和型別安全的好處。</span><span class="sxs-lookup"><span data-stu-id="d47e5-420">Unsafe code may not execute the same way in different environments and also loses the benefits of a garbage collector and type safety.</span></span> <span data-ttu-id="d47e5-421">建議您盡可能限制和集中使用 Unsafe 程式碼，並徹底測試該程式碼。</span><span class="sxs-lookup"><span data-stu-id="d47e5-421">It's recommended to confine and centralize unsafe code as much as possible and test that code thoroughly.</span></span>

<span data-ttu-id="d47e5-422">如需詳細資訊，請參閱 [Unsafe 程式碼和指標](../csharp/programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e5-422">For more information, see [Unsafe code and pointers](../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d47e5-423">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d47e5-423">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d47e5-424">選擇 .NET 教學課程</span><span class="sxs-lookup"><span data-stu-id="d47e5-424">Choose a .NET tutorial</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="d47e5-425">在您的瀏覽器中嘗試 .NET</span><span class="sxs-lookup"><span data-stu-id="d47e5-425">Try .NET in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)

> [!div class="nextstepaction"]
> [<span data-ttu-id="d47e5-426">流覽 C#</span><span class="sxs-lookup"><span data-stu-id="d47e5-426">Take a tour of C#</span></span>](../csharp/tour-of-csharp/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="d47e5-427">流覽 F#</span><span class="sxs-lookup"><span data-stu-id="d47e5-427">Take a tour of F#</span></span>](../fsharp/tour.md)
