---
title: 如何：控制 PLINQ 查詢中的順序
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e0abf711730326b6391184a2e3a1b55b303957
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="8fb84-102">如何：控制 PLINQ 查詢中的順序</span><span class="sxs-lookup"><span data-stu-id="8fb84-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="8fb84-103">這些範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 擴充方法來控制 PLINQ 查詢中的順序。</span><span class="sxs-lookup"><span data-stu-id="8fb84-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8fb84-104">這些範例主要是為了示範用法，執行速度可能比對應的循序 LINQ to Objects 查詢快或慢。</span><span class="sxs-lookup"><span data-stu-id="8fb84-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fb84-105">範例</span><span class="sxs-lookup"><span data-stu-id="8fb84-105">Example</span></span>  
 <span data-ttu-id="8fb84-106">下列範例會保留來源序列中的順序。</span><span class="sxs-lookup"><span data-stu-id="8fb84-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="8fb84-107">這有時是必要的；比方說，有些查詢運算子需要已排序的來源序列才能產生正確結果。</span><span class="sxs-lookup"><span data-stu-id="8fb84-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="8fb84-108">範例</span><span class="sxs-lookup"><span data-stu-id="8fb84-108">Example</span></span>  
 <span data-ttu-id="8fb84-109">下列範例示範來源序列可能會排序的部分查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="8fb84-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="8fb84-110">這些運算子將處理未排序的順序，但它們可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="8fb84-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="8fb84-111">若要執行此方法，請將它貼到 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中的 PLINQDataSample 類別，然後按 F5 鍵。</span><span class="sxs-lookup"><span data-stu-id="8fb84-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fb84-112">範例</span><span class="sxs-lookup"><span data-stu-id="8fb84-112">Example</span></span>  
 <span data-ttu-id="8fb84-113">下列範例示範如何保留查詢第一個部分的順序，然後移除順序以增加 join 子句的效能，再重新套用順序至最終結果順序。</span><span class="sxs-lookup"><span data-stu-id="8fb84-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="8fb84-114">若要執行此方法，請將它貼到 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中的 PLINQDataSample 類別，然後按 F5 鍵。</span><span class="sxs-lookup"><span data-stu-id="8fb84-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb84-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="8fb84-115">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="8fb84-116">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="8fb84-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
