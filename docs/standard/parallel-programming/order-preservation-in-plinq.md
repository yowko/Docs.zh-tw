---
title: PLINQ 中的順序保留
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b98fdcd425ae62aca0149df5136c28edc023bf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="order-preservation-in-plinq"></a>PLINQ 中的順序保留
在 PLINQ 中，目標是在達到最佳效能的同時維持正確性。 查詢應以最快的速度執行，但仍應產生正確的結果。 在某些情況下，需要保留來源序列的順序以保持正確性；不過，排序可能需要大量計算。 因此，根據預設，PLINQ 不會保留來源序列的順序。 在這方面，PLINQ 類似於 [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)]，但是有別於會保留順序的 LINQ to Objects。  
  
 若要覆寫預設行為，您可以在來源序列上使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子開啟順序保留。 您之後可以使用 <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> 方法在查詢中關閉順序保留。 使用這兩種方法，查詢是依據啟發學習法來處理，而啟發學習法會判斷要以平行方式或循序執行查詢。 如需詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
 下列範例顯示未排序的平行查詢，其會篩選符合條件的所有元素，但不會嘗試以任何方式排序結果。  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 此查詢不一定會在來源序列中產生符合條件的前 1000 個城市，而是 1000 個城市中符合條件的一些組合。 PLINQ 查詢運算子會將來源序列分割為以並行工作處理的多個子序列。 如果未指定保留順序，每個分割區中的結果會以任意順序傳送到查詢的下一個階段。 此外，分割區可能會先產生其結果的子集，然後再繼續處理其餘的元素。 每次產生的順序可能會不同。 您的應用程式無法控制這點，因為這取決於作業系統排程執行緒的方式。  
  
 下列範例會在來源序列上使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子以覆寫預設行為。 如此可確保 <xref:System.Linq.ParallelEnumerable.Take%2A> 方法會在來源序列中傳回符合條件的前 1000 個城市。  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 不過，此查詢可能無法和未排序版本的執行速度一樣快，因為它必須記錄分割區內的原始順序，以及在合併時確保順序一致。 因此，建議您只在必要時使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>，並只針對查詢中需要它的組件使用。 當不再需要保留順序時，請使用 <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> 將它關閉。 下列範例透過撰寫兩個查詢來實現此目標。  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 請注意，PLINQ 會為其餘的查詢保留 order-imposing 運算子產生的序列順序。 換句話說，<xref:System.Linq.ParallelEnumerable.OrderBy%2A> 和 <xref:System.Linq.ParallelEnumerable.ThenBy%2A> 等運算子的處理方式，如同後續呼叫了 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>。  
  
## <a name="query-operators-and-ordering"></a>查詢運算子和排序  
 下列查詢運算子會將順序保留導入查詢中所有後續的作業，或直到呼叫 <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> 為止：  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 下列 PLINQ 查詢運算子在某些情況下可能需要已排序的來源序列產生正確的結果：  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 有些 PLINQ 查詢運算子的行為有所不同，這取決於其來源序列是已排序或未排序。 下表列出這些運算子。  
  
|運算子|來源序列排序的結果|來源序列未排序的結果|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|非關聯或非可交換運算的不具決定性輸出|非關聯或非可交換運算的不具決定性輸出|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|非關聯或非可交換運算的不具決定性輸出|非關聯或非可交換運算的不具決定性輸出|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|傳回指定的元素|任意元素|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|傳回指定的元素|任意元素|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|未排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|傳回指定的元素|任意元素|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|傳回指定的元素|任意元素|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|以平行方式非決定性地執行|以平行方式非決定性地執行|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|傳回指定的元素|任意元素|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|傳回指定的元素|任意元素|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|重新排列順序|啟動新的排序區段|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|重新排列順序|啟動新的排序區段|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|不適用 (與 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> 的預設值相同)|不適用|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|不適用 (與 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> 的預設值相同)|不適用|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|反轉|不執行任何動作|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (已編製索引)|排序的結果|未排序的結果。|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|排序的結果。|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (已編製索引)|排序的結果。|未排序的結果。|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|排序的比較|未排序的比較|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|略過前 *n* 個元素|略過任 *n* 個元素|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|排序的結果。|非決定性。 以目前的任意順序執行 SkipWhile|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|非關聯或非可交換運算的不具決定性輸出|非關聯或非可交換運算的不具決定性輸出|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|採用前 `n` 個元素|採用任 `n` 個元素|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|排序的結果|非決定性。 以目前的任意順序執行 TakeWhile|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|補充 `OrderBy`|補充 `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|補充 `OrderBy`|補充 `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (已編製索引)|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|排序的結果|未排序的結果|  
  
 未排序的結果不會主動打散；它們只是未套用任何特殊的排序邏輯。 在某些情況下，未排序的查詢可能會保留來源序列的順序。 對於使用已編制索引之 Select 運算子的查詢，PLINQ 可保證輸出元素將以遞增索引的順序產生，但不保證哪些索引會指派給哪些元素。  
  
## <a name="see-also"></a>請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)
