---
title: 作法：使用 Parallel.Invoke 執行平行作業
description: 請參閱如何使用工作平行程式庫中的 Parallel. Invoke 方法 (TPL) ，其會對 .NET 中的共用資料來源執行平行作業。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 6ec8f03216cc6225e909f5dc3128469047826166
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825477"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>作法：使用 Parallel.Invoke 執行平行作業

這個範例示範如何使用工作平行程式庫中的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 平行處理作業。 我們會對共用資料來源執行三項作業。 您可以直接以平行方式執行作業，因為它們都不會修改來源。

> [!NOTE]
> 本文件使用 Lambda 運算式來定義 TPL 中的委派。 如果您不熟悉 c # 或 Visual Basic 中的 lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](lambda-expressions-in-plinq-and-tpl.md)。

## <a name="example"></a>範例

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 時，您只需表達要並存執行的動作，而執行時間會處理所有線程排程詳細資料，包括自動調整為主電腦上的核心數目。

這個範例會平行處理作業，而不是資料。 除了前述方法以外，您也可以使用 PLINQ 來平行處理 LINQ 查詢，並依序執行查詢。 或者，您可以使用 PLINQ 來平行處理資料。 另一種方式是同時平行處理查詢和工作。 雖然產生的額外負荷可能會降低具有相對較少處理器之主機電腦上的效能，但在具有許多處理器的電腦上更能調整其效能。

## <a name="compile-the-code"></a>編譯程式碼

將整個範例複製並貼到 Microsoft Visual Studio 專案中，然後按 **F5** 鍵。

## <a name="see-also"></a>請參閱

- [平行程式設計](index.md)
- [作法：取消工作及其子系](how-to-cancel-a-task-and-its-children.md)
- [平行 LINQ (PLINQ)](introduction-to-plinq.md)
