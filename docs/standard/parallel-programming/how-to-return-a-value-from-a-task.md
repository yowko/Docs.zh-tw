---
title: "How to: Return a Value from a Task | Microsoft Docs"
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
  - "tasks, how to return a value"
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Return a Value from a Task
這個範例示範如何使用 <xref:System.Threading.Tasks.Task%601?displayProperty=fullName> 類型從 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性傳回值。  它需要有 C:\\Users\\Public\\Pictures\\Sample Pictures\\ 目錄存在，且其中包含檔案。  
  
## 範例  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性會封鎖呼叫執行緒，直到工作完成。  
  
 若要查看如何傳遞一個 <xref:System.Threading.Tasks.Task%601?displayProperty=fullName> 的結果到接續工作，請參閱[使用接續工作鏈結工作](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)。  
  
## 請參閱  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)