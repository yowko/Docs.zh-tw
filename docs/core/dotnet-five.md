---
title: .NET 5 的新功能
description: 深入瞭解 .NET 5，這是一個跨平臺和開放原始碼的開發平臺，也就是 .NET Core 的下一次演進。
ms.date: 11/16/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 04f72675744426f7dbc99e5978a9ea4bbb8015b1
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687591"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="ddd20-103">.NET 5 的新功能</span><span class="sxs-lookup"><span data-stu-id="ddd20-103">What's new in .NET 5</span></span>

<span data-ttu-id="ddd20-104">.NET 5.0 是下一個 .NET Core 的主要版本，之後是3.1。</span><span class="sxs-lookup"><span data-stu-id="ddd20-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="ddd20-105">我們將這個新版本的 .NET 5.0 （而不是 .NET Core 4.0）命名為以下兩個原因：</span><span class="sxs-lookup"><span data-stu-id="ddd20-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="ddd20-106">我們略過了版本號碼4.x，以避免與 .NET Framework 4.x 混淆。</span><span class="sxs-lookup"><span data-stu-id="ddd20-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="ddd20-107">我們從名稱中捨棄了「核心」，以強調這是未來的 .NET 主要實作為。</span><span class="sxs-lookup"><span data-stu-id="ddd20-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="ddd20-108">.NET 5.0 支援比 .NET Core 或 .NET Framework 更多類型的應用程式和平臺。</span><span class="sxs-lookup"><span data-stu-id="ddd20-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="ddd20-109">ASP.NET Core 5.0 是以 .NET 5.0 為基礎，但會保留 "Core" 的名稱，以避免與 ASP.NET MVC 5 混淆。</span><span class="sxs-lookup"><span data-stu-id="ddd20-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="ddd20-110">同樣地，Entity Framework Core 5.0 會保留 "Core" 的名稱，以避免與 Entity Framework 5 和6混淆。</span><span class="sxs-lookup"><span data-stu-id="ddd20-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="ddd20-111">相較于 .NET Core 3.1，.NET 5.0 包含下列改進功能和新功能：</span><span class="sxs-lookup"><span data-stu-id="ddd20-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="ddd20-112">C # 更新</span><span class="sxs-lookup"><span data-stu-id="ddd20-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="ddd20-113">F # 更新</span><span class="sxs-lookup"><span data-stu-id="ddd20-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="ddd20-114">Visual Basic 更新</span><span class="sxs-lookup"><span data-stu-id="ddd20-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="ddd20-115"> 新功能的System.Text.Js</span><span class="sxs-lookup"><span data-stu-id="ddd20-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="ddd20-116">單一檔案應用程式</span><span class="sxs-lookup"><span data-stu-id="ddd20-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="ddd20-117">應用程式修剪</span><span class="sxs-lookup"><span data-stu-id="ddd20-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="ddd20-118">Windows ARM64 和 ARM64 內建函式</span><span class="sxs-lookup"><span data-stu-id="ddd20-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="ddd20-119">傾印偵錯工具的工具支援</span><span class="sxs-lookup"><span data-stu-id="ddd20-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="ddd20-120">執行時間程式庫已針對可為[null 的參考型別](../csharp/nullable-references.md)標注80%</span><span class="sxs-lookup"><span data-stu-id="ddd20-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="ddd20-121">效能改進：</span><span class="sxs-lookup"><span data-stu-id="ddd20-121">Performance improvements:</span></span>
  - [<span data-ttu-id="ddd20-122">垃圾收集 (GC) </span><span class="sxs-lookup"><span data-stu-id="ddd20-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="ddd20-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="ddd20-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="ddd20-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="ddd20-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="ddd20-125">非同步 ValueTask 共用</span><span class="sxs-lookup"><span data-stu-id="ddd20-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="ddd20-126">容器大小優化</span><span class="sxs-lookup"><span data-stu-id="ddd20-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="ddd20-127">更多區域</span><span class="sxs-lookup"><span data-stu-id="ddd20-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="ddd20-128">.NET 5.0 不會取代 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ddd20-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="ddd20-129">.NET 5.0 是未來的 .NET 的主要執行，而且仍支援 .NET Framework 4.x。</span><span class="sxs-lookup"><span data-stu-id="ddd20-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="ddd20-130">沒有將下列技術從 .NET Framework 移植到 .NET 5.0 的計畫，但 .NET 5.0 中有替代方案：</span><span class="sxs-lookup"><span data-stu-id="ddd20-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="ddd20-131">技術</span><span class="sxs-lookup"><span data-stu-id="ddd20-131">Technology</span></span>                             | <span data-ttu-id="ddd20-132">建議的替代方案</span><span class="sxs-lookup"><span data-stu-id="ddd20-132">Recommended alternative</span></span>                                                                         |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ddd20-133">Web Form</span><span class="sxs-lookup"><span data-stu-id="ddd20-133">Web Forms</span></span>                              | <span data-ttu-id="ddd20-134">ASP.NET Core [Blazor](/aspnet/core/blazor) 或 [Razor Pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="ddd20-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="ddd20-135">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="ddd20-135">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="ddd20-136">gRPC</span><span class="sxs-lookup"><span data-stu-id="ddd20-136">gRPC</span></span>](/aspnet/core/grpc)                                                                       |
