---
title: 使用索引和範圍探索資料範圍
description: 此進階教學課程將教導您使用索引和範圍探索資料，以檢查連續資料集的配量。
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156490"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="a1350-103">索引和範圍</span><span class="sxs-lookup"><span data-stu-id="a1350-103">Indices and ranges</span></span>

<span data-ttu-id="a1350-104">範圍和索引提供了簡潔的語法，用於按循序存取單個元素或範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="a1350-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="a1350-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a1350-106">使用序列中範圍的語法。</span><span class="sxs-lookup"><span data-stu-id="a1350-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="a1350-107">了解每個序列開始和結束的設計決策。</span><span class="sxs-lookup"><span data-stu-id="a1350-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="a1350-108">了解 <xref:System.Index> 和 <xref:System.Range> 類型的案例。</span><span class="sxs-lookup"><span data-stu-id="a1350-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="a1350-109">索引和範圍的語言支援</span><span class="sxs-lookup"><span data-stu-id="a1350-109">Language support for indices and ranges</span></span>

<span data-ttu-id="a1350-110">此語言支援依賴于兩種新類型和兩個新運算子：</span><span class="sxs-lookup"><span data-stu-id="a1350-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="a1350-111"><xref:System.Index?displayProperty=nameWithType> 代表序列的索引。</span><span class="sxs-lookup"><span data-stu-id="a1350-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="a1350-112">來自結束運算子`^`的索引 ，它指定索引相對於序列的末尾。</span><span class="sxs-lookup"><span data-stu-id="a1350-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="a1350-113"><xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="a1350-114">範圍運算子`..`， 指定範圍的開始和結束作為其運算元。</span><span class="sxs-lookup"><span data-stu-id="a1350-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="a1350-115">讓我們從索引的規則開始。</span><span class="sxs-lookup"><span data-stu-id="a1350-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="a1350-116">假設有一個陣列 `sequence`。</span><span class="sxs-lookup"><span data-stu-id="a1350-116">Consider an array `sequence`.</span></span> <span data-ttu-id="a1350-117">`0` 索引與 `sequence[0]` 相同。</span><span class="sxs-lookup"><span data-stu-id="a1350-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="a1350-118">`^0` 索引與 `sequence[sequence.Length]` 相同。</span><span class="sxs-lookup"><span data-stu-id="a1350-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="a1350-119">運算式`sequence[^0]`將引發異常，就像引發異常一樣`sequence[sequence.Length]`。</span><span class="sxs-lookup"><span data-stu-id="a1350-119">The expression `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="a1350-120">針對任何數字 `n`，索引 `^n` 與 `sequence[sequence.Length - n]` 相同。</span><span class="sxs-lookup"><span data-stu-id="a1350-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp
string[] words = new string[]
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

<span data-ttu-id="a1350-121">您可以使用 `^1` 索引擷取最後一個字。</span><span class="sxs-lookup"><span data-stu-id="a1350-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="a1350-122">將下列程式碼新增於初始設定下方：</span><span class="sxs-lookup"><span data-stu-id="a1350-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="a1350-123">指定範圍「開頭」\*\* 與「結尾」\*\* 的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="a1350-124">範圍是獨佔的，這意味著範圍中不包括*結束*。</span><span class="sxs-lookup"><span data-stu-id="a1350-124">Ranges are exclusive, meaning the *end* isn't included in the range.</span></span> <span data-ttu-id="a1350-125">範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。</span><span class="sxs-lookup"><span data-stu-id="a1350-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="a1350-126">下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="a1350-127">其會包含 `words[1]` 到 `words[3]`。</span><span class="sxs-lookup"><span data-stu-id="a1350-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="a1350-128">項目 `words[4]` 不在範圍內。</span><span class="sxs-lookup"><span data-stu-id="a1350-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="a1350-129">將下列程式碼新增至相同的方法。</span><span class="sxs-lookup"><span data-stu-id="a1350-129">Add the following code to the same method.</span></span> <span data-ttu-id="a1350-130">複製並貼在互動式視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="a1350-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="a1350-131">下列程式碼會建立具有 "lazy" 和 "dog" 的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="a1350-132">其包含 `words[^2]` 及 `words[^1]`。</span><span class="sxs-lookup"><span data-stu-id="a1350-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="a1350-133">未包含結尾索引 `words[^0]`。</span><span class="sxs-lookup"><span data-stu-id="a1350-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="a1350-134">同時新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a1350-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="a1350-135">下列範例會建立不限定開始、結束或兩者的範圍：</span><span class="sxs-lookup"><span data-stu-id="a1350-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="a1350-136">您也可以將範圍或索引宣告為變數。</span><span class="sxs-lookup"><span data-stu-id="a1350-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="a1350-137">然後即可在 `[` 和 `]` 字元內使用變數：</span><span class="sxs-lookup"><span data-stu-id="a1350-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="a1350-138">下列範例顯示這些選擇的許多原因。</span><span class="sxs-lookup"><span data-stu-id="a1350-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="a1350-139">修改 `x`、`y` 和 `z` 以嘗試不同的組合。</span><span class="sxs-lookup"><span data-stu-id="a1350-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="a1350-140">在您實驗時，請使用 `x` 小於 `y`，且 `y` 小於 `z` 的有效組合值。</span><span class="sxs-lookup"><span data-stu-id="a1350-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="a1350-141">在新方法中新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="a1350-141">Add the following code in a new method.</span></span> <span data-ttu-id="a1350-142">嘗試不同的組合：</span><span class="sxs-lookup"><span data-stu-id="a1350-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="a1350-143">類型支援索引和範圍</span><span class="sxs-lookup"><span data-stu-id="a1350-143">Type support for indices and ranges</span></span>

