---
title: .NET 簡介和總覽
description: 深入瞭解 .NET 這項免費的開放原始碼開發平臺，可用於建立許多種類的應用程式。
author: tdykstra
ms.date: 11/16/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 0adc348c1fc340fe481d9987cdbe28c6cf8b065d
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938672"
---
# <a name="introduction-to-net"></a><span data-ttu-id="b2375-103">.NET 簡介</span><span class="sxs-lookup"><span data-stu-id="b2375-103">Introduction to .NET</span></span>

<span data-ttu-id="b2375-104">.NET 是免費的開放原始碼開發平臺，可用於建立許多種類的應用程式，例如：</span><span class="sxs-lookup"><span data-stu-id="b2375-104">.NET is a free, open-source development platform for building many kinds of apps, such as:</span></span>

* [<span data-ttu-id="b2375-105">Web 應用程式、web Api 和微服務</span><span class="sxs-lookup"><span data-stu-id="b2375-105">Web apps, web APIs, and microservices</span></span>](/aspnet/core/introduction-to-aspnet-core#recommended-learning-path)
* [<span data-ttu-id="b2375-106">雲端中的無伺服器函式</span><span class="sxs-lookup"><span data-stu-id="b2375-106">Serverless functions in the cloud</span></span>](/azure/azure-functions/functions-create-first-function-vs-code?pivots=programming-language-csharp)
* [<span data-ttu-id="b2375-107">雲端原生應用程式</span><span class="sxs-lookup"><span data-stu-id="b2375-107">Cloud native apps</span></span>](../architecture/cloud-native/index.md)
* [<span data-ttu-id="b2375-108">行動應用程式</span><span class="sxs-lookup"><span data-stu-id="b2375-108">Mobile apps</span></span>](https://dotnet.microsoft.com/learn/xamarin/hello-world-tutorial/intro)
* <span data-ttu-id="b2375-109">傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="b2375-109">Desktop apps</span></span>
  * [<span data-ttu-id="b2375-110">Windows WPF</span><span class="sxs-lookup"><span data-stu-id="b2375-110">Windows WPF</span></span>](/dotnet/desktop/wpf/)
  * [<span data-ttu-id="b2375-111">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2375-111">Windows Forms</span></span>](/dotnet/desktop/winforms/)
  * [<span data-ttu-id="b2375-112">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="b2375-112">Universal Windows Platform (UWP)</span></span>](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* [<span data-ttu-id="b2375-113">遊戲</span><span class="sxs-lookup"><span data-stu-id="b2375-113">Games</span></span>](https://dotnet.microsoft.com/apps/games)
* [<span data-ttu-id="b2375-114">物聯網 (IoT)</span><span class="sxs-lookup"><span data-stu-id="b2375-114">Internet of Things (IoT)</span></span>](/dotnet/iot)
* [<span data-ttu-id="b2375-115">機器學習服務</span><span class="sxs-lookup"><span data-stu-id="b2375-115">Machine learning</span></span>](../machine-learning/index.yml)
* [<span data-ttu-id="b2375-116">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b2375-116">Console apps</span></span>](tutorials/with-visual-studio-code.md)
* [<span data-ttu-id="b2375-117">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="b2375-117">Windows services</span></span>](/aspnet/core/host-and-deploy/windows-service)

<span data-ttu-id="b2375-118">使用 [類別庫](../standard/class-libraries.md)，在不同的應用程式和應用程式類型之間共用功能。</span><span class="sxs-lookup"><span data-stu-id="b2375-118">Share functionality among different apps and app types by using [class libraries](../standard/class-libraries.md).</span></span>

<span data-ttu-id="b2375-119">使用 .NET 時，無論您要建立哪種類型的應用程式，程式碼和專案檔的外觀和操作都會相同。</span><span class="sxs-lookup"><span data-stu-id="b2375-119">With .NET, your code and project files look and feel the same no matter which type of app you're building.</span></span> <span data-ttu-id="b2375-120">您可以使用每個應用程式存取相同的執行時間、API 和語言功能。</span><span class="sxs-lookup"><span data-stu-id="b2375-120">You have access to the same runtime, API, and language capabilities with each app.</span></span>

## <a name="cross-platform"></a><span data-ttu-id="b2375-121">跨平台</span><span class="sxs-lookup"><span data-stu-id="b2375-121">Cross platform</span></span>

<span data-ttu-id="b2375-122">您可以為許多作業系統建立 .NET 應用程式，包括：</span><span class="sxs-lookup"><span data-stu-id="b2375-122">You can create .NET apps for many operating systems, including:</span></span>

* <span data-ttu-id="b2375-123">Windows</span><span class="sxs-lookup"><span data-stu-id="b2375-123">Windows</span></span>
* <span data-ttu-id="b2375-124">macOS</span><span class="sxs-lookup"><span data-stu-id="b2375-124">macOS</span></span>
* <span data-ttu-id="b2375-125">Linux</span><span class="sxs-lookup"><span data-stu-id="b2375-125">Linux</span></span>
* <span data-ttu-id="b2375-126">Android</span><span class="sxs-lookup"><span data-stu-id="b2375-126">Android</span></span>
* <span data-ttu-id="b2375-127">iOS</span><span class="sxs-lookup"><span data-stu-id="b2375-127">iOS</span></span>
* <span data-ttu-id="b2375-128">tvOS</span><span class="sxs-lookup"><span data-stu-id="b2375-128">tvOS</span></span>
* <span data-ttu-id="b2375-129">watchOS</span><span class="sxs-lookup"><span data-stu-id="b2375-129">watchOS</span></span>

<span data-ttu-id="b2375-130">支援的處理器架構包括：</span><span class="sxs-lookup"><span data-stu-id="b2375-130">Supported processor architectures include:</span></span>

* <span data-ttu-id="b2375-131">x64</span><span class="sxs-lookup"><span data-stu-id="b2375-131">x64</span></span>
* <span data-ttu-id="b2375-132">x86</span><span class="sxs-lookup"><span data-stu-id="b2375-132">x86</span></span>
* <span data-ttu-id="b2375-133">ARM32</span><span class="sxs-lookup"><span data-stu-id="b2375-133">ARM32</span></span>
* <span data-ttu-id="b2375-134">ARM64</span><span class="sxs-lookup"><span data-stu-id="b2375-134">ARM64</span></span>

<span data-ttu-id="b2375-135">.NET 可讓您使用平臺特定的功能，例如作業系統 Api。</span><span class="sxs-lookup"><span data-stu-id="b2375-135">.NET lets you use platform-specific capabilities, such as operating system APIs.</span></span> <span data-ttu-id="b2375-136">範例包括 Windows 上的 Windows Forms 和 WPF，以及 Xamarin 的每個行動平臺的原生系結。</span><span class="sxs-lookup"><span data-stu-id="b2375-136">Examples are Windows Forms and WPF on Windows and the native bindings to each mobile platform from Xamarin.</span></span>

<span data-ttu-id="b2375-137">如需詳細資訊，請參閱 [支援的 OS 生命週期原則](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md) 和 [.net RID 目錄](rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-137">For more information, see [Supported OS lifecycle policy](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md) and [.NET RID Catalog](rid-catalog.md).</span></span>

## <a name="open-source"></a><span data-ttu-id="b2375-138">開放原始碼</span><span class="sxs-lookup"><span data-stu-id="b2375-138">Open source</span></span>

<span data-ttu-id="b2375-139">.NET 是開放原始碼，使用 [MIT 和 Apache 2 授權](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)。</span><span class="sxs-lookup"><span data-stu-id="b2375-139">.NET is open source, using [MIT and Apache 2 licenses](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT).</span></span> <span data-ttu-id="b2375-140">.NET 是 [.Net Foundation](https://dotnetfoundation.org/)的專案。</span><span class="sxs-lookup"><span data-stu-id="b2375-140">.NET is a project of the [.NET Foundation](https://dotnetfoundation.org/).</span></span>

<span data-ttu-id="b2375-141">如需詳細資訊，請參閱 [GitHub.com 上的專案存放庫清單](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-141">For more information, see the [list of project repositories on GitHub.com](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="b2375-142">支援</span><span class="sxs-lookup"><span data-stu-id="b2375-142">Support</span></span>

<span data-ttu-id="b2375-143">Microsoft 在 Windows、macOS 和 Linux 上支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="b2375-143">.NET is supported by Microsoft on Windows, macOS, and Linux.</span></span> <span data-ttu-id="b2375-144">它會在每個月的第二個星期二定期更新安全性和品質。</span><span class="sxs-lookup"><span data-stu-id="b2375-144">It's updated regularly for security and quality, on the second Tuesday of each month.</span></span>

<span data-ttu-id="b2375-145">Microsoft 的 .NET 二進位散發套件是在 Azure 中 Microsoft 維護的伺服器上建立和測試，並遵循 Microsoft 工程和安全性作法。</span><span class="sxs-lookup"><span data-stu-id="b2375-145">.NET binary distributions from Microsoft are built and tested on Microsoft-maintained servers in Azure and follow Microsoft engineering and security practices.</span></span>

<span data-ttu-id="b2375-146">[Red Hat 支援](https://developers.redhat.com/topics/dotnet/) Red Hat Enterprise Linux 上的 .NET (RHEL) 。</span><span class="sxs-lookup"><span data-stu-id="b2375-146">[Red Hat supports .NET](https://developers.redhat.com/topics/dotnet/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="b2375-147">Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。</span><span class="sxs-lookup"><span data-stu-id="b2375-147">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

<span data-ttu-id="b2375-148">[Tizen 支援](https://developer.tizen.org/development/training/.net-application) Tizen 平臺上的 .net。</span><span class="sxs-lookup"><span data-stu-id="b2375-148">[Tizen supports .NET](https://developer.tizen.org/development/training/.net-application) on Tizen platforms.</span></span>

<span data-ttu-id="b2375-149">如需詳細資訊，請參閱 [.Net Core 和 .net 5 的版本和支援](releases-and-support.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-149">For more information, see [Releases and support for .NET Core and .NET 5](releases-and-support.md).</span></span>

## <a name="tools-and-productivity"></a><span data-ttu-id="b2375-150">工具和生產力</span><span class="sxs-lookup"><span data-stu-id="b2375-150">Tools and productivity</span></span>

<span data-ttu-id="b2375-151">.NET 提供您選擇的語言、整合式開發環境 (Ide) 和其他工具。</span><span class="sxs-lookup"><span data-stu-id="b2375-151">.NET gives you a choice of languages, integrated development environments (IDEs), and other tools.</span></span>

### <a name="programming-languages"></a><span data-ttu-id="b2375-152">程式語言</span><span class="sxs-lookup"><span data-stu-id="b2375-152">Programming languages</span></span>

<span data-ttu-id="b2375-153">.NET 支援三種程式設計語言：</span><span class="sxs-lookup"><span data-stu-id="b2375-153">.NET supports three programming languages:</span></span>

* [<span data-ttu-id="b2375-154">C#</span><span class="sxs-lookup"><span data-stu-id="b2375-154">C#</span></span>](../csharp/index.yml)

  <span data-ttu-id="b2375-155">C # (發音為「看清晰的」 ) 是新式、物件導向且型別安全的程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="b2375-155">C# (pronounced "See Sharp") is a modern, object-oriented, and type-safe programming language.</span></span> <span data-ttu-id="b2375-156">C# 源自於是 C 系列語言，使用 C、C++、Java 和 JavaScript 的程式設計人員會立即感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="b2375-156">C# has its roots in the C family of languages and will be immediately familiar to C, C++, Java, and JavaScript programmers.</span></span>

* [<span data-ttu-id="b2375-157">F#</span><span class="sxs-lookup"><span data-stu-id="b2375-157">F#</span></span>](../fsharp/index.yml)

  <span data-ttu-id="b2375-158">F # 語言支援功能性、物件導向和命令式程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="b2375-158">The F# language supports functional, object-oriented, and imperative programming models.</span></span>

* [<span data-ttu-id="b2375-159">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2375-159">Visual Basic</span></span>](../visual-basic/index.yml)

  <span data-ttu-id="b2375-160">在 .NET 語言中，Visual Basic 的語法是最接近一般人類語言的語法，可讓您更輕鬆地學習。</span><span class="sxs-lookup"><span data-stu-id="b2375-160">Among the .NET languages, the syntax of Visual Basic is the closest to ordinary human language, which can make it easier to learn.</span></span> <span data-ttu-id="b2375-161">不同于 c # 和 F #，Microsoft 正積極開發新功能，Visual Basic 的語言是穩定的。</span><span class="sxs-lookup"><span data-stu-id="b2375-161">Unlike C# and F#, for which Microsoft is actively developing new features, the Visual Basic language is stable.</span></span> <span data-ttu-id="b2375-162">Web 應用程式不支援 Visual Basic，但 web Api 支援此功能。</span><span class="sxs-lookup"><span data-stu-id="b2375-162">Visual Basic isn't supported for web apps, but it is supported for web APIs.</span></span>

<span data-ttu-id="b2375-163">以下是 .NET 語言支援的一些功能：</span><span class="sxs-lookup"><span data-stu-id="b2375-163">Here are some of the capabilities that .NET languages support:</span></span>

* [<span data-ttu-id="b2375-164">型別安全</span><span class="sxs-lookup"><span data-stu-id="b2375-164">Type safety</span></span>](../standard/base-types/common-type-system.md)
* <span data-ttu-id="b2375-165">型別推斷- [c #](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations)、 [F #](../fsharp/language-reference/type-inference.md)、 [Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="b2375-165">Type inference - [C#](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations), [F#](../fsharp/language-reference/type-inference.md), [Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>
* [<span data-ttu-id="b2375-166">泛型類型</span><span class="sxs-lookup"><span data-stu-id="b2375-166">Generic types</span></span>](../standard/generics.md)
* [<span data-ttu-id="b2375-167">委派</span><span class="sxs-lookup"><span data-stu-id="b2375-167">Delegates</span></span>](../standard/delegates-lambdas.md)
* [<span data-ttu-id="b2375-168">Lambda</span><span class="sxs-lookup"><span data-stu-id="b2375-168">Lambdas</span></span>](../standard/delegates-lambdas.md)
* [<span data-ttu-id="b2375-169">事件</span><span class="sxs-lookup"><span data-stu-id="b2375-169">Events</span></span>](../standard/events/index.md)
* [<span data-ttu-id="b2375-170">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b2375-170">Exceptions</span></span>](../standard/exceptions/index.md)
* [<span data-ttu-id="b2375-171">屬性</span><span class="sxs-lookup"><span data-stu-id="b2375-171">Attributes</span></span>](../standard/attributes/index.md)
* [<span data-ttu-id="b2375-172">非同步程式碼</span><span class="sxs-lookup"><span data-stu-id="b2375-172">Asynchronous code</span></span>](../standard/async.md)
* [<span data-ttu-id="b2375-173">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="b2375-173">Parallel programming</span></span>](../standard/parallel-programming/index.md)
* [<span data-ttu-id="b2375-174">程式碼分析器</span><span class="sxs-lookup"><span data-stu-id="b2375-174">Code analyzers</span></span>](../fundamentals/code-analysis/overview.md)

### <a name="ides"></a><span data-ttu-id="b2375-175">IDE</span><span class="sxs-lookup"><span data-stu-id="b2375-175">IDEs</span></span>

<span data-ttu-id="b2375-176">適用于 .NET 的整合式開發環境包括：</span><span class="sxs-lookup"><span data-stu-id="b2375-176">The integrated development environments for .NET include:</span></span>

* [<span data-ttu-id="b2375-177">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2375-177">Visual Studio</span></span>](https://visualstudio.microsoft.com/vs/)

  <span data-ttu-id="b2375-178">只能在 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="b2375-178">Runs on Windows only.</span></span> <span data-ttu-id="b2375-179">具有廣泛的內建功能，其設計目的是使用 .NET。</span><span class="sxs-lookup"><span data-stu-id="b2375-179">Has extensive built-in functionality designed to work with .NET.</span></span> <span data-ttu-id="b2375-180">所有學生、開放原始碼參與者及個人均可免費取得此社區版。</span><span class="sxs-lookup"><span data-stu-id="b2375-180">The Community edition is free for students, open-source contributors, and individuals.</span></span>

* [<span data-ttu-id="b2375-181">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b2375-181">Visual Studio Code</span></span>](https://code.visualstudio.com/)

  <span data-ttu-id="b2375-182">在 Windows、macOS 和 Linux 上執行。</span><span class="sxs-lookup"><span data-stu-id="b2375-182">Runs on Windows, macOS, and Linux.</span></span> <span data-ttu-id="b2375-183">免費且開放的原始碼。</span><span class="sxs-lookup"><span data-stu-id="b2375-183">Free and open source.</span></span> <span data-ttu-id="b2375-184">擴充功能可搭配 .NET 語言使用。</span><span class="sxs-lookup"><span data-stu-id="b2375-184">Extensions are available for working with .NET languages.</span></span>

* [<span data-ttu-id="b2375-185">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="b2375-185">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/)

  <span data-ttu-id="b2375-186">只會在 macOS 上執行。</span><span class="sxs-lookup"><span data-stu-id="b2375-186">Runs on macOS only.</span></span> <span data-ttu-id="b2375-187">適用于開發適用于 iOS、Android 和 web 的 .NET 應用程式和遊戲。</span><span class="sxs-lookup"><span data-stu-id="b2375-187">For developing .NET apps and games for iOS, Android, and web.</span></span>

* [<span data-ttu-id="b2375-188">GitHub Codespaces</span><span class="sxs-lookup"><span data-stu-id="b2375-188">GitHub Codespaces</span></span>](https://github.com/features/codespaces)

  <span data-ttu-id="b2375-189">線上 Visual Studio Code 環境，目前為搶鮮版（Beta）。</span><span class="sxs-lookup"><span data-stu-id="b2375-189">An online Visual Studio Code environment, currently in beta.</span></span>

### <a name="sdk-and-runtimes"></a><span data-ttu-id="b2375-190">SDK 和執行時間</span><span class="sxs-lookup"><span data-stu-id="b2375-190">SDK and runtimes</span></span>

<span data-ttu-id="b2375-191">[.NET SDK](sdk.md)是用來開發及執行 .net 應用程式的一組程式庫和工具。</span><span class="sxs-lookup"><span data-stu-id="b2375-191">The [.NET SDK](sdk.md) is a set of libraries and tools for developing and running .NET applications.</span></span>

<span data-ttu-id="b2375-192">當您 [下載 .net](https://dotnet.microsoft.com/download/dotnet-core/)時，您可以選擇 SDK 或 *運行* 時間，例如 .net 執行時間或 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-192">When you [download .NET](https://dotnet.microsoft.com/download/dotnet-core/), you can choose the SDK or a *runtime*, such as the .NET runtime or the ASP.NET Core runtime.</span></span> <span data-ttu-id="b2375-193">在您想要準備執行 .NET 應用程式的電腦上安裝執行時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-193">Install a runtime on a machine that you want to prepare for running .NET apps.</span></span> <span data-ttu-id="b2375-194">在您要用於開發的電腦上安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="b2375-194">Install the SDK on a machine that you want to use for development.</span></span> <span data-ttu-id="b2375-195">當您下載 SDK 時，您會自動取得其執行時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-195">When you download the SDK, you automatically get the runtimes with it.</span></span>

<span data-ttu-id="b2375-196">SDK 下載包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="b2375-196">The SDK download includes the following components:</span></span>

* <span data-ttu-id="b2375-197">[.NET CLI](tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-197">The [.NET CLI](tools/index.md).</span></span> <span data-ttu-id="b2375-198">您可以用於本機開發和連續整合腳本的命令列工具。</span><span class="sxs-lookup"><span data-stu-id="b2375-198">Command-line tools that you can use for local development and continuous integration scripts.</span></span>
* <span data-ttu-id="b2375-199">`dotnet`[驅動程式](tools/index.md#driver)。</span><span class="sxs-lookup"><span data-stu-id="b2375-199">The `dotnet` [driver](tools/index.md#driver).</span></span> <span data-ttu-id="b2375-200">執行與架構相依的應用程式的 CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="b2375-200">A CLI command that runs framework-dependent apps.</span></span>
* <span data-ttu-id="b2375-201">[Roslyn](https://github.com/dotnet/roslyn)和[F #](https://github.com/microsoft/visualfsharp)程式設計語言編譯器。</span><span class="sxs-lookup"><span data-stu-id="b2375-201">The [Roslyn](https://github.com/dotnet/roslyn) and [F#](https://github.com/microsoft/visualfsharp) programming language compilers.</span></span>
* <span data-ttu-id="b2375-202">[MSBuild](/visualstudio/msbuild/msbuild)組建引擎。</span><span class="sxs-lookup"><span data-stu-id="b2375-202">The [MSBuild](/visualstudio/msbuild/msbuild) build engine.</span></span>
* <span data-ttu-id="b2375-203">[.Net 運行](#clr)時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-203">The [.NET runtime](#clr).</span></span> <span data-ttu-id="b2375-204">提供類型系統、元件載入、垃圾收集行程、原生 interop 及其他基本服務。</span><span class="sxs-lookup"><span data-stu-id="b2375-204">Provides a type system, assembly loading, a garbage collector, native interop, and other basic services.</span></span>
* <span data-ttu-id="b2375-205">[運行](#runtime-libraries)時間程式庫。</span><span class="sxs-lookup"><span data-stu-id="b2375-205">[Runtime libraries](#runtime-libraries).</span></span> <span data-ttu-id="b2375-206">提供基本資料類型和基本公用程式。</span><span class="sxs-lookup"><span data-stu-id="b2375-206">Provides primitive data types and fundamental utilities.</span></span>
* <span data-ttu-id="b2375-207">ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-207">The ASP.NET Core runtime.</span></span> <span data-ttu-id="b2375-208">為網際網路連線的應用程式（例如 web 應用程式、IoT 應用程式和行動後端）提供基本的服務。</span><span class="sxs-lookup"><span data-stu-id="b2375-208">Provides basic services for internet-connected apps, such as web apps, IoT apps, and mobile backends.</span></span>
* <span data-ttu-id="b2375-209">桌面執行時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-209">The desktop runtime.</span></span> <span data-ttu-id="b2375-210">提供 Windows 傳統型應用程式的基本服務，包括 Windows Forms 和 WPF。</span><span class="sxs-lookup"><span data-stu-id="b2375-210">Provides basic services for Windows desktop apps, including Windows Forms and WPF.</span></span>

<span data-ttu-id="b2375-211">執行時間下載包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="b2375-211">The runtime download includes the following components:</span></span>

* <span data-ttu-id="b2375-212">（選擇性）桌面或 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-212">Optionally, the desktop or ASP.NET Core runtime.</span></span>
* <span data-ttu-id="b2375-213">[.Net 運行](#clr)時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-213">The [.NET runtime](#clr).</span></span> <span data-ttu-id="b2375-214">提供類型系統、元件載入、垃圾收集行程、原生 interop 及其他基本服務。</span><span class="sxs-lookup"><span data-stu-id="b2375-214">Provides a type system, assembly loading, a garbage collector, native interop, and other basic services.</span></span>
* <span data-ttu-id="b2375-215">[運行](#runtime-libraries)時間程式庫。</span><span class="sxs-lookup"><span data-stu-id="b2375-215">[Runtime libraries](#runtime-libraries).</span></span> <span data-ttu-id="b2375-216">提供基本資料類型和基本公用程式。</span><span class="sxs-lookup"><span data-stu-id="b2375-216">Provides primitive data types and fundamental utilities.</span></span>
* <span data-ttu-id="b2375-217">`dotnet`[驅動程式](tools/index.md#driver)。</span><span class="sxs-lookup"><span data-stu-id="b2375-217">The `dotnet` [driver](tools/index.md#driver).</span></span> <span data-ttu-id="b2375-218">執行與架構相依的應用程式的 CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="b2375-218">A CLI command that runs framework-dependent apps.</span></span>

<span data-ttu-id="b2375-219">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="b2375-219">For more information, see the following resources:</span></span>

* [<span data-ttu-id="b2375-220">.NET SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="b2375-220">.NET SDK overview</span></span>](sdk.md)
* [<span data-ttu-id="b2375-221">.NET CLI 總覽</span><span class="sxs-lookup"><span data-stu-id="b2375-221">.NET CLI overview</span></span>](tools/index.md)
* [<span data-ttu-id="b2375-222">dotnet 命令</span><span class="sxs-lookup"><span data-stu-id="b2375-222">dotnet command</span></span>](tools/dotnet.md)

### <a name="project-system-and-msbuild"></a><span data-ttu-id="b2375-223">專案系統和 MSBuild</span><span class="sxs-lookup"><span data-stu-id="b2375-223">Project system and MSBuild</span></span>

<span data-ttu-id="b2375-224">.NET 應用程式是使用 [MSBuild](/visualstudio/msbuild/msbuild)從原始程式碼建立的。</span><span class="sxs-lookup"><span data-stu-id="b2375-224">A .NET app is built from source code by using [MSBuild](/visualstudio/msbuild/msbuild).</span></span> <span data-ttu-id="b2375-225">專案檔 (*.csproj*、 *>.fsproj* 或 *. vbproj*) 指定負責編譯、封裝和發佈程式碼的 [目標](/visualstudio/msbuild/msbuild-targets)[和相關聯](/visualstudio/msbuild/msbuild-tasks)工作。</span><span class="sxs-lookup"><span data-stu-id="b2375-225">A project file (*.csproj*, *.fsproj*, or *.vbproj*) specifies [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="b2375-226">有 SDK 識別碼可參考目標和工作的標準集合。</span><span class="sxs-lookup"><span data-stu-id="b2375-226">There are SDK identifiers that refer to standard collections of targets and tasks.</span></span> <span data-ttu-id="b2375-227">使用這些識別碼有助於讓專案檔變小且容易使用。</span><span class="sxs-lookup"><span data-stu-id="b2375-227">The use of these identifiers helps keep project files small and easy to work with.</span></span> <span data-ttu-id="b2375-228">例如，以下是主控台應用程式的專案檔：</span><span class="sxs-lookup"><span data-stu-id="b2375-228">For example, here is a project file for a console app:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b2375-229">以下是 web 應用程式的其中一個：</span><span class="sxs-lookup"><span data-stu-id="b2375-229">And here's one for a web app:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b2375-230">在這些範例中， `Sdk` 元素的屬性 `Project` 會指定一組 MSBuild 目標和工作，以建立專案。</span><span class="sxs-lookup"><span data-stu-id="b2375-230">In these examples, the `Sdk` attribute of the `Project` element specifies a set of MSBuild targets and tasks that build the project.</span></span>  <span data-ttu-id="b2375-231">`TargetFramework`元素會指定應用程式所相依的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="b2375-231">The `TargetFramework` element specifies the .NET version that the app depends on.</span></span> <span data-ttu-id="b2375-232">您可以編輯專案檔，以加入專案特定的其他目標和工作。</span><span class="sxs-lookup"><span data-stu-id="b2375-232">You can edit the project file to add additional targets and tasks specific to the project.</span></span>

<span data-ttu-id="b2375-233">如需詳細資訊，請參閱 [.net 專案 SDK 總覽](project-sdk/overview.md) 和 [目標 framework](../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-233">For more information, see [.NET project SDK overview](project-sdk/overview.md) and [Target frameworks](../standard/frameworks.md).</span></span>

### <a name="cicd"></a><span data-ttu-id="b2375-234">CI/CD</span><span class="sxs-lookup"><span data-stu-id="b2375-234">CI/CD</span></span>

<span data-ttu-id="b2375-235">MSBuild 和 .NET CLI 可以搭配各種持續整合工具和環境使用，例如：</span><span class="sxs-lookup"><span data-stu-id="b2375-235">MSBuild and the .NET CLI can be used with various continuous integration tools and environments, such as:</span></span>

* [<span data-ttu-id="b2375-236">GitHub 動作</span><span class="sxs-lookup"><span data-stu-id="b2375-236">GitHub Actions</span></span>](https://github.com/features/actions)
* [<span data-ttu-id="b2375-237">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="b2375-237">Azure DevOps</span></span>](/azure/devops/user-guide/what-is-azure-devops)
* [<span data-ttu-id="b2375-238">蛋糕</span><span class="sxs-lookup"><span data-stu-id="b2375-238">CAKE</span></span>](https://cakebuild.net/)
* [<span data-ttu-id="b2375-239">假</span><span class="sxs-lookup"><span data-stu-id="b2375-239">FAKE</span></span>](https://fake.build/)

<span data-ttu-id="b2375-240">如需詳細資訊，請參閱 [在持續整合 (CI 中使用 .NET SDK 和工具) ](tools/using-ci-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="b2375-240">For more information, see [Using .NET SDK and tools in Continuous Integration (CI)](tools/using-ci-with-cli.md)</span></span>

### <a name="nuget"></a><span data-ttu-id="b2375-241">NuGet</span><span class="sxs-lookup"><span data-stu-id="b2375-241">NuGet</span></span>

<span data-ttu-id="b2375-242">[NuGet](/nuget/what-is-nuget) 是專為 .net 設計的開放原始碼套件管理員。</span><span class="sxs-lookup"><span data-stu-id="b2375-242">[NuGet](/nuget/what-is-nuget) is an open-source package manager designed for .NET.</span></span> <span data-ttu-id="b2375-243">NuGet 套件是副檔名為的 *.zip* 檔案，其中 `.nupkg` 包含已編譯的程式碼 (dll) 、與該程式碼相關的其他檔案，以及包含套件版本號碼等資訊的描述性資訊清單。</span><span class="sxs-lookup"><span data-stu-id="b2375-243">A NuGet package is a *.zip* file with the `.nupkg` extension that contains compiled code (DLLs), other files related to that code, and a descriptive manifest that includes information like the package's version number.</span></span> <span data-ttu-id="b2375-244">具有程式碼的開發人員可共用建立封裝，並將其發佈至 [nuget.org](https://nuget.org) 或私用主機。</span><span class="sxs-lookup"><span data-stu-id="b2375-244">Developers with code to share create packages and publish them to [nuget.org](https://nuget.org) or a private host.</span></span> <span data-ttu-id="b2375-245">如果開發人員想要使用共用程式碼，請將封裝新增至其專案，然後在其專案程式碼中呼叫封裝所公開的 API。</span><span class="sxs-lookup"><span data-stu-id="b2375-245">Developers who want to use shared code add a package to their project and can then call the API exposed by the package in their project code.</span></span>

<span data-ttu-id="b2375-246">如需詳細資訊，請參閱 [NuGet 檔](/nuget/)集。</span><span class="sxs-lookup"><span data-stu-id="b2375-246">For more information, see [NuGet documentation](/nuget/).</span></span>

### <a name="net-interactive"></a><span data-ttu-id="b2375-247">.NET 互動</span><span class="sxs-lookup"><span data-stu-id="b2375-247">.NET Interactive</span></span>

<span data-ttu-id="b2375-248">.NET Interactive 是一組 CLI 工具和 Api，可讓使用者在 web、markdown 和筆記本之間建立互動式體驗。</span><span class="sxs-lookup"><span data-stu-id="b2375-248">.NET Interactive is a group of CLI tools and APIs that enable users to create interactive experiences across the web, markdown, and notebooks.</span></span>

<span data-ttu-id="b2375-249">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="b2375-249">For more information, see the following resources:</span></span>

* [<span data-ttu-id="b2375-250">.NET In-Browser 教學課程</span><span class="sxs-lookup"><span data-stu-id="b2375-250">.NET In-Browser Tutorial</span></span>](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1)
* [<span data-ttu-id="b2375-251">在您的電腦上搭配 Jupyter 使用 .NET 筆記本</span><span class="sxs-lookup"><span data-stu-id="b2375-251">Using .NET notebooks with Jupyter on your machine</span></span>](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)
* [<span data-ttu-id="b2375-252">.NET 互動式檔</span><span class="sxs-lookup"><span data-stu-id="b2375-252">.NET Interactive documentation</span></span>](https://github.com/dotnet/interactive/blob/main/docs/README.md)

## <a name="execution-models"></a><span data-ttu-id="b2375-253">執行模型</span><span class="sxs-lookup"><span data-stu-id="b2375-253">Execution models</span></span>

<span data-ttu-id="b2375-254">.NET 應用程式會在執行時間環境中執行 [managed 程式碼](../standard/managed-code.md) ，此環境稱為 Common Language RUNTIME (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="b2375-254">.NET apps run [managed code](../standard/managed-code.md) in a runtime environment known as the Common Language Runtime (CLR).</span></span>

### <a name="clr"></a><span data-ttu-id="b2375-255">CLR</span><span class="sxs-lookup"><span data-stu-id="b2375-255">CLR</span></span>

<span data-ttu-id="b2375-256">.NET [CLR](../standard/clr.md) 是一種跨平臺執行時間，包含對 Windows、MacOS 和 Linux 的支援。</span><span class="sxs-lookup"><span data-stu-id="b2375-256">The .NET [CLR](../standard/clr.md) is a cross-platform runtime that includes support for Windows, macOS, and Linux.</span></span> <span data-ttu-id="b2375-257">CLR 會處理記憶體配置和管理。</span><span class="sxs-lookup"><span data-stu-id="b2375-257">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="b2375-258">CLR 也是虛擬機器，不僅會執行應用程式，也會使用及時 (JIT) 編譯器來產生和編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="b2375-258">The CLR is also a virtual machine that not only executes apps but also generates and compiles code using a just-in-time (JIT) compiler.</span></span>

<span data-ttu-id="b2375-259">如需詳細資訊，請參閱 [Common Language Runtime (CLR) 總覽](../standard/clr.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-259">For more information, see [Common Language Runtime (CLR) overview](../standard/clr.md).</span></span>

### <a name="jit-compiler-and-il"></a><span data-ttu-id="b2375-260">JIT 編譯程式和 IL</span><span class="sxs-lookup"><span data-stu-id="b2375-260">JIT compiler and IL</span></span>

<span data-ttu-id="b2375-261">較高階的 .NET 語言 (例如 C#) 可向下編譯成硬體無從驗證的指令集，稱為中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="b2375-261">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="b2375-262">當應用程式執行時，JIT 編譯程式會將 IL 轉譯為處理器瞭解的機器碼。</span><span class="sxs-lookup"><span data-stu-id="b2375-262">When an app runs, the JIT compiler translates IL to machine code that the processor understands.</span></span> <span data-ttu-id="b2375-263">JIT 編譯發生在程式碼即將執行的同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="b2375-263">JIT compilation happens on the same machine that the code is going to run on.</span></span>

<span data-ttu-id="b2375-264">由於 JIT 編譯是在應用程式執行期間發生，編譯時間是執行時間的一部分。</span><span class="sxs-lookup"><span data-stu-id="b2375-264">Since JIT compilation occurs during execution of the application, the compilation time is part of the run time.</span></span> <span data-ttu-id="b2375-265">因此，JIT 編譯程式必須將花費在優化程式碼的時間與產生的程式碼所能產生的節省時間進行平衡。</span><span class="sxs-lookup"><span data-stu-id="b2375-265">Therefore, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="b2375-266">但是 JIT 編譯程式知道實際的硬體，而且可以讓開發人員不需要為不同的平臺送出不同的執行方式。</span><span class="sxs-lookup"><span data-stu-id="b2375-266">But a JIT compiler knows the actual hardware and can free developers from having to ship different implementations for different platforms.</span></span>

<span data-ttu-id="b2375-267">.NET JIT 編譯程式可以進行階層式 *編譯*，這表示它可以在執行時間重新編譯個別方法。</span><span class="sxs-lookup"><span data-stu-id="b2375-267">The .NET JIT compiler can do *tiered compilation*, which means it can recompile individual methods at run time.</span></span> <span data-ttu-id="b2375-268">這項功能可讓它快速編譯，同時仍能針對常用的方法產生高度調整的程式碼版本。</span><span class="sxs-lookup"><span data-stu-id="b2375-268">This feature lets it compile quickly while still being able to produce a highly tuned version of the code for frequently used methods.</span></span>

<span data-ttu-id="b2375-269">如需詳細資訊，請參閱 [Managed 執行](../standard/managed-execution-process.md) 程式和階層式 [編譯](whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="b2375-269">For more information, see [Managed execution process](../standard/managed-execution-process.md) and [Tiered compilation](whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>

### <a name="aot-compiler"></a><span data-ttu-id="b2375-270">AOT 編譯器</span><span class="sxs-lookup"><span data-stu-id="b2375-270">AOT compiler</span></span>

<span data-ttu-id="b2375-271">大部分 .NET 工作負載的預設體驗都是 JIT 編譯程式，但 .NET 提供兩種預先 (AOT) 編譯的形式：</span><span class="sxs-lookup"><span data-stu-id="b2375-271">The default experience for most .NET workloads is the JIT compiler, but .NET offers two forms of ahead-of-time (AOT) compilation:</span></span>

* <span data-ttu-id="b2375-272">某些案例需要 100% AOT 編譯。</span><span class="sxs-lookup"><span data-stu-id="b2375-272">Some scenarios require 100% AOT compilation.</span></span> <span data-ttu-id="b2375-273">例如 [iOS](/xamarin/ios/)。</span><span class="sxs-lookup"><span data-stu-id="b2375-273">An example is [iOS](/xamarin/ios/).</span></span>
* <span data-ttu-id="b2375-274">在其他案例中，大部分的應用程式程式碼都是由 AOT 編譯，但有些則是 JIT 編譯的。</span><span class="sxs-lookup"><span data-stu-id="b2375-274">In other scenarios, most of an app's code is AOT-compiled but some is JIT-compiled.</span></span> <span data-ttu-id="b2375-275">某些程式碼模式不適用於 AOT (例如泛型) 。</span><span class="sxs-lookup"><span data-stu-id="b2375-275">Some code patterns aren't friendly to AOT (like generics).</span></span> <span data-ttu-id="b2375-276">這種形式的 AOT 編譯範例是可 [立即執行](whats-new/dotnet-core-3-0.md#readytorun-images) 的發行選項。</span><span class="sxs-lookup"><span data-stu-id="b2375-276">An example of this form of AOT compilation is the [ready-to-run](whats-new/dotnet-core-3-0.md#readytorun-images) publish option.</span></span> <span data-ttu-id="b2375-277">這種形式的 AOT 可提供 AOT 的優點，而不會有其缺點。</span><span class="sxs-lookup"><span data-stu-id="b2375-277">This form of AOT offers the benefits of AOT without its drawbacks.</span></span>

### <a name="automatic-memory-management"></a><span data-ttu-id="b2375-278">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="b2375-278">Automatic memory management</span></span>

<span data-ttu-id="b2375-279">*垃圾收集* 行程 (GC) 管理應用程式的記憶體配置和釋放。</span><span class="sxs-lookup"><span data-stu-id="b2375-279">The *garbage collector* (GC) manages the allocation and release of memory for applications.</span></span> <span data-ttu-id="b2375-280">每當您的程式碼建立新的物件時，CLR 就會從 [managed 堆積](../standard/garbage-collection/fundamentals.md#the-managed-heap)設定物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b2375-280">Each time your code creates a new object, the CLR allocates memory for the object from the [managed heap](../standard/garbage-collection/fundamentals.md#the-managed-heap).</span></span> <span data-ttu-id="b2375-281">只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。</span><span class="sxs-lookup"><span data-stu-id="b2375-281">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="b2375-282">如果沒有足夠的可用位址空間，GC 就會檢查 managed 堆積中，應用程式不再使用的物件。</span><span class="sxs-lookup"><span data-stu-id="b2375-282">When not enough free address space remains, the GC checks for objects in the managed heap that are no longer being used by the application.</span></span> <span data-ttu-id="b2375-283">然後回收該記憶體。</span><span class="sxs-lookup"><span data-stu-id="b2375-283">It then reclaims that memory.</span></span>

<span data-ttu-id="b2375-284">GC 是可協助確保 *記憶體安全* 的其中一個 CLR 服務。</span><span class="sxs-lookup"><span data-stu-id="b2375-284">The GC is one of the CLR services that help ensure *memory safety*.</span></span> <span data-ttu-id="b2375-285">如果程式只存取已配置的記憶體，就是記憶體安全。</span><span class="sxs-lookup"><span data-stu-id="b2375-285">A program is memory safe if it accesses only allocated memory.</span></span> <span data-ttu-id="b2375-286">例如，執行階段可確保應用程式不會存取陣列界限外已取消配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b2375-286">For instance, the runtime ensures that an app doesn't access unallocated memory beyond the bounds of an array.</span></span>

<span data-ttu-id="b2375-287">如需詳細資訊，請參閱 [自動記憶體管理](../standard/automatic-memory-management.md) 和 [垃圾收集的基本](../standard/garbage-collection/fundamentals.md)概念。</span><span class="sxs-lookup"><span data-stu-id="b2375-287">For more information, see [Automatic memory management](../standard/automatic-memory-management.md) and [Fundamentals of garbage collection](../standard/garbage-collection/fundamentals.md).</span></span>

### <a name="working-with-unmanaged-resources"></a><span data-ttu-id="b2375-288">使用 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="b2375-288">Working with unmanaged resources</span></span>

<span data-ttu-id="b2375-289">有時候，程式碼需要參考 *未受管理的資源*。</span><span class="sxs-lookup"><span data-stu-id="b2375-289">Sometimes code needs to reference *unmanaged resources*.</span></span> <span data-ttu-id="b2375-290">Unmanaged 資源是指 .NET 執行階段不會自動維護的資源。</span><span class="sxs-lookup"><span data-stu-id="b2375-290">Unmanaged resources are resources that aren't automatically maintained by the .NET runtime.</span></span> <span data-ttu-id="b2375-291">例如檔案控制程式碼就是 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="b2375-291">For example, a file handle is an unmanaged resource.</span></span> <span data-ttu-id="b2375-292"><xref:System.IO.FileStream> 物件是Managed 物件，但會 Unmanaged 檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b2375-292">A <xref:System.IO.FileStream> object is a managed object, but it references a file handle, which is unmanaged.</span></span> <span data-ttu-id="b2375-293">當您使用完成時 <xref:System.IO.FileStream> ，您必須明確釋放檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b2375-293">When you're done using the <xref:System.IO.FileStream>, you need to explicitly release the file handle.</span></span>

<span data-ttu-id="b2375-294">在.NET 中，參考 Unmanaged 資源的物件會實作 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="b2375-294">In .NET, objects that reference unmanaged resources implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="b2375-295">當您完成使用此物件時，您可以呼叫物件的 <xref:System.IDisposable.Dispose> 方法來釋放任何 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="b2375-295">When you're done using the object, you call the object's <xref:System.IDisposable.Dispose> method, which is responsible for releasing any unmanaged resources.</span></span> <span data-ttu-id="b2375-296">.Net 語言提供了一個方便的 `using` 語句， ([c #](../csharp/language-reference/keywords/using.md)、 [F #](../fsharp/language-reference/resource-management-the-use-keyword.md)、 [VB](../visual-basic/language-reference/statements/using-statement.md)) ，可確保 `Dispose` 呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b2375-296">The .NET languages provide a convenient `using` statement ([C#](../csharp/language-reference/keywords/using.md), [F#](../fsharp/language-reference/resource-management-the-use-keyword.md), [VB](../visual-basic/language-reference/statements/using-statement.md)) that ensures the `Dispose` method is called.</span></span>

<span data-ttu-id="b2375-297">如需詳細資訊，請參閱 [清除非受控資源](../standard/garbage-collection/unmanaged.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-297">For more information, see [Cleaning up unmanaged resources](../standard/garbage-collection/unmanaged.md).</span></span>

## <a name="deployment-models"></a><span data-ttu-id="b2375-298">部署模型</span><span class="sxs-lookup"><span data-stu-id="b2375-298">Deployment models</span></span>

<span data-ttu-id="b2375-299">.NET 應用程式可在兩種不同的模式下發行：</span><span class="sxs-lookup"><span data-stu-id="b2375-299">.NET apps can be published in two different modes:</span></span>

* <span data-ttu-id="b2375-300">將應用程式發佈為 *獨立* 應用程式會產生可執行檔，其中包含 .net [運行](#sdk-and-runtimes) 時間和連結 [庫](#runtime-libraries)，以及應用程式及其相依性。</span><span class="sxs-lookup"><span data-stu-id="b2375-300">Publishing an app as *self-contained* produces an executable file that includes the .NET [runtime](#sdk-and-runtimes) and [libraries](#runtime-libraries), and the application and its dependencies.</span></span> <span data-ttu-id="b2375-301">應用程式的使用者可以在未安裝 .NET 執行時間的電腦上執行它。</span><span class="sxs-lookup"><span data-stu-id="b2375-301">Users of the application can run it on a machine that doesn't have the .NET runtime installed.</span></span> <span data-ttu-id="b2375-302">獨立應用程式是平臺專屬的應用程式，而且可以選擇性地使用 [AOT 編譯](#aot-compiler)形式來發佈。</span><span class="sxs-lookup"><span data-stu-id="b2375-302">Self-contained apps are platform-specific, and they can optionally be published using a form of [AOT compilation](#aot-compiler).</span></span>

* <span data-ttu-id="b2375-303">將應用程式發行為與 *framework 相依* 的應用程式，會產生可執行檔和二進位檔案 (*.dll* 檔案，) 只包含應用程式本身及其相依性。</span><span class="sxs-lookup"><span data-stu-id="b2375-303">Publishing an app as *framework-dependent* produces an executable file and binary files (*.dll* files) that include only the application itself and its dependencies.</span></span> <span data-ttu-id="b2375-304">應用程式的使用者必須分別安裝 .NET [運行](#sdk-and-runtimes)時間。</span><span class="sxs-lookup"><span data-stu-id="b2375-304">Users of the application have to separately install the .NET [runtime](#sdk-and-runtimes).</span></span> <span data-ttu-id="b2375-305">可執行檔是平臺專屬的，但架構相依應用程式的 *.dll* 檔案是跨平臺。</span><span class="sxs-lookup"><span data-stu-id="b2375-305">The executable file is platform-specific, but The *.dll* files of framework-dependent applications are cross-platform.</span></span>

  <span data-ttu-id="b2375-306">您可以並存安裝多個版本的執行時間，以執行以不同執行階段版本為目標的架構相依應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2375-306">You can install multiple versions of the runtime side by side to run framework-dependent apps that target different versions of the runtime.</span></span> <span data-ttu-id="b2375-307">如需詳細資訊，請參閱 [目標 framework](../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-307">For more information, see [Target frameworks](../standard/frameworks.md).</span></span>

<span data-ttu-id="b2375-308">系統會針對特定的目標平臺產生可執行檔，您可以使用執行時間識別碼來指定 [ (RID) ](rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-308">Executables are produced for specific target platforms, which you specify with a [runtime identifier (RID)](rid-catalog.md).</span></span>

<span data-ttu-id="b2375-309">如需詳細資訊，請參閱 [.net 應用程式發行總覽](deploying/index.md) 和 [.Net 和 Docker 簡介](docker/introduction.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-309">For more information, see [.NET application publishing overview](deploying/index.md) and [Introduction to .NET and Docker](docker/introduction.md).</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="b2375-310">執行階段程式庫</span><span class="sxs-lookup"><span data-stu-id="b2375-310">Runtime libraries</span></span>

<span data-ttu-id="b2375-311">.NET 有一組廣泛的標準類別庫，稱為執行時間連結 [庫](../standard/glossary.md#runtime)、 [架構程式庫](../standard/glossary.md#framework-libraries)，或 [ (BCL) 的基類庫 ](../standard/glossary.md#bcl)。</span><span class="sxs-lookup"><span data-stu-id="b2375-311">.NET has an expansive standard set of class libraries, known as [runtime libraries](../standard/glossary.md#runtime), [framework libraries](../standard/glossary.md#framework-libraries), or the [base class library (BCL)](../standard/glossary.md#bcl).</span></span> <span data-ttu-id="b2375-312">這些程式庫提供許多一般用途和工作負載特定類型和公用程式功能的實作為。</span><span class="sxs-lookup"><span data-stu-id="b2375-312">These libraries provide implementations for many general-purpose and workload-specific types and utility functionality.</span></span>

<span data-ttu-id="b2375-313">以下是 .NET 執行時間程式庫中定義的一些類型範例：</span><span class="sxs-lookup"><span data-stu-id="b2375-313">Here are some examples of types defined in the .NET runtime libraries:</span></span>

* <span data-ttu-id="b2375-314">基本類型，例如 <xref:System.Boolean?displayProperty=nameWithType> 和 <xref:System.Int32?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b2375-314">Primitive types, such as <xref:System.Boolean?displayProperty=nameWithType> and <xref:System.Int32?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="b2375-315">集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b2375-315">Collections, such as <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> and <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="b2375-316">資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 和 <xref:System.Data.DataTable?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b2375-316">Data types, such as <xref:System.Data.DataSet?displayProperty=nameWithType> and <xref:System.Data.DataTable?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="b2375-317">網路公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b2375-317">Network utility types, such as <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="b2375-318">檔案[和資料流程 i/o](../standard/io/index.md)公用程式類型，例如 <xref:System.IO.FileStream?displayProperty=nameWithType> 和 <xref:System.IO.TextWriter?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b2375-318">[File and stream I/O](../standard/io/index.md) utility types, such as <xref:System.IO.FileStream?displayProperty=nameWithType> and <xref:System.IO.TextWriter?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="b2375-319">[序列化](../standard/serialization/index.md) 公用程式類型，例如 <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 和 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b2375-319">[Serialization](../standard/serialization/index.md) utility types, such as <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> and <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="b2375-320">高效能類型，例如 <xref:System.Span%601?displayProperty=nameWithType> 、 <xref:System.Numerics.Vector?displayProperty=nameWithType> 和 [管線](../standard/io/pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-320">High-performance types, such as <xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Numerics.Vector?displayProperty=nameWithType>, and [Pipelines](../standard/io/pipelines.md).</span></span>

<span data-ttu-id="b2375-321">如需詳細資訊，請參閱執行時間連結 [庫總覽](../standard/runtime-libraries-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-321">For more information, see the [Runtime libraries overview](../standard/runtime-libraries-overview.md).</span></span> <span data-ttu-id="b2375-322">程式庫的原始程式碼位於 [GitHub dotnet/runtime 存放庫](https://github.com/dotnet/runtime/tree/master/src/libraries)中。</span><span class="sxs-lookup"><span data-stu-id="b2375-322">The source code for the libraries is in [the GitHub dotnet/runtime repository](https://github.com/dotnet/runtime/tree/master/src/libraries).</span></span>

### <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="b2375-323">執行時間程式庫的延伸模組</span><span class="sxs-lookup"><span data-stu-id="b2375-323">Extensions to the runtime libraries</span></span>

<span data-ttu-id="b2375-324">某些常用應用程式功能的程式庫不包含在執行時間程式庫中，但可在 NuGet 套件中使用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2375-324">Libraries for some commonly used application functionality aren't included in the runtime libraries but are made available in NuGet packages, such as the following:</span></span>

| <span data-ttu-id="b2375-325">Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="b2375-325">NuGet package</span></span> | <span data-ttu-id="b2375-326">文件</span><span class="sxs-lookup"><span data-stu-id="b2375-326">Documentation</span></span> |
|---------|---------|
| [<span data-ttu-id="b2375-327">Microsoft.Extensions.Hosting</span><span class="sxs-lookup"><span data-stu-id="b2375-327">Microsoft.Extensions.Hosting</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) | [<span data-ttu-id="b2375-328">應用程式存留期管理 (一般主機) </span><span class="sxs-lookup"><span data-stu-id="b2375-328">Application lifetime management (Generic Host)</span></span>](extensions/generic-host.md) |
| [<span data-ttu-id="b2375-329">DependencyInjection</span><span class="sxs-lookup"><span data-stu-id="b2375-329">Microsoft.Extensions.DependencyInjection</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection) | [<span data-ttu-id="b2375-330">相依性插入 (DI)</span><span class="sxs-lookup"><span data-stu-id="b2375-330">Dependency injection (DI)</span></span>](extensions/dependency-injection.md)
| [<span data-ttu-id="b2375-331">Microsoft.Extensions.Configuration</span><span class="sxs-lookup"><span data-stu-id="b2375-331">Microsoft.Extensions.Configuration</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Configuration) | [<span data-ttu-id="b2375-332">設定</span><span class="sxs-lookup"><span data-stu-id="b2375-332">Configuration</span></span>](extensions/configuration.md) |
| [<span data-ttu-id="b2375-333">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="b2375-333">Microsoft.Extensions.Logging</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Logging) | [<span data-ttu-id="b2375-334">記錄</span><span class="sxs-lookup"><span data-stu-id="b2375-334">Logging</span></span>](extensions/logging.md) |
| [<span data-ttu-id="b2375-335">Microsoft. Extensions. 選項</span><span class="sxs-lookup"><span data-stu-id="b2375-335">Microsoft.Extensions.Options</span></span>](https://www.nuget.org/packages/Microsoft.Extensions.Options) | [<span data-ttu-id="b2375-336">選項模式</span><span class="sxs-lookup"><span data-stu-id="b2375-336">Options pattern</span></span>](extensions/options.md) |

<span data-ttu-id="b2375-337">如需詳細資訊，請參閱 [GitHub 上的 dotnet/extensions 存放庫](https://github.com/dotnet/extensions)。</span><span class="sxs-lookup"><span data-stu-id="b2375-337">For more information, see the [dotnet/extensions repository on GitHub](https://github.com/dotnet/extensions).</span></span>

## <a name="data-access"></a><span data-ttu-id="b2375-338">資料存取</span><span class="sxs-lookup"><span data-stu-id="b2375-338">Data access</span></span>

<span data-ttu-id="b2375-339">.NET 提供物件/關聯式對應程式 (ORM) 以及在程式碼中撰寫 SQL 查詢的方式。</span><span class="sxs-lookup"><span data-stu-id="b2375-339">.NET provides an Object/Relational Mapper (ORM) and a way to write SQL queries in code.</span></span>

### <a name="entity-framework-core"></a><span data-ttu-id="b2375-340">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="b2375-340">Entity Framework Core</span></span>

<span data-ttu-id="b2375-341">Entity Framework (EF) Core 是一個 [開放原始](https://github.com/aspnet/EntityFrameworkCore) 碼和跨平臺的資料存取技術，可作為 ORM。</span><span class="sxs-lookup"><span data-stu-id="b2375-341">Entity Framework (EF) Core is an [open source](https://github.com/aspnet/EntityFrameworkCore) and cross-platform data-access technology that can serve as an ORM.</span></span> <span data-ttu-id="b2375-342">EF Core 可讓您在程式碼中參考 .NET 物件來處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="b2375-342">EF Core lets you work with a database by referring to .NET objects in code.</span></span> <span data-ttu-id="b2375-343">它可減少您需要撰寫和測試的資料存取程式碼數量。</span><span class="sxs-lookup"><span data-stu-id="b2375-343">It reduces the amount of data-access code you would otherwise need to write and test.</span></span> <span data-ttu-id="b2375-344">EF Core 支援許多資料庫引擎。</span><span class="sxs-lookup"><span data-stu-id="b2375-344">EF Core supports many database engines.</span></span>

<span data-ttu-id="b2375-345">如需詳細資訊，請參閱 [Entity Framework Core](/ef/core/) 和 [資料庫提供者](/ef/core/providers/)。</span><span class="sxs-lookup"><span data-stu-id="b2375-345">For more information, see [Entity Framework Core](/ef/core/) and [Database Providers](/ef/core/providers/).</span></span>

### <a name="linq"></a><span data-ttu-id="b2375-346">LINQ</span><span class="sxs-lookup"><span data-stu-id="b2375-346">LINQ</span></span>

<span data-ttu-id="b2375-347">語言整合式查詢 (LINQ) 可讓您撰寫用來運算元據的宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2375-347">Language-integrated query (LINQ) lets you write declarative code for operating on data.</span></span> <span data-ttu-id="b2375-348">資料可以是許多形式 (例如記憶體內部物件、SQL 資料庫或 XML 文件)，但您撰寫的 LINQ 程式碼在資料來源方面通常大同小異。</span><span class="sxs-lookup"><span data-stu-id="b2375-348">The data can be in many forms (such as in-memory objects, a SQL database, or an XML document), but the LINQ code you write typically doesn't differ by data source.</span></span>

<span data-ttu-id="b2375-349">如需詳細資訊，請參閱 [LINQ (語言整合式查詢) 總覽](../standard/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-349">For more information, see [LINQ (Language Integrated Query) overview](../standard/linq/index.md).</span></span>

## <a name="net-terminology"></a><span data-ttu-id="b2375-350">.NET 術語</span><span class="sxs-lookup"><span data-stu-id="b2375-350">.NET terminology</span></span>

<span data-ttu-id="b2375-351">若要瞭解 .NET 檔，可協助您瞭解某些詞彙的使用方式如何隨時間而改變。</span><span class="sxs-lookup"><span data-stu-id="b2375-351">To understand .NET documentation, it can help to know how the usage of some terms has changed over time.</span></span>

### <a name="net-core-and-net-5"></a><span data-ttu-id="b2375-352">.NET Core 和 .NET 5</span><span class="sxs-lookup"><span data-stu-id="b2375-352">.NET Core and .NET 5</span></span>

<span data-ttu-id="b2375-353">在2002中，Microsoft 發行了 [.NET Framework](../framework/get-started/overview.md)，這是用來建立 Windows 應用程式的開發平臺。</span><span class="sxs-lookup"><span data-stu-id="b2375-353">In 2002, Microsoft released [.NET Framework](../framework/get-started/overview.md), a development platform for creating Windows apps.</span></span> <span data-ttu-id="b2375-354">今天 .NET Framework 是4.8 版，而且 Microsoft 仍 [支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)此版本。</span><span class="sxs-lookup"><span data-stu-id="b2375-354">Today .NET Framework is at version 4.8 and is still [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework).</span></span>

<span data-ttu-id="b2375-355">在2014中，Microsoft 開始撰寫 .NET Framework 的跨平臺開放原始碼後續工作。</span><span class="sxs-lookup"><span data-stu-id="b2375-355">In 2014, Microsoft began writing a cross-platform, open-source successor to .NET Framework.</span></span> <span data-ttu-id="b2375-356">這項新的 .NET 實名為 .NET Core，直到它到達3.1 版為止。</span><span class="sxs-lookup"><span data-stu-id="b2375-356">This new implementation of .NET was named .NET Core until it reached version 3.1.</span></span> <span data-ttu-id="b2375-357">.NET Core 3.1 之後的下一個版本是 .NET 5.0，目前為預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="b2375-357">The next version after .NET Core 3.1 is .NET 5.0, which is currently in preview.</span></span> <span data-ttu-id="b2375-358">已略過第4版，以避免這種 .NET 的執行與 .NET Framework 4.8 的混淆。</span><span class="sxs-lookup"><span data-stu-id="b2375-358">Version number 4 was skipped to avoid confusion between this implementation of .NET and .NET Framework 4.8.</span></span> <span data-ttu-id="b2375-359">已捨棄名稱 "Core"，以確定這現在是 .NET 的主要執行。</span><span class="sxs-lookup"><span data-stu-id="b2375-359">The name "Core" was dropped to make clear that this is now the main implementation of .NET.</span></span>

<span data-ttu-id="b2375-360">這篇文章是關於 .NET 5，但 .NET 5 的大部分檔仍有 ".NET Core" 或 ".NET Framework" 的參考。</span><span class="sxs-lookup"><span data-stu-id="b2375-360">This article is about .NET 5, but much of the documentation for .NET 5 still has references to ".NET Core" or ".NET Framework".</span></span> <span data-ttu-id="b2375-361">此外，"Core" 會保留在名稱 [ASP.NET Core](/aspnet/core/) 和 [Entity Framework Core](/ef/core/)。</span><span class="sxs-lookup"><span data-stu-id="b2375-361">In addition, "Core" remains in the names [ASP.NET Core](/aspnet/core/) and [Entity Framework Core](/ef/core/).</span></span>

<span data-ttu-id="b2375-362">檔也會參考 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="b2375-362">The documentation also refers to .NET Standard.</span></span> <span data-ttu-id="b2375-363">[.NET Standard](../standard/net-standard.md) 是一種 API 規格，可讓您開發適用于多個 .net 的類別庫。</span><span class="sxs-lookup"><span data-stu-id="b2375-363">[.NET Standard](../standard/net-standard.md) is an API specification that lets you develop class libraries for multiple implementations of .NET.</span></span>

<span data-ttu-id="b2375-364">如需詳細資訊，請參閱 [.net 架構元件](../standard/components.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-364">For more information, see [.NET architectural components](../standard/components.md).</span></span>

### <a name="overloaded-terms"></a><span data-ttu-id="b2375-365">多載詞彙</span><span class="sxs-lookup"><span data-stu-id="b2375-365">Overloaded terms</span></span>

<span data-ttu-id="b2375-366">適用于 .NET 的部分術語可能會造成混淆，因為相同的單字在不同的內容中使用不同的方式。</span><span class="sxs-lookup"><span data-stu-id="b2375-366">Some of the terminology for .NET can be confusing because the same word is used in different ways in different contexts.</span></span> <span data-ttu-id="b2375-367">以下是一些比較顯著的實例：</span><span class="sxs-lookup"><span data-stu-id="b2375-367">Here are a few of the more prominent instances:</span></span>

* <span data-ttu-id="b2375-368">**執行階段**</span><span class="sxs-lookup"><span data-stu-id="b2375-368">**runtime**</span></span>

  |<span data-ttu-id="b2375-369">Context</span><span class="sxs-lookup"><span data-stu-id="b2375-369">Context</span></span>  |<span data-ttu-id="b2375-370">「執行時間」表示</span><span class="sxs-lookup"><span data-stu-id="b2375-370">"runtime" meaning</span></span> |
  |---------|---------|
  | [<span data-ttu-id="b2375-371">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="b2375-371">Common Language Runtime (CLR)</span></span>](#clr)| <span data-ttu-id="b2375-372">受管理程式的執行環境。</span><span class="sxs-lookup"><span data-stu-id="b2375-372">The execution environment for a managed program.</span></span> <span data-ttu-id="b2375-373">作業系統是執行時間環境的一部分，但不是 .NET 執行時間的一部分。</span><span class="sxs-lookup"><span data-stu-id="b2375-373">The OS is part of the runtime environment but isn't part of the .NET runtime.</span></span> |
  | [<span data-ttu-id="b2375-374">.NET 下載頁面上的 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="b2375-374">.NET runtime on the .NET download page</span></span>](https://dotnet.microsoft.com/download/dotnet-core) | <span data-ttu-id="b2375-375">[CLR](#clr)與執行時間連結[庫](#runtime-libraries)，兩者共同提供執行[架構相依](#deployment-models)應用程式的支援。</span><span class="sxs-lookup"><span data-stu-id="b2375-375">The [CLR](#clr) and [runtime libraries](#runtime-libraries), which together provide support for running [framework-dependent](#deployment-models) apps.</span></span> <span data-ttu-id="b2375-376">此頁面也提供 ASP.NET Core server 應用程式和 Windows 桌面應用程式的執行時間選項。</span><span class="sxs-lookup"><span data-stu-id="b2375-376">The page also offers runtime choices for ASP.NET Core server apps and Windows desktop apps.</span></span> |
  | [<span data-ttu-id="b2375-377"> (RID) 的執行時間識別碼 </span><span class="sxs-lookup"><span data-stu-id="b2375-377">Runtime Identifier (RID)</span></span>](rid-catalog.md) | <span data-ttu-id="b2375-378">.NET 應用程式執行所在的 OS 平臺和 CPU 架構。</span><span class="sxs-lookup"><span data-stu-id="b2375-378">The OS platform and CPU architecture that a .NET app runs on.</span></span> <span data-ttu-id="b2375-379">例如： Windows x64、Linux x64。</span><span class="sxs-lookup"><span data-stu-id="b2375-379">For example: Windows x64, Linux x64.</span></span> |

* <span data-ttu-id="b2375-380">**框架**</span><span class="sxs-lookup"><span data-stu-id="b2375-380">**framework**</span></span>

  |<span data-ttu-id="b2375-381">Context</span><span class="sxs-lookup"><span data-stu-id="b2375-381">Context</span></span>  | <span data-ttu-id="b2375-382">"framework" 意義</span><span class="sxs-lookup"><span data-stu-id="b2375-382">"framework" meaning</span></span> |
  |---------|---------------------|
  | <span data-ttu-id="b2375-383">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b2375-383">.NET Framework</span></span> | <span data-ttu-id="b2375-384">.NET 的原始、僅限 Windows 的實作為。</span><span class="sxs-lookup"><span data-stu-id="b2375-384">The original, Windows-only implementation of .NET.</span></span> <span data-ttu-id="b2375-385">"Framework" 為大寫。</span><span class="sxs-lookup"><span data-stu-id="b2375-385">"Framework" is capitalized.</span></span> |
  | <span data-ttu-id="b2375-386">Target Framework - 目標 Framework</span><span class="sxs-lookup"><span data-stu-id="b2375-386">target framework</span></span> | <span data-ttu-id="b2375-387">.NET 應用程式或程式庫依賴的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="b2375-387">The collection of APIs that a .NET app or library relies on.</span></span> <span data-ttu-id="b2375-388">範例： .NET Core 3.1、.NET Standard 2。0</span><span class="sxs-lookup"><span data-stu-id="b2375-388">Examples: .NET Core 3.1, .NET Standard 2.0</span></span> |
  | <span data-ttu-id="b2375-389">Target Framework Moniker (TFM)</span><span class="sxs-lookup"><span data-stu-id="b2375-389">Target Framework Moniker (TFM)</span></span>  | <span data-ttu-id="b2375-390">TFM 是標準化的權杖格式，用於指定 .NET 應用程式或程式庫的目標 framework。</span><span class="sxs-lookup"><span data-stu-id="b2375-390">A TFM is a standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="b2375-391">範例： `net462` 適用于 .NET Framework 4.6.2。</span><span class="sxs-lookup"><span data-stu-id="b2375-391">Example: `net462` for .NET Framework 4.6.2.</span></span> |
  | <span data-ttu-id="b2375-392">與 framework 相依的應用程式</span><span class="sxs-lookup"><span data-stu-id="b2375-392">framework-dependent app</span></span> | <span data-ttu-id="b2375-393">只能在您從 [.net 下載頁面](https://dotnet.microsoft.com/download/dotnet-core)安裝執行時間的電腦上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2375-393">An app that can only run on a machine where you've installed the runtime from the [.NET download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span> <span data-ttu-id="b2375-394">此使用方式中的「架構」與您從 .NET 下載頁面下載的「執行時間」相同。</span><span class="sxs-lookup"><span data-stu-id="b2375-394">"Framework" in this usage is the same thing as the "runtime" that you download from the .NET download page.</span></span> |
  | <span data-ttu-id="b2375-395">framework 程式庫</span><span class="sxs-lookup"><span data-stu-id="b2375-395">framework libraries</span></span> | <span data-ttu-id="b2375-396">有時會用來做為 [運行](#runtime-libraries)時間程式庫的同義字。</span><span class="sxs-lookup"><span data-stu-id="b2375-396">Sometimes used as a synonym for [runtime libraries](#runtime-libraries).</span></span> |

* <span data-ttu-id="b2375-397">**SDK**</span><span class="sxs-lookup"><span data-stu-id="b2375-397">**SDK**</span></span>

  |<span data-ttu-id="b2375-398">Context</span><span class="sxs-lookup"><span data-stu-id="b2375-398">Context</span></span>  | <span data-ttu-id="b2375-399">"SDK" 意義</span><span class="sxs-lookup"><span data-stu-id="b2375-399">"SDK" meaning</span></span> |
  |---------|---------------|
  | [<span data-ttu-id="b2375-400">.NET 下載頁面上的 SDK</span><span class="sxs-lookup"><span data-stu-id="b2375-400">SDK on the .NET download page</span></span>](#sdk-and-runtimes)  | <span data-ttu-id="b2375-401">您下載並安裝以開發和執行 .NET 應用程式的工具和程式庫集合。</span><span class="sxs-lookup"><span data-stu-id="b2375-401">A collection of tools and libraries that you download and install to develop and run .NET apps.</span></span> <span data-ttu-id="b2375-402">包括 CLI、MSBuild、.NET 執行時間和其他元件。</span><span class="sxs-lookup"><span data-stu-id="b2375-402">Includes the CLI, MSBuild, the .NET runtime, and other components.</span></span>|
  | [<span data-ttu-id="b2375-403">SDK 樣式專案</span><span class="sxs-lookup"><span data-stu-id="b2375-403">SDK-style project</span></span>](#project-system-and-msbuild) | <span data-ttu-id="b2375-404">一組 MSBuild 目標和工作，可指定如何建立特定應用程式類型的專案。</span><span class="sxs-lookup"><span data-stu-id="b2375-404">A set of MSBuild targets and tasks that specifies how to build a project for a particular app type.</span></span> <span data-ttu-id="b2375-405">此概念中的 SDK 是使用 `Sdk` 專案檔中專案的屬性所指定 `Project` 。</span><span class="sxs-lookup"><span data-stu-id="b2375-405">The SDK in this sense is specified by using the `Sdk` attribute of the `Project` element in a project file.</span></span> |

* <span data-ttu-id="b2375-406">**平台**</span><span class="sxs-lookup"><span data-stu-id="b2375-406">**platform**</span></span>

  |<span data-ttu-id="b2375-407">Context</span><span class="sxs-lookup"><span data-stu-id="b2375-407">Context</span></span>  | <span data-ttu-id="b2375-408">「平臺」意義</span><span class="sxs-lookup"><span data-stu-id="b2375-408">"platform" meaning</span></span> |
  |---------|--------------------|
  | <span data-ttu-id="b2375-409">跨平臺</span><span class="sxs-lookup"><span data-stu-id="b2375-409">cross platform</span></span> | <span data-ttu-id="b2375-410">在此詞彙中，「平臺」表示作業系統和其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。</span><span class="sxs-lookup"><span data-stu-id="b2375-410">In this term, "platform" means an operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span> |
  | <span data-ttu-id="b2375-411">.NET 平臺</span><span class="sxs-lookup"><span data-stu-id="b2375-411">.NET platform</span></span> | <span data-ttu-id="b2375-412">使用方式會有所不同。</span><span class="sxs-lookup"><span data-stu-id="b2375-412">Usage varies.</span></span> <span data-ttu-id="b2375-413">參考可能是一種 .NET (的執行，例如 .NET Framework 或 .NET 5) 或 .NET 的整體概念，包括所有的實作為。</span><span class="sxs-lookup"><span data-stu-id="b2375-413">The reference may be to one implementation of .NET (such as .NET Framework or .NET 5) or to an overarching concept of .NET including all implementations.</span></span> |

<span data-ttu-id="b2375-414">如需 .NET 術語的詳細資訊，請參閱 [.net 詞彙](../standard/glossary.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-414">For more information about .NET terminology, see the [.NET glossary](../standard/glossary.md).</span></span>

## <a name="advanced-scenarios"></a><span data-ttu-id="b2375-415">進階案例</span><span class="sxs-lookup"><span data-stu-id="b2375-415">Advanced scenarios</span></span>

<span data-ttu-id="b2375-416">下列各節說明一些適用于先進案例的 .NET 功能。</span><span class="sxs-lookup"><span data-stu-id="b2375-416">The following sections explain some capabilities of .NET that are useful in advanced scenarios.</span></span>

### <a name="native-interop"></a><span data-ttu-id="b2375-417">原生 interop</span><span class="sxs-lookup"><span data-stu-id="b2375-417">Native interop</span></span>

<span data-ttu-id="b2375-418">每個作業系統都包含提供系統服務的應用程式開發介面 (API)。</span><span class="sxs-lookup"><span data-stu-id="b2375-418">Every operating system includes an application programming interface (API) that provides system services.</span></span> <span data-ttu-id="b2375-419">.NET 提供幾種方式來呼叫這些 API。</span><span class="sxs-lookup"><span data-stu-id="b2375-419">.NET provides several ways to call those APIs.</span></span>

<span data-ttu-id="b2375-420">與原生 Api 交互操作的主要方式是透過「平台叫用」或 P/Invoke （短）。</span><span class="sxs-lookup"><span data-stu-id="b2375-420">The main way to interoperate with native APIs is via "platform invoke" or P/Invoke for short.</span></span> <span data-ttu-id="b2375-421">Linux 和 Windows 平臺之間支援 P/Invoke。</span><span class="sxs-lookup"><span data-stu-id="b2375-421">P/Invoke is supported across Linux and Windows platforms.</span></span> <span data-ttu-id="b2375-422">僅限 Windows 的交互操作方法稱為「COM interop」，可搭配 managed 程式碼中的 [COM 元件](/cpp/atl/introduction-to-com) 使用。</span><span class="sxs-lookup"><span data-stu-id="b2375-422">A Windows-only way of interoperating is known as "COM interop," which works with [COM components](/cpp/atl/introduction-to-com) in managed code.</span></span> <span data-ttu-id="b2375-423">它是以 P/Invoke 基礎結構為建置基礎，但運作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="b2375-423">It's built on top of the P/Invoke infrastructure, but it works in subtly different ways.</span></span>

<span data-ttu-id="b2375-424">如需詳細資訊，請參閱 [原生互通性](../standard/native-interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-424">For more information, see [Native interoperability](../standard/native-interop/index.md).</span></span>

### <a name="unsafe-code"></a><span data-ttu-id="b2375-425">Unsafe 程式碼</span><span class="sxs-lookup"><span data-stu-id="b2375-425">Unsafe code</span></span>

<span data-ttu-id="b2375-426">CLR 可讓您根據語言支援透過 `unsafe` 程式碼存取原生記憶體及執行指標算術。</span><span class="sxs-lookup"><span data-stu-id="b2375-426">Depending on language support, the CLR lets you access native memory and do pointer arithmetic via `unsafe` code.</span></span> <span data-ttu-id="b2375-427">特定演算法和系統互通性需要這些作業。</span><span class="sxs-lookup"><span data-stu-id="b2375-427">These operations are needed for certain algorithms and system interoperability.</span></span> <span data-ttu-id="b2375-428">雖然功能強大，但不建議使用 unsafe 程式碼，除非它必須與系統 Api 互通，或執行最有效率的演算法。</span><span class="sxs-lookup"><span data-stu-id="b2375-428">Although powerful, use of unsafe code is discouraged unless it's necessary to interoperate with system APIs or implement the most efficient algorithm.</span></span> <span data-ttu-id="b2375-429">Unsafe 程式碼在不同的環境中執行時可能不盡相同，而且也會失去記憶體回收行程和型別安全的好處。</span><span class="sxs-lookup"><span data-stu-id="b2375-429">Unsafe code may not execute the same way in different environments and also loses the benefits of a garbage collector and type safety.</span></span> <span data-ttu-id="b2375-430">建議您盡可能限制和集中使用 Unsafe 程式碼，並徹底測試該程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2375-430">It's recommended to confine and centralize unsafe code as much as possible and test that code thoroughly.</span></span>

<span data-ttu-id="b2375-431">如需詳細資訊，請參閱 [Unsafe 程式碼和指標](../csharp/programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b2375-431">For more information, see [Unsafe code and pointers](../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2375-432">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2375-432">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2375-433">選擇 .NET 教學課程</span><span class="sxs-lookup"><span data-stu-id="b2375-433">Choose a .NET tutorial</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2375-434">在您的瀏覽器中嘗試 .NET</span><span class="sxs-lookup"><span data-stu-id="b2375-434">Try .NET in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2375-435">流覽 C#</span><span class="sxs-lookup"><span data-stu-id="b2375-435">Take a tour of C#</span></span>](../csharp/tour-of-csharp/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2375-436">流覽 F#</span><span class="sxs-lookup"><span data-stu-id="b2375-436">Take a tour of F#</span></span>](../fsharp/tour.md)
