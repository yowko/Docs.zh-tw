---
title: 作法：測量 PLINQ 查詢效能
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: f240b2c275305aec5699eb42406e0689925490a8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288182"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="03783-102">作法：測量 PLINQ 查詢效能</span><span class="sxs-lookup"><span data-stu-id="03783-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="03783-103">這個範例示範如何使用 <xref:System.Diagnostics.Stopwatch> 類別來測量 PLINQ 查詢執行所需的時間。</span><span class="sxs-lookup"><span data-stu-id="03783-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03783-104">範例</span><span class="sxs-lookup"><span data-stu-id="03783-104">Example</span></span>  
 <span data-ttu-id="03783-105">這個範例會使用空的 `foreach` 迴圈 (在 Visual Basic 中為 `For Each`) 來測量執行查詢所需的時間。</span><span class="sxs-lookup"><span data-stu-id="03783-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="03783-106">在真實的程式碼中，迴圈通常包含會增加查詢執行總時間的額外處理步驟。</span><span class="sxs-lookup"><span data-stu-id="03783-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="03783-107">請注意，只有在迴圈之前才會啟動碼錶，因為這是查詢執行開始的時間。</span><span class="sxs-lookup"><span data-stu-id="03783-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="03783-108">如果您需要更精細的測量，您可以使用 `ElapsedTicks` 屬性而非 `ElapsedMilliseconds`。</span><span class="sxs-lookup"><span data-stu-id="03783-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="03783-109">當您試驗查詢執行時，總執行時間是有用的度量，但它不一定會告訴整個案例。</span><span class="sxs-lookup"><span data-stu-id="03783-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="03783-110">若要更深入且更豐富地查看查詢執行緒與其他執行中進程之間的互動，請使用[並行視覺化](/visualstudio/profiling/concurrency-visualizer)效果。</span><span class="sxs-lookup"><span data-stu-id="03783-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03783-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03783-111">See also</span></span>

- [<span data-ttu-id="03783-112">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="03783-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
