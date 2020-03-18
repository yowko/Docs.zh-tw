---
title: C# 8.0 - C# 指南中的新增功能
description: 大致了解 C# 8.0 中可用的新功能。
ms.date: 09/20/2019
ms.openlocfilehash: 0013f621268e2a4f1b916b226d83d18c68445ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399676"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="e9802-103">C# 8.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="e9802-103">What's new in C# 8.0</span></span>

<span data-ttu-id="e9802-104">C# 8.0 向 C# 語言添加了以下功能和增強功能：</span><span class="sxs-lookup"><span data-stu-id="e9802-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="e9802-105">唯讀成員</span><span class="sxs-lookup"><span data-stu-id="e9802-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="e9802-106">預設介面方法</span><span class="sxs-lookup"><span data-stu-id="e9802-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="e9802-107">[模式比對增強功能](#more-patterns-in-more-places)：</span><span class="sxs-lookup"><span data-stu-id="e9802-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="e9802-108">Switch 運算式</span><span class="sxs-lookup"><span data-stu-id="e9802-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="e9802-109">屬性模式</span><span class="sxs-lookup"><span data-stu-id="e9802-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="e9802-110">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="e9802-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="e9802-111">位置模式</span><span class="sxs-lookup"><span data-stu-id="e9802-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="e9802-112">Using 宣告</span><span class="sxs-lookup"><span data-stu-id="e9802-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="e9802-113">靜態區域函式</span><span class="sxs-lookup"><span data-stu-id="e9802-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="e9802-114">可處置的 ref struct</span><span class="sxs-lookup"><span data-stu-id="e9802-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="e9802-115">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="e9802-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="e9802-116">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="e9802-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="e9802-117">索引和範圍</span><span class="sxs-lookup"><span data-stu-id="e9802-117">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="e9802-118">空合併分配</span><span class="sxs-lookup"><span data-stu-id="e9802-118">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="e9802-119">非託管構造類型</span><span class="sxs-lookup"><span data-stu-id="e9802-119">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="e9802-120">嵌套運算式中的 Stackalloc</span><span class="sxs-lookup"><span data-stu-id="e9802-120">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="e9802-121">增強插值逐字字串</span><span class="sxs-lookup"><span data-stu-id="e9802-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="e9802-122">C# 8.0 在 **.NET Core 3.x**和 **.NET 標準 2.1**上受支援。</span><span class="sxs-lookup"><span data-stu-id="e9802-122">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="e9802-123">有關詳細資訊，請參閱[C# 語言版本控制](../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="e9802-123">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="e9802-124">本文的其餘部分會簡短說明這些功能。</span><span class="sxs-lookup"><span data-stu-id="e9802-124">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="e9802-125">提供教學課程及概觀的連結，其中包含深入詳盡的文章。</span><span class="sxs-lookup"><span data-stu-id="e9802-125">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="e9802-126">您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：</span><span class="sxs-lookup"><span data-stu-id="e9802-126">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="e9802-127">安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="e9802-127">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="e9802-128">複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="e9802-128">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="e9802-129">將目前的目錄設為 *try-samples* 存放庫的 *csharp8* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="e9802-129">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="e9802-130">執行 `dotnet try`。</span><span class="sxs-lookup"><span data-stu-id="e9802-130">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="e9802-131">唯讀成員</span><span class="sxs-lookup"><span data-stu-id="e9802-131">Readonly members</span></span>

<span data-ttu-id="e9802-132">您可以將`readonly`修改器應用於結構的成員。</span><span class="sxs-lookup"><span data-stu-id="e9802-132">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="e9802-133">它指示成員不修改狀態。</span><span class="sxs-lookup"><span data-stu-id="e9802-133">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="e9802-134">它比套用 `readonly` 修飾詞到 `struct` 宣告更為精細。</span><span class="sxs-lookup"><span data-stu-id="e9802-134">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="e9802-135">假設您有下列可變動結構：</span><span class="sxs-lookup"><span data-stu-id="e9802-135">Consider the following mutable struct:</span></span>

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

