---
title: "如何：測量 PLINQ 查詢效能"
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
helpviewer_keywords: PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03432e70454cb6203e55e340111a6cb7efe62dc4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="3e413-102">如何：測量 PLINQ 查詢效能</span><span class="sxs-lookup"><span data-stu-id="3e413-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="3e413-103">這個範例示範如何使用<xref:System.Diagnostics.Stopwatch>類別以測量 PLINQ 查詢執行所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="3e413-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e413-104">範例</span><span class="sxs-lookup"><span data-stu-id="3e413-104">Example</span></span>  
 <span data-ttu-id="3e413-105">這個範例會使用空的 `foreach` 迴圈 (在 Visual Basic 中為 `For Each`) 來測量執行查詢所需的時間。</span><span class="sxs-lookup"><span data-stu-id="3e413-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="3e413-106">在真實的程式碼中，迴圈通常包含會增加查詢執行總時間的額外處理步驟。</span><span class="sxs-lookup"><span data-stu-id="3e413-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="3e413-107">請注意，碼錶不會在迴圈之前啟動，因為迴圈就是執行查詢開始的時間。</span><span class="sxs-lookup"><span data-stu-id="3e413-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="3e413-108">如果您需要更精細的測量，您可以使用 `ElapsedTicks` 屬性而非 `ElapsedMilliseconds`。</span><span class="sxs-lookup"><span data-stu-id="3e413-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="3e413-109">當您試驗查詢實作時，總執行時間是很有用的計量，但不一定能反映全貌。</span><span class="sxs-lookup"><span data-stu-id="3e413-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="3e413-110">若要取得查詢執行緒彼此之間以及與其他執行中處理序的更深入、更豐富互動檢視，請使用 [並行視覺化檢視]。</span><span class="sxs-lookup"><span data-stu-id="3e413-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="3e413-111">如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。</span><span class="sxs-lookup"><span data-stu-id="3e413-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e413-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e413-112">See Also</span></span>  
 [<span data-ttu-id="3e413-113">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3e413-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