| <span data-ttu-id="ddd20-137">Windows Workflow (WF) </span><span class="sxs-lookup"><span data-stu-id="ddd20-137">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="ddd20-138">開放原始碼 CoreWF</span><span class="sxs-lookup"><span data-stu-id="ddd20-138">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="ddd20-139">.NET 5.0 不會取代 .NET Standard</span><span class="sxs-lookup"><span data-stu-id="ddd20-139">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="ddd20-140">新的應用程式開發可以 `net5.0` 針對所有專案類型（包括類別庫）指定目標 framework 標記 (TFM) 。</span><span class="sxs-lookup"><span data-stu-id="ddd20-140">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="ddd20-141">在 .NET 5 工作負載之間共用程式碼已經過簡化，您只需要 `net5.0` TFM。</span><span class="sxs-lookup"><span data-stu-id="ddd20-141">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="ddd20-142">針對 .NET 5.0 應用程式和程式庫， `net5.0` 目標 Framework 標記 (TFM) 結合和取代 `netcoreapp` 和 `netstandard` tfm。</span><span class="sxs-lookup"><span data-stu-id="ddd20-142">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="ddd20-143">但是，如果您打算在 .NET Framework、.NET Core 和 .NET 5 工作負載之間共用程式碼，您可以指定 `netstandard2.0` 為 TFM。</span><span class="sxs-lookup"><span data-stu-id="ddd20-143">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="ddd20-144">如需詳細資訊，請參閱 [.NET Standard](../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd20-144">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="ddd20-145">C # 更新</span><span class="sxs-lookup"><span data-stu-id="ddd20-145">C# updates</span></span>

<span data-ttu-id="ddd20-146">撰寫 .NET 5 應用程式的開發人員可以存取最新的 c # 版本和功能。</span><span class="sxs-lookup"><span data-stu-id="ddd20-146">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="ddd20-147">.NET 5 與 c # 9 配對，這對語言有許多新功能。</span><span class="sxs-lookup"><span data-stu-id="ddd20-147">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="ddd20-148">以下是一些重點：</span><span class="sxs-lookup"><span data-stu-id="ddd20-148">Here are a few highlights:</span></span>

- <span data-ttu-id="ddd20-149">記錄：具有以值為基礎之相等語義的參考型別，以及新運算式支援的非破壞性變化 `with` 。</span><span class="sxs-lookup"><span data-stu-id="ddd20-149">Records: reference types with value-based equality semantics and non-destructive mutation supported by a new `with` expression.</span></span>
- <span data-ttu-id="ddd20-150">關聯式模式比對：將模式比對功能延伸至關聯評估和運算式的關係運算子，包括邏輯模式-新的關鍵字 `and` 、 `or` 和 `not` 。</span><span class="sxs-lookup"><span data-stu-id="ddd20-150">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="ddd20-151">最上層語句：作為加速採用和學習 c # 的方法，您 `Main` 可以省略方法，並將應用程式視為有效，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ddd20-151">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="ddd20-152">函式指標：語言結構會公開下列中繼語言 (IL) 碼碼： `ldftn` 和 `calli` 。</span><span class="sxs-lookup"><span data-stu-id="ddd20-152">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="ddd20-153">如需可用 c # 9 功能的詳細資訊，請參閱 [c # 9 的新](../csharp/whats-new/csharp-9.md)功能。</span><span class="sxs-lookup"><span data-stu-id="ddd20-153">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="ddd20-154">來源產生器</span><span class="sxs-lookup"><span data-stu-id="ddd20-154">Source generators</span></span>

<span data-ttu-id="ddd20-155">除了一些醒目提示的新 c # 功能之外，來源產生器也會將其轉換成開發人員專案。</span><span class="sxs-lookup"><span data-stu-id="ddd20-155">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="ddd20-156">來源產生器可讓在編譯期間執行的程式碼檢查您的程式，並產生與其余程式碼一起編譯的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="ddd20-156">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="ddd20-157">如需來源產生器的詳細資訊，請參閱 [c # 來源](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) 產生器和 [c # 來源](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)產生器範例簡介。</span><span class="sxs-lookup"><span data-stu-id="ddd20-157">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="ddd20-158">F # 更新</span><span class="sxs-lookup"><span data-stu-id="ddd20-158">F# updates</span></span>

<span data-ttu-id="ddd20-159">F # 是 .NET 功能性程式設計語言，而在 .NET 5 中，開發人員可以存取 F # 5。</span><span class="sxs-lookup"><span data-stu-id="ddd20-159">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="ddd20-160">以下是 F # 5 的幾項新功能：</span><span class="sxs-lookup"><span data-stu-id="ddd20-160">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="ddd20-161">插入字串</span><span class="sxs-lookup"><span data-stu-id="ddd20-161">Interpolated strings</span></span>

<span data-ttu-id="ddd20-162">類似于 c # 中的字串插值，甚至 JavaScript，F # 都支援基本的字串插補。</span><span class="sxs-lookup"><span data-stu-id="ddd20-162">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="ddd20-163">除了基底字元串插補，還有具類型的插補。</span><span class="sxs-lookup"><span data-stu-id="ddd20-163">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="ddd20-164">使用具類型的插補時，指定的類型必須符合格式規範。</span><span class="sxs-lookup"><span data-stu-id="ddd20-164">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="ddd20-165">這類似于 [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) 根據型別安全輸入來格式化字串的函式。</span><span class="sxs-lookup"><span data-stu-id="ddd20-165">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="ddd20-166">Visual Basic 更新</span><span class="sxs-lookup"><span data-stu-id="ddd20-166">Visual Basic updates</span></span>

<span data-ttu-id="ddd20-167">.NET 5 中沒有適用于 Visual Basic 的新語言功能。</span><span class="sxs-lookup"><span data-stu-id="ddd20-167">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="ddd20-168">不過，在 .NET 5 中，Visual Basic 支援延伸至：</span><span class="sxs-lookup"><span data-stu-id="ddd20-168">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="ddd20-169">描述</span><span class="sxs-lookup"><span data-stu-id="ddd20-169">Description</span></span>                            | <span data-ttu-id="ddd20-170">`dotnet new` 參數</span><span class="sxs-lookup"><span data-stu-id="ddd20-170">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="ddd20-171">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ddd20-171">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="ddd20-172">類別庫</span><span class="sxs-lookup"><span data-stu-id="ddd20-172">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="ddd20-173">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="ddd20-173">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="ddd20-174">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="ddd20-174">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="ddd20-175">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="ddd20-175">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="ddd20-176">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="ddd20-176">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="ddd20-177">Windows Forms (WinForms) 應用程式</span><span class="sxs-lookup"><span data-stu-id="ddd20-177">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="ddd20-178">Windows Forms (WinForms) 類別庫</span><span class="sxs-lookup"><span data-stu-id="ddd20-178">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="ddd20-179">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="ddd20-179">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="ddd20-180">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="ddd20-180">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="ddd20-181">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="ddd20-181">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="ddd20-182">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="ddd20-182">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="ddd20-183">如需 .NET CLI 專案範本的詳細資訊，請參閱 [`dotnet new`](tools/dotnet-new.md) 。</span><span class="sxs-lookup"><span data-stu-id="ddd20-183">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="ddd20-184">新功能的 System.Text.Js</span><span class="sxs-lookup"><span data-stu-id="ddd20-184">System.Text.Json new features</span></span>

<span data-ttu-id="ddd20-185">和中有 [System.Text.Js](../standard/serialization/system-text-json-overview.md)的新功能：</span><span class="sxs-lookup"><span data-stu-id="ddd20-185">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="ddd20-186">保留參考並處理迴圈參考</span><span class="sxs-lookup"><span data-stu-id="ddd20-186">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-how-to.md#preserve-references-and-handle-circular-references)
- [<span data-ttu-id="ddd20-187">HttpClient 和 HttpContent 擴充方法</span><span class="sxs-lookup"><span data-stu-id="ddd20-187">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="ddd20-188">以引號允許或寫入數位</span><span class="sxs-lookup"><span data-stu-id="ddd20-188">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-how-to.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="ddd20-189">支援不可變的類型和 c # 9 記錄</span><span class="sxs-lookup"><span data-stu-id="ddd20-189">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-how-to.md#immutable-types-and-records)
- [<span data-ttu-id="ddd20-190">支援非公用屬性存取子</span><span class="sxs-lookup"><span data-stu-id="ddd20-190">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="ddd20-191">支援欄位</span><span class="sxs-lookup"><span data-stu-id="ddd20-191">support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="ddd20-192">有條件地忽略屬性</span><span class="sxs-lookup"><span data-stu-id="ddd20-192">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-how-to.md#ignore-properties)
- [<span data-ttu-id="ddd20-193">支援非字串索引鍵字典</span><span class="sxs-lookup"><span data-stu-id="ddd20-193">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="ddd20-194">允許自訂轉換器處理 null</span><span class="sxs-lookup"><span data-stu-id="ddd20-194">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="ddd20-195">複製 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="ddd20-195">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-how-to.md#copy-jsonserializeroptions)
- [<span data-ttu-id="ddd20-196">使用 web 預設值建立 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="ddd20-196">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-how-to.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a><span data-ttu-id="ddd20-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd20-197">See also</span></span>

- [<span data-ttu-id="ddd20-198">一個 .NET 的旅程</span><span class="sxs-lookup"><span data-stu-id="ddd20-198">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="ddd20-199">.NET 5 的效能改進</span><span class="sxs-lookup"><span data-stu-id="ddd20-199">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [<span data-ttu-id="ddd20-200">下載 .NET SDK</span><span class="sxs-lookup"><span data-stu-id="ddd20-200">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
