---
title: "How to: Specify Merge Options in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, how to use merge options"
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Specify Merge Options in PLINQ
此範例說明如何指定會套用至 PLINQ 查詢中所有後續運算子的合併選項。  您無須明確地設定合併選項，但執行此設定或許可提升效能。  如需合併選項的詳細資訊，請參閱[Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)。  
  
> [!WARNING]
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。  如需加速的詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 範例  
 下列範例會示範合併選項在來源未排序的基本案例中有何行為，並且會將高度耗費資源的函式套用至每個項目。  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 如果設定 <xref:System.Linq.ParallelMergeOptions> 選項，會在第一個項目產生之前引起不當延遲，請嘗試使用 <xref:System.Linq.ParallelMergeOptions> 選項提高產生結果項目的速度與順暢性。  
  
## 請參閱  
 <xref:System.Linq.ParallelMergeOptions>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)