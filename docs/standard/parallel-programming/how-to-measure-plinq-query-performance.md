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
ms.openlocfilehash: 37bd3bc464f719876b2fe13ee1a11ebca4339988
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635821"
---
# <a name="how-to-measure-plinq-query-performance"></a>如何：測量 PLINQ 查詢效能

此示例演示如何使用<xref:System.Diagnostics.Stopwatch>類來衡量 PLINQ 查詢執行所需的時間。  
  
## <a name="example"></a>範例  
 這個範例會使用空的 `foreach` 迴圈 (在 Visual Basic 中為 `For Each`) 來測量執行查詢所需的時間。 在真實的程式碼中，迴圈通常包含會增加查詢執行總時間的額外處理步驟。 請注意,秒表直到迴圈之前才啟動,因為此時查詢執行就開始了。 如果您需要更精細的測量，您可以使用 `ElapsedTicks` 屬性而非 `ElapsedMilliseconds`。  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 在試驗查詢實現時,總執行時間是一個有用的指標,但它並不總是能說明整個情況。 要更深入、更豐富的檢視,瞭解查詢線程彼此和其他正在運行的進程的交互,請使用[併發可視化器](/visualstudio/profiling/concurrency-visualizer)。  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
