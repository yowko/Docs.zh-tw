---
title: 作法：使用 Parallel.Invoke 執行平行作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 2b353fb8cb5e04ee4cab6b49f55539ecb40fab4f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290794"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>作法：使用 Parallel.Invoke 執行平行作業

這個範例示範如何使用工作平行程式庫中的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 平行處理作業。 我們會對共用資料來源執行三項作業。 作業可以透過直接的方式來平行執行，因為它們都不會修改來源。

> [!NOTE]
> 本文件使用 Lambda 運算式來定義 TPL 中的委派。 如果您不熟悉 c # 或 Visual Basic 中的 lambda 運算式，請參閱[PLINQ 和 TPL 中的 Lambda 運算式](lambda-expressions-in-plinq-and-tpl.md)。

## <a name="example"></a>範例

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A> ，您只需表達要並存執行的動作，執行時間就會處理所有的執行緒排程詳細資料，包括自動調整為主電腦上的核心數目。

這個範例會平行處理作業，而不是資料。 除了前述方法以外，您也可以使用 PLINQ 來平行處理 LINQ 查詢，並依序執行查詢。 或者，您可以使用 PLINQ 來平行處理資料。 另一種方式是同時平行處理查詢和工作。 雖然產生的額外負荷可能會降低具有較少處理器之主機電腦上的效能，但是在具有許多處理器的電腦上，它會調整得更好。

## <a name="compile-the-code"></a>編譯程式碼

將整個範例複製並貼到 Microsoft Visual Studio 專案中，然後按 **F5** 鍵。

## <a name="see-also"></a>另請參閱

- [平行程式設計](index.md)
- [作法：取消工作及其子系](how-to-cancel-a-task-and-its-children.md)
- [平行 LINQ (PLINQ)](introduction-to-plinq.md)
