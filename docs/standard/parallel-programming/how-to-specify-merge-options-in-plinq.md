---
title: "如何：在 PLINQ 中指定合併選項"
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
helpviewer_keywords: PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec601e8bbefd31650fb91c438b032942cfc93101
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="42b0a-102">如何：在 PLINQ 中指定合併選項</span><span class="sxs-lookup"><span data-stu-id="42b0a-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="42b0a-103">這個範例示範如何指定將套用到所有後續的運算子 PLINQ 查詢中的合併選項。</span><span class="sxs-lookup"><span data-stu-id="42b0a-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="42b0a-104">您沒有明確地設定合併選項，但這樣做可改善效能。</span><span class="sxs-lookup"><span data-stu-id="42b0a-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="42b0a-105">如需合併選項的詳細資訊，請參閱[PLINQ 中的合併選項](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="42b0a-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="42b0a-106">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="42b0a-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="42b0a-107">提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="42b0a-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42b0a-108">範例</span><span class="sxs-lookup"><span data-stu-id="42b0a-108">Example</span></span>  
 <span data-ttu-id="42b0a-109">下列範例示範基本的案例中具有未排序的來源，並將高度耗費資源的函式套用每個項目中的合併選項的行為。</span><span class="sxs-lookup"><span data-stu-id="42b0a-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="42b0a-110">萬一其中<xref:System.Linq.ParallelMergeOptions.AutoBuffered>選項會造成非預期的延遲，才能產生第一個項目時，請嘗試<xref:System.Linq.ParallelMergeOptions.NotBuffered>選項來產生結果項目，更快速且更順暢。</span><span class="sxs-lookup"><span data-stu-id="42b0a-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b0a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42b0a-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="42b0a-112">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="42b0a-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
