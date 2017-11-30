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
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="ab88c-102">如何：實作動態磁碟分割</span><span class="sxs-lookup"><span data-stu-id="ab88c-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="ab88c-103">下列範例示範如何實作自訂<xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>，會實作動態磁碟分割，並可從特定多載<xref:System.Threading.Tasks.Parallel.ForEach%2A>和從 PLINQ。</span><span class="sxs-lookup"><span data-stu-id="ab88c-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab88c-104">範例</span><span class="sxs-lookup"><span data-stu-id="ab88c-104">Example</span></span>  
 <span data-ttu-id="ab88c-105">每次呼叫分割區<xref:System.Collections.IEnumerator.MoveNext%2A>列舉值列舉值，以一個清單項目提供資料分割。</span><span class="sxs-lookup"><span data-stu-id="ab88c-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="ab88c-106">在 PLINQ 和<xref:System.Threading.Tasks.Parallel.ForEach%2A>，分割區是<xref:System.Threading.Tasks.Task>執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab88c-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="ab88c-107">要求中的多個執行緒上同時發生，因為目前的索引來存取會同步處理。</span><span class="sxs-lookup"><span data-stu-id="ab88c-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="ab88c-108">這是區塊的對進行資料分割，一個項目所組成的每個區塊的範例。</span><span class="sxs-lookup"><span data-stu-id="ab88c-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="ab88c-109">藉由一次提供多個項目，可以降低透過鎖定競爭，理論上達到更快的效能。</span><span class="sxs-lookup"><span data-stu-id="ab88c-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="ab88c-110">不過，在某些時候，較大的區塊可能需要額外的負載平衡邏輯才能使所有執行緒忙碌，直到完成所有工作。</span><span class="sxs-lookup"><span data-stu-id="ab88c-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab88c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab88c-111">See Also</span></span>  
 [<span data-ttu-id="ab88c-112">PLINQ 和 TPL 的自訂 Partitioner</span><span class="sxs-lookup"><span data-stu-id="ab88c-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="ab88c-113">操作說明：為靜態分割實作 Partitioner</span><span class="sxs-lookup"><span data-stu-id="ab88c-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
