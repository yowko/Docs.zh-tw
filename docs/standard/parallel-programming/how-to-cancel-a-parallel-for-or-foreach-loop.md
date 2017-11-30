---
title: "如何：取消 Parallel.For 或 ForEach 迴圈"
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
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="802a3-102">如何：取消 Parallel.For 或 ForEach 迴圈</span><span class="sxs-lookup"><span data-stu-id="802a3-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="802a3-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>和<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>方法使用支援取消作業取消語彙基元。</span><span class="sxs-lookup"><span data-stu-id="802a3-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="802a3-104">如需有關取消一般情況下，請參閱[取消](../../../docs/standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="802a3-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="802a3-105">在平行迴圈中，您提供<xref:System.Threading.CancellationToken>中方法<xref:System.Threading.Tasks.ParallelOptions>參數並再將平行呼叫括在 try catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="802a3-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="802a3-106">範例</span><span class="sxs-lookup"><span data-stu-id="802a3-106">Example</span></span>  
 <span data-ttu-id="802a3-107">下列範例示範如何取消呼叫<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="802a3-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="802a3-108">您可以套用至相同的方法<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>呼叫。</span><span class="sxs-lookup"><span data-stu-id="802a3-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="802a3-109">如果通知取消語彙基元相同語彙基元中指定<xref:System.Threading.Tasks.ParallelOptions>執行個體，則平行迴圈，將會擲回單一<xref:System.OperationCanceledException>上取消作業。</span><span class="sxs-lookup"><span data-stu-id="802a3-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="802a3-110">如果其他語彙基元會導致取消，迴圈將會擲回<xref:System.AggregateException>與<xref:System.OperationCanceledException>為 InnerException。</span><span class="sxs-lookup"><span data-stu-id="802a3-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="802a3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="802a3-111">See Also</span></span>  
 [<span data-ttu-id="802a3-112">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="802a3-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="802a3-113">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="802a3-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
