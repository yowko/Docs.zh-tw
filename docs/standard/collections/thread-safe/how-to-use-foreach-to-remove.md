---
title: 如何：使用 ForEach 來移除 BlockingCollection 中的項目
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b71ed726af585259b015c608e49d8c81e4e22a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512851"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>如何：使用 ForEach 來移除 BlockingCollection 中的項目
除了使用 <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 方法從 <xref:System.Collections.Concurrent.BlockingCollection%601> 擷取項目之外，您也可以使用 [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) (Visual Basic 中為 [For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md)) 來移除項目，直到新增完成，而且集合是空的。 這稱為「變動列舉」或「使用列舉」，因為不像一般 `foreach` (`For Each`) 迴圈，這個列舉程式會透過移除項目以修改來源集合。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `foreach` (`For Each`) 迴圈來移除 <xref:System.Collections.Concurrent.BlockingCollection%601> 中的所有項目。  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 本範例在使用執行緒中搭配使用 `foreach` 迴圈與 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> 方法，這樣會移除所列舉集合中的每個項目。 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>會限制集合中任何時間項目的最大數量。 列舉集合，以在沒有項目可用或集合是空的時封鎖消費者執行緒。 在此範例中，封鎖不是問題，因為生產者執行緒新增項目的速度比使用項目還要快。  
  
 不保證項目的列舉順序與生產者執行緒新增它們的順序相同。  
  
 若要列舉集合，而不修改集合，則只要使用 `foreach` (`For Each`)，而不要使用 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法。 不過，請務必了解這種列舉代表集合在精確時間點的快照集。 如果其他執行緒在您執行迴圈時同時新增或移除項目，則迴圈可能不會代表集合的實際狀態。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [平行程式設計](../../../../docs/standard/parallel-programming/index.md)
