---
title: 使用索引和範圍探索資料範圍
description: 此進階教學課程將教導您使用索引和範圍探索資料，以檢查連續資料集的配量。
ms.date: 09/20/2019
ms.custom: mvc
ms.openlocfilehash: a879601e1358f72e80983992a3cd96ba1fb06a38
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71391963"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="1a998-103">索引和範圍</span><span class="sxs-lookup"><span data-stu-id="1a998-103">Indices and ranges</span></span>

<span data-ttu-id="1a998-104">範圍和索引提供簡潔的語法，可用於存取序列中的單一專案或範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="1a998-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="1a998-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1a998-106">使用序列中範圍的語法。</span><span class="sxs-lookup"><span data-stu-id="1a998-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="1a998-107">了解每個序列開始和結束的設計決策。</span><span class="sxs-lookup"><span data-stu-id="1a998-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="1a998-108">了解 <xref:System.Index> 和 <xref:System.Range> 類型的案例。</span><span class="sxs-lookup"><span data-stu-id="1a998-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="1a998-109">索引和範圍的語言支援</span><span class="sxs-lookup"><span data-stu-id="1a998-109">Language support for indices and ranges</span></span>

<span data-ttu-id="1a998-110">此語言支援依賴兩個新的類型和兩個新的運算子：</span><span class="sxs-lookup"><span data-stu-id="1a998-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="1a998-111"><xref:System.Index?displayProperty=nameWithType> 代表序列的索引。</span><span class="sxs-lookup"><span data-stu-id="1a998-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="1a998-112">End 運算子`^`的索引，指定索引相對於序列結尾。</span><span class="sxs-lookup"><span data-stu-id="1a998-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="1a998-113"><xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="1a998-114">範圍運算子`..`，指定範圍的開始和結束作為其運算元。</span><span class="sxs-lookup"><span data-stu-id="1a998-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="1a998-115">讓我們從索引的規則開始。</span><span class="sxs-lookup"><span data-stu-id="1a998-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="1a998-116">假設有一個陣列 `sequence`。</span><span class="sxs-lookup"><span data-stu-id="1a998-116">Consider an array `sequence`.</span></span> <span data-ttu-id="1a998-117">`0` 索引與 `sequence[0]` 相同。</span><span class="sxs-lookup"><span data-stu-id="1a998-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="1a998-118">`^0` 索引與 `sequence[sequence.Length]` 相同。</span><span class="sxs-lookup"><span data-stu-id="1a998-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="1a998-119">請注意，`sequence[^0]` 會擲回例外狀況，就樣 `sequence[sequence.Length]` 會這樣做一樣。</span><span class="sxs-lookup"><span data-stu-id="1a998-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="1a998-120">針對任何數字 `n`，索引 `^n` 與 `sequence[sequence.Length - n]` 相同。</span><span class="sxs-lookup"><span data-stu-id="1a998-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp-interactive
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

