---
title: "How to: Implement Dynamic Partitions | Microsoft Docs"
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
  - "tasks, how to create a dynamic partitioner"
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# How to: Implement Dynamic Partitions
下列範例顯示如何實作自訂 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=fullName>，這個項目會實作動態磁碟分割並且可從特定多載 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 和從 PLINQ 受到使用。  
  
## 範例  
 每次磁碟分割在列舉程式上呼叫 <xref:System.Collections.IEnumerator.MoveNext%2A> 時，列舉程式都會提供一個清單項目給該磁碟分割。  在 PLINQ 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 的案例中，磁碟分割是 <xref:System.Threading.Tasks.Task> 執行個體。  因為要求會並行發生在多個執行緒上，所以對目前索引的存取會受到同步處理。  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 這是一個區塊 \(Chunk\) 分割範例，每個區塊都由一個項目組成。  藉由同時提供更多項目，您可以減少鎖定爭用情形，理論上可達到更快的效能。  但是有時候，使用較大的區塊時，可能需有額外的負載平衡邏輯來讓所有執行緒都保持運作，直到完成所有工作為止。  
  
## 請參閱  
 [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)   
 [How to: Implement a Partitioner for Static Partitioning](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)