<span data-ttu-id="e9802-136">與大多數結構一樣，`ToString()`該方法不會修改狀態。</span><span class="sxs-lookup"><span data-stu-id="e9802-136">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="e9802-137">您可以透過新增 `readonly` 修飾詞到 `ToString()` 的宣告來指出此情況：</span><span class="sxs-lookup"><span data-stu-id="e9802-137">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="e9802-138">前面的更改將生成編譯器警告，因為`ToString`訪問`Distance`屬性，該屬性未標記為`readonly`：</span><span class="sxs-lookup"><span data-stu-id="e9802-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="e9802-139">當它需要建立防禦性複本時，編譯器會警告您。</span><span class="sxs-lookup"><span data-stu-id="e9802-139">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="e9802-140">屬性`Distance`不會更改狀態，因此可以通過將`readonly`修改器添加到聲明來修復此警告：</span><span class="sxs-lookup"><span data-stu-id="e9802-140">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="e9802-141">請注意，`readonly`在唯讀屬性上需要修改器。</span><span class="sxs-lookup"><span data-stu-id="e9802-141">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="e9802-142">編譯器不假定`get`訪問器不修改狀態，但您必須顯式聲明`readonly`。</span><span class="sxs-lookup"><span data-stu-id="e9802-142">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="e9802-143">自動實現的屬性是一個例外;編譯器將所有自動實現的 getter 視為唯讀，因此此處無需將`readonly`修飾符添加到 和`X``Y`屬性。</span><span class="sxs-lookup"><span data-stu-id="e9802-143">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="e9802-144">編譯器強制實施`readonly`成員不修改狀態的規則。</span><span class="sxs-lookup"><span data-stu-id="e9802-144">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="e9802-145">除非刪除修改器，`readonly`否則以下方法不會編譯：</span><span class="sxs-lookup"><span data-stu-id="e9802-145">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="e9802-146">此功能可讓您指定您的設計意圖，以便編譯器可以強制套用，並根據該意圖進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="e9802-146">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span> <span data-ttu-id="e9802-147">您可以在 上[`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)的語言參考文章中瞭解有關唯讀成員的更多內容。</span><span class="sxs-lookup"><span data-stu-id="e9802-147">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="e9802-148">預設介面方法</span><span class="sxs-lookup"><span data-stu-id="e9802-148">Default interface methods</span></span>

<span data-ttu-id="e9802-149">您現在可以新增成員到介面並提供那些成員的實作。</span><span class="sxs-lookup"><span data-stu-id="e9802-149">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="e9802-150">此語言功能可讓 API 作者在較新的版本中新增方法到介面中，而不會因為該介面的現有實作造成原始程式碼或二進位檔案相容性受影響。</span><span class="sxs-lookup"><span data-stu-id="e9802-150">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="e9802-151">現有實作會「繼承」\*\* 預設實作。</span><span class="sxs-lookup"><span data-stu-id="e9802-151">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="e9802-152">此功能也會讓 C# 與以 Android 或 Swift 為目標的 API 相互操作，這些 API 支援類似的功能。</span><span class="sxs-lookup"><span data-stu-id="e9802-152">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="e9802-153">預設介面方法還啟用類似于"traits"語言功能的方案。</span><span class="sxs-lookup"><span data-stu-id="e9802-153">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="e9802-154">預設介面方法會影響許多方案和語言元素。</span><span class="sxs-lookup"><span data-stu-id="e9802-154">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="e9802-155">我們的第一個教學課程涵蓋[使用預設實作更新介面](../tutorials/default-interface-methods-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="e9802-155">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="e9802-156">其他教學課程與參考更新即將在正式發行時推出。</span><span class="sxs-lookup"><span data-stu-id="e9802-156">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="e9802-157">在更多位置使用更多的模式</span><span class="sxs-lookup"><span data-stu-id="e9802-157">More patterns in more places</span></span>

