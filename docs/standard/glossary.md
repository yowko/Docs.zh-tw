---
title: .NET 字彙表
description: 了解 .NET 文件中所使用之特定詞彙的意義。
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 11fad691021ec897348177c67134750e72b4ff7c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698480"
---
# <a name="net-glossary"></a><span data-ttu-id="95cc5-103">.NET 字彙表</span><span class="sxs-lookup"><span data-stu-id="95cc5-103">.NET Glossary</span></span>

<span data-ttu-id="95cc5-104">此字彙表的主要目標是釐清經常出現在 .NET 文件中但沒有定義之特定詞彙和縮略字的意義。</span><span class="sxs-lookup"><span data-stu-id="95cc5-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="95cc5-105">AOT</span><span class="sxs-lookup"><span data-stu-id="95cc5-105">AOT</span></span>

<span data-ttu-id="95cc5-106">預先編譯器。</span><span class="sxs-lookup"><span data-stu-id="95cc5-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="95cc5-107">此編譯器類似於 [JIT](#jit)，也會將 [IL](#il) 轉譯成機器碼。</span><span class="sxs-lookup"><span data-stu-id="95cc5-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="95cc5-108">相較於 JIT 編譯，AOT 編譯會在執行應用程式之前發生，而且通常會在不同的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="95cc5-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="95cc5-109">由於 AOT 工具鏈不在執行階段編譯，因此不需要縮短花在編譯的時間。</span><span class="sxs-lookup"><span data-stu-id="95cc5-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="95cc5-110">這表示它們可以花更多的時間在最佳化。</span><span class="sxs-lookup"><span data-stu-id="95cc5-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="95cc5-111">由於 AOT 的內容是整個應用程式，因此 AOT 編譯器也會執行跨模組連結和整個程式分析，這表示會追蹤所有參考並產生單一可執行檔。</span><span class="sxs-lookup"><span data-stu-id="95cc5-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="95cc5-112">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="95cc5-112">ASP.NET</span></span> 

<span data-ttu-id="95cc5-113">隨附於 .NET Framework 的原始 ASP.NET 實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-113">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="95cc5-114">有時 ASP.NET 是指包括 ASP.NET Core 在內之兩個 ASP.NET 實作的籠統名詞。</span><span class="sxs-lookup"><span data-stu-id="95cc5-114">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="95cc5-115">該詞彙在任何指定的執行個體中所代表的意義取決於內容。</span><span class="sxs-lookup"><span data-stu-id="95cc5-115">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="95cc5-116">當想要澄清您不是使用 ASP.NET 來表示這兩種實作時，請參閱 ASP.NET 4.x。</span><span class="sxs-lookup"><span data-stu-id="95cc5-116">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="95cc5-117">請參閱 [ASP.NET 文件](/aspnet/#pivot=aspnet)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-117">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="95cc5-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="95cc5-118">ASP.NET Core</span></span>

<span data-ttu-id="95cc5-119">建置於 .NET Core 之 ASP.NET 的跨平台、高效能、開放原始碼實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-119">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="95cc5-120">請參閱 [ASP.NET Core 文件](/aspnet/#pivot=core)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-120">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="95cc5-121">組件</span><span class="sxs-lookup"><span data-stu-id="95cc5-121">assembly</span></span>

