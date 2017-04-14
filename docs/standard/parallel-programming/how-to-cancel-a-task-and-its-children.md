---
title: "How to: Cancel a Task and Its Children | Microsoft Docs"
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
  - "tasks, how to cancel"
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Cancel a Task and Its Children
這些範例將說明如何執行下列工作：  
  
1.  建立及啟動可取消的工作。  
  
2.  將取消語彙基元傳遞至您的使用者委派，並選擇性地傳遞至工作執行個體。  
  
3.  注意使用者委派中的取消要求，並予以回應。  
  
4.  \(選擇性\) 注意已取消工作的呼叫端執行緒。  
  
 呼叫端執行緒不會強制結束工作；它只會有通知指出有人要求取消。  如果工作已在執行中，則應由使用者委派注意要求並予以適當回應。  如果是在工作執行前要求取消，則使用者委派未曾執行，而工作物件會轉換成「已取消」狀態。  
  
## 範例  
 此範例說明如何在回應取消要求時結束 <xref:System.Threading.Tasks.Task> 及其子系。  此範例也說明在使用者委派藉由擲回 <xref:System.Threading.Tasks.TaskCanceledException> 而結束時，呼叫端執行緒可以選擇性地使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法等候工作完成。  在這種情況下，必須使用  `try/catch` 區塊來處理呼叫端執行緒的例外狀況。  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 類別已與以 <xref:System.Threading.CancellationTokenSource?displayProperty=fullName> 和 <xref:System.Threading.CancellationToken?displayProperty=fullName> 型別為基礎的取消模型完全整合。  如需詳細資訊，請參閱[Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)與[Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md)。  
  
## 請參閱  
 <xref:System.Threading.CancellationTokenSource?displayProperty=fullName>   
 <xref:System.Threading.CancellationToken?displayProperty=fullName>   
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.Task%601?displayProperty=fullName>   
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)   
 [Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)