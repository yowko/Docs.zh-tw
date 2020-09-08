---
title: .NET Core 到 .NET 5 的演進
description: 深入瞭解 .NET 5，這是一個跨平臺和開放原始碼的開發平臺，也就是 .NET Core 的下一次演進。
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 5e8ed371173ff8b81909ceb071ed93c6b0e1eea5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515840"
---
# <a name="the-evolution-of-net-core-to-net-5"></a><span data-ttu-id="be5e2-103">.NET Core 到 .NET 5 的演進</span><span class="sxs-lookup"><span data-stu-id="be5e2-103">The evolution of .NET Core to .NET 5</span></span>

<span data-ttu-id="be5e2-104">本文將詳細說明 .NET 5 中包含的專案，這是下一個 .NET Core 3.1 版。</span><span class="sxs-lookup"><span data-stu-id="be5e2-104">This article details what is included in .NET 5, which is the next release of .NET Core following 3.1.</span></span> <span data-ttu-id="be5e2-105">版本號碼是5.0，以避免與 .NET Framework 4.x 混淆。</span><span class="sxs-lookup"><span data-stu-id="be5e2-105">The version number is 5.0 to avoid confusion with .NET Framework 4.x.</span></span> <span data-ttu-id="be5e2-106">和 "Core" 會從名稱中卸載，因為它是持續進行的 .NET 主要執行。</span><span class="sxs-lookup"><span data-stu-id="be5e2-106">And "Core" is dropped from the name because it is the main implementation of .NET going forward.</span></span> <span data-ttu-id="be5e2-107">ASP.NET Core 保留 "Core" 的名稱，以避免與 ASP.NET MVC 5 混淆。</span><span class="sxs-lookup"><span data-stu-id="be5e2-107">ASP.NET Core retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="be5e2-108">此外，Entity Framework Core 會保留 "Core" 的名稱，以避免與 Entity Framework 5 和6混淆。</span><span class="sxs-lookup"><span data-stu-id="be5e2-108">Additionally, Entity Framework Core retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span> <span data-ttu-id="be5e2-109">.NET 5 支援的應用程式類型和平臺比 .NET Core 或 .NET Framework 更多。</span><span class="sxs-lookup"><span data-stu-id="be5e2-109">.NET 5 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="be5e2-110">.NET Core 的問世以吸引人的方式發展 .NET 生態系統。</span><span class="sxs-lookup"><span data-stu-id="be5e2-110">The advent of .NET Core has evolved the .NET ecosystem in compelling ways.</span></span> <span data-ttu-id="be5e2-111">它已在 GitHub 上以開放原始碼專案的形式成熟，並可在一段時間後，慶祝誠懇改進。</span><span class="sxs-lookup"><span data-stu-id="be5e2-111">It matured as an open-source project on GitHub, celebrating community contributions, and humbly improving over time.</span></span>

<span data-ttu-id="be5e2-112">.NET Core 有幾個主要特性：</span><span class="sxs-lookup"><span data-stu-id="be5e2-112">.NET Core has several primary characteristics:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="be5e2-113">跨平台</span><span class="sxs-lookup"><span data-stu-id="be5e2-113">Cross-platform</span></span>
> - <span data-ttu-id="be5e2-114">開放原始碼</span><span class="sxs-lookup"><span data-stu-id="be5e2-114">Open-source</span></span>
> - <span data-ttu-id="be5e2-115">並存安裝</span><span class="sxs-lookup"><span data-stu-id="be5e2-115">Side-by-side installation</span></span>
> - <span data-ttu-id="be5e2-116">小型專案檔案 (SDK 樣式的) </span><span class="sxs-lookup"><span data-stu-id="be5e2-116">Small project files (SDK-style)</span></span>
> - <span data-ttu-id="be5e2-117">彈性部署</span><span class="sxs-lookup"><span data-stu-id="be5e2-117">Flexible deployment</span></span>

