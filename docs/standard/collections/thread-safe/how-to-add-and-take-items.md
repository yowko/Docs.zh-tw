---
title: "如何：從 BlockingCollection 個別加入和擷取項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
caps.latest.revision: 7
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 66b4e921a4c7285976694f4633ce1eeaadcb7cf9
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="a18b4-102">如何：從 BlockingCollection 個別加入和擷取項目</span><span class="sxs-lookup"><span data-stu-id="a18b4-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="a18b4-103">本範例示範如何利用封鎖方式和非封鎖方式，在 <xref:System.Collections.Concurrent.BlockingCollection%601> 中加入和移除項目。</span><span class="sxs-lookup"><span data-stu-id="a18b4-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and non-blocking manner.</span></span> <span data-ttu-id="a18b4-104">如需 <xref:System.Collections.Concurrent.BlockingCollection%601> 的詳細資訊，請參閱 [BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a18b4-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="a18b4-105">如需如何列舉 <xref:System.Collections.Concurrent.BlockingCollection%601> 直到其為空的以及無法再新增項目的範例，請參閱[如何：使用 ForEach 來移除 BlockingCollection 中的項目](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)。</span><span class="sxs-lookup"><span data-stu-id="a18b4-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="a18b4-106">範例</span><span class="sxs-lookup"><span data-stu-id="a18b4-106">Example</span></span>  
 <span data-ttu-id="a18b4-107">第一個範例示範如何加入和擷取項目，以便在集合暫時空白 (擷取時)、達到最大容量 (加入時) 或超過指定的逾時期限時封鎖作業。</span><span class="sxs-lookup"><span data-stu-id="a18b4-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or a specified timeout period has elapsed.</span></span> <span data-ttu-id="a18b4-108">請注意，只有在已建立 BlockingCollection，並在建構函式中指定最大容量時，才會啟用最大容量封鎖。</span><span class="sxs-lookup"><span data-stu-id="a18b4-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 <span data-ttu-id="a18b4-109">[!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)] [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]</span><span class="sxs-lookup"><span data-stu-id="a18b4-109">[!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)] [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a18b4-110">範例</span><span class="sxs-lookup"><span data-stu-id="a18b4-110">Example</span></span>  
 <span data-ttu-id="a18b4-111">第二個範例示範如何加入和擷取項目，而不會封鎖作業。</span><span class="sxs-lookup"><span data-stu-id="a18b4-111">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="a18b4-112">如果沒有任何項目、已達到界限集合的最大容量或超過逾時期限，則 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 或 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 作業會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="a18b4-112">If no item is present, or maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="a18b4-113">如此便可讓執行緒在一段時間內先執行其他一些有用的工作，再於稍後重試擷取新的項目，或嘗試加入之前無法加入的相同項目。</span><span class="sxs-lookup"><span data-stu-id="a18b4-113">This allows the thread to do some other useful work for awhile and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="a18b4-114">這個程式也會示範如何在存取 <xref:System.Collections.Concurrent.BlockingCollection%601>時實作取消作業。</span><span class="sxs-lookup"><span data-stu-id="a18b4-114">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 <span data-ttu-id="a18b4-115">[!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)] [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]</span><span class="sxs-lookup"><span data-stu-id="a18b4-115">[!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)] [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18b4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a18b4-116">See Also</span></span>  
 <span data-ttu-id="a18b4-117"><xref:System.Collections.Concurrent?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a18b4-117"><xref:System.Collections.Concurrent?displayProperty=fullName></span></span>   
 [<span data-ttu-id="a18b4-118">BlockingCollection 概觀</span><span class="sxs-lookup"><span data-stu-id="a18b4-118">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)

