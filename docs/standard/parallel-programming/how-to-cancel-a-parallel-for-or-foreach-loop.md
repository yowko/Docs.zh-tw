---
title: "How to: Cancel a Parallel.For or ForEach Loop | Microsoft Docs"
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
  - "parallel foreach loop, how to cancel"
  - "parallel for loops, how to cancel"
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Cancel a Parallel.For or ForEach Loop
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 方法可使用取消語彙基元支援取消作業。  如需取消作業的一般相關資訊，請參閱[取消](../../../docs/standard/threading/cancellation-in-managed-threads.md)。  在平行迴圈中，您可以在 <xref:System.Threading.Tasks.ParallelOptions> 參數中為方法提供 <xref:System.Threading.CancellationToken>，然後將平行呼叫包含在 try\-catch 區塊中。  
  
## 範例  
 下列範例說明如何取消 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 的呼叫。  您可以將相同的方法套用至 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> 呼叫。  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 如果表示取消的語彙基元是 <xref:System.Threading.Tasks.ParallelOptions> 執行個體中所指定的相同語彙基元，則平行迴圈會對取消擲回單一 <xref:System.OperationCanceledException>。  如果是其他語彙基元造成取消，則迴圈會擲回以 <xref:System.OperationCanceledException> 做為 InnerException 的 <xref:System.AggregateException>。  
  
## 請參閱  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)