---
title: "如何：使用 ForEach 來移除 BlockingCollection 中的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 823cde5ddd06d3b5cc2ad03327fc38e7651ed74d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="7a3bb-102">如何：使用 ForEach 來移除 BlockingCollection 中的項目</span><span class="sxs-lookup"><span data-stu-id="7a3bb-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="7a3bb-103">除了使用 <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 方法從 <xref:System.Collections.Concurrent.BlockingCollection%601> 擷取項目之外，您也可以使用 [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) (Visual Basic 中為 [For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md)) 來移除項目，直到新增完成，而且集合是空的。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="7a3bb-104">這稱為「變動列舉」或「使用列舉」，因為不像一般 `foreach` (`For Each`) 迴圈，這個列舉程式會透過移除項目以修改來源集合。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a3bb-105">範例</span><span class="sxs-lookup"><span data-stu-id="7a3bb-105">Example</span></span>  
 <span data-ttu-id="7a3bb-106">下列範例示範如何使用 `foreach` (`For Each`) 迴圈來移除 <xref:System.Collections.Concurrent.BlockingCollection%601> 中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 <span data-ttu-id="7a3bb-107">本範例在使用執行緒中搭配使用 `foreach` 迴圈與 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> 方法，這樣會移除所列舉集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="7a3bb-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>會限制集合中任何時間項目的最大數量。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="7a3bb-109">列舉集合，以在沒有項目可用或集合是空的時封鎖消費者執行緒。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="7a3bb-110">在此範例中，封鎖不是問題，因為生產者執行緒新增項目的速度比使用項目還要快。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="7a3bb-111">不保證項目的列舉順序與生產者執行緒新增它們的順序相同。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="7a3bb-112">若要列舉集合，而不修改集合，則只要使用 `foreach` (`For Each`)，而不要使用 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="7a3bb-113">不過，請務必了解這種列舉代表集合在精確時間點的快照集。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="7a3bb-114">如果其他執行緒在您執行迴圈時同時新增或移除項目，則迴圈可能不會代表集合的實際狀態。</span><span class="sxs-lookup"><span data-stu-id="7a3bb-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3bb-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a3bb-115">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="7a3bb-116">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="7a3bb-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
