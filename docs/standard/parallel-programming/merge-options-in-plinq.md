---
title: PLINQ 中的合併選項
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7df080185db9631e47bb7a886f6e0db894974a6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="merge-options-in-plinq"></a>PLINQ 中的合併選項
當查詢平行執行時，PLINQ 會分割來源序列，讓多個執行緒可以在不同的組件上同時工作，通常是在個別的執行緒上。 如果結果是在一個執行緒上使用，例如在 `foreach` (Visual Basic 中的 `For Each`) 迴圈中，則必須將每個執行緒中的結果合併回單一序列。 PLINQ 執行的合併類型，取決於存在查詢中的運算子。 比方說，對結果強制執行新順序的運算子，必須緩衝所有執行緒中的所有元素。 就使用執行緒的角度而言 (也是應用程式使用者的觀點)，完整緩衝的查詢在產生其第一個結果前可能會執行不算短的一段時間。 其他運算子預設會部分進行緩衝；會批次產生其結果。 有一個運算子 (<xref:System.Linq.ParallelEnumerable.ForAll%2A>) 預設不會進行緩衝。 它會立即產生所有執行緒中的所有元素。  
  
 使用 <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> 方法，如下列範例所示，您可以提供提示給 PLINQ 以指示要執行何種合併。  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 如需完整範例，請參閱[如何：在 PLINQ 中指定合併選項](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)。  
  
 如果特定查詢無法支援要求的選項，將會忽略此選項。 在多數情況下，您不需為 PLINQ 查詢指定合併選項。 不過在某些情況下，藉由測試及量測，您會發現查詢在非預設模式的執行效能最佳。 這個選項的常見用法是強制區塊合併運算子串流處理其結果，以提供更能有效回應的使用者介面。  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> 列舉包含下列選項，其中針對支援的查詢圖形，會指定在一個執行緒上使用結果時如何產生最終輸出：  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> 選項會讓每個處理過的元素一產生就從每個執行緒傳回。 此行為類似「串流處理」輸出。 如果 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子存在查詢中，`NotBuffered` 會保留來源元素的順序。 雖然 `NotBuffered` 會在一有可用的結果時就開始產生，但產生所有結果的總時間可能仍會比使用其他合併選項久。  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> 選項會讓查詢將項目收集至緩衝區中，然後定期將緩衝區內容一次產生至耗用端執行緒中。 這類似以區塊方式產生來源資料，而非使用 `NotBuffered` 的「串流處理」行為。 相較於 `NotBuffered`，`AutoBuffered` 會需要更多時間才能讓第一個元素可用於使用的執行緒上。 緩衝區的大小和確切的產生行為無法設定，而且可能有所不同，這取決於和查詢相關的各種因素。  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> 選項會在任一元素產生前先緩衝整個查詢的輸出。 使用此選項時，會需要更多時間才能讓第一個元素可用於使用的執行緒上，但產生整體結果的速度可能仍比使用其他選項快。  
  
## <a name="query-operators-that-support-merge-options"></a>支援合併選項的查詢運算子  
 下表列出支援所有合併選項模式的運算子及其具體限制。  
  
|運算子|限制|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|只含有陣列或清單來源的非排序查詢。|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|只含有陣列或清單來源的非排序查詢。|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|無|  
  
 所有其他的 PLINQ 查詢運算子可能會忽略使用者提供的合併選項。 某些查詢運算子 (例如 <xref:System.Linq.ParallelEnumerable.Reverse%2A> 和 <xref:System.Linq.ParallelEnumerable.OrderBy%2A>) 在所有元素都已產生並重新排序之前無法產生任何元素。 因此，當 <xref:System.Linq.ParallelMergeOptions> 使用於也包含運算子 (例如 <xref:System.Linq.ParallelEnumerable.Reverse%2A>) 的查詢中時，一直到該運算子已產生其結果後，才會在查詢中套用合併行為。  
  
 某些運算子是否可以處理合併選項，取決於來源序列的類型，以及先前是否在查詢中使用了 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子。 <xref:System.Linq.ParallelEnumerable.ForAll%2A> 一律為 <xref:System.Linq.ParallelMergeOptions.NotBuffered>；它會立即產生其元素。 <xref:System.Linq.ParallelEnumerable.OrderBy%2A> 一律為 <xref:System.Linq.ParallelMergeOptions.FullyBuffered>；它必須先排序整個清單後才會產生。  
  
## <a name="see-also"></a>請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [操作說明：在 PLINQ 中指定合併選項](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
