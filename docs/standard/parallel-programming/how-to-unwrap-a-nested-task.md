---
title: "如何：解除包裝巢狀工作"
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
helpviewer_keywords: tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2da3de912abb693c4342e1ede02f273348e4b571
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unwrap-a-nested-task"></a>如何：解除包裝巢狀工作
您可以從方法傳回的工作，然後等候或繼續從該工作，如下列範例所示：  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 在上述範例中，<xref:System.Threading.Tasks.Task%601.Result%2A>屬性屬於型別`string`(`String`在 Visual Basic 中)。  
  
 不過，在某些情況下，您可能想要建立另一項工作中的工作，然後傳回 巢狀的工作。 在此情況下，`TResult`的封入的工作是本身的工作。 在下列範例中，結果屬性是`Task<Task<string>>`在 C# 或`Task(Of Task(Of String))`在 Visual Basic 中。  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 雖然可以撰寫程式碼以解除包裝外部工作，並擷取原始的工作及其<xref:System.Threading.Tasks.Task%601.Result%2A>屬性，這類程式碼不容易寫入，因為您必須處理的例外狀況以及取消要求。 在此情況下，我們建議您使用其中一個<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>擴充方法，如下列範例所示。  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>方法可以用來轉換任何`Task<Task>`或`Task<Task<TResult>>`(`Task(Of Task)`或`Task(Of Task(Of TResult))`在 Visual Basic 中) 以`Task`或`Task<TResult>`(`Task(Of TResult)`在 Visual Basic 中)。 新的工作完全代表內部的巢狀的工作，並包含取消狀態，以及所有例外狀況。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>擴充方法。  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [以工作為基礎的非同步程式設計](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
