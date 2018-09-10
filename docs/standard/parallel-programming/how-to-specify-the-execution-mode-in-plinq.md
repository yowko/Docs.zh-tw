---
title: 如何：在 PLINQ 中指定執行模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85731b991399e92297d6109a3000c1e345e02f6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087203"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="7f576-102">如何：在 PLINQ 中指定執行模式</span><span class="sxs-lookup"><span data-stu-id="7f576-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="7f576-103">這個範例示範如何強制 PLINQ 略過其預設啟發學習法並以平行方式處理查詢，而不考慮查詢的種類。</span><span class="sxs-lookup"><span data-stu-id="7f576-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="7f576-104">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="7f576-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="7f576-105">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="7f576-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f576-106">範例</span><span class="sxs-lookup"><span data-stu-id="7f576-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="7f576-107">PLINQ 的設計，是要利用可以平行處理的機會。</span><span class="sxs-lookup"><span data-stu-id="7f576-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="7f576-108">不過，並非所有查詢都適合平行執行。</span><span class="sxs-lookup"><span data-stu-id="7f576-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="7f576-109">例如，當查詢包含工作極少的單一使用者委派時，循序執行查詢通常會更快。</span><span class="sxs-lookup"><span data-stu-id="7f576-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="7f576-110">這是因為啟用平行執行的額外負荷所耗用的資源高於增加的速度。</span><span class="sxs-lookup"><span data-stu-id="7f576-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="7f576-111">因此，PLINQ 不會自動平行處理每個查詢。</span><span class="sxs-lookup"><span data-stu-id="7f576-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="7f576-112">它會先檢查查詢的種類，和組成查詢的各個運算子。</span><span class="sxs-lookup"><span data-stu-id="7f576-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="7f576-113">根據這項分析，預設執行模式的 PLINQ 就能決定要循序執行部分或所有的查詢。</span><span class="sxs-lookup"><span data-stu-id="7f576-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="7f576-114">不過，在某些情況下，您所能得知的查詢資訊，不僅僅是 PLINQ 能夠從其分析中判斷的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f576-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="7f576-115">例如，您可能知道委派相當耗費資源，因此查詢明確地適合平行處理。</span><span class="sxs-lookup"><span data-stu-id="7f576-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="7f576-116">在這種情況下，您可以使用 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>方法並指定 <xref:System.Linq.ParallelExecutionMode.ForceParallelism> 值，指示 PLINQ 永遠以平行方式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="7f576-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f576-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7f576-117">Compiling the Code</span></span>  
 <span data-ttu-id="7f576-118">將此程式碼剪下並貼到 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)，並從 `Main` 呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="7f576-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f576-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f576-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
- [<span data-ttu-id="7f576-120">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7f576-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
