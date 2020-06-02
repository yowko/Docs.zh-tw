---
title: 作法：在 PLINQ 中指定執行模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 39ccde003b60ac9cbcff7ab824103a9cf37cc453
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288091"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="324a0-102">作法：在 PLINQ 中指定執行模式</span><span class="sxs-lookup"><span data-stu-id="324a0-102">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="324a0-103">這個範例示範如何強制 PLINQ 略過其預設啟發學習法並以平行方式處理查詢，而不考慮查詢的種類。</span><span class="sxs-lookup"><span data-stu-id="324a0-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="324a0-104">這個範例的目的是要示範使用方式，而且其執行速度可能會比對等的順序 LINQ to Objects 查詢更快。</span><span class="sxs-lookup"><span data-stu-id="324a0-104">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="324a0-105">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="324a0-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="324a0-106">範例</span><span class="sxs-lookup"><span data-stu-id="324a0-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="324a0-107">PLINQ 的設計，是要利用可以平行處理的機會。</span><span class="sxs-lookup"><span data-stu-id="324a0-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="324a0-108">不過，並非所有查詢都適合平行執行。</span><span class="sxs-lookup"><span data-stu-id="324a0-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="324a0-109">例如，當查詢包含的單一使用者委派沒有足夠的效果時，查詢通常會以較快的循序執行。</span><span class="sxs-lookup"><span data-stu-id="324a0-109">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="324a0-110">連續執行的速度較快，因為啟用平行執行所涉及的額外負荷比取得的加速更昂貴。</span><span class="sxs-lookup"><span data-stu-id="324a0-110">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="324a0-111">因此，PLINQ 不會自動平行處理每個查詢。</span><span class="sxs-lookup"><span data-stu-id="324a0-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="324a0-112">它會先檢查查詢的種類，和組成查詢的各個運算子。</span><span class="sxs-lookup"><span data-stu-id="324a0-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="324a0-113">根據這項分析，預設執行模式的 PLINQ 就能決定要循序執行部分或所有的查詢。</span><span class="sxs-lookup"><span data-stu-id="324a0-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="324a0-114">不過，在某些情況下，您所能得知的查詢資訊，不僅僅是 PLINQ 能夠從其分析中判斷的資訊。</span><span class="sxs-lookup"><span data-stu-id="324a0-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="324a0-115">例如，您可能知道委派的成本很高，而且查詢一定會受益于平行處理。</span><span class="sxs-lookup"><span data-stu-id="324a0-115">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="324a0-116">在這種情況下，您可以使用 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>方法並指定 <xref:System.Linq.ParallelExecutionMode.ForceParallelism> 值，指示 PLINQ 永遠以平行方式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="324a0-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="324a0-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="324a0-117">Compiling the Code</span></span>  
 <span data-ttu-id="324a0-118">將此程式碼剪下並貼到 [PLINQ 資料範例](plinq-data-sample.md)，並從 `Main` 呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="324a0-118">Cut and paste this code into the [PLINQ Data Sample](plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324a0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="324a0-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="324a0-120">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="324a0-120">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