<span data-ttu-id="e9802-158">**模式比對**讓您能夠使用提供相關但不同種類資料間圖形相依功能的工具。</span><span class="sxs-lookup"><span data-stu-id="e9802-158">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="e9802-159">C# 7.0 使用[`is`](../language-reference/keywords/is.md)運算式和 語句引入了類型模式和常量[`switch`](../language-reference/keywords/switch.md)模式的語法。</span><span class="sxs-lookup"><span data-stu-id="e9802-159">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="e9802-160">這些功能代表達成支援程式設計範例 (資料及功能分開) 的暫訂步驟。</span><span class="sxs-lookup"><span data-stu-id="e9802-160">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="e9802-161">隨著業界趨勢轉向微服務及其他雲端式架構，也產生其他語言工具的需求。</span><span class="sxs-lookup"><span data-stu-id="e9802-161">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="e9802-162">C# 8.0 可展開此詞彙，讓您能夠在程式碼中的更多位置，使用更多的模式運算式。</span><span class="sxs-lookup"><span data-stu-id="e9802-162">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="e9802-163">當您的資料與功能分開時，請考慮使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="e9802-163">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="e9802-164">當您的演算法取決於物件執行階段類型外的事實時，請考慮使用模式比對。</span><span class="sxs-lookup"><span data-stu-id="e9802-164">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="e9802-165">這些技術提供表達設計的另一種方式。</span><span class="sxs-lookup"><span data-stu-id="e9802-165">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="e9802-166">除了在新位置的新模式之外，C# 8.0 還新增了**遞迴模式**。</span><span class="sxs-lookup"><span data-stu-id="e9802-166">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="e9802-167">任何模式運算式的結果皆是運算式。</span><span class="sxs-lookup"><span data-stu-id="e9802-167">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="e9802-168">遞迴模式僅為套用到其他模式運算式輸出的模式運算式。</span><span class="sxs-lookup"><span data-stu-id="e9802-168">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="e9802-169">switch 運算式</span><span class="sxs-lookup"><span data-stu-id="e9802-169">Switch expressions</span></span>

<span data-ttu-id="e9802-170">通常，語句[`switch`](../language-reference/keywords/switch.md)在其`case`每個塊中生成值。</span><span class="sxs-lookup"><span data-stu-id="e9802-170">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="e9802-171">**Switch 運算式**讓您能夠使用更精簡的運算式語法。</span><span class="sxs-lookup"><span data-stu-id="e9802-171">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="e9802-172">重複的 `case` 及 `break` 關鍵字和大括號都減少了。</span><span class="sxs-lookup"><span data-stu-id="e9802-172">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="e9802-173">例如，請考慮以下列出彩虹色彩的列舉：</span><span class="sxs-lookup"><span data-stu-id="e9802-173">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="e9802-174">如果您的應用程式定義了由 `R`、`G` 和 `B` 元件所建構的 `RGBColor` 型別，則可以使用包含 switch 運算式的下列方法，將 `Rainbow` 值轉換為其 RGB 值：</span><span class="sxs-lookup"><span data-stu-id="e9802-174">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="e9802-175">幾項語法改進如下：</span><span class="sxs-lookup"><span data-stu-id="e9802-175">There are several syntax improvements here:</span></span>

- <span data-ttu-id="e9802-176">變數挪到了 `switch` 關鍵字前。</span><span class="sxs-lookup"><span data-stu-id="e9802-176">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="e9802-177">不同的順序讓您可輕鬆區分出 switch 運算式及 switch 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9802-177">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="e9802-178">`case` 及 `:` 元素取代為 `=>`。</span><span class="sxs-lookup"><span data-stu-id="e9802-178">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="e9802-179">這更加精簡而且符合直覺。</span><span class="sxs-lookup"><span data-stu-id="e9802-179">It's more concise and intuitive.</span></span>
- <span data-ttu-id="e9802-180">`default` 案例取代為 `_` 捨棄。</span><span class="sxs-lookup"><span data-stu-id="e9802-180">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="e9802-181">主體為運算式，而非陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9802-181">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="e9802-182">對比該語法與使用傳統 `switch` 陳述式的對等程式碼：</span><span class="sxs-lookup"><span data-stu-id="e9802-182">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a><span data-ttu-id="e9802-183">屬性模式</span><span class="sxs-lookup"><span data-stu-id="e9802-183">Property patterns</span></span>

