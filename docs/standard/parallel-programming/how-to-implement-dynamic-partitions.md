---
title: 作法：實作動態分割
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5719c6afc1c5efc6138f0a4931d1725a6f20909a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424046"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="0f305-102">作法：實作動態分割</span><span class="sxs-lookup"><span data-stu-id="0f305-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="0f305-103">下列範例示範如何實作自訂 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>，它會實作動態分割，並可從特定多載 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 和 PLINQ 使用。</span><span class="sxs-lookup"><span data-stu-id="0f305-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f305-104">範例</span><span class="sxs-lookup"><span data-stu-id="0f305-104">Example</span></span>

<span data-ttu-id="0f305-105">每次分割區在列舉程式上呼叫 <xref:System.Collections.IEnumerator.MoveNext%2A> 時，列舉程式就會提供一個清單元素給分割區。</span><span class="sxs-lookup"><span data-stu-id="0f305-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="0f305-106">在 PLINQ 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 的案例中，分割區是 <xref:System.Threading.Tasks.Task> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0f305-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="0f305-107">由於要求是在多個執行緒上同時發生，因而也會同步存取目前的索引。</span><span class="sxs-lookup"><span data-stu-id="0f305-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="0f305-108">這是區塊分割的範例，其中每個區塊包含一個元素。</span><span class="sxs-lookup"><span data-stu-id="0f305-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="0f305-109">藉由一次提供更多元素，可以減少鎖定競爭，理論上可以實現更快的效能。</span><span class="sxs-lookup"><span data-stu-id="0f305-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="0f305-110">不過，在某些時候，較大的區塊可能需要額外的負載平衡邏輯，才能在所有工作完成前使所有執行緒保持忙碌。</span><span class="sxs-lookup"><span data-stu-id="0f305-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f305-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f305-111">See also</span></span>

* [<span data-ttu-id="0f305-112">PLINQ 和 TPL 的自訂 Partitioner</span><span class="sxs-lookup"><span data-stu-id="0f305-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="0f305-113">如何：為靜態分割實作 Partitioner</span><span class="sxs-lookup"><span data-stu-id="0f305-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
