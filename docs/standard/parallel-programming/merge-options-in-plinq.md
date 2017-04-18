---
title: "Merge Options in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, merge options"
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Merge Options in PLINQ
以平行方式執行查詢時，PLINQ 會將來源序列分割，讓多個執行緒可以同時處理不同的部分 \(通常是在不同的執行緒上\)。  如果有一個執行緒 \(例如 `foreach` 迴圈，在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 `For Each` 迴圈\) 需要耗用結果，則必須將所有執行緒的結果合併成一個序列。  PLINQ 執行的合併類型取決於查詢中出現的運算子。  例如，對結果施加新順序的運算子必須將所有執行緒中的所有項目都放在緩衝區中。  從耗用端執行緒 \(也是從應用程式使用者\) 的觀點來看，如果讓查詢將項目全都放在緩衝區中，則這個查詢可能要執行很長一段時間才會產生第一個結果。  其他運算子則預設只會將部分項目放在緩衝區中，因為它們會分批產生結果。  有一個運算子預設不會將項目放在緩衝區中，那就是 <xref:System.Linq.ParallelEnumerable.ForAll%2A>。  它會直接產生所有執行緒中的所有項目。  
  
 您可以使用 <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> 方法 \(如下列範例所示\) 向 PLINQ 提供提示，表示要執行的合併類型。  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 如需完整的範例，請參閱 [How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)。  
  
 如果特定查詢無法支援所要求的選項，即會直接忽略該選項。  大部分情況下，您不需要指定 PLINQ 查詢的合併選項。  不過，有時候經由測試和測量，您可能會發現某個查詢在非預設模式下的執行效能最佳。  這個選項的一個常見用途是強制區塊合併運算子將結果變成一個資料流，以提供回應性更佳的使用者介面。  
  
## ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> 列舉包含下列選項，這些選項針對支援的查詢型態，指定在一個執行緒上耗用結果時，要如何產生最終查詢結果：  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions> 選項會讓每個執行緒中處理的每個項目在產生後立即傳回。  這種行為類似於輸出的「串流」。  如果查詢中出現 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子，則 `NotBuffered` 會保留來源項目的順序。  雖然 `NotBuffered` 會在一有結果時立即開始產生結果，但是產生所有結果的總時間仍可能會比使用其他任何一個合併選項還長。  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions> 選項會讓查詢將項目收集至緩衝區中，然後定期將緩衝區內容一次產生至耗用端執行緒中。  這類似於產生成塊的來源資料，而不是使用 `NotBuffered` 的「串流」行為。  `AutoBuffered` 可能會花費比 `NotBuffered` 更多的時間將第一個項目放在耗用端執行緒上。  緩衝區大小和實際的產生行為是無法設定的，這些會因查詢的各種相關因素而異。  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions> 選項會先將整個查詢輸出都放在緩衝區中，然後才產生任何項目。  當您使用這個選項時，可能需花費更長的時間才能將第一個項目放在耗用端執行緒上，但是產生完整結果的速度仍可能會比使用其他選項還快。  
  
## 支援合併選項的查詢運算子  
 下表列出所有支援合併選項模式的運算子，並指出每個運算子受到的限制。  
  
|運算子|限制|  
|---------|--------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|只有 Array 或 List 來源的未排序查詢。|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|只有 Array 或 List 來源的未排序查詢。|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|無|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|無|  
  
 所有其他 PLINQ 查詢運算子可能都會忽略使用者提供的合併選項。  某些查詢運算子 \(例如 <xref:System.Linq.ParallelEnumerable.Reverse%2A> 和 <xref:System.Linq.ParallelEnumerable.OrderBy%2A>\) 必須等到產生並排序所有項目之後才能產生任何項目。  因此，當使用 <xref:System.Linq.ParallelMergeOptions> 的查詢中還包含 <xref:System.Linq.ParallelEnumerable.Reverse%2A> 之類的運算子時，必須等到該運算子產生結果之後，才會在查詢中套用合併行為。  
  
 某些運算子處理合併選項的能力取決於來源序列的型別，以及查詢中先前是否已使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 運算子。  <xref:System.Linq.ParallelEnumerable.ForAll%2A> 永遠是 <xref:System.Linq.ParallelMergeOptions>，它會立即產生項目。  <xref:System.Linq.ParallelEnumerable.OrderBy%2A> 永遠是 <xref:System.Linq.ParallelMergeOptions>，它必須先排序整個清單才會產生項目。  
  
## 請參閱  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)