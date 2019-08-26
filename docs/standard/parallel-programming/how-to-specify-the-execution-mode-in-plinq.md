---
title: 作法：在 PLINQ 中指定執行模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 705b6bc364e2ecf00c3629814228157c90017a8b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988451"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>作法：在 PLINQ 中指定執行模式
這個範例示範如何強制 PLINQ 略過其預設啟發學習法並以平行方式處理查詢，而不考慮查詢的種類。  
  
> [!WARNING]
> 這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ 的設計，是要利用可以平行處理的機會。 不過，並非所有查詢都適合平行執行。 例如，當查詢包含工作極少的單一使用者委派時，循序執行查詢通常會更快。 這是因為啟用平行執行的額外負荷所耗用的資源高於增加的速度。 因此，PLINQ 不會自動平行處理每個查詢。 它會先檢查查詢的種類，和組成查詢的各個運算子。 根據這項分析，預設執行模式的 PLINQ 就能決定要循序執行部分或所有的查詢。 不過，在某些情況下，您所能得知的查詢資訊，不僅僅是 PLINQ 能夠從其分析中判斷的資訊。 例如，您可能知道委派相當耗費資源，因此查詢明確地適合平行處理。 在這種情況下，您可以使用 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>方法並指定 <xref:System.Linq.ParallelExecutionMode.ForceParallelism> 值，指示 PLINQ 永遠以平行方式執行查詢。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 將此程式碼剪下並貼到 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)，並從 `Main` 呼叫此方法。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
