---
title: "如何：實作動態磁碟分割"
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
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b08c387c9b10a9d6fa8728a7fce87a7894a37fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-dynamic-partitions"></a>如何：實作動態磁碟分割
下列範例示範如何實作自訂 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>，它會實作動態分割，並可從特定多載 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 和 PLINQ 使用。  
  
## <a name="example"></a>範例  
 每次分割區在列舉程式上呼叫 <xref:System.Collections.IEnumerator.MoveNext%2A> 時，列舉程式就會提供一個清單元素給分割區。 在 PLINQ 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 的案例中，分割區是 <xref:System.Threading.Tasks.Task> 執行個體。 由於要求是在多個執行緒上同時發生，因而也會同步存取目前的索引。  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 這是區塊分割的範例，其中每個區塊包含一個元素。 藉由一次提供更多元素，可以減少鎖定競爭，理論上可以實現更快的效能。 不過，在某些時候，較大的區塊可能需要額外的負載平衡邏輯，才能在所有工作完成前使所有執行緒保持忙碌。  
  
## <a name="see-also"></a>請參閱  
 [PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [操作說明：為靜態分割實作 Partitioner](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