<span data-ttu-id="a1350-144">索引和範圍提供清晰、簡潔的語法，用於訪問序列中的單個元素或元素的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-144">Indexes and ranges provide clear, concise syntax to access a single element or a subrange of elements in a sequence.</span></span> <span data-ttu-id="a1350-145">索引運算式通常返回序列元素的類型。</span><span class="sxs-lookup"><span data-stu-id="a1350-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="a1350-146">範圍運算式通常返回與源序列相同的序列類型。</span><span class="sxs-lookup"><span data-stu-id="a1350-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="a1350-147">向[索引子](../programming-guide/indexers/index.md)提供<xref:System.Index>或<xref:System.Range>參數的任何類型的索引子分別顯式支援索引或範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-147">Any type that provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="a1350-148">採用單個<xref:System.Range>參數的索引子可能會返回不同的序列類型，例如<xref:System.Span%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a1350-148">An indexer that takes a single <xref:System.Range> parameter may return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a1350-149">如果類型具有名為`Length`或`Count`具有可訪問 getter 的屬性和 返回類型，**則類型是可計數**的。 `int`</span><span class="sxs-lookup"><span data-stu-id="a1350-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="a1350-150">不顯式支援索引或範圍的可計數類型可能會為索引或範圍提供隱式支援。</span><span class="sxs-lookup"><span data-stu-id="a1350-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="a1350-151">有關詳細資訊，請參閱[功能建議注釋](~/_csharplang/proposals/csharp-8.0/ranges.md)的[隱式索引支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support)和[隱式範圍支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support)部分。</span><span class="sxs-lookup"><span data-stu-id="a1350-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="a1350-152">使用隱式範圍支援的範圍返回與源序列相同的序列類型。</span><span class="sxs-lookup"><span data-stu-id="a1350-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="a1350-153">例如，以下 .NET 類型同時支援索引和範圍： <xref:System.String> <xref:System.Span%601>和<xref:System.ReadOnlySpan%601>。</span><span class="sxs-lookup"><span data-stu-id="a1350-153">For example, the following .NET types support both indices and ranges: <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="a1350-154">支援<xref:System.Collections.Generic.List%601>索引，但不支援範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

<span data-ttu-id="a1350-155"><xref:System.Array>有更多的細微差別的行為。</span><span class="sxs-lookup"><span data-stu-id="a1350-155"><xref:System.Array> has more nuanced behavior.</span></span> <span data-ttu-id="a1350-156">單個維度陣列同時支援索引和範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-156">Single dimension arrays support both indices and ranges.</span></span> <span data-ttu-id="a1350-157">多維陣列沒有。</span><span class="sxs-lookup"><span data-stu-id="a1350-157">Multi-dimensional arrays don't.</span></span> <span data-ttu-id="a1350-158">多維陣列的索引子具有多個參數，而不是單個參數。</span><span class="sxs-lookup"><span data-stu-id="a1350-158">The indexer for a multi-dimensional array has multiple parameters, not a single parameter.</span></span> <span data-ttu-id="a1350-159">鋸齒狀陣列（也稱為陣列陣列）支援範圍和索引子。</span><span class="sxs-lookup"><span data-stu-id="a1350-159">Jagged arrays, also referred to as an array of arrays, support both ranges and indexers.</span></span> <span data-ttu-id="a1350-160">下面的示例演示如何反覆運算鋸齒陣列的矩形子節。</span><span class="sxs-lookup"><span data-stu-id="a1350-160">The following example shows how to iterate a rectangular subsection of a jagged array.</span></span> <span data-ttu-id="a1350-161">它預告中心中的節，不包括第一行和後三行，以及每個選定行中的第一列和後兩列：</span><span class="sxs-lookup"><span data-stu-id="a1350-161">It iterates the section in the center, excluding the first and last three rows, and the first and last two columns from each selected row:</span></span>

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="a1350-162">索引和範圍的方案</span><span class="sxs-lookup"><span data-stu-id="a1350-162">Scenarios for indices and ranges</span></span>

<span data-ttu-id="a1350-163">當您要分析較大序列的子範圍時，您通常會使用範圍和索引。</span><span class="sxs-lookup"><span data-stu-id="a1350-163">You'll often use ranges and indices when you want to analyze a subrange of a larger sequence.</span></span> <span data-ttu-id="a1350-164">在準確讀取牽涉的子範圍時，新語法較清晰。</span><span class="sxs-lookup"><span data-stu-id="a1350-164">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="a1350-165">區域函式 `MovingAverage` 採用 <xref:System.Range> 作為其引數。</span><span class="sxs-lookup"><span data-stu-id="a1350-165">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="a1350-166">然後，方法在計算最小值、最大值和平均值時，僅會列舉該範圍。</span><span class="sxs-lookup"><span data-stu-id="a1350-166">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="a1350-167">請在您的專案中嘗試下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a1350-167">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
