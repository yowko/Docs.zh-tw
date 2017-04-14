---
title: "How to: Unwrap a Nested Task | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tasks, how to unwrap nested tasks"
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Unwrap a Nested Task
您可以從方法傳回工作，然後等候該工作完成或從該工作繼續執行，如下列範例所示：  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 在前述範例中，<xref:System.Threading.Tasks.Task%601.Result%2A> 屬性為 `string` \(在 Visual Basic 中則為 `String`\) 型別。  
  
 但是，在某些情節中，您可能需要在另一項工作內建立工作，然後傳回該巢狀工作。  在這種情況下，封入工作的 `TResult` 本身就是一項工作。  在下列範例中，Result 屬性為 `Task<Task<string>>` \(在 C\# 中\) 或 `Task(Of Task(Of String))` \(在 Visual Basic 中\)。  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 雖然可以撰寫程式碼來解開外部工作並擷取原始工作和其 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性，但是這類程式碼並不容易撰寫，因為您必須處理例外狀況還有取消要求。  在這種情況下，建議您使用其中一種 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法，如下列範例所示。  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 方法可用來將任何 `Task<Task>` 或 `Task<Task<TResult>>` \(在 Visual Basic 中為 `Task(Of Task)` 或 `Task(Of Task(Of TResult))`\) 轉換成 `Task` 或 `Task<TResult>` \(在 Visual Basic 中為 `Task(Of TResult)`\)。  新的工作完全表示內部巢狀工作，而且包含取消狀態和所有的例外狀況。  
  
## 範例  
 下列範例示範如何使用 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法。  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## 請參閱  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=fullName>   
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)