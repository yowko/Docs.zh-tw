---
title: .NET Core 3.0 的新功能
description: 了解 .NET Core 3.0 所提供的新功能。
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: 89264098ed17b398c83bc2dcddd98d9d8fc958f7
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679732"
---
# <a name="whats-new-in-net-core-30-preview-2"></a><span data-ttu-id="5340b-103">.NET Core 3.0 (Preview 2) 的新功能</span><span class="sxs-lookup"><span data-stu-id="5340b-103">What's new in .NET Core 3.0 (Preview 2)</span></span>

<span data-ttu-id="5340b-104">本文描述 .NET Core 3.0 (Preview 2) 的新功能。</span><span class="sxs-lookup"><span data-stu-id="5340b-104">This article describes what is new in .NET Core 3.0 (preview 2).</span></span> <span data-ttu-id="5340b-105">其中一個最大的增強功能是對 Windows 傳統型應用程式的支援 (僅限 Windows)。</span><span class="sxs-lookup"><span data-stu-id="5340b-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="5340b-106">您可以運用名為「Windows 傳統型」的 .NET Core 3.0 SDK 元件來移植 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5340b-106">By utilizing a .NET Core 3.0 SDK component called Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="5340b-107">具體而言，只有在 Windows 上才支援並包含「Windows 傳統型」元件。</span><span class="sxs-lookup"><span data-stu-id="5340b-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="5340b-108">如需詳細資訊，請參閱下面的 [Windows 傳統型](#windows-desktop)一節。</span><span class="sxs-lookup"><span data-stu-id="5340b-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="5340b-109">.NET Core 3.0 新增 C# 8.0 支援。</span><span class="sxs-lookup"><span data-stu-id="5340b-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="5340b-110">立即在 Windows、Mac 及 Linux 上[下載並開始使用 .NET Core 3.0 Preview 2](https://aka.ms/netcore3download)。</span><span class="sxs-lookup"><span data-stu-id="5340b-110">[Download and get started with .NET Core 3.0 Preview 2](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="5340b-111">您可以在 [.NET Core 3.0 Preview 2 版本資訊](https://aka.ms/netcore3releasenotes)中查看完整的版本詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5340b-111">You can see complete details of the release in the [.NET Core 3.0 Preview 2 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="5340b-112">如需各版本發行內容的詳細資訊，請參閱下列公告：</span><span class="sxs-lookup"><span data-stu-id="5340b-112">For more information about what was released with each version, see the following announcements:</span></span>

