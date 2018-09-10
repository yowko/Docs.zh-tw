---
title: 如何：結合平行和循序 LINQ 查詢
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fd67d5f0cb5af33dc2b79f86148557a0dca6ec4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273641"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="932a5-102">如何：結合平行和循序 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="932a5-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="932a5-103">此範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法來指示 PLINQ 循序處理查詢中所有後續的運算子。</span><span class="sxs-lookup"><span data-stu-id="932a5-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="932a5-104">雖然循序處理的速度通常比平行處理慢，但有時為了產生正確結果卻是必要的。</span><span class="sxs-lookup"><span data-stu-id="932a5-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="932a5-105">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="932a5-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="932a5-106">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="932a5-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="932a5-107">範例</span><span class="sxs-lookup"><span data-stu-id="932a5-107">Example</span></span>  
 <span data-ttu-id="932a5-108">下列範例示範必須使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的案例，也就是要保留先前的查詢子句中所建立的順序。</span><span class="sxs-lookup"><span data-stu-id="932a5-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="932a5-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="932a5-109">Compiling the Code</span></span>  
 <span data-ttu-id="932a5-110">若要編譯及執行此程式碼，請將它貼入 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案，加入從 `Main` 呼叫方法一行，然後按 F5 鍵。</span><span class="sxs-lookup"><span data-stu-id="932a5-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="932a5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="932a5-111">See also</span></span>

- [<span data-ttu-id="932a5-112">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="932a5-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
