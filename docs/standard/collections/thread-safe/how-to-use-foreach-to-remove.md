---
title: "如何：使用 ForEach 來移除 BlockingCollection 中的項目 | Microsoft Docs"
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
  - "安全執行緒集合，如何列舉封鎖集合"
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 ForEach 來移除 BlockingCollection 中的項目
除了使用 <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 方法從 <xref:System.Collections.Concurrent.BlockingCollection%601> 取得項目之外，您也可以使用 [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) \(在 Visual Basic 中則為 [For Each](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)\) 移除項目，直到加入完成且集合清空為止。  這種列舉稱為「*變動列舉*」\(Mutating Enumeration\) 或「*耗用列舉*」\(Consuming Enumeration\)，因為不像一般 `foreach` \(`For Each`\) 迴圈，這個列舉程式會藉由移除項目以修改來源集合。  
  
## 範例  
 下列範例顯示如何使用 `foreach` \(`For Each`\) 迴圈來移除 <xref:System.Collections.Concurrent.BlockingCollection%601> 中的所有項目。  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 這個範例會在耗用端執行緒中使用 `foreach` 迴圈並搭配 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> 方法，以在列舉項目的同時將項目從集合中移除。  <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 會隨時限制集合中的項目數上限。  以此方式列舉集合時，如果沒有項目可用或集合是空集合，則消費者執行緒會無法繼續。  在這個範例中，封鎖並非考量重點，因為生產者執行緒加入項目的速度比使用的速度還要快。  
  
 項目的列舉順序不保證會和生產者執行緒加入項目的順序相同。  
  
 若要列舉集合而不加以修改，請使用 `foreach` \(`For Each`\) 就好，不要搭配 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法。  但是，請務必了解這種列舉代表的是集合在某個時間點的快照。  如果當您執行迴圈時同時有其他執行緒在加入或移除項目，則這個迴圈可能無法代表集合的實際狀態。  
  
## 請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Parallel Programming](../../../../docs/standard/parallel-programming/index.md)