---
title: 如何：測量 PLINQ 查詢效能
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211628"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="3012f-102">如何：測量 PLINQ 查詢效能</span><span class="sxs-lookup"><span data-stu-id="3012f-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="3012f-103">這個範例示範如何使用 <xref:System.Diagnostics.Stopwatch> 類別，測量執行 PLINQ 查詢所需的時間。</span><span class="sxs-lookup"><span data-stu-id="3012f-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3012f-104">範例</span><span class="sxs-lookup"><span data-stu-id="3012f-104">Example</span></span>  
 <span data-ttu-id="3012f-105">這個範例會使用空的 `foreach` 迴圈 (在 Visual Basic 中為 `For Each`) 來測量執行查詢所需的時間。</span><span class="sxs-lookup"><span data-stu-id="3012f-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="3012f-106">在真實的程式碼中，迴圈通常包含會增加查詢執行總時間的額外處理步驟。</span><span class="sxs-lookup"><span data-stu-id="3012f-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="3012f-107">請注意，碼錶不會在迴圈之前啟動，因為迴圈就是執行查詢開始的時間。</span><span class="sxs-lookup"><span data-stu-id="3012f-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="3012f-108">如果您需要更精細的測量，您可以使用 `ElapsedTicks` 屬性而非 `ElapsedMilliseconds`。</span><span class="sxs-lookup"><span data-stu-id="3012f-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="3012f-109">當您試驗查詢實作時，總執行時間是很有用的計量，但不一定能反映全貌。</span><span class="sxs-lookup"><span data-stu-id="3012f-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="3012f-110">若要取得查詢執行緒彼此之間以及與其他執行中處理序的更深入、更豐富互動檢視，請使用 [並行視覺化檢視]。</span><span class="sxs-lookup"><span data-stu-id="3012f-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="3012f-111">如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。</span><span class="sxs-lookup"><span data-stu-id="3012f-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3012f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3012f-112">See also</span></span>

- [<span data-ttu-id="3012f-113">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3012f-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