<span data-ttu-id="95cc5-122">可以包含可由應用程式或其他組件呼叫之 API 集合的 *.dll*/*.exe* 檔案。</span><span class="sxs-lookup"><span data-stu-id="95cc5-122">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="95cc5-123">一個組件可以包含介面、類別、結構、列舉和委派等類型。</span><span class="sxs-lookup"><span data-stu-id="95cc5-123">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="95cc5-124">專案的 *bin* 資料夾中的組件有時稱為「二進位檔」。</span><span class="sxs-lookup"><span data-stu-id="95cc5-124">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="95cc5-125">另請參閱[程式庫](#library)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-125">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="95cc5-126">CLR</span><span class="sxs-lookup"><span data-stu-id="95cc5-126">CLR</span></span>

<span data-ttu-id="95cc5-127">Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="95cc5-127">Common Language Runtime.</span></span>

<span data-ttu-id="95cc5-128">確切意義取決於內容，但這通常是指 .NET Framework 的執行階段。</span><span class="sxs-lookup"><span data-stu-id="95cc5-128">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="95cc5-129">CLR 會處理記憶體配置和管理。</span><span class="sxs-lookup"><span data-stu-id="95cc5-129">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="95cc5-130">CLR 也是虛擬機器，它不只會執行應用程式，也會使用 JIT 編譯器即時產生和編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="95cc5-130">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="95cc5-131">目前的 Microsoft CLR 實作僅限 Windows。</span><span class="sxs-lookup"><span data-stu-id="95cc5-131">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="95cc5-132">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="95cc5-132">CoreCLR</span></span>

<span data-ttu-id="95cc5-133">.NET Core Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="95cc5-133">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="95cc5-134">此 CLR 是從與 CLR 相同的程式碼基底所建置。</span><span class="sxs-lookup"><span data-stu-id="95cc5-134">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="95cc5-135">一開始，CoreCLR 是 Silverlight 的執行階段，其設計目的是為了在多個平台上執行，特別是 Windows 和 OS X。CoreCLR 現在是 .NET Core 的一部分，代表 CLR 的簡化版本。</span><span class="sxs-lookup"><span data-stu-id="95cc5-135">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="95cc5-136">它仍然是跨平台執行階段，現在支援許多 Linux 發行版本。</span><span class="sxs-lookup"><span data-stu-id="95cc5-136">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="95cc5-137">CoreCLR 也是具有 JIT 和程式碼執行功能的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="95cc5-137">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="95cc5-138">CoreFX</span><span class="sxs-lookup"><span data-stu-id="95cc5-138">CoreFX</span></span>

<span data-ttu-id="95cc5-139">.NET Core 基底類別庫 (BCL)</span><span class="sxs-lookup"><span data-stu-id="95cc5-139">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="95cc5-140">由 System.\* (以及一定範圍內的 Microsoft.\*) 命名空間組成的一組程式庫。</span><span class="sxs-lookup"><span data-stu-id="95cc5-140">A set of libraries that comprise the System.\* (and to a limited extent  Microsoft.\*) namespaces.</span></span> <span data-ttu-id="95cc5-141">BCL 是 ASP.NET Core 等較高層級的應用程式架構建置所在之較低層級的一般目的架構。</span><span class="sxs-lookup"><span data-stu-id="95cc5-141">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="95cc5-142">.NET Core BCL 的原始程式碼包含在 [CoreFX 存放庫](https://github.com/dotnet/corefx)中。</span><span class="sxs-lookup"><span data-stu-id="95cc5-142">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="95cc5-143">不過，大多數的 .NET Core API 也適用於 .NET Framework；因此您可以將 CoreFX 視為 .NET Framework BCL 的分支。</span><span class="sxs-lookup"><span data-stu-id="95cc5-143">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="95cc5-144">CoreRT</span><span class="sxs-lookup"><span data-stu-id="95cc5-144">CoreRT</span></span>

<span data-ttu-id="95cc5-145">.NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="95cc5-145">.NET Core runtime.</span></span>

<span data-ttu-id="95cc5-146">相較於 CLR/CoreCLR，CoreRT 不是虛擬機器，這表示它不會包含即時產生和執行程式碼的功能，因為它不包含 [JIT](#jit)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-146">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="95cc5-147">不過，它包含 [GC](#gc)，以及執行階段類型識別 (RTTI) 和反映功能。</span><span class="sxs-lookup"><span data-stu-id="95cc5-147">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="95cc5-148">不過，其型別系統已設計成不需要反映的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="95cc5-148">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="95cc5-149">這讓 [AOT](#aot) 工具鏈能夠抽離不必要的中繼資料，更重要的是，它能夠識別應用程式未使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="95cc5-149">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="95cc5-150">CoreRT 正在開發中。</span><span class="sxs-lookup"><span data-stu-id="95cc5-150">CoreRT is in development.</span></span>

<span data-ttu-id="95cc5-151">請參閱 [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) (.NET Native 和 CoreRT 簡介)</span><span class="sxs-lookup"><span data-stu-id="95cc5-151">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="95cc5-152">生態系統</span><span class="sxs-lookup"><span data-stu-id="95cc5-152">ecosystem</span></span>

<span data-ttu-id="95cc5-153">用來建置及執行適用於指定技術之應用程式的所有執行階段軟體、開發工具和社群資源。</span><span class="sxs-lookup"><span data-stu-id="95cc5-153">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="95cc5-154">「.NET 生態系統」一詞與「.NET 堆疊」等類似詞彙的不同之處在於，前者包含協力廠商應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="95cc5-154">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="95cc5-155">以下是用於句子中的範例：</span><span class="sxs-lookup"><span data-stu-id="95cc5-155">Here's an example in a sentence:</span></span>

- <span data-ttu-id="95cc5-156">「[.NET Standard](#net-standard) 背後的動機是在 .NET 生態系統中建立更高的一致性。」</span><span class="sxs-lookup"><span data-stu-id="95cc5-156">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="95cc5-157">架構</span><span class="sxs-lookup"><span data-stu-id="95cc5-157">framework</span></span>

<span data-ttu-id="95cc5-158">一般而言，一組功能齊全的 API 可加快開發和部署以特定技術為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="95cc5-158">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="95cc5-159">ASP.NET Core 和 Windows Forms 即為此一般意義的應用程式架構範例。</span><span class="sxs-lookup"><span data-stu-id="95cc5-159">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="95cc5-160">另請參閱[程式庫](#library)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-160">See also [library](#library).</span></span>

<span data-ttu-id="95cc5-161">「架構」一字在下列詞彙中有更特定的技術意義：</span><span class="sxs-lookup"><span data-stu-id="95cc5-161">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="95cc5-162">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="95cc5-162">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="95cc5-163">目標 Framework</span><span class="sxs-lookup"><span data-stu-id="95cc5-163">target framework</span></span>](#target-framework)
* [<span data-ttu-id="95cc5-164">TFM (目標 Framework Moniker)</span><span class="sxs-lookup"><span data-stu-id="95cc5-164">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="95cc5-165">在現有的文件中，「架構」有時是指 [.NET 實作](#implementation-of-net)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-165">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="95cc5-166">例如，某篇文章可能會將 .NET Core 稱為架構。</span><span class="sxs-lookup"><span data-stu-id="95cc5-166">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="95cc5-167">我們計劃從文件中排除這個令人混淆的用法。</span><span class="sxs-lookup"><span data-stu-id="95cc5-167">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="95cc5-168">GC</span><span class="sxs-lookup"><span data-stu-id="95cc5-168">GC</span></span>

<span data-ttu-id="95cc5-169">記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="95cc5-169">Garbage collector.</span></span>

<span data-ttu-id="95cc5-170">記憶體回收行程是自動記憶體管理的實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-170">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="95cc5-171">GC 會釋放不再使用之物件所佔用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="95cc5-171">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="95cc5-172">請參閱[記憶體回收](garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-172">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="95cc5-173">IL</span><span class="sxs-lookup"><span data-stu-id="95cc5-173">IL</span></span>

<span data-ttu-id="95cc5-174">中繼語言。</span><span class="sxs-lookup"><span data-stu-id="95cc5-174">Intermediate language.</span></span>

<span data-ttu-id="95cc5-175">較高階的 .NET 語言 (例如 C#) 可向下編譯成硬體無從驗證的指令集，稱為中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-175">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="95cc5-176">IL 有時稱為 MSIL (Microsoft IL) 或 CIL (Common IL)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-176">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="95cc5-177">JIT</span><span class="sxs-lookup"><span data-stu-id="95cc5-177">JIT</span></span>

<span data-ttu-id="95cc5-178">Just-in-Time 編譯器。</span><span class="sxs-lookup"><span data-stu-id="95cc5-178">Just-in-time compiler.</span></span>

<span data-ttu-id="95cc5-179">此編譯器類似於 [AOT](#aot)，會將 [IL](#il) 轉譯成處理器了解的機器碼。</span><span class="sxs-lookup"><span data-stu-id="95cc5-179">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="95cc5-180">不同於 AOT，JIT 編譯會視需要發生，而且會在必須執行程式碼的相同電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="95cc5-180">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="95cc5-181">由於 JIT 編譯會在應用程式執行期間發生，因此編譯時間會是執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="95cc5-181">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="95cc5-182">因此，JIT 編譯器必須在最佳化程式碼所花費的時間與結果程式碼可能省下的時間之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="95cc5-182">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="95cc5-183">但 JIT 知道實際硬體，因此開發人員不需要提供不同的實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-183">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="95cc5-184">.NET 實作</span><span class="sxs-lookup"><span data-stu-id="95cc5-184">implementation of .NET</span></span>

<span data-ttu-id="95cc5-185">.NET 實作包括：</span><span class="sxs-lookup"><span data-stu-id="95cc5-185">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="95cc5-186">一或多個執行階段。</span><span class="sxs-lookup"><span data-stu-id="95cc5-186">One or more runtimes.</span></span> <span data-ttu-id="95cc5-187">範例：CLR、CoreCLR、CoreRT。</span><span class="sxs-lookup"><span data-stu-id="95cc5-187">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="95cc5-188">實作 .NET Standard 版本並可能包含其他 API 的類別庫。</span><span class="sxs-lookup"><span data-stu-id="95cc5-188">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="95cc5-189">範例：.NET Framework 基底類別庫、.NET Core 基底類別庫。</span><span class="sxs-lookup"><span data-stu-id="95cc5-189">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="95cc5-190">(選擇性) 一或多個應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="95cc5-190">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="95cc5-191">範例：ASP.NET、Windows Forms 和 WPF 會包含在 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="95cc5-191">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="95cc5-192">(選擇性) 開發工具。</span><span class="sxs-lookup"><span data-stu-id="95cc5-192">Optionally, development tools.</span></span> <span data-ttu-id="95cc5-193">某些開發工具可在多個實作之間共用。</span><span class="sxs-lookup"><span data-stu-id="95cc5-193">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="95cc5-194">.NET 實作的範例：</span><span class="sxs-lookup"><span data-stu-id="95cc5-194">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="95cc5-195">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="95cc5-195">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="95cc5-196">.NET Core</span><span class="sxs-lookup"><span data-stu-id="95cc5-196">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="95cc5-197">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="95cc5-197">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="95cc5-198">程式庫</span><span class="sxs-lookup"><span data-stu-id="95cc5-198">library</span></span>

<span data-ttu-id="95cc5-199">可由應用程式或其他程式庫呼叫的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="95cc5-199">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="95cc5-200">.NET 程式庫是由一或多個[組件](#assembly)組成。</span><span class="sxs-lookup"><span data-stu-id="95cc5-200">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="95cc5-201">程式庫和[架構](#framework)等字在使用時通常同義。</span><span class="sxs-lookup"><span data-stu-id="95cc5-201">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="95cc5-202">中繼套件</span><span class="sxs-lookup"><span data-stu-id="95cc5-202">metapackage</span></span>

<span data-ttu-id="95cc5-203">沒有自己的程式庫，而只是一份相依性清單的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="95cc5-203">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="95cc5-204">內含的套件可以選擇性地建立目標 Framework 的 API。</span><span class="sxs-lookup"><span data-stu-id="95cc5-204">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="95cc5-205">請參閱[套件、中繼套件和架構](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="95cc5-205">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="95cc5-206">Mono</span><span class="sxs-lookup"><span data-stu-id="95cc5-206">Mono</span></span>

<span data-ttu-id="95cc5-207">Mono 是需要小型執行階段時主要使用的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-207">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="95cc5-208">它是支援 Android、Mac、iOS、tvOS 和 watchOS 版 Xamarin 應用程式的執行階段，而且主要著重在資源使用量較少的應用程式。</span><span class="sxs-lookup"><span data-stu-id="95cc5-208">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="95cc5-209">它支援目前發行的所有 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="95cc5-209">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="95cc5-210">在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。</span><span class="sxs-lookup"><span data-stu-id="95cc5-210">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="95cc5-211">它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95cc5-211">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="95cc5-212">Mono 通常可搭配 Just-In-Time 編譯器使用，但也提供適用於 iOS 等平台的完整靜態編譯器 (預先編譯)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-212">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="95cc5-213">若要深入了解 Mono，請參閱 [Mono 文件](https://www.mono-project.com/docs/)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-213">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="95cc5-214">.NET</span><span class="sxs-lookup"><span data-stu-id="95cc5-214">.NET</span></span>

<span data-ttu-id="95cc5-215">[.NET Standard](#net-standard) 以及所有 [.NET 實作](#implementation-of-net)和工作負載的籠統詞彙。</span><span class="sxs-lookup"><span data-stu-id="95cc5-215">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="95cc5-216">一律為大寫，絕對不會是 ".Net"。</span><span class="sxs-lookup"><span data-stu-id="95cc5-216">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="95cc5-217">請參閱 [.NET 指南](index.md)</span><span class="sxs-lookup"><span data-stu-id="95cc5-217">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="95cc5-218">.NET Core</span><span class="sxs-lookup"><span data-stu-id="95cc5-218">.NET Core</span></span> 

<span data-ttu-id="95cc5-219">.NET 的跨平台、高效能、開放原始碼實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-219">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="95cc5-220">包括 Core Common Language Runtime (CoreCLR)、Core AOT 執行階段 (CoreRT 開發中)、Core 基底類別庫，以及 Core SDK。</span><span class="sxs-lookup"><span data-stu-id="95cc5-220">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="95cc5-221">請參閱 [.NET Core](../core/index.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-221">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="95cc5-222">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="95cc5-222">.NET Core CLI</span></span>

<span data-ttu-id="95cc5-223">用於開發 .NET Core 應用程式的跨平台工具鏈。</span><span class="sxs-lookup"><span data-stu-id="95cc5-223">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="95cc5-224">請參閱 [.NET Core 命令列介面 (CLI) 工具](../core/tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-224">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="95cc5-225">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="95cc5-225">.NET Core SDK</span></span>

<span data-ttu-id="95cc5-226">可讓開發人員建立 .NET Core 應用程式和程式庫的一組程式庫和工具。</span><span class="sxs-lookup"><span data-stu-id="95cc5-226">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="95cc5-227">包括用於建置應用程式的 [.NET Core CLI](#net-core-cli)、用於建置及執行應用程式的 .NET Core 程式庫和執行階段，以及執行 CLI 命令及執行應用程式的 dotnet 可執行檔 (*dotnet.exe*)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-227">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="95cc5-228">請參閱 [.NET Core SDK 概觀](../core/sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-228">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="95cc5-229">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="95cc5-229">.NET Framework</span></span>

<span data-ttu-id="95cc5-230">只會在 Windows 上執行的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-230">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="95cc5-231">包括 Common Language Runtime (CLR)、基底類別庫，以及 ASP.NET、Windows Forms 和 WPF 等應用程式架構程式庫。</span><span class="sxs-lookup"><span data-stu-id="95cc5-231">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="95cc5-232">請參閱 [.NET Framework 指南](../framework/index.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-232">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="95cc5-233">.NET Native</span><span class="sxs-lookup"><span data-stu-id="95cc5-233">.NET Native</span></span>

<span data-ttu-id="95cc5-234">產生機器碼預先編譯 (AOT) 而不是 Just-In-Time (JIT) 的編譯器工具鏈。</span><span class="sxs-lookup"><span data-stu-id="95cc5-234">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="95cc5-235">編譯會在開發人員的電腦上發生，其運作方式類似於 C++ 編譯器和連結器。</span><span class="sxs-lookup"><span data-stu-id="95cc5-235">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="95cc5-236">它會移除未使用的程式碼，並花更多時間在最佳化。</span><span class="sxs-lookup"><span data-stu-id="95cc5-236">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="95cc5-237">它會從程式庫擷取程式碼，並將其合併成可執行檔。</span><span class="sxs-lookup"><span data-stu-id="95cc5-237">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="95cc5-238">結果會是代表整個應用程式的單一模組。</span><span class="sxs-lookup"><span data-stu-id="95cc5-238">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="95cc5-239">UWP 是 .NET Native 第一個支援的應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="95cc5-239">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="95cc5-240">現在，我們支援建置適用於 Windows、macOS 和 Linux 的原生主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="95cc5-240">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="95cc5-241">請參閱 [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) (.NET Native 和 CoreRT 簡介)</span><span class="sxs-lookup"><span data-stu-id="95cc5-241">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="95cc5-242">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="95cc5-242">.NET Standard</span></span>

<span data-ttu-id="95cc5-243">可用於每個 .NET 實作之 .NET API 的型式規格。</span><span class="sxs-lookup"><span data-stu-id="95cc5-243">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="95cc5-244">.NET Standard 規格在文件中有時稱為程式庫。</span><span class="sxs-lookup"><span data-stu-id="95cc5-244">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="95cc5-245">由於程式庫不只包含規格 (介面)，還包含 API 實作，因此將 .NET Standard 稱為「程式庫」會造成誤導。</span><span class="sxs-lookup"><span data-stu-id="95cc5-245">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="95cc5-246">我們計劃從文件中排除該用法，只有參考 .NET Standard 中繼套件的名稱 (`NETStandard.Library`) 時除外。</span><span class="sxs-lookup"><span data-stu-id="95cc5-246">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="95cc5-247">請參閱 [.NET Standard](net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-247">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="95cc5-248">NGEN</span><span class="sxs-lookup"><span data-stu-id="95cc5-248">NGEN</span></span>

<span data-ttu-id="95cc5-249">原生 (映像) 產生。</span><span class="sxs-lookup"><span data-stu-id="95cc5-249">Native (image) generation.</span></span>

<span data-ttu-id="95cc5-250">您可以將這項技術視為永續性 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="95cc5-250">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="95cc5-251">它通常會在執行程式碼的電腦上編譯程式碼，但編譯通常會發生在安裝期間。</span><span class="sxs-lookup"><span data-stu-id="95cc5-251">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="95cc5-252">套件</span><span class="sxs-lookup"><span data-stu-id="95cc5-252">package</span></span>

<span data-ttu-id="95cc5-253">NuGet 套件 (簡稱套件) 是 *.zip* 檔案，其中包含一或多個同名組件及其他中繼資料 (例如作者名稱)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-253">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="95cc5-254">*.zip* 檔案包含一個 *.nupkg* 延伸模組和許多特定資產 (例如 *.dll* 檔案和 *.xml* 檔案)，可搭配多個架構和版本使用。</span><span class="sxs-lookup"><span data-stu-id="95cc5-254">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="95cc5-255">安裝於應用程式或程式庫時，會根據應用程式或程式庫所指定的目標 Framework 來選取適當的資產。</span><span class="sxs-lookup"><span data-stu-id="95cc5-255">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="95cc5-256">定義介面的資產位於 *ref* 資料夾中，而定義實作的資產則位於 *lib* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="95cc5-256">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="95cc5-257">platform</span><span class="sxs-lookup"><span data-stu-id="95cc5-257">platform</span></span>

<span data-ttu-id="95cc5-258">作業系統及其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。</span><span class="sxs-lookup"><span data-stu-id="95cc5-258">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="95cc5-259">以下是用於句子中的範例：</span><span class="sxs-lookup"><span data-stu-id="95cc5-259">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="95cc5-260">「.NET Core 是 .NET 的跨平台實作。」</span><span class="sxs-lookup"><span data-stu-id="95cc5-260">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="95cc5-261">「PCL 設定檔代表 Microsoft 平台，而 .NET Standard 則無從驗證平台。」</span><span class="sxs-lookup"><span data-stu-id="95cc5-261">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="95cc5-262">.NET 文件經常使用「.NET 平台」來表示 .NET 實作或包含所有實作的 .NET 堆疊。</span><span class="sxs-lookup"><span data-stu-id="95cc5-262">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="95cc5-263">這兩種用法通常會與主要 (OS/硬體) 意義混淆，因此我們計劃從文件中排除這些用法。</span><span class="sxs-lookup"><span data-stu-id="95cc5-263">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="95cc5-264">執行階段</span><span class="sxs-lookup"><span data-stu-id="95cc5-264">runtime</span></span>

<span data-ttu-id="95cc5-265">受管理程式的執行環境。</span><span class="sxs-lookup"><span data-stu-id="95cc5-265">The execution environment for a managed program.</span></span>

<span data-ttu-id="95cc5-266">OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="95cc5-266">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="95cc5-267">以下是 .NET 執行階段的一些範例：</span><span class="sxs-lookup"><span data-stu-id="95cc5-267">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="95cc5-268">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="95cc5-268">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="95cc5-269">Core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="95cc5-269">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="95cc5-270">.NET Native (適用於 UWP)</span><span class="sxs-lookup"><span data-stu-id="95cc5-270">.NET Native (for UWP)</span></span>
- <span data-ttu-id="95cc5-271">Mono 執行階段</span><span class="sxs-lookup"><span data-stu-id="95cc5-271">Mono runtime</span></span>

<span data-ttu-id="95cc5-272">.NET 文件有時會使用「執行階段」來表示 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-272">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="95cc5-273">例如，在下列句子中，「執行階段」應該取代成「實作」：</span><span class="sxs-lookup"><span data-stu-id="95cc5-273">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="95cc5-274">「不同的 .NET 執行階段會實作特定版本的 .NET Standard。」</span><span class="sxs-lookup"><span data-stu-id="95cc5-274">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="95cc5-275">「要在多個執行階段上執行的程式庫應以此架構為目標。」</span><span class="sxs-lookup"><span data-stu-id="95cc5-275">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="95cc5-276">(指的是 .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="95cc5-276">(referring to .NET Standard)</span></span>
- <span data-ttu-id="95cc5-277">「不同的 .NET 執行階段會實作特定版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="95cc5-277">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="95cc5-278">…</span><span class="sxs-lookup"><span data-stu-id="95cc5-278">…</span></span> <span data-ttu-id="95cc5-279">每個 .NET 執行階段版本會宣佈它所支援的最高 .NET Standard 版本...」</span><span class="sxs-lookup"><span data-stu-id="95cc5-279">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="95cc5-280">我們計劃排除這個不一致的用法。</span><span class="sxs-lookup"><span data-stu-id="95cc5-280">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="95cc5-281">堆疊</span><span class="sxs-lookup"><span data-stu-id="95cc5-281">stack</span></span>

<span data-ttu-id="95cc5-282">可搭配使用以建置及執行應用程式的一組程式設計技術。</span><span class="sxs-lookup"><span data-stu-id="95cc5-282">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="95cc5-283">「.NET 堆疊」是指 .NET Standard 和所有 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-283">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="95cc5-284">「一個 .NET 堆疊」一詞可能是指 .NET 的一項實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-284">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="95cc5-285">Target Framework - 目標 Framework</span><span class="sxs-lookup"><span data-stu-id="95cc5-285">target framework</span></span>

<span data-ttu-id="95cc5-286">.NET 應用程式或程式庫依賴的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="95cc5-286">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="95cc5-287">應用程式或程式庫可以將目標設為某個版本的 .NET Standard (例如 .NET Standard 2.0)，這會是跨所有 .NET 實作之一組標準化 API 的規格。</span><span class="sxs-lookup"><span data-stu-id="95cc5-287">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="95cc5-288">應用程式或程式庫也可以將目標設為某個版本的特定 .NET 實作；在此情況下，它可以存取實作特定的 API。</span><span class="sxs-lookup"><span data-stu-id="95cc5-288">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="95cc5-289">例如，以 Xamarin.iOS 為目標的應用程式可以存取 Xamarin 提供的 iOS API 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="95cc5-289">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="95cc5-290">針對某些目標 Framework (例如 .NET Framework)，可用的 API 是由 .NET 實作安裝在系統上的組件所定義，這可能包含應用程式架構 API (例如 ASP.NET、WinForms)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-290">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="95cc5-291">針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，架構 API 是由安裝在應用程式或程式庫中的套件所定義。</span><span class="sxs-lookup"><span data-stu-id="95cc5-291">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="95cc5-292">在此情況下，目標 Framework 會隱含指定一個中繼套件，該套件會參考組成架構的所有套件。</span><span class="sxs-lookup"><span data-stu-id="95cc5-292">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="95cc5-293">請參閱[目標 Framework](frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-293">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="95cc5-294">TFM</span><span class="sxs-lookup"><span data-stu-id="95cc5-294">TFM</span></span>

<span data-ttu-id="95cc5-295">目標 Framework Moniker。</span><span class="sxs-lookup"><span data-stu-id="95cc5-295">Target framework moniker.</span></span>

<span data-ttu-id="95cc5-296">用於指定 .NET 應用程式或程式庫之目標 Framework 的標準化語彙基元格式。</span><span class="sxs-lookup"><span data-stu-id="95cc5-296">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="95cc5-297">目標 Framework 通常會由簡短名稱參考，例如 `net462`。</span><span class="sxs-lookup"><span data-stu-id="95cc5-297">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="95cc5-298">雖然有完整格式的 TFM (例如 .NETFramework,Version=4.6.2)，但通常不會用來指定目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="95cc5-298">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="95cc5-299">請參閱[目標 Framework](frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc5-299">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="95cc5-300">UWP</span><span class="sxs-lookup"><span data-stu-id="95cc5-300">UWP</span></span>

<span data-ttu-id="95cc5-301">通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="95cc5-301">Universal Windows Platform.</span></span>

<span data-ttu-id="95cc5-302">用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="95cc5-302">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="95cc5-303">其設計目的是為了整合您可能想要設為目標的不同裝置類型，包括電腦、平板電腦、平板手機、手機，甚至是 Xbox。</span><span class="sxs-lookup"><span data-stu-id="95cc5-303">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="95cc5-304">UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。</span><span class="sxs-lookup"><span data-stu-id="95cc5-304">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="95cc5-305">您可以使用 C++、C#、VB.NET 和 JavaScript 來撰寫應用程式。</span><span class="sxs-lookup"><span data-stu-id="95cc5-305">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="95cc5-306">使用 C# 和 VB.NET 時，.NET API 是由 .NET Core 所提供。</span><span class="sxs-lookup"><span data-stu-id="95cc5-306">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="95cc5-307">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95cc5-307">See also</span></span>

- [<span data-ttu-id="95cc5-308">.NET 指南</span><span class="sxs-lookup"><span data-stu-id="95cc5-308">.NET Guide</span></span>](index.md)  
- [<span data-ttu-id="95cc5-309">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="95cc5-309">.NET Framework Guide</span></span>](../framework/index.md)  
- [<span data-ttu-id="95cc5-310">.NET Core</span><span class="sxs-lookup"><span data-stu-id="95cc5-310">.NET Core</span></span>](../core/index.md)  
- [<span data-ttu-id="95cc5-311">ASP.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="95cc5-311">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
- [<span data-ttu-id="95cc5-312">ASP.NET Core 概觀</span><span class="sxs-lookup"><span data-stu-id="95cc5-312">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  
