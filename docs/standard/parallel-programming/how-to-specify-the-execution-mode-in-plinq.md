---
title: "How to: Specify the Execution Mode in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, how to use execution mode"
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Specify the Execution Mode in PLINQ
這個範例顯示如何強制 PLINQ 略過其預設啟發式，直接平行處理查詢而不考慮查詢的型態。  
  
> [!WARNING]
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。  如需加速的詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 範例  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ 是專為運用平行處理的機會而設計。  不過，不是所有查詢都適合平行執行方式。  例如，當查詢只包含一個執行極少工作的使用者委派時，以循序方式執行查詢通常會較快。  這是因為啟用平行化執行帶來的負荷高於所獲得的加速效益。  因此，PLINQ 並不會自動平行處理每個查詢。  它會先檢查查詢的型態和查詢中的各種運算子。  根據這項分析，在預設執行模式下的 PLINQ 可能會決定以循序方式執行局部或整個查詢。  不過，有時候相較於 PLINQ 從分析結果來做判斷，您可能還比較瞭解您自己的查詢。  例如，您可能知道某個委派非常耗費資源，所以很肯定平行化作業一定有益於查詢。  在這種情況下，您可以使用 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> 方法並指定 <xref:System.Linq.ParallelExecutionMode> 值，以指示 PLINQ 永遠以平行方式執行查詢。  
  
## 編譯程式碼  
 請將這段程式碼剪下並貼在 [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md)中，然後從 `Main` 中呼叫方法。  
  
## 請參閱  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)