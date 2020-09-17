---
title: 使用索引和範圍探索資料範圍
description: 這個 advanced 教學課程會教您如何使用索引和範圍探索資料，以檢查連續的連續資料集範圍。
ms.date: 09/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: cf6c83484332ed517b2326b3fd9d7458f191227e
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738862"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="e3dad-103">索引和範圍</span><span class="sxs-lookup"><span data-stu-id="e3dad-103">Indices and ranges</span></span>

<span data-ttu-id="e3dad-104">範圍和索引提供簡潔的語法，以存取順序中的單一元素或範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="e3dad-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="e3dad-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e3dad-106">使用序列中範圍的語法。</span><span class="sxs-lookup"><span data-stu-id="e3dad-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="e3dad-107">了解每個序列開始和結束的設計決策。</span><span class="sxs-lookup"><span data-stu-id="e3dad-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="e3dad-108">了解 <xref:System.Index> 和 <xref:System.Range> 類型的案例。</span><span class="sxs-lookup"><span data-stu-id="e3dad-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="e3dad-109">索引和範圍的語言支援</span><span class="sxs-lookup"><span data-stu-id="e3dad-109">Language support for indices and ranges</span></span>

<span data-ttu-id="e3dad-110">此語言支援依賴兩種新的類型和兩個新的運算子：</span><span class="sxs-lookup"><span data-stu-id="e3dad-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="e3dad-111"><xref:System.Index?displayProperty=nameWithType> 代表序列的索引。</span><span class="sxs-lookup"><span data-stu-id="e3dad-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="e3dad-112">End 運算子的索引 `^` ，指定索引相對於序列結尾。</span><span class="sxs-lookup"><span data-stu-id="e3dad-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="e3dad-113"><xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="e3dad-114">範圍運算子 `..` ，指定範圍的開頭和結尾做為其運算元。</span><span class="sxs-lookup"><span data-stu-id="e3dad-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="e3dad-115">讓我們從索引的規則開始。</span><span class="sxs-lookup"><span data-stu-id="e3dad-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="e3dad-116">假設有一個陣列 `sequence`。</span><span class="sxs-lookup"><span data-stu-id="e3dad-116">Consider an array `sequence`.</span></span> <span data-ttu-id="e3dad-117">`0` 索引與 `sequence[0]` 相同。</span><span class="sxs-lookup"><span data-stu-id="e3dad-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="e3dad-118">`^0` 索引與 `sequence[sequence.Length]` 相同。</span><span class="sxs-lookup"><span data-stu-id="e3dad-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="e3dad-119">運算式 `sequence[^0]` 會擲回例外狀況，就像這樣 `sequence[sequence.Length]` 。</span><span class="sxs-lookup"><span data-stu-id="e3dad-119">The expression `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="e3dad-120">針對任何數字 `n`，索引 `^n` 與 `sequence[sequence.Length - n]` 相同。</span><span class="sxs-lookup"><span data-stu-id="e3dad-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="e3dad-121">您可以使用 `^1` 索引擷取最後一個字。</span><span class="sxs-lookup"><span data-stu-id="e3dad-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="e3dad-122">將下列程式碼新增於初始設定下方：</span><span class="sxs-lookup"><span data-stu-id="e3dad-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="e3dad-123">指定範圍「開頭」\*\* 與「結尾」\*\* 的範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="e3dad-124">範圍是專屬的，這表示範圍中不包含 *結尾* 。</span><span class="sxs-lookup"><span data-stu-id="e3dad-124">Ranges are exclusive, meaning the *end* isn't included in the range.</span></span> <span data-ttu-id="e3dad-125">範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。</span><span class="sxs-lookup"><span data-stu-id="e3dad-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="e3dad-126">下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="e3dad-127">其會包含 `words[1]` 到 `words[3]`。</span><span class="sxs-lookup"><span data-stu-id="e3dad-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="e3dad-128">項目 `words[4]` 不在範圍內。</span><span class="sxs-lookup"><span data-stu-id="e3dad-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="e3dad-129">將下列程式碼新增至相同的方法。</span><span class="sxs-lookup"><span data-stu-id="e3dad-129">Add the following code to the same method.</span></span> <span data-ttu-id="e3dad-130">複製並貼在互動式視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="e3dad-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="e3dad-131">下列程式碼會傳回具有 "lazy" 和 "dog" 的範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-131">The following code returns the range with "lazy" and "dog".</span></span> <span data-ttu-id="e3dad-132">其包含 `words[^2]` 及 `words[^1]`。</span><span class="sxs-lookup"><span data-stu-id="e3dad-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="e3dad-133">未包含結尾索引 `words[^0]`。</span><span class="sxs-lookup"><span data-stu-id="e3dad-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="e3dad-134">同時新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e3dad-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="e3dad-135">下列範例會建立不限定開始、結束或兩者的範圍：</span><span class="sxs-lookup"><span data-stu-id="e3dad-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="e3dad-136">您也可以將範圍或索引宣告為變數。</span><span class="sxs-lookup"><span data-stu-id="e3dad-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="e3dad-137">然後即可在 `[` 和 `]` 字元內使用變數：</span><span class="sxs-lookup"><span data-stu-id="e3dad-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="e3dad-138">下列範例顯示這些選擇的許多原因。</span><span class="sxs-lookup"><span data-stu-id="e3dad-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="e3dad-139">修改 `x`、`y` 和 `z` 以嘗試不同的組合。</span><span class="sxs-lookup"><span data-stu-id="e3dad-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="e3dad-140">在您實驗時，請使用 `x` 小於 `y`，且 `y` 小於 `z` 的有效組合值。</span><span class="sxs-lookup"><span data-stu-id="e3dad-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="e3dad-141">在新方法中新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e3dad-141">Add the following code in a new method.</span></span> <span data-ttu-id="e3dad-142">嘗試不同的組合：</span><span class="sxs-lookup"><span data-stu-id="e3dad-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="e3dad-143">索引和範圍的類型支援</span><span class="sxs-lookup"><span data-stu-id="e3dad-143">Type support for indices and ranges</span></span>

