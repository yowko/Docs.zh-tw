---
title: 作法：結合平行和循序 LINQ 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: e851c6d72a5fd932c065368b893b907d7820c918
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827096"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>作法：結合平行和循序 LINQ 查詢

此範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法來指示 PLINQ 循序處理查詢中所有後續的運算子。 雖然連續處理的速度通常會比平行處理慢，但有時需要產生正確的結果。  
  
> [!NOTE]
> 此範例的目的是要示範使用方式，而且執行速度可能會比對等的連續 LINQ to Objects 查詢更快。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 下列範例示範必須使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的案例，也就是要保留先前的查詢子句中所建立的順序。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯和執行此程式碼，請將它貼到 [ [PLINQ 資料範例](plinq-data-sample.md) ] 專案中，加入從呼叫方法的行 `Main` ，然後按下 **F5**。  
  
## <a name="see-also"></a>請參閱

- [平行 LINQ (PLINQ)](introduction-to-plinq.md)
