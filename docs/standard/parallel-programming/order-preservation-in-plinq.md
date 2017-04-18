---
title: "Order Preservation in PLINQ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PLINQ queries, order preservation"
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Order Preservation in PLINQ
使用 PLINQ 的目標是充分發揮效能，並兼顧正確性。  查詢執行的速度固然愈快愈好，但產生的結果也必須要正確。  在某些情況下，來源序列必須保有其順序，才能達到查詢的正確性；但排序是十分耗費運算資源的。  因此在預設情況下，PLINQ 不會保留來源序列的順序。  PLINQ 在這方面與 [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] 相似，但與會保留順序的 LINQ to Objects 不同。  
  
 若要覆寫預設行為，您可以在來源序列上使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子開啟順序保留功能。  後續您可以使用 <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> 方法關閉查詢中的順序保留功能。  在這兩個方法中，都是根據判斷以平行或循序方式執行查詢的啟發學習法來處理查詢。  如需詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
 下列範例說明未排序的平行查詢如何篩選所有符合條件的項目，而不嘗試以任何方式排序結果  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 此查詢不一定會產生來源序列中符合條件的前 1000 個城市，而是會產生符合條件的其中 1000 個城市。  PLINQ 查詢運算子會將來源序列分割成多個以並行工作的形式處理的子序列。  如果未指定順序保留，則每次分割所產生的結果就會以任意順序交付至下一個查詢階段。  此外，分割在繼續處理其餘項目之前，可能會產生其結果的子集。  產生的順序可能每次都不同。  您的應用程式無法控制這一點，因為這取決於作業系統排序執行緒的方式。  
  
 下列範例會在來源序列上使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子覆寫預設行為。  如此可確保 <xref:System.Linq.ParallelEnumerable.Take%2A> 方法會傳回來源序列中符合條件的前 1000 個城市。  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 但此查詢可能無法和未排序的查詢執行得一樣快，因為它必須在整個分割過程中追蹤原始順序，並在合併期間確保順序的一致性。  因此，建議您只有在必要時才使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>，且僅用於查詢中需要此項目的部分。  無須再保留順序時，請使用 <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> 加以關閉。  下列範例將撰寫兩個查詢以執行此作業。  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 請注意，PLINQ 會為其餘查詢保留 order\-imposing 運算子所產生的序列順序。  換句話說，<xref:System.Linq.ParallelEnumerable.OrderBy%2A> 和 <xref:System.Linq.ParallelEnumerable.ThenBy%2A> 之類的運算子，會被視為後續接著會有 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 呼叫的運算子。  
  
## 查詢運算子和順序  
 下列查詢運算子會在查詢的所有後續作業中執行順序保留，或在呼叫 <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> 後執行：  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 下列 PLINQ 查詢運算子在某些情況下可能要有排序的來源序列，才能產生正確的結果：  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 有些 PLINQ 查詢運算子的行為會隨著其來源序列排序與否而不同。  這些運算子如下表所列。  
  
|運算子|來源序列已排序的結果|來源序列未排序的結果|  
|---------|----------------|----------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|不具關聯性或不具互換性之作業的不具決定性輸出|不具關聯性或不具互換性之作業的不具決定性輸出|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|不具關聯性或不具互換性之作業的不具決定性輸出|不具關聯性或不具互換性之作業的不具決定性輸出|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|未排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|非決定性地平行執行|非決定性地平行執行|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|傳回指定的項目|任意項目|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|重新排序序列|啟動新的排序區段|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|重新排序序列|啟動新的排序區段|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|不適用 \(與 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> 相同的預設值\)|不適用|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|不適用 \(與 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> 相同的預設值\)|不適用|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|反轉|不執行任何動作|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> \(已編排索引\)|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> \(已編排索引\)|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|排序比較|未排序比較|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|略過前 *n*個項目|略過任 *n* 個項目|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|排序結果|非決定性。  以目前的任意順序執行 SkipWhile|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|不具關聯性或不具互換性之作業的不具決定性輸出|不具關聯性或不具互換性之作業的不具決定性輸出|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|取用前 `n` 個項目|取用任 `n` 個項目|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|排序結果|非決定性。  以目前的任意順序執行 TakeWhile|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|補充 `OrderBy`|補充 `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|補充 `OrderBy`|補充 `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|不適用|不適用|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> \(已編排索引\)|排序結果|未排序結果|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|排序結果|未排序結果|  
  
 未排序結果不是主動隨機排列，而是未套用任何特殊排序邏輯。  在某些情況中，未排序的查詢可能保有來源序列順序。  對於使用索引 Select 運算子的查詢，PLINQ 保證輸出項目會依遞增索引順序顯示，但不保證哪個索引會指派給項目。  
  
## 請參閱  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)