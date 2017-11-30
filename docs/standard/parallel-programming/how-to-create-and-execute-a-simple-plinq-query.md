---
title: "如何：建立並執行簡單的 PLINQ 查詢"
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
helpviewer_keywords: PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a99eedc05bbf8d4dcd58e46b484bd57c29f70886
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="eb65a-102">如何：建立並執行簡單的 PLINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="eb65a-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="eb65a-103">下列範例說明如何在來源序列上使用 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> 擴充方法建立簡易平行 LINQ 查詢，以及如何使用 <xref:System.Linq.ParallelEnumerable.ForAll%2A> 方法執行查詢。</span><span class="sxs-lookup"><span data-stu-id="eb65a-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb65a-104">本文件使用 Lambda 運算式來定義 PLINQ 中的委派。</span><span class="sxs-lookup"><span data-stu-id="eb65a-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="eb65a-105">如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="eb65a-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb65a-106">範例</span><span class="sxs-lookup"><span data-stu-id="eb65a-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="eb65a-107">這個範例示範在結果序列的順序不重要時，用以建立及執行任何平行 LINQ 查詢的基本模式；未排序的查詢通常比排序的查詢快。</span><span class="sxs-lookup"><span data-stu-id="eb65a-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="eb65a-108">查詢會將來源分割成在多個執行緒上非同步執行的工作。</span><span class="sxs-lookup"><span data-stu-id="eb65a-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="eb65a-109">每項工作的完成順序不僅取決於處理分割中的項目時所涉及的工作量，也取決於一些外部因素，例如作業系統排程每個執行緒的方式。</span><span class="sxs-lookup"><span data-stu-id="eb65a-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="eb65a-110">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="eb65a-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="eb65a-111">提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="eb65a-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="eb65a-112">如需如何保留在查詢中的項目順序的詳細資訊，請參閱[如何： 控制 PLINQ 查詢中所訂購](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="eb65a-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb65a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb65a-113">See Also</span></span>  
 [<span data-ttu-id="eb65a-114">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="eb65a-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
