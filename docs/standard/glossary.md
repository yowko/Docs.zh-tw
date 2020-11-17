---
title: .NET 字彙表
description: 了解 .NET 文件中所使用之特定詞彙的意義。
ms.date: 11/16/2020
ms.openlocfilehash: 143657b4ec360640c0a43099ca5c1c0d9c863453
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687775"
---
# <a name="net-glossary"></a><span data-ttu-id="57c34-103">.NET 字彙表</span><span class="sxs-lookup"><span data-stu-id="57c34-103">.NET Glossary</span></span>

<span data-ttu-id="57c34-104">此字彙表的主要目標是釐清經常出現在 .NET 文件中但沒有定義之特定詞彙和縮略字的意義。</span><span class="sxs-lookup"><span data-stu-id="57c34-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="57c34-105">AOT</span><span class="sxs-lookup"><span data-stu-id="57c34-105">AOT</span></span>

<span data-ttu-id="57c34-106">預先編譯器。</span><span class="sxs-lookup"><span data-stu-id="57c34-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="57c34-107">此編譯器類似於 [JIT](#jit)，也會將 [IL](#il) 轉譯成機器碼。</span><span class="sxs-lookup"><span data-stu-id="57c34-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="57c34-108">相較於 JIT 編譯，AOT 編譯會在執行應用程式之前發生，而且通常會在不同的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="57c34-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="57c34-109">因為 AOT 工具鏈不會在執行時間編譯，所以不需要將編譯花費的時間降到最低。</span><span class="sxs-lookup"><span data-stu-id="57c34-109">Because AOT tool chains don't compile at run time, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="57c34-110">這表示它們可以花更多的時間在最佳化。</span><span class="sxs-lookup"><span data-stu-id="57c34-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="57c34-111">由於 AOT 的內容是整個應用程式，因此 AOT 編譯器也會執行跨模組連結和整個程式分析，這表示會追蹤所有參考並產生單一可執行檔。</span><span class="sxs-lookup"><span data-stu-id="57c34-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="57c34-112">請參閱 [CoreRT](#corert) 及 [.NET Native](#net-native)。</span><span class="sxs-lookup"><span data-stu-id="57c34-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="app-model"></a><span data-ttu-id="57c34-113">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="57c34-113">app model</span></span>

