---
title: "How to: Write a Custom PLINQ Aggregate Function | Microsoft Docs"
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
  - "PLINQ queries, how to create aggregate function"
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Write a Custom PLINQ Aggregate Function
這個範例示範如何使用 <xref:System.Linq.ParallelEnumerable.Aggregate%2A> 方法，將自訂的彙總函式套用至來源序列。  
  
> [!WARNING]
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。  如需加速的詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 範例  
 下列範例會計算整數序列的標準差。  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 此範例會使用 PLINQ 之唯一彙總標準查詢運算子的多載。  此多載會使用額外的 <xref:System.Func%603?displayProperty=fullName> 做為第三個輸入參數。  此委派會先結合所有執行緒的結果，再執行彙總結果的最終計算。  在此範例中，我們會加總所有執行緒的總計。  
  
 請注意，如果 lambda 運算式主體是由單一運算式所組成，則 <xref:System.Func%602?displayProperty=fullName> 委派的傳回值即為運算式的值。  
  
## 請參閱  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)