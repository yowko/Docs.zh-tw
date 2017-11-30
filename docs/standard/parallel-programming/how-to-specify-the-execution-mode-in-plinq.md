---
title: "如何：在 PLINQ 中指定執行模式"
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
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 745ceae9832582c7b66a56075d128f9cf1c8ff69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>如何：在 PLINQ 中指定執行模式
這個範例示範如何強制 PLINQ 略過其預設啟發學習法，不論查詢的圖形的查詢平行處理。  
  
> [!WARNING]
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ 被為了利用平行處理的機會。 不過，並非所有的查詢平行執行而受益。 例如，當查詢包含非常少運作的單一使用者委派，查詢將通常更快依序執行。 這是因為參與啟用平行執行的額外負荷成本高於所取得的加速效果。 因此，PLINQ 不會自動平行處理每個查詢。 它會先檢查查詢和各種運算子組成的圖形。 根據這項分析，PLINQ 的預設執行模式中可能會決定要循序執行部分或所有的查詢。 不過，在某些情況下您可能知道更多查詢的相關比 PLINQ 能夠從其分析判斷。 例如，您可能知道委派是相當耗費資源，並確認此查詢會明確地受益於平行處理。 在這種情況下，您可以使用<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>方法並指定<xref:System.Linq.ParallelExecutionMode.ForceParallelism>值，指示 PLINQ 永遠以平行方式執行查詢。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 剪下並貼到這個程式碼[PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)呼叫此方法從`Main`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
