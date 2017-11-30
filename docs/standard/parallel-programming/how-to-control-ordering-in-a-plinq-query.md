---
title: "如何：控制 PLINQ 查詢中的順序"
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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="73f7f-102">如何：控制 PLINQ 查詢中的順序</span><span class="sxs-lookup"><span data-stu-id="73f7f-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="73f7f-103">這些範例示範如何控制順序 PLINQ 查詢中使用<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>擴充方法。</span><span class="sxs-lookup"><span data-stu-id="73f7f-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="73f7f-104">這些範例主要為了示範用法，並可能或可能未執行速度比不上對應的循序 LINQ to 物件查詢。</span><span class="sxs-lookup"><span data-stu-id="73f7f-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73f7f-105">範例</span><span class="sxs-lookup"><span data-stu-id="73f7f-105">Example</span></span>  
 <span data-ttu-id="73f7f-106">下列範例會保留來源序列中的順序。</span><span class="sxs-lookup"><span data-stu-id="73f7f-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="73f7f-107">這有時是必要的;比方說有些查詢運算子需要已排序的來源序列產生正確的結果。</span><span class="sxs-lookup"><span data-stu-id="73f7f-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="73f7f-108">範例</span><span class="sxs-lookup"><span data-stu-id="73f7f-108">Example</span></span>  
 <span data-ttu-id="73f7f-109">下列範例會示範部分查詢可能預期來排序其來源序列的運算子。</span><span class="sxs-lookup"><span data-stu-id="73f7f-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="73f7f-110">這些運算子將適用於未排序的順序，但它們可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="73f7f-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="73f7f-111">若要執行這個方法，將它貼到中的 PLINQDataSample 類別[PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案，然後按 f5 鍵。</span><span class="sxs-lookup"><span data-stu-id="73f7f-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73f7f-112">範例</span><span class="sxs-lookup"><span data-stu-id="73f7f-112">Example</span></span>  
 <span data-ttu-id="73f7f-113">下列範例會示範如何保留順序的第一個查詢的一部份，然後移除排序來增加效能的 join 子句中，然後重新套用至最終結果的順序排序。</span><span class="sxs-lookup"><span data-stu-id="73f7f-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="73f7f-114">若要執行這個方法，將它貼到中的 PLINQDataSample 類別[PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案，然後按 f5 鍵。</span><span class="sxs-lookup"><span data-stu-id="73f7f-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f7f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73f7f-115">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="73f7f-116">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="73f7f-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
