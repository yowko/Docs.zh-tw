---
title: "How to: Control Ordering in a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to control ordering"
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Control Ordering in a PLINQ Query
這些範例顯示如何使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 擴充方法來控制 PLINQ 查詢中的順序。  
  
> [!WARNING]
>  這些範例主要是為了示範用法，執行速度不一定比對應的循序 LINQ to Objects 查詢更快。  
  
## 範例  
 下列範例會保留來源序列的順序。  這有時候是必要的，例如某些查詢運算子需要已排序的來源序列，才能產生正確的結果。  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## 範例  
 下列範例顯示一些可能需要已排序來源序列的查詢運算子。  這些運算子對未排序的序列同樣能運作，但可能會產生未預期的結果。  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 若要執行這個方法，請將方法貼至 [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中的 PLINQDataSample 類別，然後按 F5。  
  
## 範例  
 下列範例顯示如何保留查詢中第一個部分的順序，接著移除順序以增加 join 子句的效能，然後再將順序重新套用至最終結果序列。  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 若要執行這個方法，請將方法貼至 [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中的 PLINQDataSample 類別，然後按 F5。  
  
## 請參閱  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)