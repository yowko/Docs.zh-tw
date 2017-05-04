---
title: "如何：使用 ForEach 來移除 BlockingCollection 中的項目 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 88d36d440b6a1d79f978e2cf39bbe2cde241af6b
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>如何：使用 ForEach 來移除 BlockingCollection 中的項目
除了使用 <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 方法從 <xref:System.Collections.Concurrent.BlockingCollection%601> 取得項目之外，您也可以使用 [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) (在 Visual Basic 中為 [For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md)) 移除項目，直到加入完成且集合清空為止。 這稱為「變動列舉」或「使用列舉」，因為不像一般 `foreach` (`For Each`) 迴圈，這個列舉程式會透過移除項目以修改來源集合。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用 `foreach` (`For Each`) 迴圈來移除 <xref:System.Collections.Concurrent.BlockingCollection%601> 中的所有項目。  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 這個範例會在使用端執行緒中使用 `foreach` 迴圈搭配 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> 方法，以在列舉項目的同時將項目從集合中移除。 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 會隨時限制集合中的項目數上限。 列舉集合，以在沒有項目可用或集合是空的時封鎖消費者執行緒。 在此範例中，封鎖不是問題，因為生產者執行緒新增項目的速度比使用項目還要快。  
  
 不保證項目的列舉順序與生產者執行緒新增它們的順序相同。  
  
 若要列舉集合而不加以修改，只需使用 `foreach` (`For Each`)，不要搭配 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法。 不過，請務必了解這種列舉代表集合在精確時間點的快照集。 如果其他執行緒在您執行迴圈時同時新增或移除項目，則迴圈可能不會代表集合的實際狀態。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [平行程式設計](../../../../docs/standard/parallel-programming/index.md)