<span data-ttu-id="e9802-184">**屬性模式**使您得以比對所檢查物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9802-184">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="e9802-185">試想必須根據購買者地址計算營業稅的電子商務網站。</span><span class="sxs-lookup"><span data-stu-id="e9802-185">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="e9802-186">這種計算不是`Address`類的核心責任。</span><span class="sxs-lookup"><span data-stu-id="e9802-186">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="e9802-187">這項計算會隨著時間變更，而且可能比地址格式的變更更加頻繁。</span><span class="sxs-lookup"><span data-stu-id="e9802-187">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="e9802-188">營業稅額取決於地址的 `State` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9802-188">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="e9802-189">下列方法會使用屬性模式，從地址及價格計算營業稅：</span><span class="sxs-lookup"><span data-stu-id="e9802-189">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="e9802-190">模式比對會建立簡潔的語法以表示此演算法。</span><span class="sxs-lookup"><span data-stu-id="e9802-190">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="e9802-191">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="e9802-191">Tuple patterns</span></span>

<span data-ttu-id="e9802-192">某些演算法需仰賴數個輸入。</span><span class="sxs-lookup"><span data-stu-id="e9802-192">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="e9802-193">**Tuple 模式**可讓您根據以 [tuple](../tuples.md) 形式表示的多個值進行切換。</span><span class="sxs-lookup"><span data-stu-id="e9802-193">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="e9802-194">下列範例示範「剪刀、石頭、布」\*\* 遊戲的 switch 運算式：</span><span class="sxs-lookup"><span data-stu-id="e9802-194">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

<span data-ttu-id="e9802-195">訊息會指出優勝者。</span><span class="sxs-lookup"><span data-stu-id="e9802-195">The messages indicate the winner.</span></span> <span data-ttu-id="e9802-196">捨棄案例代表平手的三個組合，或其他文字輸入。</span><span class="sxs-lookup"><span data-stu-id="e9802-196">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="e9802-197">位置模式</span><span class="sxs-lookup"><span data-stu-id="e9802-197">Positional patterns</span></span>

<span data-ttu-id="e9802-198">某些類型會包含 `Deconstruct` 方法，其能將自己的屬性解構成離散變數。</span><span class="sxs-lookup"><span data-stu-id="e9802-198">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="e9802-199">可存取 `Deconstruct` 方法時，您可以使用**位置模式**來檢查物件的屬性，然後將那些屬性用於某個模式。</span><span class="sxs-lookup"><span data-stu-id="e9802-199">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="e9802-200">請考慮下列 `Point` 類別，其包含 `Deconstruct` 方法來針對 `X` 和 `Y` 建立離散變數：</span><span class="sxs-lookup"><span data-stu-id="e9802-200">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="e9802-201">此外，請考慮下列代表象限各種不同位置的列舉：</span><span class="sxs-lookup"><span data-stu-id="e9802-201">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

<span data-ttu-id="e9802-202">下列方法會使用**位置模式**擷取 `x` 及 `y` 的值。</span><span class="sxs-lookup"><span data-stu-id="e9802-202">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="e9802-203">接著，它使用 `when` 子句判斷點的 `Quadrant`：</span><span class="sxs-lookup"><span data-stu-id="e9802-203">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

<span data-ttu-id="e9802-204">當 `x` 或 `y` 為 0 (非兩者) 時，上述 switch 中的捨棄模式就會符合。</span><span class="sxs-lookup"><span data-stu-id="e9802-204">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="e9802-205">switch 運算式必須產生值或者擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9802-205">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="e9802-206">若沒有任何案例符合，則 switch 運算式會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9802-206">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="e9802-207">如果未涵蓋交換器運算式中的所有可能情況，編譯器將為您生成警告。</span><span class="sxs-lookup"><span data-stu-id="e9802-207">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="e9802-208">您可以在此[模式比對進階教學課程](../tutorials/pattern-matching.md)中探索模式比對技巧。</span><span class="sxs-lookup"><span data-stu-id="e9802-208">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="e9802-209">using 宣告</span><span class="sxs-lookup"><span data-stu-id="e9802-209">Using declarations</span></span>

