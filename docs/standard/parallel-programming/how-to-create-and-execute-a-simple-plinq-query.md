---
title: 如何：建立並執行簡單的 PLINQ 查詢
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: c4cd75e55aabb551e5951a902ea6394a5659c9ee
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635846"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>如何：建立並執行簡單的 PLINQ 查詢

本文中的範例展示如何使用來源序列上的<xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType>擴充方法建立簡單的並行語言整合查詢 (LINQ) 查詢,並使用該方法<xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp>執行查詢。  
  
> [!NOTE]
> 本文件使用 Lambda 運算式來定義 PLINQ 中的委派。 如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 此示例演示了在結果序列的順序不重要時創建和執行任何 Parallel LINQ 查詢的基本模式。 無序查詢通常比有序查詢快。 查詢會將來源分割成在多個執行緒上非同步執行的工作。 每項工作的完成順序不僅取決於處理分割中的項目時所涉及的工作量，也取決於一些外部因素，例如作業系統排程每個執行緒的方式。 這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。 如需如何在查詢中保留元素順序的詳細資訊，請參閱[如何：控制 PLINQ 查詢中的順序](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)。  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
