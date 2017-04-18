---
title: "How to: Synchronize Concurrent Operations with a Barrier | Microsoft Docs"
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
  - "Barrier, how to use"
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Synchronize Concurrent Operations with a Barrier
下列範例示範如何使並行工作與 <xref:System.Threading.Barrier> 同步。  
  
## 範例  
 下列程式的目的，是要計算在使用隨機化演算法將字組重新排列的情況下，讓兩個執行緒在相同階段都各自找到一半方案，需要多少個反覆項目 \(或階段\)。  在每個執行緒都將其單字重新排列後，階段後的 Barrier 作業就會比較這兩個結果，查看是否以正確的字組順序產生正確的句子。  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <xref:System.Threading.Barrier> 這個物件可防止平行作業中的個別工作繼續進行，直到所有工作都到達屏障為止。  當分階段進行平行作業，而每個階段又需要在工作之間同步處理時，這個物件會很有用。  在這個範例中，作業分兩個階段。  在第一階段中，每個工作會將資料填入緩衝區的區段。  當個別工作填好它的區段之後，便會通知屏障表示它準備繼續進行，然後等待。  當所有工作都已通知屏障之後，即解除對這些工作的封鎖，接著開始進行第二階段。  設置屏障有其必要性，因為第二階段需要每個工作都能存取到這點為止產生的所有資料。  如果沒有這個屏障，首先要完成的工作可能會是嘗試從其他工作尚未填入的緩衝區讀取資料。  您可以運用上述方式同步處理多個階段，而階段的數目並沒有限制。  
  
## 請參閱  
 [Data Structures for Parallel Programming](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)