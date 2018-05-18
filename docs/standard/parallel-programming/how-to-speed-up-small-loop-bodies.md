---
title: 如何：加速小型迴圈主體
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bff41416dd2263c185cc94de045b2c8a26ea194d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-speed-up-small-loop-bodies"></a>如何：加速小型迴圈主體
當 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 迴圈有小型的主體時，其執行速度可能會比同等的循序迴圈更慢，例如 C# 中的 [for](~/docs/csharp/language-reference/keywords/for.md) 迴圈和 Visual Basic 中的 [For](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) 迴圈。 效能較慢的起因是分割資料時相關的負擔，以及在每次迴圈反覆運算上叫用委派的成本。 為了解決這類情況，<xref:System.Collections.Concurrent.Partitioner> 類別提供 <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> 方法，可讓您提供循序迴圈給委派主體，讓每個資料分割只叫用一次委派，而不會每個反覆項目叫用一次。 如需詳細資訊，請參閱 [PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 在此範例中示範的方法適用於迴圈執行最少量工作的情況。 當工作變得更運算密集時，藉由使用 <xref:System.Threading.Tasks.Parallel.For%2A> 或 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈與預設 Partitioner，您可能會取得相同或更高的效能。  
  
## <a name="see-also"></a>請參閱  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [迭代器](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
