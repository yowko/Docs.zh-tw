---
title: 作法：在 PLINQ 中指定執行模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 725f232337952449cd8569b12f65da75569996df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722381"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>作法：在 PLINQ 中指定執行模式

這個範例示範如何強制 PLINQ 略過其預設啟發學習法並以平行方式處理查詢，而不考慮查詢的種類。  
  
> [!NOTE]
> 此範例的目的是要示範使用方式，而且執行速度可能會比對等的連續 LINQ to Objects 查詢更快。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  

 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ 的設計，是要利用可以平行處理的機會。 不過，並非所有查詢都適合平行執行。 例如，當查詢包含沒有足夠工作的單一使用者委派時，查詢通常會以較快的速度執行。 循序執行的速度較快，因為啟用平行執行的額外負荷比取得的加速更昂貴。 因此，PLINQ 不會自動平行處理每個查詢。 它會先檢查查詢的種類，和組成查詢的各個運算子。 根據這項分析，預設執行模式的 PLINQ 就能決定要循序執行部分或所有的查詢。 不過，在某些情況下，您所能得知的查詢資訊，不僅僅是 PLINQ 能夠從其分析中判斷的資訊。 例如，您可能知道委派的成本很高，而且查詢一定會受益于平行處理。 在這種情況下，您可以使用 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>方法並指定 <xref:System.Linq.ParallelExecutionMode.ForceParallelism> 值，指示 PLINQ 永遠以平行方式執行查詢。  
  
## <a name="compiling-the-code"></a>編譯程式碼  

 將此程式碼剪下並貼到 [PLINQ 資料範例](plinq-data-sample.md)，並從 `Main` 呼叫此方法。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [平行 LINQ (PLINQ)](introduction-to-plinq.md)
