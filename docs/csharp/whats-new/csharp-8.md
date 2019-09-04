---
title: C# 8.0 的新功能 - C# 指南
description: 大致了解 C# 8.0 中可用的新功能。 此文章為適用於預覽 5 的最新資訊。
ms.date: 09/02/2019
ms.openlocfilehash: 7210f2e978f307b3ecef2eff272fea0d19025de6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252894"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="3bb6c-104">C# 8.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="3bb6c-104">What's new in C# 8.0</span></span>

<span data-ttu-id="3bb6c-105">您已經可以試用許多 C# 語言的增強功能。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-105">There are many enhancements to the C# language that you can try out already.</span></span>

- [<span data-ttu-id="3bb6c-106">唯讀成員</span><span class="sxs-lookup"><span data-stu-id="3bb6c-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="3bb6c-107">預設介面成員</span><span class="sxs-lookup"><span data-stu-id="3bb6c-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="3bb6c-108">[模式比對增強功能](#more-patterns-in-more-places)：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="3bb6c-109">Switch 運算式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-109">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="3bb6c-110">屬性模式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-110">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="3bb6c-111">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-111">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="3bb6c-112">位置模式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="3bb6c-113">Using 宣告</span><span class="sxs-lookup"><span data-stu-id="3bb6c-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="3bb6c-114">靜態區域函式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="3bb6c-115">可處置的 ref struct</span><span class="sxs-lookup"><span data-stu-id="3bb6c-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="3bb6c-116">可為 Null 的參考類型</span><span class="sxs-lookup"><span data-stu-id="3bb6c-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="3bb6c-117">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="3bb6c-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="3bb6c-118">索引和範圍</span><span class="sxs-lookup"><span data-stu-id="3bb6c-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="3bb6c-119">增強內插逐字字串</span><span class="sxs-lookup"><span data-stu-id="3bb6c-119">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

> [!NOTE]
> <span data-ttu-id="3bb6c-120">此文章內容為 C# 8.0 預覽 5 的最新更新。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-120">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="3bb6c-121">本文的其餘部分會簡短說明這些功能。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-121">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="3bb6c-122">提供教學課程及概觀的連結，其中包含深入詳盡的文章。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-122">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="3bb6c-123">您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-123">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="3bb6c-124">安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-124">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="3bb6c-125">複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-125">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="3bb6c-126">將目前的目錄設為 *try-samples* 存放庫的 *csharp8* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-126">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="3bb6c-127">執行 `dotnet try`。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-127">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="3bb6c-128">唯讀成員</span><span class="sxs-lookup"><span data-stu-id="3bb6c-128">Readonly members</span></span>

<span data-ttu-id="3bb6c-129">您可以套用 `readonly` 修飾詞到結構的任何成員。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-129">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="3bb6c-130">它指出成員不會修改狀態。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-130">It indicates that the member does not modify state.</span></span> <span data-ttu-id="3bb6c-131">它比套用 `readonly` 修飾詞到 `struct` 宣告更為精細。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-131">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="3bb6c-132">假設您有下列可變動結構：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-132">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="3bb6c-133">就像大部分的結構一樣，`ToString()` 方法不會修改狀態。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-133">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="3bb6c-134">您可以透過新增 `readonly` 修飾詞到 `ToString()` 的宣告來指出此情況：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-134">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="3bb6c-135">上述變更會產生編譯器警告，因為 `ToString` 會存取 `Distance` 屬性，但此屬性未標示為 `readonly`：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-135">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="3bb6c-136">當它需要建立防禦性複本時，編譯器會警告您。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-136">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="3bb6c-137">`Distance` 屬性不會變更狀態，因此您可以透過新增 `readonly` 修飾詞到宣告以修正此警告：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-137">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="3bb6c-138">請注意，`readonly` 修飾詞在唯讀屬性上是必要的。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-138">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="3bb6c-139">編譯器不會假設 `get` 存取子不會修改狀態；您必須明確地宣告 `readonly`。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-139">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="3bb6c-140">編譯器會強制 `readonly` 成員不得修改狀態的規則。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-140">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="3bb6c-141">除非您移除 `readonly` 修飾詞，否則下列方法將不會編譯：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-141">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="3bb6c-142">此功能可讓您指定您的設計意圖，以便編譯器可以強制套用，並根據該意圖進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-142">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="3bb6c-143">預設介面成員</span><span class="sxs-lookup"><span data-stu-id="3bb6c-143">Default interface members</span></span>

<span data-ttu-id="3bb6c-144">您現在可以新增成員到介面並提供那些成員的實作。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-144">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="3bb6c-145">此語言功能可讓 API 作者在較新的版本中新增方法到介面中，而不會因為該介面的現有實作造成原始程式碼或二進位檔案相容性受影響。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-145">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="3bb6c-146">現有實作會「繼承」預設實作。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-146">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="3bb6c-147">此功能也會讓 C# 與以 Android 或 Swift 為目標的 API 相互操作，這些 API 支援類似的功能。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-147">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="3bb6c-148">預設介面成員也會啟用類似「特徵」語言功能的案例。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-148">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="3bb6c-149">預設介面成員會影響許多案例與語言元素。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-149">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="3bb6c-150">我們的第一個教學課程涵蓋[使用預設實作更新介面](../tutorials/default-interface-members-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-150">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="3bb6c-151">其他教學課程與參考更新即將在正式發行時推出。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-151">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="3bb6c-152">在更多位置使用更多的模式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-152">More patterns in more places</span></span>

<span data-ttu-id="3bb6c-153">**模式比對**讓您能夠使用提供相關但不同種類資料間圖形相依功能的工具。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-153">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="3bb6c-154">C# 7.0 透過使用 [`is`](../language-reference/keywords/is.md) 運算式及 [`switch`](../language-reference/keywords/switch.md) 陳述式，推出了類型模式及常數模式的語法。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-154">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="3bb6c-155">這些功能代表達成支援程式設計範例 (資料及功能分開) 的暫訂步驟。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-155">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="3bb6c-156">隨著業界趨勢轉向微服務及其他雲端式架構，也產生其他語言工具的需求。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-156">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="3bb6c-157">C# 8.0 可展開此詞彙，讓您能夠在程式碼中的更多位置，使用更多的模式運算式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-157">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="3bb6c-158">當您的資料與功能分開時，請考慮使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-158">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="3bb6c-159">當您的演算法取決於物件執行階段類型外的事實時，請考慮使用模式比對。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-159">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="3bb6c-160">這些技術提供表達設計的另一種方式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-160">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="3bb6c-161">除了在新位置的新模式之外，C# 8.0 還新增了**遞迴模式**。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-161">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="3bb6c-162">任何模式運算式的結果皆是運算式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-162">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="3bb6c-163">遞迴模式僅為套用到其他模式運算式輸出的模式運算式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-163">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="3bb6c-164">switch 運算式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-164">switch expressions</span></span>

<span data-ttu-id="3bb6c-165">通常，[`switch`](../language-reference/keywords/switch.md) 陳述式會在其各個 `case` 區塊中產生值。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-165">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="3bb6c-166">**Switch 運算式**讓您能夠使用更精簡的運算式語法。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-166">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="3bb6c-167">重複的 `case` 及 `break` 關鍵字和大括號都減少了。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-167">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="3bb6c-168">例如，請考慮以下列出彩虹色彩的列舉：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-168">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="3bb6c-169">如果您的應用程式定義了由 `R`、`G` 和 `B` 元件所建構的 `RGBColor` 型別，則可以使用包含 switch 運算式的下列方法，將 `Rainbow` 值轉換為其 RGB 值：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-169">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="3bb6c-170">幾項語法改進如下：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-170">There are several syntax improvements here:</span></span>

- <span data-ttu-id="3bb6c-171">變數挪到了 `switch` 關鍵字前。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-171">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="3bb6c-172">不同的順序讓您可輕鬆區分出 switch 運算式及 switch 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-172">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="3bb6c-173">`case` 及 `:` 元素取代為 `=>`。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-173">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="3bb6c-174">這更加精簡而且符合直覺。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-174">It's more concise and intuitive.</span></span>
- <span data-ttu-id="3bb6c-175">`default` 案例取代為 `_` 捨棄。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-175">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="3bb6c-176">主體為運算式，而非陳述式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-176">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="3bb6c-177">對比該語法與使用傳統 `switch` 陳述式的對等程式碼：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-177">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="3bb6c-178">屬性模式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-178">Property patterns</span></span>

<span data-ttu-id="3bb6c-179">**屬性模式**使您得以比對所檢查物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-179">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="3bb6c-180">試想必須根據購買者地址計算營業稅的電子商務網站。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-180">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="3bb6c-181">`Address` 類別的核心功能並非負責進行該計算。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-181">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="3bb6c-182">這項計算會隨著時間變更，而且可能比地址格式的變更更加頻繁。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-182">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="3bb6c-183">營業稅額取決於地址的 `State` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-183">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="3bb6c-184">下列方法會使用屬性模式，從地址及價格計算營業稅：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-184">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="3bb6c-185">模式比對會建立簡潔的語法以表示此演算法。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-185">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="3bb6c-186">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-186">Tuple patterns</span></span>

<span data-ttu-id="3bb6c-187">某些演算法需仰賴數個輸入。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-187">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="3bb6c-188">**Tuple 模式**可讓您根據以 [tuple](../tuples.md) 形式表示的多個值進行切換。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-188">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="3bb6c-189">下列範例示範「剪刀、石頭、布」遊戲的 switch 運算式：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-189">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="3bb6c-190">訊息會指出優勝者。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-190">The messages indicate the winner.</span></span> <span data-ttu-id="3bb6c-191">捨棄案例代表平手的三個組合，或其他文字輸入。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-191">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="3bb6c-192">位置模式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-192">Positional patterns</span></span>

<span data-ttu-id="3bb6c-193">某些類型會包含 `Deconstruct` 方法，其能將自己的屬性解構成離散變數。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-193">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="3bb6c-194">可存取 `Deconstruct` 方法時，您可以使用**位置模式**來檢查物件的屬性，然後將那些屬性用於某個模式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-194">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="3bb6c-195">請考慮下列 `Point` 類別，其包含 `Deconstruct` 方法來針對 `X` 和 `Y` 建立離散變數：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-195">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="3bb6c-196">此外，請考慮下列代表象限各種不同位置的列舉：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-196">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="3bb6c-197">下列方法會使用**位置模式**擷取 `x` 及 `y` 的值。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-197">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="3bb6c-198">接著，它使用 `when` 子句判斷點的 `Quadrant`：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-198">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="3bb6c-199">當 `x` 或 `y` 為 0 (非兩者) 時，上述 switch 中的捨棄模式就會符合。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-199">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="3bb6c-200">switch 運算式必須產生值或者擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-200">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="3bb6c-201">若沒有任何案例符合，則 switch 運算式會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-201">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="3bb6c-202">若您未在 switch 運算式中涵蓋所有可能的案例，則編譯器會對您產生警告。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-202">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="3bb6c-203">您可以在此[模式比對進階教學課程](../tutorials/pattern-matching.md)中探索模式比對技巧。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-203">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="3bb6c-204">using 宣告</span><span class="sxs-lookup"><span data-stu-id="3bb6c-204">using declarations</span></span>

<span data-ttu-id="3bb6c-205">**using 宣告**為以 `using` 關鍵字開頭的變數宣告。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-205">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="3bb6c-206">其會告知編譯器，應在括住的範圍結尾處置所宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-206">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="3bb6c-207">例如，試想下列寫入文字檔的程式碼：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-207">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="3bb6c-208">在上述範例中，到達方法的右大括號時，就會處置檔案。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-208">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="3bb6c-209">這是宣告 `file` 之範圍的結尾。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-209">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="3bb6c-210">上述程式碼相當於使用傳統 [using 陳述式](../language-reference/keywords/using-statement.md)的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-210">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="3bb6c-211">在上述範例中，到達與 `using` 陳述式相關的結尾右大括號時，就會處置檔案。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-211">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="3bb6c-212">在這兩個案例中，編譯器皆會產生對 `Dispose()` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-212">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="3bb6c-213">若無法處置 `using` 陳述式中的運算式，編譯器會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-213">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="3bb6c-214">靜態區域函式</span><span class="sxs-lookup"><span data-stu-id="3bb6c-214">Static local functions</span></span>

<span data-ttu-id="3bb6c-215">您現可將 `static` 修飾詞新增至區域函式，以確保區域函式不會從括住的範圍擷取 (參考) 任何變數。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-215">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="3bb6c-216">這樣會產生 `CS8421`「靜態區域函式不可包含對 \<變數> 的參考」。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-216">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="3bb6c-217">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-217">Consider the following code.</span></span> <span data-ttu-id="3bb6c-218">區域函式 `LocalFunction` 會存取在所括住範圍 (方法 `M`) 中宣告的變數 `y`。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-218">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="3bb6c-219">因此，無法使用 `static` 修飾詞宣告 `LocalFunction`：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-219">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="3bb6c-220">下列程式碼包含靜態區域函式。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-220">The following code contains a static local function.</span></span> <span data-ttu-id="3bb6c-221">因為其不會存取所括住範圍中的任何變數，所以可以為靜態：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-221">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="3bb6c-222">可處置的 ref struct</span><span class="sxs-lookup"><span data-stu-id="3bb6c-222">Disposable ref structs</span></span>

<span data-ttu-id="3bb6c-223">使用 `ref` 修飾詞宣告的 `struct` 不會實作任何介面，故無法實作 <xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-223">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="3bb6c-224">因此，若要讓 `ref struct` 可處置，其必須具有可存取的 `void Dispose()` 方法。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-224">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="3bb6c-225">這也適用於 `readonly ref struct` 宣告。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-225">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="3bb6c-226">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="3bb6c-226">Nullable reference types</span></span>

<span data-ttu-id="3bb6c-227">在可為 Null 的註解內容中，參考型別的任何變數皆視為**不可為 Null 的參考型別**。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-227">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="3bb6c-228">若您要表示變數可能為 Null，則必須使用 `?` 來附加類型名稱，以將變數宣告為**可為 Null 的參考型別**。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-228">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="3bb6c-229">對於不可為 Null 的參考型別，編譯器會使用流程分析來確保將區域變數在宣告時，初始化為非 Null 的值。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-229">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="3bb6c-230">必須在建構期間將欄位初始化。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-230">Fields must be initialized during construction.</span></span> <span data-ttu-id="3bb6c-231">若變數不是由對任何可用建構函式的呼叫，或是初始設定式所設定，則編譯器會產生警告。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-231">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="3bb6c-232">此外，也不能對不可為 Null 的參考型別指派可為 Null 的值。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-232">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="3bb6c-233">系統不會檢查可為 Null 的參考型別，來確保其不會指派或初始化為 Null。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-233">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="3bb6c-234">不過，編譯器會在將變數存取或指派至不可為 Null 的參考型別之前，使用流程分析來確保已對可為 Null 參考型別的所有變數檢查可 Null 性。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-234">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="3bb6c-235">您可在[可為 Null 的參考型別](../nullable-references.md)概觀中深入了解功能。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-235">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="3bb6c-236">在此[可為 Null 的參考型別教學課程](../tutorials/nullable-reference-types.md)中，親自在新的應用程式內試用。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-236">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="3bb6c-237">在[移轉應用程式以使用可為 Null 的參考型別教學課程](../tutorials/upgrade-to-nullable-references.md)中，了解移轉現有程式碼基底的步驟，進而利用可為 Null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-237">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="3bb6c-238">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="3bb6c-238">Asynchronous streams</span></span>

<span data-ttu-id="3bb6c-239">自 C# 8.0 起，您可非同步地建立及取用資料流。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-239">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="3bb6c-240">傳回非同步資料流的方法具有三個屬性：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-240">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="3bb6c-241">使用 `async` 修飾詞來宣告。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-241">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="3bb6c-242">其會傳回 <xref:System.Collections.Generic.IAsyncEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-242">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="3bb6c-243">方法會包含 `yield return` 陳述式以傳回非同步資料流中的後續元素。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-243">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="3bb6c-244">當您列舉資料流的元素時，必須在 `foreach` 關鍵字前新增 `await` 關鍵字，才可取用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-244">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="3bb6c-245">需要方法才可新增 `await` 關鍵字，而且該方法列舉要使用 `async` 修飾詞宣告的非同步資料流，並傳回 `async` 方法允許的類型。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-245">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="3bb6c-246">通常這代表傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-246">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="3bb6c-247">也可以是 <xref:System.Threading.Tasks.ValueTask> 或 <xref:System.Threading.Tasks.ValueTask%601>。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-247">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="3bb6c-248">方法可同時取用及產生非同步資料流，這代表其會傳回 <xref:System.Collections.Generic.IAsyncEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-248">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="3bb6c-249">下列程式碼會產生 0 到 19 的序列，產生每個號碼需等待 100 毫秒的間隔：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-249">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="3bb6c-250">您應使用 `await foreach` 陳述式列舉序列：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-250">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="3bb6c-251">您可在我們有關[建立及取用非同步資料流](../tutorials/generate-consume-asynchronous-stream.md)的教學課程中，親自試用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-251">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="3bb6c-252">索引和範圍</span><span class="sxs-lookup"><span data-stu-id="3bb6c-252">Indices and ranges</span></span>

<span data-ttu-id="3bb6c-253">範圍及索引可提供用來指定陣列中子範圍的簡潔語法，<xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601>。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-253">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="3bb6c-254">此語言支援依賴兩個新的類型和兩個新的運算子:</span><span class="sxs-lookup"><span data-stu-id="3bb6c-254">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="3bb6c-255"><xref:System.Index?displayProperty=nameWithType> 代表序列的索引。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-255"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="3bb6c-256">`^` 運算子，它會指定索引相對於序列結尾。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-256">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="3bb6c-257"><xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-257"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="3bb6c-258">Range 運算子 (`..`)，它會指定範圍的開頭與結尾作為其運算子。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-258">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="3bb6c-259">讓我們從索引的規則開始。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-259">Let's start with the rules for indexes.</span></span> <span data-ttu-id="3bb6c-260">假設有一個陣列 `sequence`。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-260">Consider an array `sequence`.</span></span> <span data-ttu-id="3bb6c-261">`0` 索引與 `sequence[0]` 相同。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-261">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="3bb6c-262">`^0` 索引與 `sequence[sequence.Length]` 相同。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-262">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="3bb6c-263">請注意，`sequence[^0]` 會擲回例外狀況，就樣 `sequence[sequence.Length]` 會這樣做一樣。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-263">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="3bb6c-264">針對任何數字 `n`，索引 `^n` 與 `sequence.Length - n` 相同。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-264">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="3bb6c-265">指定範圍「開頭」與「結尾」的範圍。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-265">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="3bb6c-266">範圍的開頭會包含在內，但範圍的結尾是獨佔的，這表示開始包含在範圍內，但結束不包含在範圍內。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-266">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="3bb6c-267">範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-267">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="3bb6c-268">讓我們來看以下幾個範例。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-268">Let's look at a few examples.</span></span> <span data-ttu-id="3bb6c-269">試想下列使用其索引從開頭或從結尾標註的陣列：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-269">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="3bb6c-270">您可使用 `^1` 索引擷取最後一個字組：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-270">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="3bb6c-271">下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-271">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="3bb6c-272">其會包含 `words[1]` 到 `words[3]`。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-272">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="3bb6c-273">元素 `words[4]` 則不在範圍內。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-273">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="3bb6c-274">下列程式碼會建立具有 "lazy" 和 "dog" 的子範圍。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-274">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="3bb6c-275">其包含 `words[^2]` 及 `words[^1]`。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-275">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="3bb6c-276">不包含結束索引 `words[^0]`：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-276">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="3bb6c-277">下列範例會建立不限定開始、結束或兩者的範圍：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-277">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="3bb6c-278">您也可將範圍宣告為變數：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-278">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="3bb6c-279">接著範圍可用於 `[` 及 `]` 字元中：</span><span class="sxs-lookup"><span data-stu-id="3bb6c-279">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="3bb6c-280">您可以在[索引及範圍](../tutorials/ranges-indexes.md)上的教學課程中探索更多關於索引及範圍的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-280">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="3bb6c-281">增強內插逐字字串</span><span class="sxs-lookup"><span data-stu-id="3bb6c-281">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="3bb6c-282">內`$` `@` [插](../language-reference/tokens/interpolated.md)逐字字串`@$"..."`中的和 token 順序可以是 any:和都是有效的內插逐字字串。`$@"..."`</span><span class="sxs-lookup"><span data-stu-id="3bb6c-282">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="3bb6c-283">在較C#舊的版本`$`中, 權杖`@`必須出現在標記之前。</span><span class="sxs-lookup"><span data-stu-id="3bb6c-283">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
