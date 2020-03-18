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
# <a name="indices-and-ranges"></a>索引和範圍

範圍和索引提供了簡潔的語法，用於按循序存取單個元素或範圍。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 使用序列中範圍的語法。
> - 了解每個序列開始和結束的設計決策。
> - 了解 <xref:System.Index> 和 <xref:System.Range> 類型的案例。

## <a name="language-support-for-indices-and-ranges"></a>索引和範圍的語言支援

此語言支援依賴于兩種新類型和兩個新運算子：

- <xref:System.Index?displayProperty=nameWithType> 代表序列的索引。
- 來自結束運算子`^`的索引 ，它指定索引相對於序列的末尾。
- <xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。
- 範圍運算子`..`， 指定範圍的開始和結束作為其運算元。

讓我們從索引的規則開始。 假設有一個陣列 `sequence`。 `0` 索引與 `sequence[0]` 相同。 `^0` 索引與 `sequence[sequence.Length]` 相同。 運算式`sequence[^0]`將引發異常，就像引發異常一樣`sequence[sequence.Length]`。 針對任何數字 `n`，索引 `^n` 與 `sequence[sequence.Length - n]` 相同。

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

您可以使用 `^1` 索引擷取最後一個字。 將下列程式碼新增於初始設定下方：

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

指定範圍「開頭」** 與「結尾」** 的範圍。 範圍是獨佔的，這意味著範圍中不包括*結束*。 範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。

下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。 其會包含 `words[1]` 到 `words[3]`。 項目 `words[4]` 不在範圍內。 將下列程式碼新增至相同的方法。 複製並貼在互動式視窗的底部。

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

下列程式碼會建立具有 "lazy" 和 "dog" 的子範圍。 其包含 `words[^2]` 及 `words[^1]`。 未包含結尾索引 `words[^0]`。 同時新增下列程式碼：

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

下列範例會建立不限定開始、結束或兩者的範圍：

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

您也可以將範圍或索引宣告為變數。 然後即可在 `[` 和 `]` 字元內使用變數：

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

下列範例顯示這些選擇的許多原因。 修改 `x`、`y` 和 `z` 以嘗試不同的組合。 在您實驗時，請使用 `x` 小於 `y`，且 `y` 小於 `z` 的有效組合值。 在新方法中新增下列程式碼。 嘗試不同的組合：

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>類型支援索引和範圍

索引和範圍提供清晰、簡潔的語法，用於訪問序列中的單個元素或元素的子範圍。 索引運算式通常返回序列元素的類型。 範圍運算式通常返回與源序列相同的序列類型。

向[索引子](../programming-guide/indexers/index.md)提供<xref:System.Index>或<xref:System.Range>參數的任何類型的索引子分別顯式支援索引或範圍。 採用單個<xref:System.Range>參數的索引子可能會返回不同的序列類型，例如<xref:System.Span%601?displayProperty=nameWithType>。

如果類型具有名為`Length`或`Count`具有可訪問 getter 的屬性和 返回類型，**則類型是可計數**的。 `int` 不顯式支援索引或範圍的可計數類型可能會為索引或範圍提供隱式支援。 有關詳細資訊，請參閱[功能建議注釋](~/_csharplang/proposals/csharp-8.0/ranges.md)的[隱式索引支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support)和[隱式範圍支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support)部分。 使用隱式範圍支援的範圍返回與源序列相同的序列類型。

例如，以下 .NET 類型同時支援索引和範圍： <xref:System.String> <xref:System.Span%601>和<xref:System.ReadOnlySpan%601>。 支援<xref:System.Collections.Generic.List%601>索引，但不支援範圍。

<xref:System.Array>有更多的細微差別的行為。 單個維度陣列同時支援索引和範圍。 多維陣列沒有。 多維陣列的索引子具有多個參數，而不是單個參數。 鋸齒狀陣列（也稱為陣列陣列）支援範圍和索引子。 下面的示例演示如何反覆運算鋸齒陣列的矩形子節。 它預告中心中的節，不包括第一行和後三行，以及每個選定行中的第一列和後兩列：

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a>索引和範圍的方案

當您要分析較大序列的子範圍時，您通常會使用範圍和索引。 在準確讀取牽涉的子範圍時，新語法較清晰。 區域函式 `MovingAverage` 採用 <xref:System.Range> 作為其引數。 然後，方法在計算最小值、最大值和平均值時，僅會列舉該範圍。 請在您的專案中嘗試下列程式碼：

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
