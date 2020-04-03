---
title: 如何：使用 Parallel.Invoke 執行平行作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: f61bbf10bbeef736f66710f50e621c3619355a1d
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635795"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>如何：使用 Parallel.Invoke 執行平行作業

這個範例示範如何使用工作平行程式庫中的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 平行處理作業。 我們會對共用資料來源執行三項作業。 操作可以以簡單的方式並行執行,因為它們都無法修改源。

> [!NOTE]
> 本文件使用 Lambda 運算式來定義 TPL 中的委派。 如果您不熟悉 C# 或 Visual Basic 中的 lambda 表示式,請參考[PLINQ 與 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。

## <a name="example"></a>範例

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

使用<xref:System.Threading.Tasks.Parallel.Invoke%2A>時,只需表示要同時運行哪些操作,運行時即可處理所有線程計劃詳細資訊,包括自動縮放到主機上的內核數。

這個範例會平行處理作業，而不是資料。 除了前述方法以外，您也可以使用 PLINQ 來平行處理 LINQ 查詢，並依序執行查詢。 或者，您可以使用 PLINQ 來平行處理資料。 另一種方式是同時平行處理查詢和工作。 儘管產生的開銷可能會降低處理器相對較少的主機上的性能,但它在具有許多處理器的計算機上會更好地擴展。

## <a name="compile-the-code"></a>編譯程式碼

將整個範例複製並貼到 Microsoft Visual Studio 專案中，然後按 **F5** 鍵。

## <a name="see-also"></a>另請參閱

- [平行編程式](../../../docs/standard/parallel-programming/index.md)
- [如何：取消工作及其子系](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
