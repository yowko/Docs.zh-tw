---
title: "How to: Measure PLINQ Query Performance | Microsoft Docs"
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
  - "PLINQ queries, how to measure performance"
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Measure PLINQ Query Performance
此範例說明如何使用 <xref:System.Diagnostics.Stopwatch> 類別來測量 PLINQ 查詢執行所需的時間。  
  
## 範例  
 此範例會使用空的 `foreach` 迴圈 \(在 Visual Basic 中為 `For Each`\) 測量查詢執行所需的時間。  在實際的程式碼中，迴圈通常包含會增長查詢總執行時間的其他處理步驟。  請注意，stopwatch 要到迴圈即將開始前才會啟動，因為那是查詢開始執行的時間。  如果您需要更精密的測量，您可以使用 `ElapsedTicks` 屬性來取代 `ElapsedMilliseconds`。  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 在您嘗試進行查詢實作時，總執行時間會是有用的度量，但不見得能忠實呈現實際情況。  若要更深入而廣泛地探究查詢執行緒彼此之間以及與其他執行中處理序的互動，請使用「並行視覺化檢視」。  如需詳細資訊，請參閱[並行視覺化檢視](../Topic/Concurrency%20Visualizer.md)。  
  
## 請參閱  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)