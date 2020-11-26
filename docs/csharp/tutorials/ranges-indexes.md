---
title: 使用索引和範圍探索資料範圍
description: 這個 advanced 教學課程會教您如何使用索引和範圍探索資料，以檢查連續的連續資料集範圍。
ms.date: 09/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: cf6c83484332ed517b2326b3fd9d7458f191227e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "90738862"
---
# <a name="indices-and-ranges"></a>索引和範圍

範圍和索引提供簡潔的語法，以存取順序中的單一元素或範圍。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 使用序列中範圍的語法。
> - 了解每個序列開始和結束的設計決策。
> - 了解 <xref:System.Index> 和 <xref:System.Range> 類型的案例。

## <a name="language-support-for-indices-and-ranges"></a>索引和範圍的語言支援

此語言支援依賴兩種新的類型和兩個新的運算子：

- <xref:System.Index?displayProperty=nameWithType> 代表序列的索引。
- End 運算子的索引 `^` ，指定索引相對於序列結尾。
- <xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。
- 範圍運算子 `..` ，指定範圍的開頭和結尾做為其運算元。

讓我們從索引的規則開始。 假設有一個陣列 `sequence`。 `0` 索引與 `sequence[0]` 相同。 `^0` 索引與 `sequence[sequence.Length]` 相同。 運算式 `sequence[^0]` 會擲回例外狀況，就像這樣 `sequence[sequence.Length]` 。 針對任何數字 `n`，索引 `^n` 與 `sequence[sequence.Length - n]` 相同。

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

指定範圍「開頭」與「結尾」的範圍。 範圍是專屬的，這表示範圍中不包含 *結尾* 。 範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。

下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。 其會包含 `words[1]` 到 `words[3]`。 項目 `words[4]` 不在範圍內。 將下列程式碼新增至相同的方法。 複製並貼在互動式視窗的底部。

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

下列程式碼會傳回具有 "lazy" 和 "dog" 的範圍。 其包含 `words[^2]` 及 `words[^1]`。 未包含結尾索引 `words[^0]`。 同時新增下列程式碼：

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

下列範例會建立不限定開始、結束或兩者的範圍：

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

您也可以將範圍或索引宣告為變數。 然後即可在 `[` 和 `]` 字元內使用變數：

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

下列範例顯示這些選擇的許多原因。 修改 `x`、`y` 和 `z` 以嘗試不同的組合。 在您實驗時，請使用 `x` 小於 `y`，且 `y` 小於 `z` 的有效組合值。 在新方法中新增下列程式碼。 嘗試不同的組合：

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>索引和範圍的類型支援

索引和範圍提供清楚且簡潔的語法，以存取單一專案或序列中的某個範圍的元素。 索引運算式通常會傳回序列中元素的類型。 範圍運算式通常會傳回與來源序列相同的序列類型。

使用或參數提供 [索引子](../programming-guide/indexers/index.md) 的任何類型， <xref:System.Index> <xref:System.Range> 分別明確支援索引或範圍。 採用單一參數的索引子 <xref:System.Range> 可能會傳回不同的序列類型，例如 <xref:System.Span%601?displayProperty=nameWithType> 。

> [!IMPORTANT]
> 使用範圍運算子的程式碼效能取決於序列運算元的類型。
>
> 範圍運算子的時間複雜性取決於順序類型。 例如，如果序列是 `string` 或陣列，則結果會是輸入之指定區段的複本，因此，時間複雜度為 *O (N)* (其中 N 是) 範圍的長度。 另一方面，如果是 <xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.Memory%601?displayProperty=nameWithType> ，則結果會參考相同的備份存放區，這表示沒有任何複本，而且作業是 *(1)*。
>
> 除了時間複雜度，這會造成額外的配置和複本，進而影響效能。 在效能敏感的程式碼中，請考慮使用 `Span<T>` 或 `Memory<T>` 做為序列類型，因為範圍運算子不會配置它們。

如果類型具有 **countable** 名為的屬性， `Length` 或是 `Count` 具有可存取 getter 和傳回類型的，則會計算類型 `int` 。 未明確支援索引或範圍的計算類型可能會為其提供隱含支援。 如需詳細資訊，請參閱[功能提案附注](~/_csharplang/proposals/csharp-8.0/ranges.md)的[隱含索引支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support)和[隱含範圍支援](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support)區段。 使用隱含範圍支援的範圍會傳回與來源序列相同的序列類型。

例如，下列 .NET 類型支援索引和範圍： <xref:System.String> 、 <xref:System.Span%601> 和 <xref:System.ReadOnlySpan%601> 。 <xref:System.Collections.Generic.List%601>支援索引，但不支援範圍。

<xref:System.Array> 具有更差別細微的行為。 單一維度陣列支援索引和範圍。 多維度陣列不是。 多維度陣列的索引子有多個參數，而不是單一參數。 不規則陣列（也稱為陣列陣列）支援範圍和索引子。 下列範例顯示如何逐一查看不規則陣列的矩形子區段。 它會逐一查看中間的區段，包括第一個和最後三個數據列，以及每個所選資料列的第一個和最後兩個數據行：

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

在所有情況下，的範圍運算子都會配置 <xref:System.Array> 陣列來儲存傳回的元素。

## <a name="scenarios-for-indices-and-ranges"></a>索引和範圍的案例

當您想要分析較大順序的一部分時，您通常會使用範圍和索引。 新的語法更清楚地閱讀了序列中的哪個部分。 區域函式 `MovingAverage` 採用 <xref:System.Range> 作為其引數。 然後，方法在計算最小值、最大值和平均值時，僅會列舉該範圍。 請在您的專案中嘗試下列程式碼：

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
