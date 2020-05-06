---
title: 使用 foreach 移除 BlockingCollection 中的專案
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: 1255fcda89396ea8ff9abf6cf111e6dd9ea5a87d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82861008"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>使用 foreach 移除 BlockingCollection 中的專案

<xref:System.Collections.Concurrent.BlockingCollection%601>除了使用<xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A>和<xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>方法從取得專案，您也可以使用[Foreach](../../../csharp/language-reference/keywords/foreach-in.md) （適用于 Visual Basic 中的[每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md)）搭配<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType>來移除專案，直到新增完成，而且集合是空的。 這稱為「變動列舉」** 或「使用列舉」**，因為不像一般 `foreach` (`For Each`) 迴圈，這個列舉程式會透過移除項目以修改來源集合。

## <a name="example"></a>範例

下列範例示範如何使用 `foreach` (`For Each`) 迴圈來移除 <xref:System.Collections.Concurrent.BlockingCollection%601> 中的所有項目。

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

本範例在使用執行緒中搭配使用 `foreach` 迴圈與 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> 方法，這樣會移除所列舉集合中的每個項目。 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>會限制集合中任何時間項目的最大數量。 列舉集合，以在沒有項目可用或集合是空的時封鎖消費者執行緒。 在此範例中，封鎖不是問題，因為生產者執行緒新增項目的速度比使用項目還要快。

<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType>會傳回`IEnumerable<T>`，因此無法保證順序。 不過，內部<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>會使用做為基礎集合類型，這會在先進先出（FIFO）順序的情況下清除物件。 如果對進行<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType>了並行呼叫，它們將會競爭。 在一個列舉中耗用的一個專案（已清除佇列）無法在另一個列舉中觀察到。

若要列舉集合，而不修改集合，則只要使用 `foreach` (`For Each`)，而不要使用 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法。 不過，請務必了解這種列舉代表集合在精確時間點的快照集。 如果其他執行緒在您執行迴圈時同時新增或移除項目，則迴圈可能不會代表集合的實際狀態。

## <a name="see-also"></a>請參閱

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [平行程式設計](../../../../docs/standard/parallel-programming/index.md)