<span data-ttu-id="e3dad-144">索引和範圍提供清楚且簡潔的語法，以存取單一專案或序列中的某個範圍的元素。</span><span class="sxs-lookup"><span data-stu-id="e3dad-144">Indexes and ranges provide clear, concise syntax to access a single element or a range of elements in a sequence.</span></span> <span data-ttu-id="e3dad-145">索引運算式通常會傳回序列中元素的類型。</span><span class="sxs-lookup"><span data-stu-id="e3dad-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="e3dad-146">範圍運算式通常會傳回與來源序列相同的序列類型。</span><span class="sxs-lookup"><span data-stu-id="e3dad-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="e3dad-147">使用或參數提供 [索引子](../programming-guide/indexers/index.md) 的任何類型， <xref:System.Index> <xref:System.Range> 分別明確支援索引或範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-147">Any type that provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="e3dad-148">採用單一參數的索引子 <xref:System.Range> 可能會傳回不同的序列類型，例如 <xref:System.Span%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e3dad-148">An indexer that takes a single <xref:System.Range> parameter may return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3dad-149">使用範圍運算子的程式碼效能取決於序列運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="e3dad-149">The performance of code using the range operator depends on the type of the sequence operand.</span></span>
>
> <span data-ttu-id="e3dad-150">範圍運算子的時間複雜性取決於順序類型。</span><span class="sxs-lookup"><span data-stu-id="e3dad-150">The time complexity of the range operator depends on the sequence type.</span></span> <span data-ttu-id="e3dad-151">例如，如果序列是 `string` 或陣列，則結果會是輸入之指定區段的複本，因此，時間複雜度為 \*O (N) \* (其中 N 是) 範圍的長度。</span><span class="sxs-lookup"><span data-stu-id="e3dad-151">For example, if the sequence is a `string` or an array, then the result is a copy of the specified section of the input, so the time complexity is *O(N)* (where N is the length of the range).</span></span> <span data-ttu-id="e3dad-152">另一方面，如果是 <xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.Memory%601?displayProperty=nameWithType> ，則結果會參考相同的備份存放區，這表示沒有任何複本，而且作業是 \* (1) \*。</span><span class="sxs-lookup"><span data-stu-id="e3dad-152">On the other hand, if it's a <xref:System.Span%601?displayProperty=nameWithType> or a <xref:System.Memory%601?displayProperty=nameWithType>, the result references the same backing store, which means there is no copy and the operation is *O(1)*.</span></span>
>
> <span data-ttu-id="e3dad-153">除了時間複雜度，這會造成額外的配置和複本，進而影響效能。</span><span class="sxs-lookup"><span data-stu-id="e3dad-153">In addition to the time complexity, this causes extra allocations and copies, impacting performance.</span></span> <span data-ttu-id="e3dad-154">在效能敏感的程式碼中，請考慮使用 `Span<T>` 或 `Memory<T>` 做為序列類型，因為範圍運算子不會配置它們。</span><span class="sxs-lookup"><span data-stu-id="e3dad-154">In performance sensitive code, consider using `Span<T>` or `Memory<T>` as the sequence type, since the range operator does not allocate for them.</span></span>

