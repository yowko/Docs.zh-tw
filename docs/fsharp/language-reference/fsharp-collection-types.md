---
title: 集合型別
description: '瞭解 F # 集合類型，以及它們與 .NET 集合類型之間的差異。'
ms.date: 08/14/2020
ms.openlocfilehash: 394f6bbaf58e7e8607abc3a0c20bbc2b1c9c3c8d
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656901"
---
# <a name="f-collection-types"></a>F# 集合類型

藉由查看本主題，您可以判斷哪一個 F # 集合類型最適合特定的需求。 這些集合類型與 .NET 中的集合類型（例如命名空間中的型別不同）不同之處在于， `System.Collections.Generic` F # 集合類型是以功能性程式設計的觀點來設計，而不是以物件導向的觀點來設計。 更具體來說，只有陣列集合具有可變動的元素。 因此，當您修改集合時，會建立已修改之集合的實例，而不是改變原創組合。

集合類型也會隨著儲存物件的資料結構類型而有所不同。 雜湊資料表、連結清單和陣列等資料結構具有不同的效能特性，以及一組不同的可用作業。

## <a name="f-collection-types"></a>F# 集合類型

下表顯示 F # 集合類型。

|類型|描述|相關連結|
|----|-----------|-------------|
|[清單](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharplist-1.html)|相同類型的已排序且不可變的元素系列。 實作為連結清單。|[清單](lists.md)<br /><br />[List 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)|
|[陣列](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-array-1.html)|以零為基底的固定資料元素集合，這些專案全都屬於相同類型。|[陣列](arrays.md)<br /><br />[Array 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)<br /><br />[Array2D 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html)<br /><br />[Array3D 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array3dmodule.html)|
|[序列](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seq-1.html)|全部為一種類型之元素的邏輯序列。 當您有大量的資料收集，但不一定會預期使用所有專案時，序列特別有用。 個別順序元素只會在必要時計算，因此如果未使用所有元素，序列的執行效能會優於清單。 順序是以類型表示 `seq<'T>` ，這是的別名 `IEnumerable<T>` 。 因此，任何執行的 .NET Framework 型別都 `System.Collections.Generic.IEnumerable<'T>` 可以當做序列使用。|[序列](sequences.md)<br /><br />[Seq 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html)|
|[地圖](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharpmap-2.html)|元素的不可變字典。 專案是由索引鍵存取。|[Map 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-mapmodule.html)|
|[設定](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharpset-1.html)|以二進位樹狀結構為基礎的不可變集合，其中的比較是 F # 結構比較函式，其可能會 `System.IComparable` 在索引鍵值上使用介面的實值。|[設定模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-setmodule.html)|

### <a name="table-of-functions"></a>函數的資料表

本節將比較 F # 集合類型上可用的函式。 會提供函數的計算複雜度，其中 N 是第一個集合的大小，而 M 是第二個集合的大小（如果有的話）。 虛線 (-) 表示此函式無法在集合上使用。 因為序列會延遲評估，所以 Seq. distinct 之類的函式可能是 O (1) 因為它會立即傳回，但它仍會在列舉時影響序列的效能。