- [<span data-ttu-id="5340b-113">.NET Core 3.0 Preview 1 公告</span><span class="sxs-lookup"><span data-stu-id="5340b-113">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [<span data-ttu-id="5340b-114">.NET Core 3.0 Preview 2 公告</span><span class="sxs-lookup"><span data-stu-id="5340b-114">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)

## <a name="c-8"></a><span data-ttu-id="5340b-115">C# 8</span><span class="sxs-lookup"><span data-stu-id="5340b-115">C# 8</span></span>

<span data-ttu-id="5340b-116">.NET Core 3.0 支援 C#8，並從 .NET Core 3.0 Preview 2 開始，支援這些新功能。</span><span class="sxs-lookup"><span data-stu-id="5340b-116">.NET Core 3.0 supports C# 8, and as of .NET Core 3.0 Preview 2, supports these new features.</span></span> <span data-ttu-id="5340b-117">如需 C# 8.0 功能的詳細資訊，請參閱下列部落格文章：</span><span class="sxs-lookup"><span data-stu-id="5340b-117">For more information about C# 8.0 features, see the following blog posts:</span></span>

- [<span data-ttu-id="5340b-118">Do more with patterns in C# 8.0</span><span class="sxs-lookup"><span data-stu-id="5340b-118">Do more with patterns in C# 8.0</span></span>](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)
- [<span data-ttu-id="5340b-119">Take C# 8.0 for a spin</span><span class="sxs-lookup"><span data-stu-id="5340b-119">Take C# 8.0 for a spin</span></span>](https://devblogs.microsoft.com/dotnet/take-c-8-0-for-a-spin/)
- [<span data-ttu-id="5340b-120">Building C# 8.0</span><span class="sxs-lookup"><span data-stu-id="5340b-120">Building C# 8.0</span></span>](https://devblogs.microsoft.com/dotnet/building-c-8-0/)


### <a name="ranges-and-indices"></a><span data-ttu-id="5340b-121">範圍和索引</span><span class="sxs-lookup"><span data-stu-id="5340b-121">Ranges and indices</span></span>

<span data-ttu-id="5340b-122">新的 `Index` 類型可用於編製索引。</span><span class="sxs-lookup"><span data-stu-id="5340b-122">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="5340b-123">您可以從會從開頭算起的 `int` 或使用會從結尾算起的前置詞 `^` 運算子 (C#)，來建立一個索引：</span><span class="sxs-lookup"><span data-stu-id="5340b-123">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="5340b-124">此外，還有 `Range` 類型，此類型由兩個 `Index` 值所組成 (一個代表開頭，一個代表結尾)，並可用 `x..y` 範圍運算式 (C#) 來撰寫。</span><span class="sxs-lookup"><span data-stu-id="5340b-124">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="5340b-125">您可以接著使用 `Range` 來編製索引以產生配量：</span><span class="sxs-lookup"><span data-stu-id="5340b-125">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a><span data-ttu-id="5340b-126">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="5340b-126">Async streams</span></span>

<span data-ttu-id="5340b-127">`IAsyncEnumerable<T>` 類型是 `IEnumerable<T>` 的新非同步版本。</span><span class="sxs-lookup"><span data-stu-id="5340b-127">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="5340b-128">此語言可讓您透過 `IAsyncEnumerable<T>` 執行 `await foreach` 以取用其元素，然後對它們使用 `yield return` 以產生元素。</span><span class="sxs-lookup"><span data-stu-id="5340b-128">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="5340b-129">下列範例同時示範如何產生和取用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="5340b-129">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="5340b-130">`foreach` 是非同步陳述式，其本身會使用 `yield return` 來為呼叫端產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="5340b-130">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="5340b-131">此模式 (使用 `yield return`) 是針對產生非同步資料流建議採用的模型。</span><span class="sxs-lookup"><span data-stu-id="5340b-131">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="5340b-132">除了能夠執行 `await foreach` 之外，您也可以建立非同步迭代器，例如建立一個會傳回 `IAsyncEnumerable/IAsyncEnumerator` 以供您在其中執行 `await` 和 `yield` 的迭代器。</span><span class="sxs-lookup"><span data-stu-id="5340b-132">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="5340b-133">針對需要處置的物件，您可以使用各種 BCL 類型 (例如 `Stream` 和 `Timer`) 所實作的 `IAsyncDisposable`。</span><span class="sxs-lookup"><span data-stu-id="5340b-133">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

>[!NOTE]
><span data-ttu-id="5340b-134">如果您想要使用 Visual Studio 2019 Preview 2 或最新預覽版的 [ C# 延伸模組 (適用於 Visual Studio Code)](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5) 進行開發，則需要 .NET Core 3.0 Preview 2，才能使用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="5340b-134">You need .NET Core 3.0 Preview 2 to use async streams if you want to develop with either Visual Studio 2019 Preview 2 or the latest preview of the [C# extension for Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span></span> <span data-ttu-id="5340b-135">如果您是在命令列使用.NET Core 3.0 Preview 2，則一切將會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="5340b-135">If you are using .NET Core 3.0 Preview 2 at the command line, then everything will work as expected.</span></span>

### <a name="using-declarations"></a><span data-ttu-id="5340b-136">Using 宣告</span><span class="sxs-lookup"><span data-stu-id="5340b-136">Using Declarations</span></span>

<span data-ttu-id="5340b-137">*Using 宣告*是確保適當處置您物件的新方式。</span><span class="sxs-lookup"><span data-stu-id="5340b-137">*Using declarations* are a new way to ensure your object is properly disposed.</span></span> <span data-ttu-id="5340b-138">*using 宣告*可在物件仍在範圍內時保持其持續運作。</span><span class="sxs-lookup"><span data-stu-id="5340b-138">A *using declaration* keeps the object alive while it is still in scope.</span></span> <span data-ttu-id="5340b-139">一旦物件超出範圍，就會自動處置它。</span><span class="sxs-lookup"><span data-stu-id="5340b-139">Once the object becomes out of scope, it is automatically disposed.</span></span> <span data-ttu-id="5340b-140">這會減少巢狀 *using 陳述式*，並讓您的程式碼更簡潔。</span><span class="sxs-lookup"><span data-stu-id="5340b-140">This will reduce nested *using statements* and make your code cleaner.</span></span>

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a><span data-ttu-id="5340b-141">Switch 運算式</span><span class="sxs-lookup"><span data-stu-id="5340b-141">Switch Expressions</span></span>

<span data-ttu-id="5340b-142">*Switch 運算式*是執行 *switch 陳述式*的更簡潔方式，但是，因為它是運算式，所以會傳回一值。</span><span class="sxs-lookup"><span data-stu-id="5340b-142">*Switch expressions* are a cleaner way of doing a *switch statement* but, since it's an expression, returns a value.</span></span> <span data-ttu-id="5340b-143">*Switch 運算式*也會與模式比對完全整合，並使用捨棄模式 `_` 來代表 `default` 值。</span><span class="sxs-lookup"><span data-stu-id="5340b-143">*Switch expressions* are also fully integrated with pattern matching, and use the discard pattern, `_`, to represent the `default` value.</span></span>

<span data-ttu-id="5340b-144">您可在在下列範例中看到 *switch 運算式* 的語法：</span><span class="sxs-lookup"><span data-stu-id="5340b-144">You can see the syntax for *switch expressions* in the following example:</span></span>

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

<span data-ttu-id="5340b-145">在此範例中，播放時有兩種模式。</span><span class="sxs-lookup"><span data-stu-id="5340b-145">There are two patterns at play in this example.</span></span> <span data-ttu-id="5340b-146">`o` 首先會與 `Point` *類型模式*比對，然後與 *{大括號}* 內的*屬性模式*比對。</span><span class="sxs-lookup"><span data-stu-id="5340b-146">`o` first matches with the `Point` *type pattern* and then with the *property pattern* inside the *{curly braces}*.</span></span> <span data-ttu-id="5340b-147">`_` 描述 `discard pattern`，其與 *switch* 陳述式 的 `default` 相同。</span><span class="sxs-lookup"><span data-stu-id="5340b-147">The `_` describes the `discard pattern`, which is the same as `default` for *switch statements*.</span></span>

<span data-ttu-id="5340b-148">模式可讓您撰寫宣告式程式碼，擷取您的意圖，而不是為它實作測試的程序性程式碼。</span><span class="sxs-lookup"><span data-stu-id="5340b-148">Patterns enable you to write declarative code that captures your intent instead of procedural code that implements tests for it.</span></span> <span data-ttu-id="5340b-149">編譯器會負責實作該無趣的程序性程式碼，並保證一律正確執行。</span><span class="sxs-lookup"><span data-stu-id="5340b-149">The compiler becomes responsible for implementing that boring procedural code and is guaranteed to always do it correctly.</span></span>

<span data-ttu-id="5340b-150">仍有一些情況，*switch 陳述式*比起 *switch 運算式*將是更好的選擇，而且模式可與這兩種語法樣式搭配使用。</span><span class="sxs-lookup"><span data-stu-id="5340b-150">There will still be cases where *switch statements* will be a better choice than *switch expressions* and patterns can be used with both syntax styles.</span></span>

<span data-ttu-id="5340b-151">如需詳細資訊，請參閱 [Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)。</span><span class="sxs-lookup"><span data-stu-id="5340b-151">For more information, see [Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="5340b-152">IEEE 浮點增強功能</span><span class="sxs-lookup"><span data-stu-id="5340b-152">IEEE Floating-point improvements</span></span>

<span data-ttu-id="5340b-153">正在更新浮點 API，以遵守 [IEEE 754-2008 修訂](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)。</span><span class="sxs-lookup"><span data-stu-id="5340b-153">Floating point APIs are in the process of being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="5340b-154">這些變更的目標是公開所有的必要作業，並確定它們在行為上符合 IEEE 規格。</span><span class="sxs-lookup"><span data-stu-id="5340b-154">The goal of these changes is to expose all "required" operations and ensure that they are behaviorally compliant with the IEEE spec.</span></span>

<span data-ttu-id="5340b-155">剖析與格式化修正：</span><span class="sxs-lookup"><span data-stu-id="5340b-155">Parsing and formatting fixes:</span></span>

* <span data-ttu-id="5340b-156">正確地剖析並捨入任意長度的輸入。</span><span class="sxs-lookup"><span data-stu-id="5340b-156">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="5340b-157">正確地剖析並格式化負零。</span><span class="sxs-lookup"><span data-stu-id="5340b-157">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="5340b-158">正確地剖析無限大和 NaN，方法為執行不區分大小寫的檢查，並允許適當時在前面選擇性加上 `+`。</span><span class="sxs-lookup"><span data-stu-id="5340b-158">Correctly parse Infinity and NaN by performing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="5340b-159">新的數學 API 具有：</span><span class="sxs-lookup"><span data-stu-id="5340b-159">New Math APIs have:</span></span>

* `BitIncrement/BitDecrement`\
<span data-ttu-id="5340b-160">對應至 `nextUp` 和 `nextDown` IEEE 作業。</span><span class="sxs-lookup"><span data-stu-id="5340b-160">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="5340b-161">它們會傳回最小浮點數，比較大於或小於輸入 (分別)。</span><span class="sxs-lookup"><span data-stu-id="5340b-161">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="5340b-162">例如，`Math.BitIncrement(0.0)` 會傳回 `double.Epsilon`。</span><span class="sxs-lookup"><span data-stu-id="5340b-162">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* `MaxMagnitude/MinMagnitude`\
<span data-ttu-id="5340b-163">對應至 `maxNumMag` 和 `minNumMag`IEEE 作業，它們傳回的值大於或小於兩個輸入的範圍 (分別)。</span><span class="sxs-lookup"><span data-stu-id="5340b-163">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="5340b-164">例如，`Math.MaxMagnitude(2.0, -3.0)` 會傳回 `-3.0`。</span><span class="sxs-lookup"><span data-stu-id="5340b-164">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* `ILogB`\
<span data-ttu-id="5340b-165">對應至傳回整數值的 `logB` IEEE 作業，它會傳回輸入參數的對數，以整數 2 為底數。</span><span class="sxs-lookup"><span data-stu-id="5340b-165">Corresponds to the `logB` IEEE operation which returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="5340b-166">這實際上與 `floor(log2(x))` 相同，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="5340b-166">This is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* `ScaleB`\
<span data-ttu-id="5340b-167">對應至採用整數值的 `scaleB` IEEE 作業，它會有效傳回 `x * pow(2, n)`，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="5340b-167">Corresponds to the `scaleB` IEEE operation which takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* `Log2`\
<span data-ttu-id="5340b-168">對應至 `log2` IEEE 作業，它會傳回 2 為底數的對數。</span><span class="sxs-lookup"><span data-stu-id="5340b-168">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="5340b-169">它會將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="5340b-169">It minimizes rounding error.</span></span>

* `FusedMultiplyAdd`\
<span data-ttu-id="5340b-170">對應至 `fma` IEEE 作業，它會執行融合的乘積和。</span><span class="sxs-lookup"><span data-stu-id="5340b-170">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="5340b-171">亦即，它會將 `(x * y) + z` 當作單一作業來執行，藉此將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="5340b-171">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="5340b-172">範例將是傳回 `1e308` 的 `FusedMultiplyAdd(1e308, 2.0, -1e308)`。</span><span class="sxs-lookup"><span data-stu-id="5340b-172">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="5340b-173">一般 `(1e308 * 2.0) - 1e308` 會傳回 `double.PositiveInfinity`。</span><span class="sxs-lookup"><span data-stu-id="5340b-173">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* `CopySign`\
<span data-ttu-id="5340b-174">對應至 `copySign` IEEE 作業，它會傳回 `x` 的值，但具有 `y` 的符號。</span><span class="sxs-lookup"><span data-stu-id="5340b-174">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="5340b-175">.NET 平台相依內建</span><span class="sxs-lookup"><span data-stu-id="5340b-175">.NET Platform Dependent Intrinsics</span></span>

<span data-ttu-id="5340b-176">已新增 API，允許存取特定效能導向的 CPU 指令，例如 **SIMD** 或**位元操作指令**集合。</span><span class="sxs-lookup"><span data-stu-id="5340b-176">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="5340b-177">這些指令可協助您在某些情況 (例如有效率地平行處理資料) 下大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="5340b-177">These instructions can help achieve big performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> <span data-ttu-id="5340b-178">除了公開 API 供您的程式使用外，.NET 程式庫也已開始使用這些指令來提升效能。</span><span class="sxs-lookup"><span data-stu-id="5340b-178">In addition to exposing the APIs for your programs to use, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="5340b-179">下列 CoreCLR PR 透過實作或使用來示範一些指令：</span><span class="sxs-lookup"><span data-stu-id="5340b-179">The following CoreCLR PRs demonstrate a few of the intrinsics, either via implementation or use:</span></span>

* [<span data-ttu-id="5340b-180">實作簡單 SSE2 硬體內建</span><span class="sxs-lookup"><span data-stu-id="5340b-180">Implement simple SSE2 hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15585)
* [<span data-ttu-id="5340b-181">實作 SSE 硬體內建</span><span class="sxs-lookup"><span data-stu-id="5340b-181">Implement the SSE hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15538)
* [<span data-ttu-id="5340b-182">Arm64 基礎硬體內建</span><span class="sxs-lookup"><span data-stu-id="5340b-182">Arm64 Base HW Intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/16822)
* [<span data-ttu-id="5340b-183">針對 Locate{First|Last}Found{Byte|Char} 使用 TZCNT 和 LZCNT</span><span class="sxs-lookup"><span data-stu-id="5340b-183">Use TZCNT and LZCNT for Locate{First|Last}Found{Byte|Char}</span></span>](https://github.com/dotnet/coreclr/pull/21073)

<span data-ttu-id="5340b-184">如需詳細資訊，請參閱 [.NET 平台相依內建](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)，其會定義用於定義此硬體基礎結構的方法，允許 Microsoft、晶片廠商或任何其他公司或個體可以定義應該公開給 .NET 程式碼的硬體/晶片 API。</span><span class="sxs-lookup"><span data-stu-id="5340b-184">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), which defines an approach for defining this hardware infrastructure, allowing Microsoft, chip vendors, or any other company or individual to define hardware/chip APIs that should be exposed to .NET code.</span></span>

## <a name="default-executables"></a><span data-ttu-id="5340b-185">預設可執行檔</span><span class="sxs-lookup"><span data-stu-id="5340b-185">Default executables</span></span>

<span data-ttu-id="5340b-186">.NET Core 現在預設將會建置 [Framework 依存性可執行檔](../deploying/index.md#framework-dependent-executables-fde)。</span><span class="sxs-lookup"><span data-stu-id="5340b-186">.NET Core will now build [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="5340b-187">這對於使用 .NET Core 全域安裝版本的應用程式來說，是一項新功能。</span><span class="sxs-lookup"><span data-stu-id="5340b-187">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="5340b-188">到目前為止，只有[獨立式部署](../deploying/index.md#self-contained-deployments-scd)會產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="5340b-188">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="5340b-189">進行 `dotnet build` 或 `dotnet publish` 期間，如果與您所使用 SDK 的環境和平台相符，就會建立可執行檔。</span><span class="sxs-lookup"><span data-stu-id="5340b-189">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="5340b-190">針對這些可執行檔，您可以預期能夠進行與其他原生可執行檔相同的操作，例如：</span><span class="sxs-lookup"><span data-stu-id="5340b-190">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="5340b-191">您可以按兩下可執行檔。</span><span class="sxs-lookup"><span data-stu-id="5340b-191">You can double-click on the executable.</span></span>
* <span data-ttu-id="5340b-192">您可以直接從命令提示字元啟動應用程式，例如在 Windows 上為 `myapp.exe`，在 Linux 和 macOS 上為 `./myapp`。</span><span class="sxs-lookup"><span data-stu-id="5340b-192">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="5340b-193">組建複本相依性</span><span class="sxs-lookup"><span data-stu-id="5340b-193">Build copies dependencies</span></span>

<span data-ttu-id="5340b-194">`dotnet build` 現在會從 NuGet 快取將您應用程式的 NuGet 相依性複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="5340b-194">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="5340b-195">先前，只有在進行 `dotnet publish` 的過程中，才會複製相依性。</span><span class="sxs-lookup"><span data-stu-id="5340b-195">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="5340b-196">有些作業 (例如連結和 Razor 頁面發佈) 仍然需要發佈。</span><span class="sxs-lookup"><span data-stu-id="5340b-196">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="5340b-197">本機 dotnet 工具</span><span class="sxs-lookup"><span data-stu-id="5340b-197">Local dotnet tools</span></span>

>[!WARNING]
><span data-ttu-id="5340b-198">在 .NET Core 3.0 Preview 1 與 .NET Core 3.0 Preview 2 之間，.NET Core 本機工具已發生變更。</span><span class="sxs-lookup"><span data-stu-id="5340b-198">There was a change in .NET Core Local Tools between .NET Core 3.0 Preview 1 and .NET Core 3.0 Preview 2.</span></span>  <span data-ttu-id="5340b-199">如果您執行 `dotnet tool restore` 或 `dotnet tool install` 這類命令，嘗試 Preview 1 中的本機工具，則需要先刪除您的本機工具快取資料夾，然後本機工具才能在 Preview 2 中正常運作。</span><span class="sxs-lookup"><span data-stu-id="5340b-199">If you tried out local tools in Preview 1 by running a command like `dotnet tool restore` or `dotnet tool install`, you need to delete your local tools cache folder before local tools will work correctly in Preview 2.</span></span> <span data-ttu-id="5340b-200">此資料夾位於：</span><span class="sxs-lookup"><span data-stu-id="5340b-200">This folder is located at:</span></span>
>
><span data-ttu-id="5340b-201">在 mac、Linux 上：`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="5340b-201">On mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
><span data-ttu-id="5340b-202">在 Windows 上：`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="5340b-202">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>
>
><span data-ttu-id="5340b-203">如果您沒有刪除此資料夾，則會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="5340b-203">If you do not delete this folder, you will receive an error.</span></span>

<span data-ttu-id="5340b-204">.NET Core 2.1 支援全域工具，.NET Core 3.0 現在則具有本機工具。</span><span class="sxs-lookup"><span data-stu-id="5340b-204">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="5340b-205">本機工具與全域工具類似，但與磁碟上的某個特定位置相關聯。</span><span class="sxs-lookup"><span data-stu-id="5340b-205">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="5340b-206">這可針對個別專案和個別存放庫提供工具。</span><span class="sxs-lookup"><span data-stu-id="5340b-206">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="5340b-207">所有安裝在本機的工具都不是全域可用的工具。</span><span class="sxs-lookup"><span data-stu-id="5340b-207">Any tool installed locally isn't available globally.</span></span> <span data-ttu-id="5340b-208">這些工具是以 NuGet 套件形式散發。</span><span class="sxs-lookup"><span data-stu-id="5340b-208">Tools are distributed as NuGet packages.</span></span>

<span data-ttu-id="5340b-209">本機工具會倚賴您目前目錄中名為 `dotnet-tools.json` 的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="5340b-209">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="5340b-210">此資訊清單檔定義可在該資料夾和以下資料夾提供的工具。</span><span class="sxs-lookup"><span data-stu-id="5340b-210">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="5340b-211">藉由在存放庫的根目錄建立此資訊清單檔，您便可確保任何複製您程式碼的人員都可進行還原，以及使用成功運用您程式碼所需的工具。</span><span class="sxs-lookup"><span data-stu-id="5340b-211">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="5340b-212">若要建立 `dotnet-tools.json` 資訊清單，請使用：</span><span class="sxs-lookup"><span data-stu-id="5340b-212">To create a `dotnet-tools.json` manifest file, use:</span></span>

```console
dotnet new tool-manifest
```

<span data-ttu-id="5340b-213">使用下列方式將新工具加入至本機資訊清單：</span><span class="sxs-lookup"><span data-stu-id="5340b-213">Add a new tool to the local manifest with:</span></span>

```console
dotnet tool install <packageId>
```

<span data-ttu-id="5340b-214">您也可以使用下列方式，列出本機資訊清單中的工具：</span><span class="sxs-lookup"><span data-stu-id="5340b-214">You can also list the tools in the local manifest with:</span></span>

```console
dotnet tool list
```

<span data-ttu-id="5340b-215">若要查看全域安裝的工具，請使用：</span><span class="sxs-lookup"><span data-stu-id="5340b-215">To see what tools are installed globally, use:</span></span>

```console
dotnet tool list -g
```

<span data-ttu-id="5340b-216">當有本機工具資訊清單檔可用，但尚未安裝資訊清單中定義的工具時，請使用下列命令自動下載並安裝這些工具：</span><span class="sxs-lookup"><span data-stu-id="5340b-216">When the local tools manifest file is available, but the tools defined in the manifest have not been installed, use the following command to automatically download and install those tools:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="5340b-217">使用下列命令來執行本機工具：</span><span class="sxs-lookup"><span data-stu-id="5340b-217">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="5340b-218">執行本機工具時，dotnet 會沿著現行目錄結構向上搜尋資訊清單。</span><span class="sxs-lookup"><span data-stu-id="5340b-218">When a local tool is run, dotnet searches for a manifest up the current directory structure.</span></span> <span data-ttu-id="5340b-219">找到工具資訊清單檔時，會在其中搜尋所要求的工具。</span><span class="sxs-lookup"><span data-stu-id="5340b-219">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="5340b-220">如果在資訊清單中找到工具，但在快取中找不到，使用者就會收到錯誤，而且需要執行 `dotnet tool restore`。</span><span class="sxs-lookup"><span data-stu-id="5340b-220">If the tool is found in the manifest, but not the cache, the user receives an error and needs to run `dotnet tool restore`.</span></span>

<span data-ttu-id="5340b-221">若要從本機工具資訊清單檔中移除某個工具，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="5340b-221">To remove a tool from the local tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <packageId>
```

<span data-ttu-id="5340b-222">工具資訊清單檔的設計目的是要允許手動編輯 – 當您要更新與存放庫搭配運作所需的版本時，可能會這麼做。</span><span class="sxs-lookup"><span data-stu-id="5340b-222">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span> <span data-ttu-id="5340b-223">以下是一個範例 `dotnet-tools.json` 檔案：</span><span class="sxs-lookup"><span data-stu-id="5340b-223">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="5340b-224">不論是全域工具還是區域工具，都需要一個相容的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="5340b-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="5340b-225">NuGet.org 上目前許多工具都以 .NET Core 執行階段 2.1 為目標。</span><span class="sxs-lookup"><span data-stu-id="5340b-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="5340b-226">若要在全域或本機安裝這些工具，您仍然需要安裝 [NET Core 2.1 執行階段](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="5340b-226">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="5340b-227">Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="5340b-227">Windows desktop</span></span>

<span data-ttu-id="5340b-228">從 .NET Core 3.0 Preview 1 開始，您可以使用 WPF 和 Windows Forms 來建置 Windows 傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="5340b-228">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="5340b-229">這些架構也支援透過 [XAML 島](/windows/uwp/xaml-platform/xaml-host-controls)使用來自 Windows UI XAML 程式庫 (WinUI) 的新式控制項和 Fluent 樣式。</span><span class="sxs-lookup"><span data-stu-id="5340b-229">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="5340b-230">「Windows 傳統型」元件是 Windows .NET Core 3.0 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="5340b-230">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="5340b-231">您可以使用下列 `dotnet` 命令來建立新的 WPF 或 Windows Forms 應用程式：</span><span class="sxs-lookup"><span data-stu-id="5340b-231">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="5340b-232">Visual Studio 2019 Preview 2 會新增**專案**範本，供 .NET Core 3.0 Windows Forms 和 WPF 使用。</span><span class="sxs-lookup"><span data-stu-id="5340b-232">Visual Studio 2019 Preview 2 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span> <span data-ttu-id="5340b-233">仍然尚未支援設計工具。</span><span class="sxs-lookup"><span data-stu-id="5340b-233">Designers are still not yet supported.</span></span> <span data-ttu-id="5340b-234">您可以在 Visual Studio 2019 中開啟、啟動和偵錯這些專案。</span><span class="sxs-lookup"><span data-stu-id="5340b-234">And you can open, launch, and debug these projects in Visual Studio 2019.</span></span>

<span data-ttu-id="5340b-235">Visual Studio 2017 15.9 新增了[啟用 .NET Core 預覽](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/)的功能，但您需要開啟該功能，而且它不是支援的情節。</span><span class="sxs-lookup"><span data-stu-id="5340b-235">Visual Studio 2017 15.9 adds the ability to [enable .NET Core previews](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/), but you need to turn that feature on, and it's not a supported scenario.</span></span>

<span data-ttu-id="5340b-236">新專案與現有的 .NET Core 專案相同，但有新增一些項目。</span><span class="sxs-lookup"><span data-stu-id="5340b-236">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="5340b-237">以下是基本 .NET Core 主控台專案與基本 Windows Forms 和 WPF 專案的比較。</span><span class="sxs-lookup"><span data-stu-id="5340b-237">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="5340b-238">在 .NET Core 主控台專案中，專案會使用 `Microsoft.NET.Sdk` SDK，並透過 `netcoreapp3.0` 目標架構宣告與 .NET Core 3.0 的相依性。</span><span class="sxs-lookup"><span data-stu-id="5340b-238">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="5340b-239">若要建立 Windows 傳統型應用程式，請使用 `Microsoft.NET.Sdk.WindowsDesktop` SDK，然後選擇要使用的 UI 架構：</span><span class="sxs-lookup"><span data-stu-id="5340b-239">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="5340b-240">若要選擇 Windows Forms 而不選擇 WPF，請設定 `UseWindowsForms` 而不要設定 `UseWPF`：</span><span class="sxs-lookup"><span data-stu-id="5340b-240">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="5340b-241">如果應用程式同時使用這兩種架構 (例如當 Windows Forms 對話方塊裝載 WPF 控制項時)，則可以將 `UseWPF` 和 `UseWindowsForms` 都設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5340b-241">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="5340b-242">請在 [dotnet/winforms](https://github.com/dotnet/winforms/issues)、[dotnet/wpf](https://github.com/dotnet/wpf/issues) 及 [dotnet/core](https://github.com/dotnet/core/issues) 存放庫上分享您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="5340b-242">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="msix-deployment-for-windows-desktop"></a><span data-ttu-id="5340b-243">Windows 傳統型的 MSIX 部署</span><span class="sxs-lookup"><span data-stu-id="5340b-243">MSIX Deployment for Windows Desktop</span></span>

<span data-ttu-id="5340b-244">[MSIX](https://docs.microsoft.com/windows/msix/) 是新的 Windows 應用程式套件格式。</span><span class="sxs-lookup"><span data-stu-id="5340b-244">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows app package format.</span></span> <span data-ttu-id="5340b-245">它可以用來將 .NET Core 3.0 桌面應用程式部署至 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="5340b-245">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="5340b-246">Visual Studio 2019 Preview 2 中提供的 [Windows 應用程式套件專案](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)可讓您利用[自封式](../deploying/index.md#self-contained-deployments-scd) .NET Core 應用程式建立 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="5340b-246">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019 Preview 2, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

><span data-ttu-id="5340b-247">注意:.NET Core 專案檔必須指定在 `<RuntimeIdentifiers>` 屬性中支援的執行階段：</span><span class="sxs-lookup"><span data-stu-id="5340b-247">Note: The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>
```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="fast-built-in-json-support"></a><span data-ttu-id="5340b-248">快速的內建 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="5340b-248">Fast built-in JSON support</span></span>

<span data-ttu-id="5340b-249">.NET 生態系統倚賴 [**Json.NET**](https://www.newtonsoft.com/json) 及其他熱門的 JSON 程式庫 (這些仍持續是絕佳的選擇)。</span><span class="sxs-lookup"><span data-stu-id="5340b-249">The .NET ecosystem has relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="5340b-250">**Json.NET** 使用 .NET 字串作為其基底資料類型，實際上就是 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="5340b-250">**Json.NET** uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span>

<span data-ttu-id="5340b-251">新的內建 JSON 支援是高效能、低配置，並以 `Span<byte>` 為基礎。</span><span class="sxs-lookup"><span data-stu-id="5340b-251">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="5340b-252">三個新的主要 JSON 相關類型已新增到 .NET Core 3.0 `System.Text.Json` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5340b-252">Three new main JSON-related types have been added to .NET Core 3.0 the `System.Text.Json` namespace.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="5340b-253">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="5340b-253">Utf8JsonReader</span></span>

<span data-ttu-id="5340b-254">`System.Text.Json.Utf8JsonReader` 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。</span><span class="sxs-lookup"><span data-stu-id="5340b-254">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="5340b-255">`Utf8JsonReader` 是一個基礎的低階類型，可用來建置自訂剖析器和還原序列化程式。</span><span class="sxs-lookup"><span data-stu-id="5340b-255">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="5340b-256">使用新的 `Utf8JsonReader` 來讀取 JSON 承載會比使用來自 **Json.NET** 的讀取器快兩倍。</span><span class="sxs-lookup"><span data-stu-id="5340b-256">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="5340b-257">它會等到您需要將 JSON 權杖實現為 (UTF-16) 字串時，才進行配置。</span><span class="sxs-lookup"><span data-stu-id="5340b-257">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="5340b-258">這個新 API 將包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="5340b-258">This new API will include the following components:</span></span>

* <span data-ttu-id="5340b-259">在 Preview 1 中：JSON 讀取器 (循序存取)</span><span class="sxs-lookup"><span data-stu-id="5340b-259">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="5340b-260">在即將推出的版本中：JSON 寫入器、DOM (隨機存取)、POCO 序列化程式、POCO 還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="5340b-260">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="5340b-261">以下是 `Utf8JsonReader` 的基本讀取器迴圈，您可以使用它作為起點：</span><span class="sxs-lookup"><span data-stu-id="5340b-261">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a><span data-ttu-id="5340b-262">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="5340b-262">Utf8JsonWriter</span></span>

<span data-ttu-id="5340b-263">`System.Text.Json.Utf8JsonWriter` 提供高效能、非快取、僅轉接方式，從常見的 .NET 類型 (像是 `String`、`Int32` 和 `DateTime`) 撰寫 UTF-8 編碼的 JSON 文字。</span><span class="sxs-lookup"><span data-stu-id="5340b-263">`System.Text.Json.Utf8JsonWriter` provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="5340b-264">如同讀取器，寫入器是一個基礎的低階類型，可用來組建自訂序列化程式。</span><span class="sxs-lookup"><span data-stu-id="5340b-264">Like the reader, the writer is a foundational, low-level type, that can be leveraged to build custom serializers.</span></span> <span data-ttu-id="5340b-265">使用新的 `Utf8JsonWriter` 撰寫 JSON 承載，其速度比從 **Json.NET** 使用寫入器還要快 30-80%，而且不會配置。</span><span class="sxs-lookup"><span data-stu-id="5340b-265">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and does not allocate.</span></span>

<span data-ttu-id="5340b-266">以下是 `Utf8JsonWriter` 的使用方式樣本，其可作為起點：</span><span class="sxs-lookup"><span data-stu-id="5340b-266">Here is a sample usage of the `Utf8JsonWriter` that can be used as a starting point:</span></span>

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

<span data-ttu-id="5340b-267">`Utf8JsonWriter` 接受 `IBufferWriter<byte>` 作為輸出位置，以同步方式將 json 資料寫入其中，而且身為呼叫者的您需要提供具體實作。</span><span class="sxs-lookup"><span data-stu-id="5340b-267">The `Utf8JsonWriter` accepts `IBufferWriter<byte>` as the output location to synchronously write the json data into, and you as the caller need to provide a concrete implementation.</span></span> <span data-ttu-id="5340b-268">平台目前不包含這個介面的實作。</span><span class="sxs-lookup"><span data-stu-id="5340b-268">The platform does not currently include an implementation of this interface.</span></span> <span data-ttu-id="5340b-269">如需 [ 的範例，請參閱 `IBufferWriter<byte>`https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span><span class="sxs-lookup"><span data-stu-id="5340b-269">For an example of `IBufferWriter<byte>`, see [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span></span>

### <a name="jsondocument"></a><span data-ttu-id="5340b-270">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="5340b-270">JsonDocument</span></span>

<span data-ttu-id="5340b-271">`System.Text.Json.JsonDocument` 是組建在 `Utf8JsonReader` 之上。</span><span class="sxs-lookup"><span data-stu-id="5340b-271">`System.Text.Json.JsonDocument` is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="5340b-272">`JsonDocument` 可讓您剖析 JSON 資料和組建唯讀文件物件模型 (DOM)，而您可以查詢此模型來支援隨機存取和列舉。</span><span class="sxs-lookup"><span data-stu-id="5340b-272">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="5340b-273">撰寫資料的 JSON 元素可以透過 `JsonElement` 類型來存取，而此類型被 `JsonDocument` 屬性公開為名為 `RootElement` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="5340b-273">The JSON elements that compose the data can be accessed via the `JsonElement` type which is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="5340b-274">`JsonElement` 包含 JSON 陣列和物件列舉程式，以及將 JSON 文字轉換為一般.NET 類型的 API。</span><span class="sxs-lookup"><span data-stu-id="5340b-274">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="5340b-275">使用 `JsonDocument` 剖析一般 JSON 承載，並存取其所有成員，速度比 **Json.NET** 還要快 2-3 倍，而且極少配置合理大小 (亦即 < 1 MB) 的資料。</span><span class="sxs-lookup"><span data-stu-id="5340b-275">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with very little allocations for data that is reasonably sized (i.e. < 1 MB).</span></span>

<span data-ttu-id="5340b-276">以下是 `JsonDocument` 和 `JsonElement` 的使用方式樣本，其可作為起點：</span><span class="sxs-lookup"><span data-stu-id="5340b-276">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a><span data-ttu-id="5340b-277">組件卸載功能</span><span class="sxs-lookup"><span data-stu-id="5340b-277">Assembly Unloadability</span></span>

<span data-ttu-id="5340b-278">組件卸載功能是 `AssemblyLoadContext` 的新功能。</span><span class="sxs-lookup"><span data-stu-id="5340b-278">Assembly unloadability is a new capability of `AssemblyLoadContext`.</span></span> <span data-ttu-id="5340b-279">從 API 觀點來看，這項新功能是透明的，僅對少數新的 API 公開。</span><span class="sxs-lookup"><span data-stu-id="5340b-279">This new feature is largely transparent from an API perspective, exposed with just a few new APIs.</span></span> <span data-ttu-id="5340b-280">它可讓您卸載載入器內容，釋放所有具現化類型、靜態欄位和組件本身的所有記憶體。</span><span class="sxs-lookup"><span data-stu-id="5340b-280">It enables a loader context to be unloaded, releasing all memory for instantiated types, static fields and for the assembly itself.</span></span> <span data-ttu-id="5340b-281">應用程式應該能夠永遠透過這項機制載入和卸載組件，而不會遇到記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="5340b-281">An application should be able to load and unload assemblies via this mechanism forever without experiencing a memory leak.</span></span>

<span data-ttu-id="5340b-282">這項新功能可以用於如下情節：</span><span class="sxs-lookup"><span data-stu-id="5340b-282">This new capability can be used for scenarios similar to:</span></span>

* <span data-ttu-id="5340b-283">需要動態外掛程式載入和卸載的外掛程式情節。</span><span class="sxs-lookup"><span data-stu-id="5340b-283">Plugin scenarios where dynamic plugin loading and unloading is required.</span></span> 
* <span data-ttu-id="5340b-284">動態編譯、執行，然後清除程式碼。</span><span class="sxs-lookup"><span data-stu-id="5340b-284">Dynamically compiling, running and then flushing code.</span></span> <span data-ttu-id="5340b-285">適用於網站、指令碼引擎等等。</span><span class="sxs-lookup"><span data-stu-id="5340b-285">Useful for web sites, scripting engines, etc.</span></span>
* <span data-ttu-id="5340b-286">載入組件進行內部檢查 (例如 ReflectionOnlyLoad)，但在許多情況下，[MetadataLoadContext](#type-metadataloadcontext) (已在 Preview 1 中發佈) 將會是更好的選項。</span><span class="sxs-lookup"><span data-stu-id="5340b-286">Loading assemblies for introspection (like ReflectionOnlyLoad), although [MetadataLoadContext](#type-metadataloadcontext) (released in Preview 1) will be a better choice in many cases.</span></span>

<span data-ttu-id="5340b-287">如需詳細資訊，請參閱[使用卸載功能](https://github.com/dotnet/coreclr/pull/22221)文件。</span><span class="sxs-lookup"><span data-stu-id="5340b-287">For more information, see the [Using Unloadability](https://github.com/dotnet/coreclr/pull/22221) document.</span></span>

<span data-ttu-id="5340b-288">組件卸載需要相當小心，以確保從載入器內容外參考受控物件時，一切了然並受到管理。</span><span class="sxs-lookup"><span data-stu-id="5340b-288">Assembly unloading requires significant care to ensure that all references to managed objects from outside a loader context are understood and managed.</span></span> <span data-ttu-id="5340b-289">要求卸載載入器內容時，需要了解任何外部參考，以便載入器內容只會與自己一致。</span><span class="sxs-lookup"><span data-stu-id="5340b-289">When the loader context is requested to be unloaded, any outside references need to have been unreferenced so that the loader context is self-consistent only to itself.</span></span>

<span data-ttu-id="5340b-290">.NET Framework 透過應用程式定義域 (AppDomain) 提供了組件卸載功能，但不支援其與 .NET Core 搭配。</span><span class="sxs-lookup"><span data-stu-id="5340b-290">Assembly unloadability was provided in the .NET Framework by Application Domains (AppDomains), which are not supported with .NET Core.</span></span> <span data-ttu-id="5340b-291">相較於這個新模型，AppDomain 既有優點也有限制。</span><span class="sxs-lookup"><span data-stu-id="5340b-291">AppDomains had both benefits and limitations compared to this new model.</span></span> <span data-ttu-id="5340b-292">相較於 AppDomain 時，若需要更多彈性和更高效能，請考慮這個新的載入器模型。</span><span class="sxs-lookup"><span data-stu-id="5340b-292">Consider this new loader model to be more flexible and higher performant when compared to AppDomains.</span></span>

## <a name="windows-native-interop"></a><span data-ttu-id="5340b-293">Windows 原生 Interop</span><span class="sxs-lookup"><span data-stu-id="5340b-293">Windows Native Interop</span></span>

<span data-ttu-id="5340b-294">Windows 提供了豐富的原生 API，其採用的形式為一般 C API、COM 和 WinRT。</span><span class="sxs-lookup"><span data-stu-id="5340b-294">Windows offers a rich native API, in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="5340b-295">自 .NET Core 1.0 起，已支援 **P/Invoke**。</span><span class="sxs-lookup"><span data-stu-id="5340b-295">Since .NET Core 1.0, **P/Invoke** has been supported.</span></span> <span data-ttu-id="5340b-296">現在 .NET Core 3.0 支援**共同建立 COM API**和**啟用 WinRT API** 的能力。</span><span class="sxs-lookup"><span data-stu-id="5340b-296">Now with .NET Core 3.0, support for the ability to **CoCreate COM APIs** and **Activate WinRT APIs** has been added.</span></span>

<span data-ttu-id="5340b-297">您可以看到使用 COM 與 [Excel 示範原始程式碼](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo)搭配的範例。</span><span class="sxs-lookup"><span data-stu-id="5340b-297">You can see an example of using COM with the [Excel Demo source code](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>


## <a name="type-sequencereader"></a><span data-ttu-id="5340b-298">類型：SequenceReader</span><span class="sxs-lookup"><span data-stu-id="5340b-298">Type: SequenceReader</span></span>

<span data-ttu-id="5340b-299">在 .NET Core 3.0 中已新增 `System.Buffers.SequenceReader`，這可用來作為 `ReadOnlySequence<T>` 的讀取器。</span><span class="sxs-lookup"><span data-stu-id="5340b-299">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="5340b-300">這可讓您以輕鬆、高效能、低配置的方式，剖析可跨多個支援緩衝區的 `System.IO.Pipelines` 資料。</span><span class="sxs-lookup"><span data-stu-id="5340b-300">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="5340b-301">下列範例將輸入 `Sequence` 分成以 `CR/LF` 分隔的有效行：</span><span class="sxs-lookup"><span data-stu-id="5340b-301">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="5340b-302">類型：MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="5340b-302">Type: MetadataLoadContext</span></span>

<span data-ttu-id="5340b-303">已新增 `MetadataLoadContext` 類型，可讓您讀取組件中繼資料，而不會影響到呼叫端的應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="5340b-303">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="5340b-304">讀取組件 (包括為與目前執行階段環境不同的架構和平台建置的組件) 時，會將組件當作資料來讀取。</span><span class="sxs-lookup"><span data-stu-id="5340b-304">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="5340b-305">`MetadataLoadContext` 與 <xref:System.Reflection.Assembly.ReflectionOnlyLoad*> (只有在 .NET Framework 中才有提供) 重疊。</span><span class="sxs-lookup"><span data-stu-id="5340b-305">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="5340b-306">`MetdataLoadContext` 是 [System.Reflection.MetadataLoadContext 套件](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext)中所提供的類型。</span><span class="sxs-lookup"><span data-stu-id="5340b-306">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="5340b-307">這是一個 .NET Standard 2.0 套件。</span><span class="sxs-lookup"><span data-stu-id="5340b-307">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="5340b-308">`MetadataLoadContext` 公開 API 的方式與 <xref:System.Runtime.Loader.AssemblyLoadContext> 類型類似，但並非以該類型為基礎。</span><span class="sxs-lookup"><span data-stu-id="5340b-308">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="5340b-309">就像 <xref:System.Runtime.Loader.AssemblyLoadContext> 一樣，`MetadataLoadContext` 也可讓您載入已隔離之組件載入 Universe 內的組件。</span><span class="sxs-lookup"><span data-stu-id="5340b-309">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="5340b-310">`MetdataLoadContext` API 會傳回 <xref:System.Reflection.Assembly> 物件，以讓您使用熟悉的反映 API。</span><span class="sxs-lookup"><span data-stu-id="5340b-310">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="5340b-311">執行導向 API (例如 [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127)) 不是允許使用的 API，將會擲回 InvalidOperationException。</span><span class="sxs-lookup"><span data-stu-id="5340b-311">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="5340b-312">下列範例示範如何在實作指定介面的組件中尋找具體的類型：</span><span class="sxs-lookup"><span data-stu-id="5340b-312">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="5340b-313">`MetadataLoadContext` 的案例包括設計階段功能、組建階段工具及執行階段啟動功能，這些功能需要將一組組件當作資料來檢查，並將所有檔案鎖定及在執行檢查後將記憶體釋出。</span><span class="sxs-lookup"><span data-stu-id="5340b-313">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="5340b-314">`MetadataLoadContext` 具有一個會傳送給其建構函式的解析程式類別。</span><span class="sxs-lookup"><span data-stu-id="5340b-314">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="5340b-315">此解析程式的工作是在已指定 `AssemblyName` 的情況下載入 `Assembly`。</span><span class="sxs-lookup"><span data-stu-id="5340b-315">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="5340b-316">此解析程式類別衍生自抽象的 `MetadataAssemblyResolver` 類別。</span><span class="sxs-lookup"><span data-stu-id="5340b-316">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="5340b-317">提供路徑型案例的解析器實作時，會以 `PathAssemblyResolver` 提供。</span><span class="sxs-lookup"><span data-stu-id="5340b-317">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="5340b-318">[MetadataLoadContext 測試](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) 示範許多使用案例。</span><span class="sxs-lookup"><span data-stu-id="5340b-318">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="5340b-319">[組件測試](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs)是一個絕佳的起點。</span><span class="sxs-lookup"><span data-stu-id="5340b-319">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="5340b-320">Linux 上的 TLS 1.3 和 OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="5340b-320">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="5340b-321">.NET Core 現在會利用 [OpenSSL 1.1.1 中的 TLS 1.3 支援](https://www.openssl.org/blog/blog/2018/09/11/release111/) (當在指定的環境中有提供時)。</span><span class="sxs-lookup"><span data-stu-id="5340b-321">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="5340b-322">依據 [OpenSSL 小組](https://www.openssl.org/blog/blog/2018/09/11/release111/)，TLS 1.3 有多項優點：</span><span class="sxs-lookup"><span data-stu-id="5340b-322">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="5340b-323">因為用戶端與伺服器之間的來回行程次數減少，所以改善了連線時間。</span><span class="sxs-lookup"><span data-stu-id="5340b-323">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="5340b-324">因為移除各種已淘汰和不安全的密碼編譯演算法，並加密更大部分的連線信號交換，所以提升了安全性。</span><span class="sxs-lookup"><span data-stu-id="5340b-324">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="5340b-325">.NET Core 3.0 Preview 1 能夠利用 **OpenSSL 1.1.1**、**OpenSSL 1.1.0** 或 **OpenSSL 1.0.2** (不論在 Linux 系統上找到的最佳版本是哪一個)。</span><span class="sxs-lookup"><span data-stu-id="5340b-325">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="5340b-326">當 **OpenSSL 1.1.1** 可供使用時，在使用 `SslProtocols.None` (系統預設通訊協定) 的情況下，如果用戶端和伺服器都支援 **TLS 1.3**，SslStream 和 HttpClient 類型就會使用 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="5340b-326">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="5340b-327">下列範例示範連線至 <https://www.cloudflare.com> 之 Ubuntu 18.10 上的 .NET Core 3.0 Preview 1：</span><span class="sxs-lookup"><span data-stu-id="5340b-327">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="5340b-328">Windows 和 macOS 尚未支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="5340b-328">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="5340b-329">.NET Core 3.0 將在有支援可用時，在這些作業系統上支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="5340b-329">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="5340b-330">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="5340b-330">Cryptography</span></span>

<span data-ttu-id="5340b-331">已新增對 **AES-GCM** 和 **AES-CCM** 加密方式的支援 (透過 `System.Security.Cryptography.AesGcm` 和 `System.Security.Cryptography.AesCcm` 來實作)。</span><span class="sxs-lookup"><span data-stu-id="5340b-331">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="5340b-332">這些演算法既是[搭配關聯資料的驗證加密 (AEAD) 演算法](https://en.wikipedia.org/wiki/Authenticated_encryption)，也是最先新增至 .NET Core 的「驗證加密」(AE) 演算法。</span><span class="sxs-lookup"><span data-stu-id="5340b-332">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="5340b-333">下列程式碼示範如何使用 **AesGcm** 加密方式將隨機資料加密和解密。</span><span class="sxs-lookup"><span data-stu-id="5340b-333">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="5340b-334">**AesCcm** 的程式碼看起來幾乎完全相同 (只有類別變數名稱會有所不同)。</span><span class="sxs-lookup"><span data-stu-id="5340b-334">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="5340b-335">密碼編譯金鑰匯入/匯出</span><span class="sxs-lookup"><span data-stu-id="5340b-335">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="5340b-336">.NET Core 3.0 Preview 1 支援從標準格式匯入及匯出非對稱式公開金鑰與私密金鑰，而無須使用 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="5340b-336">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="5340b-337">所有金鑰類型 (RSA、DSA、ECDsa、ECDiffieHellman) 都支援適用於公開金鑰的 **X.509 SubjectPublicKeyInfo** 格式，以及適用於私密金鑰的 **PKCS#8 PrivateKeyInfo** 和 **PKCS#8 EncryptedPrivateKeyInfo** 格式。</span><span class="sxs-lookup"><span data-stu-id="5340b-337">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="5340b-338">RSA 還額外支援 **PKCS#1 RSAPublicKey** 和 **PKCS#1 RSAPrivateKey**。</span><span class="sxs-lookup"><span data-stu-id="5340b-338">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="5340b-339">所有匯出方法都會產生 DER 編碼的二進位資料，而匯出方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="5340b-339">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="5340b-340">如果金鑰是以適合文字的 PEM 格式儲存的，呼叫端在呼叫匯入方法之前，就必須先對內容進行 Base64 解碼。</span><span class="sxs-lookup"><span data-stu-id="5340b-340">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="5340b-341">若要檢查 PKCS#8 檔案，可以使用 `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` 類別。</span><span class="sxs-lookup"><span data-stu-id="5340b-341">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="5340b-342">若要檢查和操作 PFX/PKCS#12 檔案，可以分別使用 `System.Security.Cryptography.Pkcs.Pkcs12Info` 和 `System.Security.Cryptography.Pkcs.Pkcs12Builder`。</span><span class="sxs-lookup"><span data-stu-id="5340b-342">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="5340b-343">適用於 Linux 的 SerialPort</span><span class="sxs-lookup"><span data-stu-id="5340b-343">SerialPort for Linux</span></span>

<span data-ttu-id="5340b-344">.NET Core 3.0 現已在 Linux 上支援 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5340b-344">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="5340b-345">先前，.NET Core 僅支援在 Windows 上使用 `SerialPort` 類型。</span><span class="sxs-lookup"><span data-stu-id="5340b-345">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="5340b-346">更多 BCL 改進</span><span class="sxs-lookup"><span data-stu-id="5340b-346">More BCL Improvements</span></span>

<span data-ttu-id="5340b-347">在 .NET Core 3.0 中，已將在 .NET Core 2.1 中導入的 `Span<T>`、`Memory<T>` 及相關類型最佳化。</span><span class="sxs-lookup"><span data-stu-id="5340b-347">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="5340b-348">範圍建構、配量、剖析及格式化等常見作業現在執行效能更佳。</span><span class="sxs-lookup"><span data-stu-id="5340b-348">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="5340b-349">此外，`String` 這類類型也有隱含的改進，使其在搭配 `Dictionary<TKey, TValue>` 及其他集合作為金鑰使用時更有效率。</span><span class="sxs-lookup"><span data-stu-id="5340b-349">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="5340b-350">您無須進行任何程式碼變更，即可享有這些改進的好處。</span><span class="sxs-lookup"><span data-stu-id="5340b-350">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="5340b-351">以下也是 .NET Core 3 Preview 1 中新增的改進：</span><span class="sxs-lookup"><span data-stu-id="5340b-351">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="5340b-352">HttpClient 內建 Brotli 支援</span><span class="sxs-lookup"><span data-stu-id="5340b-352">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="5340b-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="5340b-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="5340b-354">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="5340b-354">Unsafe.Unbox</span></span>
* <span data-ttu-id="5340b-355">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="5340b-355">CancellationToken.Unregister</span></span>
* <span data-ttu-id="5340b-356">複雜算術運算子</span><span class="sxs-lookup"><span data-stu-id="5340b-356">Complex arithmetic operators</span></span>
* <span data-ttu-id="5340b-357">適用於 TCP 持續連線的通訊端 API</span><span class="sxs-lookup"><span data-stu-id="5340b-357">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="5340b-358">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="5340b-358">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="5340b-359">IPEndPoint 剖析</span><span class="sxs-lookup"><span data-stu-id="5340b-359">IPEndPoint parsing</span></span>
* <span data-ttu-id="5340b-360">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="5340b-360">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="5340b-361">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="5340b-361">Tiered compilation</span></span>

<span data-ttu-id="5340b-362">使用 .NET Core 3.0 時，預設會開啟[階層式編譯](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/)。</span><span class="sxs-lookup"><span data-stu-id="5340b-362">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="5340b-363">這是一項可讓執行階段更彈性使用 Just-In-Time (JIT) 編譯器的功能，可在啟動時及將輸送量最大化時獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="5340b-363">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="5340b-364">此功能在 [.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) 中是新增為選用功能，然後在 [.NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/) 中為預設啟用的功能。</span><span class="sxs-lookup"><span data-stu-id="5340b-364">This feature was added as an opt-in feature in [.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="5340b-365">之後，在 .NET Core 2.2 版本中則又還原回選用功能。</span><span class="sxs-lookup"><span data-stu-id="5340b-365">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="5340b-366">ARM64 Linux 支援</span><span class="sxs-lookup"><span data-stu-id="5340b-366">ARM64 Linux support</span></span>

<span data-ttu-id="5340b-367">已新增 ARM64 for Linux 的支援。</span><span class="sxs-lookup"><span data-stu-id="5340b-367">Support has been added for ARM64 for Linux.</span></span> <span data-ttu-id="5340b-368">ARM64 的主要使用案例目前是搭配 IoT 案例。</span><span class="sxs-lookup"><span data-stu-id="5340b-368">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="5340b-369">[針對適用於 ARM64 的 .NET Core 有提供 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/) (Alpine、Debian 及 Ubuntu Docker 映像)。</span><span class="sxs-lookup"><span data-stu-id="5340b-369">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="5340b-370">如需詳細資訊，請參閱 [.NET Core ARM64 狀態](https://github.com/dotnet/announcements/issues/82) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="5340b-370">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="5340b-371">目前尚未提供 **ARM64** Windows 支援。</span><span class="sxs-lookup"><span data-stu-id="5340b-371">**ARM64** Windows support isn't yet available.</span></span>

## <a name="install-net-core-30-previews-on-linux-with-snap"></a><span data-ttu-id="5340b-372">在 Linux 上使用嵌入式管理單元安裝.NET Core 3.0 Preview</span><span class="sxs-lookup"><span data-stu-id="5340b-372">Install .NET Core 3.0 Previews on Linux with Snap</span></span>

<span data-ttu-id="5340b-373">嵌入式管理單元是慣用方法，用來在 [支援嵌入式管理單元的 Linux 散發套件](https://docs.snapcraft.io/installing-snapd/6735)上安裝和嘗試 .NET Core Preview。</span><span class="sxs-lookup"><span data-stu-id="5340b-373">Snap is the preferred way to install and try .NET Core previews on [Linux distributions that support Snap](https://docs.snapcraft.io/installing-snapd/6735).</span></span>

<span data-ttu-id="5340b-374">在您的系統上設定嵌入式管理單元之後，請執行下列命令來安裝 [.NET Core SDK 3.0 Preview SDK](https://snapcraft.io/dotnet-sdk)。</span><span class="sxs-lookup"><span data-stu-id="5340b-374">After configuring Snap on your system, run the following command to install the [.NET Core SDK 3.0 Preview SDK](https://snapcraft.io/dotnet-sdk).</span></span>

```console
sudo snap install dotnet-sdk --beta --classic
```
 
<span data-ttu-id="5340b-375">使用嵌入式管理單元套件安裝 .NET Core 時，預設 .NET Core 命令是 `dotnet-sdk.dotnet`，而非只是 `dotnet`。</span><span class="sxs-lookup"><span data-stu-id="5340b-375">When .NET Core in installed using the Snap package, the default .NET Core command is `dotnet-sdk.dotnet`, as opposed to just `dotnet`.</span></span> <span data-ttu-id="5340b-376">命名空間命令的優點是，不會與您可能已全域安裝的 .NET Core 版本發生衝突。</span><span class="sxs-lookup"><span data-stu-id="5340b-376">The benefit of the namespaced command is that it will not conflict with a globally installed .NET Core version you may have.</span></span> <span data-ttu-id="5340b-377">可以使用下列方式，將這個命令的別名設為 `dotnet`：</span><span class="sxs-lookup"><span data-stu-id="5340b-377">This command can be aliased to `dotnet` with:</span></span>

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="5340b-378">某些散發套件需要額外的步驟來啟用 SSL 憑證的存取。</span><span class="sxs-lookup"><span data-stu-id="5340b-378">Some distros require an additional step to enable access to the SSL certificate.</span></span> <span data-ttu-id="5340b-379">如需詳細資料，請參閱我們的 [Linux 安裝程式](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="5340b-379">See our [Linux Setup](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) for details.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="5340b-380">Raspberry Pi 的 GPIO 支援</span><span class="sxs-lookup"><span data-stu-id="5340b-380">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="5340b-381">兩個新的套件已發佈至您可以用於 GPIO 程式設計的 NuGet。</span><span class="sxs-lookup"><span data-stu-id="5340b-381">Two new packages have been released to NuGet that you can use for GPIO programming.</span></span>

* [<span data-ttu-id="5340b-382">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="5340b-382">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [<span data-ttu-id="5340b-383">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="5340b-383">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

<span data-ttu-id="5340b-384">GPIO 套件包含 GPIO、SPI、I2C 和 PWM 裝置的 API。</span><span class="sxs-lookup"><span data-stu-id="5340b-384">The GPIO Packages includes APIs for GPIO, SPI, I2C and PWM devices.</span></span> <span data-ttu-id="5340b-385">IoT 繫結套件包含各種晶片和感應器的[裝置繫結](https://github.com/dotnet/iot/blob/master/src/devices/README.md)，與 [dotnet/iot - src/devices](https://github.com/dotnet/iot/tree/master/src/devices) 中提供的裝置繫結相同。</span><span class="sxs-lookup"><span data-stu-id="5340b-385">The IoT bindings package includes [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) for various chips and sensors, the same ones available at [dotnet/iot - src/devices](https://github.com/dotnet/iot/tree/master/src/devices).</span></span>

<span data-ttu-id="5340b-386">已宣佈為.NET Core 3.0 Preview 1 一部分的更新序列連接埠，不是這些套件的一部分，但可以作為 .NET Core 平台的一部分。</span><span class="sxs-lookup"><span data-stu-id="5340b-386">The updated serial port APIs that were announced as part of .NET Core 3.0 Preview 1 are not part of these packages but are available as part of the .NET Core platform.</span></span>


## <a name="platform-support"></a><span data-ttu-id="5340b-387">平台支援</span><span class="sxs-lookup"><span data-stu-id="5340b-387">Platform Support</span></span>

<span data-ttu-id="5340b-388">以下作業系統將支援 .NET Core 3：</span><span class="sxs-lookup"><span data-stu-id="5340b-388">.NET Core 3 will be supported on the following operating systems:</span></span>

* <span data-ttu-id="5340b-389">Windows 用戶端：7、8.1、10 (1607+)</span><span class="sxs-lookup"><span data-stu-id="5340b-389">Windows Client: 7, 8.1, 10 (1607+)</span></span>
* <span data-ttu-id="5340b-390">Windows Server：2012 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="5340b-390">Windows Server: 2012 R2 SP1+</span></span>
* <span data-ttu-id="5340b-391">macOS：10.12+</span><span class="sxs-lookup"><span data-stu-id="5340b-391">macOS: 10.12+</span></span>
* <span data-ttu-id="5340b-392">RHEL：6+</span><span class="sxs-lookup"><span data-stu-id="5340b-392">RHEL: 6+</span></span>
* <span data-ttu-id="5340b-393">Fedora：26+</span><span class="sxs-lookup"><span data-stu-id="5340b-393">Fedora: 26+</span></span>
* <span data-ttu-id="5340b-394">Ubuntu：16.04+</span><span class="sxs-lookup"><span data-stu-id="5340b-394">Ubuntu: 16.04+</span></span>
* <span data-ttu-id="5340b-395">Debian：9+</span><span class="sxs-lookup"><span data-stu-id="5340b-395">Debian: 9+</span></span>
* <span data-ttu-id="5340b-396">SLES：12+</span><span class="sxs-lookup"><span data-stu-id="5340b-396">SLES: 12+</span></span>
* <span data-ttu-id="5340b-397">openSUSE：42.3+</span><span class="sxs-lookup"><span data-stu-id="5340b-397">openSUSE: 42.3+</span></span>
* <span data-ttu-id="5340b-398">Alpine：3.8+</span><span class="sxs-lookup"><span data-stu-id="5340b-398">Alpine: 3.8+</span></span>

<span data-ttu-id="5340b-399">晶片支援如下：</span><span class="sxs-lookup"><span data-stu-id="5340b-399">Chip support follows:</span></span>

* <span data-ttu-id="5340b-400">Windows、macOS 及 Linux 上的 x64</span><span class="sxs-lookup"><span data-stu-id="5340b-400">x64 on Windows, macOS, and Linux</span></span>
* <span data-ttu-id="5340b-401">Windows 上的 x86</span><span class="sxs-lookup"><span data-stu-id="5340b-401">x86 on Windows</span></span>
* <span data-ttu-id="5340b-402">Windows 和 Linux 上的 ARM32</span><span class="sxs-lookup"><span data-stu-id="5340b-402">ARM32 on Windows and Linux</span></span>
* <span data-ttu-id="5340b-403">Linux 上的 ARM64</span><span class="sxs-lookup"><span data-stu-id="5340b-403">ARM64 on Linux</span></span>

<span data-ttu-id="5340b-404">若為 Linux，Debian 9+ 和 Ubuntu 16.04+ 支援 ARM32。</span><span class="sxs-lookup"><span data-stu-id="5340b-404">For Linux, ARM32 is supported on Debian 9+ and Ubuntu 16.04+.</span></span> <span data-ttu-id="5340b-405">若為 ARM64，與 ARM32 相同，但加上 Alpine 3.8。</span><span class="sxs-lookup"><span data-stu-id="5340b-405">For ARM64, it is the same as ARM32 with the addition of Alpine 3.8.</span></span> <span data-ttu-id="5340b-406">這些與 X64 支援的散發套件版本相同。</span><span class="sxs-lookup"><span data-stu-id="5340b-406">These are the same versions of those distros as is supported for X64.</span></span>

<span data-ttu-id="5340b-407">.NET Core 3.0 的 Docker 映像位於 [Docker Hub 上的 microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="5340b-407">Docker images for .NET Core 3.0 are available at [microsoft/dotnet on Docker Hub](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="5340b-408">Microsoft 目前正在採用 [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/)，而且預期最終 .NET Core 3.0 映像只會發佈至 MCR。</span><span class="sxs-lookup"><span data-stu-id="5340b-408">Microsoft is currently in the process of adopting [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) and it is expected that the final .NET Core 3.0 images will only be published to MCR.</span></span>
