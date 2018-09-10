---
title: 如何：取消 Parallel.For 或 ForEach 迴圈
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db0ff4cbc343cfbc1c81b24aa4401fa00ecf4f4b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44199384"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="6f022-102">如何：取消 Parallel.For 或 ForEach 迴圈</span><span class="sxs-lookup"><span data-stu-id="6f022-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="6f022-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 方法可透過使用取消權杖來支援取消作業。</span><span class="sxs-lookup"><span data-stu-id="6f022-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="6f022-104">如需取消的詳細資訊，請參閱[取消](../../../docs/standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="6f022-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="6f022-105">在平行迴圈中，將 <xref:System.Threading.CancellationToken> 提供給 <xref:System.Threading.Tasks.ParallelOptions> 參數中的方法，然後將平行呼叫包含在 try catch 區塊中。</span><span class="sxs-lookup"><span data-stu-id="6f022-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f022-106">範例</span><span class="sxs-lookup"><span data-stu-id="6f022-106">Example</span></span>  
 <span data-ttu-id="6f022-107">下列範例將示範如何取消呼叫 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6f022-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6f022-108">您可以套用相同的方法到 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f022-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="6f022-109">如果通知取消的權杖和 <xref:System.Threading.Tasks.ParallelOptions> 執行個體中指定的權杖相同，則平行迴圈在取消時將擲回單一 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="6f022-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="6f022-110">如果是其他權杖導致取消，迴圈將會擲回<xref:System.AggregateException>，而其中的 <xref:System.OperationCanceledException> 是 InnerException。</span><span class="sxs-lookup"><span data-stu-id="6f022-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f022-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f022-111">See also</span></span>

- [<span data-ttu-id="6f022-112">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="6f022-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [<span data-ttu-id="6f022-113">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="6f022-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