<span data-ttu-id="57c34-114">[工作負載](#workload)特定的 API。</span><span class="sxs-lookup"><span data-stu-id="57c34-114">A [workload](#workload)-specific API.</span></span> <span data-ttu-id="57c34-115">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="57c34-115">Here are some examples:</span></span>

* <span data-ttu-id="57c34-116">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="57c34-116">ASP.NET</span></span>
* <span data-ttu-id="57c34-117">ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="57c34-117">ASP.NET Web API</span></span>
* <span data-ttu-id="57c34-118">Entity Framework (EF) </span><span class="sxs-lookup"><span data-stu-id="57c34-118">Entity Framework (EF)</span></span>
* <span data-ttu-id="57c34-119">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="57c34-119">Windows Presentation Foundation (WPF)</span></span>
* <span data-ttu-id="57c34-120">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="57c34-120">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="57c34-121">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="57c34-121">Windows Workflow Foundation (WF)</span></span>
* <span data-ttu-id="57c34-122">Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="57c34-122">Windows Forms (WinForms)</span></span>

## <a name="aspnet"></a><span data-ttu-id="57c34-123">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="57c34-123">ASP.NET</span></span>

<span data-ttu-id="57c34-124">隨附於 .NET Framework 的原始 ASP.NET 實作。</span><span class="sxs-lookup"><span data-stu-id="57c34-124">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="57c34-125">有時 ASP.NET 是指包括 ASP.NET Core 在內之兩個 ASP.NET 實作的籠統名詞。</span><span class="sxs-lookup"><span data-stu-id="57c34-125">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="57c34-126">該詞彙在任何指定的執行個體中所代表的意義取決於內容。</span><span class="sxs-lookup"><span data-stu-id="57c34-126">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="57c34-127">如果您想要清楚說您不是使用 ASP.NET 來表示這兩個執行，請參閱 ASP.NET 4.x。</span><span class="sxs-lookup"><span data-stu-id="57c34-127">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="57c34-128">請參閱 [ASP.NET 文件](/aspnet/#pivot=aspnet)。</span><span class="sxs-lookup"><span data-stu-id="57c34-128">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="57c34-129">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="57c34-129">ASP.NET Core</span></span>

<span data-ttu-id="57c34-130">ASP.NET 的跨平臺、高效能、開放原始碼的實作為。</span><span class="sxs-lookup"><span data-stu-id="57c34-130">A cross-platform, high-performance, open-source implementation of ASP.NET.</span></span>

<span data-ttu-id="57c34-131">請參閱 [ASP.NET Core 文件](/aspnet/#pivot=core)。</span><span class="sxs-lookup"><span data-stu-id="57c34-131">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="57c34-132">組件</span><span class="sxs-lookup"><span data-stu-id="57c34-132">assembly</span></span>

<span data-ttu-id="57c34-133">*.Dll* / *.exe* 檔，可包含可由應用程式或其他元件呼叫的 api 集合。</span><span class="sxs-lookup"><span data-stu-id="57c34-133">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="57c34-134">一個組件可以包含介面、類別、結構、列舉和委派等類型。</span><span class="sxs-lookup"><span data-stu-id="57c34-134">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="57c34-135">專案的 *bin* 資料夾中的組件有時稱為「二進位檔」。</span><span class="sxs-lookup"><span data-stu-id="57c34-135">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="57c34-136">另請參閱[程式庫](#library)。</span><span class="sxs-lookup"><span data-stu-id="57c34-136">See also [library](#library).</span></span>

## <a name="bcl"></a><span data-ttu-id="57c34-137">B c l</span><span class="sxs-lookup"><span data-stu-id="57c34-137">BCL</span></span>

<span data-ttu-id="57c34-138">基類庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-138">Base Class Library.</span></span>

<span data-ttu-id="57c34-139">組成系統的一組程式庫。 \* (以及 Microsoft 的範圍有限。 \*) 命名空間。</span><span class="sxs-lookup"><span data-stu-id="57c34-139">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="57c34-140">BCL 是 ASP.NET Core 等較高層級的應用程式架構建置所在之較低層級的一般目的架構。</span><span class="sxs-lookup"><span data-stu-id="57c34-140">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span>

<span data-ttu-id="57c34-141">.Net 5 (的 BCL 原始程式碼 [和 .Net Core) 和更新版本](#net-5-and-later-versions) 都包含在 [.net 運行](https://github.com/dotnet/runtime)時間存放庫中。</span><span class="sxs-lookup"><span data-stu-id="57c34-141">The source code of the BCL for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions) is contained in the [.NET runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="57c34-142">這些 BCL Api 大部分也都可在 .NET Framework 中使用，因此您可以將此原始程式碼視為 .NET Framework BCL 原始程式碼的分支。</span><span class="sxs-lookup"><span data-stu-id="57c34-142">The majority of these BCL APIs are also available in .NET Framework, so you can think of this source code as a fork of the .NET Framework BCL source code.</span></span>

<span data-ttu-id="57c34-143">下列詞彙通常會參考 BCL 所指的相同 Api 集合：</span><span class="sxs-lookup"><span data-stu-id="57c34-143">The following terms often refer to the same collection of APIs that BCL refers to:</span></span>

- [<span data-ttu-id="57c34-144">核心 .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="57c34-144">core .NET libraries</span></span>](../core/compatibility/3.1-5.0.md#core-net-libraries)
- [<span data-ttu-id="57c34-145">framework 程式庫</span><span class="sxs-lookup"><span data-stu-id="57c34-145">framework libraries</span></span>](#framework-libraries)
- [<span data-ttu-id="57c34-146">執行時間程式庫</span><span class="sxs-lookup"><span data-stu-id="57c34-146">runtime libraries</span></span>](#runtime)
- [<span data-ttu-id="57c34-147">共用架構</span><span class="sxs-lookup"><span data-stu-id="57c34-147">shared framework</span></span>](#shared-framework)

## <a name="clr"></a><span data-ttu-id="57c34-148">CLR</span><span class="sxs-lookup"><span data-stu-id="57c34-148">CLR</span></span>

<span data-ttu-id="57c34-149">Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="57c34-149">Common Language Runtime.</span></span>

<span data-ttu-id="57c34-150">確切的意義取決於內容。</span><span class="sxs-lookup"><span data-stu-id="57c34-150">The exact meaning depends on the context.</span></span> <span data-ttu-id="57c34-151">Common Language Runtime 通常是指 [.NET Framework](#net-framework) 的執行時間，或是 [.net 5 (和 .net Core) 和更新版本](#net-5-and-later-versions)的執行時間。</span><span class="sxs-lookup"><span data-stu-id="57c34-151">Common Language Runtime usually refers to the runtime of [.NET Framework](#net-framework) or the runtime of [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

<span data-ttu-id="57c34-152">CLR 會處理記憶體配置和管理。</span><span class="sxs-lookup"><span data-stu-id="57c34-152">A CLR handles memory allocation and management.</span></span> <span data-ttu-id="57c34-153">CLR 也是虛擬機器，不僅可執行應用程式，也會使用 [JIT](#jit) 編譯器來即時產生和編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="57c34-153">A CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span>

<span data-ttu-id="57c34-154">.NET Framework 的 CLR 實作為僅限 Windows。</span><span class="sxs-lookup"><span data-stu-id="57c34-154">The CLR implementation for .NET Framework is Windows only.</span></span>

<span data-ttu-id="57c34-155">適用于 .NET 5 和更新版本的 CLR 實 (也稱為核心 CLR) 是從與 .NET Framework CLR 相同的程式碼基底所建立。</span><span class="sxs-lookup"><span data-stu-id="57c34-155">The CLR implementation for .NET 5 and later versions (also known as the Core CLR) is built from the same code base as the .NET Framework CLR.</span></span> <span data-ttu-id="57c34-156">核心 CLR 原本是 Silverlight 的執行時間，其設計目的是要在多個平臺上執行，特別是 Windows 和 OS X。它仍然是一種 [跨平臺](#cross-platform) 的執行時間，現在包含許多 Linux 發行版本的支援。</span><span class="sxs-lookup"><span data-stu-id="57c34-156">Originally, the Core CLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span>

<span data-ttu-id="57c34-157">另請參閱 [運行](#runtime)時間。</span><span class="sxs-lookup"><span data-stu-id="57c34-157">See also [runtime](#runtime).</span></span>

## <a name="core-clr"></a><span data-ttu-id="57c34-158">核心 CLR</span><span class="sxs-lookup"><span data-stu-id="57c34-158">Core CLR</span></span>

<span data-ttu-id="57c34-159">適用于 [.net 5 (和 .Net Core) 和更新版本](#net-5-and-later-versions)的 Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="57c34-159">The Common Language Runtime for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

<span data-ttu-id="57c34-160">請參閱 [CLR](#clr)</span><span class="sxs-lookup"><span data-stu-id="57c34-160">See [CLR](#clr)</span></span>

## <a name="corert"></a><span data-ttu-id="57c34-161">CoreRT</span><span class="sxs-lookup"><span data-stu-id="57c34-161">CoreRT</span></span>

<span data-ttu-id="57c34-162">相較于 [CLR](#clr)，CoreRT 不是虛擬機器，這表示它不包含可即時產生和執行程式碼的功能，因為它不包含 [JIT](#jit)。</span><span class="sxs-lookup"><span data-stu-id="57c34-162">In contrast to the [CLR](#clr), CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="57c34-163">不過，它確實包含 [GC](#gc) ，以及執行時間類型識別 (RTTI) 和反映的能力。</span><span class="sxs-lookup"><span data-stu-id="57c34-163">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="57c34-164">不過，其型別系統已設計成不需要反映的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="57c34-164">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="57c34-165">不需要中繼資料可讓 [AOT](#aot) 工具鏈連結到多餘的中繼資料， (更重要的是) 識別應用程式未使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="57c34-165">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="57c34-166">CoreRT 正在開發中。</span><span class="sxs-lookup"><span data-stu-id="57c34-166">CoreRT is in development.</span></span>

<span data-ttu-id="57c34-167">請參閱 [.NET Native 和 CoreRT 簡介](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-167">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="57c34-168">跨平台</span><span class="sxs-lookup"><span data-stu-id="57c34-168">cross-platform</span></span>

<span data-ttu-id="57c34-169">開發和執行應用程式的能力，可用於多個不同的作業系統（例如 Linux、Windows 和 iOS），而不需要特別針對每個作業系統進行重寫。</span><span class="sxs-lookup"><span data-stu-id="57c34-169">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="57c34-170">這可讓您在不同平臺上的應用程式之間重複使用程式碼和一致性。</span><span class="sxs-lookup"><span data-stu-id="57c34-170">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="57c34-171">生態系統</span><span class="sxs-lookup"><span data-stu-id="57c34-171">ecosystem</span></span>

<span data-ttu-id="57c34-172">用來建置及執行適用於指定技術之應用程式的所有執行階段軟體、開發工具和社群資源。</span><span class="sxs-lookup"><span data-stu-id="57c34-172">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="57c34-173">「.NET 生態系統」一詞與「.NET 堆疊」等類似詞彙的不同之處在於，前者包含協力廠商應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-173">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="57c34-174">以下是用於句子中的範例：</span><span class="sxs-lookup"><span data-stu-id="57c34-174">Here's an example in a sentence:</span></span>

- <span data-ttu-id="57c34-175">「 [.NET Standard](#net-standard) 背後的動機是在 .net 生態系統中建立更高的一致性。」</span><span class="sxs-lookup"><span data-stu-id="57c34-175">"The motivation behind [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="57c34-176">架構</span><span class="sxs-lookup"><span data-stu-id="57c34-176">framework</span></span>

<span data-ttu-id="57c34-177">一般而言，一組功能齊全的 API 可加快開發和部署以特定技術為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-177">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="57c34-178">ASP.NET Core 和 Windows Forms 即為此一般意義的應用程式架構範例。</span><span class="sxs-lookup"><span data-stu-id="57c34-178">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="57c34-179">另請參閱[程式庫](#library)。</span><span class="sxs-lookup"><span data-stu-id="57c34-179">See also [library](#library).</span></span>

<span data-ttu-id="57c34-180">"Framework" 這個字在下列詞彙中有不同的意義：</span><span class="sxs-lookup"><span data-stu-id="57c34-180">The word "framework" has a different meaning in the following terms:</span></span>

- [<span data-ttu-id="57c34-181">framework 程式庫</span><span class="sxs-lookup"><span data-stu-id="57c34-181">framework libraries</span></span>](#framework-libraries)
- [<span data-ttu-id="57c34-182">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="57c34-182">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="57c34-183">共用架構</span><span class="sxs-lookup"><span data-stu-id="57c34-183">shared framework</span></span>](#shared-framework)
- [<span data-ttu-id="57c34-184">目標 framework</span><span class="sxs-lookup"><span data-stu-id="57c34-184">target framework</span></span>](#target-framework)
- [<span data-ttu-id="57c34-185">TFM (目標 Framework Moniker)</span><span class="sxs-lookup"><span data-stu-id="57c34-185">TFM (target framework moniker)</span></span>](#tfm)
- [<span data-ttu-id="57c34-186">與 framework 相依的應用程式</span><span class="sxs-lookup"><span data-stu-id="57c34-186">framework-dependent app</span></span>](../core/deploying/index.md#publish-framework-dependent)

<span data-ttu-id="57c34-187">有時「架構」是指 [.net 的實](#implementation-of-net)。</span><span class="sxs-lookup"><span data-stu-id="57c34-187">Sometimes "framework" refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="57c34-188">例如，文章可能會呼叫 .NET 5 架構。</span><span class="sxs-lookup"><span data-stu-id="57c34-188">For example, an article may call .NET 5 a framework.</span></span>

## <a name="framework-libraries"></a><span data-ttu-id="57c34-189">framework 程式庫</span><span class="sxs-lookup"><span data-stu-id="57c34-189">framework libraries</span></span>

<span data-ttu-id="57c34-190">意義取決於內容。</span><span class="sxs-lookup"><span data-stu-id="57c34-190">Meaning depends on context.</span></span> <span data-ttu-id="57c34-191">可能參考 .Net 5 的 framework 程式庫 [ (和 .Net Core) 和更新版本](#net-5-and-later-versions)，在此情況下，它會參考 [BCL](#bcl) 所參考的相同程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-191">May refer to the framework libraries for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions), in which case it refers to the same libraries that [BCL](#bcl) refers to.</span></span> <span data-ttu-id="57c34-192">它也可以參考 ASP.NET Core framework 程式庫，該程式庫是以 BCL 為依據，並為 web 應用程式提供額外的 Api。</span><span class="sxs-lookup"><span data-stu-id="57c34-192">It may also refer to the ASP.NET Core framework libraries, which build on the BCL and provide additional APIs for web apps.</span></span>

## <a name="gc"></a><span data-ttu-id="57c34-193">GC</span><span class="sxs-lookup"><span data-stu-id="57c34-193">GC</span></span>

<span data-ttu-id="57c34-194">記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="57c34-194">Garbage collector.</span></span>

<span data-ttu-id="57c34-195">記憶體回收行程是自動記憶體管理的實作。</span><span class="sxs-lookup"><span data-stu-id="57c34-195">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="57c34-196">GC 會釋放不再使用之物件所佔用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="57c34-196">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="57c34-197">請參閱[記憶體回收](garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-197">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="57c34-198">IL</span><span class="sxs-lookup"><span data-stu-id="57c34-198">IL</span></span>

<span data-ttu-id="57c34-199">中繼語言。</span><span class="sxs-lookup"><span data-stu-id="57c34-199">Intermediate language.</span></span>

<span data-ttu-id="57c34-200">較高階的 .NET 語言 (例如 C#) 可向下編譯成硬體無從驗證的指令集，稱為中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="57c34-200">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="57c34-201">IL 有時稱為 MSIL (Microsoft IL) 或 CIL (Common IL)。</span><span class="sxs-lookup"><span data-stu-id="57c34-201">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="57c34-202">JIT</span><span class="sxs-lookup"><span data-stu-id="57c34-202">JIT</span></span>

<span data-ttu-id="57c34-203">Just-in-Time 編譯器。</span><span class="sxs-lookup"><span data-stu-id="57c34-203">Just-in-time compiler.</span></span>

<span data-ttu-id="57c34-204">此編譯器類似於 [AOT](#aot)，會將 [IL](#il) 轉譯成處理器了解的機器碼。</span><span class="sxs-lookup"><span data-stu-id="57c34-204">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="57c34-205">不同於 AOT，JIT 編譯會視需要發生，而且會在必須執行程式碼的相同電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="57c34-205">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="57c34-206">由於 JIT 編譯會在應用程式執行期間發生，因此編譯時間會是執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="57c34-206">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="57c34-207">因此，JIT 編譯器必須在最佳化程式碼所花費的時間與結果程式碼可能省下的時間之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="57c34-207">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="57c34-208">但 JIT 知道實際硬體，因此開發人員不需要提供不同的實作。</span><span class="sxs-lookup"><span data-stu-id="57c34-208">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="57c34-209">.NET 實作</span><span class="sxs-lookup"><span data-stu-id="57c34-209">implementation of .NET</span></span>

<span data-ttu-id="57c34-210">.NET 的執行包括：</span><span class="sxs-lookup"><span data-stu-id="57c34-210">An implementation of .NET includes:</span></span>

- <span data-ttu-id="57c34-211">一或多個執行階段。</span><span class="sxs-lookup"><span data-stu-id="57c34-211">One or more runtimes.</span></span> <span data-ttu-id="57c34-212">範例： [CLR](#clr)、 [CoreRT](#corert)。</span><span class="sxs-lookup"><span data-stu-id="57c34-212">Examples: [CLR](#clr), [CoreRT](#corert).</span></span>
- <span data-ttu-id="57c34-213">.NET Standard 的類別庫，可執行版本的且可能包含其他 Api。</span><span class="sxs-lookup"><span data-stu-id="57c34-213">A class library that implements a version of .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="57c34-214">範例： [.NET Framework](#net-framework)和 .net 5 的[BCLs](#bcl) [ (和 .net Core) 和更新版本](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="57c34-214">Examples: the [BCLs](#bcl) for [.NET Framework](#net-framework) and [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>
- <span data-ttu-id="57c34-215">(選擇性) 一或多個應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="57c34-215">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="57c34-216">範例： [ASP.NET](#aspnet)、WINDOWS FORMS 和 WPF 包含在 .NET FRAMEWORK 和 .net 5 中。</span><span class="sxs-lookup"><span data-stu-id="57c34-216">Examples: [ASP.NET](#aspnet), Windows Forms, and WPF are included in the .NET Framework and .NET 5.</span></span>
- <span data-ttu-id="57c34-217">(選擇性) 開發工具。</span><span class="sxs-lookup"><span data-stu-id="57c34-217">Optionally, development tools.</span></span> <span data-ttu-id="57c34-218">某些開發工具可在多個實作之間共用。</span><span class="sxs-lookup"><span data-stu-id="57c34-218">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="57c34-219">.NET 實作的範例：</span><span class="sxs-lookup"><span data-stu-id="57c34-219">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="57c34-220">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="57c34-220">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="57c34-221">.NET 5 和更新版本 (包括 .NET Core 2.1-3.1) </span><span class="sxs-lookup"><span data-stu-id="57c34-221">.NET 5 and later versions (including .NET Core 2.1-3.1)</span></span>](#net-5-and-later-versions)
- [<span data-ttu-id="57c34-222">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="57c34-222">Universal Windows Platform (UWP)</span></span>](#uwp)
- [<span data-ttu-id="57c34-223">Mono</span><span class="sxs-lookup"><span data-stu-id="57c34-223">Mono</span></span>](#mono)

## <a name="library"></a><span data-ttu-id="57c34-224">圖書館</span><span class="sxs-lookup"><span data-stu-id="57c34-224">library</span></span>

<span data-ttu-id="57c34-225">可由應用程式或其他程式庫呼叫的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="57c34-225">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="57c34-226">.NET 程式庫是由一或多個[組件](#assembly)組成。</span><span class="sxs-lookup"><span data-stu-id="57c34-226">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="57c34-227">程式庫和[架構](#framework)等字在使用時通常同義。</span><span class="sxs-lookup"><span data-stu-id="57c34-227">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="mono"></a><span data-ttu-id="57c34-228">Mono</span><span class="sxs-lookup"><span data-stu-id="57c34-228">Mono</span></span>

<span data-ttu-id="57c34-229">Mono 是開放原始碼、[跨平台](#cross-platform)的 .NET 實作，主要用於需要小型執行階段時。</span><span class="sxs-lookup"><span data-stu-id="57c34-229">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="57c34-230">它是在 Android、Mac、iOS、tvOS 和 watchOS 上提供 Xamarin 應用程式的執行時間，主要著重于需要少量資源的應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-230">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="57c34-231">它支援目前發行的所有 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="57c34-231">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="57c34-232">在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。</span><span class="sxs-lookup"><span data-stu-id="57c34-232">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="57c34-233">它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-233">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="57c34-234">Mono 通常與 [即時編譯器](#jit)搭配使用，但也提供完整的 [靜態編譯器 (預先編譯) ](#aot) ，可在 iOS 等平臺上使用。</span><span class="sxs-lookup"><span data-stu-id="57c34-234">Mono is typically used with a [just-in-time compiler](#jit), but it also features a full [static compiler (ahead-of-time compilation)](#aot) that is used on platforms like iOS.</span></span>

<span data-ttu-id="57c34-235">請參閱 [Mono 檔](https://www.mono-project.com/docs/)。</span><span class="sxs-lookup"><span data-stu-id="57c34-235">See the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="57c34-236">.NET</span><span class="sxs-lookup"><span data-stu-id="57c34-236">.NET</span></span>

<span data-ttu-id="57c34-237">[.NET Standard](#net-standard) 以及所有 [.NET 實作](#implementation-of-net)和工作負載的籠統詞彙。</span><span class="sxs-lookup"><span data-stu-id="57c34-237">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="57c34-238">一律為完全大寫，絕對不會是 ".Net"。</span><span class="sxs-lookup"><span data-stu-id="57c34-238">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="57c34-239">當 [.net 5](#net-5-and-later-versions) (目前處於) 預覽狀態時，系統會針對所有新的 .net 開發建議使用 .net，因此在某些內容中，".net" 將表示「.net 5 和更新版本」。</span><span class="sxs-lookup"><span data-stu-id="57c34-239">When [.NET 5](#net-5-and-later-versions) (currently in preview) is released, it will be the recommended .NET implementation for all new .NET development, and so in some contexts ".NET" will imply ".NET 5 and later versions."</span></span>

<span data-ttu-id="57c34-240">查看 [.net 基礎](../fundamentals/index.yml)</span><span class="sxs-lookup"><span data-stu-id="57c34-240">See [.NET fundamentals](../fundamentals/index.yml)</span></span>

## <a name="net-5-and-later-versions"></a><span data-ttu-id="57c34-241">.NET 5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="57c34-241">.NET 5 and later versions</span></span>

<span data-ttu-id="57c34-242">.NET 的跨平臺、高效能、開放原始碼的實作為。</span><span class="sxs-lookup"><span data-stu-id="57c34-242">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="57c34-243">包括 Common Language Runtime ([CLR](#clr)) 、 ([CoreRT](#corert)的[AOT](#aot)執行時間、開發) 、基類庫 ([BCL](#bcl)) 和[.net SDK](#net-sdk)。</span><span class="sxs-lookup"><span data-stu-id="57c34-243">Includes a Common Language Runtime ([CLR](#clr)), an [AOT](#aot) runtime ([CoreRT](#corert), in development), a Base Class Library ([BCL](#bcl)), and the [.NET SDK](#net-sdk).</span></span>

<span data-ttu-id="57c34-244">此 .NET 實作為較早的版本，稱為 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="57c34-244">Earlier versions of this .NET implementation are known as .NET Core.</span></span> <span data-ttu-id="57c34-245">.NET 5.0 是 .NET Core 3.1 之後的下一版。</span><span class="sxs-lookup"><span data-stu-id="57c34-245">.NET 5.0 is the next version following .NET Core 3.1.</span></span> <span data-ttu-id="57c34-246">已略過第4版，以避免使用較舊的實作為（稱為 [.NET Framework](#net-framework)）來混淆這項較新的 .net 執行。</span><span class="sxs-lookup"><span data-stu-id="57c34-246">Version 4 was skipped to avoid confusing this newer implementation of .NET with the older implementation that is known as [.NET Framework](#net-framework).</span></span> <span data-ttu-id="57c34-247">.NET Framework 目前的版本為4.8。</span><span class="sxs-lookup"><span data-stu-id="57c34-247">The current version of .NET Framework is 4.8.</span></span>

<span data-ttu-id="57c34-248">請參閱 [.net 基本](../fundamentals/index.yml)概念。</span><span class="sxs-lookup"><span data-stu-id="57c34-248">See [.NET fundamentals](../fundamentals/index.yml).</span></span>

## <a name="net-cli"></a><span data-ttu-id="57c34-249">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="57c34-249">.NET CLI</span></span>

<span data-ttu-id="57c34-250">適用于開發 [.net 5 (和 .Net Core) 和更新版本](#net-5-and-later-versions)之應用程式和程式庫的跨平臺工具鏈。</span><span class="sxs-lookup"><span data-stu-id="57c34-250">A cross-platform toolchain for developing applications and libraries for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span> <span data-ttu-id="57c34-251">也稱為 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="57c34-251">Also known as the .NET Core CLI.</span></span>

<span data-ttu-id="57c34-252">請參閱 [.NET CLI](../core/tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-252">See [.NET CLI](../core/tools/index.md).</span></span>

## <a name="net-core"></a><span data-ttu-id="57c34-253">.NET Core</span><span class="sxs-lookup"><span data-stu-id="57c34-253">.NET Core</span></span>

<span data-ttu-id="57c34-254">請參閱 [.net 5 和更新版本](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="57c34-254">See [.NET 5 and later versions](#net-5-and-later-versions).</span></span>

## <a name="net-framework"></a><span data-ttu-id="57c34-255">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="57c34-255">.NET Framework</span></span>

<span data-ttu-id="57c34-256">只會在 Windows 上執行的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="57c34-256">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="57c34-257">包括 Common Language Runtime ([CLR](#clr)) 、基類庫 ([BCL](#bcl)) 和應用程式架構程式庫（例如 [ASP.NET](#aspnet)、Windows Forms 和 WPF）。</span><span class="sxs-lookup"><span data-stu-id="57c34-257">Includes the Common Language Runtime ([CLR](#clr)), the Base Class Library ([BCL](#bcl)), and application framework libraries such as [ASP.NET](#aspnet), Windows Forms, and WPF.</span></span>

<span data-ttu-id="57c34-258">請參閱 [.NET Framework 指南](../framework/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="57c34-258">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="57c34-259">.NET Native</span><span class="sxs-lookup"><span data-stu-id="57c34-259">.NET Native</span></span>

<span data-ttu-id="57c34-260">產生原生程式碼提前 ([AOT](#aot)) 的編譯器工具鏈，而非即時 ([JIT](#jit)) 。</span><span class="sxs-lookup"><span data-stu-id="57c34-260">A compiler tool chain that produces native code ahead-of-time ([AOT](#aot)), as opposed to just-in-time ([JIT](#jit)).</span></span>

<span data-ttu-id="57c34-261">編譯會在開發人員的電腦上發生，其運作方式類似於 C++ 編譯器和連結器。</span><span class="sxs-lookup"><span data-stu-id="57c34-261">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="57c34-262">它會移除未使用的程式碼，並花更多時間在最佳化。</span><span class="sxs-lookup"><span data-stu-id="57c34-262">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="57c34-263">它會從程式庫擷取程式碼，並將其合併成可執行檔。</span><span class="sxs-lookup"><span data-stu-id="57c34-263">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="57c34-264">結果會是代表整個應用程式的單一模組。</span><span class="sxs-lookup"><span data-stu-id="57c34-264">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="57c34-265">UWP 是 .NET Native 第一個支援的應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="57c34-265">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="57c34-266">現在，我們支援建置適用於 Windows、macOS 和 Linux 的原生主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-266">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="57c34-267">請參閱 [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) (.NET Native 和 CoreRT 簡介)</span><span class="sxs-lookup"><span data-stu-id="57c34-267">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-sdk"></a><span data-ttu-id="57c34-268">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="57c34-268">.NET SDK</span></span>

<span data-ttu-id="57c34-269">一組程式庫和工具，可讓開發人員建立 .net [5 (和 .Net Core) 和更新版本](#net-5-and-later-versions)的 .net 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-269">A set of libraries and tools that allow developers to create .NET applications and libraries for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span> <span data-ttu-id="57c34-270">也稱為 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="57c34-270">Also known as the .NET Core SDK.</span></span>

<span data-ttu-id="57c34-271">包含用來建立應用程式的 [.NET CLI](#net-cli) 、用來建立和執行應用程式的 .net 程式庫和執行時間，以及 dotnet 可執行檔 (*dotnet.exe* 執行 CLI 命令和執行應用程式的) 。</span><span class="sxs-lookup"><span data-stu-id="57c34-271">Includes the [.NET CLI](#net-cli) for building apps, .NET libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="57c34-272">請參閱 [.NET SDK 總覽](../core/sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-272">See [.NET SDK Overview](../core/sdk.md).</span></span>

## <a name="net-standard"></a><span data-ttu-id="57c34-273">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="57c34-273">.NET Standard</span></span>

<span data-ttu-id="57c34-274">可用於每個 .NET 實作之 .NET API 的型式規格。</span><span class="sxs-lookup"><span data-stu-id="57c34-274">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="57c34-275">.NET Standard 規格在文件中有時稱為程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-275">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="57c34-276">由於程式庫不只包含規格 (介面)，還包含 API 實作，因此將 .NET Standard 稱為「程式庫」會造成誤導。</span><span class="sxs-lookup"><span data-stu-id="57c34-276">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span>

<span data-ttu-id="57c34-277">請參閱 [.NET Standard](net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-277">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="57c34-278">NGEN</span><span class="sxs-lookup"><span data-stu-id="57c34-278">NGEN</span></span>

<span data-ttu-id="57c34-279">原生 (映像) 產生。</span><span class="sxs-lookup"><span data-stu-id="57c34-279">Native (image) generation.</span></span>

<span data-ttu-id="57c34-280">您可以將這項技術視為持續性 [JIT](#jit) 編譯器。</span><span class="sxs-lookup"><span data-stu-id="57c34-280">You can think of this technology as a persistent [JIT](#jit) compiler.</span></span> <span data-ttu-id="57c34-281">它通常會在執行程式碼的電腦上編譯程式碼，但編譯通常會發生在安裝期間。</span><span class="sxs-lookup"><span data-stu-id="57c34-281">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="57c34-282">套件</span><span class="sxs-lookup"><span data-stu-id="57c34-282">package</span></span>

<span data-ttu-id="57c34-283">NuGet 套件 (簡稱套件) 是 *.zip* 檔案，其中包含一或多個同名組件及其他中繼資料 (例如作者名稱)。</span><span class="sxs-lookup"><span data-stu-id="57c34-283">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="57c34-284">*.zip* 檔案包含一個 *.nupkg* 延伸模組和許多特定資產 (例如 *.dll* 檔案和 *.xml* 檔案)，可搭配多個架構和版本使用。</span><span class="sxs-lookup"><span data-stu-id="57c34-284">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="57c34-285">安裝於應用程式或程式庫時，會根據應用程式或程式庫所指定的目標 Framework 來選取適當的資產。</span><span class="sxs-lookup"><span data-stu-id="57c34-285">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="57c34-286">定義介面的資產位於 *ref* 資料夾中，而定義實作的資產則位於 *lib* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="57c34-286">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="57c34-287">平台</span><span class="sxs-lookup"><span data-stu-id="57c34-287">platform</span></span>

<span data-ttu-id="57c34-288">作業系統及其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。</span><span class="sxs-lookup"><span data-stu-id="57c34-288">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="57c34-289">以下是用於句子中的範例：</span><span class="sxs-lookup"><span data-stu-id="57c34-289">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="57c34-290">「.NET Core 是 .NET 的跨平台實作。」</span><span class="sxs-lookup"><span data-stu-id="57c34-290">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="57c34-291">「PCL 設定檔代表 Microsoft 平臺，而 .NET Standard 與平臺無關」。</span><span class="sxs-lookup"><span data-stu-id="57c34-291">"PCL profiles represent Microsoft platforms, while .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="57c34-292">舊版 .NET 檔有時會使用 ".NET platform" 來表示 .NET 或 .NET [stack](#stack)的執行，包括所有[的實](#implementation-of-net)作為。</span><span class="sxs-lookup"><span data-stu-id="57c34-292">Legacy .NET documentation sometimes uses ".NET platform" to mean either an [implementation of .NET](#implementation-of-net) or the .NET [stack](#stack) including all implementations.</span></span> <span data-ttu-id="57c34-293">這兩種使用方式通常會與主要 (作業系統/硬體) 含意混淆，因此我們會嘗試避免這些使用方式。</span><span class="sxs-lookup"><span data-stu-id="57c34-293">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we try to avoid these usages.</span></span>

<span data-ttu-id="57c34-294">「平臺」在「開發人員平臺」一詞中有不同的意義，這是指提供建立和執行應用程式之工具和程式庫的軟體。</span><span class="sxs-lookup"><span data-stu-id="57c34-294">"Platform" has a different meaning in the phrase "developer platform," which refers to software that provides tools and libraries for building and running apps.</span></span> <span data-ttu-id="57c34-295">.NET 是一種跨平臺的開放原始碼開發人員平臺，可用於建立許多不同類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-295">.NET is a cross-platform, open source developer platform for building many different types of applications.</span></span>

## <a name="runtime"></a><span data-ttu-id="57c34-296">執行階段</span><span class="sxs-lookup"><span data-stu-id="57c34-296">runtime</span></span>

<span data-ttu-id="57c34-297">一般情況下，受管理程式的執行環境。</span><span class="sxs-lookup"><span data-stu-id="57c34-297">In general, the execution environment for a managed program.</span></span> <span data-ttu-id="57c34-298">OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="57c34-298">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="57c34-299">以下是 .NET 執行時間的一些範例：</span><span class="sxs-lookup"><span data-stu-id="57c34-299">Here are some examples of .NET runtimes in this sense of the word:</span></span>

- <span data-ttu-id="57c34-300">Common Language Runtime ([CLR](#clr)) </span><span class="sxs-lookup"><span data-stu-id="57c34-300">Common Language Runtime ([CLR](#clr))</span></span>
- <span data-ttu-id="57c34-301">.NET Native (適用於 UWP)</span><span class="sxs-lookup"><span data-stu-id="57c34-301">.NET Native (for UWP)</span></span>
- <span data-ttu-id="57c34-302">Mono 執行階段</span><span class="sxs-lookup"><span data-stu-id="57c34-302">Mono runtime</span></span>

<span data-ttu-id="57c34-303">「執行時間」一詞在某些內容中有不同的意義：</span><span class="sxs-lookup"><span data-stu-id="57c34-303">The word "runtime" has a different meaning in some contexts:</span></span>

* <span data-ttu-id="57c34-304">[.Net 5.0 下載頁面](https://dotnet.microsoft.com/download/dotnet/5.0)上的 *.net 運行* 時間。</span><span class="sxs-lookup"><span data-stu-id="57c34-304">*.NET runtime* on the [.NET 5.0 download page](https://dotnet.microsoft.com/download/dotnet/5.0).</span></span>

  <span data-ttu-id="57c34-305">您可以下載 *.net 運行* 時間或其他執行時間，例如 *ASP.NET Core 運行* 時間。</span><span class="sxs-lookup"><span data-stu-id="57c34-305">You can download the *.NET runtime* or other runtimes, such as the *ASP.NET Core runtime*.</span></span> <span data-ttu-id="57c34-306">此使用方式中的 *運行* 時間是一組必須安裝在電腦上的元件，以便在電腦上執行與 [framework 相依](../core/deploying/index.md#publish-framework-dependent) 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-306">A *runtime* in this usage is the set of components that must be installed on a machine to run a [framework-dependent](../core/deploying/index.md#publish-framework-dependent) app on the machine.</span></span> <span data-ttu-id="57c34-307">.NET 執行時間包含可提供[BCL](#bcl)的[CLR](#clr)和 .net[共用架構](#shared-framework)。</span><span class="sxs-lookup"><span data-stu-id="57c34-307">The .NET runtime includes the [CLR](#clr) and the .NET [shared framework](#shared-framework), which provides the [BCL](#bcl).</span></span>

* <span data-ttu-id="57c34-308">*.NET 執行時間程式庫*</span><span class="sxs-lookup"><span data-stu-id="57c34-308">*.NET runtime libraries*</span></span>

  <span data-ttu-id="57c34-309">參考 [BCL](#bcl) 所參考的相同程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-309">Refers to the same libraries that [BCL](#bcl) refers to.</span></span> <span data-ttu-id="57c34-310">不過，其他執行時間（例如 ASP.NET Core 執行時間）會有不同的 [共用](#shared-framework)架構，以及在 BCL 上建立的其他程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-310">However, other runtimes, such as the ASP.NET Core runtime, have different [shared frameworks](#shared-framework), with additional libraries that build on the BCL.</span></span>

* <span data-ttu-id="57c34-311">[ (RID) 的執行時間識別碼 ](../core/rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-311">[Runtime Identifier (RID)](../core/rid-catalog.md).</span></span>

  <span data-ttu-id="57c34-312">這裡的 *運行* 時程表示 .net 應用程式執行所在的作業系統平臺和 CPU 架構，例如： `linux-x64` 。</span><span class="sxs-lookup"><span data-stu-id="57c34-312">*Runtime* here means the OS platform and CPU architecture that a .NET app runs on, for example: `linux-x64`.</span></span>

* <span data-ttu-id="57c34-313">有時會使用 "runtime" 來瞭解 [.net 的執行](#implementation-of-net)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="57c34-313">Sometimes "runtime" is used in the sense of an [implementation of .NET](#implementation-of-net), as in the following examples:</span></span>

  - <span data-ttu-id="57c34-314">「不同的 .NET 執行階段會實作特定版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="57c34-314">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="57c34-315">…</span><span class="sxs-lookup"><span data-stu-id="57c34-315">…</span></span> <span data-ttu-id="57c34-316">每個 .NET 執行階段版本會宣佈它所支援的最高 .NET Standard 版本...」</span><span class="sxs-lookup"><span data-stu-id="57c34-316">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>
  - <span data-ttu-id="57c34-317">「要在多個執行階段上執行的程式庫應以此架構為目標。」</span><span class="sxs-lookup"><span data-stu-id="57c34-317">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="57c34-318">(指的是 .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="57c34-318">(referring to .NET Standard)</span></span>

## <a name="shared-framework"></a><span data-ttu-id="57c34-319">共用架構</span><span class="sxs-lookup"><span data-stu-id="57c34-319">shared framework</span></span>

<span data-ttu-id="57c34-320">意義取決於內容。</span><span class="sxs-lookup"><span data-stu-id="57c34-320">Meaning depends on context.</span></span> <span data-ttu-id="57c34-321">*.Net 共用架構* 是指 [.net 運行](#runtime)時間中包含的程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-321">The *.NET shared framework* refers to the libraries included in the [.NET runtime](#runtime).</span></span> <span data-ttu-id="57c34-322">在此情況下，適用于 .Net 5 的 *共用架構* [ (和 .net Core) 和更新版本](#net-5-and-later-versions) 會參考 [BCL](#bcl) 所參考的相同程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-322">In this case, the *shared framework* for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions) refers to the same libraries that [BCL](#bcl) refers to.</span></span>

<span data-ttu-id="57c34-323">還有其他共用架構。</span><span class="sxs-lookup"><span data-stu-id="57c34-323">There are other shared frameworks.</span></span> <span data-ttu-id="57c34-324">*ASP.NET Core 共用架構* 是指包含在 [ASP.NET Core 運行](#runtime)時間中的程式庫，其中包含 BCL 加上 web Apps 使用的其他 api。</span><span class="sxs-lookup"><span data-stu-id="57c34-324">The *ASP.NET Core shared framework* refers to the libraries included in the [ASP.NET Core runtime](#runtime), which includes the BCL plus additional APIs for use by web apps.</span></span>

<span data-ttu-id="57c34-325">針對與 [framework 相依的應用程式](../core/deploying/index.md#publish-framework-dependent)，共用架構包含在執行應用程式之電腦上的資料夾中所安裝之元件的程式庫。</span><span class="sxs-lookup"><span data-stu-id="57c34-325">For [framework-dependent apps](../core/deploying/index.md#publish-framework-dependent), the shared framework consists of libraries that are contained in assemblies installed in a folder on the machine that runs the app.</span></span> <span data-ttu-id="57c34-326">針對獨立式 [應用](../core/deploying/index.md#publish-self-contained)程式，共用架構元件會隨附于應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-326">For [self-contained apps](../core/deploying/index.md#publish-self-contained), the shared framework assemblies are included with the app.</span></span>

<span data-ttu-id="57c34-327">如需詳細資訊，請參閱 [.Net Core 基本專案的深入探討，第2部分：共用架構](https://natemcmaster.com/blog/2018/08/29/netcore-primitives-2/)。</span><span class="sxs-lookup"><span data-stu-id="57c34-327">For more information, see [Deep-dive into .NET Core primitives, part 2: the shared framework](https://natemcmaster.com/blog/2018/08/29/netcore-primitives-2/).</span></span>

## <a name="stack"></a><span data-ttu-id="57c34-328">堆疊</span><span class="sxs-lookup"><span data-stu-id="57c34-328">stack</span></span>

<span data-ttu-id="57c34-329">可搭配使用以建置及執行應用程式的一組程式設計技術。</span><span class="sxs-lookup"><span data-stu-id="57c34-329">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="57c34-330">「.NET stack」指的是 .NET Standard 和所有的 .NET 執行。</span><span class="sxs-lookup"><span data-stu-id="57c34-330">"The .NET stack" refers to .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="57c34-331">「一個 .NET 堆疊」一詞可能是指 .NET 的一項實作。</span><span class="sxs-lookup"><span data-stu-id="57c34-331">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="57c34-332">Target Framework - 目標 Framework</span><span class="sxs-lookup"><span data-stu-id="57c34-332">target framework</span></span>

<span data-ttu-id="57c34-333">.NET 應用程式或程式庫依賴的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="57c34-333">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="57c34-334">應用程式或程式庫可以將目標設為某個版本的 .NET Standard (例如 .NET Standard 2.0) ，這是一組標準化的 Api，適用于所有 .NET 執行。</span><span class="sxs-lookup"><span data-stu-id="57c34-334">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is a specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="57c34-335">應用程式或程式庫也可以將目標設為某個版本的特定 .NET 實作；在此情況下，它可以存取實作特定的 API。</span><span class="sxs-lookup"><span data-stu-id="57c34-335">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="57c34-336">例如，以 Xamarin.iOS 為目標的應用程式可以存取 Xamarin 提供的 iOS API 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="57c34-336">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="57c34-337">針對某些目標 Framework (例如 .NET Framework)，可用的 API 是由 .NET 實作安裝在系統上的組件所定義，這可能包含應用程式架構 API (例如 ASP.NET、WinForms)。</span><span class="sxs-lookup"><span data-stu-id="57c34-337">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="57c34-338">針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，架構 API 是由安裝在應用程式或程式庫中的套件所定義。</span><span class="sxs-lookup"><span data-stu-id="57c34-338">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="57c34-339">在此情況下，目標架構會隱含地指定參考所有封裝的封裝，這些封裝會組成架構。</span><span class="sxs-lookup"><span data-stu-id="57c34-339">In that case, the target framework implicitly specifies a package that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="57c34-340">請參閱[目標 Framework](frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-340">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="57c34-341">TFM</span><span class="sxs-lookup"><span data-stu-id="57c34-341">TFM</span></span>

<span data-ttu-id="57c34-342">目標 Framework Moniker。</span><span class="sxs-lookup"><span data-stu-id="57c34-342">Target framework moniker.</span></span>

<span data-ttu-id="57c34-343">用於指定 .NET 應用程式或程式庫之目標 Framework 的標準化語彙基元格式。</span><span class="sxs-lookup"><span data-stu-id="57c34-343">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="57c34-344">目標 Framework 通常會由簡短名稱參考，例如 `net462`。</span><span class="sxs-lookup"><span data-stu-id="57c34-344">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="57c34-345">雖然有完整格式的 TFM (例如 .NETFramework,Version=4.6.2)，但通常不會用來指定目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="57c34-345">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="57c34-346">請參閱[目標 Framework](frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="57c34-346">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="57c34-347">UWP</span><span class="sxs-lookup"><span data-stu-id="57c34-347">UWP</span></span>

<span data-ttu-id="57c34-348">通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="57c34-348">Universal Windows Platform.</span></span>

<span data-ttu-id="57c34-349">用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="57c34-349">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="57c34-350">它是設計來統一您可能想要鎖定的不同裝置類型，包括電腦、平板電腦、手機，甚至是 Xbox。</span><span class="sxs-lookup"><span data-stu-id="57c34-350">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="57c34-351">UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。</span><span class="sxs-lookup"><span data-stu-id="57c34-351">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="57c34-352">您可以用 c + +、c #、Visual Basic 和 JavaScript 來撰寫應用程式。</span><span class="sxs-lookup"><span data-stu-id="57c34-352">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="57c34-353">使用 c # 和 Visual Basic 時，.net Api 是由 .NET 5 (和 .NET Core) 和更新版本所提供。</span><span class="sxs-lookup"><span data-stu-id="57c34-353">When using C# and Visual Basic, the .NET APIs are provided by .NET 5 (and .NET Core) and later versions.</span></span>

## <a name="workload"></a><span data-ttu-id="57c34-354">workload</span><span class="sxs-lookup"><span data-stu-id="57c34-354">workload</span></span>

<span data-ttu-id="57c34-355">某人正在建立的應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="57c34-355">A type of app someone is building.</span></span> <span data-ttu-id="57c34-356">更通用於 [應用程式模型](#app-model)。</span><span class="sxs-lookup"><span data-stu-id="57c34-356">More generic than [app model](#app-model).</span></span> <span data-ttu-id="57c34-357">例如，在每個 .NET 檔頁面的頂端（包括此頁面）是 **工作負載** 的下拉式清單，可讓您切換至 **Web** **、行動**、 **雲端**、 **桌面** 和 **Machine Learning \& 資料** 的檔。</span><span class="sxs-lookup"><span data-stu-id="57c34-357">For example, at the top of every .NET documentation page, including this one, is a drop-down list for **Workloads**, which lets you switch to documentation for **Web**, **Mobile**, **Cloud**, **Desktop**, and **Machine Learning \& Data**.</span></span>

<span data-ttu-id="57c34-358">在某些內容中， *工作負載* 是指您可以選擇安裝以支援特定應用程式類型的 Visual Studio 功能集合。</span><span class="sxs-lookup"><span data-stu-id="57c34-358">In some contexts, *workload* refers to a collection of Visual Studio features that you can choose to install to support a particular type of app.</span></span> <span data-ttu-id="57c34-359">如需範例，請參閱 [選取工作負載](../core/install/windows.md#select-a-workload)。</span><span class="sxs-lookup"><span data-stu-id="57c34-359">For an example, see [Select a workload](../core/install/windows.md#select-a-workload).</span></span>

## <a name="see-also"></a><span data-ttu-id="57c34-360">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57c34-360">See also</span></span>

- [<span data-ttu-id="57c34-361">.NET 基本概念</span><span class="sxs-lookup"><span data-stu-id="57c34-361">.NET fundamentals</span></span>](../fundamentals/index.yml)
- [<span data-ttu-id="57c34-362">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="57c34-362">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="57c34-363">ASP.NET 總覽</span><span class="sxs-lookup"><span data-stu-id="57c34-363">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="57c34-364">ASP.NET Core 總覽</span><span class="sxs-lookup"><span data-stu-id="57c34-364">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
