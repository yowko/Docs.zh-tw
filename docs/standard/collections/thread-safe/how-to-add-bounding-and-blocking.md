---
title: 如何：將界限和封鎖功能加入至集合
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f52d1067a8aa907c8f1cf8b550eec82d1133b3f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261742"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="e2333-102">如何：將界限和封鎖功能加入至集合</span><span class="sxs-lookup"><span data-stu-id="e2333-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="e2333-103">這個範例示範如何實作類別中的 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> 介面，然後使用類別執行個體作為 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 的內部儲存機制，以將界限和封鎖功能新增至自訂集合類別。</span><span class="sxs-lookup"><span data-stu-id="e2333-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e2333-104">如需界限和封鎖的詳細資訊，請參閱 [BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e2333-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2333-105">範例</span><span class="sxs-lookup"><span data-stu-id="e2333-105">Example</span></span>  
 <span data-ttu-id="e2333-106">自訂集合類別是優先順序層級呈現為 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> 物件陣列的基本優先順序佇列。</span><span class="sxs-lookup"><span data-stu-id="e2333-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="e2333-107">在每個佇列內不會執行額外的排序。</span><span class="sxs-lookup"><span data-stu-id="e2333-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="e2333-108">在用戶端程式碼中，會啟動三項工作。</span><span class="sxs-lookup"><span data-stu-id="e2333-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="e2333-109">第一項工作只會輪詢鍵盤按鍵，可在執行期間隨時取消。</span><span class="sxs-lookup"><span data-stu-id="e2333-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="e2333-110">第二項工作是生產者執行緒；它會將新的項目新增至封鎖回收，並根據隨機值來指定每個項目的優先順序。</span><span class="sxs-lookup"><span data-stu-id="e2333-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="e2333-111">第三項工作是在項目可供使用時將其從集合中移除。</span><span class="sxs-lookup"><span data-stu-id="e2333-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="e2333-112">您可以讓其中一個執行緒的執行速度快於另一個執行緒，來調整應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="e2333-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="e2333-113">如果生產者的執行速度較快，則會注意到界限功能，原因是封鎖回收在已包含建構函式中所指定的項目數時會防止新增項目。</span><span class="sxs-lookup"><span data-stu-id="e2333-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="e2333-114">如果消費者的執行速度較快，您會在消費者等待新增項目時注意到封鎖功能。</span><span class="sxs-lookup"><span data-stu-id="e2333-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="e2333-115">根據預設，<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 的儲存體是 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e2333-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2333-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2333-116">See also</span></span>

- [<span data-ttu-id="e2333-117">安全執行緒集合</span><span class="sxs-lookup"><span data-stu-id="e2333-117">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
