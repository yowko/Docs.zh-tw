---
title: "PLINQ 中的順序保留"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 060459cf8f408e40ddc394fbcda6a022ec6379de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="order-preservation-in-plinq"></a>PLINQ 中的順序保留
在 PLINQ，目標是為了達到最佳效能，同時維護正確性。 查詢應該盡快執行，但仍會產生正確的結果。 在某些情況下，正確性需要保留; 來源序列的順序不過，順序可能會高度耗費計算能力。 因此，根據預設，PLINQ 不會保留來源序列中的順序。 在這方面類似於 PLINQ [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)]，但是與 LINQ to Objects，它就會保留順序不同。  
  
 若要覆寫預設行為，您可以開啟順序保留使用<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>來源序列上的運算子。 您可以再關閉順序保留稍後在查詢中使用<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>方法。 這兩種方法，以根據啟發學習法，判斷是否要執行為平行查詢或為循序處理的查詢。 如需詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
 下列範例顯示未排序的平行查詢篩選之符合條件，但不會嘗試以任何方式排序結果的所有項目。  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 此查詢不一定會產生符合的條件，但而 1000年城市符合條件的某些組來源序列中的前 1000 個城市。 PLINQ 查詢運算子的資料分割成多個並行工作以處理的子來源序列。 如果未指定保留順序，每個資料分割的結果都會傳送給查詢以任意順序的下一個階段。 此外，資料分割可能會產生其結果的子集，它會繼續處理其餘的項目之前。 產生的順序可能會每次可能不同。 您的應用程式無法控制這點因為它相依於作業系統排程執行緒的方式。  
  
 下列範例會覆寫預設行為使用<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>來源序列上的運算子。 如此可確保<xref:System.Linq.ParallelEnumerable.Take%2A>方法會傳回符合條件的來源序列中的前 1000 個城市。  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 不過，此查詢可能無法執行的未排序的版本為快速因為它必須持續追蹤的資料分割的整個原始順序，以及在合併時確保順序一致。 因此，我們建議您改用<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>只在必要時，並只針對這些組件的查詢需要它。 當不再需要保留順序時，使用<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>將它關閉。 下列範例會達到這撰寫兩個查詢。  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 請注意，會保留 PLINQ 查詢的其餘部分的順序諸運算子產生序列的排序。 換句話說，運算子，例如<xref:System.Linq.ParallelEnumerable.OrderBy%2A>和<xref:System.Linq.ParallelEnumerable.ThenBy%2A>會視為已後面呼叫<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>。  
  
## <a name="query-operators-and-ordering"></a>查詢運算子和排序  
 下列查詢運算子導入到所有後續的作業，在查詢中，或直到順序保留<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>稱為：  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 下列的 PLINQ 查詢運算子在某些情況下可能需要已排序的來源順序來產生正確的結果：  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 有些 PLINQ 查詢運算子的行為有所不同，取決於排序或未排序其來源序列。 下表列出這些運算子。  
  
|運算子|當來源序列排序的結果|當來源序列是未排序的結果|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|不具決定性 nonassociative 或 noncommutative 作業輸出|不具決定性 nonassociative 或 noncommutative 作業輸出|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|不具決定性 nonassociative 或 noncommutative 作業輸出|不具決定性 nonassociative 或 noncommutative 作業輸出|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|未排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|非確定性地以平行方式執行|非確定性地以平行方式執行|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|重新排列順序|啟動新的排序區段|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|重新排列順序|啟動新的排序區段|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|不適用 (相同預設值為<xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|不適用|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|不適用 (相同預設值為<xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|不適用|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|反轉|不執行任何動作|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>（索引）|排序的結果|未排序的結果。|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|排序的結果。|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>（索引）|排序的結果。|未排序的結果。|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|已排序的比較|未排序的比較|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|略過第一次 *n* 項目|略過任何 *n* 項目|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|排序的結果。|不具決定性。 SkipWhile 對目前的任意順序|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|不具決定性 nonassociative 或 noncommutative 作業輸出|不具決定性 nonassociative 或 noncommutative 作業輸出|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|會採用第一個`n`項目|會採用任何`n`項目|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|排序的結果|不具決定性。 TakeWhile 對目前的任意順序|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|增補`OrderBy`|增補`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|增補`OrderBy`|增補`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>（索引）|排序的結果|未排序的結果|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|排序的結果|未排序的結果|  
  
 未排序的結果不主動打散;只要沒有任何特殊的順序邏輯套用至它們。 在某些情況下，未排序的查詢可能會保留來源序列的排序。 使用索引的 Select 運算子的查詢，PLINQ 可保證輸出項目的順序遞增索引，但不保證哪些索引會指派給哪些項目會將恰。  
  
## <a name="see-also"></a>另請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)