<span data-ttu-id="e9802-210">**using 宣告**為以 `using` 關鍵字開頭的變數宣告。</span><span class="sxs-lookup"><span data-stu-id="e9802-210">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="e9802-211">其會告知編譯器，應在括住的範圍結尾處置所宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="e9802-211">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="e9802-212">例如，試想下列寫入文字檔的程式碼：</span><span class="sxs-lookup"><span data-stu-id="e9802-212">For example, consider the following code that writes a text file:</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

<span data-ttu-id="e9802-213">在上述範例中，到達方法的右大括號時，就會處置檔案。</span><span class="sxs-lookup"><span data-stu-id="e9802-213">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="e9802-214">這是宣告 `file` 之範圍的結尾。</span><span class="sxs-lookup"><span data-stu-id="e9802-214">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="e9802-215">上述程式碼相當於使用傳統 [using 陳述式](../language-reference/keywords/using-statement.md)的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e9802-215">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

<span data-ttu-id="e9802-216">在上述範例中，到達與 `using` 陳述式相關的結尾右大括號時，就會處置檔案。</span><span class="sxs-lookup"><span data-stu-id="e9802-216">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="e9802-217">在這兩個案例中，編譯器皆會產生對 `Dispose()` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e9802-217">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="e9802-218">如果語句中的運算式不是一次性的，`using`編譯器將建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9802-218">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="e9802-219">靜態區域函式</span><span class="sxs-lookup"><span data-stu-id="e9802-219">Static local functions</span></span>

<span data-ttu-id="e9802-220">您現可將 `static` 修飾詞新增至區域函式，以確保區域函式不會從括住的範圍擷取 (參考) 任何變數。</span><span class="sxs-lookup"><span data-stu-id="e9802-220">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="e9802-221">這樣會產生 `CS8421`「靜態區域函式不可包含對 \<變數> 的參考」。</span><span class="sxs-lookup"><span data-stu-id="e9802-221">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="e9802-222">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e9802-222">Consider the following code.</span></span> <span data-ttu-id="e9802-223">區域函式 `LocalFunction` 會存取在所括住範圍 (方法 `M`) 中宣告的變數 `y`。</span><span class="sxs-lookup"><span data-stu-id="e9802-223">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="e9802-224">因此，無法使用 `static` 修飾詞宣告 `LocalFunction`：</span><span class="sxs-lookup"><span data-stu-id="e9802-224">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="e9802-225">下列程式碼包含靜態區域函式。</span><span class="sxs-lookup"><span data-stu-id="e9802-225">The following code contains a static local function.</span></span> <span data-ttu-id="e9802-226">因為其不會存取所括住範圍中的任何變數，所以可以為靜態：</span><span class="sxs-lookup"><span data-stu-id="e9802-226">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="e9802-227">可處置的 ref struct</span><span class="sxs-lookup"><span data-stu-id="e9802-227">Disposable ref structs</span></span>

<span data-ttu-id="e9802-228">使用`struct``ref`修飾符聲明的不能實現任何介面，因此無法實現<xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="e9802-228">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="e9802-229">因此，若要讓 `ref struct` 可處置，其必須具有可存取的 `void Dispose()` 方法。</span><span class="sxs-lookup"><span data-stu-id="e9802-229">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="e9802-230">此功能也適用于`readonly ref struct`聲明。</span><span class="sxs-lookup"><span data-stu-id="e9802-230">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="e9802-231">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="e9802-231">Nullable reference types</span></span>

