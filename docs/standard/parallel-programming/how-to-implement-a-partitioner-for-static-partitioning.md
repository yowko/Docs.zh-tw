---
title: 如何：為靜態分割實作 Partitioner
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 302d7d98d04e528d205edf38c3fa13bb3f2b2252
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863069"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="06420-102">如何：為靜態分割實作 Partitioner</span><span class="sxs-lookup"><span data-stu-id="06420-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="06420-103">下列範例示範如何為執行靜態分割的 PLINQ 實作簡單的自訂 Partitioner。</span><span class="sxs-lookup"><span data-stu-id="06420-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="06420-104">Partitioner 不支援動態分割，因此無法從 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 中使用。</span><span class="sxs-lookup"><span data-stu-id="06420-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="06420-105">對於每個元素需要增加處理時間量的資料來源，這個特定 Partitioner 的執行速度可能會比預設的範圍 Partitioner 來得快。</span><span class="sxs-lookup"><span data-stu-id="06420-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06420-106">範例</span><span class="sxs-lookup"><span data-stu-id="06420-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="06420-107">對於此範例中的分割區，我們假設每個元素的處理時間以線性增加。</span><span class="sxs-lookup"><span data-stu-id="06420-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="06420-108">在真實世界中，可能很難以這種方式來預測處理時間。</span><span class="sxs-lookup"><span data-stu-id="06420-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="06420-109">如果您正在使用包含特定資料來源的靜態 Partitioner，您可以最佳化來源的分割公式、加入負載平衡邏輯，或使用[如何： 實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)中示範的區塊分割方法。</span><span class="sxs-lookup"><span data-stu-id="06420-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06420-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06420-110">See also</span></span>

- [<span data-ttu-id="06420-111">PLINQ 和 TPL 的自訂 Partitioner</span><span class="sxs-lookup"><span data-stu-id="06420-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
