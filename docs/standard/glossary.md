---
title: .NET 字彙表
description: 了解 .NET 文件中所使用之特定詞彙的意義。
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: c984a29208d8680de3c04f6b4d16c6f41afedc71
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812337"
---
# <a name="net-glossary"></a><span data-ttu-id="a358d-103">.NET 字彙表</span><span class="sxs-lookup"><span data-stu-id="a358d-103">.NET Glossary</span></span>

<span data-ttu-id="a358d-104">此字彙表的主要目標是釐清經常出現在 .NET 文件中但沒有定義之特定詞彙和縮略字的意義。</span><span class="sxs-lookup"><span data-stu-id="a358d-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="a358d-105">AOT</span><span class="sxs-lookup"><span data-stu-id="a358d-105">AOT</span></span>

<span data-ttu-id="a358d-106">預先編譯器。</span><span class="sxs-lookup"><span data-stu-id="a358d-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="a358d-107">此編譯器類似於 [JIT](#jit)，也會將 [IL](#il) 轉譯成機器碼。</span><span class="sxs-lookup"><span data-stu-id="a358d-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="a358d-108">相較於 JIT 編譯，AOT 編譯會在執行應用程式之前發生，而且通常會在不同的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="a358d-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="a358d-109">因為 AOT 工具鏈不會在執行時間編譯，所以不需要將編譯花費的時間降到最低。</span><span class="sxs-lookup"><span data-stu-id="a358d-109">Because AOT tool chains don't compile at run time, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="a358d-110">這表示它們可以花更多的時間在最佳化。</span><span class="sxs-lookup"><span data-stu-id="a358d-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="a358d-111">由於 AOT 的內容是整個應用程式，因此 AOT 編譯器也會執行跨模組連結和整個程式分析，這表示會追蹤所有參考並產生單一可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a358d-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="a358d-112">請參閱 [CoreRT](#corert) 及 [.NET Native](#net-native)。</span><span class="sxs-lookup"><span data-stu-id="a358d-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="a358d-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a358d-113">ASP.NET</span></span>

<span data-ttu-id="a358d-114">隨附於 .NET Framework 的原始 ASP.NET 實作。</span><span class="sxs-lookup"><span data-stu-id="a358d-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="a358d-115">有時 ASP.NET 是指包括 ASP.NET Core 在內之兩個 ASP.NET 實作的籠統名詞。</span><span class="sxs-lookup"><span data-stu-id="a358d-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="a358d-116">該詞彙在任何指定的執行個體中所代表的意義取決於內容。</span><span class="sxs-lookup"><span data-stu-id="a358d-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="a358d-117">如果您想要清楚說您不是使用 ASP.NET 來表示這兩個執行，請參閱 ASP.NET 4.x。</span><span class="sxs-lookup"><span data-stu-id="a358d-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="a358d-118">請參閱 [ASP.NET 文件](/aspnet/#pivot=aspnet)。</span><span class="sxs-lookup"><span data-stu-id="a358d-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="a358d-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a358d-119">ASP.NET Core</span></span>

<span data-ttu-id="a358d-120">ASP.NET 的跨平臺、高效能、開放原始碼的實作為。</span><span class="sxs-lookup"><span data-stu-id="a358d-120">A cross-platform, high-performance, open-source implementation of ASP.NET.</span></span>

<span data-ttu-id="a358d-121">請參閱 [ASP.NET Core 文件](/aspnet/#pivot=core)。</span><span class="sxs-lookup"><span data-stu-id="a358d-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="a358d-122">組件 (assembly)</span><span class="sxs-lookup"><span data-stu-id="a358d-122">assembly</span></span>

<span data-ttu-id="a358d-123">*.Dll* / *.exe*檔，可包含可由應用程式或其他元件呼叫的 api 集合。</span><span class="sxs-lookup"><span data-stu-id="a358d-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="a358d-124">一個組件可以包含介面、類別、結構、列舉和委派等類型。</span><span class="sxs-lookup"><span data-stu-id="a358d-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="a358d-125">專案的 *bin* 資料夾中的組件有時稱為「二進位檔」\*\*。</span><span class="sxs-lookup"><span data-stu-id="a358d-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="a358d-126">另請參閱[程式庫](#library)。</span><span class="sxs-lookup"><span data-stu-id="a358d-126">See also [library](#library).</span></span>

## <a name="bcl"></a><span data-ttu-id="a358d-127">B c l</span><span class="sxs-lookup"><span data-stu-id="a358d-127">BCL</span></span>

<span data-ttu-id="a358d-128">基類庫。</span><span class="sxs-lookup"><span data-stu-id="a358d-128">Base Class Library.</span></span> <span data-ttu-id="a358d-129">也稱為 *架構程式庫*。</span><span class="sxs-lookup"><span data-stu-id="a358d-129">Also known as *framework libraries*.</span></span>

<span data-ttu-id="a358d-130">組成系統的一組程式庫。 \* (以及 Microsoft 的範圍有限。 \*) 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a358d-130">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="a358d-131">BCL 是 ASP.NET Core 等較高層級的應用程式架構建置所在之較低層級的一般目的架構。</span><span class="sxs-lookup"><span data-stu-id="a358d-131">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span>

<span data-ttu-id="a358d-132">.Net [5 和更新版本的 BCL 原始程式碼 (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions) 包含在 [.net 運行](https://github.com/dotnet/runtime)時間存放庫中。</span><span class="sxs-lookup"><span data-stu-id="a358d-132">The source code of the BCL for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions) is contained in the [.NET runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="a358d-133">這項較新的 .NET 執行的 BCL Api 大部分也都可在 .NET Framework 中使用，因此您可以將此原始程式碼視為 .NET Framework BCL 原始程式碼的分支。</span><span class="sxs-lookup"><span data-stu-id="a358d-133">The majority of the BCL APIs for this newer implementation of .NET are also available in .NET Framework, so you can think of this source code as a fork of the .NET Framework BCL source code.</span></span>

## <a name="clr"></a><span data-ttu-id="a358d-134">CLR</span><span class="sxs-lookup"><span data-stu-id="a358d-134">CLR</span></span>

<span data-ttu-id="a358d-135">Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="a358d-135">Common Language Runtime.</span></span>

<span data-ttu-id="a358d-136">確切的意義取決於內容。</span><span class="sxs-lookup"><span data-stu-id="a358d-136">The exact meaning depends on the context.</span></span> <span data-ttu-id="a358d-137">Common Language Runtime 通常是指 [.NET Framework](#net-framework) 的執行時間或 [.net 5 和更新版本的執行時間 (包括 .net Core 2.1-3.1) ](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="a358d-137">Common Language Runtime usually refers to the runtime of [.NET Framework](#net-framework) or the runtime of [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>

<span data-ttu-id="a358d-138">CLR 會處理記憶體配置和管理。</span><span class="sxs-lookup"><span data-stu-id="a358d-138">A CLR handles memory allocation and management.</span></span> <span data-ttu-id="a358d-139">CLR 也是虛擬機器，不僅可執行應用程式，也會使用 [JIT](#jit) 編譯器來即時產生和編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="a358d-139">A CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span>

<span data-ttu-id="a358d-140">.NET Framework 的 CLR 實作為僅限 Windows。</span><span class="sxs-lookup"><span data-stu-id="a358d-140">The CLR implementation for .NET Framework is Windows only.</span></span>

<span data-ttu-id="a358d-141">適用于 .NET 5 和更新版本的 CLR 實 (也稱為核心 CLR) 是從與 .NET Framework CLR 相同的程式碼基底所建立。</span><span class="sxs-lookup"><span data-stu-id="a358d-141">The CLR implementation for .NET 5 and later versions (also known as the Core CLR) is built from the same code base as the .NET Framework CLR.</span></span> <span data-ttu-id="a358d-142">核心 CLR 原本是 Silverlight 的執行時間，其設計目的是要在多個平臺上執行，特別是 Windows 和 OS X。它仍然是一種 [跨平臺](#cross-platform) 的執行時間，現在包含許多 Linux 發行版本的支援。</span><span class="sxs-lookup"><span data-stu-id="a358d-142">Originally, the Core CLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span>

<span data-ttu-id="a358d-143">另請參閱 [運行](#runtime)時間。</span><span class="sxs-lookup"><span data-stu-id="a358d-143">See also [runtime](#runtime).</span></span>

## <a name="core-clr"></a><span data-ttu-id="a358d-144">核心 CLR</span><span class="sxs-lookup"><span data-stu-id="a358d-144">Core CLR</span></span>

<span data-ttu-id="a358d-145">適用于 [.net 5 和更新版本的 Common Language Runtime (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="a358d-145">The Common Language Runtime for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>

<span data-ttu-id="a358d-146">請參閱 [CLR](#clr)</span><span class="sxs-lookup"><span data-stu-id="a358d-146">See [CLR](#clr)</span></span>

## <a name="corert"></a><span data-ttu-id="a358d-147">CoreRT</span><span class="sxs-lookup"><span data-stu-id="a358d-147">CoreRT</span></span>

<span data-ttu-id="a358d-148">相較于 [CLR](#clr)，CoreRT 不是虛擬機器，這表示它不包含可即時產生和執行程式碼的功能，因為它不包含 [JIT](#jit)。</span><span class="sxs-lookup"><span data-stu-id="a358d-148">In contrast to the [CLR](#clr), CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="a358d-149">不過，它確實包含 [GC](#gc) ，以及執行時間類型識別 (RTTI) 和反映的能力。</span><span class="sxs-lookup"><span data-stu-id="a358d-149">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="a358d-150">不過，其型別系統已設計成不需要反映的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a358d-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="a358d-151">不需要中繼資料可讓 [AOT](#aot) 工具鏈連結到多餘的中繼資料， (更重要的是) 識別應用程式未使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a358d-151">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="a358d-152">CoreRT 正在開發中。</span><span class="sxs-lookup"><span data-stu-id="a358d-152">CoreRT is in development.</span></span>

<span data-ttu-id="a358d-153">請參閱 [.NET Native 和 CoreRT 簡介](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="a358d-154">跨平台</span><span class="sxs-lookup"><span data-stu-id="a358d-154">cross-platform</span></span>

<span data-ttu-id="a358d-155">開發和執行應用程式的能力，可用於多個不同的作業系統（例如 Linux、Windows 和 iOS），而不需要特別針對每個作業系統進行重寫。</span><span class="sxs-lookup"><span data-stu-id="a358d-155">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="a358d-156">這可讓您在不同平臺上的應用程式之間重複使用程式碼和一致性。</span><span class="sxs-lookup"><span data-stu-id="a358d-156">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="a358d-157">生態系統</span><span class="sxs-lookup"><span data-stu-id="a358d-157">ecosystem</span></span>

<span data-ttu-id="a358d-158">用來建置及執行適用於指定技術之應用程式的所有執行階段軟體、開發工具和社群資源。</span><span class="sxs-lookup"><span data-stu-id="a358d-158">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="a358d-159">「.NET 生態系統」一詞與「.NET 堆疊」等類似詞彙的不同之處在於，前者包含協力廠商應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="a358d-159">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="a358d-160">以下是用於句子中的範例：</span><span class="sxs-lookup"><span data-stu-id="a358d-160">Here's an example in a sentence:</span></span>

- <span data-ttu-id="a358d-161">「[.NET Standard](#net-standard) 背後的動機是在 .NET 生態系統中建立更高的一致性。」</span><span class="sxs-lookup"><span data-stu-id="a358d-161">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="a358d-162">架構</span><span class="sxs-lookup"><span data-stu-id="a358d-162">framework</span></span>

<span data-ttu-id="a358d-163">一般而言，一組功能齊全的 API 可加快開發和部署以特定技術為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a358d-163">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="a358d-164">ASP.NET Core 和 Windows Forms 即為此一般意義的應用程式架構範例。</span><span class="sxs-lookup"><span data-stu-id="a358d-164">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="a358d-165">另請參閱[程式庫](#library)。</span><span class="sxs-lookup"><span data-stu-id="a358d-165">See also [library](#library).</span></span>

<span data-ttu-id="a358d-166">"Framework" 這個字在下列詞彙中有不同的意義：</span><span class="sxs-lookup"><span data-stu-id="a358d-166">The word "framework" has a different meaning in the following terms:</span></span>

- [<span data-ttu-id="a358d-167">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a358d-167">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="a358d-168">目標 framework</span><span class="sxs-lookup"><span data-stu-id="a358d-168">target framework</span></span>](#target-framework)
- [<span data-ttu-id="a358d-169">TFM (目標 Framework Moniker)</span><span class="sxs-lookup"><span data-stu-id="a358d-169">TFM (target framework moniker)</span></span>](#tfm)
- [<span data-ttu-id="a358d-170">與 framework 相依的應用程式</span><span class="sxs-lookup"><span data-stu-id="a358d-170">framework-dependent app</span></span>](../core/deploying/index.md#publish-framework-dependent)

<span data-ttu-id="a358d-171">在舊版 .NET 檔中，「架構」有時是指 [.net 的實](#implementation-of-net)。</span><span class="sxs-lookup"><span data-stu-id="a358d-171">In legacy .NET documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="a358d-172">例如，文章可能會呼叫 .NET 5 架構。</span><span class="sxs-lookup"><span data-stu-id="a358d-172">For example, an article may call .NET 5 a framework.</span></span>

## <a name="gc"></a><span data-ttu-id="a358d-173">GC</span><span class="sxs-lookup"><span data-stu-id="a358d-173">GC</span></span>

<span data-ttu-id="a358d-174">記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="a358d-174">Garbage collector.</span></span>

<span data-ttu-id="a358d-175">記憶體回收行程是自動記憶體管理的實作。</span><span class="sxs-lookup"><span data-stu-id="a358d-175">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="a358d-176">GC 會釋放不再使用之物件所佔用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a358d-176">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="a358d-177">請參閱[記憶體回收](garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-177">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="a358d-178">IL</span><span class="sxs-lookup"><span data-stu-id="a358d-178">IL</span></span>

<span data-ttu-id="a358d-179">中繼語言。</span><span class="sxs-lookup"><span data-stu-id="a358d-179">Intermediate language.</span></span>

<span data-ttu-id="a358d-180">較高階的 .NET 語言 (例如 C#) 可向下編譯成硬體無從驗證的指令集，稱為中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="a358d-180">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="a358d-181">IL 有時稱為 MSIL (Microsoft IL) 或 CIL (Common IL)。</span><span class="sxs-lookup"><span data-stu-id="a358d-181">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="a358d-182">JIT</span><span class="sxs-lookup"><span data-stu-id="a358d-182">JIT</span></span>

<span data-ttu-id="a358d-183">Just-in-Time 編譯器。</span><span class="sxs-lookup"><span data-stu-id="a358d-183">Just-in-time compiler.</span></span>

<span data-ttu-id="a358d-184">此編譯器類似於 [AOT](#aot)，會將 [IL](#il) 轉譯成處理器了解的機器碼。</span><span class="sxs-lookup"><span data-stu-id="a358d-184">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="a358d-185">不同於 AOT，JIT 編譯會視需要發生，而且會在必須執行程式碼的相同電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="a358d-185">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="a358d-186">由於 JIT 編譯會在應用程式執行期間發生，因此編譯時間會是執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="a358d-186">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="a358d-187">因此，JIT 編譯器必須在最佳化程式碼所花費的時間與結果程式碼可能省下的時間之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="a358d-187">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="a358d-188">但 JIT 知道實際硬體，因此開發人員不需要提供不同的實作。</span><span class="sxs-lookup"><span data-stu-id="a358d-188">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="a358d-189">.NET 實作</span><span class="sxs-lookup"><span data-stu-id="a358d-189">implementation of .NET</span></span>

<span data-ttu-id="a358d-190">.NET 的執行包括：</span><span class="sxs-lookup"><span data-stu-id="a358d-190">An implementation of .NET includes:</span></span>

- <span data-ttu-id="a358d-191">一或多個執行階段。</span><span class="sxs-lookup"><span data-stu-id="a358d-191">One or more runtimes.</span></span> <span data-ttu-id="a358d-192">範例： [CLR](#clr)、 [CoreRT](#corert)。</span><span class="sxs-lookup"><span data-stu-id="a358d-192">Examples: [CLR](#clr), [CoreRT](#corert).</span></span>
- <span data-ttu-id="a358d-193">實作 .NET Standard 版本並可能包含其他 API 的類別庫。</span><span class="sxs-lookup"><span data-stu-id="a358d-193">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="a358d-194">範例：適用于[.NET Framework](#net-framework)的[BCLs](#bcl)和[.net 5 和更新版本 (包括 .net Core 2.1-3.1) ](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="a358d-194">Examples: the [BCLs](#bcl) for [.NET Framework](#net-framework) and [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>
- <span data-ttu-id="a358d-195">(選擇性) 一或多個應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="a358d-195">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="a358d-196">範例： [ASP.NET](#aspnet)、WINDOWS FORMS 和 WPF 包含在 .NET FRAMEWORK 和 .net 5 中。</span><span class="sxs-lookup"><span data-stu-id="a358d-196">Examples: [ASP.NET](#aspnet), Windows Forms, and WPF are included in the .NET Framework and .NET 5.</span></span>
- <span data-ttu-id="a358d-197">(選擇性) 開發工具。</span><span class="sxs-lookup"><span data-stu-id="a358d-197">Optionally, development tools.</span></span> <span data-ttu-id="a358d-198">某些開發工具可在多個實作之間共用。</span><span class="sxs-lookup"><span data-stu-id="a358d-198">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="a358d-199">.NET 實作的範例：</span><span class="sxs-lookup"><span data-stu-id="a358d-199">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="a358d-200">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a358d-200">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="a358d-201">.NET 5 和更新版本 (包括 .NET Core 2.1-3。1</span><span class="sxs-lookup"><span data-stu-id="a358d-201">.NET 5 and later versions (including .NET Core 2.1-3.1</span></span>](#net-5-and-later-versions)
- [<span data-ttu-id="a358d-202">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="a358d-202">Universal Windows Platform (UWP)</span></span>](#uwp)
- [<span data-ttu-id="a358d-203">Mono</span><span class="sxs-lookup"><span data-stu-id="a358d-203">Mono</span></span>](#mono)

## <a name="library"></a><span data-ttu-id="a358d-204">圖書館</span><span class="sxs-lookup"><span data-stu-id="a358d-204">library</span></span>

<span data-ttu-id="a358d-205">可由應用程式或其他程式庫呼叫的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="a358d-205">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="a358d-206">.NET 程式庫是由一或多個[組件](#assembly)組成。</span><span class="sxs-lookup"><span data-stu-id="a358d-206">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="a358d-207">程式庫和[架構](#framework)等字在使用時通常同義。</span><span class="sxs-lookup"><span data-stu-id="a358d-207">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="mono"></a><span data-ttu-id="a358d-208">Mono</span><span class="sxs-lookup"><span data-stu-id="a358d-208">Mono</span></span>

<span data-ttu-id="a358d-209">Mono 是開放原始碼、[跨平台](#cross-platform)的 .NET 實作，主要用於需要小型執行階段時。</span><span class="sxs-lookup"><span data-stu-id="a358d-209">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="a358d-210">它是在 Android、Mac、iOS、tvOS 和 watchOS 上提供 Xamarin 應用程式的執行時間，主要著重于需要少量資源的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a358d-210">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="a358d-211">它支援目前發行的所有 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="a358d-211">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="a358d-212">在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。</span><span class="sxs-lookup"><span data-stu-id="a358d-212">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="a358d-213">它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a358d-213">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="a358d-214">Mono 通常與 [即時編譯器](#jit)搭配使用，但也提供完整的 [靜態編譯器 (預先編譯) ](#aot) ，可在 iOS 等平臺上使用。</span><span class="sxs-lookup"><span data-stu-id="a358d-214">Mono is typically used with a [just-in-time compiler](#jit), but it also features a full [static compiler (ahead-of-time compilation)](#aot) that is used on platforms like iOS.</span></span>

<span data-ttu-id="a358d-215">請參閱 [Mono 檔](https://www.mono-project.com/docs/)。</span><span class="sxs-lookup"><span data-stu-id="a358d-215">See the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="a358d-216">.NET</span><span class="sxs-lookup"><span data-stu-id="a358d-216">.NET</span></span>

<span data-ttu-id="a358d-217">[.NET Standard](#net-standard) 以及所有 [.NET 實作](#implementation-of-net)和工作負載的籠統詞彙。</span><span class="sxs-lookup"><span data-stu-id="a358d-217">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="a358d-218">一律為完全大寫，絕對不會是 ".Net"。</span><span class="sxs-lookup"><span data-stu-id="a358d-218">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="a358d-219">當 [.net 5](#net-5-and-later-versions) (目前處於) 預覽狀態時，系統會針對所有新的 .net 開發建議使用 .net，因此在某些內容中，".net" 將表示「.net 5 和更新版本」。</span><span class="sxs-lookup"><span data-stu-id="a358d-219">When [.NET 5](#net-5-and-later-versions) (currently in preview) is released, it will be the recommended .NET implementation for all new .NET development, and so in some contexts ".NET" will imply ".NET 5 and later versions."</span></span>

<span data-ttu-id="a358d-220">請參閱 [.net 指南](index.yml)</span><span class="sxs-lookup"><span data-stu-id="a358d-220">See the [.NET guide](index.yml)</span></span>

## <a name="net-5-and-later-versions"></a><span data-ttu-id="a358d-221">.NET 5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a358d-221">.NET 5 and later versions</span></span>

<span data-ttu-id="a358d-222">.NET 的跨平臺、高效能、開放原始碼的實作為。</span><span class="sxs-lookup"><span data-stu-id="a358d-222">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="a358d-223">包括 Common Language Runtime ([CLR](#clr)) 、 ([CoreRT](#corert)的[AOT](#aot)執行時間、開發) 、基類庫 ([BCL](#bcl)) 和[.net SDK](#net-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a358d-223">Includes a Common Language Runtime ([CLR](#clr)), an [AOT](#aot) runtime ([CoreRT](#corert), in development), a Base Class Library ([BCL](#bcl)), and the [.NET SDK](#net-sdk).</span></span>

<span data-ttu-id="a358d-224">此 .NET 實作為較早的版本，稱為 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="a358d-224">Earlier versions of this .NET implementation are known as .NET Core.</span></span> <span data-ttu-id="a358d-225">.NET 5.0 是 .NET Core 3.1 之後的下一版。</span><span class="sxs-lookup"><span data-stu-id="a358d-225">.NET 5.0 is the next version following .NET Core 3.1.</span></span> <span data-ttu-id="a358d-226">已略過第4版，以避免使用較舊的實作為（稱為 [.NET Framework](#net-framework)）來混淆這項較新的 .net 執行。</span><span class="sxs-lookup"><span data-stu-id="a358d-226">Version 4 was skipped to avoid confusing this newer implementation of .NET with the older implementation that is known as [.NET Framework](#net-framework).</span></span> <span data-ttu-id="a358d-227">.NET Framework 目前的版本為4.8。</span><span class="sxs-lookup"><span data-stu-id="a358d-227">The current version of .NET Framework is 4.8.</span></span>

<span data-ttu-id="a358d-228">請參閱 [.net](../core/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="a358d-228">See [.NET](../core/index.yml).</span></span>

## <a name="net-cli"></a><span data-ttu-id="a358d-229">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="a358d-229">.NET CLI</span></span>

<span data-ttu-id="a358d-230">適用于開發 .Net 5 和更新版本之應用程式和程式庫的跨平臺工具鏈， [ (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="a358d-230">A cross-platform toolchain for developing applications and libraries for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span> <span data-ttu-id="a358d-231">也稱為 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="a358d-231">Also known as the .NET Core CLI.</span></span>

<span data-ttu-id="a358d-232">請參閱 [.NET CLI](../core/tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-232">See [.NET CLI](../core/tools/index.md).</span></span>

## <a name="net-core"></a><span data-ttu-id="a358d-233">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a358d-233">.NET Core</span></span>

<span data-ttu-id="a358d-234">請參閱 [.net 5 和更新版本](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="a358d-234">See [.NET 5 and later versions](#net-5-and-later-versions).</span></span>

## <a name="net-framework"></a><span data-ttu-id="a358d-235">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a358d-235">.NET Framework</span></span>

<span data-ttu-id="a358d-236">只會在 Windows 上執行的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="a358d-236">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="a358d-237">包括 Common Language Runtime ([CLR](#clr)) 、基類庫 ([BCL](#bcl)) 和應用程式架構程式庫（例如 [ASP.NET](#aspnet)、Windows Forms 和 WPF）。</span><span class="sxs-lookup"><span data-stu-id="a358d-237">Includes the Common Language Runtime ([CLR](#clr)), the Base Class Library ([BCL](#bcl)), and application framework libraries such as [ASP.NET](#aspnet), Windows Forms, and WPF.</span></span>

<span data-ttu-id="a358d-238">請參閱 [.NET Framework 指南](../framework/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="a358d-238">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="a358d-239">.NET Native</span><span class="sxs-lookup"><span data-stu-id="a358d-239">.NET Native</span></span>

<span data-ttu-id="a358d-240">產生原生程式碼提前 ([AOT](#aot)) 的編譯器工具鏈，而非即時 ([JIT](#jit)) 。</span><span class="sxs-lookup"><span data-stu-id="a358d-240">A compiler tool chain that produces native code ahead-of-time ([AOT](#aot)), as opposed to just-in-time ([JIT](#jit)).</span></span>

<span data-ttu-id="a358d-241">編譯會在開發人員的電腦上發生，其運作方式類似於 C++ 編譯器和連結器。</span><span class="sxs-lookup"><span data-stu-id="a358d-241">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="a358d-242">它會移除未使用的程式碼，並花更多時間在最佳化。</span><span class="sxs-lookup"><span data-stu-id="a358d-242">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="a358d-243">它會從程式庫擷取程式碼，並將其合併成可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a358d-243">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="a358d-244">結果會是代表整個應用程式的單一模組。</span><span class="sxs-lookup"><span data-stu-id="a358d-244">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="a358d-245">UWP 是 .NET Native 第一個支援的應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="a358d-245">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="a358d-246">現在，我們支援建置適用於 Windows、macOS 和 Linux 的原生主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a358d-246">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="a358d-247">請參閱 [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) (.NET Native 和 CoreRT 簡介)</span><span class="sxs-lookup"><span data-stu-id="a358d-247">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-sdk"></a><span data-ttu-id="a358d-248">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="a358d-248">.NET SDK</span></span>

<span data-ttu-id="a358d-249">一組程式庫和工具，可讓開發人員建立 .net 5 和更新版本的 .NET 應用程式和程式庫 [ (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="a358d-249">A set of libraries and tools that allow developers to create .NET applications and libraries for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span> <span data-ttu-id="a358d-250">也稱為 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a358d-250">Also known as the .NET Core SDK.</span></span>

<span data-ttu-id="a358d-251">包含用來建立應用程式的 [.NET CLI](#net-cli) 、用來建立和執行應用程式的 .net 程式庫和執行時間，以及 dotnet 可執行檔 (*dotnet.exe* 執行 CLI 命令和執行應用程式的) 。</span><span class="sxs-lookup"><span data-stu-id="a358d-251">Includes the [.NET CLI](#net-cli) for building apps, .NET libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="a358d-252">請參閱 [.NET SDK 總覽](../core/sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-252">See [.NET SDK Overview](../core/sdk.md).</span></span>

## <a name="net-standard"></a><span data-ttu-id="a358d-253">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a358d-253">.NET Standard</span></span>

<span data-ttu-id="a358d-254">可用於每個 .NET 實作之 .NET API 的型式規格。</span><span class="sxs-lookup"><span data-stu-id="a358d-254">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="a358d-255">.NET Standard 規格在文件中有時稱為程式庫。</span><span class="sxs-lookup"><span data-stu-id="a358d-255">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="a358d-256">由於程式庫不只包含規格 (介面)，還包含 API 實作，因此將 .NET Standard 稱為「程式庫」會造成誤導。</span><span class="sxs-lookup"><span data-stu-id="a358d-256">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span>

<span data-ttu-id="a358d-257">請參閱 [.NET Standard](net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-257">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="a358d-258">NGEN</span><span class="sxs-lookup"><span data-stu-id="a358d-258">NGEN</span></span>

<span data-ttu-id="a358d-259">原生 (映像) 產生。</span><span class="sxs-lookup"><span data-stu-id="a358d-259">Native (image) generation.</span></span>

<span data-ttu-id="a358d-260">您可以將這項技術視為持續性 [JIT](#jit) 編譯器。</span><span class="sxs-lookup"><span data-stu-id="a358d-260">You can think of this technology as a persistent [JIT](#jit) compiler.</span></span> <span data-ttu-id="a358d-261">它通常會在執行程式碼的電腦上編譯程式碼，但編譯通常會發生在安裝期間。</span><span class="sxs-lookup"><span data-stu-id="a358d-261">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="a358d-262">套件</span><span class="sxs-lookup"><span data-stu-id="a358d-262">package</span></span>

<span data-ttu-id="a358d-263">NuGet 套件 (簡稱套件) 是 *.zip* 檔案，其中包含一或多個同名組件及其他中繼資料 (例如作者名稱)。</span><span class="sxs-lookup"><span data-stu-id="a358d-263">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="a358d-264">*.zip* 檔案包含一個 *.nupkg* 延伸模組和許多特定資產 (例如 *.dll* 檔案和 *.xml* 檔案)，可搭配多個架構和版本使用。</span><span class="sxs-lookup"><span data-stu-id="a358d-264">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="a358d-265">安裝於應用程式或程式庫時，會根據應用程式或程式庫所指定的目標 Framework 來選取適當的資產。</span><span class="sxs-lookup"><span data-stu-id="a358d-265">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="a358d-266">定義介面的資產位於 *ref* 資料夾中，而定義實作的資產則位於 *lib* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a358d-266">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="a358d-267">平台</span><span class="sxs-lookup"><span data-stu-id="a358d-267">platform</span></span>

<span data-ttu-id="a358d-268">作業系統及其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。</span><span class="sxs-lookup"><span data-stu-id="a358d-268">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="a358d-269">以下是用於句子中的範例：</span><span class="sxs-lookup"><span data-stu-id="a358d-269">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="a358d-270">「.NET Core 是 .NET 的跨平台實作。」</span><span class="sxs-lookup"><span data-stu-id="a358d-270">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="a358d-271">「PCL 設定檔代表 Microsoft 平台，而 .NET Standard 則無從驗證平台。」</span><span class="sxs-lookup"><span data-stu-id="a358d-271">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="a358d-272">舊版 .NET 檔有時會使用 ".NET platform" 來表示 .NET 或 .NET [stack](#stack)的執行，包括所有[的實](#implementation-of-net)作為。</span><span class="sxs-lookup"><span data-stu-id="a358d-272">Legacy .NET documentation sometimes uses ".NET platform" to mean either an [implementation of .NET](#implementation-of-net) or the .NET [stack](#stack) including all implementations.</span></span> <span data-ttu-id="a358d-273">這兩種使用方式通常會與主要 (作業系統/硬體) 含意混淆，因此我們會嘗試避免這些使用方式。</span><span class="sxs-lookup"><span data-stu-id="a358d-273">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we try to avoid these usages.</span></span>

<span data-ttu-id="a358d-274">「平臺」在「開發人員平臺」一詞中有不同的意義，這是指提供建立和執行應用程式之工具和程式庫的軟體。</span><span class="sxs-lookup"><span data-stu-id="a358d-274">"Platform" has a different meaning in the phrase "developer platform," which refers to software that provides tools and libraries for building and running apps.</span></span> <span data-ttu-id="a358d-275">.NET 是一種跨平臺的開放原始碼開發人員平臺，可用於建立許多不同類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a358d-275">.NET is a cross-platform, open source developer platform for building many different types of applications.</span></span>

## <a name="runtime"></a><span data-ttu-id="a358d-276">執行階段</span><span class="sxs-lookup"><span data-stu-id="a358d-276">runtime</span></span>

<span data-ttu-id="a358d-277">一般情況下，受管理程式的執行環境。</span><span class="sxs-lookup"><span data-stu-id="a358d-277">In general, the execution environment for a managed program.</span></span> <span data-ttu-id="a358d-278">OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="a358d-278">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="a358d-279">以下是 .NET 執行時間的一些範例：</span><span class="sxs-lookup"><span data-stu-id="a358d-279">Here are some examples of .NET runtimes in this sense of the word:</span></span>

- <span data-ttu-id="a358d-280">Common Language Runtime ([CLR](#clr)) </span><span class="sxs-lookup"><span data-stu-id="a358d-280">Common Language Runtime ([CLR](#clr))</span></span>
- <span data-ttu-id="a358d-281">.NET Native (適用於 UWP)</span><span class="sxs-lookup"><span data-stu-id="a358d-281">.NET Native (for UWP)</span></span>
- <span data-ttu-id="a358d-282">Mono 執行階段</span><span class="sxs-lookup"><span data-stu-id="a358d-282">Mono runtime</span></span>

<span data-ttu-id="a358d-283">"Runtime" 這個字在下列內容中有不同的意義：</span><span class="sxs-lookup"><span data-stu-id="a358d-283">The word "runtime" has a different meaning in the following contexts:</span></span>

* <span data-ttu-id="a358d-284">[.Net 下載頁面](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="a358d-284">The [.NET download page](https://dotnet.microsoft.com/download).</span></span>

  <span data-ttu-id="a358d-285">此處的「執行時間」表示 [CLR](#clr) 與 [BCL](#bcl) (framework 程式庫) ，您可以在電腦上下載並安裝該程式庫，讓您可以在電腦上執行與 [framework 相依](../core/deploying/index.md#publish-framework-dependent) 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a358d-285">"Runtime" here means the [CLR](#clr) together with the [BCL](#bcl) (framework libraries), that you can download and install on a machine so that you can run [framework-dependent](../core/deploying/index.md#publish-framework-dependent) apps on the machine.</span></span>

* <span data-ttu-id="a358d-286">[.Net 5 和更新版本 (包括 .Net Core 2.1-3.1) ](#net-5-and-later-versions) [ (RID) 的執行時間識別碼](../core/rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-286">The [Runtime Identifier (RID)](../core/rid-catalog.md) for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>

  <span data-ttu-id="a358d-287">此處的「執行時間」表示 .NET 應用程式執行所在的作業系統平臺和 CPU 架構，例如： `linux-x64` 。</span><span class="sxs-lookup"><span data-stu-id="a358d-287">"Runtime" here means the OS platform and CPU architecture that a .NET app runs on, for example: `linux-x64`.</span></span>

<span data-ttu-id="a358d-288">舊版 .NET 檔有時候會使用「執行時間」，以 [實現 .net](#implementation-of-net)的意義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a358d-288">Legacy .NET documentation sometimes uses "runtime" in the sense of an [implementation of .NET](#implementation-of-net), as in the following examples:</span></span>

- <span data-ttu-id="a358d-289">「不同的 .NET 執行階段會實作特定版本的 .NET Standard。」</span><span class="sxs-lookup"><span data-stu-id="a358d-289">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="a358d-290">「要在多個執行階段上執行的程式庫應以此架構為目標。」</span><span class="sxs-lookup"><span data-stu-id="a358d-290">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="a358d-291">(指的是 .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="a358d-291">(referring to .NET Standard)</span></span>
- <span data-ttu-id="a358d-292">「不同的 .NET 執行階段會實作特定版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="a358d-292">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="a358d-293">…</span><span class="sxs-lookup"><span data-stu-id="a358d-293">…</span></span> <span data-ttu-id="a358d-294">每個 .NET 執行階段版本會宣佈它所支援的最高 .NET Standard 版本...」</span><span class="sxs-lookup"><span data-stu-id="a358d-294">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

## <a name="stack"></a><span data-ttu-id="a358d-295">堆疊</span><span class="sxs-lookup"><span data-stu-id="a358d-295">stack</span></span>

<span data-ttu-id="a358d-296">可搭配使用以建置及執行應用程式的一組程式設計技術。</span><span class="sxs-lookup"><span data-stu-id="a358d-296">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="a358d-297">「.NET 堆疊」是指 .NET Standard 和所有 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="a358d-297">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="a358d-298">「一個 .NET 堆疊」一詞可能是指 .NET 的一項實作。</span><span class="sxs-lookup"><span data-stu-id="a358d-298">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="a358d-299">Target Framework - 目標 Framework</span><span class="sxs-lookup"><span data-stu-id="a358d-299">target framework</span></span>

<span data-ttu-id="a358d-300">.NET 應用程式或程式庫依賴的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="a358d-300">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="a358d-301">應用程式或程式庫可以將目標設為某個版本的 .NET Standard (例如 .NET Standard 2.0) ，這是一組標準化的 Api，適用于所有 .NET 執行。</span><span class="sxs-lookup"><span data-stu-id="a358d-301">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is a specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="a358d-302">應用程式或程式庫也可以將目標設為某個版本的特定 .NET 實作；在此情況下，它可以存取實作特定的 API。</span><span class="sxs-lookup"><span data-stu-id="a358d-302">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="a358d-303">例如，以 Xamarin.iOS 為目標的應用程式可以存取 Xamarin 提供的 iOS API 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="a358d-303">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="a358d-304">針對某些目標 Framework (例如 .NET Framework)，可用的 API 是由 .NET 實作安裝在系統上的組件所定義，這可能包含應用程式架構 API (例如 ASP.NET、WinForms)。</span><span class="sxs-lookup"><span data-stu-id="a358d-304">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="a358d-305">針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，架構 API 是由安裝在應用程式或程式庫中的套件所定義。</span><span class="sxs-lookup"><span data-stu-id="a358d-305">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="a358d-306">在此情況下，目標架構會隱含地指定參考所有封裝的封裝，這些封裝會組成架構。</span><span class="sxs-lookup"><span data-stu-id="a358d-306">In that case, the target framework implicitly specifies a package that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="a358d-307">請參閱[目標 Framework](frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-307">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="a358d-308">TFM</span><span class="sxs-lookup"><span data-stu-id="a358d-308">TFM</span></span>

<span data-ttu-id="a358d-309">目標 Framework Moniker。</span><span class="sxs-lookup"><span data-stu-id="a358d-309">Target framework moniker.</span></span>

<span data-ttu-id="a358d-310">用於指定 .NET 應用程式或程式庫之目標 Framework 的標準化語彙基元格式。</span><span class="sxs-lookup"><span data-stu-id="a358d-310">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="a358d-311">目標 Framework 通常會由簡短名稱參考，例如 `net462`。</span><span class="sxs-lookup"><span data-stu-id="a358d-311">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="a358d-312">雖然有完整格式的 TFM (例如 .NETFramework,Version=4.6.2)，但通常不會用來指定目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="a358d-312">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="a358d-313">請參閱[目標 Framework](frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="a358d-313">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="a358d-314">UWP</span><span class="sxs-lookup"><span data-stu-id="a358d-314">UWP</span></span>

<span data-ttu-id="a358d-315">通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="a358d-315">Universal Windows Platform.</span></span>

<span data-ttu-id="a358d-316">用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="a358d-316">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="a358d-317">它是設計來統一您可能想要鎖定的不同裝置類型，包括電腦、平板電腦、手機，甚至是 Xbox。</span><span class="sxs-lookup"><span data-stu-id="a358d-317">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="a358d-318">UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。</span><span class="sxs-lookup"><span data-stu-id="a358d-318">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="a358d-319">您可以用 c + +、c #、Visual Basic 和 JavaScript 來撰寫應用程式。</span><span class="sxs-lookup"><span data-stu-id="a358d-319">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="a358d-320">使用 c # 和 Visual Basic 時，.net Api 是由 .NET 5 和更新版本所提供， (包括 .NET Core 2.1-3.1) 。</span><span class="sxs-lookup"><span data-stu-id="a358d-320">When using C# and Visual Basic, the .NET APIs are provided by .NET 5 and later versions (including .NET Core 2.1-3.1).</span></span>

## <a name="see-also"></a><span data-ttu-id="a358d-321">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a358d-321">See also</span></span>

- [<span data-ttu-id="a358d-322">.NET 指南</span><span class="sxs-lookup"><span data-stu-id="a358d-322">.NET Guide</span></span>](index.yml)
- [<span data-ttu-id="a358d-323">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="a358d-323">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="a358d-324">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a358d-324">.NET Core</span></span>](../core/index.yml)
- [<span data-ttu-id="a358d-325">ASP.NET 總覽</span><span class="sxs-lookup"><span data-stu-id="a358d-325">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="a358d-326">ASP.NET Core 總覽</span><span class="sxs-lookup"><span data-stu-id="a358d-326">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