<span data-ttu-id="e9802-232">在可為 Null 的註解內容中，參考型別的任何變數皆視為**不可為 Null 的參考型別**。</span><span class="sxs-lookup"><span data-stu-id="e9802-232">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="e9802-233">若您要表示變數可能為 Null，則必須使用 `?` 來附加類型名稱，以將變數宣告為**可為 Null 的參考型別**。</span><span class="sxs-lookup"><span data-stu-id="e9802-233">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="e9802-234">對於不可為 Null 的參考型別，編譯器會使用流程分析來確保將區域變數在宣告時，初始化為非 Null 的值。</span><span class="sxs-lookup"><span data-stu-id="e9802-234">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="e9802-235">必須在建構期間將欄位初始化。</span><span class="sxs-lookup"><span data-stu-id="e9802-235">Fields must be initialized during construction.</span></span> <span data-ttu-id="e9802-236">如果變數不是通過調用任何可用的建構函式或初始化器設置，編譯器將生成警告。</span><span class="sxs-lookup"><span data-stu-id="e9802-236">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="e9802-237">此外，也不能對不可為 Null 的參考型別指派可為 Null 的值。</span><span class="sxs-lookup"><span data-stu-id="e9802-237">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="e9802-238">系統不會檢查可為 Null 的參考型別，來確保其不會指派或初始化為 Null。</span><span class="sxs-lookup"><span data-stu-id="e9802-238">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="e9802-239">不過，編譯器會在將變數存取或指派至不可為 Null 的參考型別之前，使用流程分析來確保已對可為 Null 參考型別的所有變數檢查可 Null 性。</span><span class="sxs-lookup"><span data-stu-id="e9802-239">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="e9802-240">您可在[可為 Null 的參考型別](../nullable-references.md)概觀中深入了解功能。</span><span class="sxs-lookup"><span data-stu-id="e9802-240">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="e9802-241">在此[可為 Null 的參考型別教學課程](../tutorials/nullable-reference-types.md)中，親自在新的應用程式內試用。</span><span class="sxs-lookup"><span data-stu-id="e9802-241">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="e9802-242">在[移轉應用程式以使用可為 Null 的參考型別教學課程](../tutorials/upgrade-to-nullable-references.md)中，了解移轉現有程式碼基底的步驟，進而利用可為 Null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="e9802-242">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="e9802-243">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="e9802-243">Asynchronous streams</span></span>

<span data-ttu-id="e9802-244">自 C# 8.0 起，您可非同步地建立及取用資料流。</span><span class="sxs-lookup"><span data-stu-id="e9802-244">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="e9802-245">傳回非同步資料流的方法具有三個屬性：</span><span class="sxs-lookup"><span data-stu-id="e9802-245">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="e9802-246">使用 `async` 修飾詞來宣告。</span><span class="sxs-lookup"><span data-stu-id="e9802-246">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="e9802-247">其會傳回 <xref:System.Collections.Generic.IAsyncEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="e9802-247">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="e9802-248">方法會包含 `yield return` 陳述式以傳回非同步資料流中的後續元素。</span><span class="sxs-lookup"><span data-stu-id="e9802-248">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="e9802-249">當您列舉資料流的元素時，必須在 `foreach` 關鍵字前新增 `await` 關鍵字，才可取用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="e9802-249">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="e9802-250">需要方法才可新增 `await` 關鍵字，而且該方法列舉要使用 `async` 修飾詞宣告的非同步資料流，並傳回 `async` 方法允許的類型。</span><span class="sxs-lookup"><span data-stu-id="e9802-250">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="e9802-251">通常這代表傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="e9802-251">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e9802-252">也可以是 <xref:System.Threading.Tasks.ValueTask> 或 <xref:System.Threading.Tasks.ValueTask%601>。</span><span class="sxs-lookup"><span data-stu-id="e9802-252">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="e9802-253">方法可同時取用及產生非同步資料流，這代表其會傳回 <xref:System.Collections.Generic.IAsyncEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="e9802-253">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="e9802-254">下列程式碼會產生 0 到 19 的序列，產生每個號碼需等待 100 毫秒的間隔：</span><span class="sxs-lookup"><span data-stu-id="e9802-254">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="e9802-255">您應使用 `await foreach` 陳述式列舉序列：</span><span class="sxs-lookup"><span data-stu-id="e9802-255">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="e9802-256">您可在我們有關[建立及取用非同步資料流](../tutorials/generate-consume-asynchronous-stream.md)的教學課程中，親自試用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="e9802-256">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="e9802-257">預設情況元素在捕獲的上下文中處理。</span><span class="sxs-lookup"><span data-stu-id="e9802-257">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="e9802-258">如果要禁用上下文捕獲，請使用<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>擴充方法。</span><span class="sxs-lookup"><span data-stu-id="e9802-258">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="e9802-259">有關同步上下文和捕獲當前上下文的詳細資訊，請參閱有關[使用基於任務的非同步模式](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="e9802-259">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="e9802-260">索引和範圍</span><span class="sxs-lookup"><span data-stu-id="e9802-260">Indices and ranges</span></span>