<span data-ttu-id="e3dad-155">如果類型具有**countable**名為的屬性， `Length` 或是 `Count` 具有可存取 getter 和傳回類型的，則會計算類型 `int` 。</span><span class="sxs-lookup"><span data-stu-id="e3dad-155">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="e3dad-156">未明確支援索引或範圍的計算類型可能會為其提供隱含支援。</span><span class="sxs-lookup"><span data-stu-id="e3dad-156">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="e3dad-157">如需詳細資訊，請參閱[功能提案附注](~/_csharplang/proposals/csharp-8.0/ranges.md)的[隱含索引支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support)和[隱含範圍支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support)區段。</span><span class="sxs-lookup"><span data-stu-id="e3dad-157">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="e3dad-158">使用隱含範圍支援的範圍會傳回與來源序列相同的序列類型。</span><span class="sxs-lookup"><span data-stu-id="e3dad-158">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="e3dad-159">例如，下列 .NET 類型支援索引和範圍： <xref:System.String> 、 <xref:System.Span%601> 和 <xref:System.ReadOnlySpan%601> 。</span><span class="sxs-lookup"><span data-stu-id="e3dad-159">For example, the following .NET types support both indices and ranges: <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="e3dad-160"><xref:System.Collections.Generic.List%601>支援索引，但不支援範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-160">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

<span data-ttu-id="e3dad-161"><xref:System.Array> 具有更差別細微的行為。</span><span class="sxs-lookup"><span data-stu-id="e3dad-161"><xref:System.Array> has more nuanced behavior.</span></span> <span data-ttu-id="e3dad-162">單一維度陣列支援索引和範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-162">Single dimension arrays support both indices and ranges.</span></span> <span data-ttu-id="e3dad-163">多維度陣列不是。</span><span class="sxs-lookup"><span data-stu-id="e3dad-163">Multi-dimensional arrays don't.</span></span> <span data-ttu-id="e3dad-164">多維度陣列的索引子有多個參數，而不是單一參數。</span><span class="sxs-lookup"><span data-stu-id="e3dad-164">The indexer for a multi-dimensional array has multiple parameters, not a single parameter.</span></span> <span data-ttu-id="e3dad-165">不規則陣列（也稱為陣列陣列）支援範圍和索引子。</span><span class="sxs-lookup"><span data-stu-id="e3dad-165">Jagged arrays, also referred to as an array of arrays, support both ranges and indexers.</span></span> <span data-ttu-id="e3dad-166">下列範例顯示如何逐一查看不規則陣列的矩形子區段。</span><span class="sxs-lookup"><span data-stu-id="e3dad-166">The following example shows how to iterate a rectangular subsection of a jagged array.</span></span> <span data-ttu-id="e3dad-167">它會逐一查看中間的區段，包括第一個和最後三個數據列，以及每個所選資料列的第一個和最後兩個數據行：</span><span class="sxs-lookup"><span data-stu-id="e3dad-167">It iterates the section in the center, excluding the first and last three rows, and the first and last two columns from each selected row:</span></span>

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

<span data-ttu-id="e3dad-168">在所有情況下，的範圍運算子都會配置 <xref:System.Array> 陣列來儲存傳回的元素。</span><span class="sxs-lookup"><span data-stu-id="e3dad-168">In all cases, the range operator for <xref:System.Array> allocates an array to store the elements returned.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="e3dad-169">索引和範圍的案例</span><span class="sxs-lookup"><span data-stu-id="e3dad-169">Scenarios for indices and ranges</span></span>

<span data-ttu-id="e3dad-170">當您想要分析較大順序的一部分時，您通常會使用範圍和索引。</span><span class="sxs-lookup"><span data-stu-id="e3dad-170">You'll often use ranges and indices when you want to analyze a portion of a larger sequence.</span></span> <span data-ttu-id="e3dad-171">新的語法更清楚地閱讀了序列中的哪個部分。</span><span class="sxs-lookup"><span data-stu-id="e3dad-171">The new syntax is clearer in reading exactly what portion of the sequence is involved.</span></span> <span data-ttu-id="e3dad-172">區域函式 `MovingAverage` 採用 <xref:System.Range> 作為其引數。</span><span class="sxs-lookup"><span data-stu-id="e3dad-172">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="e3dad-173">然後，方法在計算最小值、最大值和平均值時，僅會列舉該範圍。</span><span class="sxs-lookup"><span data-stu-id="e3dad-173">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="e3dad-174">請在您的專案中嘗試下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e3dad-174">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