|函式|Array|清單|順序|對應|設定|描述|
|--------|-----|----|--------|---|---|-----------|
|附加|O (N) |O (N) |O (N) |-|-|傳回新的集合，其中包含第一個集合的元素，後面接著第二個集合的元素。|
|add|-|-|-|O (記錄 (N) # A3|O (記錄 (N) # A3|傳回已加入專案的新集合。|
|average|O (N) |O (N) |O (N) |-|-|傳回集合中元素的平均值。|
|averageBy|O (N) |O (N) |O (N) |-|-|傳回已套用至每個元素之所提供函式的結果平均值。|
|array.blit|O (N) |-|-|-|-|複製陣列的區段。|
|快取|-|-|O (N) |-|-|計算和儲存序列的元素。|
|cast|-|-|O (N) |-|-|將元素轉換成指定的類型。|
|choose|O (N) |O (N) |O (N) |-|-|將指定的函式套用 `f` 至清單的每個元素 `x` 。 傳回清單，其中包含函式傳回之每個元素的結果 `Some(f(x))` 。|
|收集|O (N) |O (N) |O (N) |-|-|將指定的函式套用至集合中的每個元素、串連所有結果，並傳回合並的清單。|
|Seq.comparewith|-|-|O (N) |-|-|使用指定的比較函式、element by 專案來比較兩個序列。|
|concat|O (N) |O (N) |O (N) |-|-|將指定列舉列舉型別合併為單一串連列舉。|
|包含|-|-|-|-|O (記錄 (N) # A3|如果集合包含指定的元素，則傳回 true。|
|containsKey|-|-|-|O (記錄 (N) # A3|-|測試專案是否在對應的定義域中。|
|count|-|-|-|-|O (N) |傳回集合中項目的數目。|
|Seq.countby|-|-|O (N) |-|-|將索引鍵產生函式套用至序列的每個專案，並傳回會產生唯一索引鍵的序列，以及其在原始序列中的發生次數。|
|copy|O (N) |-|O (N) |-|-|複製集合。|
|建立|O (N) |-|-|-|-|建立整個專案的陣列，這些元素最初都是指定的值。|
|delay|-|-|O (1) |-|-|傳回從指定之序列的延遲規格建立的序列。|
|差異|-|-|-|-|O (M \* log (N) # A3|傳回新的集合，其中包含從第一個集合中移除之第二個集合的元素。|
|distinct|||O (1) \*|||根據專案的泛型雜湊和相等比較，傳回不含重複專案的序列。 如果專案在順序中多次出現，則會捨棄之後的發生次數。|
|Seq.distinctby|||O (1) \*|||根據給定的索引鍵產生函數所傳回之索引鍵的泛型雜湊和相等比較，傳回不含重複專案的序列。 如果專案在順序中多次出現，則會捨棄之後的發生次數。|
|empty|O (1) |O (1) |O (1) |O (1) |O (1) |建立空集合。|
|exists|O (N) |O (N) |O (N) |O (記錄 (N) # A3|O (記錄 (N) # A3|測試序列中的任何元素是否符合指定的述詞。|
|array.exists2|O (min (N，M) # A3|-|O (min (N，M) # A3|||測試輸入序列中是否有任何一對對應的元素符合指定的述詞。|
|fill|O (N) |||||將陣列的元素範圍設定為指定的值。|
|filter|O (N) |O (N) |O (N) |O (N) |O (N) |傳回新的集合，其中只包含指定述詞所傳回之集合的元素 `true` 。|
|尋找|O (N) |O (N) |O (N) |O (記錄 (N) # A3|-|傳回指定的函式傳回的第一個元素 `true` 。 `System.Collections.Generic.KeyNotFoundException`如果沒有這類元素，則傳回。|
|findIndex|O (N) |O (N) |O (N) |-|-|傳回陣列中滿足給定述詞的第一個元素的索引。 如果沒有任何專案滿足述詞，則會引發 `System.Collections.Generic.KeyNotFoundException` 。|
|Map.findkey|-|-|-|O (記錄 (N) # A3|-|評估集合中每個對應的函式，並傳回函式傳回之第一個對應的索引鍵 `true` 。 如果沒有這類專案存在，則會引發此函式 `System.Collections.Generic.KeyNotFoundException` 。|
|摺疊|O (N) |O (N) |O (N) |O (N) |O (N) |將函式套用至集合中的每個元素，並透過計算將累計引數串接。 如果輸入函式為 f，且元素為 i0 .。。在中，此函式會計算 f ( ... (f s i0) ... ) 。|
|list.fold2|O (N) |O (N) |-|-|-|將函數套用至兩個集合的對應元素，並透過計算將累計引數串接。 集合的大小必須相同。 如果輸入函式為 f，且元素為 i0 .。。iN 和 j0 .。。jN，此函式會計算 f ( ... (f s i0 j0) ... ) jN 中。|
|List.foldback|O (N) |O (N) |-|O (N) |O (N) |將函式套用至集合中的每個元素，並透過計算將累計引數串接。 如果輸入函式為 f，且元素為 i0 .。。在中，此函式會在 s) # A3 中計算 f i0 ( ... (f。|
|List.foldback2|O (N) |O (N) |-|-|-|將函數套用至兩個集合的對應元素，並透過計算將累計引數串接。 集合的大小必須相同。 如果輸入函式為 f，且元素為 i0 .。。iN 和 j0 .。。jN，此函式會計算 jN s) # A3 中的 f i0 j0 ( ... (f。|
|forall|O (N) |O (N) |O (N) |O (N) |O (N) |測試集合的所有元素是否滿足指定的述詞。|
|array.forall2|O (N) |O (N) |O (N) |-|-|測試集合中所有對應的元素是否符合給定的述詞成對。|
|get/n|O (1) |O (N) |O (N) |-|-|根據指定的索引，從集合傳回專案。|
|head|-|O (1) |O (1) |-|-|傳回集合的第一個元素。|
|init|O (N) |O (N) |O (1) |-|-|建立集合，並指定維度和產生器函式來計算元素。|
|Seq.initinfinite|-|-|O (1) |-|-|產生順序，在反復查看時，會藉由呼叫指定的函式傳回連續的元素。|
|intersect|-|-|-|-|O (記錄 (N) \* 記錄 (M) # A5|計算兩個集合的交集。|
|Set.intersectmany|-|-|-|-|O (N1 \* N2 ... ) |計算一連串集合的交集。 順序不得為空白。|
|isEmpty|O (1) |O (1) |O (1) |O (1) |-|`true`如果集合是空的，則傳回。|
|Set.ispropersubset|-|-|-|-|O (M \* log (N) # A3|`true`如果第一個集合的所有專案都在第二個集合中，而且第二個集合中至少有一個元素不在第一個集合中，則傳回。|
|Set.ispropersuperset|-|-|-|-|O (M \* log (N) # A3|`true`如果第二個集合的所有元素都在第一個集合中，而且第二個集合中至少有一個元素不在第二個集合中，則傳回。|
|Set.issubset|-|-|-|-|O (M \* log (N) # A3|`true`如果第一個集合的所有元素都在第二個集合中，則傳回。|
|Set.issuperset|-|-|-|-|O (M \* log (N) # A3|`true`如果第二個集合的所有元素都在第一個集合中，則傳回。|
|Iter|O (N) |O (N) |O (N) |O (N) |O (N) |將指定的函式套用至集合的每個元素。|
|list.iteri|O (N) |O (N) |O (N) |-|-|將指定的函式套用至集合的每個元素。 傳遞至函式的整數指出元素的索引。|
|array.iteri2|O (N) |O (N) |-|-|-|將指定的函式套用至一對從兩個數組中的相符索引所繪製的元素。 傳遞至函式的整數指出元素的索引。 這兩個數組的長度必須相同。|
|list.iter2|O (N) |O (N) |O (N) |-|-|將指定的函式套用至一對從兩個數組中的相符索引所繪製的元素。 這兩個數組的長度必須相同。|
|last|O (1) |O (N) |O (N) |-|-|傳回適用集合中的最後一個專案。|
|長度|O (1) |O (N) |O (N) |-|-|傳回集合中的元素數目。|
|map|O (N) |O (N) |O (1) |-|-|建立集合，其專案為將指定函式套用至陣列的每個元素的結果。|
|list.map2|O (N) |O (N) |O (1) |-|-|建立集合，其專案是將指定的函式套用至兩個集合之對應元素的結果。 這兩個輸入陣列的長度必須相同。|
|list.map3|-|O (N) |-|-|-|建立集合，其專案是將指定函式同時套用至三個集合之對應元素的結果。|
|Mapi|O (N) |O (N) |O (N) |-|-|建立陣列，其專案為將指定函式套用至陣列的每個元素的結果。 傳遞至函式的整數索引，表示要轉換之元素的索引。|
|list.mapi2|O (N) |O (N) |-|-|-|建立集合，其專案為將指定函式套用至兩個集合的對應元素的結果，也會傳遞元素的索引。 這兩個輸入陣列的長度必須相同。|
|最大值|O (N) |O (N) |O (N) |-|-|傳回集合中最大的專案，並使用 [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) 運算子進行比較。|
|maxBy|O (N) |O (N) |O (N) |-|-|傳回集合中最大的專案，相較于在函數結果上使用 [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) 。|
|Set.maxelement|-|-|-|-|O (記錄 (N) # A3|根據用於集合的順序，傳回集合中最大的元素。|
|最小值|O (N) |O (N) |O (N) |-|-|傳回集合中最小的專案，使用 [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) 運算子進行比較。|
|minBy|O (N) |O (N) |O (N) |-|-|傳回集合中最小的專案，並使用函數結果上的 [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) 運算子來比較。|
|Set.minelement|-|-|-|-|O (記錄 (N) # A3|根據用於集合的順序，傳回集合中的最小元素。|
|List.ofarray|-|O (N) |O (1) |O (N) |O (N) |建立集合，其中包含與指定陣列相同的元素。|
|ofList|O (N) |-|O (1) |O (N) |O (N) |建立集合，其包含與指定清單相同的元素。|
|List.ofseq|O (N) |O (N) |-|O (N) |O (N) |建立集合，其包含與指定序列相同的元素。|
|派|-|-|O (N) |-|-|傳回輸入序列中每個專案及其前置專案的序列，但第一個專案除外，後者只會傳回做為第二個元素的前置專案。|
|partition|O (N) |O (N) |-|O (N) |O (N) |將集合分割成兩個集合。 第一個集合包含指定述詞傳回的專案 `true` ，而第二個集合則包含指定述詞傳回的元素 `false` 。|
|permute|O (N) |O (N) |-|-|-|傳回陣列，其中包含根據指定排列排列的所有元素。|
|選擇|O (N) |O (N) |O (N) |O (記錄 (N) # A3|-|將指定的函式套用至後續的元素，並傳回函式傳回部分的第一個結果。 如果函式永遠不會傳回部分， `System.Collections.Generic.KeyNotFoundException` 就會引發。|
|readonly|-|-|O (N) |-|-|建立可委派給指定順序物件的順序物件。 這種作業可確保類型轉換無法重新探索並改變原始序列。 例如，如果指定了陣列，傳回的序列將會傳回陣列的元素，但您無法將傳回的序列物件轉換成陣列。|
|reduce|O (N) |O (N) |O (N) |-|-|將函式套用至集合中的每個元素，並透過計算將累計引數串接。 此函式一開始會將函式套用至前兩個元素、將此結果連同第三個元素一起傳遞至函式，依此類推。 函數會傳回最終結果。|
|Array.reduceback|O (N) |O (N) |-|-|-|將函式套用至集合中的每個元素，並透過計算將累計引數串接。 如果輸入函式為 f，且元素為 i0 .。。在中，此函式會計算) # A3 中-1 的 f i0 ( ... (f。|
|remove|-|-|-|O (記錄 (N) # A3|O (記錄 (N) # A3|從對應的定義域中移除專案。 如果元素不存在，則不會引發任何例外狀況。|
|複製|-|O (N) |-|-|-|建立指定長度的清單，並將每個元素設定為指定的值。|
|轉速|O (N) |O (N) |-|-|-|以反向順序傳回包含元素的新清單。|
|掃描|O (N) |O (N) |O (N) |-|-|將函式套用至集合中的每個元素，並透過計算將累計引數串接。 這項作業會將函式套用至第二個引數和清單的第一個元素。 接著，作業會將此結果連同第二個元素一起傳遞到函式中，依此類推。 最後，此作業會傳回中繼結果清單和最終結果。|
|Array.scanback|O (N) |O (N) |-|-|-|類似于 List.foldback 作業，但會傳回中繼和最終結果。|
|singleton|-|-|O (1) |-|O (1) |傳回只產生一個專案的序列。|
|set|O (1) |-|-|-|-|將陣列的元素設定為指定的值。|
|skip|-|-|O (N) |-|-|傳回序列，這個序列會略過基礎序列的 N 個元素，然後產生序列的其餘專案。|
|skipWhile|-|-|O (N) |-|-|傳回序列，此序列會在指定的述詞傳回時略過基礎序列的元素， `true` 然後產生序列的其餘專案。|
|sort|O (N \* 記錄 (n) # A3 平均<br /><br />O (N ^ 2) 最糟的情況|O (N \* 記錄 (n) # A3|O (N \* 記錄 (n) # A3|-|-|依元素值排序集合。 使用 [compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)來比較元素。|
|sortBy|O (N \* 記錄 (n) # A3 平均<br /><br />O (N ^ 2) 最糟的情況|O (N \* 記錄 (n) # A3|O (N \* 記錄 (n) # A3|-|-|使用指定投射提供的索引鍵來排序指定的清單。 使用 [compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)來比較索引鍵。|
|Array.sortinplace|O (N \* 記錄 (n) # A3 平均<br /><br />O (N ^ 2) 最糟的情況|-|-|-|-|藉由就地變更並使用指定的比較函式，來排序陣列的元素。 使用 [compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)來比較元素。|
|Array.sortinplaceby|O (N \* 記錄 (n) # A3 平均<br /><br />O (N ^ 2) 最糟的情況|-|-|-|-|藉由就地變更並使用指定的索引鍵投射，來排序陣列的元素。 使用 [compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)來比較元素。|
|Array.sortinplacewith|O (N \* 記錄 (n) # A3 平均<br /><br />O (N ^ 2) 最糟的情況|-|-|-|-|使用指定的比較函式來排序陣列的元素，並使用指定的比較函數作為順序。|
|List.sortwith|O (N \* 記錄 (n) # A3 平均<br /><br />O (N ^ 2) 最糟的情況|O (N \* 記錄 (n) # A3|-|-|-|使用指定的比較函式作為順序，並傳回新的集合，以排序集合的元素。|
|sub|O (N) |-|-|-|-|建立陣列，其中包含由起始索引和長度指定的指定子範圍。|
|Sum|O (N) |O (N) |O (N) |-|-|傳回集合中元素的總和。|
|sumBy|O (N) |O (N) |O (N) |-|-|傳回將函數套用至集合的每個專案所產生的結果總和。|
|尾巴|-|O (1) |-|-|-|傳回不含第一個元素的清單。|
|take|-|-|O (N) |-|-|傳回序列的元素，直到指定的計數為止。|
|takeWhile|-|-|O (1) |-|-|傳回序列，此序列會在指定的述詞傳回時產生基礎序列的元素， `true` 然後不會傳回更多元素。|
|toArray|-|O (N) |O (N) |O (N) |O (N) |從指定的集合建立陣列。|
|toList|O (N) |-|O (N) |O (N) |O (N) |從指定的集合建立清單。|
|List.toseq|O (1) |O (1) |-|O (1) |O (1) |從指定的集合建立序列。|
|truncate|-|-|O (1) |-|-|傳回序列，這個序列會在列舉時傳回不超過 N 個元素。|
|tryFind|O (N) |O (N) |O (N) |O (記錄 (N) # A3|-|搜尋符合指定之述詞的元素。|
|Array.tryfindindex|O (N) |O (N) |O (N) |-|-|搜尋符合指定述詞的第一個元素，並傳回相符專案的索引， `None` 如果沒有這類專案，則為。|
|Map.tryfindkey|-|-|-|O (記錄 (N) # A3|-|傳回集合中符合指定述詞之第一個對應的索引鍵， `None` 如果沒有這類專案存在，則傳回。|
|Array.trypick|O (N) |O (N) |O (N) |O (記錄 (N) # A3|-|將指定的函式套用至連續的元素，並傳回函式針對某個值傳回的第一個結果 `Some` 。 如果沒有這類元素存在，則作業會傳回 `None` 。|
|展開|-|-|O (N) |-|-|傳回包含指定計算所產生之元素的序列。|
|union|-|-|-|-|O (M \* log (N) # A3|計算兩個集合的聯集。|
|Set.unionmany|-|-|-|-|O (N1 \* N2 ... ) |計算一系列集合的聯集。|
|unzip|O (N) |O (N) |O (N) |-|-|將配對清單分割成兩個清單。|
|list.unzip3|O (N) |O (N) |O (N) |-|-|將三合一清單分割成三個清單。|
|視窗|-|-|O (N) |-|-|傳回序列，這個序列會產生包含從輸入序列中繪製之元素的滑動視窗。 每個視窗都會以全新的陣列傳回。|
|zip|O (N) |O (N) |O (N) |-|-|將兩個集合合併成成對的清單。 這兩個清單必須有相等的長度。|
|array.zip3|O (N) |O (N) |O (N) |-|-|將三個集合合併成三個清單。 清單必須有相等的長度。|

## <a name="see-also"></a>請參閱

- [F# 類型](fsharp-types.md)
- [F # 語言參考](index.md)