<span data-ttu-id="e9802-261">索引和範圍提供了簡潔的語法，用於按循序存取單個元素或範圍。</span><span class="sxs-lookup"><span data-stu-id="e9802-261">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="e9802-262">此語言支援依賴于兩種新類型和兩個新運算子：</span><span class="sxs-lookup"><span data-stu-id="e9802-262">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="e9802-263"><xref:System.Index?displayProperty=nameWithType> 代表序列的索引。</span><span class="sxs-lookup"><span data-stu-id="e9802-263"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="e9802-264">來自結束運算子`^`的索引 ，它指定索引相對於序列的末尾。</span><span class="sxs-lookup"><span data-stu-id="e9802-264">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="e9802-265"><xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。</span><span class="sxs-lookup"><span data-stu-id="e9802-265"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="e9802-266">範圍運算子`..`， 指定範圍的開始和結束作為其運算元。</span><span class="sxs-lookup"><span data-stu-id="e9802-266">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="e9802-267">讓我們從索引的規則開始。</span><span class="sxs-lookup"><span data-stu-id="e9802-267">Let's start with the rules for indexes.</span></span> <span data-ttu-id="e9802-268">假設有一個陣列 `sequence`。</span><span class="sxs-lookup"><span data-stu-id="e9802-268">Consider an array `sequence`.</span></span> <span data-ttu-id="e9802-269">`0` 索引與 `sequence[0]` 相同。</span><span class="sxs-lookup"><span data-stu-id="e9802-269">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="e9802-270">`^0` 索引與 `sequence[sequence.Length]` 相同。</span><span class="sxs-lookup"><span data-stu-id="e9802-270">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="e9802-271">請注意，`sequence[^0]` 會擲回例外狀況，就樣 `sequence[sequence.Length]` 會這樣做一樣。</span><span class="sxs-lookup"><span data-stu-id="e9802-271">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="e9802-272">針對任何數字 `n`，索引 `^n` 與 `sequence.Length - n` 相同。</span><span class="sxs-lookup"><span data-stu-id="e9802-272">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="e9802-273">指定範圍「開頭」\*\* 與「結尾」\*\* 的範圍。</span><span class="sxs-lookup"><span data-stu-id="e9802-273">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="e9802-274">範圍的開頭是包羅萬象的，但範圍的結束是獨佔的，這意味著*起始項*包含在範圍內，但範圍中不包括*結束*。</span><span class="sxs-lookup"><span data-stu-id="e9802-274">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="e9802-275">範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。</span><span class="sxs-lookup"><span data-stu-id="e9802-275">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="e9802-276">讓我們來看以下幾個範例。</span><span class="sxs-lookup"><span data-stu-id="e9802-276">Let's look at a few examples.</span></span> <span data-ttu-id="e9802-277">試想下列使用其索引從開頭或從結尾標註的陣列：</span><span class="sxs-lookup"><span data-stu-id="e9802-277">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="e9802-278">您可使用 `^1` 索引擷取最後一個字組：</span><span class="sxs-lookup"><span data-stu-id="e9802-278">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="e9802-279">下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。</span><span class="sxs-lookup"><span data-stu-id="e9802-279">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="e9802-280">其會包含 `words[1]` 到 `words[3]`。</span><span class="sxs-lookup"><span data-stu-id="e9802-280">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="e9802-281">項目 `words[4]` 不在範圍內。</span><span class="sxs-lookup"><span data-stu-id="e9802-281">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="e9802-282">下列程式碼會建立具有 "lazy" 和 "dog" 的子範圍。</span><span class="sxs-lookup"><span data-stu-id="e9802-282">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="e9802-283">其包含 `words[^2]` 及 `words[^1]`。</span><span class="sxs-lookup"><span data-stu-id="e9802-283">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="e9802-284">不包括最終索引`words[^0]`：</span><span class="sxs-lookup"><span data-stu-id="e9802-284">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="e9802-285">下列範例會建立不限定開始、結束或兩者的範圍：</span><span class="sxs-lookup"><span data-stu-id="e9802-285">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="e9802-286">您也可將範圍宣告為變數：</span><span class="sxs-lookup"><span data-stu-id="e9802-286">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="e9802-287">接著範圍可用於 `[` 及 `]` 字元中：</span><span class="sxs-lookup"><span data-stu-id="e9802-287">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="e9802-288">不僅陣列支援索引和範圍。</span><span class="sxs-lookup"><span data-stu-id="e9802-288">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="e9802-289">您還可以使用索引和範圍與[字串](../language-reference/builtin-types/reference-types.md#the-string-type)、<xref:System.Span%601>或<xref:System.ReadOnlySpan%601>。</span><span class="sxs-lookup"><span data-stu-id="e9802-289">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="e9802-290">有關詳細資訊，請參閱[索引和範圍的類型支援](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges)。</span><span class="sxs-lookup"><span data-stu-id="e9802-290">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="e9802-291">您可以在[索引及範圍](../tutorials/ranges-indexes.md)上的教學課程中探索更多關於索引及範圍的資訊。</span><span class="sxs-lookup"><span data-stu-id="e9802-291">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="e9802-292">空合併分配</span><span class="sxs-lookup"><span data-stu-id="e9802-292">Null-coalescing assignment</span></span>

<span data-ttu-id="e9802-293">C# 8.0 引入了空聚聚指派運算子`??=`。</span><span class="sxs-lookup"><span data-stu-id="e9802-293">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="e9802-294">僅當左側運算元`??=`計算到`null`時，才能使用運算子將其右側運算元的值分配給其左側運算元。</span><span class="sxs-lookup"><span data-stu-id="e9802-294">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="e9802-295">有關詳細資訊，請參閱[？和？？• 運算子](../language-reference/operators/null-coalescing-operator.md)文章。</span><span class="sxs-lookup"><span data-stu-id="e9802-295">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="e9802-296">非託管構造類型</span><span class="sxs-lookup"><span data-stu-id="e9802-296">Unmanaged constructed types</span></span>

<span data-ttu-id="e9802-297">在 C# 7.3 和更早版本中，構造類型（至少包含一個類型參數的類型）不能為[非託管類型](../language-reference/builtin-types/unmanaged-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e9802-297">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="e9802-298">從 C# 8.0 開始，如果構造的數值型別僅包含非託管類型的欄位，則該數值型別將處於非託管類型。</span><span class="sxs-lookup"><span data-stu-id="e9802-298">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="e9802-299">例如，給定泛型`Coords<T>`類型的以下定義：</span><span class="sxs-lookup"><span data-stu-id="e9802-299">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="e9802-300">類型`Coords<int>`是 C# 8.0 及更高版本中的非託管類型。</span><span class="sxs-lookup"><span data-stu-id="e9802-300">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="e9802-301">與任何非託管類型一樣，您可以創建指向此類型的變數的指標，或在[堆疊上為此類實例分配區塊](../language-reference/operators/stackalloc.md)：</span><span class="sxs-lookup"><span data-stu-id="e9802-301">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="e9802-302">有關詳細資訊，請參閱[非託管類型](../language-reference/builtin-types/unmanaged-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e9802-302">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="e9802-303">嵌套運算式中的 Stackalloc</span><span class="sxs-lookup"><span data-stu-id="e9802-303">Stackalloc in nested expressions</span></span>

<span data-ttu-id="e9802-304">從 C# 8.0 開始，如果[stackalloc](../language-reference/operators/stackalloc.md)運算式的結果為<xref:System.Span%601?displayProperty=nameWithType><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>或 類型，則可以在其他`stackalloc`運算式中使用運算式：</span><span class="sxs-lookup"><span data-stu-id="e9802-304">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="e9802-305">增強插值逐字字串</span><span class="sxs-lookup"><span data-stu-id="e9802-305">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="e9802-306">插值逐`$`字`@`字串中的[interpolated](../language-reference/tokens/interpolated.md)和 標記的順序可以是任意：兩`$@"..."``@$"..."`者都是有效插值逐字字串。</span><span class="sxs-lookup"><span data-stu-id="e9802-306">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="e9802-307">在早期的 C# 版本中`$`，權杖必須出現在權杖`@`之前。</span><span class="sxs-lookup"><span data-stu-id="e9802-307">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
