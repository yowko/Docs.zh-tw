---
title: 作法：結合平行和循序 LINQ 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: e851c6d72a5fd932c065368b893b907d7820c918
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827096"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="abdfb-102">作法：結合平行和循序 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="abdfb-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>

<span data-ttu-id="abdfb-103">此範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法來指示 PLINQ 循序處理查詢中所有後續的運算子。</span><span class="sxs-lookup"><span data-stu-id="abdfb-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="abdfb-104">雖然連續處理的速度通常會比平行處理慢，但有時需要產生正確的結果。</span><span class="sxs-lookup"><span data-stu-id="abdfb-104">Although sequential processing is often slower than parallel, sometimes it's necessary to produce correct results.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abdfb-105">此範例的目的是要示範使用方式，而且執行速度可能會比對等的連續 LINQ to Objects 查詢更快。</span><span class="sxs-lookup"><span data-stu-id="abdfb-105">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="abdfb-106">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="abdfb-106">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abdfb-107">範例</span><span class="sxs-lookup"><span data-stu-id="abdfb-107">Example</span></span>  
 <span data-ttu-id="abdfb-108">下列範例示範必須使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的案例，也就是要保留先前的查詢子句中所建立的順序。</span><span class="sxs-lookup"><span data-stu-id="abdfb-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="abdfb-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="abdfb-109">Compiling the Code</span></span>  
 <span data-ttu-id="abdfb-110">若要編譯和執行此程式碼，請將它貼到 [ [PLINQ 資料範例](plinq-data-sample.md) ] 專案中，加入從呼叫方法的行 `Main` ，然後按下 **F5**。</span><span class="sxs-lookup"><span data-stu-id="abdfb-110">To compile and run this code, paste it into the [PLINQ Data Sample](plinq-data-sample.md) project, add a line to call the method from `Main`, and press **F5**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abdfb-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="abdfb-111">See also</span></span>

- [<span data-ttu-id="abdfb-112">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="abdfb-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
