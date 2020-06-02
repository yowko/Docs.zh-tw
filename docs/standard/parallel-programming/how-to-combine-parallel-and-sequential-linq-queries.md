---
title: 作法：結合平行和循序 LINQ 查詢
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 2bdf074bc2977dc501e0726a52e825c89828565f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289534"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>作法：結合平行和循序 LINQ 查詢

此範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法來指示 PLINQ 循序處理查詢中所有後續的運算子。 雖然連續處理通常會比平行處理慢，但有時必須產生正確的結果。  
  
> [!NOTE]
> 這個範例的目的是要示範使用方式，而且其執行速度可能會比對等的順序 LINQ to Objects 查詢更快。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 下列範例示範必須使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的案例，也就是要保留先前的查詢子句中所建立的順序。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯並執行此程式碼，請將它貼到[PLINQ 資料範例](plinq-data-sample.md)專案中，加入從呼叫方法的行， `Main` 然後按**F5**。  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](introduction-to-plinq.md)
