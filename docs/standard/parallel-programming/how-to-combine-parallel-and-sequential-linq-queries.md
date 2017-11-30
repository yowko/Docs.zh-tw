---
title: "如何：結合平行和循序 LINQ 查詢"
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
helpviewer_keywords: parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4da91ff535059b181baa637164a854cd75d06334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>如何：結合平行和循序 LINQ 查詢
這個範例示範如何使用<xref:System.Linq.ParallelEnumerable.AsSequential%2A>指示 PLINQ 查詢中的所有後續運算子會循序處理方法。 雖然通常低於平行循序處理，但有時候很需要產生正確的結果。  
  
> [!WARNING]
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示在其中一個案例<xref:System.Linq.ParallelEnumerable.AsSequential%2A>為必要項，也就是要保留先前的查詢子句中已建立的順序。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯及執行此程式碼，將它貼入[PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中，加入一行呼叫的方法，從`Main`，然後按 f5 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
