---
title: "如何：為靜態分割實作 Partitioner"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b28ff0bb8436fefc4956918889435e258ae98b12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="8adec-102">如何：為靜態分割實作 Partitioner</span><span class="sxs-lookup"><span data-stu-id="8adec-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="8adec-103">下列範例會示範如何實作簡單的自訂 partitioner 的 PLINQ 執行靜態分割。</span><span class="sxs-lookup"><span data-stu-id="8adec-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="8adec-104">Partitioner 不支援動態磁碟分割，因為它不是您可以從使用<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8adec-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8adec-105">這個特定的 partitioner 可能會針對每個項目需要處理時間增加量的資料來源，以提供透過預設範圍 partitioner 加速。</span><span class="sxs-lookup"><span data-stu-id="8adec-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8adec-106">範例</span><span class="sxs-lookup"><span data-stu-id="8adec-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="8adec-107">在此範例中的資料分割為基礎的假設的每個項目的處理時間的線性增加。</span><span class="sxs-lookup"><span data-stu-id="8adec-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="8adec-108">在真實世界中，可能很難預測處理時間，以這種方式。</span><span class="sxs-lookup"><span data-stu-id="8adec-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="8adec-109">如果您正在使用特定資料來源的靜態 partitioner，您可以最佳化的來源資料分割的公式，加入負載平衡的邏輯，或使用區塊 (chunk) 中所示，資料分割方法[How to： 實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="8adec-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8adec-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8adec-110">See Also</span></span>  
 [<span data-ttu-id="8adec-111">PLINQ 和 TPL 的自訂 Partitioner</span><span class="sxs-lookup"><span data-stu-id="8adec-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
