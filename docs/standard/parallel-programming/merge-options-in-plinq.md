---
title: "PLINQ 中的合併選項"
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
helpviewer_keywords: PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9bf586c1805fc5b5f1cc5f96f4e6b08d80c199a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="merge-options-in-plinq"></a>PLINQ 中的合併選項
當查詢正在執行平行 PLINQ 資料分割作為來源序列，讓多個執行緒可以在不同的組件上同時處理，通常在個別執行緒上。 如果結果使用上一個執行緒，例如，在`foreach`(`For Each`中[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 迴圈，則必須以每個執行緒的結果合併回單一序列。 PLINQ 執行的合併類型而定的運算子會出現在查詢中。 比方說，強制執行結果，在新的訂單的運算子必須緩衝處理所有執行緒的所有項目。 觀點耗用端執行緒 （這也是應用程式使用者） 的完整緩衝的查詢可能會執行值得注意的一段時間，它會產生其第一個結果。 其他運算子，根據預設，會部分進行緩衝處理;會產生其結果批次中。 運算子，<xref:System.Linq.ParallelEnumerable.ForAll%2A>預設不會經過緩衝。 它會產生所有項目從所有執行緒立即。  
  
 使用<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>方法，如所示，在下列範例中，您可以提供提示給 PLINQ，表示何種合併，以執行。  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 完整的範例，請參閱[How to： 在 PLINQ 中指定 「 合併選項](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)。  
  
 如果特定的查詢無法支援要求的選項，此選項將只忽略。 在大部分情況下，您就不需要指定 PLINQ 查詢的合併選項。 不過，在某些情況下，您可能會發現藉由測試及查詢的執行最佳的非預設模式的度量。 這個選項的常見用法是強制使用區塊合併的運算子，將串流處理其結果，以提供更能有效回應的使用者介面。  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions>列舉會包含下列選項，指定當一個執行緒上耗用結果查詢的最終輸出產生的時，支援的查詢圖形：  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered>選項會讓每個處理過的項目，傳回每個執行緒，因為它會產生。 此行為是類似於 「 streaming 」 的輸出。 如果<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>運算子是在查詢中，存在`NotBuffered`保留來源項目順序。 雖然`NotBuffered`而產生的結果，因為已經有開始、 所有結果可能仍會產生的總時間會超過使用其他合併選項之一。  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> 選項會讓查詢將項目收集至緩衝區中，然後定期將緩衝區內容一次產生至耗用端執行緒中。 這是產生 「 區塊 」 中的來源資料，而不使用 「 資料流 」 的行為類似`NotBuffered`。 `AutoBuffered`可能需要花費長於`NotBuffered`至耗用端執行緒上使用第一個項目。 緩衝區的大小以及產生的確切行為不是可設定，而可能有所不同，取決於各種因素與查詢相關聯。  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered>選項會使任何項目產生之前進行緩衝處理整個查詢的輸出。 當您使用此選項時，就可以花長時間之前第一個項目位於耗用端執行緒，但仍會產生完整的結果，可能會較快，使用其他選項。  
  
## <a name="query-operators-that-support-merge-options"></a>支援的合併選項的查詢運算子  
 下表列出支援所有的合併選項模式，受限於指定的限制的運算子。  
  
|運算子|限制|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|需要陣列或清單僅限於來源的非排序查詢。|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|需要陣列或清單僅限於來源的非排序查詢。|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|無|  
  
 所有其他 PLINQ 查詢運算子可能會忽略使用者提供的合併選項。 例如，某些查詢運算子，<xref:System.Linq.ParallelEnumerable.Reverse%2A>和<xref:System.Linq.ParallelEnumerable.OrderBy%2A>，無法產生任何項目，直到所有已產生及重新排列。 因此，當<xref:System.Linq.ParallelMergeOptions>也包含這類運算子的查詢中使用了<xref:System.Linq.ParallelEnumerable.Reverse%2A>，合併行為將不會套用在查詢中，直到之後該運算子所產生的結果。  
  
 有些運算子能夠處理的合併選項取決於來源序列中，類型及是否<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>稍早在查詢中使用運算子。 <xref:System.Linq.ParallelEnumerable.ForAll%2A>一定是<xref:System.Linq.ParallelMergeOptions.NotBuffered>; 它會立即產生其項目。 <xref:System.Linq.ParallelEnumerable.OrderBy%2A>一定是<xref:System.Linq.ParallelMergeOptions.FullyBuffered>; 它會產生前，它必須排序整份清單。  
  
## <a name="see-also"></a>另請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [操作說明：在 PLINQ 中指定合併選項](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
