---
title: 作法：從工作傳回值
description: 請參閱如何使用 [System.object] 工作 <TResult> 類型，從 .net 中的 Result 屬性傳回值。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 051cef7cac654e4369ec1486884876004370ba0b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767971"
---
# <a name="how-to-return-a-value-from-a-task"></a>作法：從工作傳回值
這個範例示範如何使用 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 類型從 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性傳回值。 它需要有 C:\Users\Public\Pictures\Sample Pictures\ 目錄存在，且其中包含檔案。  
  
## <a name="example"></a>範例  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性會封鎖呼叫執行緒，直到工作完成。  
  
 若要查看如何傳遞一個 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 的結果到接續工作，請參閱[使用接續工作鏈結工作](chaining-tasks-by-using-continuation-tasks.md)。  
  
## <a name="see-also"></a>另請參閱

- [以工作為基礎的非同步程式設計](task-based-asynchronous-programming.md)
- [PLINQ 和 TPL 中的 Lambda 運算式](lambda-expressions-in-plinq-and-tpl.md)
