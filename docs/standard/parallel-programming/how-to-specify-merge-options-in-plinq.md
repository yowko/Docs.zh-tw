---
title: HOW TO：在 PLINQ 中指定合併選項
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87079337ae3cea81dbb4aab13ec2043b74498d9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573565"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="490ab-102">HOW TO：在 PLINQ 中指定合併選項</span><span class="sxs-lookup"><span data-stu-id="490ab-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="490ab-103">此範例示範如何指定將套用到 PLINQ 查詢中所有後續運算子的合併選項。</span><span class="sxs-lookup"><span data-stu-id="490ab-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="490ab-104">您不需明確地設定合併選項，但這樣做可改善效能。</span><span class="sxs-lookup"><span data-stu-id="490ab-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="490ab-105">如需合併選項的詳細資訊，請參閱 [PLINQ 中的合併選項](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="490ab-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="490ab-106">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="490ab-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="490ab-107">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="490ab-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="490ab-108">範例</span><span class="sxs-lookup"><span data-stu-id="490ab-108">Example</span></span>  
 <span data-ttu-id="490ab-109">下列範例示範具有未排序來源之基本案例中的合併選項行為，並將高度耗費資源的函式套用至每個元素。</span><span class="sxs-lookup"><span data-stu-id="490ab-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="490ab-110">如果 <xref:System.Linq.ParallelMergeOptions.AutoBuffered> 在產生第一個元素前造成非預期的延遲，請試用 <xref:System.Linq.ParallelMergeOptions.NotBuffered> 選項，以更快且更順暢的方式產生結果元素。</span><span class="sxs-lookup"><span data-stu-id="490ab-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490ab-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="490ab-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="490ab-112">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="490ab-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
