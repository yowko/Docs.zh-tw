---
title: ReadyToRun 部署總覽
description: 瞭解什麼是 ReadyToRun 部署，以及為什麼您應該考慮在使用 .NET 5 和 .NET Core 3.0 和更新版本發行應用程式時使用它。
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: b4052a0c0f4ed9f6cfd273abe5ef45d018bd0ae0
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654958"
---
# <a name="readytorun-compilation"></a><span data-ttu-id="48f42-103">ReadyToRun 編譯</span><span class="sxs-lookup"><span data-stu-id="48f42-103">ReadyToRun Compilation</span></span>

<span data-ttu-id="48f42-104">將您的應用程式元件編譯為 ReadyToRun (R2R) 格式，即可改善 .NET 應用程式啟動時間和延遲。</span><span class="sxs-lookup"><span data-stu-id="48f42-104">.NET application startup time and latency can be improved by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="48f42-105">R2R 是一種預先(AOT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="48f42-105">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="48f42-106">R2R 二進位檔會透過減少 Just-In-Time (JIT) 編譯器在應用程式載入時所需執行的工作量，來改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="48f42-106">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="48f42-107">二進位檔包含的機器碼，與 JIT 所會產生的內容類似。</span><span class="sxs-lookup"><span data-stu-id="48f42-107">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="48f42-108">但是，R2R 二進位檔大小較大，因為它們會同時包含中繼語言 (IL) 程式碼 (在某些案例下仍需要使用)，以及相同程式碼的原生版本。</span><span class="sxs-lookup"><span data-stu-id="48f42-108">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="48f42-109">只有當您發佈以特定執行時間環境為目標的應用程式時，才可使用 R2R， (RID) 例如 Linux x64 或 Windows x64。</span><span class="sxs-lookup"><span data-stu-id="48f42-109">R2R is only available when you publish an app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="48f42-110">若要將您的專案編譯為 ReadyToRun，應用程式必須在 PublishReadyToRun 屬性設定為 true 的情況下發行。</span><span class="sxs-lookup"><span data-stu-id="48f42-110">To compile your project as ReadyToRun, the application must be published with the PublishReadyToRun property set to true.</span></span>

<span data-ttu-id="48f42-111">有兩種方式可以將您的應用程式發佈為 ReadyToRun：</span><span class="sxs-lookup"><span data-stu-id="48f42-111">There are two ways to publish your app as ReadyToRun:</span></span>

01. <span data-ttu-id="48f42-112">直接指定 dotnet publish 命令的 PublishReadyToRun 旗標。</span><span class="sxs-lookup"><span data-stu-id="48f42-112">Specify the PublishReadyToRun flag directly to the dotnet publish command.</span></span> <span data-ttu-id="48f42-113">如需詳細資訊，請參閱 [dotnet publish](../tools/dotnet-publish.md) 。</span><span class="sxs-lookup"><span data-stu-id="48f42-113">See [dotnet publish](../tools/dotnet-publish.md) for details.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. <span data-ttu-id="48f42-114">在專案中指定屬性</span><span class="sxs-lookup"><span data-stu-id="48f42-114">Specify the property in the project</span></span>

    - <span data-ttu-id="48f42-115">將 `<PublishReadyToRun>` 設定新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="48f42-115">Add the `<PublishReadyToRun>` setting to your project.</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - <span data-ttu-id="48f42-116">發佈沒有任何特殊參數的應用程式。</span><span class="sxs-lookup"><span data-stu-id="48f42-116">Publish the application without any special parameters.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a><span data-ttu-id="48f42-117">使用 ReadyToRun 功能的影響</span><span class="sxs-lookup"><span data-stu-id="48f42-117">Impact of using the ReadyToRun feature</span></span>

<span data-ttu-id="48f42-118">預先編譯會對應用程式效能造成複雜的效能影響，這可能很難預測。</span><span class="sxs-lookup"><span data-stu-id="48f42-118">Ahead-of-time compilation has complex performance impact on application performance, which may be difficult to predict.</span></span> <span data-ttu-id="48f42-119">一般情況下，元件的大小會增加到兩到三倍以上。</span><span class="sxs-lookup"><span data-stu-id="48f42-119">In general, the size of an assembly will grow to between two to three times larger.</span></span> <span data-ttu-id="48f42-120">檔案的實體大小增加可能會降低從磁片載入元件的效能，並增加進程的工作集。</span><span class="sxs-lookup"><span data-stu-id="48f42-120">This increase in the physical size of the file may reduce the performance of loading the assembly from disk, and increase working set of the process.</span></span> <span data-ttu-id="48f42-121">不過，在執行時間編譯的方法數目通常會大幅減少。</span><span class="sxs-lookup"><span data-stu-id="48f42-121">However, in return the number of methods compiled at runtime is typically reduced substantially.</span></span> <span data-ttu-id="48f42-122">結果是，大部分的應用程式，大部分的應用程式都能獲得大幅的效能，而不是啟用 ReadyToRun。</span><span class="sxs-lookup"><span data-stu-id="48f42-122">The result is that most applications that large amounts of code receive large performance benefits from enabling ReadyToRun.</span></span> <span data-ttu-id="48f42-123">因為 .NET 執行時間程式庫已經使用 ReadyToRun 先行編譯，所以具有少量程式碼的應用程式可能不會遇到大幅改善的啟用 ReadyToRun。</span><span class="sxs-lookup"><span data-stu-id="48f42-123">Applications, which have small amounts of code will likely not experience a significant improvement from enabling ReadyToRun, as the .NET runtime libraries have already been precompiled with ReadyToRun.</span></span>

<span data-ttu-id="48f42-124">此處所討論的啟始改進不僅適用于應用程式啟動，也適用于應用程式中的任何程式碼首次使用。</span><span class="sxs-lookup"><span data-stu-id="48f42-124">The startup improvement discussed here applies not only to application startup, but also to the first use of any code in the application.</span></span> <span data-ttu-id="48f42-125">比方說，ReadyToRun 可以用來減少在 ASP.NET 應用程式中第一次使用 Web API 時的回應延遲。</span><span class="sxs-lookup"><span data-stu-id="48f42-125">For instance, ReadyToRun can be used to reduce the response latency of the first use  of Web API in an ASP.NET application.</span></span>

### <a name="interaction-with-tiered-compilation"></a><span data-ttu-id="48f42-126">與分層式編譯的互動</span><span class="sxs-lookup"><span data-stu-id="48f42-126">Interaction with tiered compilation</span></span>

<span data-ttu-id="48f42-127">預先產生的並不像 JIT 所產生的程式碼一樣高度優化。</span><span class="sxs-lookup"><span data-stu-id="48f42-127">Ahead-of-time generated is not as highly optimized as code produced by the JIT.</span></span> <span data-ttu-id="48f42-128">為了解決這個問題，階層式編譯會以 JIT 產生的方法取代常用的 ReadyToRun 方法。</span><span class="sxs-lookup"><span data-stu-id="48f42-128">To address this issue, tiered compilation will replace commonly used ReadyToRun methods with JIT-generated methods.</span></span>

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a><span data-ttu-id="48f42-129">如何選擇預先編譯的元件集？</span><span class="sxs-lookup"><span data-stu-id="48f42-129">How is the set of precompiled assemblies chosen?</span></span>

<span data-ttu-id="48f42-130">SDK 將會先行編譯隨應用程式散發的元件。</span><span class="sxs-lookup"><span data-stu-id="48f42-130">The SDK will precompile the assemblies that are distributed with the application.</span></span> <span data-ttu-id="48f42-131">若為獨立應用程式，這組元件將包含架構。</span><span class="sxs-lookup"><span data-stu-id="48f42-131">For self-contained applications, this set of assemblies will include the framework.</span></span> <span data-ttu-id="48f42-132">C + +/CLI 二進位檔不符合 ReadyToRun 編譯的資格。</span><span class="sxs-lookup"><span data-stu-id="48f42-132">C++/CLI binaries are not eligible for ReadyToRun compilation.</span></span>

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a><span data-ttu-id="48f42-133">如何選擇預先編譯的一組方法？</span><span class="sxs-lookup"><span data-stu-id="48f42-133">How is the set of methods to precompile chosen?</span></span>

<span data-ttu-id="48f42-134">編譯器會嘗試預先編譯的方法越多。</span><span class="sxs-lookup"><span data-stu-id="48f42-134">The compiler will attempt to pre-compile as many methods as it can.</span></span> <span data-ttu-id="48f42-135">不過，使用 ReadyToRun 功能時，不應該預期會造成 JIT 無法執行。</span><span class="sxs-lookup"><span data-stu-id="48f42-135">However various reasons it is not expected that using the ReadyToRun feature will result in preventing the JIT from executing.</span></span>

<span data-ttu-id="48f42-136">這類原因可能包括但不限於：</span><span class="sxs-lookup"><span data-stu-id="48f42-136">Such reasons may include, but are not limited to:</span></span>

- <span data-ttu-id="48f42-137">使用在個別元件中定義的泛型型別</span><span class="sxs-lookup"><span data-stu-id="48f42-137">Use of generic types defined in separate assemblies</span></span>
- <span data-ttu-id="48f42-138">使用機器碼進行 Interop</span><span class="sxs-lookup"><span data-stu-id="48f42-138">Interop with native code</span></span>
- <span data-ttu-id="48f42-139">使用編譯器無法證明的硬體內建函式可在目的電腦上安全地使用</span><span class="sxs-lookup"><span data-stu-id="48f42-139">Use of hardware intrinsics that the compiler cannot prove are safe to use on a target machine</span></span>
- <span data-ttu-id="48f42-140">某些不尋常的 IL 模式</span><span class="sxs-lookup"><span data-stu-id="48f42-140">Certain unusual IL patterns</span></span>
- <span data-ttu-id="48f42-141">透過反映或 LINQ 建立動態方法</span><span class="sxs-lookup"><span data-stu-id="48f42-141">Dynamic method creation via reflection, or LINQ</span></span>

## <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="48f42-142">跨平台/架構限制</span><span class="sxs-lookup"><span data-stu-id="48f42-142">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="48f42-143">針對某些 SDK 平臺，ReadyToRun 編譯器可以跨平臺編譯其他目標平臺。</span><span class="sxs-lookup"><span data-stu-id="48f42-143">For some SDK platforms, the ReadyToRun compiler is capable of cross-compiling for other target platforms.</span></span> <span data-ttu-id="48f42-144">下表說明支援的編譯目標。</span><span class="sxs-lookup"><span data-stu-id="48f42-144">Supported compilation targets are described in the table below.</span></span>

| <span data-ttu-id="48f42-145">SDK 平台</span><span class="sxs-lookup"><span data-stu-id="48f42-145">SDK platform</span></span> | <span data-ttu-id="48f42-146">支援的目標平台</span><span class="sxs-lookup"><span data-stu-id="48f42-146">Supported target platforms</span></span> |
| ------------ | --------------------------- |
| <span data-ttu-id="48f42-147">Windows X64</span><span class="sxs-lookup"><span data-stu-id="48f42-147">Windows X64</span></span>  | <span data-ttu-id="48f42-148">Windows X86、Windows X64、Windows ARM32、Windows ARM64</span><span class="sxs-lookup"><span data-stu-id="48f42-148">Windows X86, Windows X64, Windows ARM32, Windows ARM64</span></span> |
| <span data-ttu-id="48f42-149">Windows X86</span><span class="sxs-lookup"><span data-stu-id="48f42-149">Windows X86</span></span>  | <span data-ttu-id="48f42-150">Windows X86、Windows ARM32</span><span class="sxs-lookup"><span data-stu-id="48f42-150">Windows X86, Windows ARM32</span></span> |
| <span data-ttu-id="48f42-151">Linux X64</span><span class="sxs-lookup"><span data-stu-id="48f42-151">Linux X64</span></span>    | <span data-ttu-id="48f42-152">Linux X86、Linux X64、Linux ARM32、Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="48f42-152">Linux X86, Linux X64, Linux ARM32, Linux ARM64</span></span> |
| <span data-ttu-id="48f42-153">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="48f42-153">Linux ARM32</span></span>  | <span data-ttu-id="48f42-154">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="48f42-154">Linux ARM32</span></span> |
| <span data-ttu-id="48f42-155">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="48f42-155">Linux ARM64</span></span>  | <span data-ttu-id="48f42-156">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="48f42-156">Linux ARM64</span></span> |
| <span data-ttu-id="48f42-157">macOS X64</span><span class="sxs-lookup"><span data-stu-id="48f42-157">macOS X64</span></span>    | <span data-ttu-id="48f42-158">macOS X64</span><span class="sxs-lookup"><span data-stu-id="48f42-158">macOS X64</span></span> |
