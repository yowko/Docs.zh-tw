---
title: "如何：使用屏障同步處理並行作業"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="b9cd5-102">如何：使用屏障同步處理並行作業</span><span class="sxs-lookup"><span data-stu-id="b9cd5-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="b9cd5-103">下列範例示範如何同步處理並行的工作與<xref:System.Threading.Barrier>。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9cd5-104">範例</span><span class="sxs-lookup"><span data-stu-id="b9cd5-104">Example</span></span>  
 <span data-ttu-id="b9cd5-105">下列程式的目的是方案的，計算多少反覆項目 （或階段） 所需的每個尋找兩個執行緒及其半 「 相同 」 階段使用 randomizing 演算法 reshuffle 單字。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="b9cd5-106">每個執行緒有打散其文字之後，屏障的後續階段作業會比較兩個結果，以查看完整的句子若已呈現正確的字順序。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="b9cd5-107">A<xref:System.Threading.Barrier>是可防止平行作業無法繼續，直到所有工作都到達屏障中的個別工作的物件。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="b9cd5-108">會很有用時，平行作業中階段，就必須同步處理工作之間，每個階段。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="b9cd5-109">在此範例中，有兩個階段作業。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="b9cd5-110">在第一個階段中，每項工作會填滿的緩衝區的資料 > 一節。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="b9cd5-111">每個工作完成時填入 > 一節，工作會表示屏障可準備好繼續進行，然後等候。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="b9cd5-112">所有工作有收到都信號時屏障，它們會解除封鎖，第二個階段開始。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="b9cd5-113">屏障是必要的因為第二個階段需要每個工作有已產生到這個點的存取權的所有資料。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="b9cd5-114">屏障沒有完成的第一個工作可能會嘗試從已不填入尚未由其他工作的緩衝區讀取。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="b9cd5-115">您可以將任意數目的階段以這種方式同步處理。</span><span class="sxs-lookup"><span data-stu-id="b9cd5-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9cd5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9cd5-116">See Also</span></span>  
 [<span data-ttu-id="b9cd5-117">適用於平行程式設計的資料結構</span><span class="sxs-lookup"><span data-stu-id="b9cd5-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
