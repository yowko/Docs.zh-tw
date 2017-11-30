---
title: "如何：結合平行和循序 LINQ 查詢"
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
helpviewer_keywords: parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4da91ff535059b181baa637164a854cd75d06334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="21c67-102">如何：結合平行和循序 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="21c67-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="21c67-103">這個範例示範如何使用<xref:System.Linq.ParallelEnumerable.AsSequential%2A>指示 PLINQ 查詢中的所有後續運算子會循序處理方法。</span><span class="sxs-lookup"><span data-stu-id="21c67-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="21c67-104">雖然通常低於平行循序處理，但有時候很需要產生正確的結果。</span><span class="sxs-lookup"><span data-stu-id="21c67-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="21c67-105">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="21c67-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="21c67-106">提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="21c67-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21c67-107">範例</span><span class="sxs-lookup"><span data-stu-id="21c67-107">Example</span></span>  
 <span data-ttu-id="21c67-108">下列範例顯示在其中一個案例<xref:System.Linq.ParallelEnumerable.AsSequential%2A>為必要項，也就是要保留先前的查詢子句中已建立的順序。</span><span class="sxs-lookup"><span data-stu-id="21c67-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="21c67-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="21c67-109">Compiling the Code</span></span>  
 <span data-ttu-id="21c67-110">若要編譯及執行此程式碼，將它貼入[PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中，加入一行呼叫的方法，從`Main`，然後按 f5 鍵。</span><span class="sxs-lookup"><span data-stu-id="21c67-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c67-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21c67-111">See Also</span></span>  
 [<span data-ttu-id="21c67-112">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="21c67-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