<span data-ttu-id="1a998-121">您可以使用 `^1` 索引擷取最後一個字。</span><span class="sxs-lookup"><span data-stu-id="1a998-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="1a998-122">將下列程式碼新增於初始設定下方：</span><span class="sxs-lookup"><span data-stu-id="1a998-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="1a998-123">指定範圍「開頭」與「結尾」的範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="1a998-124">範圍具有排除性，這表示「結尾」不包含在範圍內。</span><span class="sxs-lookup"><span data-stu-id="1a998-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="1a998-125">範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。</span><span class="sxs-lookup"><span data-stu-id="1a998-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="1a998-126">下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="1a998-127">其會包含 `words[1]` 到 `words[3]`。</span><span class="sxs-lookup"><span data-stu-id="1a998-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="1a998-128">項目 `words[4]` 不在範圍內。</span><span class="sxs-lookup"><span data-stu-id="1a998-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="1a998-129">將下列程式碼新增至相同的方法。</span><span class="sxs-lookup"><span data-stu-id="1a998-129">Add the following code to the same method.</span></span> <span data-ttu-id="1a998-130">複製並貼在互動式視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="1a998-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="1a998-131">下列程式碼會建立具有 "lazy" 和 "dog" 的子範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="1a998-132">其包含 `words[^2]` 及 `words[^1]`。</span><span class="sxs-lookup"><span data-stu-id="1a998-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="1a998-133">未包含結尾索引 `words[^0]`。</span><span class="sxs-lookup"><span data-stu-id="1a998-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="1a998-134">同時新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="1a998-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="1a998-135">下列範例會建立不限定開始、結束或兩者的範圍：</span><span class="sxs-lookup"><span data-stu-id="1a998-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="1a998-136">您也可以將範圍或索引宣告為變數。</span><span class="sxs-lookup"><span data-stu-id="1a998-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="1a998-137">然後即可在 `[` 和 `]` 字元內使用變數：</span><span class="sxs-lookup"><span data-stu-id="1a998-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="1a998-138">下列範例顯示這些選擇的許多原因。</span><span class="sxs-lookup"><span data-stu-id="1a998-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="1a998-139">修改 `x`、`y` 和 `z` 以嘗試不同的組合。</span><span class="sxs-lookup"><span data-stu-id="1a998-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="1a998-140">在您實驗時，請使用 `x` 小於 `y`，且 `y` 小於 `z` 的有效組合值。</span><span class="sxs-lookup"><span data-stu-id="1a998-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="1a998-141">在新方法中新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a998-141">Add the following code in a new method.</span></span> <span data-ttu-id="1a998-142">嘗試不同的組合：</span><span class="sxs-lookup"><span data-stu-id="1a998-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="1a998-143">索引和範圍的類型支援</span><span class="sxs-lookup"><span data-stu-id="1a998-143">Type support for indices and ranges</span></span>

<span data-ttu-id="1a998-144">如果型別提供具有 <xref:System.Index> 或 <xref:System.Range> 參數的[索引子](../programming-guide/indexers/index.md)，則會分別明確支援索引或範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-144">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span>

<span data-ttu-id="1a998-145">如果類型具有名為 `Length` 的屬性，或具有可存取 getter 的 `Count`，且傳回型別為 `int`，則型別為**計算**。</span><span class="sxs-lookup"><span data-stu-id="1a998-145">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="1a998-146">未明確支援索引或範圍的計算類型可能會為其提供隱含支援。</span><span class="sxs-lookup"><span data-stu-id="1a998-146">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="1a998-147">如需詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-8.0/ranges.md)的[隱含索引支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support)和[隱含範圍支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support)章節。</span><span class="sxs-lookup"><span data-stu-id="1a998-147">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

<span data-ttu-id="1a998-148">例如，下列 .NET 類型支援索引和範圍： <xref:System.Array>、<xref:System.String>、<xref:System.Span%601> 和 <xref:System.ReadOnlySpan%601>。</span><span class="sxs-lookup"><span data-stu-id="1a998-148">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="1a998-149">@No__t-0 支援索引，但不支援範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-149">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="1a998-150">索引和範圍的案例</span><span class="sxs-lookup"><span data-stu-id="1a998-150">Scenarios for indices and ranges</span></span>

<span data-ttu-id="1a998-151">當您希望對整個序列的子範圍執行某些分析時，您會經常使用範圍和索引。</span><span class="sxs-lookup"><span data-stu-id="1a998-151">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="1a998-152">在準確讀取牽涉的子範圍時，新語法較清晰。</span><span class="sxs-lookup"><span data-stu-id="1a998-152">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="1a998-153">區域函式 `MovingAverage` 採用 <xref:System.Range> 作為其引數。</span><span class="sxs-lookup"><span data-stu-id="1a998-153">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="1a998-154">然後，方法在計算最小值、最大值和平均值時，僅會列舉該範圍。</span><span class="sxs-lookup"><span data-stu-id="1a998-154">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="1a998-155">請在您的專案中嘗試下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="1a998-155">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="1a998-156">您可以從 [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) 存放庫下載完整的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a998-156">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
