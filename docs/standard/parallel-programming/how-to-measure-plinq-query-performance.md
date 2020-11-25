---
title: 作法：測量 PLINQ 查詢效能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 2cbd178d5004d28120ab701a777a474a7e78e09e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734435"
---
# <a name="how-to-measure-plinq-query-performance"></a>作法：測量 PLINQ 查詢效能

此範例示範如何使用 <xref:System.Diagnostics.Stopwatch> 類別來測量 PLINQ 查詢執行所需的時間。  
  
## <a name="example"></a>範例  

 這個範例會使用空的 `foreach` 迴圈 (在 Visual Basic 中為 `For Each`) 來測量執行查詢所需的時間。 在真實的程式碼中，迴圈通常包含會增加查詢執行總時間的額外處理步驟。 請注意，在迴圈之前，不會啟動碼錶，因為這是查詢執行開始的時間。 如果您需要更精細的測量，您可以使用 `ElapsedTicks` 屬性而非 `ElapsedMilliseconds`。  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 當您試驗查詢執行時，總執行時間是有用的度量，但它不一定會告訴整個案例。 若要取得更深入且更豐富的查詢執行緒互動，以及其他執行中進程的互動，請使用 [並行視覺化](/visualstudio/profiling/concurrency-visualizer)效果。  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](introduction-to-plinq.md)