<span data-ttu-id="be5e2-118">.NET 5 擴充了這些特性，可進行累加式改善：</span><span class="sxs-lookup"><span data-stu-id="be5e2-118">.NET 5 extends these characteristics, making incremental improvements:</span></span>

- <span data-ttu-id="be5e2-119">單一檔案應用程式</span><span class="sxs-lookup"><span data-stu-id="be5e2-119">Single file apps</span></span>
- <span data-ttu-id="be5e2-120">Windows ARM64 和 ARM64 內建函式</span><span class="sxs-lookup"><span data-stu-id="be5e2-120">Windows ARM64, and ARM64 intrinsics</span></span>
- <span data-ttu-id="be5e2-121">的效能改進：</span><span class="sxs-lookup"><span data-stu-id="be5e2-121">Sweeping performance improvements to:</span></span>
  - [<span data-ttu-id="be5e2-122">垃圾收集 (GC) </span><span class="sxs-lookup"><span data-stu-id="be5e2-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="be5e2-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="be5e2-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="be5e2-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="be5e2-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="be5e2-125">非同步 ValueTask 共用</span><span class="sxs-lookup"><span data-stu-id="be5e2-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="be5e2-126">更多區域</span><span class="sxs-lookup"><span data-stu-id="be5e2-126">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- <span data-ttu-id="be5e2-127">容器大小優化</span><span class="sxs-lookup"><span data-stu-id="be5e2-127">Container size optimizations</span></span>
- [<span data-ttu-id="be5e2-128">應用程式修剪</span><span class="sxs-lookup"><span data-stu-id="be5e2-128">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [<span data-ttu-id="be5e2-129">C # 編譯器增強功能</span><span class="sxs-lookup"><span data-stu-id="be5e2-129">C# compiler enhancements</span></span>](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- <span data-ttu-id="be5e2-130">傾印偵錯工具的工具支援</span><span class="sxs-lookup"><span data-stu-id="be5e2-130">Tooling support for dump debugging</span></span>
- <span data-ttu-id="be5e2-131">平臺是以[可為 null 的參考](../csharp/nullable-references.md)型別標注的80%</span><span class="sxs-lookup"><span data-stu-id="be5e2-131">Platform is 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>

### <a name="what-net-5-is-not"></a><span data-ttu-id="be5e2-132">什麼是 .NET 5</span><span class="sxs-lookup"><span data-stu-id="be5e2-132">What .NET 5 is not</span></span>

<span data-ttu-id="be5e2-133">.NET 5 不是 .NET Framework 的替代方案。</span><span class="sxs-lookup"><span data-stu-id="be5e2-133">.NET 5 is not a replacement for .NET Framework.</span></span> <span data-ttu-id="be5e2-134">沒有將下列技術從 .NET Framework 移植到 .NET 5 的計畫，但 .NET 5 中包含支援的替代方案：</span><span class="sxs-lookup"><span data-stu-id="be5e2-134">There are no plans to port the following technologies from .NET Framework to .NET 5, but there are supported alternatives included in .NET 5:</span></span>

| <span data-ttu-id="be5e2-135">技術</span><span class="sxs-lookup"><span data-stu-id="be5e2-135">Technology</span></span>                             | <span data-ttu-id="be5e2-136">建議</span><span class="sxs-lookup"><span data-stu-id="be5e2-136">Recommendation</span></span>                                              |
|----------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="be5e2-137">Web Form</span><span class="sxs-lookup"><span data-stu-id="be5e2-137">Web Forms</span></span>                              | [<span data-ttu-id="be5e2-138">ASP.NET Core Blazor</span><span class="sxs-lookup"><span data-stu-id="be5e2-138">ASP.NET Core Blazor</span></span>](/aspnet/core/blazor)                  |
| <span data-ttu-id="be5e2-139">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="be5e2-139">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="be5e2-140">gRPC</span><span class="sxs-lookup"><span data-stu-id="be5e2-140">gRPC</span></span>](/aspnet/core/grpc)                                   |
| <span data-ttu-id="be5e2-141">Windows Workflow (WF) </span><span class="sxs-lookup"><span data-stu-id="be5e2-141">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="be5e2-142">開放原始碼 CoreWF</span><span class="sxs-lookup"><span data-stu-id="be5e2-142">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a><span data-ttu-id="be5e2-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="be5e2-143">.NET Standard</span></span>

<span data-ttu-id="be5e2-144">新的應用程式開發可以 `net5.0` 針對所有專案類型（包括類別庫）指定目標 framework 標記 (TFM) 。</span><span class="sxs-lookup"><span data-stu-id="be5e2-144">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="be5e2-145">在 .NET 5 工作負載之間共用程式碼已經過簡化，您只需要 `net5.0` TFM。</span><span class="sxs-lookup"><span data-stu-id="be5e2-145">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="be5e2-146">`net5.0`TFM 結合和取代 `netcoreapp` 和 `netstandard` 名稱。</span><span class="sxs-lookup"><span data-stu-id="be5e2-146">The `net5.0` TFM combines and replaces `netcoreapp` and `netstandard` names.</span></span> <span data-ttu-id="be5e2-147">這種 TFM 通常只包含可跨平臺運作的技術，例如使用 .NET Standard 完成。</span><span class="sxs-lookup"><span data-stu-id="be5e2-147">This TFM will generally only include technologies that work cross-platform, like was done with .NET Standard.</span></span> <span data-ttu-id="be5e2-148">但是，如果您打算在 .NET Framework、.NET Core 和 .NET 5 工作負載之間共用程式碼，您可以藉由指定 TFM 來進行 `netstandard2.0` 。</span><span class="sxs-lookup"><span data-stu-id="be5e2-148">However, if you're planning on sharing code between .NET Framework, .NET Core, and .NET 5 workloads - you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="be5e2-149">如需詳細資訊，請參閱 [如何指定目標 framework](../standard/frameworks.md#how-to-specify-target-frameworks)。</span><span class="sxs-lookup"><span data-stu-id="be5e2-149">For more information, see [How to specify target frameworks](../standard/frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="language-updates"></a><span data-ttu-id="be5e2-150">語言更新</span><span class="sxs-lookup"><span data-stu-id="be5e2-150">Language updates</span></span>

<span data-ttu-id="be5e2-151">使用 .NET 5，.NET 程式設計語言仍會持續改進。</span><span class="sxs-lookup"><span data-stu-id="be5e2-151">With .NET 5, the .NET programming languages are continuing to improve.</span></span>

### <a name="c-updates"></a><span data-ttu-id="be5e2-152">C # 更新</span><span class="sxs-lookup"><span data-stu-id="be5e2-152">C# updates</span></span>

<span data-ttu-id="be5e2-153">撰寫 .NET 5 應用程式的開發人員可以存取最新的 c # 版本和功能。</span><span class="sxs-lookup"><span data-stu-id="be5e2-153">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="be5e2-154">.NET 5 與 c # 9 配對。</span><span class="sxs-lookup"><span data-stu-id="be5e2-154">.NET 5 is paired with C# 9.</span></span> <span data-ttu-id="be5e2-155">C # 9 將許多新功能帶入語言，以下提供一些重點：</span><span class="sxs-lookup"><span data-stu-id="be5e2-155">C# 9 brings many new features to the language, here are a few highlights:</span></span>

- <span data-ttu-id="be5e2-156">記錄：行為類似實值型別的不可變引用型別，並且會在語言中引入新的 `with` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="be5e2-156">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="be5e2-157">關聯式模式比對：將模式比對功能延伸至關聯評估和運算式的關係運算子，包括邏輯模式-新的關鍵字 `and` 、 `or` 和 `not` 。</span><span class="sxs-lookup"><span data-stu-id="be5e2-157">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="be5e2-158">最上層語句：作為加速採用和學習 c # 的方法，您 `Main` 可以省略方法，並將應用程式視為有效，如下所示：</span><span class="sxs-lookup"><span data-stu-id="be5e2-158">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="be5e2-159">函式指標：語言結構會公開下列中繼語言 (IL) 碼碼： `ldftn` 和 `calli` 。</span><span class="sxs-lookup"><span data-stu-id="be5e2-159">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="be5e2-160">如需可用 c # 9 功能的詳細資訊，請參閱 [c # 9 的新](../csharp/whats-new/csharp-9.md)功能。</span><span class="sxs-lookup"><span data-stu-id="be5e2-160">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

#### <a name="source-generators"></a><span data-ttu-id="be5e2-161">來源產生器</span><span class="sxs-lookup"><span data-stu-id="be5e2-161">Source generators</span></span>

<span data-ttu-id="be5e2-162">除了一些醒目提示的新 c # 功能之外，來源產生器也會將其轉換成開發人員專案。</span><span class="sxs-lookup"><span data-stu-id="be5e2-162">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="be5e2-163">來源產生器可讓在編譯期間執行的程式碼檢查您的程式，並產生與其余程式碼一起編譯的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="be5e2-163">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="be5e2-164">如需來源產生器的詳細資訊，請參閱 [c # 來源](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) 產生器和 [c # 來源](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)產生器範例簡介。</span><span class="sxs-lookup"><span data-stu-id="be5e2-164">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

### <a name="f-updates"></a><span data-ttu-id="be5e2-165">F # 更新</span><span class="sxs-lookup"><span data-stu-id="be5e2-165">F# updates</span></span>

<span data-ttu-id="be5e2-166">F # 是 .NET 功能性程式設計語言，而在 .NET 5 中，開發人員可以存取 F # 5。</span><span class="sxs-lookup"><span data-stu-id="be5e2-166">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="be5e2-167">以下是 F # 5 的幾項新功能：</span><span class="sxs-lookup"><span data-stu-id="be5e2-167">Here are several new features of F# 5:</span></span>

#### <a name="interpolated-strings"></a><span data-ttu-id="be5e2-168">插入字串</span><span class="sxs-lookup"><span data-stu-id="be5e2-168">Interpolated strings</span></span>

<span data-ttu-id="be5e2-169">類似于 c # 中的字串插值，甚至 JavaScript-F # 都支援基本的字串插補。</span><span class="sxs-lookup"><span data-stu-id="be5e2-169">Similar to interpolated string in C#, and even JavaScript - F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="be5e2-170">除了基底字元串插補，還有具類型的插補。</span><span class="sxs-lookup"><span data-stu-id="be5e2-170">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="be5e2-171">使用具類型的插補時，指定的類型必須符合格式規範。</span><span class="sxs-lookup"><span data-stu-id="be5e2-171">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="be5e2-172">這類似于 [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) 根據型別安全輸入來格式化字串的函式。</span><span class="sxs-lookup"><span data-stu-id="be5e2-172">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

### <a name="visual-basic-updates"></a><span data-ttu-id="be5e2-173">Visual Basic 更新</span><span class="sxs-lookup"><span data-stu-id="be5e2-173">Visual Basic updates</span></span>

<span data-ttu-id="be5e2-174">.NET 5 中沒有適用于 Visual Basic 的新語言功能。</span><span class="sxs-lookup"><span data-stu-id="be5e2-174">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="be5e2-175">不過，在 .NET 5 中，Visual Basic 支援延伸至：</span><span class="sxs-lookup"><span data-stu-id="be5e2-175">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="be5e2-176">描述</span><span class="sxs-lookup"><span data-stu-id="be5e2-176">Description</span></span>                            | <span data-ttu-id="be5e2-177">`dotnet new` 參數</span><span class="sxs-lookup"><span data-stu-id="be5e2-177">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="be5e2-178">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="be5e2-178">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="be5e2-179">類別庫</span><span class="sxs-lookup"><span data-stu-id="be5e2-179">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="be5e2-180">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="be5e2-180">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="be5e2-181">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="be5e2-181">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="be5e2-182">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="be5e2-182">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="be5e2-183">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="be5e2-183">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="be5e2-184">Windows Forms (WinForms) 應用程式</span><span class="sxs-lookup"><span data-stu-id="be5e2-184">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="be5e2-185">Windows Forms (WinForms) 類別庫</span><span class="sxs-lookup"><span data-stu-id="be5e2-185">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="be5e2-186">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="be5e2-186">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="be5e2-187">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="be5e2-187">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="be5e2-188">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="be5e2-188">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="be5e2-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="be5e2-189">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="be5e2-190">如需 .NET CLI 專案範本的詳細資訊，請參閱 [`dotnet new`](tools/dotnet-new.md) 。</span><span class="sxs-lookup"><span data-stu-id="be5e2-190">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="net-maui"></a><span data-ttu-id="be5e2-191">.NET MAUI</span><span class="sxs-lookup"><span data-stu-id="be5e2-191">.NET MAUI</span></span>

<span data-ttu-id="be5e2-192">.NET MAUI 是日益普及的 Xamarin 工具組演進，在 GitHub 上的開放原始碼位於 [dotnet/MAUI](https://github.com/dotnet/maui)。</span><span class="sxs-lookup"><span data-stu-id="be5e2-192">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="be5e2-193">使用 .NET MAUI，可簡化 .NET 開發人員的選擇，提供支援所有新式工作負載的單一堆疊： Android、iOS、macOS 和 Windows。</span><span class="sxs-lookup"><span data-stu-id="be5e2-193">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="be5e2-194">使用 .NET MAUI，您可以取得以多個平臺和裝置為目標的單一專案開發人員體驗。</span><span class="sxs-lookup"><span data-stu-id="be5e2-194">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be5e2-195">.NET MAUI 是早期預覽版本。</span><span class="sxs-lookup"><span data-stu-id="be5e2-195">.NET MAUI is in early preview.</span></span> <span data-ttu-id="be5e2-196">您可以在 [xamarin/net6](https://github.com/xamarin/net6-samples)範例中找到範例原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="be5e2-196">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="be5e2-197">模型-視圖-更新模式</span><span class="sxs-lookup"><span data-stu-id="be5e2-197">Model-View-Update pattern</span></span>

<span data-ttu-id="be5e2-198">開發人員喜歡新式開發模式。</span><span class="sxs-lookup"><span data-stu-id="be5e2-198">Developers love modern development patterns.</span></span> <span data-ttu-id="be5e2-199">「榆樹架構」是一種流暢的 UI 開發方法，它是 [模型視圖-更新](https://elmprogramming.com/model-view-update-part-1.html) 或 MVU 模式。</span><span class="sxs-lookup"><span data-stu-id="be5e2-199">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="be5e2-200">MVU 可提升資料和狀態管理的單向流程，以及程式碼優先的開發經驗，只要套用必要的變更，就能快速更新 UI。</span><span class="sxs-lookup"><span data-stu-id="be5e2-200">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="be5e2-201">例如，請考慮使用 MVU 模式，以 .NET MAUI 撰寫的下列計數器：</span><span class="sxs-lookup"><span data-stu-id="be5e2-201">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

```csharp
readonly State<int> _count = 0;

[Body]
View body() => new StackLayout
{
    new Label("Welcome to .NET MAUI!"),
    new Button(
        () => $"You clicked {_count} times.",
        () => ++ _count.Value)
    )
};
```

<span data-ttu-id="be5e2-202">如需詳細資訊，請參閱 [.NET MAUI 藍圖](https://github.com/dotnet/maui/wiki/Roadmap)和 [.net MAUI 簡介](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) 文章。</span><span class="sxs-lookup"><span data-stu-id="be5e2-202">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="be5e2-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be5e2-203">See also</span></span>

- [<span data-ttu-id="be5e2-204">一個 .NET 的旅程</span><span class="sxs-lookup"><span data-stu-id="be5e2-204">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="be5e2-205">.NET 5 的效能改進</span><span class="sxs-lookup"><span data-stu-id="be5e2-205">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
