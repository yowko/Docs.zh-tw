---
title: "如何：在 PLINQ 中指定執行模式"
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
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 745ceae9832582c7b66a56075d128f9cf1c8ff69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="582d3-102">如何：在 PLINQ 中指定執行模式</span><span class="sxs-lookup"><span data-stu-id="582d3-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="582d3-103">這個範例示範如何強制 PLINQ 略過其預設啟發學習法，不論查詢的圖形的查詢平行處理。</span><span class="sxs-lookup"><span data-stu-id="582d3-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="582d3-104">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="582d3-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="582d3-105">提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="582d3-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="582d3-106">範例</span><span class="sxs-lookup"><span data-stu-id="582d3-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="582d3-107">PLINQ 被為了利用平行處理的機會。</span><span class="sxs-lookup"><span data-stu-id="582d3-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="582d3-108">不過，並非所有的查詢平行執行而受益。</span><span class="sxs-lookup"><span data-stu-id="582d3-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="582d3-109">例如，當查詢包含非常少運作的單一使用者委派，查詢將通常更快依序執行。</span><span class="sxs-lookup"><span data-stu-id="582d3-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="582d3-110">這是因為參與啟用平行執行的額外負荷成本高於所取得的加速效果。</span><span class="sxs-lookup"><span data-stu-id="582d3-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="582d3-111">因此，PLINQ 不會自動平行處理每個查詢。</span><span class="sxs-lookup"><span data-stu-id="582d3-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="582d3-112">它會先檢查查詢和各種運算子組成的圖形。</span><span class="sxs-lookup"><span data-stu-id="582d3-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="582d3-113">根據這項分析，PLINQ 的預設執行模式中可能會決定要循序執行部分或所有的查詢。</span><span class="sxs-lookup"><span data-stu-id="582d3-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="582d3-114">不過，在某些情況下您可能知道更多查詢的相關比 PLINQ 能夠從其分析判斷。</span><span class="sxs-lookup"><span data-stu-id="582d3-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="582d3-115">例如，您可能知道委派是相當耗費資源，並確認此查詢會明確地受益於平行處理。</span><span class="sxs-lookup"><span data-stu-id="582d3-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="582d3-116">在這種情況下，您可以使用<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>方法並指定<xref:System.Linq.ParallelExecutionMode.ForceParallelism>值，指示 PLINQ 永遠以平行方式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="582d3-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="582d3-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="582d3-117">Compiling the Code</span></span>  
 <span data-ttu-id="582d3-118">剪下並貼到這個程式碼[PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)呼叫此方法從`Main`。</span><span class="sxs-lookup"><span data-stu-id="582d3-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582d3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="582d3-119">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [<span data-ttu-id="582d3-120">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="582d3-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
