---
title: 如何：結合平行和循序 LINQ 查詢
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 074714b1152c8804ee1e747104dbaf47f4645546
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635861"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>如何：結合平行和循序 LINQ 查詢

此範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法來指示 PLINQ 循序處理查詢中所有後續的運算子。 儘管順序處理通常比並行慢,但有時需要生成正確的結果。  
  
> [!NOTE]
> 此示例旨在演示使用方式,並且可能不會比等效的連續 LINQ 到物件查詢運行得更快。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 下列範例示範必須使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的案例，也就是要保留先前的查詢子句中所建立的順序。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 要編譯與執行此代碼,請將您的程式貼上[到 PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)項目中,新增一`Main`行以呼叫方法,然後按**F5**。  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
