---
title: "如何：傳回工作的值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ade2aadc7d76c12c633f84eeb9eced7a637d5df9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-task"></a>如何：傳回工作的值
這個範例示範如何使用 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 類型從 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性傳回值。 它需要有 C:\Users\Public\Pictures\Sample Pictures\ 目錄存在，且其中包含檔案。  
  
## <a name="example"></a>範例  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性會封鎖呼叫執行緒，直到工作完成。  
  
 若要查看如何傳遞其中一個結果<xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>接續工作，請參閱[使用接續工作鏈結工作](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)。  
  
## <a name="see-also"></a>另請參閱  
 [以工作為基礎的非同步程式設計](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
