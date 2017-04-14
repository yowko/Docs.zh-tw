---
title: "How to: Combine Parallel and Sequential LINQ Queries | Microsoft Docs"
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
  - "parallel queries, combine parallel and sequential"
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Combine Parallel and Sequential LINQ Queries
這個範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法指示 PLINQ 循序處理查詢中所有的後續運算子。  雖然循序處理的速度通常比平行處理慢，但有時必須使用循序處理才能產生正確結果。  
  
> [!WARNING]
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。  如需加速的詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 範例  
 下列範例說明必須使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的案例，也就是要保留先前的查詢子句中所建立的順序。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## 編譯程式碼  
 若要編譯和執行這個程式碼，請將程式碼貼上至 [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案、在 `Main` 中加入一行呼叫這個方法的程式碼，然後按 F5。  
  
## 請參閱  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)